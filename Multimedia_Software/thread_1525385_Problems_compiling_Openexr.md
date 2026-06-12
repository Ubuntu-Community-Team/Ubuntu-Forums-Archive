---
title: "Problems compiling Openexr"
date: 2010-07-06
forum: Multimedia Software
---

### Post by cogvos on 2010-07-06
Dear all I am haveing odd problems compiling Openexr in Ubuntu 9.10.

./configue works OK but the make fails with 

Making all in exrmaketiled
make[1]: Entering directory `/home/john/Desktop/openexr-1.6.1/exrmaketiled'
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -I.. -I../IlmImf -I../config -pthread -I/usr/local/include/OpenEXR     -pipe -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:213: error: &#8216;strcmp&#8217; was not declared in this scope
make[1]: *** [main.o] Error 1
make[1]: Leaving directory `/home/john/Desktop/openexr-1.6.1/exrmaketiled'
make: *** [all-recursive] Error 1

strcmp not declared in this scope?? What on Earth does that mean? ./configue picked up string.h ok. I am trying (and failing) to compile OpenEXR 1.6.1 from [http://www.openexr.com/downloads.html](http://www.openexr.com/downloads.html).

Any ideas? I cannot find an Openexr package using synaptic and want to try out cinepaint (which needs it)

---

### Post by cogvos on 2010-07-06
Hmmm Just tried the 1.4 version and this failed as well complaining about all the file functions...

reating libIlmImf.la
(cd .libs && rm -f libIlmImf.la && ln -s ../libIlmImf.la libIlmImf.la)
make[1]: Leaving directory `/home/john/Desktop/openexr-1.4.0/IlmImf'
Making all in IlmImfTest
make[1]: Entering directory `/home/john/Desktop/openexr-1.4.0/IlmImfTest'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/john/Desktop/openexr-1.4.0/IlmImfTest'
Making all in exrdisplay
make[1]: Entering directory `/home/john/Desktop/openexr-1.4.0/exrdisplay'
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -I/usr/include/freetype2 -D_THREAD_SAFE -D_REENTRANT -I.. -I../Iex -I../Half -I../Imath -I../IlmImf -I../config   -pipe -g -O2 -pthread -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
	then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -I/usr/include/freetype2 -D_THREAD_SAFE -D_REENTRANT -I.. -I../Iex -I../Half -I../Imath -I../IlmImf -I../config   -pipe -g -O2 -pthread -MT ImageView.o -MD -MP -MF ".deps/ImageView.Tpo" -c -o ImageView.o ImageView.cpp; \
	then mv -f ".deps/ImageView.Tpo" ".deps/ImageView.Po"; else rm -f ".deps/ImageView.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../config -I/usr/include/freetype2 -D_THREAD_SAFE -D_REENTRANT -I.. -I../Iex -I../Half -I../Imath -I../IlmImf -I../config   -pipe -g -O2 -pthread -MT ImageViewFragShader.o -MD -MP -MF ".deps/ImageViewFragShader.Tpo" -c -o ImageViewFragShader.o ImageViewFragShader.cpp; \
	then mv -f ".deps/ImageViewFragShader.Tpo" ".deps/ImageViewFragShader.Po"; else rm -f ".deps/ImageViewFragShader.Tpo"; exit 1; fi
ImageViewFragShader.cpp: In member function ‘void ImageViewFragShader::loadFragShaderFromFile()’:
ImageViewFragShader.cpp:255: error: ‘fopen’ was not declared in this scope
ImageViewFragShader.cpp:262: error: ‘fseek’ was not declared in this scope
ImageViewFragShader.cpp:263: error: ‘ftell’ was not declared in this scope
ImageViewFragShader.cpp:268: error: ‘fread’ was not declared in this scope
ImageViewFragShader.cpp:284: error: ‘fclose’ was not declared in this scope
ImageViewFragShader.cpp:290: error: ‘fclose’ was not declared in this scope
make[1]: *** [ImageViewFragShader.o] Error 1
make[1]: Leaving directory `/home/john/Desktop/openexr-1.4.0/exrdisplay'
make: *** [all-recursive] Error 1

Ugh!

---

### Post by Yellow Pasque on 2010-07-06
Make sure you have build-essential package installed.

---

### Post by cogvos on 2010-07-06
> **Temüjin said:**
> Make sure you have build-essential package installed.

Sorry I don't understand. Please explain what you mean by 'build-essential' The compile appears to be failing to find basic c headers (stdio, string etc). I haven't checked the sources yet but they wouldn't release without checking something like that, would they?

---

### Post by Yellow Pasque on 2010-07-06
Open Synaptic and find build-essential or:
```
sudo apt-get install build-essential
```

---

