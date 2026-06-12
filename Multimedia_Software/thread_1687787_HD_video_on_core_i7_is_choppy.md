---
title: "HD video on core i7 is choppy"
date: 2011-02-14
forum: Multimedia Software
---

### Post by jfd3220 on 2011-02-14
I've got a Lenovo T410 with just the onboard intel graphics, with the i7 620m and 10.04 64-bit installed.  I've also added the xorg-edgers ppa and installed all the packages from there.  When I try to watch a 720p video full-screen in youtube it is unwatchable, just too choppy.  I haven't been able to find an answer to this elsewhere.  
I've tried disabling the hardware acceleration in flash but that does nothing. 
It seems that the driver in use is i915.  Is that the driver that should be used? From lspci:

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Lenovo Device 215a
	Flags: bus master, fast devsel, latency 0, IRQ 34
	Memory at f2000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

---

### Post by cbanakis on 2011-02-14
How much RAM to you have assigned to your video card in BIOS?

Might not solve the issue, but couldn't hurt to max it out.

Beyond that, you could look into your flash plug-in.

Another thing you can try, is if you wait until the video is fully buffered, you can look in your tmp directory and play the flv file in mplayer.

I think you have to leave your browser open while you grab the file though, or it might clear itself.

The file name will be gibberish, but if you sort by date, and look for the newest, largest flv file...

---

### Post by gradinaruvasile on 2011-02-14
If i heard right, the i series chipsets are not yet fully supported by intels drivers in 2.6.32 series kernels. Maybe in the upcoming 2.6.37-38...

---

### Post by BicyclerBoy on 2011-02-14
AFAIK
The i915 driver is geared to the GM945 chipset etc i.e. the atom support chipsets.
GMA900,950 etc.

It does run on the i3,5,7 but is limited..
It has very restricted video formats that it will decode.

The i965_va driver could be the weapon of choice.

But that aside, your CPU is more than adequate to video decode, post-process & filter full bitrate HD1080 etc.
(An atom netbook GME945 can decode playback H264 576i)
Maybe the limitation will be copying the data into video memory.
So max out the video RAM (shared system RAM).

---

### Post by jfd3220 on 2011-02-14
Thanks for the reply. I don't think I can change the video settings in the BIOS.  I was able to view 720p vids in youtube flawlessly with the W7 that the machine came with.  I used to have dual boot but I recently dumped the W7 for Ubuntu.  When I was able to tether to my Nokia phone with bluetooth quite easily I knew it was time to switch for good :)  
I figured that the xorg-edgers ppa would somehow automagically set the right driver.  Is there some way to switch to the i965_va driver without an xorg.conf file?
By the way, I have some .mkv files that are supposedly 720p and they seem to play fairly smoothly with vlc.

---

### Post by cbanakis on 2011-02-14
Are you positive you cannot adjust the RAM in your BIOS?

I dont think Ive ever seen a BIOS that would not let you adjust it at all.

Sometimes its just hard to find the option, or it only lets you allocate a very small amount.

---

### Post by jfd3220 on 2011-02-14
There's definitely nowhere to adjust the RAM in the BIOS.  

I downloaded a 720p video clip from [here]("http://www.mediacollege.com/downloads/video/hd/") and it seemed to play smoothly in vlc.  I tried playing a 720p youtube video from the browser cache folder but the 720p ones always disappear when downloading is complete so I couldn't open any of them.  

Maybe the choppy video is a flash issue.

---

### Post by cbanakis on 2011-02-14
"Maybe the choppy video is a flash issue."

Thats what I'm thinking

Thats weird that the HD ones disappear right away though.

Maybe if you time it just right, you can snatch them outa there?

LOL

---

### Post by jfd3220 on 2011-02-14
I'm guessing it has to do with the large file size. I think they may get broken up into .dat files or something.

---

### Post by BicyclerBoy on 2011-02-15
AFAIK i3,5,7 GMA driver..

[http://packages.ubuntu.com/maverick/libs/i965-va-driver](http://packages.ubuntu.com/maverick/libs/i965-va-driver)

AFAIK you need driver listed in the xorg.conf file clues here..
[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

---

### Post by Grenage on 2011-02-15
I never have much luck with the default flash player, and install one from Adobe's website.  While I dislike flash, sometimes you just can't get around it.

---

### Post by jfd3220 on 2011-02-15
> **BicyclerBoy said:**
> AFAIK i3,5,7 GMA driver..

[http://packages.ubuntu.com/maverick/libs/i965-va-driver](http://packages.ubuntu.com/maverick/libs/i965-va-driver)

AFAIK you need driver listed in the xorg.conf file clues here..
[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

Unfortunately there doesn't seem to be a i965-va-driver package for 10.04.  I do have the following 2 files though:

/usr/lib32/dri/i965_dri.so
/usr/lib/dri/i965_dri.so

Don't know what good those do me.  And I actually have the Adobe flashplayer installed, v.10.2.152.27.

EDIT: Actually there appears to be a [PPA]("http://www.ubuntuupdates.org/ppa/lucidbleed?dist=lucid") with the package for 10.04 but it's experimental.

---

### Post by Yellow Pasque on 2011-02-15
You should try Flash aid: [http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)
Use this repo to get latest stable video driver: [https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)
If you're feeling adventurous, you can try the xorg-edgers repo: [https://launchpad.net/~xorg-edgers/+archive](https://launchpad.net/~xorg-edgers/+archive)

---

### Post by jfd3220 on 2011-02-15
> **Temüjin said:**
> You should try Flash aid: [http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)
Use this repo to get latest stable video driver: [https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)
If you're feeling adventurous, you can try the xorg-edgers repo: [https://launchpad.net/~xorg-edgers/+archive](https://launchpad.net/~xorg-edgers/+archive)

Hmm. I remember reading about flash-aid. Maybe I'll try it out.

I am already using the xorg-edgers repo and I have the latest version of xserver-xorg-video-intel 2:2.14.0+git20110214.23f9b14d-0ubuntu0sarvatt~lucid, which is supposed to have support for the i965 series chips.

---

### Post by Kirboosy on 2011-02-15
[Flash aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") works well for me. I can play youtube videos much better on my Atom processor now.


If you have video issues outside of firefox try using VLC. I know my processor is way less powerful than yours but I can play 1080p videos flawlessly in VLC. If I try and run it in Totem or any other media player it just dies.

Good Luck :)

---

### Post by jfd3220 on 2011-02-15
Flash-aid fixed it! Thanks!  I installed it from [here]("http://www.webgapps.org/addons/flash-aid").

---

### Post by ogilvierothchild on 2011-03-16
I got around this problem on my T410 by editing the file /etc/default/grub 

$ sudo gedit /etc/default/grub

and add the options in the GRUB_CMDLINE_LINUX parameter, so that it reads:

GRUB_CMDLINE_LINUX="enable_mtrr_cleanup mtrr_spare_reg_nr=1"

then running

$ sudo update-grub

and rebooting.

See also [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370552](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/370552)

---

