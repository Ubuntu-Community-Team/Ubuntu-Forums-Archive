---
title: "[SOLVED] Tascam US-122 howto: Alsa Firmware Link broken"
date: 2008-09-23
forum: Multimedia Software
---

### Post by Mzwo on 2008-09-23
hi,

the link mentioned [here]("https://help.ubuntu.com/community/TASCAM_US-122") won't work - anybody know of the up to date location?

thanks,

Mzwo

---

### Post by Mzwo on 2008-09-24
*bumpety*

anyone?

Mzwo

---

### Post by Mzwo on 2008-09-25
... echo ...

---

### Post by Baloroth on 2008-09-28
Hi there!

I googled a little bit and found this link, working perfectly:

ftp://ftp.uniroma2.it/{E/Linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm

Hope you get it working

---

### Post by Mzwo on 2008-09-29
thanks! just out of interest: what did you google for? all my searches yielded zilch ...

will try and report back.

Mzwo

---

### Post by Baloroth on 2008-10-02
I simply googled for "alsa-firmware-1.0.9-4.noarch.rpm",

the first result was a page with about 20 links to the file, some were broken, but the last link worked fine, i got my card running by now:D

---

### Post by Mzwo on 2008-10-03
i see. could have figured it out myself, really .... 

my card's working too, playback at least. recording won't. is yours working both ways?

Mzwo

---

### Post by Baloroth on 2008-10-05
My card works both ways with jack audio server, the only problem is that on bootup the LED stays off, but if unplug/plug it again, everything's fine

how do you check your recording? do you use jack or simply via Alsa?

I had only problems with my playback on another machine,
sorry

---

### Post by Mzwo on 2008-10-06
same boot-up problem here - i resorted to booting first, plugging second and not a problem. 

my grasp of all things jack is as yet somewhat limited - i think i simply used alsa and nothing came through. haven't had the time yet to fiddle, though, will try and report back. am almost certain that i missed something fairly obvious. 

playback works a treat. 

Mzwo

---

### Post by EggplantOfFire on 2008-10-06
Ok, totally ignorant here, I have a tascam us-122 looking to get it working with my fresh install of Ubuntu Studio on Hardy. I found the alsa-firmware-1.0.17 thing and downloaded it. I unzipped it and tried the ./configure but that failed. not sure why. Am I doing the right thing by doing the ./configure thing? 
I'm really not sure what I'm doing, which I know is dangerous. I'm learning though. I've been searching everywhere for info and I can't seem to find anything for a complete noob to linux. I'd appreciate any help I can get.

Edit: Nevermind, I fixed it

---

### Post by Mzwo on 2008-10-09
@ baloroth: works a treat with jack, problem solved.
@ eggplantoffire: i know how you feel. i had, and still have, next to no clue as to what i'm doing. somehow, following instructions worked eventually. glad you worked it out.

Mzwo

---

### Post by Baloroth on 2008-10-09
glad you workd it out,

just for interest, how high is your latency, 
are you using the realtime kernel?

On my machine i have 23 ms, don't know if the RT-Kernel would help that much


Baloroth

---

### Post by Mzwo on 2008-10-10
hi,

real time is enabled in jack setup (if that's what you mean), but my latency, according to qtjack setup is 46.4 - no idea if that's good or bad. 

running ubuntu studio, so i guess i ma running the realtime kernel (don't think i've got a choice there, do i?).

sorry for the incompetent answers, i'm just a dumb user .. ;-) 

Mzwo

---

### Post by Mzwo on 2008-10-10
@baloroth: i've encountered strange crashing problems: [http://ubuntuforums.org/showthread.php?t=943450](http://ubuntuforums.org/showthread.php?t=943450)

would that have anything to do with the tascam?

cheers,
Mzwo

---

### Post by fgomes on 2008-10-11
Hi, I've followed this tutorial for installing Tascam US-122 on a fresh install of Ubuntu Studio 8.04:

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

replacing the link for the alsa firmware by this:

ftp://ftp.uniroma2.it/{E/Linux/opensuse/distribution/SL-10.0-OSS/inst-source/suse/noarch/alsa-firmware-1.0.9-4.noarch.rpm

as suggested by Baloroth. When I execute lsusb I got

Bus 004 Device 002: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw)

Then I execute:

sudo fxload -s ~/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/004/002

and lsusb result change to:

Bus 004 Device 003: ID 1604:8007 Tascam US-122 Audio/Midi Interface

