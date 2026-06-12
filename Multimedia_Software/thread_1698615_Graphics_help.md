---
title: "Graphics help"
date: 2011-03-02
forum: Multimedia Software
---

### Post by misselain on 2011-03-02
I am using a dell inperon 1440 laptop with a Intel Graphics Media Accelerator 4500MHD graphics processor. I am already aware that linux and intel don't really mesh well. I've been having gaming problems with being able to view moving images and words. I was hoping someone could suggest something that might be able to help the situation.

---

### Post by Joe of loath on 2011-03-02
What is your problem, exactly? I have the same GPU, and it works perfectly on Linux (Arch Linux here to be precise, but I've used Ubuntu 9.04-10.10 no issues). Admittedly it's too slow for gaming, but it works fine with compiz etc.

---

### Post by misselain on 2011-03-02
I have problems with two games to date. Sims 3 (which I play non stop) and INVU (Which my cousin plays when she visits). The problems appear to be very similar in both games. It's like the moving images don't really work, where there are any moving images it's just black and doesn't really function. Also there are no words in the Sims 3. 

I hope that is a little clearer.

---

### Post by Joe of loath on 2011-03-02
Sounds more like problems with WINE than problems with the graphics driver. Try the WINE subforum instead?

---

### Post by misselain on 2011-03-02
Yes that is where I was before and they said that they think there is something wrong with my graphics. I don't know that for a fact, I'd do just about anything to figure this out.

---

### Post by misselain on 2011-03-03
Is there really no one on this website that is willing to give me any kind of help? 

I just want help with my graphics without putting in a new processor. Please people anything. A taste if nothing more.

---

### Post by Joe of loath on 2011-03-03
It's probably a problem with how WINE interfaces with the driver.

Since you've probably got the newest version of both, there isn't much anyone can do. Intel graphics aren't made for gaming anyway, and the Linux drivers are rubbish, so be glad you got as far as you did on WINE ;)

Buying a new processor won't make any difference. You'd need to upgrade the graphics chip, which isn't possible on laptops.

---

### Post by johntaylor1887 on 2011-03-03
I suggest setting up a dual boot and using windows for games.

---

### Post by misselain on 2011-03-03
Reinstalling windows will be hell and according to the wine website Sims is supposed to run at a 'golden' level. I just would like to know if there is anything practical that could be done. Reinstalling windows is my last resort.  

Any suggestion will be accepted, no matter how outlandish. And thank you so very much to those who have taken the time to respond to my thread. It really means a lot. :)

---

### Post by BicyclerBoy on 2011-03-03
By default Ubuntu does **not** use the proprietary intel driver.
The free open driver does not have 3d or video decode acceleration.
You can try to activate the intel driver..

Your graphics are the same as G45 chipset & is quite capable.
VA-API could help leverage some video decode performance, don't think H264 decode is working.

You can post the output of this cmd (terminal)
lsmod
look for intel i915

You will likely need to create a simple /etc/X11/xorg.conf file like this..
  
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "AccelMethod"   "UXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Module"
        Load "glx"
        Load "dri"
EndSection

After rebooting post the file
/var/log/Xorg.0.log

---

### Post by Yellow Pasque on 2011-03-03
Post output of:
```
sudo apt-get install mesa-utils
LIBGL_VERBOSE=yes glxinfo
```

---

### Post by Yellow Pasque on 2011-03-03
> **BicyclerBoy said:**
> By default Ubuntu does **not** use the proprietary intel driver.
The free open driver does not have 3d or video decode acceleration.
You can try to activate the intel driver..
What? There is no proprietary intel driver for this chipset..

---

### Post by BicyclerBoy on 2011-03-03
I freely admit the intel drivers situation is confusing (for me)..

I thought the i915 driver supported the G45, albeit limited ?

The "intel" entry in the xorg.conf results in the i915 driver being loaded by xorg on a 945GME & the i915 can support (limited) the X4500MHD (G45).

Is this i915 driver just the free driver or the closed intel one ?

Thanks.

---

### Post by Joe of loath on 2011-03-04
i915 is just the generic intel driver. there's nothing else, so you have to use it :p believe it is open source, though.

---

### Post by BicyclerBoy on 2011-03-04
I think you are right about open source..but the Intel is involved 
[http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html)

[http://lists.freedesktop.org/mailman/listinfo/intel-gfx](http://lists.freedesktop.org/mailman/listinfo/intel-gfx)
> >[I] > GM45 (4500MHD) is well supported, and you should be able to use it
[/I]>[I] > to watch HD movies (if the cpu is not too bad). If you have
[/I]>[I] > problems, feel free to file bugs.
[/I]>[I] > 
[/I]>[I] > Just H.264 hw decoding not supported yet. (it’s already supported on
[/I]>[I] > newer hw, but with lower priority to port to G45/GM45.) 
[/I]

The i965  driver is better choice for G45 4500MHD chipsets.
Both the i915 & i965 come from the above project..

Does Ubuntu use these drivers by default ??

---

