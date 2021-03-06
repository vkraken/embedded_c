09/02/2020
Embedded C studies

Final Assessment

Expanded Build System and Memory.

File Requirements

main.c

Your main function will be very simple. You will just need to call a function
that is defined in the course1.c source file. However, you need to use a
compile time switch to wrap this function to call. This way we can have a
simple main() function that can switch which course deliverable we wish to
call by specifying the -DCOURSE1 compile time switch.

stats.c/stats.h

You need to modify your print_array() function in stats.c so that you can
enable/disable debug printing with a compile time switch. This compile time
switch should be enabled with a VERBOSE flag in the makefile ( -DVERBOSE ). If
enabled, the print_array function should print as normal. If not defined,
nothing should print. Additionally, you need to modify your use of
printf to use the PRINTF macro defined in platform.h

memory.c/memory.h Requirements

Add some memory manipulation functions.

uint8_t * my_memmove(uint8_t * src, uint8_t * dst, size_t length);

	* this function takes two byte pointers (one source and one
	destination) and a length of bytes to move from the source location
	to the destination;

	* the behavior should handle overlap of source and destination, copy
	should occur, with no data corruption;

	* all operations need to be performed using pointer arithmetic, not
	array indexing;

	* should return a pointer to the destination (dst).


uint8_t * my_memcopy(uint8_t * src, uint8_t * dst, size_t length);

	* this function takes two byte pointers (one source and one
	destination) and a length of bytes to copy from the source location
	to the destination;

	* the behavior is undefined if there is overlap of source and
	destination, copy should still occur, but will likely corrupt your
	data.

	* all operations need to be performed using pointer arithmetic, not
	array indexing. 

	* should return a pointer to the destination (dst).


uint8_t * my_memset(uint8_t * src, size_t length, uint8_t value);

	* this should take a pointer to a source memory location, a length
	in bytes and set all locations of that memory to a given value;

	* all operations need to be performed using pointer arithmetic, not
	array indexing; 

	* should return a pointer to the source (src).


uint8_t * my_memzero(uint8_t * src, size_t length);

	* this should take a pointer to a memory location, a length in bytes
	and zero out all of the memory; 

	* all operations need to be performed using pointer arithmetic, not
	array indexing; 

	* should return a pointer to the source (src).


uint8_t * my_reverse(uint8_t * src, size_t length);

	* this should take a pointer to a memory location and a length
	in bytes and reverse the order of all of the bytes; 

	* all operations need to be performed using pointer arithmetic,
	not array indexing; 

	* should return a pointer to the source.


int32_t * reserve_words(size_t length);

	* this should take number of words to allocate in dynamic memory;

	* all operations need to be performed using pointer arithmetic,
	not array indexing;

	* should return a pointer to memory if successful, or a Null Pointer
	if not successful.


void free_words(int32_t * src);

	* should free a dynamic memory allocation by providing the pointer
	src to the function; 

	* all operations need to be performed using pointer arithmetic,
	not array indexing.


data.c/data.h Requirements

This file should do some very basic data manipulation.

uint8_t my_itoa(int32_t data, uint8_t * ptr, uint32_t base)

	* Integer-to-ASCII needs to convert data from a standard
	integer type into an ASCII string; 

	* all operations need to be performed using pointer arithmetic,
	not array indexing;

	* the number you wish to convert is passed in as a signed 32-bit
	integer;

	* you should be able to support bases 2 to 16 by specifying
	the integer value of the base you wish to convert to (base).

	* copy the converted character string to the uint8_t* pointer passed
	in as a parameter (ptr);

	* the signed 32-bit number will have a maximum string size
	(Hint: Think base 2);

	* you must place a null terminator at the end of the converted
	c-string;

	* function should return the length of the converted data
	(including a negative sign), example: my_itoa(ptr, 1234, 10) should
	return an ASCII string length of 5 (including the null terminator);

	* this function needs to handle signed data;

	* you may not use any string functions or libraries.


int32_t my_atoi(uint8_t * ptr, uint8_t digits, uint32_t base)

	* ASCII-to-Integer needs to convert data back from an
	ASCII represented string into an integer type;

	* all operations need to be performed using pointer arithmetic,
	not array indexing;

	* the character string to convert is passed in as a
	uint8_t * pointer (ptr);

	* the number of digits in your character set is passed in
	as a uint8_t integer (digits);

	* you should be able to support bases 2 to 16;

	* the converted 32-bit signed integer should be returned;

	* this function needs to handle signed data;

	* you may not use any string functions or libraries.


How To Compile:

1. Add a PATH to bin folder inside the GNU Arm Embedded Toolchain
(9-2019-q4-major release is used for this study):

	export PATH="...:/home/mercury/embedded/gcc-arm-none-eabi-9-2019-q4-major/bin"

2. In the top of course1 folder run:

	make all COURSE1=COURSE1 PLATFORM=HOST for x86

or
	make all COURSE1=COURSE1 PLATFORM=MSP432 for TI MSP432P401R

with more verbosity:

	make all COURSE1=COURSE1 PLATFORM=MSP432 VERBOSE=VERBOSE

	
