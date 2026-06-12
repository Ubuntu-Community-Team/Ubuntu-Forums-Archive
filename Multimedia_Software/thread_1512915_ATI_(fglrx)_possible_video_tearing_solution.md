---
title: "ATI (fglrx) possible video tearing solution"
date: 2010-06-18
forum: Multimedia Software
---

### Post by urbanus on 2010-06-18
**Issue:**
fglrx video tearing, need I say more?

**My relevant specs (UPDATED):**
GPU: ATI Radeon HD 3850 AGP
Flatscreen TV (connected via DVI to HDMI)
Resolution: 1280x720@50hz
Distro: Linux Mint 9 x86 (I know, I know)
fglrx: 10.6 (Catalyst Version)
X.Org: 1.7.6

**Settings:**
Compiz: off
fglrx: Vertical Refresh Always On ([like this]("http://ubuntuforums.org/attachment.php?attachmentid=160869&stc=1&d=1276895739"))
Video player: Gnome Mplayer (_Video Output: "gl"_)

**Result (UPDATED):**
My video playback seems flawless. The flickering is more or less gone with the 10.6 driver, the 2D preformance is also much better. I'm also actually able to play 720p h 264 video (note the cpu, Athlon 3000+) with a 70-80% cpu load. Some stuttering when maximizing and such, and once in a while regardless of what is playing, but smooth video otherwise.

I also did some testing with similar specs, but an ATI HD 4870x2. Using Mplayer and x11 video output and Compiz On if I remember correctly. Also had dual screens.Was also able to play games.

Hope this can help someone. If you uninstall Totem in Linux Mint, Gnome Mplayer will become the default video player. Its installed by default in Linux Mint, but is also in the repos for Ubuntu.

Can anybody confirm?

**Catalyst 10.6 Driver Installation:**
[I]Notice that this was done on Linux Mint, but this shouldn't matter for Ubuntu users.
I also had the fglrx driver already installed via the Restricted Driver utility.
I did this on another computer, but without a previous fglrx installed, and it didn't activate, aticonfig was missing++?!?![/I]

1. Download the Linux driver from [www.ati.com](www.ati.com)
2. Open terminal and "cd" into the Download folder.
> cd Download
3. Create the proper packages for Ubuntu 10.04 ("--listpkg" gives you the list)
> sudo sh ati-driver-installer-10-6-x86.x86_64.run --buildpkg Ubuntu/lucid

4. Install the deb's created (assuming no other deb packages are in the folder)
> sudo dpkg -i *.deb
5. Restart the computer.
6. You can check for Catalyst version in the Catalyst Control Panel to verify :-)

**PS!** 
I've been playing different videos, and so far so good. There isn't GPU acceleration, so the Athlon 3000+ doesn't cope entirely with 720p video, but the computer does in Windows with Mediaplayer Classic and ATI gpu accel, so one can only hope. Other than that, it works well if you don't need compiz and can ignore the screen flashing every now and then when starting mplayer.

**PPS!**
I've now tried some more combinations on my 3850 card, and it doesn't like when compiz is on, and x11 or xv.

---

### Post by DJYoshaBYD on 2010-06-18
i have always had issues with playing video and running compiz at the same time.. especially flash.. i mean, its ok at this point, but its never up to par, IMO..

---

### Post by urbanus on 2010-06-18
Flash is even an issue on Windows which is a prioritized platform. I haven't tested an Nvidia card with the new 10.1 release for Linux yet. Let's pray for some GPU Accel on the Linux platform and compatibility with Flash and video players.

I should add that the open source ATI driver works well for desktop use, but Open Arena made my ATI HD 4870x2 with 2 GPU's and 2 GIG Ram kneel and shut down. So not quite there yet???? :-P

---

### Post by SpEcIeS on 2010-07-02
Unfortunately this did not work for my Radeon 3450 HD and I have yet to find a solution for the tearing. The open source drivers seem to work fine, but there is a lack of performance. However, they do not tear video and OpenGL.

Some methods, aside from the ones posted on this thread, that I have implemented are: **aticonfig *[ --sync-video=on --vs=on and even --overlay-type=opengl ]*** none of which worked on any visual level. Also, on my machine it does not seem to matter if compiz is running or not; the tearing continues.

Due to the problems related to ATI video, my next box will not have AMD or ATI. Stick to what works and stay away from disappointment. ;)