So the first phase of firmware is ok (the ID changed from 8006 to 8007, I don't know if the USB device should change, it has changed also from device 002 to device 003)

Then, if I execute 

sudo usx2yloader

The result is:

usx2yloader: no US-X2Y-compatible cards found

Can you give some tip to help solve the problem? I already reinstalled the operating system,m but the result is the same :-(

Thanks!

Fernando

---

### Post by Baloroth on 2008-10-12
@ mzwo:seems like I'm not that bad on with my latency though i'm using standart Ubuntu without RT

Concerning your system crashes I have absolute no ideas, sorry

@ fgomes: The changing of your ID and your Device Number indicates that your first satage firmware was loaded correctly, so far everything allright.

Try to name usx2yloader the device it schould load,try:

        usx2yloader -c1

I had the same problem an got it solved by this, but don't ask me why the card isn't detected automaticly, i have no idea.

Hope I could help, please report back if it helped you or not

Baloroth

---

### Post by Mzwo on 2008-10-12
@ baloroth: seems as if the sreensaver has something to do with it. deactivated it => no more crashes. also, i choose gnome under "session" when logging in, seems to help too. previously i logged in choosing "xscripts" (whatever that means. you wouldn't know, would you :-))
regarding latency: 1024 seem to work fine for me, lower latency not required. i stopped enabling rt in jack, btw - if enabled, i get an error message saying that jack is "unable to mlock port buffers: cannot allocate memory" and, consequently ardour is letting me know that it may run out of memory before the system does, since memory is locked. no idea what that means either or how to solve this problem - rt disabled, all fine. 

@ fgomes: try plugging in your box AFTER booting, leaving it unplugged during bootup. works for me (i followed the same steps as you have) and the card is detected automatically every time. 

Mzwo

PS @ fgomes: do you have automatic updates enabled? because, if i'm not mistaken, the card only started to work after i got the latest version of alsa-firmware (install using the old version as linked to above, though).

---

### Post by fgomes on 2008-10-12
> **Baloroth said:**
> 
Try to name usx2yloader the device it schould load,try:

        usx2yloader -c1

I had the same problem an got it solved by this, but don't ask me why the card isn't detected automaticly, i have no idea.

Baloroth

After the first phase finished, I have the following result for
 
cat /proc/asound/cards

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe8f4000 irq 17
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfeae8000 irq 20
 2 [USX2Y          ]: USB US-X2Y - TASCAM US-X2Y
                      TASCAM US-X2Y (1604:8007 if 0 at 002/003)

So I tried your sugestion with 

usx2yloader -c2

and the result is:

usx2yloader: cannot open the index file /lib/firmware/usx2yloader/us122.conf

I don't know why it is trying to open us122.conf in that directory, it isn't there!

And about the Mzwo comment for the automatic updates, I have them enabled, and even tried to make an apt-get update, but it says the system is updated :S 
What is the alsa-firmware available at the ubuntu repositories? I will try to check why it doesn't update to a more recent version, after installing the alsa-firmware according to the tutorial referred above.
I didn't try the Mzo suggested trick of unplugging the unit during the boot process and plugging it after, I'll try this tonight :-)

Any more ideas?

Thanks :-)

---

### Post by Mzwo on 2008-10-13
you might get lucky here:

/usr/share/alsa/firmware/usx2yloader

should be a simple case of cut'n'paste. 

:-)

Mzwo

---

### Post by fgomes on 2008-10-13
> **Mzwo said:**
> you might get lucky here:

/usr/share/alsa/firmware/usx2yloader

should be a simple case of cut'n'paste. 

:-)

Mzwo

:-) Yes, I will try that, I'll copy the content from the folder:

/usr/share/alsa/firmware/usx2yloader

to this one:

/lib/firmware/usx2yloader

Do you know why it is looking for the file in this folder, instead of looking into the correct one? It is strange that there is no error logged, and didn't find any configuration file where this could be configured. I only noticed this error when trying to force usx2yloader using the parameter -c2.

Thanks

Fernando

---

