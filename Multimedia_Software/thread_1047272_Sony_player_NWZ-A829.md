---
title: "Sony player NWZ-A829"
date: 2009-01-22
forum: Multimedia Software
---

### Post by adaglio on 2009-01-22
Hi everybody,
I would like to inform all of you that the player Sony NWZ-A829 and all those from the NWZ-A series are perfectly working on ubuntu 8.04.
Moreover with [AVIDEMUX]("http://fixounet.free.fr/avidemux/") you can convert video files into MP4 format with AAC as audio codec and enjoy the videos you like.

if anyone has problems I will be more than happy to help.

cheers

---

### Post by FlashBuster on 2009-04-14
Hi,

I can't seem to get the NWZ-A826 to work with the Jaunty beta,
Gnome offers me to browse or use Rhythmbox but nautilus just shows an empty folder and rhythmbox nothing.. any help?

---

### Post by maubarra on 2009-05-12
Hi, I hace this player too! What settings do you use for converting video with avidemux for the A829? I've tried MP4 (x264 & AAC) but the player doesn't play them.

Hope you can help

Thanks in advance!

---

### Post by robhem on 2009-10-12
Hey Aldo & Co, 

I'd love to hear how to get a Sony NWZ-A729 to work in Jaunty! I've been searching high and low for answers. I have the walkman mounting. But, not able to browse the contents in File Browser. Banshee, VLC, Rhythmbox etc show nothing. Anyone with any ideas please? 

Regards, 
Rab

---

### Post by McScruff on 2009-10-17
> **robhem said:**
> Hey Aldo & Co, 

I'd love to hear how to get a Sony NWZ-A729 to work in Jaunty! I've been searching high and low for answers. I have the walkman mounting. But, not able to browse the contents in File Browser. Banshee, VLC, Rhythmbox etc show nothing. Anyone with any ideas please? 

Regards, 
Rab

I too have this player and have not found a gtk app that works.  If you have KDE then use amarok, 

Start amarok then plug walkman in.  Simple and works.

---

### Post by robhem on 2009-10-25
I've had another go at this and have found the following steps will give me file access to my Sony NWZ-A729 on Jaunty/GNOME: 
 

[LIST]
[*]Plug device in to USB port and device is mounted (as SONY Corp. WALKMAN)
[*]Open the device in File Browser and it shows nothing at all (no files)
[*]Within File Browser, create a new directory on the player and leave it with the default name (untitled folder) as you can't rename it
[*]Open the new directory and you will see all the files and directories present on the device. You now have read/write access.
[/LIST]This works reliably for me. Problem solved. 
 
Regards, 
Rab
 
PS. Be sure you have the file .is_audio_player in the root of the player. My file contains the following text: 
 
audio_folders=MUSIC/,RECORDINGS/
folder_depth=2
output_formats=application/ogg,audio/x-ms-wma,audio/mpeg

---

