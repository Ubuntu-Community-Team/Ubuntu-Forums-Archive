---
title: "Sound Blaster Live External USB problems"
date: 2006-01-31
forum: Multimedia &amp; Video
---

### Post by cbs2186 on 2006-01-31
Hey all,

I just installed an Ubuntu Dual boot on my laptop (IBM T42) and am having trouble getting my Sound Blaster Live External USB card to work.  It works fine on the Windows partition, but in Ubuntu it fails.  Using music players, there is a lot of static.  I can barely make out the song.  Also, i was trying to play StepMania (Dance Dance Revolution ripoff) and it gives me an error that it "Error: Couldn't find a sound driver that works".

I think I've installed the Alsa drivers properly, and I can't figure out how to fix this.  I'm new to Linux, so I'm pretty much going to need someone to hold my hand through this.  Thanks.

---

### Post by cbs2186 on 2006-01-31
oh, I'm running Hoary, by the way

System config is:
1.7 Ghz Intel Centrino
512 MB RAM
USB Sound Blaster Live
128 MB ATI Video (not sure of model)
IBM T42 Laptop

i don't know how much that will help, but I figure it's worth a shot

---

### Post by FarEast on 2006-02-02
Hi,

> I think I've installed the Alsa drivers properly
Please paste the output after executing 'cat /proc/asound/cards' from the
command line :).

---

### Post by cbs2186 on 2006-02-06
```
$ cat /proc/asound/cards
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with AD1981B at 0xc0000c00, irq 11
1 [External       ]: USB-Audio - SB Live! 24-bit External
                     Creative Technology SB Live! 24-bit External at usb-0000:00:1d.7-4.4, full spee

```

I can get sound with my laptop's internal speakers, but nothing with the externals right now

---

### Post by Ptero-4 on 2006-02-06
Can you disable the built-in soundcard (0 [I82801DBICH4 ]: ICH4 - Intel 82801DB-ICH4
Intel 82801DB-ICH4 with AD1981B at 0xc0000c00, irq 11)
It may be conflicting with the external one.

---

### Post by cbs2186 on 2006-02-06
how would i go about disabling the card?  I'm relatively new to Linux.

---

### Post by FarEast on 2006-02-07
Enter BIOS setting on boot and look for items regarding built-in sound chip.
If you cannot disable it, describe the following in /etc/modprobe.d/sound .
```
options snd-usb-audio index=0
options snd-intel8x0 index=1
```
Then execute 'sudo update-modules' and restart the system.

---

### Post by cbs2186 on 2006-02-07
I don't have a "/etc/modprobe.d/sound" file/folder.  should I make one in "/etc/modprobe.d/" or do I need something else?  is this a file or folder?

---

### Post by cbs2186 on 2006-02-07
ok, I did the sound options thingy and I now get sound from the speakers... however it has a lot of static and buzzing when a sound plays.  it will only play system sounds and does not play music.  any suggestions?

---

### Post by stangbang on 2006-02-08
define sounds vs music. Are you just having problems with playing mp3's now, or is it that you can only get beeps?

---

### Post by cbs2186 on 2006-02-08
I cannot play mp3 files.  I do get sounds like GAIM sounds or the little boop when I open firefox.  However these are accompanied by a lot of static.  My Alsamixer is set at 50%, so I don't think i'm overdriving anything.

---

### Post by FarEast on 2006-02-08
> I cannot play mp3 files.
Are you playing them with xmms?  I think there is an item in the preferences
to specify sound output device.  I am not sure, though(Here I am using a
Windows machine).

> However these are accompanied by a lot of static.
> My Alsamixer is set at 50%, so I don't think i'm overdriving anything.

How about tweaking input levels by tweaking the volume control?
It is shown by double-clicking the volume on the upper panel.

---

