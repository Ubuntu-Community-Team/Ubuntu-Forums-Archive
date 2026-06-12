---
title: "How to mount sansa clip+ ?"
date: 2011-06-25
forum: Multimedia Software
---

### Post by orengolan on 2011-06-25
I tried to follow the advice given here - 
[http://forums.sandisk.com/t5/Clip-Clip/Sansa-Clip-Firmware-01-01-35-amp-02-01-35-Release/td-p/144965](http://forums.sandisk.com/t5/Clip-Clip/Sansa-Clip-Firmware-01-01-35-amp-02-01-35-Release/td-p/144965)
but it's not working for me.

here are the steps:

Mac and Linux users can connect their Clip in MSC mode and follow the instructions below.

MSC mode instructions:
[LIST=1]
[*]Turn on the Clip
[*]Put the device in Hold (move Hold button until orange is showing)
[*]Press and hold the Center Button
[*]Plug the mini-USB connector into the device (be sure the USB is plugged into the computer)
[*]Wait for the Clip drive to mount
[*]Follow instructions below and drag files to the Clip drive
[/LIST]


any tips/advice would be appreciated!

---

### Post by Yellow Pasque on 2011-06-25
The directions are for a Clip. I have a Clip+ and I don't have to do anything special to mount it other than plugging it in.

---

### Post by orengolan on 2011-06-25
I solved it by upgrading the firmware.
I had to use a windows machine, and install the firmware updater app. 
[http://kb.sandisk.com/app/answers/detail/a_id/156/~/sansa-firmware-updater-and-firmware-defined](http://kb.sandisk.com/app/answers/detail/a_id/156/~/sansa-firmware-updater-and-firmware-defined)

after updating it ubuntu/debian recognize it.

---

### Post by texla on 2011-07-17
My Sansa Clip+ kept unmounting in Ubuntu after a few minutes.  I had to change it to MSC mode to make it function correctly in Ubuntu - the instructions are like what's above and the other sansa players can be changed with info from the link below.

[COLOR=#0000ff]Sansa Clip+[/COLOR]
1. Turn device OFF.
2. Press and hold the center button while connecting the device to the PC.

[http://kb.sandisk.com/app/answers/detail/a_id/61/kw/msc%20change]("http://kb.sandisk.com/app/answers/detail/a_id/61/kw/msc%20change")

EDIT:  Here's the kicker - I have to do this EVERY time I connect it to my computer.  not fun...

---

### Post by Futurian on 2011-08-22
I had a similar problem, couldn't mount a 4GB clip+ in 11.04. I wanted to transfer audio files from a Truecrypt file on a USB flash drive to the clip+. I plugged the flash drive and the clip+ into the two USB ports on my USB keyboard. Nautilus saw the flash drive, and the Truecrypt "drive" on it, but did not see the clip+. (USB mode on the clip+ was set to "MSC".)

After trying  number of other suggestions, without success, I moved the clip+ from a port on the keyboard to a USB port on the computer box. Nautilus recognized it immediately, and the file transfer (from the flash drive/Truecrypt file to the clip+) proceeded without any additional drama.

I hope this helps someone.

---

### Post by ieShae5d on 2012-01-05
I need some help!
 
I turned on MSC mode on the SanDisk Sansa Clip+, itself, and Joli OS (based on Ubuntu 10.04) recognized the device in the Nautilus graphical file manager. However, despite that I could see the device's generic directories (do you call that the "filesystem"?), I could not see the .mp3 -- or any other format of -- music files that I had already uploaded to the device from Windows 7. What gives?
 
Any help would be greatly appreciated.

---

### Post by Chronon on 2012-01-06
My best guess is that you loaded media onto the player while in MTP mode.  Because of that you can't have any way of knowing where the files are actually located when you look at the file system with a file browser (e.g. Nautilus).  

If you're set on using MSC mode, your best bet is to put it in MTP again, remove those files, then use MSC mode from now on.

---

### Post by cottfcfan on 2012-01-06
I had a similar problem.
When loading media from Windows 7 onto the sansa, it wasn't recognized by Linux. Windows does something to it.
I just make sure I only use it in Linux now.

---

### Post by ieShae5d on 2012-01-11
> **esternot said:**
> I need some help!
 
I turned on MSC mode on the SanDisk Sansa Clip+, itself, and Joli OS (based on Ubuntu 10.04) recognized the device in the Nautilus graphical file manager. However, despite that I could see the device's generic directories (do you call that the "filesystem"?), I could not see the .mp3 -- or any other format of -- music files that I had already uploaded to the device from Windows 7. What gives?
 
Any help would be greatly appreciated.

Update:

To get the SanDisk Sansa Clip Plus to work in Joli OS (based on Ubuntu 10.04), I had to back up my music files to my 64-bit Windows 7 operating system and then format the Clip Plus.

I then had to download the firmware updater from [http://forums.sandisk.com/t5/Clip-Clip/Sansa-Clip-Firmware-Update-01-02-16/td-p/150227](http://forums.sandisk.com/t5/Clip-Clip/Sansa-Clip-Firmware-Update-01-02-16/td-p/150227) and install it in Windows. I couldn't just install the firmware update automatically; the Clip Plus claimed it was already at 1.02.16A, but to get the thing to be recognized in Joli OS (Ubuntu 10.04), I still had to MANUALLY update it with the latest firmware from SanDisk (available at [http://forums.sandisk.com/t5/Clip-Clip/Sansa-Clip-Firmware-Update-01-02-16/td-p/150227](http://forums.sandisk.com/t5/Clip-Clip/Sansa-Clip-Firmware-Update-01-02-16/td-p/150227)).

To do that, I had to extract it from the compressed .zip file I had downloaded from SanDisk and then had to copy the .bin file containing the latest firmware to the Clip Plus.

I let the firmware update take place on the Clip Plus after disconnecting it from my computer. I then went into the Clip Plus's Settings menu and changed the storage mode to "MSC" instead of "Auto" or "MTP" mode.

Once I copied the music files back onto the Clip Plus from Windows 7, I could see its directories and .mp3 files in Joli OS (Ubuntu 10.04). Some people said they were having issues with seeing music files in Ubuntu 10.04 that they had copied from Windows, or vice versa, but I can attest that this solution worked for me, at least when copying files from Windows and being able to see them in Joli OS (Ubuntu 10.04). I haven't tried it the other way around.

---

### Post by Chronon on 2012-01-12
I'm pretty sure those steps were sufficient but not necessary.  Not being able to see files synced via MTP is common when switching to MSC.  It shouldn't require formatting and changing the firmware.  But I'm glad you found a procedure that worked for you.

---

