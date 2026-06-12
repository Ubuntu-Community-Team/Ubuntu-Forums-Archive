---
title: "Pinnacle PCTV HD Card 800i and TVtime problems"
date: 2009-05-30
forum: Multimedia Software
---

### Post by vicmaxabcd on 2009-05-30
Hy guys! I installed Ubuntu 9.04 few days ago and I'm struggling to make my tv tuner working. :(

I tried a lot of programs MythTV, TVtime, Kaffeine, etc.... and TVtime is the only one that is kinda "working"

 lspci

> vicmaxabc@vicmaxabc-lnx:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
03:02.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
03:03.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:03.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:03.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)THX

---

### Post by efolse on 2009-05-30
Ok, been using that tuner for a while.  Did you update the firmware? (google pinnacle 800i mythtv and get [http://www.steventoth.net/linux/xc5000/](http://www.steventoth.net/linux/xc5000/))  you will need to follow the directions by going into the directiory where you download the file and type at a terminal prompt "bash extract.sh"  it will prompt you for the unzip program if now installed.  follow the directions.  after that you will need to reboot to recongnize the card.

Then you will be choosing to do the backend set-up with the applications>system>backend setup in the menu.  You will choose the 2 capture card option.  Add a new card.  We need two entries first use the arrow keys and choose dvb dtv capture (it thinks it is a samsung).  choose options and tell it to use the card on demand only and not for a dvb eit scan

Yes, you can go on and install the card again (it will be a 800i) but I did not bother.
The card is now installed.  Next is Schedules Direct.  Set it up on the Schedules Direct site first then on mythtv then on the video souces section.

Next is the input connections section.  (use the DVB part of the card as the attached point and forget about the antlog part.)
next is the channel editor section, where you will do a channel scan full scan.  Then channel scan and full scan of existing transports.  By the way, make sure that you chose cable or broadcast tv from the general section first.  Do a scan for missing icons and that should be that.

Sound is a problem on my machine but, may be ok on yours.  So, I will not bother with that detail.  After you are finished and have run mythfilldatabase once go back in the channel editor and rescan for missing Icons.

Let me know if that helps.

---

### Post by vicmaxabcd on 2009-05-30
I already did the firmware upgrade, but thank you for the advice. I figured out how make my tuner to work with tvtime, but I don't have sound at all. :(

---

### Post by efolse on 2009-05-30
I have been trying all day to get tvtime any ideas?

---

### Post by vicmaxabcd on 2009-05-30
Nothing special, i just installed tvtime and i'm running the following command 

```
arecord -D hw:2,0 -r 32000 -c 2 -f S16_LE | aplay | tvtime -d /dev/video1 -i 2
```

But after few seconds I've got a huuuuge delay between picture and sound :(

---

### Post by efolse on 2009-05-31
Do you want me to walk you through mythtv?  I have been using it for a while.  If so, install mythfrontend and mythbackend, then let me know.

Also, me-tv use to work pretty well, we could try that.

---

### Post by vicmaxabcd on 2009-05-31
I don't know why but mythtv never worked on my computer. I tried to install it on a clean install of ubuntu but still didn't work. But on my laptop is running ok.

I think that there is smth with my video card. Because my laptop's vidoe card is from nvidia.

This is how mythtv looks on my computer:

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
```

---

### Post by cam295 on 2009-06-15
I followed the instructions above to upgrade the firmware and have great video now, but I don't have any audio.  Any suggestions?  I'm not even sure where to start.

---

### Post by watchreader on 2009-06-21
> **vicmaxabcd said:**
> Nothing special, i just installed tvtime and i'm running the following command 

```
arecord -D hw:2,0 -r 32000 -c 2 -f S16_LE | aplay | tvtime -d /dev/video1 -i 2
```But after few seconds I've got a huuuuge delay between picture and sound :(

:O

How did you discover that?  I'm having the exact same problems with the exact same card btw.  I've also noticed that although I've tweaked it around a bit, the picture still looks kind of cruddy compared to what I got under WinampTV when i was running windows :(.  I've also noticed that the audio mashup problem becomes worse when I go to full screen.  I would think that would slow down my video and not my audio, but there you have it.

---

