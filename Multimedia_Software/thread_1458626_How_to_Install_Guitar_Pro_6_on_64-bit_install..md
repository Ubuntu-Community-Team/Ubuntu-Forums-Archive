---
title: "How to Install Guitar Pro 6 on 64-bit install."
date: 2010-04-20
forum: Multimedia Software
---

### Post by Lennon V C on 2010-04-20
1) Download the latest .deb from Guitar Pro's website.
2) Goto [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) and install getlibs-all.deb
3) Run this in terminal
> sudo dpkg -i --force-architecture Downloads/GuitarPro6-r7840.deb You will get some errors but ignore.
4) Run this in terminal > getlibs  /opt/GuitarPro6/GuitarPro


---

### Post by jdeleski on 2010-05-02
Hi Lennon VC,
thanks for posting this solution.
It also worked great with the newest GP6 version GuitarPro6-rev7894 running Ubuntu 9.10 Karmic Koala.
I have upgraded my OS to the Ubuntu version 10.04 Lucid Lynx and GP6 seems to work fine.
:guitar:

---

### Post by beeno on 2010-05-03
aye buddy, just wanted to post and say thanks for this.
i've been using 32 bit ubuntu for years now but i've only really dabbled into 64 bit since lucid (less than a month after the gp release, i was bummed when it wouldn't work at first hahaha, paying all that money :()

woo!
beeno. x

---

### Post by beeno on 2010-05-04
ok, i had tried it on rc1 and it worked fine.
i did a clean install of the final release of lucid and it doesn't work, crashes during the splash screen.

just wanna add to some people that i had to install libportaudio0
```
sudo apt-get install libportaudio0
```

getlibs didn't install this, i had to install that for it to work on rc1, i believe before the installation too.

however this didn't work on the final, i'll keep trying!

---

### Post by ror191505 on 2010-05-06
> **Lennon V C said:**
> 1) Download the latest .deb from Guitar Pro's website.
2) Goto [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) and install getlibs-all.deb
3) Run this in terminal
 You will get some errors but ignore.
4) Run this in terminal

could you upload exactly GuitarPro6-r7840.deb anywhere please? i need this version but not newer

---

### Post by nilsolaris on 2010-05-19
The newest version of GuitarPr6 [GuitarPro6Demo-rev7994.deb] is still asking for the serial. Do you any more information on this update? Or is there a possible way to find the older packages?

---

### Post by Lennon V C on 2010-05-26
Sorry mate, you need to purchase a serial; Tuxguitar is the open alternative. I just tried the newest version(7994) on a clean install of 10.04 and it seemed to work fine. Every version past and present of GP6 needs a serial.

---

### Post by HyperFlexed on 2010-07-10
This was working a month ago, now it's broken. You can always count on Canonical to mess up sound. I've had it with linux sound, really. TuxGuitar, AND Powertab (via wine) are also failing to produce sound. This pisses me off.

---

### Post by bloozguy on 2010-10-06
I am running 10.4 LTS on a quad AMD64 box.
I downloaded the trial version  for Linux (GuitarPro6Demo-rev8569.deb) 
I did the getlib bit which seemed to get just one lib.

When I start it up I get :

