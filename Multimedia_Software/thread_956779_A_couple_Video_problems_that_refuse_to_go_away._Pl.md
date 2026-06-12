---
title: "A couple Video problems that refuse to go away. Please, if you have any ideas..."
date: 2008-10-23
forum: Multimedia Software
---

### Post by Phases on 2008-10-23
Hey guys. 
I'm worn out. I'm hoping someone out there can help me get this straight before I rip my hair out. I've tried to be short, but this got long - I'm just trying to include all nessessary info for whoever has the time and willingness to look into this. I've been trying to fix this since 10:30pm last night, nonstop.  I've tried everything I can find.  I have two specific problems.

First, what I'm working with:

I have 2 [evga 6800GS 256mb]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130265") cards hooked into my system. I hooked them up SLI, with connector peice and "ez plug" plugged in. 

I have two [22" Asus monitors]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824236028") both hooked up DVI. Obviously one into each card.

I have 8.04 Desktop installed. 

I had trouble getting this going when I started last night so I posted, but then found [tremendous help]("http://ubuntuforums.org/showthread.php?t=884161") here. I learned I can't actually use SLI for what I wanted to do, but not to worry, there are other ways. I followed the steps the OP listed on page 2, and got both monitors going and eventually got both monitors going. At max resolution, acting just how I want. I got compiz to work right as well. (OS nvidia driver was needed, had to enable xinerama, and install xserver-xgl. Then play around and tweak a few things for compiz to act right)

*My first problem:*
For the life of me I can't get the video to quit being choppy. Framerate? Refresh rate? "Drawing?" I'm not sure what it is but, see the attachments. I get that when I move windows around or watch videos.  Also get that bright horizontal line over tops and bottoms of windows. 

I have tried everything under the sun it seems to fix it. I should mention, it does it with Compiz and Metacity both, with Emerald or GTK. It was doing this from the very start for the couple hours I only had one monitor going. (Although, both cards were in and running)

Here is my current xorg.conf. It has changed ALOT. Ive tried several options for the device section, several different things in monitor section (defining refresh rate, etc). The Modules you see in there.. it does the same thing with or without those. The DRI section...

```
Section "ServerLayout"
	Identifier "Multihead"
	Screen "Default Screen 2"
	Screen "Default Screen 1" RightOf "Default Screen 2"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
	Option "DefaultServerLayout" "Multihead"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor 1"
	HorizSync	31.3 - 80.2
	VertRefresh	56 - 75
EndSection

Section "Monitor"
        Identifier      "Configured Monitor 2"
        HorizSync       31.3 - 80.2
        VertRefresh     56 - 75
EndSection

Section "Device"
        Identifier      "Configured Video Device 1"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
	BusID 		"PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "Configured Video Device 2"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
	BusID		"PCI:2:0:0"
EndSection

Section "Screen"
        Identifier      "Default Screen 1"
        Monitor         "Configured Monitor 1"
        Device          "Configured Video Device 1"
        Option          "AddARGBGLXVisuals"     "True"
        Defaultdepth    24
	SubSection "Display"
		Depth 24
		Modes		"1680X1050"
	EndSubSection
EndSection

Section "Module"
	Load            "dbe"
	Load            "extmod"
	Load            "type1"
	Load            "freetype"
	Load            "glx"
	Load 		"dri"
	Load		"drm"
	Load		"bitmap"
EndSection

Section "Screen"
        Identifier      "Default Screen 2"
        Monitor         "Configured Monitor 2"
        Device          "Configured Video Device 2"
        Option          "AddARGBGLXVisuals"     "True"
        Defaultdepth    24
        SubSection "Display"
        	Depth 24
		Modes           "1680X1050"
	EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Section "DRI"
 Group		"video"
 Mode		0666
EndSection
```

