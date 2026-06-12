---
title: "Graphics performance regression"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by koma77 on 2010-10-02
With Maverick RC I find that graphics performance is noticeably worse than in Lucid.

I have  a GT200 [GeForce GTX 260] graphics card that was very snappy in Lucid.
In Maveric it lags when for example scrolling in Firefox or moving a window. Or using the expo desktop effect.

Open GL performance seems not to be affected by this regression.

Anyone else that experience the same thing?

---

### Post by zika on 2010-10-02
> **koma77 said:**
> With Maverick RC I find that graphics performance is noticeably worse than in Lucid.

I have  a GT200 [GeForce GTX 260] graphics card that was very snappy in Lucid.
In Maveric it lags when for example scrolling in Firefox or moving a window. Or using the expo desktop effect.

Open GL performance seems not to be affected by this regression.

Anyone else that experience the same thing?A shot in the dark: Do You use some dark theme. Try Clearlooks and see if snappiness comes back... :)

---

### Post by dino99 on 2010-10-02
its time to look at logs (system admin logviewer) and xsession-errors (/home, ctrl+h to unhide it)

remove xorg.conf:
sudo rm -f /etc/X11/xorg.conf

add x-swat ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

update, upgrade then reboot

---

### Post by plun on 2010-10-02
It is a bug within Mavericks stable nVidia version....

> Fixed an interaction problem with a change in X server behavior that caused slow text rendering on X.Org xserver 1.9.

