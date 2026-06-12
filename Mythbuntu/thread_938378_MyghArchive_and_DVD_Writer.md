---
title: "MyghArchive and DVD Writer"
date: 2008-10-04
forum: Mythbuntu
---

### Post by Buschbarber on 2008-10-04
I am new to Linux ans Mythbuntu. I am running Ultimate 1.9 and I successfully installed the drivers and firmware for my WinTV-HVR 1600 card.

I installed Mythbuntu Upgrade. MythTV works great.

I am trying to write a Recording to DVD. I am using MythArchive. I went into the Frontend Setup and defined a tmp directory. When I tried to write to DVD, it took almost an hour. I watched the log and there were no errors until near the end, the process halted when I received a message indicating that the Tray was open.

I have a Plextor 716A Internal DVD Writer, a Samsung Internal DVD Player, and an LG GSA-E60L External DVD Writer.

I cannot seem to find the Config screen to choose which DVD Writer to be the default. In the Archive Utilities Setup, I see a reference to /dev/dvd, but I do not know which drive that is.

Is there a way to speed up the process of writing a Recording to DVD?
How do I set the default DVD Writer?

---

### Post by ian dobson on 2008-10-05
Hi,

On my system the DVD-RW is /dev/scd0. You can set the DVD device by editing the settings table "DVDDeviceLocation" for your host name.

To findout which device name your DVD has go to the terminal change to root then try mounting the DVD and listing it's contents. Something like:-

mkdir /mnt/dvd
mount /dev/dvdX /mnt/dvd
ls /mnt/dvd
umount /dev/dvdX

where /dev/dvdX is the device that you think is your DVD.

On my frontend a "ls /dev/dv* -o" returns 
root@myth-frontend:~# ls /dev/dv* -o
lrwxrwxrwx 1 root 4 2008-10-05 07:34 /dev/dvd4 -> scd0
lrwxrwxrwx 1 root 4 2008-10-05 07:34 /dev/dvdrw4 -> scd0

so dvd4 and dvdrw4 are symbolic links to scd0.

Regards
Ian Dobson

---

### Post by Buschbarber on 2008-10-05
I found an application that came with Ultimate 1.9

Applications/Other/Devices and Filesystems

It defines my Plextor DVD Writer as/dev/scd0. What exactly does /dev/scd0 mean, technically, and why does /dev/dvdrw1 work, as well in MythArchive Settings?

I tried writing a DVD, from MythArchive, both as Create DVD and Create Native Archive.

Create DVD also includes a sub menu structure and chapters.
Create Native Archive produces an mpg file.

Why is it that I can turn on Commercial Flagging and the Recording skips Commercials, but when I burn that Recording to DVD, the Commercials are back?

---

### Post by klc5555 on 2008-10-06
> **Buschbarber said:**
> 

Why is it that I can turn on Commercial Flagging and the Recording skips Commercials, but when I burn that Recording to DVD, the Commercials are back?

You need to create a cutlist for the recording that incorporates the Commercial Flagging results. Then tell Mytharchive to honor that cutlist.

To do this (short version): begin watching your recorded program. While your recorded program is playing, bring up the menu (with the "m" key) and select "edit recording". Playback should stop, and a bright scrollbar appears at the bottom of the screen. You could cutlist the whole recording from this scrollbar, manually, if you wished, but if you prefer to incorporate the results of your Commercial Flagging job, just hit the "z" key. The Commercial Flagging results now appear along the scroll bar. You can edit further manually, or not. Whenever you're ready just hit the "m" key again, and the recording returns to playback, but you now have a cutlist, ready to go.

In mytharchive, when choosing recordings to be archived, there is a check box that will appear for each recording that has a cutlist, saying "honor cut list". Check this box for each recording on the DVD that this applies to, and mytharchive will eliminate the "unwanted segments" while transcoding the file.

This is all handled in more detail in the wiki doc: "Removing commercials" at 
[http://mythtv.org/wiki/index.php/Removing_Commercials](http://mythtv.org/wiki/index.php/Removing_Commercials)

Cheers!

---

### Post by Buschbarber on 2008-10-06
Thanks!! I will try that.

---

