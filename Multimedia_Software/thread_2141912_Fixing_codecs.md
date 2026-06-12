---
title: "Fixing codecs"
date: 2013-05-04
forum: Multimedia Software
---

### Post by Messyhair42 on 2013-05-04
I find when I'm trying to play high quality .mkv files (720p and up) in VLC I often get problems, the video will hang up, or part of it looks scrambled. My VC is a 512MB Nvidia card. I'm using version 1.0.6 and my Ubuntu version is 10.04.

---

### Post by andrew.46 on 2013-05-04
Have you tried using SMPlayer / MPlayer using vdpau as a video output?

---

### Post by papibe on 2013-05-04
> **andrew.46 said:**
> Have you tried using SMPlayer / MPlayer using vdpau as a video output?
+1


Hi Messyhair42.

Unless you are using an upgraded ppa, VLC does not support video acceleration on 10.04.

Could you post the results of these commands?
```
lspci -nnk | grep -iA3 vga

lsmod | grep nvidia

apt-cache policy libvdpau1
```
Regards.

---

### Post by andrew.46 on 2013-05-04
As a sidenote: Interestingly enough the next release of vlc will support vdpau...

---

### Post by papibe on 2013-05-04
> **andrew.46 said:**
> As a sidenote: Interestingly enough the next release of vlc will support vdpau...
VLC-licious :D

---

### Post by Messyhair42 on 2013-05-11
```
jason@jason-mobile:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] [10de:01d3] (rev a1)
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau
03:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
jason@jason-mobile:~$ 
jason@jason-mobile:~$ lsmod | grep nvidia
nvidia               9961216  38 
agpgart                31724  2 nvidia,intel_agp
jason@jason-mobile:~$ 
jason@jason-mobile:~$ apt-cache policy libvdpau1
libvdpau1:
  Installed: (none)
  Candidate: 0.3-2build1
  Version table:
     0.3-2build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages

```

I'm unsure what any of it means. however it may not matter in a bit, I'm hoping to have a new installation of the LTS very soon

---

### Post by shantiq on 2013-05-11
> [COLOR=#000000][INDENT]As a sidenote: Interestingly enough the next release of vlc will support vdpau...[/INDENT]
[/COLOR]



wow    that is good news
still have to use SMplayer everytime 1080p is about   
mind you 720p been ok for a long time with VLC [in my experience]
any clue as to when this might be released?

---

### Post by andrew.46 on 2013-05-11
> **shantiq said:**
> any clue as to when this might be released?

The newest version of vlc has been cooking for over a year and I am not sure when it will finally come out. You could take a walk on the wild side and try it right now:

Howto: Compile the development version of vlc under the latest Ubuntu release
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

Best tried out in a Virtual Machine...

---

### Post by papibe on 2013-05-11
> **Messyhair42 said:**
> I'm unsure what any of it means. however it may not matter in a bit, I'm hoping to have a new installation of the LTS very soon
Let me see if this helps.

This is is to determine what video card do you have, and which driver is in used:
```
lspci -nnk | grep -iA3 vga
```
From this results:
```
01:00.0 VGA compatible controller [0300]: nVidia Corporation G72 [**[COLOR="#FF0000"]GeForce 7300 SE/7200 GS[/COLOR]**] [10de:01d3] (rev a1)
Kernel driver in use: **[COLOR="#FF0000"]nvidia[/COLOR]**
```
We can determine that you have an Nvidia GeForce 7300 SE (or 7200 GS), and you are using the nvidia proprietary driver.

This other one is just to double check that the driver is loaded and in use:
```
lsmod | grep nvidia
```
and there it is:
```
[COLOR="#FF0000"]**nvidia**[/COLOR]               9961216  38 
agpgart                31724  2 nvidia,intel_agp
```

This one checks if the video acceleration library is installed:
```
apt-cache policy libvdpau1
```
It is not:
```
libvdpau1:
  [COLOR="#FF0000"]**Installed: (none)**[/COLOR]
  Candidate: 0.3-2build1
  Version table:
     0.3-2build1 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages
```
Does that help a little bit to understand the commands?

Now regarding video acceleration. Your card does not support video acceleration. You would need a 8xxx series or above. So unfortunately, even if you upgrade to 12.04, you won't be able to reproduce HD video smoothly.

If your computer have a PCIe slot available, you can get a newer Nvidia card that supports acceleration for about $40. There are several models in that price range like 210, 420, 520, 620, etc.

Let us know how it goes.
Regards.

---

### Post by Messyhair42 on 2013-05-12
So unless I find reason not to, I'm considering this  VC [VC]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130815") as an upgrade (which is something I've wanted to do for a while). Will it solve my issues?

---

### Post by papibe on 2013-05-12
Yes. The 610 supports video acceleration (see it [here]("http://en.wikipedia.org/wiki/Nvidia_PureVideo")).

When you are on 12.04+, remember to:
[LIST]
[*]Install the Nvidia proprietary driver.
[*]Install the acceleration library: libvdpau1. That would provide acceleration for S/Mplayer.
[*]Additionally, if you want acceleration on VLC install these libraries: libva1 and vdpau-va-driver.
[/LIST]
Regards.

---

### Post by Messyhair42 on 2013-05-22
I installed the geforce 610, on booting I started in low graphics mode. I deactivated the nvidia proprietary driver, thinking i'd need a new one. the drivers on the CD for the card are all windows 7/8 drivers and I'm unable to get the nvidia proprietary driver active again. I did get libvdpau1 installed but the others libraries don't seem to appear, I'm still under 10.04 though, for now. how could I get the nvidia driver back if the GUI method isn't working?

---

### Post by papibe on 2013-05-22
Try this:

Close all your applications and go to text mode console by pressing Ctrl+Alt+F1

Login, and run this commands:
```
sudo service lightdm stop

sudo mv -v /etc/X11/xorg.conf  /etc/X11/xorg.conf.bakold

sudo apt-get purge nvidia-*

sudo apt-get install nvidia-current

sudo nvidia-xconfig
```
Finally restart your machine by running:
```
sudo reboot
```
If you are still experiencing low resolution, it may be the monitor's fault. Try using pure HDMI, or DVI cable instead of VGA.

In any case of trouble, please post the content of this file after a fresh reboot:
```
/var/log/Xorg.0.log
```
Please paste it here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and post back the link to it.

Let us know how it goes.
Regards.

---

### Post by monkeybrain2012 on 2013-05-23
> **shantiq said:**
> wow    that is good news
still have to use SMplayer everytime 1080p is about   
mind you 720p been ok for a long time with VLC [in my experience]
any clue as to when this might be released?

Why "still have to use"? You sound so reluctant :) I actually like Smplayer more than VLC. Use mplayer2 as backend it is really nice for vdpau.

---

### Post by Messyhair42 on 2013-05-24
```
/var/log/Xorg.0.log
```
command not found

I did get the driver installed again, it says it's active but not in use, and HD video is still choppy

---

### Post by deadflowr on 2013-05-24
> **Messyhair42 said:**
> ```
/var/log/Xorg.0.log
```
command not found

It's a text file, open it up with gedit, or other text editor to read it's contents.
It won't run any programs, no matter how many times you type it.:D

Also, did you run 
```
sudo nvidia-xconfig
```

---

