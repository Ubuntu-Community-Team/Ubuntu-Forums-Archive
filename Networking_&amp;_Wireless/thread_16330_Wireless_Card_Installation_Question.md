---
title: "Wireless Card Installation Question"
date: 2005-02-20
forum: Networking &amp; Wireless
---

### Post by caiphn on 2005-02-20
Hi, I finally got Ubuntu up and running and after having a couple of days of no OS loading whatsoever I must say that I am relieved. However now I'm having problems getting online.

I have a Linksys 2.4GHz 802.11b WMP11 v27 (I'm assuming that's refering to 2.7 as doing a forum search someone had the same card it seemed)

1. What is the equivalent to the device manager in linux? I haven't really played with it much but I have no idea if it's picking up the wireless card whatsoever.

2. Apparently a program called 'NDISWRAPPER' can load in the Windows INF drivers so the card can be recognized. It looks as though it is downloadable at [http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148).. the file is ndiswrapper-1.0.tar.gz. Keep in mind I'm a complete and total newbie. I'm assuming I would throw this onto a disc and then unarchive it somehow. What would I need to do?

3. There are three INF files on the disc, AUTORUN.INF, WMP11NDS.INF and WMP11v27.INF. Obviously it's not autorun.inf, but what of the other two drivers would be the appropriate driver?

---

### Post by telmo on 2005-02-20
OK! First of all, i think none of the two is the important .inf file... but just in case... install the driver in your windows, and check out where the files where extracted to. I think there's also a .sys file you need. But you should only install the .inf file.

Of course you shouldn't forget to see if your wireless card is supported in ndiswrapper's website.

Now keep in mind that ndiswrapper doesn't work properly with every kernel.
Now install GCC libraries (select gcc in synaptic or yum install gcc, if you don't have synaptic installed), and install respective kernel headers and restricted modules.

Extract the ndiswrapper file (right click it and select extract here)

Now go to the ndiswrapper directory and type:

# make install
It should install with no errors

Next issue the following commands:

# ndiswrapper -i path/filename.inf
to install the driver (being path, the path to the file and filename.inf, the file.)

# ndiswrapper -l
to see if the driver is installed and working

# ndiswrapper -m
to make ndiswrapper load automatically on boot

# modprobe ndiswrapper
insert module ndiswrapper

Now... if modprobe works, you should be able to get wireless. All you have to do now is configuring 'Networking' in 'System Configuration'. Adding a new wireless connection should assume 'wlan0' or something like it. You just need to insert the ESSID and WEP (if you're using one) and DHCP (maybe auto... just guessing!)

Then reboot your computer.

By the way... if your using a new kernel (2.6.10) you should make a shortcut to your kernel headers, like this:
(When in doubt about your kernel version type 'uname -r' in the console)

# ln -s /usr/src/linux-headers-2.6.10-3 /lib/modules/2.6.10-3-686/build
(being 2.6-3 the version of your kernel)

...and if you couldn't make a modprobe, than maybe now you can.

Good luck!

Tell me if it worked.

---

### Post by caiphn on 2005-02-20
It looks as though the card is supported, I found this at the site.

Card: Linksys WMP11 v27 802.11b -- link here 
Chipset: Broadcom BCM4301 
Driver: Downloaded Windows 2000 driver from Compaq site. FilenameSP28538.exe. 
Other: Mandrake 10.1 with 2.6.8.1 kernel. NdisWrapper 0.90 built and installed. Use bcmwl5.inf. 

Now, keep in mind I am a newbie so some of the terms you have been telling me I have never heard before.

I'm not sure how to install the "GCC Libraries" or even what they are. I have not installed synaptic, I have never installed anything before or used Linux in anyway. I am trying to refrain from asking so many questions, I try to search and read as much as possible. When you're refering to installing respective kernel headers and restricted modules I have no clue as to what you're refering to... the rest of the instructions are very straight forward and I thank you for that as I am a complete newbie. I'm going to give this a shot.. I'm assuming when I right click on the file I browse to the floppy drive and just right click it there. I'll figure it out.. however if these GCC libraries need to be installed first.. in their respective kernel headers and restricted modules.... I'm not sure how to do that.

---

### Post by caiphn on 2005-02-20
I tried to go through the steps you gave, omitting the GCC libraries (which obviously is needed), I extracted the archive on the desktop and then went into the terminal which I can issue commands from. Luckily changing directories is like in DOS, using the CD command the DIR command, so I was able to navigate to the directory. In the ndiswrapper directory I typed the command 'make install' and this happened.

:~/Desktop/ndiswrapper-1.0 $ make install
make -C driver install
make[1]: Entering directory `/home/david/Desktop/ndiswrapper-1.0/driver'
Can't find kernel sources in /lib/modules/2.6.8.1-3-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/david/Desktop/ndiswrapper-1.0/driver'
make: *** [install] Error 2

This must be from me not installing the GCC libraries,.. I'll do some searching and try to figure out how to either 
A) install synaptic 
B) I believe the alternate you gave is 'yum install gcc'

I'll figure it out. (I hope.)

---

### Post by telmo on 2005-02-20
hmmm... ok!

Let's see... do the following..:

Check this forum for apt-get install and install it! (i don't really remember how i did it!) :)
Then install synaptic. (apt-get install synaptic) <---- command

Then open synaptic (you can just type synaptic in the console) and search for gcc
then right click it and select 'Mark for instalation'

Then search for headers and, once again right click and 'Mark for instalation'

And finally search Restricted Modules and install it in the same way.

NOTE: Kernel Headers and Restricted Modules should match your kernel version...
(just type 'uname -r' in the console)

Then go on from there.

Good luck once again.

---

### Post by caiphn on 2005-02-20
I've found various documents describing how to use apt-get and what it is, and how synaptic is basically a GUI apt tool, I cannot find any that say 'this is how you install apt-get for the first time.' .. not having any luck, I've been googling and browsing the forums since you posted. If anyone can help me out that'd be great.

---- Edit ----

Well, I just tried the command and it seemed to work, so I suppose apt-get comes with Ubuntu. I tried to install synaptic by typing apt-get install synaptic but I said I had to login as root first. Not sure how to do that, but I saw it earlier.

---

### Post by caiphn on 2005-02-21
Well, it looks as if synaptic is already installed. I installed the GCC libraries, there were 6 that started with GCC but 4 were already installed, and in order to install just GCC, GCC 3.3 also had to be installed, which they were. I don't think the headers and restricted modules match my kernel version, which is 2.6.8.1-3-386. I'll tell you what happens, at least I keep making it a little farther each time. :)


-edit-

Yah! I'm using Ubuntu now with my wireless connection. Thanks for the assistance telmo, I would have never figured that out in a million years, seems like my searching skills are pretty terrible. Question with the ESSID, would there have been a way to just detect wireless network connections that are available, or did it have to be put in manually? I was having some problems with the ndiswrapper pathname and whatnot, not used to it being case sensitive. Now that I've installed NDISWRAPPER can I delete the folder and the archive off of my desktop? The driver that was installed was also on my desktop, can I get rid of it as well? Thanks for getting me up and running! \\:D/

---

### Post by baseballfan on 2005-06-26
So how did you get it to work?  I have the same problem,ried to use bcmwl5.inf and it didnt work...ndiswrapper says invalid driver when I do ndiswrapper -l.

---

