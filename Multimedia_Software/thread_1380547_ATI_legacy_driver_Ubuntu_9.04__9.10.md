---
title: "ATI legacy driver Ubuntu 9.04 / 9.10"
date: 2010-01-13
forum: Multimedia Software
---

### Post by binrat on 2010-01-13
Hi, i hope i am in the right place for this question , i was wondering why Ubuntu as of 9.04 has no way of installing fglrx driver for ATI legacy cards seeing as so many cards have been moved over to legacy now.

---

### Post by Melcar on 2010-01-13
Because of the newer xserver and kernel.  The legacy driver isn't compatible with either of those.  They could offer a way to downgrade, but that I imagine would create more hassles that they would rather avoid.

---

### Post by HoMie_G on 2010-01-24
I upgraded my OS as well, but i need the old fglrx driver for my ATI vidro card. Should i just go back to 8.10? Or is there a simpler way to solve this?

thanks

---

### Post by efflandt on 2010-01-25
How old is your computer, and does it need something that the current **xorg-driver-fglrx** does not do (not installed by default, but is in Synaptic)?

I had one old computer that would not even start X in Xubuntu 9.10 after doing first updates (kept recycling back to login), or in Ubuntu 9.10 would lock up gnome unless using FailsafeGNOME.  But installing xorg-driver-fglrx before doing Xubuntu updates, or from failsafe gnome, resolved that.

---

### Post by Smokex on 2010-04-06
Help with the open source ATI legacy drivers on Ubuntu 9.10:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Follow that guide to the point where it links to "KMS with a Radeon card" then follow the link to here: 
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
and follow the instructions in the section KMS with a radeon card.

This worked perfectly for me on my ATI Radeon Xpress 200M.[B] :popcorn:
[/B]

---

### Post by danteuk on 2010-04-06
I also have a legacy card:
RADEON(0): Chipset: "ATI Radeon Mobility X300 (M22) 5460 (PCIE)" (ChipID = 0x5460)

In an old Dell laptop, the screen doesn't work so it's plugged into an external monitor. 

I'm using the default xorg drivers:
```
# head Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux thor 2.6.32-19-generic #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-19-generic root=UUID=ad64b4e1-4747-4b96-9a0c-15e03d1ea61c ro quiet splash
Build Date: 30 March 2010  08:17:06PM
xorg-server 2:1.7.6-2ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>) 
Current version of pixman: 0.16.4
```

```
Section "Device"
        Identifier  "My Graphics Card"
        Driver  "radeon"
        Option  "AGPMode" "4"
        Option  "DRI" "on" 
        Option  "DynamicPM" "on"        # Dynamic powersaving.
        Option  "ClockGating" "on"    # Assisting option for powersaving.
        Option  "AccelMethod" "EXA"   # EXA should fit most cases.
        Option  "EXAVSync" "on" # EXAVSync is explained above.
        Option  "DMAForXv" "on" # Forced option in order to enable Xv overlay.
        Option  "ScalerWidth" "2048"  # That should fix some very rare bugs.
        Option  "EnablePageFlip" "on" # It will not be enabled on R5xx cards.
        Option  "RenderAccel" "on"    # Optional. It should be enabled by default.
        Option  "AccelDFS" "on" #Optional. See the man page.
        BusID   "PCI:1:0:0"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

OpenGL for desktop effects doesn't work, it reverts to Xrender which is very slow.
Previously in 9.10 VLC would play videos okay(but slow) if I set it to use OpenGL ( otherwise I just got a black screen and sound, no video), but now in 10.4 VLC crashes when set to OpenGL ( other modes still don't work, ie blackness in place of video )
```
$ vlc SUNP0004.AVI 
VLC media player 1.0.5 Goldeneye
[0x884c148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
failed to create drawable
[????????] x11 video output error: X11 request 55.0 failed with error code 9:
 BadDrawable (invalid Pixmap or Window parameter)
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x4200007
  Serial number of failed request:  60
  Current serial number in output stream:  62
Segmentation fault (core dumped)
```

---

### Post by Mark Phelps on 2010-04-06
If by "10.4" you're meaning Ubuntu v10.04 -- that is still in beta testing.  If you're asking questions about that, you need to be posting in the proper beta testing forum, not here.

That forum is Development & Programming, Lucid Lynx Testing.

---

