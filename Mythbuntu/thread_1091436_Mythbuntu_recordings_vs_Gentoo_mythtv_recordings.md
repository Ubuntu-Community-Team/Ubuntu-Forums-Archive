---
title: "Mythbuntu recordings vs Gentoo mythtv recordings"
date: 2009-03-09
forum: Mythbuntu
---

### Post by rmhurt on 2009-03-09
i have a 3.5 year-old mostly-working mythtv on a Gentoo box.  i bought a new hd and put Mythbuntu on it and was very pleased with everything compared to the hands-always-on work that Gentoo forced me into.  however, i'm afraid i'm going to have to stick with Gentoo due to my 4-year old CPU (Intel P4 Prescott i think).  

here's what is happening on both the old Gentoo box and my new spiffy Mythbuntu box.  i have 2 pcHDTV HD-3000 cards and when both are recording, mythbackend takes about 5-10% of the cpu.  when i play a recording using my nVidia GeForce FX 5200, mythfrontend takes about 50% of the cpu.  these numbers are about the same on both O/S's.  however, on my Gentoo box when i'm watching a recording the program/process "X" (x windows?) takes up 5-10% of the cpu.  on Mythbuntu, the program/process "Xorg" takes up 25-50% of the cpu.  so between mythfrontend and Xorg, the cpu gets maxed out and the playback stutters to a point that it's not watchable.

but, i also noticed that the 25-50% that Xorg takes is ONLY FOR NEW RECORDINGS.  RECORDINGS COPIED FROM GENTOO PLAY BACK JUST FINE in Mythbuntu and Xorg only takes 5-10% of the cpu - just like X does in Gentoo.

WHAT IS GOING ON??  why does Xorg have to work so hard when playing Mythbuntu recordings but hardly at all when playing Gentoo recordings??

i first thought the problem was my setup in mythfrontend and tried running it in a window, full-screen, etc, but because Gentoo's recordings play back just fine i now think the problem is with mythbackend.  i would dearly like to make the switch to Mythbuntu but unless i can make mythbackend record like Gentoo did, i'm going to have to stick with high-maintenance Gentoo (the needy bitch).  are there mythbackend compiler settings i should be using?  anything?  i really really hope someone can help...

---

### Post by newlinux on 2009-03-09
That is weird... The only thing I was gonna suggest was the playback profiles and making sure you have

Option "UseEvents" "on"  

in your nvidia device section of your xorg.conf, but that gentoo recordings working fine thing is strange. Are you talking analog or digital recordings with the HD-3000? There shouldn't be any differences in teh digital recordings, but analog recordings may be different. This would be controlled by your V4L recording profiles in mythfrontend.

---

### Post by utar on 2009-03-09
Perhaps Myth is de-interlacing the new recordings and not the old ones for some reason.  De-interlacing can be CPU intensive.  While playing back a new recording try selecting progressive from one of the myth pop up menus and seeing what happens to CPU usage.

---

### Post by rmhurt on 2009-03-09
> **newlinux said:**
> That is weird... The only thing I was gonna suggest was the playback profiles and making sure you have

Option "UseEvents" "on"  

in your nvidia device section of your xorg.conf, but that gentoo recordings working fine thing is strange. Are you talking analog or digital recordings with the HD-3000? There shouldn't be any differences in teh digital recordings, but analog recordings may be different. This would be controlled by your V4L recording profiles in mythfrontend.

i don't have it in front of me but i'm pretty sure i have 

Option "UseEvents" "1"

which is the same thing as "on" or "true", isn't it?  the recordings i was testing were all digital and HD.

---

### Post by rmhurt on 2009-03-09
> **utar said:**
> Perhaps Myth is de-interlacing the new recordings and not the old ones for some reason.  De-interlacing can be CPU intensive.  While playing back a new recording try selecting progressive from one of the myth pop up menus and seeing what happens to CPU usage.

i will try that this evening, but can you give me a hint on where these myth pop up menus are?  no bells are going off in my head.

---

### Post by rmhurt on 2009-03-09
oh yeah - thanks very much for the replies.  this is killing me and i'm going to be extremely disappointed if i have to abandon Mythbuntu.

---

### Post by newlinux on 2009-03-09
> **rmhurt said:**
> i don't have it in front of me but i'm pretty sure i have 

Option "UseEvents" "1"

which is the same thing as "on" or "true", isn't it?  the recordings i was testing were all digital and HD.

Yes it is... so much for that. What exact CPU are you using?

> **rmhurt said:**
> i will try that this evening, but can you give me a hint on where these myth pop up menus are?  no bells are going off in my head.

While playing back a recording, press the "m" key. It will be under the "Video Scan" menu, which I think is at the end.

utar has a good point - it could be that the programs you are trying from your gentoo box happen to be progressive and 1280x720 (720p) whereas the ones from your ubuntu box are interlaced and 1920x1080 (1080i). Different channels broadcast HD in different formats. 

