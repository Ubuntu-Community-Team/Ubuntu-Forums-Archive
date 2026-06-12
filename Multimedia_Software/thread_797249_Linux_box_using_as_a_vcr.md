---
title: "Linux box using as a vcr"
date: 2008-05-17
forum: Multimedia Software
---

### Post by andlinux on 2008-05-17
Hi

I have installed the latest Ubuntu 8.04 on a computer and it has a tv-card (wintv). I already tried mythtv but that's not my thing.
So does somebody know a good program what I can use to record tv programs ?

---

### Post by cotcot on 2008-05-17
TVtime

---

### Post by MeKino on 2008-05-17
I found vlc best. Check out this link

[http://ubuntuforums.org/showthread.php?t=758845](http://ubuntuforums.org/showthread.php?t=758845)

---

### Post by andlinux on 2008-05-17
Tvtime can't record.

And If with vlc is not so user friendly, difficult to change a channel and program a time to record.

---

### Post by MeKino on 2008-05-17
You may (not) have noticed in my link that I show how to record with vlc using crontab.

There is an application called MonkeyRemote which may work with vlc although I haven't tried it.

---

### Post by steefjeqv on 2008-05-17
Hi,

If you're planning to use DVB TV then I can recommend VDR :

[http://www.vdr-portal.de/board/portal.php]("http://www.vdr-portal.de/board/portal.php")

[http://www.vdr-wiki.de/wiki/index.php/Hauptseite]("http://www.vdr-wiki.de/wiki/index.php/Hauptseite")

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

There's a version available in the Ubuntu repositories (Synaptic).

It can be a bit tricky to get it configured, but (in my opinion) it sure was worth the effort.

Greetings,
Steven

---

### Post by andlinux on 2008-05-17
> **steefjeqv said:**
> Hi,

If you're planning to use DVB TV then I can recommend VDR :

[http://www.vdr-portal.de/board/portal.php]("http://www.vdr-portal.de/board/portal.php")

[http://www.vdr-wiki.de/wiki/index.php/Hauptseite]("http://www.vdr-wiki.de/wiki/index.php/Hauptseite")

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

There's a version available in the Ubuntu repositories (Synaptic).

It can be a bit tricky to get it configured, but (in my opinion) it sure was worth the effort.

Greetings,
Steven
I installed VDR and kvdr but how do I start it ? When I write vdr in a console then it gives me a message: 
```
vdr: can't access video directory /var/lib/video.00
```
I already made that directory manualy but it doesn't work.

---

### Post by steefjeqv on 2008-05-17
Hi,

In terminal :

sudo chmod 777 /var/lib/video.00

This should solve the error message.

But this isn't all you'll have to do.

Most importantly : what kind of tv card do you use (analog, digital ?).

Greetings,
Steven

---

### Post by andlinux on 2008-05-17
> **steefjeqv said:**
> Hi,

In terminal :

sudo chmod 777 /var/lib/video.00

This should solve the error message.

But this isn't all you'll have to do.

Most importantly : what kind of tv card do you use (analog, digital ?).

Greetings,
Steven
I have an analog tv card (Wintv from hauppauge).

Indeed I have to do more, if I give the vdr command now then I get this:
```
vdr: no primary device found - using first device!
```

---

### Post by steefjeqv on 2008-05-17
Hi,

If you're Hauppauge card is a PVR (hardware mpeg2) version, then you can use VDR.

Otherwise, I'm afraid you're going to have to look for another solution.

Greetings,
Steven

---

### Post by andlinux on 2008-05-17
> **steefjeqv said:**
> Hi,

If you're Hauppauge card is a PVR (hardware mpeg2) version, then you can use VDR.

Otherwise, I'm afraid you're going to have to look for another solution.

Greetings,
Steven
I'm not sure if that card has mpeg2 hardware, I need to look that up. It's an old card...

---

### Post by steefjeqv on 2008-05-17
Hi,

Just type the following in your terminal :

sudo lspci

This will list all your pci devices.

Greetings,
Steven

---

### Post by wolfen69 on 2008-05-17
i have a Hauppauge pvr card and installed Mythbuntu. it comes with the xfce desktop, but i installed the regular ubuntu desktop and absolutely love it. works kind of like a tivo. i highly recommend it.

---

### Post by andlinux on 2008-05-18
> **steefjeqv said:**
> Hi,

Just type the following in your terminal :

sudo lspci

This will list all your pci devices.

Greetings,
Steven
This is what I get: 
```
00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)


00:0b.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0b.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)


```

---

### Post by Cuppa-Chino on 2008-05-18
in gnome just install me-tv for simple tv, but I am unsure if it works with analog cards

---

### Post by andlinux on 2008-05-18
> **Cuppa-Chino said:**
> in gnome just install me-tv for simple tv, but I am unsure if it works with analog cards

The card works perfect, I already installed kdetv. But I want a program so that I can record a tv program and set a time to start record.

---

### Post by Chris Musampa on 2008-05-18
> **wolfen69 said:**
> i have a Hauppauge pvr card and installed Mythbuntu. it comes with the xfce desktop, but i installed the regular ubuntu desktop and absolutely love it. works kind of like a tivo. i highly recommend it.

Word to that brother, Mythtv rocks and mythweb is the D's Bs.  The only small gripe I have with it is that it would be handy if the frontend was a resizable window.

---

### Post by Porpoise on 2008-07-06
Alternatively, you can use v4l2 to control the card (I use these methods personally):

The device setting (usually) for Hauppauge PVR-150:  /dev/video0:
```

v4l2-ctl --device=/dev/video0

```Then the standard (I'm in europe-west/PAL):
```

v4l2-ctl --set-standard=pal

```To select inputs:
```

v4l2-ctl --set-input=0    #for Tuner 1
v4l2-ctl --set-input=1    #S-Video 1
v4l2-ctl --set-input=2    #Composite 1
v4l2-ctl --set-input=3    #S-Video 2
v4l2-ctl --set-input=4    #Composite 2

```If using the Tuner as input, then to select channels:
```

v4l2-ctl -f 711.250    #Frequency: 11380 (711.250000 MHz) (BBC 1)
v4l2-ctl -f 655.250    #Frequency: 10484 (655.250000 MHz) (BBC 2)
v4l2-ctl -f 631.250    #Frequency: 10100 (631.250000 MHz) (ITV 1)
v4l2-ctl -f 679.250    #Frequency: 10868 (679.250000 MHz) (CHA 4)

```This method requires your default (PAL, SECAM, NTSC) and region settings to have previously been set (for which you can also use ivtv-tune as previously mentioned).
Further information and the various switches for v4l2-ctl can be found here: [http://ivtvdriver.org/index.php/V4l2-ctl](http://ivtvdriver.org/index.php/V4l2-ctl)

Obviously, if you are in a different location/using a different system, you will need to use the relevant frequencies.

Then, the VLC command-line to record:
```

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'

```Or, if you wish to view the stream whilst recording:
```

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts,dst="/home/steve/Desktop/raid-partition/DVCR/filename.mpg"}}'

```This method allows you to use the same command for capture irrespective of input/channel settings - you can set the input/channel individually without having to mess about editing the VLC command-line each time.

There is also a utility called TV-Viewer available which gives you a GUI for TV Channel switching

As previously mentioned, if you wish to do timed recordings you can use a cron job.

I tried MythTV and found that it was way over the top for simply wanting to watch TV and/or record programmes or capture video from external devices. Also, I still haven't been able to get it to actually produce a TV picture!?! Maybe I'll try it again one day but it the meantime, I've found the above method far simpler!

---