I just don't know what else to try, but there's no reason my cards shouldn't be able to push to these monitors. The specs match up. I've got a [decent processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103544").. I've broke my diplay a million times trying to figure it out..

(Should the cards still be connected with the SLI bridge/Ez Plug, since it's not technically using SLI?) 

Anyway..
*My second Problem:*

I can't play a DVD. Meet the Robinsons. [Edit: It's playing other DVDs I've tried, Illusionist, Pan's Lab, Shrek 2, and Matrix, and Finding Nemo. But not Meet the Robinsons. However sometimes when rewinding/fastfoward it hangs) I will attach a picture of what I get with every player but one. 

All players (VLC, MPlayer, Movie Player, Gnome MPlayer..) do what you see in that picture, sound is also jarbled. All except gxine. It will play it great some of the time but most of the time it plays the first 9 seconds, with no sound, and stops. 

I searched and searched and followed everything that looked good. I spent a while on Part 1 and 2 of _this awesome thread_ and feel like I've downloaded/installed everything Ubuntu has to offer. God knows how much stuff I've put on my comp in the last twelve hours that I'll probably never use. Ive changed outputs of players, even seen suggestions for audio output changes and tried those...

..If anyone has any ideas please feel post them. Sorry this got so long..

Many thanks in advance.

---

### Post by Phases on 2008-10-24
Just verified that it isn't due to the SLI stuff being connected still. The 6 monitor beast you've all read about is hooked up that wasy too.

Any ideas, please post em, I'm open to any thoughts. Thanks!

---

### Post by Phases on 2008-10-25
I refuse to beg. 

I'm not going to do it! 

......

Phases <--- begs for a suggestion.

---

### Post by eternalnewbee on 2008-10-25
trying to figure out a way to stop you from begging ( just kidding ) hold on.

---

### Post by eternalnewbee on 2008-10-25
OK, first attempt: Disable Visual Effects and see what happens...

---

### Post by Phases on 2008-10-25
Thanks for the reply! 

No change to the way it acts on each screen, and when I drag a window from one screen to the next it jarbles (if that's a word) to a buncha junk on the monitor it's going to.

---

### Post by eternalnewbee on 2008-10-25
Sorry, I don't have any experience with more than one monitor.
Do you have this problem when you are using only one monitor, too?

---

### Post by gandaran on 2008-10-25
have you tried changing the video drivers in mplayer or vlc preferences/video tab to xv or x11?

---

### Post by Phases on 2008-10-25
Thanks guys, appreciate the replies.

> **eternalnewbee said:**
> Sorry, I don't have any experience with more than one monitor.
Do you have this problem when you are using only one monitor, too?

When I first set this up, for the first few hours I only had one monitor running. Both were hooked up to video cards that were both powered on, but xorg.conf was only configured for one. I did have the problem on the one monitor.

> **gandaran said:**
> have you tried changing the video drivers in mplayer or vlc preferences/video tab to xv or x11?

Yeah, I've changed the output to all other options.

Ok, I've recently noticed.. it's playing other movies I've tried okay. Matrix, Pan's Lab, Shrek 2, Finding Nemo, and Illusionist. But not Meet the Robinsons?? Sup with that? Having a little trouble with fast forward and rewind.. lockups..  but it's playing! (So, mostly yay there!)

---

### Post by Phases on 2008-10-25
I've removed all the extras in my xorg.conf that I've messed with trying to fix. Now it looks like this. I haven't notice any difference using one over the other.

```
Section "ServerLayout"
	Identifier "Multihead"
	Screen "Default Screen 2"
	Screen "Default Screen 1" RightOf "Default Screen 2"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
EndSection

Section "ServerFlags"
	Option "Xinerama" "true"
	Option "DefaultServerLayout" "Multihead"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor 1"
	HorizSync	31 - 80
	VertRefresh	56 - 75
EndSection

Section "Monitor"
        Identifier      "Configured Monitor 2"
        HorizSync       31 - 82
        VertRefresh     56 - 75
EndSection

Section "Device"
        Identifier      "Configured Video Device 1"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
	BusID 		"PCI:1:0:0"
EndSection

Section "Device"
        Identifier      "Configured Video Device 2"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
	BusID		"PCI:2:0:0"
EndSection

Section "Screen"
        Identifier      "Default Screen 1"
        Monitor         "Configured Monitor 1"
        Device          "Configured Video Device 1"
        Option          "AddARGBGLXVisuals"     "True"
	Defaultdepth    24
	SubSection "Display"
		Depth 24
		Modes		"1680X1050"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Default Screen 2"
        Monitor         "Configured Monitor 2"
        Device          "Configured Video Device 2"
        Option          "AddARGBGLXVisuals"     "True"
        Defaultdepth    24
        SubSection "Display"
        	Depth 24
		Modes           "1680X1050"
	EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

---

### Post by gandaran on 2008-10-25
> But not Meet the Robinsons
do you have libdvdcss2 for drm protected/encrypted playback installed?

---

### Post by Phases on 2008-10-25
> **gandaran said:**
> do you have libdvdcss2 for drm protected/encrypted playback installed?

Thanks for the reply :)

yeah, sure do..

---

### Post by Phases on 2008-10-26
/begs for advice on my video driver.

---

