---
title: "Video works in Firefox- but no DVD/ video on pc otherwise"
date: 2009-01-28
forum: Multimedia Software
---

### Post by saffagirl on 2009-01-28
Hi guys,

I'm using Hardy latest kernel.  I have vostro 1310- have had endless issues with it, the latest kernel wiped my video, unmapped my dvd eject button and I lost sound. The sound I understand I've had to compile the driver every new kernel. The video and dvd /cd support is just plain annoying.

I can see video in youtube, but nothing in mplayer or anything else. I've posted before and haven't had much joy.

Has anyone got a workaround, at the moment I've found .19 is at least stable and been chosing that from grub.

---

### Post by saffagirl on 2009-01-28
BUMP 

Anyone?

---

### Post by UbuntuNerd on 2009-01-28
I haven't try mplayer yet only because my pc plays everything with "totem" if you like to give a try just follow this guide:
[http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem](http://my.opera.com/ubuntunerd1/blog/how-to-play-quicktime-videos-and-other-media-with-totem)

---

### Post by saffagirl on 2009-01-29
Hi Ubuntunerd,

thanks for your help. All those plugins are already installed. My video works in .19 kernel. I get failed to connect to stream: invalid argument.

This applies to Mplayer; totem; Gstreamer.

Do you have any other ideas?

---

### Post by saffagirl on 2009-01-29
Bump

---

### Post by saffagirl on 2009-02-03
Bump- can anyone help? I've not had playback/ sound since Nov.

---

### Post by mc4man on 2009-02-03
Put a dvd in the drive and then run this in the terminal and post what's listed for *cdrom

```
sudo lshw -C disk
```

---

### Post by saffagirl on 2009-02-03
Here's the log for you.

2 things- could my lack of sound be the problem as well? The video is not playing in either avi standalones on my hd or on dvds.

thanks in advance.

 *-cdrom                 
       description: DVD-RAM writer
       product: DVD+-RW DVW28SLC
       vendor: TEAC
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: A.06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready

---

### Post by mc4man on 2009-02-05
Your lshw looks fine - indicates that a dvd was in the drive and mounted properly at /media/cdrom0

Why don't you see if you can resolve dvd playback first. 
Here's simple 2 min. method (from terminal, 1 at a time
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 vlc totem-xine libxine1-ffmpeg
```

(feel free to remove totem-xine libxine1-ffmpeg, really only need vlc to troubleshoot. Totem-xine is a totem player that actually is pretty good at dvd's, unlike the default totem-gstreamer.

After everything is installed, insert a dvd, if totem opens close it out.
Open vlc and go settings -> preferences. Click the little button " Advanced options"
Expand the audio tree, highlight "Output modules" and in drop down on right switch from 'Default' to 'Alsa audio output'. Click save.
Now go to file -> open disc -> ok and see what happens.

If no go or quality issues stop playback if any, close vlc, and try again but open vlc from a terminal with just this and post output
```
vlc
```

---

### Post by saffagirl on 2009-02-08
Hi, thanks for the helpful reply. I've done all your suggestions however still no joy I'm afraid- I've installed totem-xine / vlc; all the same problem. I get the copyright notice, but nothing else as soon as vlc gets to the main movie, the window opens and closes again- nothing plays, same goes for any .avi file as well.

I can't choose alsa or any other sound- this kernel has messed up my sound and my soundcard is not being recognised (it's alc228); I've had to recompile in the past, but the fix isn't working anymore. .19 is the last kernel which actually worked on my machine.

---