### Post by Mzwo on 2008-10-13
i remember reading about this problem somewhere (can't find the link to save my life, though >:-( ) - apparently, in earlier disributions, this path would have been correct, but hardy looks for the things it needs elsewhere. whyever it would do so. 
 

sorry, can't be much more technical - user only :-) 

Mzwo

---

### Post by fgomes on 2008-10-13
> **Mzwo said:**
> 
sorry, can't be much more technical - user only :-) 
Mzwo
And a very useful user, shall I say :D
Bingo, problem solved! I made a copy f the folder 

/usr/share/alsa/firmware/usx2yloader

to

/lib/firmware/usx2yloader

It works even without -c2 parameter, only calling usx2yloader and the leds light up!
Now I have to test it, but at least the second phase worked! Perhaps a symlink would be better.
Thanks for your help! Perhaps some reference to this problkem should be included in the wiki [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122) ?

Fernando

---

### Post by Mzwo on 2008-10-14
!found the link:

[http://alsa.opensrc.org/index.php/Tascam_US-122](http://alsa.opensrc.org/index.php/Tascam_US-122)

and here:

[http://ubuntuforums.org/showthread.php?t=734730](http://ubuntuforums.org/showthread.php?t=734730)

quite why the last link never came up in any of my searches in this forums, heaven knows. i don't. 

glad it worked :-)

Mzwo

---

### Post by pneaveill on 2008-10-23
Ok, I give up and asking questions here.  I have been working on the US-122 for over close to a year now and have not gotten it and am not sure why.  Hoping someone can lend a hand on this please.  Still running [COLOR=Blue]7.10 gutsy[/COLOR] (yes, I understand it is a year old) on wife's computer she absolutely has to have running and not wanting to grock anything with it.

knowing from past experience: 

[INDENT]root@studio:~# lsusb
Bus 001 Device 004: ID 0781:b6b7 SanDisk Corp. 
Bus 001 Device 003: ID 04cc:1122 Philips Semiconductors Hub
Bus 001 Device 002: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0644:800e TEAC Corp. 
Bus 002 Device 002: ID 8086:1120 Intel Corp. 
Bus 002 Device 001: ID 0000:0000 
[/INDENT]
Somehow lost soundblaster live card (emu10k1) :( yet, 


[INDENT] root@studio:~#cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SBLive! Value [CT4831]
                      SBLive! Value [CT4831] (rev.7, serial:0x80311102) at 0xdf80, irq 19
[/INDENT]> root@studio:~/alsa-firmware-1.0.16# sudo apt-get install fxload alsa-base alsa-firmware-loaders alsa-tools alsa-tools-gui alsa-utils alsamixergui alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fxload is already the newest version.
alsa-base is already the newest version.
alsa-firmware-loaders is already the newest version.
alsa-tools is already the newest version.
alsa-tools-gui is already the newest version.
alsa-utils is already the newest version.
alsamixergui is already the newest version.
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up timidity (2.13.2-15ubuntu1) ...
 * Starting timidity                                                             * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntustudio-audio:
 ubuntustudio-audio depends on timidity; however:
  Package timidity is not configured yet.
dpkg: error processing ubuntustudio-audio (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 timidity
 ubuntustudio-audio
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone have ideas on this?

---

### Post by Mzwo on 2008-10-24
lsusb doesn't seem to show your us-122 - sure it's working properly? even before i got it to work lsusb would have listed the box as connected. 

Mzwo

---

### Post by pneaveill on 2008-10-26
> **Mzwo said:**
> lsusb doesn't seem to show your us-122 - sure it's working properly? even before i got it to work lsusb would have listed the box as connected. 

Mzwo

Guess am confused. Is this not it?

```

root@studio:~# lsusb
Bus 001 Device 004: ID 0781:b6b7 SanDisk Corp. 
Bus 001 Device 003: ID 04cc:1122 Philips Semiconductors Hub
Bus 001 Device 002: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 001 Device 001: ID 0000:0000  
[COLOR=Blue]** Bus 002 Device 003: ID 0644:800e TEAC Corp. **[/COLOR]
Bus 002 Device 002: ID 8086:1120 Intel Corp. 
Bus 002 Device 001: ID 0000:0000
```

---

### Post by Baloroth on 2008-10-28
Hi,
your card should be detected as 

```
phil@ubuntu-phil:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

or with another ID, for the ID is 1604:8006 if the firmware isn't loaded

I would susbect you to try it on another PC, perhaps one with 
Windows (I know, bad bad thing ;-)), because  normally lsusb 
displays the card, doesn't matter if it's working or not, so better 
check if it's working at all

Baloroth

---

### Post by pneaveill on 2008-10-28
> **Baloroth said:**
> Hi,
your card should be detected as 

```
phil@ubuntu-phil:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```or with another ID, for the ID is 1604:8006 if the firmware isn't loaded

I would susbect you to try it on another PC, perhaps one with 
Windows (I know, bad bad thing ;-)), because  normally lsusb 
displays the card, doesn't matter if it's working or not, so better 
check if it's working at all

Baloroth

Ok. I committed treason and booted into the windows side of the dual boot and it did not work from there despite 3 attempts to load the software into m$ windoze.:(

What is frustrating is that the green light comes on at bootup and the midi in light also work, but nothing goes in or out from there. Will try to send it in under warranty.  Thanks for the assist on this.

---

### Post by Mzwo on 2008-10-30
> **pneaveill said:**
> Guess am confused. Is this not it?

```

root@studio:~# lsusb
Bus 001 Device 004: ID 0781:b6b7 SanDisk Corp. 
Bus 001 Device 003: ID 04cc:1122 Philips Semiconductors Hub
Bus 001 Device 002: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 001 Device 001: ID 0000:0000  
[COLOR=Blue]** Bus 002 Device 003: ID 0644:800e TEAC Corp. **[/COLOR]
Bus 002 Device 002: ID 8086:1120 Intel Corp. 
Bus 002 Device 001: ID 0000:0000
```

hi,

teac coporation is right - however, my card shows up as Baloroth mentioned above. did the box ever work?

Mzwo

edit: ignore this. should start reading post properly .... 
sorry to heat about the result. good luck with the warranty!

Mzwo

---

### Post by smaba on 2008-11-08
Hey I got a problem with my Tascam US-122, too. Since I upgraded to Kubuntu Ibex my Tascam only works every second time I boot. That means I always have to boot up twice in order to get my LED's on. I tried all the HOWTO'S and also copied the usx2yloader-folder to the right place.

It even detects my Tascam, but the lights are still not on and the card won't work before I boot up again:

lsusb
Bus 005 Device 002: ID 046d:09a4 Logitech, Inc.
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 006: ID 1604:8007 Tascam US-122 Audio/Midi Interface**
Bus 002 Device 004: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Any ideas what's going wrong here?

thanks a lot

smaba

---

### Post by Mzwo on 2008-11-08
quick question: does un- and replugging do the trick as well?

just upgraded to 8.10 myself literally minutes ago, the box seems to work, however i think i noticed that the lights will only come up every second time it's plugged in. i'll keep an eye on it and will report back.

Mzwo

---

### Post by smaba on 2008-11-09
With Hardy replugging did the trick. But not anymore under Ibex...unfortunately :(

---

### Post by Mzwo on 2008-11-09
strange. 

i'm not convinced by ibex either - graphics won't work properly. sort of regretting the upgrade already ...

good luck sorting things out.

Mzwo

---

### Post by jstaples on 2008-11-26
If I may jump in here, I am desperate for help with this same issue.  I am brand new to linux of any flavor.  I installed Ubuntu Intrepid Ibex so that I could try out Rose Garden.  I set it up as a dual boot on an Acer TravelMate C310. Install was flawless.  Then I discovered Ubuntu studio which I was able to install with a little more trouble.  I then tried to hook up My Tascam US-122 which I was previously using on this same machine with Cubase LE in windows XP.  I have tried all the things written in this thread as well as here: [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)   I just can't seem to get this thing working.  I'm sure I just have something in the wrong place.

I moved the usx2yloader folder to root/lib/firmware/  

typing lsusb at the command prompt shows 
Bus 003 Device 002: ID 1604:8006 Tascam US-122 Audio/Midi Interface (without fw).  

john@john-laptop:~$ usx2yloader
usx2yloader: no US-X2Y-compatible cards found

Alas, the coveted green light still eludes me

---

### Post by dweebazoid on 2008-12-21
Dunno if this will help anyone, but I've managed to get my card working on Ibex

I followed the same tutorial that a lot of you have probably followed and spent 3 or 4 hours banging my head against the desk, like most of.  Then I read an article advising me to create a symlink between my /usr/share/alsa/firmware/usx2yloader folder and /lib/firmware/usx2yloader like so:

sudo ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader

Now I get the green light!  The only problem is that I have a fair amount of feedback coming out of my speakers right now so I need to fix that.  But at least I have sound.  Feedback sounds better than nothing.

---

### Post by pneaveill on 2008-12-22
Will have to try that after the holidays. Meanwhile, somehow lost all sound drivers or something even from the internal creative card.  Meanwhile, I have that green light and even get the midi light; but that is all.

---

### Post by pneaveill on 2008-12-22
Noticed this is your first post. Welcome to the forums.

> **dweebazoid said:**
> Dunno if this will help anyone, but I've managed to get my card working on Ibex

I followed the same tutorial that a lot of you have probably followed and spent 3 or 4 hours banging my head against the desk, like most of.  Then I read an article advising me to create a symlink between my /usr/share/alsa/firmware/usx2yloader folder and /lib/firmware/usx2yloader like so:

sudo ln -s /usr/share/alsa/firmware/usx2yloader /lib/firmware/usx2yloader

Now I get the green light!  The only problem is that I have a fair amount of feedback coming out of my speakers right now so I need to fix that.  But at least I have sound.  Feedback sounds better than nothing.

---