[COLOR="DarkGreen"]**[http://www.phoronix.com/forums/forumdisplay.php?f=19]("http://www.phoronix.com/forums/forumdisplay.php?f=19")**[/COLOR]

---

### Post by urbanus on 2010-08-11
Let's hope the future brings better drivers!

I can add that the new 10.7 drivers works with my ATI HD 4870x2 without tearing when using mplayer and opengl output. I haven't changed any Ati settings, using default ones.

---

### Post by deepakdtg on 2010-09-07
I get no video tear with default drivers that ubuntu installs even with compiz enabled. But when fglrx driver is installed and compiz is enabled, there is a remarkable amount of tear apparent even when a window is minimized or restored.Disabling compiz seemed to have solved this problem, but disabling compiz is not an option for me.I have looked in many forums for a solution but none of them work. Is there a workaround for this problem?
I currently use a Sony VAIO E series laptop with ATI Radeon 5145 graphic card.

---

### Post by SpEcIeS on 2010-09-08
> **deepakdtg said:**
> I get no video tear with default drivers that ubuntu installs even with compiz enabled. But when fglrx driver is installed and compiz is enabled, there is a remarkable amount of tear apparent even when a window is minimized or restored.Disabling compiz seemed to have solved this problem, but disabling compiz is not an option for me.I have looked in many forums for a solution but none of them work. Is there a workaround for this problem?
I currently use a Sony VAIO E series laptop with ATI Radeon 5145 graphic card.

Unfortunately there is no current work around for this issue. I am currently using an Radeon 3450 HD card and there is no fix yet for the tearing while using the fglrx drivers, however you could use the open source radeon drivers which have absolutely no tearing. These drivers do not allow for great fps, but if you are more interesting ridding yourself of tearing then this is the way to go. Radeonhd open source drivers also tear from my readings on the net too.

I have had success in clearing the tearing in opengl games using fglrx, but not for video. You could even try MPlayer using opengl which eliminates tearing, but there tends to be transition problems going from fullscreen and back to window mode.

Also, for the Radeon 5000 series there are rumors that using the 2.6.35 kernel reduces tearing, or even eliminates it. The only real way to find this out is to give it a go.

Good luck :D

---

### Post by urbanus on 2010-09-08
I'm actually using the open source drivers myself now. I've added repositories for the latest kernel and open source radeon drivers. 

Some native linux games work fine (eduke32, warsow etc), but they should considering I have an HD 4870x2 card. Also the vented air is much hotter than usual. But apart from that it work fine, I'm also running dual screen with the right monitor as the primary one.

---

### Post by SpEcIeS on 2010-09-12
> **urbanus said:**
> I'm actually using the open source drivers myself now. I've added repositories for the latest kernel and open source radeon drivers. 

Some native linux games work fine (eduke32, warsow etc), but they should considering I have an HD 4870x2 card. Also the vented air is much hotter than usual. But apart from that it work fine, I'm also running dual screen with the right monitor as the primary one.

Out of curiosity, what frame rates are you getting on your games?

---

### Post by wildcard_seven on 2010-12-08
goddamn genius. 

I can finally do more of this
:popcorn:

And less of this
](*,)

---

### Post by jonyibandi on 2011-01-06
Hi Everybody!
How can it be possible that ATI programmers are incapable of writing a workable driver for the Ubuntu and ati users. I've many many problems with tearing, I tried everything, without any result. The open source driver is  really weak. But check this!
My friend asked me, to install on his acer notebook a new Ubuntu. I installed it, and tried the fglrx driver too. On his notebook, there are no tearing, no backfilling, everything well.
Glxgears makes 300fps per 5 seconds. HD films run perfectly.
How Can I check his settings? He use the 2.6.32.26 kernel and 8.771 fglrx. In catalyst the vertical refresh's also checked.

Any ideas?



Andrew

---

### Post by Shadow Player on 2011-01-06
Hi

[ATi doesn't exist any more actually.]("http://www.engadget.com/2010/08/30/amd-kills-ati-brand-you-can-look-forward-to-blood-stained-radeo/")

To check what graphics controller your friend has on his acer open a terminal and type:
```
lspci
```

Cheers, have a nice day

---

### Post by jonyibandi on 2011-01-06
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 3400 Series]

The lspci is an information code only? Is there any code, that gives detailed information about the driver. I have a HD2600 Mobility card, so I would like to compare these "detailed settings". 
And there is an interesting fact. If I enable the snow plugin, in the compiz-settings-manager, there is no tearing. :)

I think, we are to close to the solution, and we can not find it...

---

### Post by jonyibandi on 2011-01-09
Hi!

I tried to disable waiting for vertical refresh on my friend's notebook, and there were many tearing. After I Re-enable it, tearing goes away. 
What things the catalyst set, when I en/disable waiting f.v.refresh.
Is there a config file or what?

---

### Post by urbanus on 2011-01-14
Not sure about this one, but isn't there graphical utilities in the repository for hardware info as well?

---

### Post by urbanus on 2011-01-14
Not sure about this one, but isn't there graphical utilities in the repository for hardware info as well?

---

### Post by jonyibandi on 2011-01-14
I'm not interested in the hardware infos. I would like to know, what the catalyst set, when I turn the vsync on.

---

### Post by urbanus on 2011-01-30
Ahhh, good question! Im not sure, but if it edits the xorg.conf file, then there are guides with the different settings one can apply in there.

---

### Post by karthikvs88 on 2012-03-03
```
amdcccle
```

Under Display Options->Tear Free, select "Enable Tear Free Desktop to reduce tearing"

---

