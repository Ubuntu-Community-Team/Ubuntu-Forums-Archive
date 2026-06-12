---
title: "Help with dial up"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by cody1233 on 2010-07-10
I am new to ubuntu and the only connection to the internet is dial up.  I found out ubuntu doesn't support dial up...I tried to use wvdial but my modem was not configured, so i installed setserial but i could not figure that out.  i am looking for any information on using setserial or any help with dialup in general.  I am using ubuntu karmic koala on a dell latitude c610

---

### Post by pdc on 2010-07-10
so tell us what sort of modem you are using

---

### Post by bytbox on 2010-07-10
Ubuntu supports dialup just fine - even AOL. If aol: find a place to download the source for 'penggy' (an old repository from 8.04 worked for me, I think). If not aol, look at kppp (for kde), or gnome-ppp (for gnome and, I guess, XFCE).

---

### Post by Pi-Rat on 2010-07-10
You may have the same problem I did before I got broadband: a "Winsoft" modem. It's a little bit of hardware and lots of proprietary Windows code to make you a dial up modem. The only way I was able to resolve it was to get an external hardware modem. This was under Dapper, so might be a slightly different story now, but maybe not.

---

### Post by ieee488 on 2010-07-10
> **cody1233 said:**
> I am new to ubuntu and the only connection to the internet is dial up.  I found out ubuntu doesn't support dial up...I tried to use wvdial but my modem was not configured, so i installed setserial but i could not figure that out.  i am looking for any information on using setserial or any help with dialup in general.  I am using ubuntu karmic koala on a dell latitude c610

Ubuntu most certainly supports dial-up. Before I was on DSL, I had ATT dial-up and it worked perfectly for me. Of course, my modem was supported by Ubuntu.

