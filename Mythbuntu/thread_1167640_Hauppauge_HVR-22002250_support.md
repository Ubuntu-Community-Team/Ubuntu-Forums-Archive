---
title: "Hauppauge HVR-2200/2250 support"
date: 2009-05-23
forum: Mythbuntu
---

### Post by Batnun on 2009-05-23
Hi,

Does anybody knows when the new driver will be supported on Mythbuntu daily builds?
(or maybe is already supported?)

Thanks in advance!


Batnun

---

### Post by LowSky on 2009-06-09
here is  my tutorial

> **LowSky said:**
> OK here is the awesome news, I got it working, but it took forever as I had to go through miles of web pages just to get this to work! I'll list my sources at the bottom if I missed something and you need to look through it for answers. 

So I'm going to be nice and do some people some favours and post what I did to get it working in MythTV. 

**This driver is a BETA** and only works on digital side of the tuner, 

_NO ANALOGUE_ and _please be careful using_.

**_*I am not responsible for the outcome of you using my tutorial.*_** 

As I think my tutorial is rather crude and may miss an important step, please see the sources listed below. This is not for people new to Linux, as it might break (and it might, I've only had this running for about 30 minutes, so fingers crossed). 

If you really need to use this card for analogue and need a free OS, try the Windows 7 MCE, the free RC is currently available and should work until May 2010 before MS make you purchase a real copy and works completely with this tuner card.

Instructions for using HVR-2250 in MythTV (also works on HVR-2200 or any video capture card using the SAA7164 chipset)

you need to be running Ubuntu 8.10 or higher for these drivers

Enter this into your Terminal it is the code for the firmware and to install it
```

wget http://www.steventoth.net/linux/hvr22xx/22xxdrv_27086.zip
wget http://www.steventoth.net/linux/hvr22xx/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
wget http://www.steventoth.net/linux/hvr22xx/extract.sh
```
```

sh extract.sh
sudo cp *fw /lib/firmware

```
you need to install mercurial and build essential for the next steps
```
sudo apt-get install mercurial build-essential
```

then we need the driver using this command to fetch
```
hg clone http://kernellabs.com/hg/saa7164-stable/
```

now change to the directory
```
cd saa7164-stable
```

then run make
```
make
```

that will take some time, go grab a drink and wait it out, when it completes run this command
```
sudo make install
```

wait for that to complete and reboot
from the command line
```
sudo reboot
```

Note that an application like TVtime will not work, TVtime only works on Analog signals, and so far this driver only gets the digital stuff working.

then install MythTV using whatever method you like, I personally went into synaptic and installed the frontend and backend and extra plug-ins

once installed and you set up your passwords go to
System> administration> MythTV backend setup

once there go to Capture Cards, Should be choice #2
choose new capture card, you will ave to do this step twice (this card has two tuners)
At card Type, pick DTB DTV
the first will be device number 0, 
repeats choosing capture card to add the second tuner
the second device will be #1 (Linux starts counting at 0, good thing to know, especially for hard drives)

then go to video sources, pick your options, will vary so mine will not work with yours most likely, so I dont want to post something I dont know)

then go to Input Connections, again you will have 0 and 1, configure both

then edit channels and directories as needed.

close let it fill database, for some reason mine keeps running in a loop, just exit after you see it finish the first or second time

now go to Applications > Sound & Video > MythTV Frontend

And you should be able to watch TV

I must say the Linux HTPC community is way too technical for most people, they need to make these things simpler, Windows 7 MCE is  10 times better at setting up these things.

[SIZE="3"]Notes[/SIZE]
I used Ubuntu 9.04, results should work for anyone using *buntu 8.10 releases, including Mythbuntu
I must say the configuring MythTV is exhausting so if I missed something or it doens't work please post better steps.
Special thanks to Steven over at [KernelLabs]("http://www.kernellabs.com/blog/?page_id=17"), the person who made the drivers.


