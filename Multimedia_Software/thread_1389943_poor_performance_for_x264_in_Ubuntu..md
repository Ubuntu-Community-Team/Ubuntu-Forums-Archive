---
title: "poor performance for x264 in Ubuntu."
date: 2010-01-25
forum: Multimedia Software
---

### Post by tbird79 on 2010-01-25
So for the last, oh, three or four hours now, I've been trying to get videos to play properly in Ubuntu. I have the default player, I have vlc, I (apparently) installed mplayer, but it won't play anything at all.

I was having horrible screen tearing with standard definition .avi's in vlc, fixed that by setting vsync in catalyst control center to always on or whatever it is.

Now, I have tried to run a 720p x264 video. It PLAYS, but not well. Audio is fine, however video is all jerky in VLC, and in Totem it's just a mess of screen tearing (although the video does no jerk on that player).

I have just spent HOURS trying to get VIDEOS TO PLAY. This makes no sense. Playing a video should be the simplest thing in the world for any OS to do, but with Ubuntu it is like pulling teeth. I have NEVER been so frustrated while using a computer. What is going on here?

BTW, I installed every single thing needed to use mplayer but it still does not work. The player comes up but will not play any type of file.

My system specs:

2.2Ghz dual core (intel)
3gb ram
1GB radeon hd 4650 vid card
asus ipibl-lb mobo

I was really enjoying Ubuntu until I got around to trying to watch some videos. Now I am maybe minutes away from going back to vista. At least on there I can watch full 1080p videos if I want with no problems.

Please help this stupid noob, as I am sick and tired of sending my data to msoft all day long! I really like this Ubuntu but this is INSANE!

---

### Post by VertexPusher on 2010-01-25
Have you installed the ATI display driver (fglrx)?

Have you disabled Compiz (i.e. desktop effects)?

Have you enabled XVideo hardware overlay? This is required for smooth video playback without tearing. When I had ATI graphics a while ago, XVideo had to be enabled manually in the driver by running "sudo aticonfig --ovt Xv" at least once. This may also be the reason why MPlayer does not work at all. See the driver's README file for details.

As far as I know (ATI users correct me please) there is currently no hardware acceleration for H.264 playback available with ATI cards on Linux. Right now it works only with Nvidia. Your CPU should be able to decode 720p H.264, but 1080p may continue to be a problem.

If you consider switching to Linux, you'll definitely want Nvidia graphics.

---

### Post by tbird79 on 2010-01-25
> **VertexPusher said:**
> Have you installed the ATI display driver (fglrx)?

Have you disabled Compiz (i.e. desktop effects)?

Have you enabled XVideo hardware overlay? This is required for smooth video playback without tearing. When I had ATI graphics a while ago, XVideo had to be enabled manually in the driver by running "sudo aticonfig --ovt Xv" at least once. This may also be the reason why MPlayer does not work at all. See the driver's README file for details.

As far as I know (ATI users correct me please) there is currently no hardware acceleration for H.264 playback available with ATI cards on Linux. Right now it works only with Nvidia. Your CPU should be able to decode 720p H.264, but 1080p may continue to be a problem.

If you consider switching to Linux, you'll definitely want Nvidia graphics.

I have installed the latest driver from ATI, and Compiz I also dealt with, although I did not remove it, I set the desktop effects to "none".

I will try out this XVideo hardware overlay. Fingers crossed!

---

### Post by tbird79 on 2010-01-25
well it tried that and got this:

No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.

So I went to xorg.conf and opened it with GEdit. Got this:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection


I am confused.

---

### Post by VertexPusher on 2010-01-25
Yes, run "sudo aticonfig --initial" first, then "sudo aticonfig --ovt Xv". Then reboot.

---

### Post by tbird79 on 2010-01-25
> **VertexPusher said:**
> Yes, run "sudo aticonfig --initial" first, then "sudo aticonfig --ovt Xv". Then reboot.

when I run "sudo aticonfig --initial" I get this:

Found fglrx primary device section
 Unable to find any supported Screen sections


When I then run "sudo ati-config --ovt Xv" I get this:

No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.

I know how to open xorg.conf in GEdit, but there are not many options there, not sure what to configure.

---

### Post by VertexPusher on 2010-01-25
aticonfig seems to be confused because the fglrx device section already exists. Delete xorg.conf (but keep a backup copy), then run the two commands again.

---

### Post by tbird79 on 2010-01-25
> **VertexPusher said:**
> aticonfig seems to be confused because the fglrx device section already exists. Delete xorg.conf (but keep a backup copy), then run the two commands again.

Ok, thanks, that seems to have fixed it! So far so good in VLC anyways. The tearing and 'jerkiness' seem to have cleared up (VLC had more jerkiness, totem had more tearing).

I'm definitely sticking with Ubuntu. I'm so sick of windows it's not even funny. I've only had Ubuntu installed for half a day, but I really like it so far. 

It's funny, I was totally fluent in BASIC back in the late 80's/early 90's when I was in grade school, and was very comfortable in DOS. Seems like I've almost forgotten how to type. Bloody Windows and it's mouse driven interface! LOL!!

Thanks again!

---

### Post by macaronii on 2010-10-30
Interesting. I'm having similar issues, but aticonfig doesn't recognize the Xv type:
> 
sudo aticonfig --ovt Xv
Error: invalid string value for --ovt option. 
Please check aticonfig help info for supported overlay type.
aticonfig: parsing the command-line failed.


---

### Post by SkylinesSuck on 2011-01-02
> **macaronii said:**
> Interesting. I'm having similar issues, but aticonfig doesn't recognize the Xv type:

Bump for this.  I did the above mentioned command when I still had the regular restricted drivers (10.4 catalyst) offered by lucid on initial start up, and I got all the outputs that were described saying Xv was working.  It still didn't fix the tearing though.  Now I'm using the 10.12 version of catalyst and I get the same error message as the guy in the post directly above this one.  Any ideas on how to tell if it's up and running and if not, how to turn it on?

---

### Post by SkylinesSuck on 2011-01-02
almost forgot, here is what my xorg.conf looks like 

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2732 768
        Depth     24
    EndSubSection
EndSection

---

### Post by BicyclerBoy on 2011-01-02
Just FYI.

x264 is an encoder library & cmd-line tool that can generate H264 AVC video stream.

It is not a decoder or a video format/container etc.
It had nothing to do with the OP problem..

---