I suggest that you read [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by cody1233 on 2010-07-11
i have the original modem for it...can i download a driver for windows and install it under wine?

---

### Post by cody1233 on 2010-07-11
Oh the modem is a pctel

---

### Post by ieee488 on 2010-07-11
> **cody1233 said:**
> i have the original modem for it...can i download a driver for windows and install it under wine?

Did you bother reading the HOWTO????

Did anything in there say anything about using Wine??????

---

### Post by nnamdi on 2010-07-11
Hey have tried using wvdial u can install it then configure it.it should work atleast

---

### Post by klytu on 2010-07-11
> **cody1233 said:**
> Oh the modem is a pctel
If you are using a 32-bit kernel, there are excellent resources for pctel modems at: [http://132.68.73.235/linmodems/pctel-linux/](http://132.68.73.235/linmodems/pctel-linux/)

Here are the basic steps to get your modem up and running:

READ pctel-ubuntu.txt and the README in the unpacked directory from step 3 below. 

1. Download latest driver (13-Jun-2010 at the time of this entry) pctel-0.9.7-9-rht-11.tar.gz
2. Install kernel sources and header for the current kernel:
	```
sudo aptitude install linux-headers-$(uname -r)
	sudo aptitude install build-essential
```
3. Unpack tarball:
	```
tar zxf pctel*.tar.gz
```
4. Navigate to the pctel directory created : ```
cd pctel-0.9.7-9-rht-11
```
5. run setup as root: ```
sudo ./setup
``` (or follow instructions for manual installation)
6. Compilation should complete and indicate modem is installed. Test this with: ```
sudo wvdialconf /etc/wvdial.conf
``` 
7. If everything is OK, then set up wvdial with: sudo gedit /etc/wvdial.conf or install gnome-ppp and set up the gnome-ppp dialer accordingly.

---

### Post by cody1233 on 2010-07-11
thank you guys so much...

---

### Post by cody1233 on 2010-07-11
don't forget i can't download anything from ubuntu ( i am doing this from win :( )

---

### Post by klytu on 2010-07-11
> **cody1233 said:**
> don't forget i can't download anything from ubuntu ( i am doing this from win :( )

Yeah, I realize you can't download from Ubuntu yet. :-) But you can download the drivers with whatever computer you are using to post here, store them to a flash drive, cd, or whatever and then save them to the home directory of your Ubuntu machine. Just print out the instructions in my post to get you started.

FYI, the driver file is not that large - less than 2MB. Even on dial-up that should only take a couple of minutes to download.

---

### Post by cody1233 on 2010-07-11
alright...so i went in and used terminal to start the main setup thing and it gave me this...

cody@cody-laptop:~/pctel-0.9.7-9-rht-11$ ./setup
checking for running kernel version...2.6.31
checking for ptserial...ptserial-2.6.c
checking for gcc...4.4.1 (4.4)
checking for kernel gcc version...4.4.1 (4.4)
searching for kernel includes...found at /lib/modules/2.6.31-14-generic/build/include
checking for autoconf.h.../lib/modules/2.6.31-14-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in linux/utsrelease.h...UTS_RELEASE is 2.6.31-14-generic
checking type of tty_struct.count...int
checking for presence of udev...present (kernel version 2.6.13 or later)
detecting your modem...found. Your modem is a i8xx type modem.
** error
this driver does not support this kind of modem
under 2.6 series kernels. Please use the SmartLink
driver instead.
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.
cody@cody-laptop:~/pctel-0.9.7-9-rht-11$

---

### Post by pdc on 2010-07-12
at this stage, you might need to do a bit of home work your self

You posted

> [I]this driver does not support this kind of modem
under 2.6 series[/I] [B]Please use the SmartLink
driver instead[/B].

I suggest you have a read at this link 

[http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html)

.. particularly the SmartLink .. reference

.. sometimes a little understand of how the petrol goes around the engine and out the exhaust helps .....

and wait for klytu to come back and help you; he seems very knowledgable and gave very detailed posts ..........

---

### Post by cody1233 on 2010-07-12
Ahhh...screw it...im gonna buy a usb modem...

---

### Post by cody1233 on 2010-07-24
Alright...i bought a zoom model 3095 usb modem that has precompiled ubuntu drivers but only up to jaunty...im running karmic...can anybody tell me where or how to get the drivers?

---

### Post by bkratz on 2010-07-24
I don't know anything about it--but I think you may find some help here.

[http://swiss.ubuntuforums.org/showthread.php?p=9626226](http://swiss.ubuntuforums.org/showthread.php?p=9626226)

Sorry not more help.

---

### Post by cody1233 on 2010-08-02
Alright...so i got the driver and installed it...restarted my comp and tried again to get gnomeppp to find it and still nothing...PLEASE HELP!!!

---

### Post by pdc on 2010-08-02
> Oh the modem is a pctel

There are two types of the old dialup modems

1) win-modems

2) free standing serial modems

I suspect a pctel modem is a winmodem:

here is a website all about it ...

[http://www.linmodems.org/](http://www.linmodems.org/)

**In fact, here is a pctel website**

[http://pctelcompdb.sourceforge.net/](http://pctelcompdb.sourceforge.net/)

seems to suggest to me you have a truly wretched **WIN-MODEM** 

what is that?

[http://pcquest.ciol.com/content/linux/handson/102082101.asp](http://pcquest.ciol.com/content/linux/handson/102082101.asp)

which country do you live in ?

you need to buy yourself a second-hand **external serial modem**

which are compatible with linux: well, nearly all 

eg read this

[http://my.opera.com/lounge/forums/topic.dml?id=195038](http://my.opera.com/lounge/forums/topic.dml?id=195038)

get on ebay or somesuch and buy yourself one for a few dollars ... 

If you insist on sticking with your pctel, **join a winmodem forum** because they will be the only ones with the time and interest to chase winmodem problems 

good luck

---

### Post by _duncan_ on 2010-08-03
It seems someone was able to get a USB zoom modem 3095 to work in [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1484323") thread.

---

### Post by cody1233 on 2010-08-06
Alrite...Thanks to everybody that has helped me, and thanks to you i am doing this from my ubuntu laptop...what i did:went to linuxant website and downloaded dgcmodem srivers for my kernel version, then installed them, then type the tty address into the pppconfig serial port thing, then use pon then poff, then type the tty address into the gnome dial thing then i was up!!!


Thanks!

---

