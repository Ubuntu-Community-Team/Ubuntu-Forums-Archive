---
title: "Video Playback Frame Tearing New Mythbuntu"
date: 2010-10-24
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2010-10-24
After [building my first HTPC]("http://ubuntuforums.org/showthread.php?t=1587584") and [installing Mythbuntu,]("http://ubuntuforums.org/showpost.php?p=9988441&postcount=18") I finally got to sit down and watch some exciting TV.  NLCS game 6.

But, alas, there was considerable frame tearing.  Switching over to the regular TV, no tearing there so it's Mythbuntu. :(

I believe I had adequate computing power and nvidia VDPAU for great rendering, so I'm at a loss. :confused:

So I ran a playback with "[FONT="Courier New"]mythfrontend -v playback,channel[/FONT]"

The results are [here]("https://docs.google.com/document/edit?id=1nIfSXTy2PecBv6bbQ37_gJ5Fce68f4o50u-rXW83sxI&hl=en"), they look ok to me but I'm a noo·b. 

I took screen shots of some Frontend settings, they are [here]("https://docs.google.com/document/edit?id=1pxNPZ3WxtqV7Bd0LZRong67-raDxQiWjOREzh0hMJwQ&hl=en").

The television is a Toshiba faux 1080p, *e.g.* it says 1080p everywhere but it only accepts up to 1080i and "upscacles" it to 1080p, details [here]("https://docs.google.com/fileview?id=0B2Z1PtrPT-grYzIzMmE4NWQtZmNhMC00MzFlLTk3MmYtZWY5MmZjZDI0Njg4&hl=en").

Perhaps someone with more knowledge of Mythbuntu could take a look and give me a clue as to what to do?

Thanks

---

### Post by keepitsimpleengr on 2010-10-27
I ***_may_*** have solved the problem.

I increased the maximum real time clock timing from the ubuntu stadard of 64 to 2048.  In 10.10 this is done by adding the following lines to /etc/rc.local

```
echo 2048 >/sys/class/rtc/rtc0/max_user_freq
echo 2048 >/proc/sys/dev/hpet/max-user-freq
```

The suggestion came from [MythTV:Frame display timing]("http://www.mythtv.org/wiki/Frame_display_timing") and [How to set the RTC max_user_freq in newer kernels]("http://www.ralree.com/2009/07/19/how-to-set-the-rtc-max_user_freq-in-newer-kernels/")

I also have added 
[FONT="Courier New"]"vdpauhqscaling"[/FONT]
to the filter options at "[FONT="Fixedsys"]Utilities/Setup&#8943;>Setup&#8943;>TV Settings&#8943;>Playback&#8943;>Playback Profiles&#8943;>Custom Filters[/FONT]" 
and using 
[FONT="Courier New"]"VDPAU High Quality"[/FONT] 
at "[FONT="Fixedsys"][FONT="System"]Utilities&#8943;>Setup&#8943;>TV Settings&#8943;>Playback&#8943;>Playback Profiles (3/8)[/FONT][/FONT]"

I am also adding [FONT="Courier New"]'Option "TripleBuffer" "true"'[/FONT] to the Device section of xorg.conf (following the 'Driver nvidia' line).

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"TVOutFormat"	"COMPONENT"
	Option	"TVStandard"	"HD1080i"
	Option	"DPI"	"100x100"
	Option	"NoLogo"	"1"
	Option	"ConnectedMonitor"	"TV"
        Option  "TripleBuffer"	"true"
EndSection

