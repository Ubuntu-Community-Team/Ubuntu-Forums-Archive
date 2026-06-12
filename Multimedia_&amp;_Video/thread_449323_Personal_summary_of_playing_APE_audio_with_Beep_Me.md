---
title: "Personal summary of playing APE audio with Beep Media Player"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by chunchengch on 2007-05-20
I surveyed many threads and websites, and finally I successfully enable Beep Media Player (BMP) to play APE audio in my laptop, now I am enjoying the beauty of piano. 

Here are the complete processes, wish it will be helpful!


**1.Install Beep Media Player and necessary packages:**

sudo apt-get install beep-media-player
sudo apt-get install beep-media-player-dev
sudo apt-get install build-essential
sudo apt-get install nasm
sudo apt-get install libgtk2.0-0
sudo apt-get install libglib2.0-dev
sudo apt-get install gcc-3.4

PS: all these packages can be installed in **Synaptic**

**2.Download, extract and install the MAC libs:**

[ATTACH]32995[/ATTACH]

cd /home/YOURLOGINNAME/Desktop
sudo tar zxvf mac-3.99-u4-b5.tar.gz

cd /home/YOURLOGINNAME/Desktop/mac-3.99-u4-b5
./configure --enable-assembly 
make 
sudo make install

**3.Download, extract and install the BMP MAC plugin:**

[ATTACH]32996[/ATTACH]

cd /home/YOURLOGINNAME/Desktop
sudo tar zxvf bmp-mac-0.1.1.tar.gz

cd /home/YOURLOGINNAME/Desktop/bmp-mac-0.1.1
./configure --enable-local=yes 
make 
sudo make install

**4.Exit terminal and press ctrl+alt+backspace to restart X windows, then launch Beep Media Player and check if "Monkey's Audio Codec Player 0.1.1" is enabled in BMP preferences>plugins>media, if it is, congratulation and enjoy APE:**

[ATTACH]32997[/ATTACH]

---

### Post by chunchengch on 2007-05-20
_Adding CUE plugin_

**5.Download, extract and install the BMP CUE plugin: **
[ATTACH]33005[/ATTACH]

cd /home/YOURLOGINNAME/Desktop
sudo tar jxvf  bmp-cueinfo-0.2.0.tar.bz2

cd /home/YOURLOGINNAME/Desktop/ bmp-cueinfo-0.2.0
./configure 
make 
sudo make install

**6.Check if "Cue Info 0.2.0" is enabled in BMP Preferences>Plugins>General, then press ctrl+alt+backspace to restart X windows**
[ATTACH]33006[/ATTACH]

---

