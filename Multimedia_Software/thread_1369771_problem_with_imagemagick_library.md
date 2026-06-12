---
title: "problem with imagemagick library"
date: 2010-01-01
forum: Multimedia Software
---

### Post by slience on 2010-01-01
i try to compile this program with gcc:
```
#include <ImageMagick/Magick++.h>
#include <iostream>

using namespace std;
using namespace Magick;

int main(int argc, char *argv[])
{
	// Declaring variables
	Image mybitmap;
	
	try {
		// Read a file into image object
    		mybitmap.read( "pic.gif" );
  	}
  	catch( Exception &error_ )
    	{
		cout << "Caught exception: " << error_.what() << endl;
		return 1;
    	}

	return 0;
}
```
But it's return me this errors:
```
mhossein@mhossein-desktop:~/Documents/Image Processing$ g++ 1.c -o "1.o"
/tmp/ccEL4VcO.o: In function `main':
1.c:(.text+0x13): undefined reference to `Magick::Image::Image()'
1.c:(.text+0x4f): undefined reference to `Magick::Image::read(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
1.c:(.text+0x11f): undefined reference to `Magick::Image::~Image()'
1.c:(.text+0x137): undefined reference to `Magick::Image::~Image()'
/tmp/ccEL4VcO.o:(.gcc_except_table+0x2c): undefined reference to `typeinfo for Magick::Exception'
collect2: ld returned 1 exit status

```
Can everybody help me?

---

