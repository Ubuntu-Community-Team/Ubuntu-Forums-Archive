---
title: "BCM4313 [14e4:4727] RFMON/Packet-injection , possible?"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by hamidk on 2010-10-31
Hi, 

I`m trying to enable RFMON & Packet-injection for my BCM4313 card,
but no luck so far. I've tried many tips and tricks I searched, solving the issue on
broadcom cards, but non seems to work for 4313 model.

Card is currently operational by 'wl' driver.

Card currently works fine for daily use, by using broadcom-sta driver, how ever no way to get it to work the way I want. While I got disappointed about a way to patch current driver, and noticed that b43 (or it`s patched version) does NOT pick up BCM4313 (b43 works fine for 4312 though) , I noticed the new open-source driver BRCM80211 that seems be a possible replacement for current 'wl' driver. 
I tried the new brcm80211, after rmmod current wl & b43 drivers, but brcm80211 did not initiated or detected anything = no wifi interface.

Any comments on how to get this card into RFMON/Injection mode?
previously I've opened similar thread on another[ forum]("http://www.backtrack-linux.org/forums/beginners-forum/33133-broadcom-bcm4313-wl-not-work-mon-inject.html"), with no useful response.

Just in case, I`m running 2.6.35-22 x64 (ubuntu 10.10)

---

### Post by nabiladeeb on 2010-11-20
**[FONT=Arial][SIZE=2]hi, I have [/SIZE][/FONT]**[B][B][FONT=Arial][SIZE=2]brcm80211 driver working for my card. RFMON is working but still working on packet injection. see the link below for installing the driver.
If you have any luck with packet injection let me know.

[/SIZE][/FONT][/B][/B]**[http://ubuntuforums.org/showthread.php?p=10107880](http://ubuntuforums.org/showthread.php?p=10107880)**

---

### Post by hamidk on 2010-11-21
Thanks for the comment,
but, Are you using exactly the same Broadcom card model as mine? (BCM4313)

[Edited:]

Just wrote to confirm that the new source from git IS working on bcm4313 too.
Thank you very much for the link you provided.

Just to note, unlike what you said , I also confirm that packet injection is working too.
[Edit 2:]
Injection is working but NOT stable and as it should. farther investigations required.

---

### Post by hamidk on 2010-12-13
I'm still playing with brcm80211 and some progress since the last time I posted here.
Below I`m sharing some details, to help others who have stuck in same problem:

----
Note & to entire thread :
 I've recompiled and installed a fresh brcm80211 git today (13 dec) and card
 performance and sensitivity (better probe and detection of networks) seems have
 been improved.

Updated:
   Ok, Seems now I`m stuck in situation where Lupius is at. No data-packets in RFMON.
   Just in case others have problem making their environment work, here`s quick comment on how to make
   things work, till this stage

1-Get latest brcm80211 driver from git. No need to use git client and  get entire repository. you can get just brcm80211 snapshot by visiting  [http://2.gp/c4nb](http://2.gp/c4nb) and get only the latest brcm80211 snapshot.

2-Apply changes to Makefile in snapshot, as mentioned here [http://2.gp/c4ne](http://2.gp/c4ne)  and follow other steps described there for building and loading  brcm80211 . After this, your card will be able to pass RFMON and  injection test. but the annoying "-1" channel in aireplay-ng is still  there.

3-Get latest compat-wireless driver from [http://2.gp/c4nf](http://2.gp/c4nf)

4-Apply [http://patches.aircrack-ng.org/chann...ne-maxim.patch]("http://patches.aircrack-ng.org/channel-negative-one-maxim.patch")  to compat-wireless , build and install patched drivers. This will fix  the "-1" channel bug, and aireplay-ng will now be able to work as  expected.

5-At this stage, everything seems ok but as mentioned, in RFMON mode,  brcm80211 is NOT getting data packets and just process beacons. Now wait  for this bug to be fixed too, and read updates here, OR the better  choice is to keep working on this issue, find the solution, and report  back here


---------

More on this here : [http://2.gp/c4p2](http://2.gp/c4p2)

Please leave a comment if you've found a workaround for lack of data packets in RFMON.

---

### Post by juanfpina on 2010-12-19
Hello I'm new to all this. I have the same Broadcom chip in my laptop, id 14e4:4727, and I was wondering if anything can be done to get this to work with aircrack? Should I just buy a usb wifi dongle instead? Thanks in advance.

---

### Post by t0nj0uR5 on 2011-04-27
Thanks a lot for your posts hamidk. 
A firmware for BCM4313 has been released with stability fixes. i hope this would be working fine. Lemme know if this works fine for you people too. Thank you.

[http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=e4379d14549cd9b29988cf3c5b74b29d2051dd09](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=e4379d14549cd9b29988cf3c5b74b29d2051dd09)

---

### Post by gps3dx on 2012-03-02
Almost one year later...

Can someone PLEASE help me getting my BCM4313[14e4:4727] card to work properly with AirCrack-ng ??

PLEASE HELP !
What do I need to change ?
drivers?
firmware ?
patches ?
i'm confused !:confused:

I need instuctions like hamidk published... but a bit more specific...

I use natty, and my card right now freeze natty, when i try to "ifconfig wlan0 up" after I enter to monitor mode.

Thanks in advance to the savior !:P

---

### Post by bohemian9485 on 2012-07-11
Can't help on posting something to this old thread.

As of Ubuntu 12.04, Broadcom BCM4313 chipset is using the brcmsmac driver (I think it was introduced in 11.10, that's when my wireless card start working). [COLOR=Blue]**[Linux Wireless]("http://linuxwireless.org/en/users/Drivers")**[/COLOR] states that packet injection is still not possible for this model. I tried using latest compat-wireless build but it seems there's a bug in brcmsmac module and the driver failed to compile. B43 driver has the injection capability but I have yet to try that.

---

