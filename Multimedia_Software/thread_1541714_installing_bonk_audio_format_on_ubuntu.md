---
title: "installing bonk audio format on ubuntu"
date: 2010-07-29
forum: Multimedia Software
---

### Post by shantiq on 2010-07-29
trying to install the bonk audio format on my machine but not managing it so far

using the enclosed codec


```
shantiq@shantiq-desktop:~$ cd ./bonk-0.6
shantiq@shantiq-desktop:~/bonk-0.6$ make
g++ -O3 -funroll-loops -o bonk bonk.cc 
In file included from bonk.cc:64:
utility.h: In member function &#8216;int bitstream_in::read()&#8217;:
utility.h:88: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from bonk.cc:65:
wav.h: In function &#8216;void read_wav_header(FILE*, int&, int&, int&)&#8217;:
wav.h:18: warning: deprecated conversion from string constant to &#8216;char*&#8217;
wav.h:19: warning: deprecated conversion from string constant to &#8216;char*&#8217;
wav.h:24: warning: deprecated conversion from string constant to &#8216;char*&#8217;
wav.h:25: warning: deprecated conversion from string constant to &#8216;char*&#8217;
wav.h:38: warning: deprecated conversion from string constant to &#8216;char*&#8217;
wav.h:39: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc: In member function &#8216;void encoder::begin(FILE*, const char*, uint32, uint32, int, bool, bool, int, int, int, double)&#8217;:
bonk.cc:289: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:295: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:297: error: &#8216;strlen&#8217; was not declared in this scope
bonk.cc: In member function &#8216;void decoder::begin(FILE*)&#8217;:
bonk.cc:453: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:459: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:476: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc: In function &#8216;FILE* open_dsp(int, bool)&#8217;:
bonk.cc:546: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:550: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:554: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:557: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc: In function &#8216;bool has_parameter(int&, char**&, char*, char*&)&#8217;:
bonk.cc:564: error: &#8216;strcasecmp&#8217; was not declared in this scope
bonk.cc: In function &#8216;bool has_flag(int&, char**&, char*)&#8217;:
bonk.cc:578: error: &#8216;strcasecmp&#8217; was not declared in this scope
bonk.cc: In function &#8216;void play_file(char*)&#8217;:
bonk.cc:596: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:601: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc: In function &#8216;void do_play(int, char**)&#8217;:
bonk.cc:630: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:632: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc: In function &#8216;void do_decode(int, char**)&#8217;:
bonk.cc:659: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:665: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:669: error: &#8216;strlen&#8217; was not declared in this scope
bonk.cc:670: error: &#8216;strcpy&#8217; was not declared in this scope
bonk.cc:671: error: &#8216;strcasecmp&#8217; was not declared in this scope
bonk.cc:673: error: &#8216;strcat&#8217; was not declared in this scope
bonk.cc:683: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:689: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc: In function &#8216;void do_encode(int, char**)&#8217;:
bonk.cc:733: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:736: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:738: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:740: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:742: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:745: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:746: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:749: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:750: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:753: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:754: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:755: error: &#8216;strcasecmp&#8217; was not declared in this scope
bonk.cc:760: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:761: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:770: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:801: error: &#8216;strlen&#8217; was not declared in this scope
bonk.cc:802: error: &#8216;strcpy&#8217; was not declared in this scope
bonk.cc:803: error: &#8216;strcasecmp&#8217; was not declared in this scope
bonk.cc:805: error: &#8216;strcat&#8217; was not declared in this scope
bonk.cc:813: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:820: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc:849: warning: deprecated conversion from string constant to &#8216;char*&#8217;
bonk.cc: In function &#8216;int main(int, char**)&#8217;:
bonk.cc:889: error: &#8216;strcmp&#8217; was not declared in this scope
make: *** [bonk] Error 1
shantiq@shantiq-desktop:~/bonk-0.6$ 

```


the read file tells you to look at the makefile
i am not sure how to edit it


```

PREFIX=		/usr
CXX=		g++
CXXFLAGS=	-O3 -funroll-loops
INSTALL=	install -c

[COLOR="Red"]# Uncomment this line for Linux and FreeBSD
[/COLOR]LIBS=

# Uncomment this line for NetBSD and OpenBSD
#LIBS=		-lossaudio

all : bonk

bonk : bonk.cc utility.h wav.h
	${CXX} ${CXXFLAGS} -o bonk bonk.cc ${LIBS}

install : bonk
	${INSTALL} bonk ${PREFIX}/bin

clean :
	rm -f core bonk
```


anyone knows how to do this


thnx   shan

---

### Post by shantiq on 2010-08-05
ok so i tried and it would not work
wrote to Paul Harrison who designed it
and there is a kink in the code on bonk-0.6

so i made some lossless bonk files through bonkenc under wine and that went swimmingly then played them through winamp

very nice too

the xmms-bonk plugin knocking around does not seem to work 

so for the other guys who are curious about bonk this is as far as i managed to get

---

### Post by shantiq on 2010-08-06
> **shantiq said:**
> 

the xmms-bonk plugin knocking around does not seem to work 




one needs to add xmms-dev first and i cannot see it anywhere