```

The suggestion came from [mythTV:VDPAU]("http://www.mythtv.org/wiki/VDPAU") and pertains to ["C" nvidia video adapter cards]("http://en.wikipedia.org/wiki/Nvidia_PureVideo#Nvidia_VDPAU_Feature_Sets").

The proof will be in the pudding,  Tonite is game one of [World Series]("http://en.wikipedia.org/wiki/2010_World_Series").

---

### Post by bcg30506 on 2010-10-27
Thanks for the details.  Please post your results after testing it.

---

### Post by keepitsimpleengr on 2010-10-28
> **bcg30506 said:**
> Thanks for the details.  Please post your results after testing it.

The Giants really embarrassed the Texas Rangers, 11-7.  It was a pretty exciting game to watch with some really excellent infield action.

Oh! you meant the frame tearing.  It was _much_ better, with only a few minor tears occasionally.  I would have most likely missed them if I had been watching so closely.  Incidently, I watched the game both as it recorded, then later as mythTV was recording two other shows.  I'll add a screen shot of htop later for this.

Rain possible for tomorrow's game. (I'm 50 miles east of San Francisco but born and raised Texan)

---

### Post by uncle hammy on 2010-10-28
[http://www.mythtv.org/wiki/VDPAU#Troubleshooting](http://www.mythtv.org/wiki/VDPAU#Troubleshooting)

Note the first section, about eliminating tearing...

```
sudo nvidia-xconfig --no-composite
```

I have heard claims it is no longer needed with newer nvidia drivers, but have never found that to be supported by fact (at least with my cards).  Adding that line to my machines always completely eliminates tearing.  I am somewhat OCD, and I notice anything that's out of place....it's gone with composite disabled.

Oh, and "Enable OpenGL for VSync" in SETTINGS>TV SETTING>PLAYBACK works wonders too.

---

### Post by keepitsimpleengr on 2010-10-28
> **keepitsimpleengr said:**
> &#8943; I'll add a screen shot of htop later for this.&#8943;

htop screenshot shows two recording while watching recording,

Using an external probe, I measured 110°F near nvidia adapter output, it's 77°F normally.  Hardware [here]("http://ubuntuforums.org/showthread.php?t=1587584").

---

### Post by keepitsimpleengr on 2010-10-28
> **uncle hammy said:**
> [http://www.mythtv.org/wiki/VDPAU#Troubleshooting](http://www.mythtv.org/wiki/VDPAU#Troubleshooting)

Note the first section, about eliminating tearing...

```
sudo nvidia-xconfig --no-composite
```

I have heard claims it is no longer needed with newer nvidia drivers, but have never found that to be supported by fact (at least with my cards).  Adding that line to my machines always completely eliminates tearing.  I am somewhat OCD, and I notice anything that's out of place....it's gone with composite disabled.

Oh, and "Enable OpenGL for VSync" in SETTINGS>TV SETTING>PLAYBACK works wonders too.

I'll check this out, thanks!

---

### Post by keepitsimpleengr on 2010-10-28
> **keepitsimpleengr said:**
> I'll check this out, thanks!

O.K.

GOOD NEWS

BUT  when I ran nvidia-settings, it completely changed [FONT="Courier New"]xorg.conf[/FONT] &#8943; which is too much risk for me. However, the totally revamped [FONT="Courier New"]xorg.conf[/FONT] included this section.

```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
``` So I added it to my [FONT="Courier New"]xorg.conf[/FONT] and it made a difference.

I watched the recording briefly of MLB World Series Game 1, and no sign of frame tear.

BTW OpenGL for VSync was already enabled.

Here is my xorg.conf now&#8230;
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "TVOutFormat"   "COMPONENT"
        Option  "TVStandard"    "HD1080i"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
        Option  "ConnectedMonitor"      "TV"
        Option  "TripleBuffer"  "true"
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

Thanks for the great tip, uncle hammy! :guitar:

---

### Post by rhpot1991 on 2010-10-28
What processor are you using?

---

### Post by keepitsimpleengr on 2010-10-29
> **rhpot1991 said:**
> What processor are you using?

Processor and hardware bill of materials [here]("http://ubuntuforums.org/showpost.php?p=9921839&postcount=1").

Processor performance [here]("http://ubuntuforums.org/showpost.php?p=10039776&postcount=6").

[CENTER]:popcorn:[/CENTER]

---

### Post by SnafuFlux on 2010-12-08
> **uncle hammy said:**
> [http://www.mythtv.org/wiki/VDPAU#Troubleshooting](http://www.mythtv.org/wiki/VDPAU#Troubleshooting)

Note the first section, about eliminating tearing...

```
sudo nvidia-xconfig --no-composite
```

Uncle Hammy, I've tried using the no composite option, and it causes my system to react quite odd.  Tearing is completely gone, but it seems now all video is replicated to all other workspaces.  But it's not 100% the same video, it's as if I'm watching the video through a screendoor.  I can make out all the images, but it's dotted. 

Anyway, it also does this in the guide.  some times it'll even result in the backend crashing.  This happens while watching anything with the internal player.

system info: Asus M3N78-VM with onboard 8200 gpu.  

I appreciate any help you could provide.

---

### Post by uncle hammy on 2010-12-08
Sorry dude, I am far from an expert.  I just reported what I had read on the Wiki, and what had worked for me.

I can tell you this, on my Mythbuntu installations, one of the first things I do is knock that available workspaces down to 1.  I don't see any need for multiple workspaces on a HTPC.

I have also experienced (visually, anyways) what you describe.  However, it is only with the Nvidia 260.x drivers, and it is only when I forcibly terminate a frontend while it is playing video (usually because it has locked up).  Remnants of the video that was being played are left behind on everything (desktop, menus, etc).  Only a reboot clears it up.

---

### Post by SnafuFlux on 2010-12-09
Yah ok as long as I'm not the only one who sees this.  I see it with my 195.x drivers.  I tried upgrading to .24 repo and it did the same thing.  I went back down to .23 and didn't have any issue until I did that config.  

Anyone else experience this and found a fix for it?

---

