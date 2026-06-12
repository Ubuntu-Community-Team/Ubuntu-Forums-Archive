---
title: "[SOLVED] Soundblaster 16 working in Dapper 6.06LTS"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by antmenj on 2007-02-05
Being a linux newcomer I'v spent more time than I'd care to mention sorting this out.  Every sentence I read was full of stuff I didn't understand and needed more research but in the end I'v got there so hope this may help some of you before you tare your hair out.

Software: Ubuntu 6.06LTS but may apply to other variants.

Sound card in question:
CT2960 but probebly applys to many others listed here with the "sb16 chipset" as showen at the following.
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix")

Problem:
Sound card wasn't auto detected on instalation and / or boot up thus no sound.

Solution:
1 Open Applications >Accessories >Terminal
A box will appear with a command prompt.
2 At the command prompt type  ```
sudo nano /etc/modules
```  Press enter
You will be asked for a password - use your login pass word and press enter
3a  Another box will open and there will be a number of lines of text.
3b Useing the arrow key move the curser to the line bellow the last text line (not the 2 lines at the bottom of the box with lots of "^" and letters.)
Type ```
snd-sb16
```
Hold down the Ctrl key and press the "O" (letter O) key to save the file.
4 Close the window with your mouse and the "X" icon in the top corner.
5 Repeat steps 1 to 3a to check if the extra line you entered was saved.  If it was good if not try again maybe
6 Close all programs and reboot the computer
7 Play a sound file to see what happens.  I used an MP3 and totom and also XMMS (xmms is an extra download).

If still no joy have a look at [LordRaiden's Sound guide]("http://www.ubuntuforums.org/showthread.php?t=205449").  It may pay to skip his item 2 as it only applys to PCI cards (the ones in the 8.5 centermeter white socket) not ISA (the older cards that go in the 14 cetermeter black socket) .

---

### Post by yabbadabbadont on 2007-02-05
If it is an ISA card, you probably need to use the isapnptools package to initialize the card correctly.  At least that is what I used to do with my sb16 back in the 2.0 and 2.4 kernel days.  I had to do the same thing with my ISA SB-AWE64 card too.

---

### Post by antmenj on 2007-09-20
Well time has passed I'v found my above solution dosn't **always** work at boot so I just tryed ```
sudo apt-get install isapnptools
``` and I get "Package not found".  

2 Questions

1 How do I get isapnptools installed?

2 How does "apt-get" know where to get apt-get from & do I need to steer it elseware some how?

I'v just done a new install on a biger drive and havn't got updates yet as bandwidth is more abundant off peak.

---

### Post by yabbadabbadont on 2007-09-20
1) It must not be supported/needed with 2.6 kernels as I can't find it anywhere in the repositories.

2) /etc/apt/sources.list tells apt where to find its repositories.

Edit: Here is the project page for it: [http://www.roestock.demon.co.uk/isapnptools/](http://www.roestock.demon.co.uk/isapnptools/)

It doesn't get a lot of activity since motherboards with an ISA bus are becoming quite rare.

---

### Post by antmenj on 2007-09-20
Ok have had a look in the /etc/apt/sources.list and copyed some URLs into firefox to have a bit of a look at whats there.

I take it *.gz files are what get used for installs.

Have also had a bit of a read of the isapnptools site.

Should I be compiling (however thats done) for ubuntu or downloading a .gz file from the debian repos or enable debian repos in the above file from here?

[http://packages.debian.org/sarge/isapnptools/i386/filelist](http://packages.debian.org/sarge/isapnptools/i386/filelist)

PS thanks for the reply above after this long:):)

---

### Post by yabbadabbadont on 2007-09-20
> **antmenj said:**
> Ok have had a look in the /etc/apt/sources.list and copyed some URLs into firefox to have a bit of a look at whats there.There will be a lot of stuff there that you won't/can't use as packages for different architectures will be there.  x86, x86_64, ppc, ...

> **antmenj said:**
> I take it *.gz files are what get used for installs.No, the *.deb files are the native packages for Debian based linux distributions.  (of which, Ubuntu is one)

> **antmenj said:**
> Have also had a bit of a read of the isapnptools site.

Should I be compiling (however thats done) for ubuntu or downloading a .gz file from the debian repos or enable debian repos in the above file from here?

[http://packages.debian.org/sarge/isapnptools/i386/filelist](http://packages.debian.org/sarge/isapnptools/i386/filelist)Probably you would want the deb from the Debian sid repository.  No guarantees though.

> **antmenj said:**
> PS thanks for the reply above after this long:):)No problem.  I just wish that I could remember more about how I configured my sp16/sbawe64 cards in the past.  It could be that you could specify the correct IRQ, DMA, and Base address as parameters passed when the kernel module for the card is loaded.  (via the /etc/modprobe.d/options file)  It has just been too long since I used one to remember all the details.

---

### Post by antmenj on 2007-09-24
Have looked into the mater a bit more and done a bit more investigation.  Found this:
```
cat /proc/interrupts
```.  The card is consistantly on IRQ5.  The above regarding it working intermitantly is... well.... not stricktly true perhaps. :oops:

What,it seems is happening is that XMMS is intermitantly saying that the sound card is incorectly configured or in use by another app.  Movie player & Rytham box always seem to be able to play ogg sound.

---

### Post by antmenj on 2007-10-15
Well finaly fitted a PCI card and removed the above line.  Solved in one way:) and defeated in another :( .

For others info I got Rytham Box and Movie player (on audio files) working fine on the SB16 but other audio programs like xmms or beep are a no go with the current updates :(

---

