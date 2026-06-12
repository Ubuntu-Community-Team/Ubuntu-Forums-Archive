---
title: "New ATI driver 9.1 fix anyones tearing?  4800 series"
date: 2009-01-31
forum: Multimedia Software
---

### Post by keypox on 2009-01-31
I have yet to find a solution to the tearing in videos.  With or without compiz enabled.  

I would love to fix this as this is pretty much the only thing holding ubuntu back.

---

### Post by keypox on 2009-01-31
hmmm it seems mplayer with compiz disabled, running opengl video mode.  Has very minimal tearing.  

I guess its good enough.  But still windows never has tearing...

---

### Post by mozychan on 2009-01-31
9.1 does fix the choppy video playback, but at a small price.  It doesn't align the videos correctly within the players window.  Everything is great if you play things in full screen.

Also note that regardless of the version of the ATI Catalyst driver, other video output drivers may work better for your hardware.  x11 works great on my Radion HD 3450.  Give it a try.

-moose

---

### Post by keypox on 2009-02-01
mine wasnt choppy video playback.  It is tearing, video refresing at a different rate than the video card.  And v sync not working.  

I think its hard to see and if you had such a big problem as choppy then you would be happy with tearing lol.

---

### Post by wolfdale on 2009-02-01
I had to use -vo gl in order to eliminate video tearing. I did a little bit of researching and I believe that the 9.1 drivers do not support video overlaying which may be the root to our problem. I'm using a 4850 ATI card on Intrepid (8.10).

---

### Post by zika on 2009-02-01
did You try:System->Preferences->MultiMedia_Systems_Selector->Video->X_Window_System(No Xv)?

---

### Post by DavidBeijer on 2009-02-01
> **zika said:**
> did You try:System->Preferences->MultiMedia_Systems_Selector->Video->X_Window_System(No Xv)?

I think I've messed around with every possible setting with the older drivers, and they all did not fix the problem. I was very happy to read about the new drivers, especially since it was mentioned in the release notes that the tearing problem should be fixed. 

I installed it today, but I still have tearing. I tried all of the solutions suggested above, but to no effect. Compiz on/off, XV or no XV, vertical sync on or off, it all doesn't have any effect. I have a radeon HD3650 BTW.

Another thing that strikes me as odd after installation, is that the Catalyst centre indicates the 2D drivers as being version 8.57.2 and OpenGL as version 2.1.8395. Is this normal or did something go wrong with installing the drivers? I thought I was supposed to have version 9.1 with OpenGL 3.0.

---

### Post by Nextract on 2009-02-01
I have the same issue, i just installed 8.10 I have a HD3450 and I cannot for the life of me get smooth video playback, i think it might be time to return to windows, since i spend most of time watching videos. 

Out of curiosity, what is the DirectX equivalent output module in Linux?

I tried VLC and MPlayer and both tear constantly and are choppy as hell that is with the new drivers and the drivers that came with Ubuntu 8.10 in the restricted drivers system.

Thanks.

---

### Post by DavidBeijer on 2009-02-01
I've been experimenting the last hour or so, I'd say the best results I got were using the following settings:
[LIST]
[*]Using the latest drivers by ATI, installed as instructed on [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)
[*]Setting Vsync to "always on" in the Catalyst control centre
[*]Using VLC as player, rendering to the XV output
[*]Added these lines to xorg.conf under Device settings:
Option	    "VideoOverlay" "on"
Option	    "OpenGLOverlay" "off" 	
Option	    "TexturedVideo" "on"
[/LIST]

As said, these settings still produce some tearing, but they seem to give the best results. If anyone has any ideas on how to improve my settings, I'd be happy to listen :)! Another thing I noticed is that some files seem to produce more tearing than others. I don't know if that is because of driver issues or because how they are filmed (more or less panning, steadier camera work, etc...).

---

### Post by zika on 2009-02-01
I have HD 3650 also and the adjustment I mentioned in #6 (with xorg.conf as plain as it gets) solved my flicker and other issues with video. if I try xv there is no flicker (new in 9.1) but in non-full-screen picture is shifted 1/2 window down. 

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier  "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier  "aticonfig-Screen[0]-0"
    Device      "aticonfig-Device[0]-0"
    Monitor     "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection
