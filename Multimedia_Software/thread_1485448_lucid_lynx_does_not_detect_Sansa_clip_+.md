---
title: "lucid lynx does not detect Sansa clip +"
date: 2010-05-16
forum: Multimedia Software
---

### Post by rey1321 on 2010-05-16
hey guys, I can't mount my sansa clip +
It doesn't charge the battery either 

this is my lsusb output: (usb mode:MSC)

rey@rey-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 001 Device 006: ID 0781:74d0 SanDisk Corp. [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rey@rey-desktop:~$ 

My dmesg|tail:

[ 3953.664108] usb 1-5: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 128 rq 6 len 1000 ret -110
[ 4011.596032] usb 1-5: usbfs: USBDEVFS_CONTROL failed cmd mtp-detect rqt 128 rq 6 len 1024 ret -110
[ 5165.897217] usb 1-5: USB disconnect, address 17
[ 6833.764265] hub 1-0:1.0: unable to enumerate USB device on port 5
[ 6835.448040] [COLOR="Red"]usb 1-5: new high speed USB device using ehci_hcd and address 19[/COLOR]
[ 6840.580250] usb 1-5: unable to read config index 0 descriptor/start: -110
[ 6840.580258] usb 1-5: chopping to 0 config(s)
[ 6850.580205] usb 1-5: string descriptor 0 read error: -110
[ 6850.580376] usb 1-5: no configuration chosen from 0 choices
[ 6851.704060] usb 1-5: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 128 rq 6 len 1000 ret -110


MY MTP-detect (USB-MODE MTP)

mtp-detect
libmtp version: 1.0.2

Listing raw device(s)
Device 0 (VID=0781 and PID=74d0) is a SanDisk Sansa Clip+.
   [COLOR="Red"]Found 1 device(s):
   SanDisk: Sansa Clip+ (0781:74d0) @ bus 1, dev 19[/COLOR]
Attempting to connect device(s)
LIBMTP PANIC: Unable to find interface & endpoints of device
Unable to open raw device 0
OK.


as you can see, my sansa is detected it
[COLOR="Red"]Id 0781; 74do 
[/COLOR]but I can't not see it anywhere!
not at desktop, nor filesystem,nor under media folder or under mount folder

PLEASE HEELPPPPPP!!!!

---

### Post by scorpio74 on 2010-05-30
It wouldn't mount for me when on the Clip+ Settings->System Settings->USB Mode was set to AutoDetect or MTP.

The solution: I set it to MSC it worked. It looks like you already had it set to MSC mode though.

My USB ID is 0781:74d1 and I updated the firmware recently.

It's funny.. it worked for me on Ubuntu versions prior to Lucid by being set to AutoDetect.

---

### Post by a z on 2010-05-30
same problem for me, too.
i first solved this (sort of) by logging out, THEN plugging in the Clip+, then logging back in. That worked, but certainly a hollow victory.
Next I found this Ubuntu help page:
[https://help.ubuntu.com/10.04/musicvideophotos/C/music-portable.html](https://help.ubuntu.com/10.04/musicvideophotos/C/music-portable.html)
and installed mtpfs and mtp-tools as prescribed.

now...

It works like you'd expect, only it seems to be mounting with root permissions, and I can only drag  (or copy/paste) files in or out of it with "gksudo nautilus". Rrr...

a z

---

### Post by a z on 2010-05-30
bump

---

### Post by rey1321 on 2010-06-02
Hi guys , I still have the problem
I already installed the mtp-tools, and everything
the Official Ubuntu guide said about
mp3 players, One weird thing is that it can
be detected by my friend's computer, he is using
Lucid too, I tried in a Windows Vista home edition
and it detected too with no problem.:sad:

---

### Post by MetaMs on 2010-06-02
I have the problem. The mtp-tools were already installed in my player. The player freezes when I open it with the Sansa Clip plugged in.

This is not good. I have two Sansa Clips which I use for classes that I receive via mp3.

I REALLY want to stay with Ubuntu. But I'm getting very discouraged. It's OK for my netbook where I just check emails and Facebook. But for my "real" computer, I keep being forced back to Windows.

A very sad Newbie

---

### Post by dimeotane on 2010-06-23
Same problem here on Lucid, solved by setting to MSC in the player settings.
I was puzzled at first because it worked when I plugged it into my karmic netbook, but not into my other computer running Lucid.

> The solution: I set it to MSC it worked.

---

### Post by hangturi on 2010-06-25
i have the same problem when plug my Sansa device...Media Player device error! Unable to open SanDisk Sansa Express device. This OS cannot  detect my DVD rom, USB Sansa express, luckily i'm not fully converted to Ubuntu, have no problem with Window looks like we still need the fence and the wall and Gates.

---

### Post by BigJules on 2010-06-25
Have you changed the SANSA device itself to MSC? Go to its Settings > USB Mode and set it to MSC. I have 2 of them and like everything else they work perfectly on Lucid. Nothing wrong with the OS...

A dream to manage with gPodder, too.

BTW, found this site v helpful, if you want to do a SANSA Clip firmware upgrade in Ubuntu, deal with corrupt file sys etc:

[http://www.anythingbutipod.com/forum/forumdisplay.php?f=119](http://www.anythingbutipod.com/forum/forumdisplay.php?f=119)

---

### Post by hangturi on 2010-06-26
Thank you BigJules, but my Sansa is Express not Clip. I did go to setting but could not find USB mode in it so could not set MSC. In the pass i use kubuntu and it detect my Sansa Express and my DVD rom. but this time with Lucid Lynx nothing, i am new with this and not an expert but i will always us Kubuntu hoping it get better.

---

### Post by ancientrustic on 2010-06-30
I had the same problem with a fresh install of Lucid. Installing VLC player solved the problem. I hope this helps someone else.

---

### Post by vlke on 2010-07-11
> **scorpio74 said:**
> It wouldn't mount for me when on the Clip+ Settings->System Settings->USB Mode was set to AutoDetect or MTP.

The solution: I set it to MSC it worked. It looks like you already had it set to MSC mode though.

My USB ID is 0781:74d1 and I updated the firmware recently.

It's funny.. it worked for me on Ubuntu versions prior to Lucid by being set to AutoDetect.
Sorry to be pain, but where exactly is "Settings > System Settings" tab that allows to switch to MSC? I looked through all SYSTEM menus and I can't seem to locate anything related to USB. I sort of feel like this should be directly on the MP3 player, but obviously since I can't mount the mp3 player I can't click on its settings because my computer doesn't recognize it. So what I am missing here?

---

### Post by vlke on 2010-07-11
> **vlke said:**
> Sorry to be pain, but where exactly is "Settings > System Settings" tab that allows to switch to MSC? I looked through all SYSTEM menus and I can't seem to locate anything related to USB. I sort of feel like this should be directly on the MP3 player, but obviously since I can't mount the mp3 player I can't click on its settings because my computer doesn't recognize it. So what I am missing here?

I figured out a way how to change settings on the MP3 player itself and forcing it to MSC. Check [ScanDisk support page]("http://kb.sandisk.com/app/answers/detail/a_id/61") on how to force various models of Sansa players into MSC mode.

---

### Post by dwpbike on 2010-09-11
bump.  my sansa express works on ubuntu 9.10, but not ubuntu 10.4.  and given the nvidia/x11 issues, where is the incentive to "update"?

update:  sansa express is recognized on my 32 bit machine running 32 bit 10.4, but not my 64 bit machine running 32 bit 10.4.  nexus?

---

### Post by grayamf on 2010-10-19
I spent so much time digging for a solution to the sansa clip plus problem on lucid lynx. It showed in my "lspci" and "lsusb" commands, and "dmseg |tail" did not come up with any error. It was however not showing under "fdisk -l," or otherwise recognized on the lynx.

Including installing mtpfs and mtp-tools, flashing my firmware under windows, and other software upgrades under linux. Dig through the system preference switches in ubuntu and all that with no avail. 

Then I tried as this thread suggested, to **change mtp into msc mode**, and BOOM! Clip was recognized right away. If I had tried this earlier! Thanks a lot, folks!

---