**[SIZE="3"]Sources[/SIZE]**

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers)
[http://www.kernellabs.com/blog/?page_id=17](http://www.kernellabs.com/blog/?page_id=17)
[http://kernellabs.com/hg/saa7164-stable/](http://kernellabs.com/hg/saa7164-stable/)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial](http://www.linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers#Using_Mercurial)
[http://www.steventoth.net/blog/products/hvr-2250/](http://www.steventoth.net/blog/products/hvr-2250/)
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

---

### Post by jaketrunk on 2009-06-12
I followed LowSky's instructions and was able to set up the Hauppauge 2250.  It works great - except for one issue.  My OTA ATSC channels come in crystal clear, but the signal strength shows 0% with a S/N or 2.5.  Is anyone else with a 2250 having the same issue?

---

### Post by LowSky on 2009-06-12
I'm not using OTA so I cant help, sorry. Probably related to the beta driver. best  thing to do is contact the person responsible for the driver

[email]stoth@kernellabs.com[/email]
[http://www.kernellabs.com/blog/?page_id=17](http://www.kernellabs.com/blog/?page_id=17)

---

### Post by epi 1:10,000 on 2009-06-12
I have about the same stats on my 2250, 1600, and 1250's.  They all have a signal strength of 0% with a S/N ratio of 2.4 to 2.6, and a low BER.  I find the settup and diagnostic screens on my Motorola DCT6XXX to be a better tool for assessing signal quality and strength.  I remember Steven Toth posting something on some development board on how to calculate signal strength but I cant remember where.  I'm not sure what the units are on the MythTV information overlay thing but it doesn't seem to corespond to the Motorola metric.

---

### Post by lxowle on 2009-06-12
> LOWSKY: Enter this into your Terminal it is the code for the firmware and to install it

That's fantastic, thanks for this. I'm new to this and I dual boot to windows xp. If I install the firmware you've mentioned above, does it affect the card, or is the term "firmware" here being in another way? I need to ask because I want to try this to see if I can get it working under ubuntu, but it's on my wife's xp machine and I don't want to stuff that up by writing new firmware to the card :)

---

### Post by Ozsmoka on 2009-08-05
Thanks heaps for this LowSky,

 it works perfectly for me from the 2.6.28-14-generic kernel, but after updating to the next kernel this morning, the system was unable to detect the card...at all. I was using Kaffeine to view tv from my desktop, but I also tried other packages which all failed to detect the card.

I reverted to 2.6.28-14-generic and everything is working again as it was previously with no problems.

Hopefully the issue can be resolved soon.

cheers

oz

---

### Post by silverdulcet on 2009-08-06
> **Ozsmoka said:**
> Thanks heaps for this LowSky,

 it works perfectly for me from the 2.6.28-14-generic kernel, but after updating to the next kernel this morning, the system was unable to detect the card...at all. I was using Kaffeine to view tv from my desktop, but I also tried other packages which all failed to detect the card.

I reverted to 2.6.28-14-generic and everything is working again as it was previously with no problems.

Hopefully the issue can be resolved soon.

cheers

oz

Since you compiled the drivers for the currently installed kernel, anytime there is a kernel update you need to recompile the drivers for the new kernel. So just follow the instructions again, except downloading and copying the firmware since you already have that in place.

---

### Post by Ozsmoka on 2009-08-06
Hi & thanks silverdulcet,

I tried just recompiling, but looking at the code as it executes, it looks like it uses the old kernel headers? Sorry I'm not a coder, so I don't know a lot about it. I'd love to learn more though.

I ran the code from the cd command onwards. Is that correct?

I did try downloading again, just in case, but as you say, the files are identical, so no joy there.

Thanks for your help.

cheers

---

### Post by silverdulcet on 2009-08-06
> **Ozsmoka said:**
> Hi & thanks silverdulcet,

I tried just recompiling, but looking at the code as it executes, it looks like it uses the old kernel headers? Sorry I'm not a coder, so I don't know a lot about it. I'd love to learn more though.

I ran the code from the cd command onwards. Is that correct?

I did try downloading again, just in case, but as you say, the files are identical, so no joy there.

Thanks for your help.

cheers

Remove the directory you downloaded the source to, from the directions above its:
```
rm -r saa7164-stable/
```

Then run from the hg clone command on. 

This will download the source again, then you can recompile it. I don't have this card, but another card that requires newer drivers then those that are in the kernel. I think the command:
```
make clean
```

might work as well, but I think I tried that once and ran into the problem you did. Removing the source directory, then downloading it again solved my problem.

---

### Post by Ozsmoka on 2009-08-07
ahhh tyvm silverdulcet,

That worked perfectly! All is good now. Didn't need the 'make clean' command.

Thanks for your patience and I really appreciate the explanation as to what the code is doing as well as the code supplied. 

Gotta love this community. 

Cheers 

oz

---

### Post by silverdulcet on 2009-08-07
> **Ozsmoka said:**
> ahhh tyvm silverdulcet,

That worked perfectly! All is good now. Didn't need the 'make clean' command.

Thanks for your patience and I really appreciate the explanation as to what the code is doing as well as the code supplied. 

Gotta love this community. 

Cheers 

oz

Just an FYI, I figured out how to build with the existing source directory after a kernal update, without removing the directory and downloading the source over again. First change into the source directory:
```
cd saa7164-stable/
```

Then use this command:
```
make distclean
```

Then
```
make
```

Finally
```
sudo make install
```


From the INSTALL file instructions, this will remove the leftover build files from the last time you built the driver. When you use the make/make install commands it should now use your updated kernel instead of the old one.
> distclean - Cleans compiled files from the tree,
                   latest used configuration and kernel
       	           version.

---

### Post by Ozsmoka on 2009-08-20
Ahh cool, silverdulcet

I just updated the kernel and restored the driver using the previous method, as I missed your last post prior to updating.

The new method you just mentioned is much more efficient. Efficient is good :)  I'll give that a go next time.

Thanks.

--yep thanks silverdulcet, 

that worked.

Compiz is not happy with the upgrade though. I wound up with perfect sound and reception, but no video at all. No complaints, just no video in Me TV and VLC.

I tried using the previous method for upgrading the driver as well, and wound up with exactly the same result.

I thought it might have to do with my 9.7 ati catalyst drivers, but before uninstalling them, I disabled 'visual effects' as a first step, and the picture is fine.

No great loss while tv viewing.

Cheers.

---