[http://www.nvnews.net/vbulletin/showthread.php?p=2318734](http://www.nvnews.net/vbulletin/showthread.php?p=2318734)



X-swat serves this version
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by koma77 on 2010-10-02
Thanks for the quick answers.

I take it the Maverick version of nVidia will evetually have the fix as well?

---

### Post by plun on 2010-10-02
> **koma77 said:**
> 
I take it the Maverick version of nVidia will evetually have the fix as well?

No, I don't think so.....

ver 260.19.06 is an unstable beta version, perhaps if nVidia releases this version early next week.

---

### Post by Quark718 on 2010-10-02
[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

---

### Post by plun on 2010-10-02
> **Quark718 said:**
> [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

No, I am not using the Nouveau c--p for my nVidia graphic card.

It runs better with the "real thing"....;)

---

### Post by ajgreeny on 2010-10-02
Looking at this from an ati users perspective, and with an old 9200SE video card running with the open source driver, I have found 10.10 to be enormously better than 10.04.

In lucid I needed a custom xorg.conf to get reasonable performance, and had to run at 16 bit colour for a decent refresh rate.  That is definitely not so in 10.10, which works great with the default install of the xserver, and with no xorg.conf.  In that respect I am very happy.  10.10 is far from perfect, but it's getting closer, as far as I can see, at the moment.

---

### Post by Jim_in_Omaha on 2010-10-02
> **koma77 said:**
> With Maverick RC I find that graphics performance is noticeably worse than in Lucid.

I have  a GT200 [GeForce GTX 260] graphics card that was very snappy in Lucid.
In Maveric it lags when for example scrolling in Firefox or moving a window. Or using the expo desktop effect.

Open GL performance seems not to be affected by this regression.

Anyone else that experience the same thing?

I installed the new BETA version and it did improve it dramatically but I still see large CPU usage in (for example) a terminal and scrolling through text. First time in a while I'm considering going back to ATI.

If you turn off the subpixel smoothing it does see to fix it but wow does it not look as good...

---

### Post by koma77 on 2010-10-03
Disabling nvidia-settings did not seem to solve the issue for me, at least.

I want to try that X ppa, but I am unsure on how to switch back to stock X once I've tested it?

---

### Post by koma77 on 2010-10-03
> **plun said:**
> No, I don't think so.....

ver 260.19.06 is an unstable beta version, perhaps if nVidia releases this version early next week.

Ah, well, what I meant was: will the updated nVidia driver get into Maverick during Mavericks lifetime, or do we have to wait for 11.04?

---

### Post by plun on 2010-10-03
> **koma77 said:**
> Ah, well, what I meant was: will the updated nVidia driver get into Maverick during Mavericks lifetime, or do we have to wait for 11.04?

Ok... this bug is relevant and has "High" as importance.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/629910](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/629910)

More about this from nVidias site: 
[http://www.nvnews.net/vbulletin/showthread.php?t=154563&page=4](http://www.nvnews.net/vbulletin/showthread.php?t=154563&page=4)


Only a developer knows if it will be upgraded.....

---

### Post by koma77 on 2010-10-03
Thanks for finding that bug!
It is clearly what I experience.

I've marked it as "Affects me"

---

### Post by Half-Left on 2010-10-03
Looks like we are stuck with it because Canonical are not going to delay the release over a proprietary driver bug, while the fixed driver is still in beta.

Very bad for us NVIDIA binary driver users. I'll stick with the Nouveau driver for now, with experimental 3D support.

---

### Post by Jim_in_Omaha on 2010-10-03
> **Half-Left said:**
> Looks like we are stuck with it because Canonical are not going to delay the release over a proprietary driver bug, while the fixed driver is still in beta.

Very bad for us NVIDIA binary driver users. I'll stick with the Nouveau driver for now, with experimental 3D support.

I could not get the Nouveau to work with the experimental 3D. And I would still like to play around with that because I like the idea.

The Nvidia Beta drivers have an uninstall. I did a 'sudo nvidia-uninstall' and it removed it (at least it looked like it did...)

---

### Post by exploder on 2010-10-03
My machine with an NVidea GT 220 card seems to work alright with the nvidea current driver. My machine with on-board nvidea graphics has problems with plymouth displaying properly. I can get plymouth to work but you can see the grid of the LCD when it displays, so it is using the Nouveau driver. I tried the experimental 3D package but it left the system unbootable...

The Nouveau driver seems to work much better other than the lack of 3D support. Mark Shuttleworth said in his blog that graphics were going to get attention in the next release.

Edit: Something I should mention, multimedia playback works perfectly with the Nouveau driver. Full screen flash for example is flawless.

---

### Post by efflandt on 2010-10-03
GT216 [GeForce GT 220] (rev a2) likewise works fine with the regular nvidia 256.53 on relatively new i5 650 3.2 GHz with all default video and appearance settings on 1080p display.

The only thing non-standard is real 64-bit flash 10.2 r161 instead of flashplugin-installer.  For some reason flashplayer.so from flashplugin-installer segfaults, crashing npviewer.bin in Firefox 3.6.10, which when I checked my logs was also happening in Lucid.  Although, it was not noticeable when viewing videos (maybe just flash ads).  No such issues with real 64-bit flash in 10.04 or 10.10.

---

### Post by exploder on 2010-10-03
efflandt, my GT 220 works fine. My 6150 on-board graphics on my other machine has issues with the NVidea drivers though, mainly with Plymouth.

---

### Post by cariboo on 2010-10-03
I'm running a GT218 (Geforce 210) using nvidia-current, I'm quite happy with the performance. 

Gtkperf - New Wave:

```
GtkPerf 0.40 - Starting testing: Sun Oct  3 14:54:14 2010

GtkEntry - time:  0.07
GtkComboBox - time:  1.56
GtkComboBoxEntry - time:  1.12
GtkSpinButton - time:  0.13
GtkProgressBar - time:  0.28
GtkToggleButton - time:  0.29
GtkCheckButton - time:  0.12
GtkRadioButton - time:  0.23
GtkTextView - Add text - time:  4.03
GtkTextView - Scroll - time:  4.60
GtkDrawingArea - Lines - time:  0.40
GtkDrawingArea - Circles - time:  0.31
GtkDrawingArea - Text - time: 13.05
GtkDrawingArea - Pixbufs - time:  0.59
 --- 
Total time: 26.79
```

Gtkperf - Ambiance

```
GtkPerf 0.40 - Starting testing: Sun Oct  3 14:56:35 2010

GtkEntry - time:  0.09
GtkComboBox - time:  0.95
GtkComboBoxEntry - time:  0.64
GtkSpinButton - time:  0.06
GtkProgressBar - time:  0.21
GtkToggleButton - time:  0.57
GtkCheckButton - time:  0.11
GtkRadioButton - time:  0.24
GtkTextView - Add text - time:  3.64
GtkTextView - Scroll - time:  4.75
GtkDrawingArea - Lines - time:  0.37
GtkDrawingArea - Circles - time:  0.31
GtkDrawingArea - Text - time: 12.97
GtkDrawingArea - Pixbufs - time:  0.62
 --- 
Total time: 25.55
```

---

### Post by exploder on 2010-10-03
No complaints here either. Both the proprietary and open source drivers have their own advantages and disadvantages but both my systems seem to run just fine. Things are at least moving in the right direction. :)

---

### Post by mc4man on 2010-10-03
even though the gtkperf tests read good it still seems overall there are some performance issue on the desktop, though certainly improved from a couple of wk.s ago (menu dropdowns, r. clicking on icons, files, folders, ect.
(nvidia, 8400m, ambience

> GtkPerf 0.40 - Starting testing: Sun Oct  3 18:50:42 2010

GtkEntry - time:  0.05
GtkComboBox - time:  1.35
GtkComboBoxEntry - time:  1.00
GtkSpinButton - time:  0.30
GtkProgressBar - time:  0.33
GtkToggleButton - time:  0.51
GtkCheckButton - time:  0.16
GtkRadioButton - time:  0.36
GtkTextView - Add text - time:  0.69
GtkTextView - Scroll - time:  0.49
GtkDrawingArea - Lines - time:  0.52
GtkDrawingArea - Circles - time:  0.55
GtkDrawingArea - Text - time:  0.33
GtkDrawingArea - Pixbufs - time:  0.08
 --- 
Total time:  6.72

I seem to remember a test suite from a site somewhere that had some more challenging tests, may try to search out

---

### Post by sdowney717 on 2010-10-03
[http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.04-driver.html)

I am using this one on MM and it's working fine.

---

### Post by plun on 2010-10-04
> **nvidia-graphics-drivers (260.19.06-0ubuntu1) maverick;** urgency=low

  * New upstream release:
    - Fixed an interaction problem with a change in X server
      behavior that caused slow text rendering on X.Org xserver
      1.9 (LP: #629910).
    - Enhanced VDPAU to support interop with CUDA and OpenGL
      when Xinerama is active.
    - Fixed a bug in VDPAU that prevented temporal-spatial
      de-interlacing from operating when temporal de-interlacing
      was not also enabled.
    - Added support for configuring the dithering depth used when
      driving a flat panel with a GeForce 8 family or Quadro
      4600/5600 or newer GPU. See the "Dithering Controls" in the
      Flat Panel page in nvidia-settings.
  * debian/headers, nvidia-current-dev.install{.in}:
   - Put the headers from 256.53 in debian/headers and install
     them in nvidia-current-dev as usual. Starting from the 260
     series, these headers are no longer distributed with the
     Nvidia installer. In Natty we'll package them separately
     but for now we'll keep them in nvidia-current-dev.
  * debian/dkms/patches/nvidia-2.6.36-ioctl.patch:
    - Refresh patch.

[https://lists.ubuntu.com/archives/maverick-changes/2010-October/008725.html](https://lists.ubuntu.com/archives/maverick-changes/2010-October/008725.html)

Buidling for the moment.....

---

### Post by webme on 2010-10-04
> **plun said:**
> Buidling for the moment.....

Nvidia 260 released!!!

---

### Post by ElSlunko on 2010-10-04
Using gtx260 w/ 260.19.06 on 64 bit 10.10.

Booting took a VERY long time for me and graphic performance was pretty bad on initial boot with the driver. However after putting it to sleep and waking up my performance issues were gone.

```
GtkPerf 0.40 - Starting testing: Mon Oct  4 11:00:13 2010

GtkEntry - time:  0.02
GtkComboBox - time:  0.63
GtkComboBoxEntry - time:  0.62
GtkSpinButton - time:  0.17
GtkProgressBar - time:  0.16
GtkToggleButton - time:  1.03
GtkCheckButton - time:  0.16
GtkRadioButton - time:  0.28
GtkTextView - Add text - time:  0.60
GtkTextView - Scroll - time:  0.29
GtkDrawingArea - Lines - time:  0.73
GtkDrawingArea - Circles - time:  0.93
GtkDrawingArea - Text - time:  0.64
GtkDrawingArea - Pixbufs - time:  0.16
 --- 
Total time:  6.41


```

---

### Post by cprofitt on 2010-10-04
I used the PPA drivers and am getting good results

---

### Post by cprofitt on 2010-10-04
Looks like the official repos have the new drivers now. NICE!

---

### Post by koma77 on 2010-10-04
The updated drivers in the repository fixed my regression! 
That's great!!

---

### Post by cariboo on 2010-10-04
I just updated to the latest nvidia-current and gtkperf time went from around 29 seconds to just over 6, on this system

---

### Post by ktp on 2010-10-04
> **plun said:**
> Buidling for the moment.....

sweet thanks...it's nice to see 260 in 10.10.

---

