---
title: "MSI Mega Sky 580 &amp; m920x/gl861"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by uggeli on 2006-12-16
Hi!

I just got my MSI Mega Sky 580 yesterday and while I noticed it was the "PC-DTV Receiver" version I desided to not even try it on linux. But after several several Blue screen of death in windows I was thinking that I got to get this work on linux and did some searching again. I found [[color=blue]this thread on gentoo forum[/color]](http://forums.gentoo.org/viewtopic-t-477817.html) and noticed that there is now driver for  "PC-DTV Receiver" as well as "DTV USB MINI":

[quote=cyrus@gentoo-forums]
Please report if the driver works for your device when you have tried it.
And if you have the 0db0:5580 (m920x) or the 0db0:5581 (gl861) version.
[/quote]

My "PC-DTV Receiver" ID is 0db0:5581, so this should work with gl861 driver if I got it right. The only problem is that I don't know how to install those drivers. I would appreciate very much if some of you could give some "step by step" guide of driver installation.


Edit: Forgot to but this link (it's in gentoo forums link though) : [http://linuxtv.org/hg/~mkrufky/megasky](http://linuxtv.org/hg/~mkrufky/megasky)


Edit2: Found allso these pages: [http://silverkat.pbwiki.com/MSI_MEGASKY580](http://silverkat.pbwiki.com/MSI_MEGASKY580)
                                                           [http://www.spinics.net/lists/linux-dvb/msg13420.html](http://www.spinics.net/lists/linux-dvb/msg13420.html)


I don't know if there's any help with those links, but just trying to add something here and hoping to get an answer. :)

---

### Post by uggeli on 2006-12-17
Up


Anyone?

---

### Post by juveyfruit on 2006-12-28
Following up from the previous post.

I have a Mega Sky 580, id version 0db0:5580 (m920x).  I downloaded the driver source code from [http://linuxtv.org/hg/]("http://linuxtv.org/hg/").  Searched for section ~mkrufky/megasky on that webpage and found the source code.

The source code is located at [http://linuxtv.org/hg/~mkrufky/megasky?ca=tip;type=gz]("http://linuxtv.org/hg/~mkrufky/megasky?ca=tip;type=gz") as a .gz file.

OR

[http://linuxtv.org/hg/~mkrufky/megasky?ca=tip;type=bz2]("http://linuxtv.org/hg/~mkrufky/megasky?ca=tip;type=bz2") as a .bz2 file.

I compiled using:

```
sudo make install
```

and encountered the following errors:

[HTML]
root@sam-desktop:/usr/src/megasky-11fa5f80d049# make install
make -C /usr/src/megasky-11fa5f80d049/v4l install
make[1]: Entering directory `/usr/src/megasky-11fa5f80d049/v4l'
Stripping debug info from files:
Usage: strip <option(s)> in-file(s)
 Removes symbols and sections from files
 The options are:
  -I --input-target=<bfdname>      Assume input file is in format <bfdname>
  -O --output-target=<bfdname>     Create an output file in format <bfdname>
  -F --target=<bfdname>            Set both input and output format to <bfdname>
  -p --preserve-dates              Copy modified/access timestamps to the output
  -R --remove-section=<name>       Remove section <name> from the output
  -s --strip-all                   Remove all symbol and relocation information
  -g -S -d --strip-debug           Remove all debugging symbols & sections
     --strip-unneeded              Remove all symbols not needed by relocations
     --only-keep-debug             Strip everything but the debug information
  -N --strip-symbol=<name>         Do not copy symbol <name>
  -K --keep-symbol=<name>          Do not strip symbol <name>
     --keep-file-symbols           Do not strip file symbol(s)
  -w --wildcard                    Permit wildcard in symbol comparison
  -x --discard-all                 Remove all non-global symbols
  -X --discard-locals              Remove any compiler-generated symbols
  -v --verbose                     List all object files modified
  -V --version                     Display this program's version number
  -h --help                        Display this output
     --info                        List object formats & architectures supported
  -o <file>                        Place stripped output into <file>
strip: supported targets: elf32-i386 a.out-i386-linux efi-app-ia32 elf32-little elf32-big elf64-x86-64 elf64-little elf64-big srec symbolsrec tekhex binary ihex trad-core
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/usr/src/megasky-11fa5f80d049/v4l'
make: *** [install] Error 2
root@sam-desktop:/usr/src/megasky-11fa5f80d049#[/HTML] 

From there on, I have no idea, hopefully someone else can help.

---

### Post by mock_alien on 2006-12-29
Hello,
I (also) have bought the MSI dvb-t device
(i have a 0db0:5581 Micro Star International)

Any help making this device work would be really appreciated.

/kind regards
Mike

---

### Post by mock_alien on 2006-12-29
and oh, i found a (in process working) firmware.
But i just don't know what to do with it.
(it's bound to be buggy, but at the moment this is all i got)

---

### Post by uggeli on 2007-01-13
Hi again.

I got my Mega Sky working now, thanks to joggey & Juhhe1 from Ubuntu Finnish forum! Anyway here is whatI needed to do :

```

sudo apt-get install mercurial linux-headers-`uname -r` build-essentials
hg clone http://linuxtv.org/hg/~mkrufky/megasky
make distclean
make update
hg merge
make
sudo make install

```

After that I just installed Kaffeine and libxine-extracodecs package and Kaffeine was ready to rock'n roll. Oh and by the way, I didn't need that firmware package mentioned earlier at all.

---

### Post by juveyfruit on 2007-01-14
Thanks for the last post.

I did the same procedure and compiled with no errors.  But I couldn't  get kaffeine to use the tuner properly.  For some reason it picks up the dvb device as a Zarlink MT352 DVB-T.  Is this right?

Problems: 
1. It scans but cannot pick up the channels.
2. When Kaffeine loads it comes with an error: DVB-client "cannot bind info socket"

---

### Post by uggeli on 2007-01-17
> **juveyfruit said:**
> Thanks for the last post.

I did the same procedure and compiled with no errors.  But I couldn't  get kaffeine to use the tuner properly.  For some reason it picks up the dvb device as a Zarlink MT352 DVB-T.  Is this right?

Problems: 
1. It scans but cannot pick up the channels.
2. When Kaffeine loads it comes with an error: DVB-client "cannot bind info socket"

Do you have PC-DTV Receiver or DTV USB MINI model of the device? I have PC-DTV Receiver and Kaffeine identifies it as Zarlink ZL10353 DVB-T. I'm sorry but I can't help much with the problems, hope someone else can. I got channels scanned easilly after I selected country/area where I am. If I remember correctly I couldn't manage to get channels (or at least all of them) with auto configuration (I allso had antenna problems at first), but I'm not 100% sure if I remember it right. Anyway after all I was lucky and my device is working, but on the other hand there are some cases at Finnish forum with same model as I have, but those won't work. 

So I'm sorry I can't help you (quite a forever newbie myself), and is it state of moon that  I got mine working :), but nevertheless first successfully saving of movie was in linux, in windows all I got was blue screen of death. Hopefully you got yours working allso.


PS. If you have m920x chipset version (DTV USB MINI) of device, then according to gentoo forum link which I but in first post, that model won't work yet. But I don't know if things have changed since that last comment there.

---

### Post by kandd on 2007-02-03
Hi,
i have the MSI MegaSky 580 too and I have switched 1 month ago from WinXP to Ubuntu. So far I'm very happy but my DVB-T Stick doesn't work. Of course I'm quite noob with Linux and so I have some questions.

I installed Kaffeine and libxine-extracodecs. Then I wrote the following in the terminal

sudo apt-get install mercurial
hg clone [http://linuxtv.org/hg/~mkrufky/megasky](http://linuxtv.org/hg/~mkrufky/megasky)
make distclean
make update
hg merge
make
sudo make install

and everything was ok.

But it doesn't work. I didn't do the following "you allso need build-essentials and kernel headers" because I dont know what I should do.

Can someone help me to get working the MSI DVB-T Stick plz?

Thank so far

K and D

---

### Post by uggeli on 2007-02-06
> **kandd said:**
> 

I installed Kaffeine and libxine-extracodecs. Then I wrote the following in the terminal...

...and everything was ok.

But it doesn't work. I didn't do the following "you allso need build-essentials and kernel headers" because I dont know what I should do.

Can someone help me to get working the MSI DVB-T Stick plz?

Thank so far

K and D


I added installation of linux-headers & build-essentials to above, since my text obviously was confucing. I had those allready and that's why I leave those off (was telling what I did).

Anyway since you said "everything was ok" you must have everything installed what was needed. Unfortunately I can't  tell what to do if your MSI stick wont work that way. Even I got mine working with help of joggey & Juhhe1 from Ubuntu Finnish forum, I just updated that info in this thread, and even in that Finnish forum not everyone got their stick working. Maybe I was lucky one, after not so lucky testings in XP. Hopefully someone can help you out.

---

### Post by kandd on 2007-03-02
> **uggeli said:**
> I added installation of linux-headers & build-essentials to above, since my text obviously was confucing. I had those allready and that's why I leave those off (was telling what I did).

Anyway since you said "everything was ok" you must have everything installed what was needed. Unfortunately I can't  tell what to do if your MSI stick wont work that way. Even I got mine working with help of joggey & Juhhe1 from Ubuntu Finnish forum, I just updated that info in this thread, and even in that Finnish forum not everyone got their stick working. Maybe I was lucky one, after not so lucky testings in XP. Hopefully someone can help you out.

Perfect, now it works. Thanks to Uggeli and Finnish Ubuntu Forum. You're great. 

[www.ubuntu.bz](www.ubuntu.bz)

---

### Post by Mr. J007K4 on 2007-03-03
Thank you for these instructions. They helped me a lot.

I had some trouble  with these commands:

```

hg clone http://linuxtv.org/hg/~mkrufky/megasky
hg merge

```

After some detective work I found out that some code merges had changed the url to ~mkrufky/qt1010. I believe that the current url now is ~mkrufky/v4l-dvb.

The "hg merge" didn't do anything. I wonder what it was supposed to do.

Finally I got the tuner working and installed mythtv. I noticed that the remote worked as a some kind of keyboard just like the Hauppauge remote from my former PC. So I followed three first steps of jon_benges exellent tutorial:

[http://www.ubuntuforums.org/showthread.php?t=183545&highlight=lirc+hauppauge+remote](http://www.ubuntuforums.org/showthread.php?t=183545&highlight=lirc+hauppauge+remote)

with lircd.conf from:

[http://www.lemis.com/grog/HOWTO/mythtv-setup.html](http://www.lemis.com/grog/HOWTO/mythtv-setup.html)

Since I couldn't get irrecord working I had to name the remote buttons and fish the remote codes with:

```

sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n
irw            # in a different terminal

```

Lastly I created my own lircrc with the help of:

[http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper#Configure_Remote](http://www.mythtv.org/wiki/index.php/Lirc_on_Ubuntu_Dapper#Configure_Remote)

and

[http://wilsonet.com/mythtv/tips.php](http://wilsonet.com/mythtv/tips.php)      on mythpowerbutton.sh.

I Noticed that irexec requires ~/.lircrc so I made it to be a symlink to ~/.mythtv/lircrc and ensured irexecs startup by adding "irexec -d" to System - Preferences - Sessions - Startup Programs.

I Noticed that Channel Up and Vol+ keys aren't working on my remote. Do you have this problem as well?

Ubuntu Dapper 2.6.15-28-686, 0db0:5581 Micro Star International

---

### Post by pljones on 2007-03-04
> ~mkrufky/v4l-dvb
Ah!  Finally I'm getting somewhere with this DVB-T stuff...

---

### Post by pljones on 2007-04-07
...except with these drivers I've been getting complete deadlocks with the -lowlatency kernel...

---

### Post by mock_alien on 2007-06-16
Hi!
I have tried this step by step instruction and it seems to be working, alas i can only get one channel sometimes, but that's life.
BUT my usb2 webcam is not working anymore... what can i do?

after i done sudo make install

how do i revert?(if i want to remove the driver)
sudo make uninstall?

/kind regards
Mike

---

### Post by potnoodles on 2007-10-23
I have read this thread but I am confused as to what to do to start up the megasky 580 .

It seems I only need to turn on the USB device to access its functionality.(check this post)

[http://ubuntuforums.org/showthread.php?t=587130](http://ubuntuforums.org/showthread.php?t=587130)

Perhaps I should have submitted  that post  here.

regards,

potnoodles

edit - my problem now solved - see link

---

### Post by juveyfruit on 2007-11-27
Referring to the following thread:

[http://ubuntuforums.org/showthread.php?t=587130]("http://ubuntuforums.org/showthread.php?t=587130")

It seems that in Gutsy it is possible to load the Megasky device in warm state by making sure that the firmware is loaded into your current kernel folder.  I am using 2.6.22-14-generic (please change to suit your system).

```
sudo cp dvb-usb-megasky-02.fw /lib/firmware/2.6.22-14-generic/dvb-usb-megasky-02.fw
```

The file is attached in this post.

Unfortunately I am now stuck because I cannot successfully pick up any channels after scanning.  I can pick up all available channels in Windows.

---

### Post by potnoodles on 2007-12-15
> **juveyfruit said:**
> Referring to the following thread:

[http://ubuntuforums.org/showthread.php?t=587130]("http://ubuntuforums.org/showthread.php?t=587130")

It seems that in Gutsy it is possible to load the Megasky device in warm state by making sure that the firmware is loaded into your current kernel folder.  I am using 2.6.22-14-generic (please change to suit your system).

```
sudo cp dvb-usb-megasky-02.fw /lib/firmware/2.6.22-14-generic/dvb-usb-megasky-02.fw
```

The file is attached in this post.

Unfortunately I am now stuck because I cannot successfully pick up any channels after scanning.  I can pick up all available channels in Windows.

I am using  Kaffeine with the Megasky  and it picks up all the channels just fine - I can even enter the PIDs for TVX and get that working in Kaffeine.

regards,
Potnoodles

---

### Post by rebski on 2008-03-20
In fact there are two MSI Mega Sky 580s. Although the packaging and branding look exactly the same in reality they are two different models internally. The chipsets are different and so are the drivers. 

One is reported under Windows as PC-DTV Receiver, details as: -
Genesys Chip, Zarlink ZL10353 DVB- T, Product ID 0x5581 
I have been unable to get it to work under Linux.

The other is reported under Windows as a DTV-Mini Receiver details as: -
Zarlink MT352 DVB-T, Product ID 0x5580, Drivers 5.1.2600.1031 17/11/2005 
This works perfectly with Kaffeine.

Another DVB-TV USB stick that works perfectly for me with Kaffeine is the MSI Digi Vox
[http://global.msi.com.tw/index.php?func=proddesc&prod_no=619&maincat_no=132&cat2_no=&cat3_no=](http://global.msi.com.tw/index.php?func=proddesc&prod_no=619&maincat_no=132&cat2_no=&cat3_no=)

I hope this information is useful to someone looking for a Linux TV setup.

---

### Post by Freebirth One on 2008-06-24
> One is reported under Windows as PC-DTV Receiver, details as: -
Genesys Chip, Zarlink ZL10353 DVB- T, Product ID 0x5581 
I have been unable to get it to work under Linux.

Exactly this one am I using, and it's running ootb.

Sticking into an USB Port, starting Kaffeine, looking how something is downloaded by big K, and than having a running dvb-t - device.


I have running my Notebook with Ubuntu Hardy, perhaps there have been changes to apply compatibility.

---

