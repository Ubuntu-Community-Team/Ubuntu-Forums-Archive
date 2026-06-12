---
title: "frontend on eee box - screen goes black after a while"
date: 2009-02-21
forum: Mythbuntu
---

### Post by jfix on 2009-02-21
I've installed mythbuntu 8.10 yesterday on my brand new eee box using a 4gb usb stick as boot medium.

the install worked perfectly and an hour later, livetv was working.

today, I installed it behind the lcd tv (highest wife approval factor ever! look, no cables!) using the supplied vesa-compliant metal bracket.

all this to say that when watching tv (any channel), after an arbitrary period, sometimes 5 minutes, sometimes around 40 minutes, the screen goes dark.  sound continues.  I can still use the remote control to pause, continue, go back to main menu, but the screen remains black.

of course, I checked and disabled the screensaver (but this doesn't seem to have any influence either way), disabled all power saving options, to see what happens, but it is completely reproducible, except for the timing.

I haven't tested it for videos or without the mythfrontend yet.

does anybody else observed this behaviour, and possibly found an explanation and/or resolution?

I can supply more information, log files, etc.

thanks in advance,
Jakob.

---

### Post by fudnet on 2009-02-21
Even changing the power saving options doesn't always turn this off. Try running this from a terminal:
```
xset -dpms
```
and
```
xset s off
```

--Tim

---

### Post by jfix on 2009-02-22
ok, I tried what Tim suggested, but no change.

however, one observation:
just displaying the desktop worked fine without any problems, for hours.

when I used mythtv to watch a recording or live tv, however, screen goes blank/dark after a while.

I noticed the following (many many lines) in /var/log/messages just before the screen became dark:

```

===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83

```

apparently, this is to do with wireless networking.  so, I disabled wireless and no messages any more.  also, I then monitored the mythfrontend.log (which is put in /tmp?!):

```
[...]
Feb 22 15:12:55 teevee kernel: [  602.825245] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Feb 22 15:23:19 teevee -- MARK --
```

what else sh/could I look at?

thanks,
Jakob.

---

### Post by crez79 on 2009-02-22
Is it getting enough cooling? When it is playing a recording it used more cpu and makes more heat than sitting on the desktop. When things heat up they don't work right act 'screwy'. LCD tv's make a lot of heat which may not help. Try and put a fan blowing back there as best as possible to try to move some of the heat. It shouldn't take much. If your problems go away you just need to hook up a little fan to keep the air moving back there. Depending on your tv, there may be a usb service port or one for pictures and what not, that will provide 5v when the tv is on and that may be a convenient place to connect.

---

### Post by jfix on 2009-02-22
thanks for replying.  I put the eee box next to the lcd tv and installed hddtemp (couldn't make lm-sensors work for the moment), but the problem persists.

here's some log from mythfrontend.log just before it went black (it doesn't look related, but hey, it's the start of a recorded program):

```

2009-02-22 17:37:50.624 AFD: Opened codec 0x96fe5f0, id(MPEG2VIDEO) type(Video)
2009-02-22 17:37:50.624 AFD: codec MP3 has 2 channels
2009-02-22 17:37:50.625 AFD: Opened codec 0x9351010, id(MP3) type(Audio)
2009-02-22 17:37:50.625 AFD: codec MP3 has 2 channels
2009-02-22 17:37:50.625 AFD: Opened codec 0x933ad50, id(MP3) type(Audio)
2009-02-22 17:37:50.625 AFD: Opened codec 0xa503360, id(DVB_SUBTITLE) type(Subtitle)
2009-02-22 17:37:50.938 AFD: Opened codec 0x93305d0, id(MPEG2VIDEO) type(Video)
2009-02-22 17:37:50.938 AFD: codec MP3 has 2 channels
2009-02-22 17:37:50.939 AFD: Opened codec 0x93221d0, id(MP3) type(Audio)
2009-02-22 17:37:50.939 AFD: codec MP3 has 2 channels
2009-02-22 17:37:50.939 AFD: Opened codec 0x93e8450, id(MP3) type(Audio)
2009-02-22 17:37:50.939 AFD: Opened codec 0xa636dc0, id(DVB_SUBTITLE) type(Subtitle)
2009-02-22 17:37:50.943 Opening audio device 'default'. ch 2(2) sr 48000
2009-02-22 17:37:50.943 Opening ALSA audio device 'default'.
2009-02-22 17:37:50.968 mixer unable to find control Master 1
2009-02-22 17:37:51.237 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2009-02-22 17:37:51.331 OSD Theme Dimensions W: 640 H: 480
2009-02-22 17:37:52.234 TV: Changing from None to WatchingPreRecorded
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 720 x 576
2009-02-22 17:37:52.240 Realtime priority would require SUID as root.
2009-02-22 17:37:54.560 NVP: Timed out waiting for free video buffers.
2009-02-22 17:37:55.243 Video timing method: USleep with busy wait

```

the hard disk temperature is less than 40 degrees Celsius which is completely acceptable, isn't it:

```
jakob@teevee:/var/log$ sudo hddtemp /dev/sda
/dev/sda: ST9160310AS: 39°C
jakob@teevee:/var/log$ sudo hddtemp /dev/sda
/dev/sda: ST9160310AS: 39°C
jakob@teevee:/var/log$ sudo hddtemp /dev/sda
[sudo] password for jakob: 
/dev/sda: ST9160310AS: 38°C
jakob@teevee:/var/log$ sudo hddtemp /dev/sda
/dev/sda: ST9160310AS: 38°C

```

keep the suggestions coming, please!
Jakob.

---

### Post by jfix on 2009-02-22
well, now after half an hour of watching live tv the screen became white, not black.

progress, of some sort?!

---

### Post by jfix on 2009-02-27
Ok, here's an update:

I connected the eee box with a computer display (20" Dell LCD) and it worked perfectly without any problems.

The only difference I can see, is how the computer is connected to both displays:
[LIST]
[*]eee box -> TV: **eee box video output:** HDMI, **TV input:** DVI
[*]eee box -> monitor: **HDMI on both sides**
[/LIST]

Could this be a cable problem?  The TV set doesn't have an HDMI input, only DVI and VGA.  

The TV doesn't have the "blank screen" problem with any other input (wii, ps2) through scart/peritel and composite.  Also, previously I connected an old mythtv box using the exact same HDMI->DVI cable without a problem (a part from the fact that there was a big beige noisy box next to the TV).

Any suggestion on what to do?

Thanks,
Jakob.

---

### Post by gmspence on 2009-05-20
any update to this problem as I am experiencing the exact same thing on Jaunty

---

### Post by dStrom on 2009-05-20
I'm also seeing the same issue on Jaunty using DVI connected to a 19" lcd monitor.

---

### Post by gmspence on 2009-05-22
just played a movie full screen in vlc with no problems...is there away to change the default player in myth from mplayer to vlc? anyone tried that? will have a play about with it later.  would appear the black screen problem is limited to myth frontend only

---

### Post by dStrom on 2009-05-22
I just switched to a vga cable and I haven't had the blank screens since.

---

### Post by gmspence on 2009-05-23
I'm using the VGA cable with a DVI adapter?

---

### Post by gmspence on 2009-05-25
PROBLEM SOLVED!

followed this thread:

[http://ubuntuforums.org/showthread.php?t=880303&page=4](http://ubuntuforums.org/showthread.php?t=880303&page=4)

still using the DVI connection works flawlessly.

Now if only i could get mythvodka to work :)

---

### Post by motang on 2009-08-02
> **fudnet said:**
> Even changing the power saving options doesn't always turn this off. Try running this from a terminal:
```
xset -dpms
```
and
```
xset s off
```

--Tim
Cool, thanks I have similar problem but after you tip it worked great. :D

---

