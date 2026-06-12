---
title: "Help installing JAPA"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by AdrianOfTyriel on 2007-07-11
Hi there, i'm fairly new to linux, and i'm trying to install japa from a make script, but can't seem to get it to work... i get a list of errors like this:

```
g++  -O3 -Wall -MMD -MP -DVERSION=\"0.2.1\" -DPREFIX=\"/usr\" -I/usr/include/freetype2  -c -o analyser.o analyser.cc
In file included from analyser.cc:24:
analyser.h:24:19: warning: fftw3.h: No such file or directory
analyser.h:60: error: ‘fftwf_complex’ has not been declared
analyser.h:61: error: ‘fftwf_complex’ has not been declared
analyser.h:67: error: ‘fftwf_plan’ does not name a type
analyser.h:70: error: ISO C++ forbids declaration of ‘fftwf_complex’ with no type
analyser.h:70: error: expected ‘;’ before ‘*’ token
analyser.cc: In constructor ‘Analyser::Analyser(int, int, float)’:
analyser.cc:45: error: class ‘Analyser’ does not have any field named ‘_fftplan’
analyser.cc:51: error: ‘fftwf_malloc’ was not declared in this scope
analyser.cc:52: error: ‘_trdata’ was not declared in this scope
analyser.cc:52: error: ‘fftwf_complex’ was not declared in this scope
analyser.cc:52: error: expected primary-expression before ‘)’ token
analyser.cc:52: error: expected `;' before ‘fftwf_malloc’
analyser.cc: In destructor ‘Analyser::~Analyser()’:
analyser.cc:60: error: ‘_fftplan’ was not declared in this scope
analyser.cc:60: error: ‘fftwf_destroy_plan’ was not declared in this scope
analyser.cc:63: error: ‘_trdata’ was not declared in this scope
analyser.cc:63: error: ‘fftwf_free’ was not declared in this scope
analyser.cc: In member function ‘void Analyser::set_fftlen(int)’:
analyser.cc:74: error: ‘_fftplan’ was not declared in this scope
analyser.cc:74: error: ‘fftwf_destroy_plan’ was not declared in this scope
analyser.cc:76: error: ‘_fftplan’ was not declared in this scope
analyser.cc:76: error: ‘_trdata’ was not declared in this scope
analyser.cc:76: error: ‘FFTW_ESTIMATE’ was not declared in this scope
analyser.cc:76: error: ‘fftwf_plan_dft_r2c_1d’ was not declared in this scope
analyser.cc: At global scope:
analyser.cc:109: error: ‘float Analyser::conv0’ is not a static member of ‘class Analyser’
analyser.cc:109: error: ‘fftwf_complex’ was not declared in this scope
analyser.cc:109: error: ‘v’ was not declared in this scope
analyser.cc:110: error: expected ‘,’ or ‘;’ before ‘{’ token
analyser.cc:119: error: ‘float Analyser::conv1’ is not a static member of ‘class Analyser’
analyser.cc:119: error: ‘fftwf_complex’ was not declared in this scope
analyser.cc:119: error: ‘v’ was not declared in this scope
analyser.cc:120: error: expected ‘,’ or ‘;’ before ‘{’ token
analyser.cc: In member function ‘void Analyser::process(int, bool)’:
analyser.cc:185: error: ‘_fftplan’ was not declared in this scope
analyser.cc:185: error: ‘fftwf_execute’ was not declared in this scope
analyser.cc:188: error: ‘_trdata’ was not declared in this scope
analyser.cc:201: error: ‘_trdata’ was not declared in this scope
analyser.cc:212: error: ‘_trdata’ was not declared in this scope
analyser.cc: At global scope:
analyser.cc:232: fatal error: opening dependency file analyser.d: Permission denied
compilation terminated.
make: *** [analyser.o] Error 1

```



Any help would be greatly appreciated.

---

