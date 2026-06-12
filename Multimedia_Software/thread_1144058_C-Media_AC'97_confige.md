---
title: "C-Media AC'97 confige"
date: 2009-04-30
forum: Multimedia Software
---

### Post by gabrielshier on 2009-04-30
Hey,
New to ubuntu and quiet a noob. Just found my motherboard drivers CD. What is want is to have a software which will make my 'mic' and 'input' audio jacks into an output for a 5.1 sound system. C-Media has a wonderfull software for doing that. Also, i have the linux drivers for it. 
The Readme file says:
```
Step 1. unzip source code

        tar xfvj alcsound.tar.bz2



Step 2. Turn on sound support (soundcore module, default turn on)



Step 3. Complied source code

	a. ./configure

	b. make

	c. make install

	d. ./snddevices

```

First step went fine. Step 2 - have not idea what does that mean. 
Step three got: 
```
gabriels@gabriels-desktop:~/Desktop/2-do/untitled folder/alsa-test-0.9.4$ ./configure
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for a BSD compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/gabriels/Desktop/2-do/untitled folder/alsa-test-0.9.4
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.28-11-generic/build
checking for kernel version... 0.0.0
checking for GCC version... ./configure: 2735: Bad substitution

```

Have any idea why? Tried reinstalling gcc. Still won't work. Any idea what can i do, or if there is a good software to replace the C-Media one which will do the same job?
Thanks,
Gabi

---

### Post by psyke83 on 2009-04-30
Are you sure it's necessary to install this software? Perhaps ALSA or PulseAudio can replicate the functionality you need.

---

### Post by gabrielshier on 2009-04-30
> **psyke83 said:**
> Are you sure it's necessary to install this software? Perhaps ALSA or PulseAudio can replicate the functionality you need.

Hey psyke83,
Quick answer! :)
Well, i thought about it, and it's not that i want this particular program, but i could not find a program that will offer me this feature. If ALSA can do that, or any other program, just tell me the package name and i will surely download it. Unfortunatly i didn't find one and that's why i want to install this certain driver. 
Thanks,
Gabi

---

### Post by markbuntu on 2009-04-30
Are you sure the volume control does not have switches for that in Options?
You may have open the volume control ( right click the little speaker icon on the top panel) and choosing open volume control and then preferences to make the line-in mode and mic mode switches available.

---

### Post by gabrielshier on 2009-05-01
As i said, i could not find it. If you can point me to the place where it is, or how do i do it. Went all throught the help of the ALSA but still coulden't find it. If you see any way, please tell me. I'll do it. Right now i can only hear from my FR and FL without the rear&&sub&&center. Quiet annoying :(

---

### Post by psyke83 on 2009-05-01
> **gabrielshier said:**
> As i said, i could not find it. If you can point me to the place where it is, or how do i do it. Went all throught the help of the ALSA but still coulden't find it. If you see any way, please tell me. I'll do it. Right now i can only hear from my FR and FL without the rear&&sub&&center. Quiet annoying :(

You need to un-hide the switches/sliders.

Open Volume Control from the notification icon, click Options, and place checkmarks for the items that you wish to display. Note that enabling the checkmarks here only make the options visible, they do not enable the options. You must then go back to the Volume Control window and adjust the new sliders/switches.

---

### Post by gabrielshier on 2009-05-01
Hey
i'm quiet a smart *** :(...
Tried using some how-to's of online site of editing the ALSA driver files. Endded up with no sound what so ever. The computer acts like it's playing, but i hear no sound. What to do?

---

