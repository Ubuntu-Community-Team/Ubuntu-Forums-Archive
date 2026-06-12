---
title: "Rhythmbox, MTP, and MSC on ubuntu 12.04LTS 64bit"
date: 2014-10-06
forum: Multimedia Software
---

### Post by pi6502 on 2014-10-06
Hello,

my android stock rom was version 4.2.2. To make Rhythmbox (2.96 version in 12.04 LTS) recognize the device as music player, I had MSC (mass storage) activated, put a .is_audio_player in root directory and synched my music on my android's external sd card. It was pretty straightforward, i.e. drag and drop from Rhythmbox to the music player device icon.

I had to upgrade my android with Cyanogenmod 11, which gave me android version 4.4.4. MSC is gone and I'm left with MTP. Despite using the portable player MTP plugin, no music device is recognized within Rhythmbox. When I plug the device, nautilus opens, I see  "internal storage" and "sd card" and I can copy the files with nautilus, but it's not exactly the same (I have to reconstruct folder hierarchy on sd card, something that Rhythmbox did automatically). I tried banshee and Clementine - both show me the player, but synching is not very successful at all (takes too long, returns timeout, or apps crash).

If I could at least use gnome-commander here, but I can't find where the sdcard is mounted to.

I also tried airdroid, but apart from feeing a little overkill, it still doesn't sync my music's folder structure, i.e. I must manually create them.

Any help would be greatly appreciated, thanks!

---

### Post by zebul on 2014-12-12
I have the same problem.

My phone shows up in nautilus or the launcher bar,being recognized as a MTP device. It shows both the sd card the internal memory in nautilus.

But I did not see anything in rhythmbox. I don't know where it is supposed to show up.

Even though this is not recommend, I am thinking of adding my user to the audio group to see if it changes anyhting. because the usb device for the phone is of the audio group only.

lsusb
[...]
Bus 003 Device 005: ID 22b8:2e82 Motorola PCS

 ls -l /dev/bus/usb/003/005crw-rw----+ 1 root audio 189, 260 déc.  12 21:06 /dev/bus/usb/003/005

---

### Post by David2009 on 2014-12-29
I have just loaded up Rhythmbox for the first time.  I have moved 100% away from Windows.  Have first CD in the computer to get it to my MP3 player.  I'll put in the iPhone 5S, and iTouch 4th Gen...which has most of my music.

---

### Post by Vladimir_Oufa on 2014-12-30
On 14.04 LTS I see my music and video files, but not able to play them.

I unlock my Phone ( currently S5 with Android 4.4 ), then I plug it on USB, 20 secondes later Phone appear in Nautilus

I see files through ls -l /run/user/$(id -u)/gvfs/mtp*/

I see music and video in Rhythmbox, but it crashes when trying to play them

MTP is a mess, should be replaced by a robust open protocol

---

