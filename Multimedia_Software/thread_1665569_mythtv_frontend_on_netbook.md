---
title: "mythtv frontend on netbook"
date: 2011-01-12
forum: Multimedia Software
---

### Post by pl@yer on 2011-01-12
I have a working backend/frontend and a second separate frontend, all running 0.23-fixes. I decided to install a third frontend on a netbook. 

I compiled mythtv and can connect to the backend but when I try to watch live TV the hdpvr lights up indicating it is capturing but the screen goes black and stays that way. I notice in the terminal that there are some errors related to interlacer and syncing. 

The weird thing is that when I mount the tv directory on the netbook fontend, using NFS, I can play the recorded shows using mplayer. 

If anyone has any ideas for me to try I would greatly appreciate it.
Thanks 
Steve

---

### Post by BicyclerBoy on 2011-01-12
What netbook hardware ?

HDPVR suggests MPEG-4/10 H264 stuff ?

You should try different frontend playback profiles.
Try CPU++ etc...
Edit the CPU+ profile & try different de-interlacing & rendering options.

Could be tricks to lighten the load..
Check out the possible playback profile filters..

Edit:

MythTV0.24 on atom intel 845   intel GPU driver profile CPU+/openGL rendering
SD H264AVC   playback watchable audio fine
HD720p           video okay audio glitchy
HD1080i          video 50% <frames audio bad  not watchable.

should add this is over wireless (not N)

---

### Post by pl@yer on 2011-01-13
Hi BicyclerBoy Thanks for replying. 

The hardware is a Toshiba model NB305. The capture resolution is 640x480 s-video. 

CPU info
```

britney@britney-TOSHIBA-NB305:~$ cat /proc/cpuinfo|egrep -i 'name|process'
processor	: 0
model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
processor	: 1
model name	: Intel(R) Atom(TM) CPU N455   @ 1.66GHz

```

video info
```

britney@britney-TOSHIBA-NB305:~$ lspci|grep -i graphi
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller

```



I'll try playing with the playback options and let you know.

---

### Post by BicyclerBoy on 2011-01-13
Ah. That's the new atom CPU with integrated GPU).

Should be/could be/might be a lot better than my atom 330.

I don't know if there are any drivers for this GPU that will make it work any better.

Sorry.

Edit 1:
Try running 
glxgears (in terminal fullscreen)

Edit 2:
The N10 integrated graphics is GMA3150
This is (for all intents & purposes) the same thing as the GMA900 & 950. This is the same graphics as in most of the old 270/330 netbooks.

If you feel confident & know how to undo this edit from console log on then --->
A simple improvement is to edit /etc/X11/xorg.conf
and change vesa to intel & restart.

If you need to create this file then paste this.
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by pl@yer on 2011-01-13
cant delete our own posts? 
BTW glxgears gets around 60fps full screen.

---

### Post by pl@yer on 2011-01-13
I really don't think it is a resource issue. I can play the recorded files with mplayer when I mount the backend's storage dir at the netbook. 

I ran into compile problems because of qt4.7 and null qstring values. I modified some files in order to get it to compile...starting to think it might be bad compile, just noticed that there is stuff missing in the playback settings screen (no edit). 

I guess I will upgrade the backend and the other frontend to 0.24 which compiles fine on the netbook. 

I'll probably do this tomorrow after work, too tired tonight!

Thanks again

---

### Post by BicyclerBoy on 2011-01-14
Use VLC to play and post the media infoformation

Or use ffmpeg -i recordingname.ts
mythffmpeg -i recordingname.ts

or mediainfo

The resolution is only part of the problem it is the compression (codec) that matters

Why do you bother to compile ? I find it's a real pain to make frontend & backend only packages & then debs..
There are very good 3rd part ppa for lucid maverick..

---

### Post by pl@yer on 2011-01-18
Sorry for not answering back earlier. I was waiting to have some kind of resolution or at least some more info to share.

The reason I compile mythtv 0-23-fixes is to get vdpau support, at least I think that was the reason I moved away from the prepackaged version available in squeeze and lenny (backend/frontend). I tried apt-get'ing mythtv-frontend on the netbook and got a message about the database schema being different from what the backend was using. 

I am using h264 with s-video input ( don't  have a high deff receiver...yet ). glxgears runs at around 64+ fps full screen. 

Over the last couple of days I did a "make uninstall" in the old 0-23 build dir and compiled 0.24-fixes so that the netbook and the backend would be the same version. I also blew away the database and installed fresh version from the new source. Some things are broke as far as hdpvr + h264 + vdpau in 0.24-fixes. Huge amount of tearing and stutter. Also same black screan when tring to watch tv on the netbook. 

Back to using 0.23-fixes on the squeeze backend. I should have mentioned before that I am using different distros and versions on my LAN. Maybe that was the reason for compiling? Anyway I am going to plug away a bit more at it, when I have some time.

---

### Post by BicyclerBoy on 2011-01-18
The MythTV ppa that I have always used have vdpau support.
The mythbuntu repos can be used, it has vdpau.

I compiled for a while to stick with Ubu10.04 & myth0.23+fixes but 0.24 has greatly improved DVD playback etc.

But you can not make use of it on the netbook so you could compile without.

Your post prompted me to install MythTV frontend on an atom netbook (ubu net mix 10.10) just to see if it would work...
My netbook (intel driver) works fine with SD H264 720x576..
Marginal H264 720p glitchy audio etc
Not usable with H264 1080i
Using wifi..(not N).

---

### Post by pl@yer on 2011-01-19
Thanks for confirming that it should work on the netbook. I will be trying again as soon as I have time.

---

