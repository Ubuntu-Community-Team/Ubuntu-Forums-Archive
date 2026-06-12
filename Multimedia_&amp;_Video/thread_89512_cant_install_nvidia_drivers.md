---
title: "cant install nvidia drivers"
date: 2005-11-12
forum: Multimedia &amp; Video
---

### Post by bobbin on 2005-11-12
Hi, ill try to explane my problem whith the best english possible.
i have a 6600gt and i cant install de nvidia drivers or run de xserver (dont know if thats the name)..
i tryed the all; the 6629, 7667, 7174, etc. All whith multiple mistakes, not having the matching gcc compiler (i know nothing about linux, is my first time so i could be wrong in explaning the errors), not having the libc, not having a certain linux-headers, etc. i installed the libc-dev, the linux-headers, and other stuff thar asked me for.
the closest i got to install the was when it gave an error that it couldent install becouse it would colide whith "rivafb".
it also said something about not been able to make an interface for the installer because of my kernel version (dont know the version, the one that comes whith ubunto 5.10), it tyed to download one but couldnt..


i tryed a lot of solutions that i found on the web but they didnt work.
what can i do?

it wold be great thar any explanation would be explicit and explicative, i dont know nothing!

---

### Post by Samuel on 2005-11-12
are you using apt-get?
```
sudo apt-get nvidia-glx
```
then enable the driver with 
```
sudo nvidia-glx-config enable
```

the reason you get the errors is because the drivers from nvidia's site
cant be run with nvidia framebuffer support built in to the kernel.
im pretty sure you need the kernel source and the linux headers and some other
stuff to compile the drivers too, the one from apt-get should work fine...

---

### Post by 23meg on 2005-11-12
[QUOTE=bobbin]
i tryed a lot of solutions that i found on the web but they didnt work.
what can i do?

it wold be great thar any explanation would be explicit and explicative, i dont know nothing![/QUOTE]

Check out [this guide]("http://www.ubuntuforums.org/showthread.php?t=75074"); if you follow the steps carefully you'll get it working.

Samuel: nvidia-glx on its own isn't enough since it doesn't include the nvidia kernel module, which I think is in the restricted modules packages.

---

### Post by bobbin on 2005-11-13
[QUOTE=23meg]Check out [this guide]("http://www.ubuntuforums.org/showthread.php?t=75074"); if you follow the steps carefully you'll get it working.
[/QUOTE]

mmmm no:confused: 
it asumes im in X and im not. cant run synaptic, put i tyed to do it manually but it doesnt work, i cant installm the packages thas asks me

---

### Post by 23meg on 2005-11-13
On the contrary, it just assumes you are in X to make you shut down X; you can't install the driver if you **are** in X; please take time to read more carefully.

How exactly does synaptic fail? Did you [enable extra repositories]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse")?

---

### Post by bobbin on 2005-11-13
[QUOTE=23meg]How exactly does synaptic fail?[/QUOTE]
my giving me this error:
Gtk-WARNING **:cannot open display

---

### Post by 23meg on 2005-11-13
What is your kernel version? Type "uname -r" in the console if you're not sure.

---

### Post by bobbin on 2005-11-13
[QUOTE=23meg]What is your kernel version? Type "uname -r" in the console if you're not sure.[/QUOTE]

the version is 2.6.12-9-686
i had the same in 386 but i read that de 686 is better for my p4 ht

---

### Post by 23meg on 2005-11-13
If you have a hyperthreading processor 686-smp is even better. 

Try this: ```
sudo apt-get install linux-restricted-modules-2.6.12-9-686 nvidia-glx
sudo nvidia-glx-config enable

``` and then reboot.

---

### Post by bobbin on 2005-11-13
thanks, ill  try

what does it mean the smp?

---

### Post by 23meg on 2005-11-13
It stands for Symmetric Multi Processing. If you install the 686-smp kernel you'll need to get linux-restricted-modules-2.6.12-9-686-smp.

---

### Post by bobbin on 2005-11-13
ok, i changed the kernel and installed the restricted modules but de smp version.
for what are they for?

---

### Post by 23meg on 2005-11-13
The restricted modules package includes the nvidia kernel module, which is needed for your card to work. Did you get it working?

---

### Post by bobbin on 2005-11-13
no.
the dirver intall program asks me for the kernel source that refuses to install, it says the i already have the las one but i have nothing in the /usr/src/ file (exept the headres). this is trying to instal the linux-source-2.6.12 source, i tryed to install linux-source-2.6.12-9-686-smp but it doesnt exist.
if it says that is already installed..where is it?..so i can use it

---

### Post by 23meg on 2005-11-13
linux-source-2.6.12 should be ok; what error do you get when trying to install it with "sudo apt-get install linux-source-2.6.12"?

---

### Post by bobbin on 2005-11-13
is sais that the last version is already installed, so it does nothing.

---

### Post by 23meg on 2005-11-13
If it says it's installed, then it is. Are you sure you installed the correct version of the headers as well? If you're running the 686-smp kernel you need linux-headers-2.6.12-9-686-smp. Make sure you have it, and if you're still getting errors in the installer, please report the exact error so I'll have a chance of understanding what's going wrong.

---

### Post by bobbin on 2005-11-13
i have the correct version of headers....:???: ...

---

### Post by 23meg on 2005-11-14
You still haven't told me what error the nvidia installer is failing with at the moment. Please tell me the exact error, and the exact version of the driver you are installing, and post the contents of your /var/log/nvidia-installer.log file.

---

### Post by bobbin on 2005-11-16
sorry im late, and thank you for all the trouble.
here is the error:

if you are using linux 2.6 kernel please make sure you have configurated kernel sources matching your sources matching your kernel installed on your system. If you specified a separated autput directory using either the "KBUILDOUTPUT" or the "0" KBUILD parameter, make sure to specify this directory whith the SYSOUT enviroment variable or whith the eqiovalent nvidia-installer comand line option.

Dependind on where and how the kernel sources (or the kernel headers) where installed, you may need to specify their location whith the SYSSRC enviroment variable or the equivalent nvidia-installer command line option

---

### Post by bobbin on 2005-11-22
:( :confused: :( :???: :(

---

