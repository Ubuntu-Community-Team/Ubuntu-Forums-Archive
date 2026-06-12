---
title: "Problems making stb0899 driver in Ubuntu Feisty (For MythTV with Technotrend S2-3200)"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by kevpatts on 2007-05-31
I'm getting the following error:```
kev@kev-feisty:~/Desktop/stb0899-c5-760cb230695c$ sudo su
root@kev-feisty:/home/kev/Desktop/stb0899-c5-760cb230695c# make
make -C /home/kev/Desktop/stb0899-c5-760cb230695c/v4l 
make[1]: Entering directory `/home/kev/Desktop/stb0899-c5-760cb230695c/v4l'
scripts/make_makefile.pl /lib/modules/2.6.20-16-generic/build
make[1]: execvp: scripts/make_makefile.pl: Permission denied
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/kev/Desktop/stb0899-c5-760cb230695c/v4l'
make: *** [all] Error 2
root@kev-feisty:/home/kev/Desktop/stb0899-c5-760cb230695c# 

```

Can anyone help?

---

### Post by x-point on 2007-06-01
Try this one: [http://jusst.de/manu/stb0899-v4l-dvb.tar.bz2](http://jusst.de/manu/stb0899-v4l-dvb.tar.bz2)

---

### Post by kevpatts on 2007-06-02
That seems like a more appropriate package, cause I was downloading this one before: [http://linuxtv.org/hg/~manu/stb0899-c5/archive/tip.tar.bz2](http://linuxtv.org/hg/~manu/stb0899-c5/archive/tip.tar.bz2)
But now I get:```
kev@kev-feisty:~/Desktop/v4l-dvb$ sudo make
Password:
make -C /home/kev/Desktop/v4l-dvb/v4l 
make[1]: Entering directory `/home/kev/Desktop/v4l-dvb/v4l'
creating symbolic links...
make -C /lib/modules/2.6.20/build SUBDIRS=/home/kev/Desktop/v4l-dvb/v4l  modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.20/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/kev/Desktop/v4l-dvb/v4l'
make: *** [all] Error 2
kev@kev-feisty:~/Desktop/v4l-dvb$ 
```I thought this may be a kernel headers/source thing, but I've installed both and have no luck still.

Thanks for your help,
Kevpatts

---

### Post by kevpatts on 2007-06-05
a ```
sudo ln -s /lib/modules/2.6.20-16-generic /lib/modules/2.6.20
```sorted out my problems.

---

### Post by kevpatts on 2007-06-05
actually that was a lie. I still dont have a /dev/dvb directory (which I assume is why I'm getting "no such file of directory" on the DVB DTV capture card (v3.x) setup page.

Is this just a case of a simple link again and it so, what do I link to? Has anyone tried this before with this card?

---

### Post by adriankendall on 2007-08-20
Did you get anywhere with solving this issue. I am struggling with getting a pair of satelco cards the DVB-T and DVB-S2 version going under ubuntu Feisty. A couple days of googling and searching thses forums haven't reduced the confusion.

Similar symptoms LSPCI shows the cards are there but I cannot configure a driver that gets them running nothing in dmesg or messages, admittedly the STB0899 and is new I had tried budget-av and budget-ci only so far. 

Is any firmware required for these cards?

Any input would be thankfly recieved, also a confirmation if Diseqc and CI is operational for the Satelco DVB-S2 card as well.

---

### Post by Gothem on 2007-12-14
> **kevpatts said:**
> actually that was a lie. I still dont have a /dev/dvb directory (which I assume is why I'm getting "no such file of directory" on the DVB DTV capture card (v3.x) setup page.

Is this just a case of a simple link again and it so, what do I link to? Has anyone tried this before with this card?

Did you load the modules after building them? lsmod should show you whetherthey are loaded or not. There should be the following modules present:
stb0899, stb6100, lnbp21 and budget-ci
if not try 
modprobe stb0899 stb6100 lnbp21
modprobe budget-ci

if one of the first 3 fails try them one at a time, i dont know if there is a specific order for them to be loaded.
But im pretty sure budget-ci should be the last one loaded.

---

### Post by Skerit on 2008-01-31
Err, so how's this going?

(I'm planning on buying this dvb-s2 tuner card :P)

---

### Post by Skerit on 2008-05-14
Great - 4 months later, I finally installed the card and I have *the exact* same problem!

I'm installing those multiproto drivers from here:
[http://jusst.de/hg/multiproto](http://jusst.de/hg/multiproto)
following this tutorial:
[http://wilco.bercot.org/debian/s2-3200.html](http://wilco.bercot.org/debian/s2-3200.html)

My kernel version is 2.6.22-14-generic (feisty linuxmce)

However, some people are talking about other drivers (seperate stb0899 file?) What's that all about?

---

### Post by ZippyP on 2008-07-06
Hello

Same here except using hardy 8.04.1. And now more months later...  What is with this card that Linux just plain does not want to run?  I think I may have seen one post that someone got it working and dumb me did not bookmark the post.  Lucky them...
I followed a set of directions posted by Jonas Kvinge. Pretty straight forward, to the point and easy to understand. Well I thought. [http://www.jonas.io](http://www.jonas.io)
I did not get to the "Compile and install mythtv" part since the Multiproto did not compile the STB0899 So I did the usual install.  Every package I tried, including the stb0899 package, same errors.
At the terminal I typed [color=red]lsmod | grep dvb[/color] Yep... The STB0899 info was not there. In a former install of Myth I saw the card in the setup when setting the cards up, when it came to scanning the transponders, the signal was there for a second then shut off the card or the LNB voltage.  This was fixed by clicking finish then going back one menu and clicking finish in that menu.
For what its worth, I am a satellite broadcast engineer, this project is killing me.  I usually can get stuff running even without the manuals.  I am new to linux, yep, after over 20 years in the business I am just getting my feet wet with Linux.  I have been at it for over a month now and printed out a ream of paper of various posts on this subject.  Something was said a while back about the version of the chipset on the card and it had something to do with the install. Figures, I forgot what that said.  Well, anyway here is what I got from the statement [color=red]lsmod | grep dvb[/color].
> 
lsmod | grep dvb
dvb_pll                13448  1 
cx88_dvb               14724  0 
cx88_vp3054_i2c         3968  1 cx88_dvb
videobuf_dvb            7812  1 cx88_dvb
dvb_core               89212  3 budget_ci,budget_core,videobuf_dvb
cx8802                 19076  1 cx88_dvb
cx88xx                 66856  3 cx88_dvb,cx8800,cx8802
i2c_core               24832  25 lnbp21,stb6100,stb0899,nvidia,tuner,tea5767,tda8290,tda18271,dvb_pll,tda827x,tuner_xc2028,xc5000,nxt200x,tda9887,tuner_simple,mt20xx,tea5761,budget_ci,budget_core,cx88_vp3054_i2c,ttpci_eeprom,cx88xx,i2c_algo_bit,tveeprom,v4l2_common
videobuf_dma_sg        14852  5 cx88_dvb,videobuf_dvb,cx8800,cx8802,cx88xx
videobuf_core          19332  5 videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg 
The STB0899 is in there but not the right info for the dvb_core.
Again is this due to the chipset. Jonas seems to have his working, maybe working.
Has anyone there got multiproto to go through the make (compile) with out any errors in the stb0899 section?

Thanks

[color=red]Update[/color]
I now have the Technotrend showing up as a STB0899 in Myth's backend. When scanning a transponder there is no signal but my Spectrum Analyzer is showing a signal. Anyone experience this with the TT-3200?

---

### Post by Skerit on 2008-07-23
I'm just as stumped as you are.

I've tried time and time again, sometimes it works, sometimes it doesn't. (I actually watched TV in mythtv once! and yesterday I even got locks on the channels) That's the non-logical thing about it! It should be consistent

However, I compile lots of different drivers after another. Somehow I believe these don't get removed completely when I do a "make rminstall" or "make distclean". I'm currently trying to create a debian of the drivers using checkinstall so that I can get clear results that will always work. Unfortunately, the debian doesn't work because it'll overwrite somee xisting files...

---