### Post by murmansky on 2007-05-22
Great!!! It works!!  :D:D:D
I had tried to play ape files for two days with no result, trying to install Gstreamer plugins!!! :(:(:(

I'm a newbie, so maybe I'm making some mistakes....
But I have this problem:
the .cue plugin diplays track titles but with a huge .ape file and a .cue one, in Beep Media Player I can't choose tracks and jump back an forward like I used to do in windoz with foobar2000.
Do you know how could I do it?
Thanks :p

---

### Post by chunchengch on 2007-05-22
murmansky,

Glad it works for you!

I am a newbie too, as I know for the time being it is still unsolved to play cue directly with BMP.

---

### Post by murmansky on 2007-05-23
Thank you very much! :p

---

### Post by malonggood on 2007-06-04
Oh!!!It's working!!!Thanks very much!!!;););)

---

### Post by ariel on 2007-07-07
All,

  is the cue plugin working for you? I just followed the instructions above; BMP works perfectly and can now play .ape with no problem, but it doesn't recognize the .cue.

  The CUE plugin does show up in the "General" plugin configuration tab; it appears unchecked; I check it, then close BMP, then restart X, reload BMP, it shows as disabled again. Also tried enabling the pluging, then restarting X right away, same problem. The plugin does not seem to work.

Any hint, anyone?

Thanks!

---

### Post by murmansky on 2007-08-09
Hi Ariel,
I've some problems too.... the .cue plugin only displays general information, but I can't choose the desired tracks for playback.
In Win I used foobar2000 (for playback) and burrrn (for burning) and I can't find something similar (and easy to use) in Linux.
For playback I'll try to install foobar under Wine... 

bye
mur

---

### Post by Gabix on 2008-01-25
Thanks, APE works great! I also like this player. 
But do you know now how to get the flacs working? 
I'm completely new to Ubuntu or any kind of Linux, It's been only 3 days since I've installed it and I'm constantly moving through this great forum trying to know what am I doing to make thinghs work.

---

### Post by ariel on 2008-01-25
I just installed the latest version of audacious (1.4.5), by adding morgoth's repo. 

Instructions here:
[http://morgoth.free.fr/ubports/](http://morgoth.free.fr/ubports/)

I installed audacious, plugins, plugins-extra, plugins-ugly. 

The result can play flacs with no problem.

---

### Post by Gabix on 2008-01-25
Audacius works with Flac, also totem. But my problem is that I can't play Ape now in those two, only with Beep MP. And in this late one I can't play flac. What I want is an unified player. And if possible an explanation on how to install the codecs to all the players, like in winXP. I'm sure there's a way, only that in my totally limited experience It escaped me.

PD. I did install the morgoth repo, but maybe in a wrong way... This is what I did:

In a terminal:
gksudo gedit /etc/apt/sources.list

> there I added:

## Morgoth Repository
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) gutsy-backports main 
#deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) gutsy-backports main

-- (I have the 7.10 gutsy for AMD64) 
> I saved and again in the terminal I inputed the signing key:

wget -O - [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc) | sudo apt-key add -

> and after:

sudo aptitude update
> &
sudo aptitude upgrade

> finally from applications > add remove > I checked Audacius and Installed it

PD2. Ariel: Guille siempre fue mi preferido de Mafalda!!

---

### Post by ariel on 2008-02-02
Gabix, once you have the repo on, the "audacious-mac" package (mac = monkey's audio codec). It should show up in synaptics (version 0.3.10) if morgoth's repo was correctly added. 

After that, launch audacious and check in Preferences > Plugins > Decoders,
 you shoud see the entry for "Monkey's audio codec player" activated. Normally you would also need the CUE Sheet plugin present and activated too.


~~ aguante mafalda a full ~~ :)

---

### Post by Gabix on 2008-02-03
I can't see it neither in synaptic and -obviously- in plugins in audacious. I have all the software repositories available in synaptic, but now this is what it says:
**[http://morgoth.free.fr/ubuntu/dists/gutsy-backports/Release:](http://morgoth.free.fr/ubuntu/dists/gutsy-backports/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)**

Maybe morgoth doesn't supports 64bits... Or I made something wrong...

---

### Post by drorata on 2008-02-13
Work great for me.

There's only one thing I'd like to point out - At first run, once I tried to play audio in BeepPlayer it crashed. No matter if it was .APE or .MP3. I resolved it by choosing "OSS output plug in" instead of the default "ALSA 0.9.7". Once I changed it it works great!

Thanks a lot!!!

Dror

---

### Post by disturbedite on 2008-02-13
i prefer audacious, which has an ape plugin available for it already...no compilation necessary if you use a repo that has it available.
but then again, i prefer flac.  i think its better (not in terms of quality tho).

---

### Post by Josep Lluis on 2008-06-17
Hi,

I'm new in Linux/Ubuntu, and English is not my first language.

executing ./configure mac-3.99-u4-b5 --enable-assembly  gives this error:

configure:2076: checking for C++ compiler version
configure:2079: g++ --version </dev/null >&5
/home/ubuntu/Escritorio/mac-3.99-u4-b5/configure: line 2080: g++: command not found
configure:2082: $? = 127
configure:2084: g++ -v </dev/null >&5
/home/ubuntu/Escritorio/mac-3.99-u4-b5/configure: line 2085: g++: command not found
configure:2087: $? = 127
configure:2089: g++ -V </dev/null >&5
/home/ubuntu/Escritorio/mac-3.99-u4-b5/configure: line 2090: g++: command not found
configure:2092: $? = 127
configure:2115: checking for C++ compiler default output file name
configure:2118: g++  -O3 -Wall -pedantic -Wno-long-long   conftest.cc  >&5
/home/ubuntu/Escritorio/mac-3.99-u4-b5/configure: line 2119: g++: command not found
configure:2121: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "mac"
| #define PACKAGE_TARNAME "mac"
| #define PACKAGE_VERSION "3.99-u4-b5"
| #define PACKAGE_STRING "mac 3.99-u4-b5"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "mac"
| #define VERSION "3.99-u4-b5"
| /* end confdefs.h.  */
| 

any help?

Thanks

---

### Post by ariel on 2008-06-17
> **Josep Lluis said:**
> Hi,

I'm new in Linux/Ubuntu, and English is not my first language.

executing ./configure mac-3.99-u4-b5 --enable-assembly  gives this error:

configure:2076: checking for C++ compiler version
configure:2079: g++ --version </dev/null >&5
/home/ubuntu/Escritorio/mac-3.99-u4-b5/configure: line 2080: g++: command not found
configure:2082: $? = 127
configure:2084: g++ -v </dev/null >&5
/home/ubuntu/Escritorio/mac-3.99-u4-b5/configure: line 2085: g++: command not found
configure:2087: $? = 127
configure:2089: g++ -V </dev/null >&5
/home/ubuntu/Escritorio/mac-3.99-u4-b5/configure: line 2090: g++: command not found
configure:2092: $? = 127
configure:2115: checking for C++ compiler default output file name
configure:2118: g++  -O3 -Wall -pedantic -Wno-long-long   conftest.cc  >&5
/home/ubuntu/Escritorio/mac-3.99-u4-b5/configure: line 2119: g++: command not found
configure:2121: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "mac"
| #define PACKAGE_TARNAME "mac"
| #define PACKAGE_VERSION "3.99-u4-b5"
| #define PACKAGE_STRING "mac 3.99-u4-b5"
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "mac"
| #define VERSION "3.99-u4-b5"
| /* end confdefs.h.  */
| 

any help?

Thanks

You need to install the basic tools for compiling stuff. / tenes que instalar los compiladores:

```
sudo apt-get install build-essential
```Puede ser que tambien te falten librerias; ./configure te va a decir cuales.

---

### Post by Josep Lluis on 2008-06-20
Ariel,

He instalado MAC para poder usar audio-convert, y ha funcionado sin problemas con las instrucciones que me diste. 
Gracias

---

### Post by Arrgoss on 2008-06-21
Hi,

I know this is a bit off-topic, but does anyone know how to install the mac libraries in a AMD 64 architecture?

---

### Post by ariel on 2008-06-22
> **Arrgoss said:**
> Hi,

I know this is a bit off-topic, but does anyone know how to install the mac libraries in a AMD 64 architecture?


Just follow the build/recompiling instructions above, they work fine in amd64 as well. 

Not sure if it was already noted in this thread, but to play .ape files there is a new option. Recently Audacious ([http://audacious-media-player.org](http://audacious-media-player.org)) added out-of-the-box MAC support, their team wrote a plugin from scratch and included it in their extra plugins, which does not require libmac any more. This is in Audacious 1.5 which ships with Hardy. 

However the 1.5 implementation has some limitations (refuses to play certain .ape files), which are fully fixed in 1.5.1, but there are no debs of it yet. (Here's a workaround for hardy's version: [https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/211908](https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/211908))

Also it seems a new gstreamer plugin implementation is in the works.

---

### Post by murmansky on 2008-07-13
I know it's off-topic, but I'd like to tell you what I've done in the end (after using Audacious with Morgoth repositories for some times).

The definitive solution, for me, was installing xbmc. 

It only requires an OpenGL 2.0 video card and it can read _everything_ (ape, flac, cue, 3gp, MKV, etc.) and it has a lot of plugins!

It works perfectly and in the official forum you can find also precompiled builds 

[http://xbmc.org/forum/showthread.php?t=33327](http://xbmc.org/forum/showthread.php?t=33327)

which make installing xbmc easy using 
"sudo apt-get update" and then "sudo apt-get install xbmc"

Have fun! 
Probably this is the best way for managing all multimedia formats under Linux with no problem.
Bye

---