If this is the case, your playback profile settings can make a big difference (especially your choice of deinterlacer).

---

### Post by newlinux on 2009-03-09
I'd also take a look at your respective xorg.conf and nvidia-settings settings from both systems. After that, for more clues look a the mythfrontend logs... Not too mention nvidia driver versions

---

### Post by rhpot1991 on 2009-03-09
I'd be willing to bet this is a 720p vs 1080i issue here, I'd rule that out first.

---

### Post by rmhurt on 2009-03-09
> **newlinux said:**
> [snip] What exact CPU are you using?


oh, man - i hope there's a place or command in Mythbuntu that will show the exact cpu since i don't remember.  it was a Fry's Electronics mb/cpu special nearly 4 years ago.  i can give you the motherboard; EliteGroup ECS PT800CE-A: "Socket 478 for Intel Pentium 4 processor".

> **newlinux said:**
> [snip] utar has a good point - it could be that the programs you are trying from your gentoo box happen to be progressive and 1280x720 (720p) whereas the ones from your ubuntu box are interlaced and 1920x1080 (1080i). Different channels broadcast HD in different formats.

i know the Gentoo recording i was testing was Two And A Half Men on CBS but i cannot recall whether the channel Mythbuntu was recording was also CBS. (dumb.) i will try that tonight, and also try it with ABC/NBC/FOX depending on what Gentoo recordings i still have, and post my findings.  is it true that FOX & ABC shoot in 720p while NBC & CBS use 1080i?

> **newlinux said:**
>  If this is the case, your playback profile settings can make a big difference (especially your choice of deinterlacer).

i'm using xvmc with the bob deinterlacer.  without xvmc, mythfrontend uses ~75-90% of the cpu which results in too much stutter.

> **newlinux said:**
> 
I'd also take a look at your respective xorg.conf and nvidia-settings settings from both systems. After that, for more clues look a the mythfrontend logs... Not too mention nvidia driver versions

i copied my Gentoo xorg.conf settings so they're nearly identical if not identical, but i know Mythbuntu has more recent versions of both nvidia-settings and the nvidia driver.  Mythbuntu is using the 173 driver while Gento is using an earlier version (i want to say 100).  i tried to make the nvidia-settings settings identical.

it doesn't seem like any setting within mythfrontend should effect Xorg, unlike xorg.conf, nvidia-settings and the nvidia driver itself.  do you agree?

---

### Post by newlinux on 2009-03-09
Yep, my understanding is that ABC and Fox are 720p, the other majors 1080i so that's not it either apparently. Especially since it seems you are using xvmc deinterlacer.

You can find out more about your proc by doing:
```

cat /proc/cpuinfo

```

I think as different things interact with X they can affect Xorg usage. But I'm no expert on that...

Next place to look after you confirm all this stuff (filters, xorg settings, use events, source recording resolution, interlacing) will be the logs and see if there are any playback errors or issues or differences between the two. 

Another thing to check is what happens when you play those gentoo and myth recordings using myth's internal player and compare that to mplayer... I'm just grasping at straws and trying to get more information - maybe something will stick out...

It still seems very weird to me - the recordings shouldn't be different - it's just digital capture of what's sent with no processing at all.

---

### Post by rmhurt on 2009-03-10
[QUOTE=rmhurt aka The Big Dummy]
i copied my Gentoo xorg.conf settings so they're nearly identical if not identical [snip]
[/QUOTE]