```
/opt/GuitarPro6/gp-launcher.sh
Please make sure you're running a composition manager!
Found ARGB visual. Starting app...
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device 
```

 When I try a File/Import/*option*
nothing at all happens even though the options have the appearance of being active.


When I try File/New/Empty I get :
```
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device
0 ms
8 ms
[RENDERER] UpdateAll : 9ms
[RENDERER] UpdateAll : 0ms
[RENDERER] UpdateAll : 0ms
[RENDERER] UpdateAll : 0ms
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device
QTextStream: No device


``` 

I don't know how to make it go for the 32 bit library.


When I try Bar/System layout ... and pick either option I get :

```
ASSERT failure in QVector<T>::operator[]: "index out of range", file /home/arobas/qtsdk-2010.02/qt/include/QtCore/qvector.h, line 346
Aborted

```

Not looking good :guitar:

---

### Post by Finn bjerke on 2010-12-27
I gave up and downgraded my 64 bits tl 32 bits in order to use Guitar Pro 6. I works well except for file import. The programme can not import tabledit files. Midi file are OK.

---

### Post by wicki on 2011-05-13
Hi I have followed the thread here and installed GP6 on my system, it appears in the menu but when I start it I get the initial splash screen and then nothing ...I am totally new to Ubuntu and if GP wont run its back to Winblows ...any ideas what may be wrong?

---

### Post by arkeyn on 2011-05-26
```
sudo /usr/bin/getlibs /opt/GuitarPro6/GuitarPro 
No match for libportaudio.so.2
No packages to install

```

help plz.
though I'm newbee using Linux Mint 10 x64, but it's ubuntu based.

---

### Post by wicki on 2011-05-26
Hi sorry I am not really sure what your asking ...but then i know next to nothing about linux....I reverted to a 32 bit install and all my problems disappeared...I don't really need 64 bit for anything I am aware of so it was the easiest solution.

---

### Post by arkeyn on 2011-05-26
> **wicki said:**
> Hi sorry I am not really sure what your asking ...but then i know next to nothing about linux....I reverted to a 32 bit install and all my problems disappeared...I don't really need 64 bit for anything I am aware of so it was the easiest solution.
  trying to use getlibs utility to get some libraries to start Guitar Pro 6, but I get no match output.
though somebody could help to install missing library manually or something else to get it started.

---

### Post by bloozguy on 2011-05-26
SEE ALSO [http://ubuntuforums.org/showthread.php?p=10865630#post10865630:(](http://ubuntuforums.org/showthread.php?p=10865630#post10865630:()

---

### Post by bloozguy on 2011-06-22
Finally got it to work after I got ahold of the GP people.

The solution is to dumb down the 32 bit libraries for any version of Ubuntu newer than Maverick.

"It seems a bug in the latest ia32-libs causes some trouble to applications that uses 32bit libraries (GP6 use 32 bit libraries too).

A workaround exists, simply downgrade the ia32-libs package.

Follow these guidelines to downgrade ia32:
- download the package from this page [http://packages.ubuntu.com/maverick/...-libs/download](http://packages.ubuntu.com/maverick/...-libs/download)
- run a terminal and go to the directory where the .deb is stored
- execute this command line: sudo dpkg --force-downgrade -i ia32-libs_20090808ubuntu9.1_amd64.deb "

---

### Post by arthur.duarte on 2011-07-25
This worked for me smoothly =)

Thank You very much.

---

### Post by yggdrasyl on 2012-01-14
> **Lennon V C said:**
> 1) Download the latest .deb from Guitar Pro's website.
2) Goto [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/) and install getlibs-all.deb
3) Run this in terminal
 You will get some errors but ignore.
4) Run this in terminal

Very usefull on my 10.04LTS x64!
Thanks!
Pasquale

---

### Post by SiDas on 2012-02-29
> **arkeyn said:**
> ```
sudo /usr/bin/getlibs /opt/GuitarPro6/GuitarPro 
No match for libportaudio.so.2
No packages to install

```help plz.
though I'm newbee using Linux Mint 10 x64, but it's ubuntu based.

After installing getlibs and updating GP 32bit dependencies and downgrading the ia32 libs 
I also had this issue as well as a wrong ELF CLASS for libportaudio2 error when trying to run GP
I fixed it by using getlibs to fix the libportaudio 32bit depencies
I did this for libportaudio0 and libportaudio2 but was probably only necessary for 2

$ getlibs - p libportaudio2
I don't know if downgrading the ia32 package was necessary as it was the command above that finally fixed.

So in summary (all as root so su or sudo): download required debs (had to google for getlibs)
Force install of 32 bit package (some error messages) - 
$ sudo dpkg -i --force-architecture Downloads/gp6-full-linux-demo-r10558.deb
installed getlibs using package manager (just click deb)
$ getlibs /opt/GuitarPro6/GuitarPro
$ sudo dpkg --force-downgrade -i Downloads/ia32-libs_20090808ubuntu9.1_amd64.deb
$ getlibs - p libportaudio0
$ getlibs - p libportaudio2

Hope this helps somebody:p

---

### Post by BFris on 2012-07-07
Ladies, forget about getlibs. At least for 12.04 (precise).

  1. install ia32-libs (sudo apt-get install ia32-libs)
  2. edit the deb file for guitar pro 6 to REMOVE the 
     gksu dependency. Check out this forum post for a script:
     [http://ubuntuforums.org/showthread.php?t=636724]("http://ubuntuforums.org/showthread.php?t=636724")
  3. install guitarpro (sudo dpkg -i <modified debfile>.deb)

shazam. now you're rocking!

---

### Post by exo88 on 2012-07-16
> **BFris said:**
> Ladies, forget about getlibs. At least for 12.04 (precise).

  1. install ia32-libs (sudo apt-get install ia32-libs)
  2. edit the deb file for guitar pro 6 to REMOVE the 
     gksu dependency. Check out this forum post for a script:
     [http://ubuntuforums.org/showthread.php?t=636724]("http://ubuntuforums.org/showthread.php?t=636724")
  3. install guitarpro (sudo dpkg -i <modified debfile>.deb)

shazam. now you're rocking!

Hi Bfris, can you please explain to a noob like me, how to run the script to remove gksu dependencies? Thank you :D

---

### Post by Nat135 on 2012-09-18
I have exact the same problem always when I'm trying to install GuitarPro6 on 12.04 (64bit) the error appears: "gksu:i386 can not be installed" 
what can I do now? 
When I try to install this gksu:i386 from the Software Center it says this:

"gksu:i386: Depends: libc6 (>= 2.3.6-6~) aber 2.15-0ubuntu10 soll installiert werden
           Depends: libgksu2-0 (>= 2.0.8) aber 2.0.13~pre1-5ubuntu2 soll installiert werden
           Depends: libglib2.0-0 (>= 2.16) aber 2.32.3-0ubuntu1 soll installiert werden
           Depends: libgtk2.0-0 (>= 2.8.0) aber 2.24.10-0ubuntu6 soll installiert werden"

libc6 etc but 2.15 shall be installed :(

I don't know; where is the problem, it seems my software is up to date :(
Please help me, I don't work very long with Ubuntu and that's the only program I can't use

---