```

I've tinkered with all the options left and right, up and down and my conclusion is following: total default in Catalyst, total default in ccsm in "extra" (apart from specifying the right refreshment rate) (it's funny that "good" in ccsm:general->display_settings->texture_filter is faster than "fast", etc.), channeling video to X11, gives the best pictuire and most stable machine (ati hd 3650) for me. it's even faster than metacity in overall.

---

### Post by keypox on 2009-02-01
Yeah i too was very excited about the new drivers.  I will try some of the 'fixes' above but i have found that mplayer seems to work best with mode opengl (first one)

Need to disable compiz, best with compiz enabled is mplayer or vlc with x11.  

But the opengl works pretty nicely.  Compared using old saving private ryan and opening scene of bolt cartoon.

---

### Post by keypox on 2009-02-01
> **DavidBeijer said:**
> I've been experimenting the last hour or so, I'd say the best results I got were using the following settings:
[LIST]
[*]Using the latest drivers by ATI, installed as instructed on [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)


Whats the advantage of following those directions versus just downloading form ati and isntalling via there installer?

---

### Post by markbuntu on 2009-02-01
I just installed 9.1 on Intrepid and ran the installer and it worked just fine. Those directions at cchtml.com were originally written when the automatic installer did not support Ubuntu.

I also have a HD3650 and I have found that setting the CCC 3D options to Override application settings and putting all the sliders to the left generates the highest quality picture with no tearing or other problems with compiz running. The video  plays and looks good even while rotating the cylinders, full screen or windowed from either of my big-desktop displays, even from behind.

The problem with picture position in vlc was fixed by selecting X11 and accelerated video output.

I also now get no tearing with the totem plugin for firefox in windowed mode which I could never resolve before. That was really the last thing and now it is fixed, yay!!.

---

### Post by mozychan on 2009-02-01
> **markbuntu said:**
> I also now get no tearing with the totem plugin for firefox in windowed mode which I could never resolve before. That was really the last thing and now it is fixed, yay!!.

using mplayer plug-in with xv is pushing video up. gl is choppy.  while x11 remains to work perfectly for me.  no problems with tearing.

-moose

---

### Post by DavidBeijer on 2009-02-02
> **keypox said:**
> Whats the advantage of following those directions versus just downloading form ati and isntalling via there installer?

In my opinion these instructions are somewhat more helpful when something goes wrong. If the installer works flawlessly at once you can and should use that one, but in case something goes wrong the wiki provides more information on were to mess around in order to try and fix it. It also provides a way to check whether the new drivers are in place and working.

To me (being a total n00b with Ubuntu) they learned me more.

---

### Post by DavidBeijer on 2009-02-02
> **markbuntu said:**
> 
I also have a HD3650 and I have found that setting the CCC 3D options to Override application settings and putting all the sliders to the left generates the highest quality picture with no tearing or other problems with compiz running. The video  plays and looks good even while rotating the cylinders, full screen or windowed from either of my big-desktop displays, even from behind.


I also tried these settings for my HD3650 but I still have tearing, in both VLC player and (S)Mplayer. I tried the XV and X11 output mode in VLC, but it didn't make a difference. Are you sure that all sliders need to be positioned to the left? That would turn off vertical Sync right? 

I also tried these settings with Compiz turned off (I thought the V-sync settings of Compiz might interfere), this improved things slightly, but I still have tearing. The file I use to verify is a 24 episode. 

Any suggestions anyone?

---

### Post by markbuntu on 2009-02-02
left ,right, i get so confused sometimes. I meant right, sorry. But I did not notice any difference with the  wait for vertical refresh slider in any position. the other sliders were just for better picture quality which is quite noticable with dvds.

In compiz settings/utility I have Video Playback checked and set for YV12 colorspace. I also have all the Workarounds checked. You should look into those settings.

I also have set no options in xorg.conf, none, nada, zero.

A little side note here. I have never had any tearing with firefox/flash 10 either windowed or full screen.

---

### Post by DavidBeijer on 2009-02-03
Ah, that explains :). I tried these settings also, my Compiz settings were already the same way as yours. There is some improvement, but I STILL have tearing though. I still have to test removing all the extra lines in my xorg.conf, but I don't have time for that now, as I have a lecture to attend in a couple of minutes. I'll keep you posted on results though.

This starting to get really annoying, I am pretty satisfied with Ubuntu, except for this tearing. As I am somewhat of a movie fanatic, I'm almost considering making my pc a dual boot machine with windows, just to be able to watch video's the way they are supposed to be. 

I noticed in your forum avatar thing that you run Ubuntu 8.04. I run 8.10, could that make a difference in this case?

David

---

### Post by markbuntu on 2009-02-03
I am currently running Hardy 8.04 386 and Hardy amd64UbuntuStudio and Intrepid 8.10 amd64 and Mandriva One 2009 i586. I will also be running Jaunty as soon as I can make the time to figure a way around the currently buggy install.

Everything I wrote here was on 8.10. I have not yet tried the new driver on my Hardy installs.

I found that many of the options I used in previous drivers have been not working or messing things up so I just gave up on bothering with all that a few drivers ago. The defaults seem to be working just fine for me

---

### Post by zika on 2009-02-04
> **markbuntu said:**
> i found that many of the options i used in previous drivers have been not working or messing things up so i just gave up on bothering with all that a few drivers ago. The defaults seem to be working just fine for me
+1 (even though I love to tinker) ... ;)

---

### Post by DavidBeijer on 2009-02-08
Bummer, I removed all the extra lines from xorg.conf, the tearing has visibly reduced, but it is still there. 

A friend has lended me his old nVidia card. If that doesn't show the tearing I will probably replace my ATI with an nVidia. If the problem also persists with that one I will most probably create a dual boot setup with windows to watch video's, and wait for new ATI drivers to fix the issue.

---

### Post by sodapop_ on 2009-02-09
please post your results with nvidia, i recently bought an HD3650 and i get tearing everywhere i've been trying to solve it for 3 days now, tried all available drivers even the beta ones with no luck. Can't even watch a dvd.....

im not using composite
tried all the different settings with aticonfig --vs --sync-video etc.
tried a bunch of different flags with mplayer ([http://www.linuxquestions.org/questions/linux-software-2/mplayer-opengl-video-output-driver-too-slow-694320/]("http://www.linuxquestions.org/questions/linux-software-2/mplayer-opengl-video-output-driver-too-slow-694320/"))

---

### Post by sodapop_ on 2009-02-09
went back to the store today and replaced the ATI HD3650 with Geforce 6800.
Tearing is gone completely i even played an 720p mkv file with no problems
at all. 
good luck!

---

### Post by radox1912 on 2009-02-11
try this -

[LIST]
[*]install newest driver from ATI website (be sure to follow [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat91-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat91-inst.pdf) , especially the point 7 on page 6)
[*]install vlc player and set it to opengl output (alternatively u can use x11 -not tested)
[*]go to ati catalyst control center(previously installed
[*]go in 3D setting -> more settings -> and set Wait for vertical refresh to always on
[*]try vlc to play some video ->for me tearing is gone! completely
[/LIST]

not sure if it helps for 4800 series also, but you can try:)im using ati mobility x2300 btw

and let me now if it works.

---

### Post by fnmo on 2009-02-15
Hi Everyone!

I'm using (S)mplayer with "**gl (fast - ATI cards)**" in metacity and no tearing at all, i also use mplayer with compiz but with "x11" output mode and a little tearing in this case but nothing to annoying.

Hope (S)mplayer with "**gl (fast - ATI cards)**" in metacity works for you too.

Sorry for my English.

---

### Post by DavidBeijer on 2009-02-16
> **fnmo said:**
> Hi Everyone!

I'm using (S)mplayer with "**gl (fast - ATI cards)**" in metacity and no tearing at all, i also use mplayer with compiz but with "x11" output mode and a little tearing in this case but nothing to annoying.

Hope (S)mplayer with "**gl (fast - ATI cards)**" in metacity works for you too.

Sorry for my English.

Haha! This did it! Metacity with GL in SMPlayer is (for me) the only setting with no noticable tearing on the HD3650. I cannot thank you enough! Must have been a combination of settings that I overlooked :). Now we'll just have to wait until the drivers also support this under Compiz, and I can watch videos without having to switch anything off or on. (<==ghehe, can you tell I'm happy?)

Oh and BTW: your English is perfectly understandable, I wouldn't worry about it too much.

---

### Post by zika on 2009-02-16
sorry, ... deleted, not relevant.

---

### Post by bebox on 2009-02-22
> **fnmo said:**
> Hi Everyone!

I'm using (S)mplayer with "**gl (fast - ATI cards)**" in metacity and no tearing at all, i also use mplayer with compiz but with "x11" output mode and a little tearing in this case but nothing to annoying.

Hope (S)mplayer with "**gl (fast - ATI cards)**" in metacity works for you too.

Sorry for my English.

yeaaa...this also helped me...thanks alot!!!!

---

### Post by DavidBeijer on 2009-02-23
For anyone interested in this solution: it works, but I've discovered that my secondary monitor still suffers from tearing. I'm not exactly sure why that is, since my primary monitor has no problem at all. This is kind of unfortunate, as I use my secondary monitor output to connect my beamer. The obvious solution is to switch the cables when I want to use the beamer, but that is not a solution I prefer of course.

---