"nearly identical" was correct, it turns out. the new Mythbuntu xorg.conf and the old Gentoo xorg.conf were pretty similar with the glaring difference of the device option "XvMCUsesTextures" which was set to "0" instead of "1". that turned out to be my sole source of aggravation. the recording i was "testing" (don't hire me as a tester) was CBS which broadcasts in 1080i which is easier on Xorg, but i don't understand why it's easier. comment?

i believe the incorrect option is due to my reading of [this post]("http://ubuntuforums.org/archive/index.php/t-675836.html") and the first reply by "not4us".

note that the post uses "XvmcUsesTextures" with different capitalization than i have in my xorg.conf.  does that make a difference?  what exactly does XvMCUsesTextures do, anyway?  Google wasn't a big help.

i actually wrote yesterday that my OSD was in color and not in grayscale which has always been the tell-tale of xvmc not working. but like a big dummy i deleted the sentence because i didn't want to distract from what i thought was the problem.  i Googled for the mythtv OSD and it looked like a fix for the grayscale had been added since the version of mythtv i have running on Gentoo, so i discounted it.

from my 3 hours of testing last night of new and old recordings on ABC, CBS and NBC, Xorg stayed mostly in the 5-10% cpu area except for a few times usually at the very beginning of playback.  i did see a few lurches but they were few and pretty far between.

here is my current xorg.conf which seems to be working:

```

Section "Module"
    Load           "glx"
    [COLOR="Red"]# any other modules i should add?[/COLOR]
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"

    # added the following from Gentoo:
    VendorName     "Panasonic"
    ModelName      "52-inch LCD Projection"
    ModeLine       "ATSC-720-59.94p" 74.1 1280 1320 1376 1648 720 722
728 750
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "DPI" "100x100" [COLOR="Red"]# what's this?[/COLOR]
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1" [COLOR="Red"]# and this?[/COLOR]
    Option         "AddARGBGLXVisuals" "1" [COLOR="Red"]# and this?[/COLOR]
    Option         "NoLogo" "1"

    # added the following 3 lines from Gentoo:
    Option         "RenderAccel" "1"
    Option         "NVAGP" "1"
    Option         "XvMCUsesTextures" "1" [COLOR="Red"]# argh - was "0"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select" "1920x1080" "1280x720"
"1024x768" "720x480" "800x600" "640x480"
###     Modes      "ATSC-720-59.94p"  [COLOR="Red"]# from Gentoo; seems OK without[/COLOR]
    EndSubSection
EndSection

# added the following section
# per http://ubuntuforums.org/archive/index.php/t-675836.html :
Section "Extensions"
    Option         "Composite" "Disabled" [COLOR="Red"]# i don't think i need this[/COLOR]
EndSection

```

can you tell me if anything is questionable, or if i might add anything to improve performance? my Gentoo xorg.conf had many more sections, many relating to keyboard, fonts, mouse, etc, and none of this was in the Mythbuntu xorg.conf which kind of throws me.  like the opening Module section which is only loading glx; my Gentoo Module section loads a number of other modules but i didn't add them to Mythbuntu. i added the Extensions section at the end based on the post above, but seeing how much that post has helped me i think i should probably remove it.  i guess i need a good tutorial on the possible xorg.conf settings...

THANK YOU, THANK YOU, THANK YOU! :D

---

### Post by rmhurt on 2009-03-10
ps: here's some cpu info from my /proc/cpuinfo, since i've been mentioning cpu percentages in my ramblings:

```

processor       : 0 & 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz

```

---

### Post by newlinux on 2009-03-10
Most of us have been there, don't beat yourself up. As far as the differences in Xorg settings go, and why you had a lot more in gentoo than you seem to need in mythbuntu - I think this is due to a more mature drivers. Up until Ubuntu 8.04 I used to have a ton of things in my Xorg.conf, and now most of the needed settings are simply detected automatically or default to the write setting (UseEvents is one that doesn't). This is somewhat dependent on X properly detecting the EDID information from your monitor.

From my memory, I'm sure some of those settings aren't needed (heck, I don't even have resolutions in most of my xorg.confs anymore - only when I need a special modeline or EDID is somewhat off). I think some of your options (like the RGBGLXVisuals and Composite off) actually nullify each other (if composites are off, I don't think the other option will do anything). You can get more Xorg nvidia specific settings,in:

/usr/share/doc/nvidia-glx-new/README.txt.gz (unzip it first, of course). for more info on the options.

man xorg.conf tells that
> 
Config file keywords are case-insensitive, and "_" characters
are ignored. Most strings (including Option names) are also case-
insensitive, and insensitive to white space
and "_" characters.


The man page also has more generic options for xorg.conf


For me, 1080i recordings take more to decode than 720p. Maybe some options you had/have set were/are giving your 720p programs more problems decoding, or were only working with 1080i recordings.

---

### Post by newlinux on 2009-03-10
> **rmhurt said:**
> ps: here's some cpu info from my /proc/cpuinfo, since i've been mentioning cpu percentages in my ramblings:

```

processor       : 0 & 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz

```

I have a prescott P4 3.0 (hyperthreading) that plays back 720p and 1080i just fine without XvMC (CPU usually around 80%). Seems your proc shouldn't even *need* XvMC. It's running on a nvidia 7100 (which shouldn't make much of a difference since I'm not using any GPU acceleration) and the only options I have in Xorg.conf around the nvidia driver are just so I can run it dual headed (connected to a CRT and TV).

I also used to have good 720p and 1080i playback from my old P4 2.6Ghz (HT) and a Geforce 440MX. CPU would creep up to 90, but no XvMC, and pretty much no stuttering if I wasn't doing anything else with the box.

This is just for reference. If you have yours working, it's all good.

---

### Post by newlinux on 2009-03-10
one more thing - to get a color OSD back with XvMC, you need to use the chromakey OSD, not the softblend OSD in your playback profile. this will work for 5200 (doesn't work on 6 series and up).


EDIT:
[http://www.mythtv.org/wiki/XvMC#NVIDIA_2](http://www.mythtv.org/wiki/XvMC#NVIDIA_2)

Apparently, you have to have

Option "XvmcUsesTextures" "false"

for this tow ork

---

