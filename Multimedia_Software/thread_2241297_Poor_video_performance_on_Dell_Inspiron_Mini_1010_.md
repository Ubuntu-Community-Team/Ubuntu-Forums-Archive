---
title: "Poor video performance on Dell Inspiron Mini 1010 after installing Ubuntu 14.04"
date: 2014-08-25
forum: Multimedia Software
---

### Post by bpino on 2014-08-25
Hi all, I don't very much about Ubuntu and I'm having a hard time to view and listen to videos on my Dell Inspiron 1010 after installing Ubuntu. Could you tell me how to fix this problem? Thanks a lot in advance

I have already installed all Ubuntu restricted extras and checked suggested additional drivers in Software & Updates
This is what I get when I run the commands &#8220;sudo lshw -C video&#8221; and then &#8220;/usr/lib/nux/unity_support_test -p&#8221;, respectively.


 *-display               
       description: VGA compatible controller
       product: System Controller Hub (SCH Poulsbo) Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=gma500 latency=0
       resources: irq:16 memory:d8100000-d817ffff ioport:1800(size=8) memory:d0000000-d7ffffff memory:d8380000-d839ffff


---------------------------------------------------


OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.1.3


Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes
Unity 3D supported:       no

---

### Post by mikewhatever on 2014-08-25
You should not be running Ubuntu on a Dell Mini with Intel's GMA500, try Xubuntu or Lubuntu instead. It's not going to improve video performance by much, but at least the window manager will be snappier.
There is no fix. Intel has failed to support its own hardware with a decent driver, so we are stuck with a surrogate, that can barely manage to set the right resolution.

---

### Post by bpino on 2014-08-25
Thank you mikewhatever. It's a shame there is no solution for video performance in this case, since that's the only serious problem I've experienced so far on this Dell mini..

---

### Post by mikewhatever on 2014-08-26
...then consider yourself lucky. Mine have had all kinds of problems - freezing, sound, wireless, and of cause, Intel's graphics.

---

### Post by thopiekar on 2015-04-18
You can also give the EMGD driver a try which I provide in my PPA. It includes many patches needed to run on newer kernels. At the moment the kernel module is not tested on every version, but builds against kernel versions 3.0.x -> 4.0.x.
Today I made patches for 3.19.x which will be used for Ubuntu vivid and it works as I am currently writing this post with it.

When having problems see:
[http://ubuntuforums.org/showthread.php?t=2107593](http://ubuntuforums.org/showthread.php?t=2107593)
[https://github.com/EMGD-Community/intel-binaries-linux](https://github.com/EMGD-Community/intel-binaries-linux)

---

### Post by gordintoronto on 2015-04-18
I'm running the pre-release version (15.04) of Ubuntu Mate on a six-year-old Acer Aspire One, which has similar specs to your Dell. It plays videos just fine. In fact, everything I have tried has worked just fine. (Shared folder, shared printer, remote desktop, webcam, VLC, conky...)

If the video has a resolution larger than the screen of your Dell, the player has a lot more work to do to scale it down.

---

### Post by Yellow Pasque on 2015-04-20
> **mikewhatever said:**
> Intel has failed to support its own hardware with a decent driver

Intel supports its own hardware very well, but the Imagination Technologies "PowerVR" graphics licensed in earlier Atom chips are not supported well at all. I know most end-users don't care about that distinction, but I feel it's worth pointing out for the benefit of those making purchasing decisions. Intel now uses its own GPU's in the current Atom lineup.

---

### Post by Adam_GUI on 2015-12-15
> **thopiekar said:**
> You can also give the EMGD driver a try which I provide in my PPA. It includes many patches needed to run on newer kernels. At the moment the kernel module is not tested on every version, but builds against kernel versions 3.0.x -> 4.0.x.
Today I made patches for 3.19.x which will be used for Ubuntu vivid and it works as I am currently writing this post with it.

When having problems see:
[http://ubuntuforums.org/showthread.php?t=2107593](http://ubuntuforums.org/showthread.php?t=2107593)
[https://github.com/EMGD-Community/intel-binaries-linux](https://github.com/EMGD-Community/intel-binaries-linux)

I don't mean to necrobump, but, I just need a bit of clarification and I'm not sure where else to address it.
I'm back to trying EMGD on my dell mini 1010.

On your github page ([here]("https://github.com/EMGD-Community/intel-binaries-linux")) you've listed:
```
Create a xorg.conf on your own xorg.conf 
```
I want to believe that was typed in tiredness.  I know I've typed that kind of thing while tired.
And, As much as I want to fight making a "Yo, dog, I heard you like xorg.conf" joke...

It's been a while since I've had to fuss with xorg.conf in any distro.
Does this mean copying one of your generic examples into "/etc/X11/" as xorg.conf?

After modifying Xorg.conf, is it only a matter of running ```
apt-get install emgd-drm-dkms xserver-xorg-1.9-video-emgd
```?

---

### Post by Rob Sayer on 2015-12-18
Personally I would not use a 3rd party source for any sort of driver situation such as this.  Especially when it looks to be maintained by one guy ...

As mentioned, there is no good solution for this.  Intel outsourced the GMA on some Atoms to powerVR and they will not release the source code.

You definitely should not be using Unity.  Or cinnamon or gnome 3 or any other DE that needs 3D hardware acceleration just by itself.  You don't have 3D hardware accelerated video with that gpu so the CPU has to move all those pixels around.  Xubuntu or Lubuntu would be much better, esp. Lubuntu.  And in those, *turn off all display compositing*.

My 1Gb netbook has Atom 2600 with the GMA3600 video, also outsourced and with no 3D hardware accel, so my situation is similar.  It has MInt 17.2 (14.04 based) installed with the Mate desktop, but I installed the Lxde desktop comes with Lubuntu.  It's much faster but you still aren't going to get great HD video perfomance, period.

There are some things you can do though.  Don't use vlc or other heavy programs.  Kodi/xbmc would be out of the question.  Use mplayer, which is very fast, by itself or with a GUI like smplayer or gnome-mplayer.  In settings enable frame drop and multi threading and set the local file cache to a larger value (I use 8192Kb).

I guess I was lucky with this netbook because I knew what I was getting into, and I never intended to use it to watch videos much.  I can see where others may be ticked off ...

My recommendation would be to just back up your data and install Lubuntu.

---