anyone got that? one that would work with XMMS.1.2.11

thnx   shan

---

### Post by mc4man on 2010-08-06
Here - see how it goes
(otherwise I'll explain how to compile


Edit: best way to dl is to r. click on the attachment - 'save link as'

---

### Post by shantiq on 2010-08-07
thanx man you are a resourceful guy:KS:KS:KS

did /not see that one anywhere on the net. Had you found it a while back ?

anyway

how to proceed place bonk1 in your home folder

1.   ```
cd ./bonk1
```

2.   ```
sudo cp bonk /usr/bin
```

3.   ```
bonk
```

4.    this will appear   ```
[ Bonk lossy/lossless audio compressor (version 0.6) ]

Copyright (C) 2001 Paul Harrison
This is free software distributed under the GNU General Public License.
See the source for further information.

[ Encoding into BONK format ]

  bonk encode [options] file1.wav file2.wav ...

  Options:
    -q n.nn      Set sample quantization level to n.nn
                   (default 1.00)
    -d n         Set downsampling ratio to n:1
                   (default 2, use 1 to disable)
    -s n         Set predictor size to n
                   (default 128, use 10 for speech)
    -m on        Enable middle/side rather than left/right stereo encoding
                   (default)
    -m off       Disable middle/side encoding
    -l           Lossless encoding mode
    -a "Blah"    Specify who the file is by
    -t "Blah"    Specify the title of the file
    -c "Blah"    Include a comment in the file
    -o file.bonk Write output to file.bonk

[ Decoding back to WAV format ]

  bonk decode [options] file1.bonk file2.bonk ...

  Options:
    -o file.wav  Write output to file.wav

[ Playing BONK format files ]

  bonk play [options] file1.bonk file2.bonk ...

  Options:
    -r           Random order
    -l           Loop

```



you now can encode and decode with the bonk format

if you want it lossless and you file is called 2.wav   (it is the letter L not number one)


```
bonk encode -l 2.wav
```




thanx again mc4man

---

### Post by shantiq on 2010-08-07
bonk will play in xmms with the enclosed plugin

does anyone know of other players which will play it too ????


so far i have only found winamp and xmms


also found [bonkenc]("http://www.bonkenc.org/") on my travels which is a really nifty ripper/converter for quite a few formats including bonk and runs perfect under wine

---

### Post by shantiq on 2010-08-07
and if you want to rip a disc to bonk read [here]("http://ubuntuforums.org/showpost.php?p=9689572&postcount=38")

---

### Post by mc4man on 2010-08-07
> did /not see that one anywhere on the net. Had you found it a while back ?

No, it only took a few seconds to build, but because it required installing half a dozen outdated libraries I decided it would be easier to just to attach it for you.
Here's the whole build 'log'
> doug@doug-desktop1:~/Desktop/bonk-0.6$ make
g++-3.3 -O3 -funroll-loops -o bonk bonk.cc 
doug@doug-desktop1:~/Desktop/bonk-0.6$

---

### Post by shantiq on 2010-08-07
i am even more grateful then i would not know how to do that.
can you explain what you had to do if you do not mind?
would love to know


  Cheers.   Shan:KS

---

### Post by mc4man on 2010-08-07
Well - there may have been ways to do otherwise but this seemed the most straightfoward - 

i gathered these packages from [http://packages.ubuntu.com/search?searchon=names&keywords=gcc](http://packages.ubuntu.com/search?searchon=names&keywords=gcc) and put them in a folder I named gcc

> doug@doug-desktop1:~/Desktop/gcc$ ls *.deb
cpp-3.3_3.3.6-15ubuntu4_i386.deb  
gcc-3.3-base_3.3.6-15ubuntu4_i386.deb
g++-3.3_3.3.6-15ubuntu4_i386.deb  
libstdc++5_3.3.6-15ubuntu4_i386.deb
gcc-3.3_3.3.6-15ubuntu4_i386.deb 
libstdc++5-3.3-dev_3.3.6-15ubuntu4_i386.deb


Then I cd'ed to that folder and ran this to install them
```
sudo dpkg -i *.deb
```

After that made a small edit to the Makefile in the bonk source (blue
> PREFIX=		/usr
CXX=		g++[COLOR="Blue"]-3.3[/COLOR]
CXXFLAGS=	-O3 -funroll-loops
INSTALL=	install -c

.....clipped


Then ran make, afterwards to test just copied the bonk binary to a bin in my path - ~/bin here

---

### Post by shantiq on 2010-08-07
ok thanx for that. way beyond my level of knowledge at this point
but it helps understand how things work (one day:KS)

just one question. how do you know these packages > doug@doug-desktop1:~/Desktop/gcc$ ls *.deb
cpp-3.3_3.3.6-15ubuntu4_i386.deb 
gcc-3.3-base_3.3.6-15ubuntu4_i386.deb
g++-3.3_3.3.6-15ubuntu4_i386.deb 
libstdc++5_3.3.6-15ubuntu4_i386.deb
gcc-3.3_3.3.6-15ubuntu4_i386.deb 
libstdc++5-3.3-dev_3.3.6-15ubuntu4_i386.deb


are required



cheers

---

