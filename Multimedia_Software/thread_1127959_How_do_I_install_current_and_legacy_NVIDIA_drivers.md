---
title: "How do I install current and legacy NVIDIA drivers at the same time?"
date: 2009-04-17
forum: Multimedia Software
---

### Post by andrewkk on 2009-04-17
How do I install both nvidia-glx-173 (legacy) and nvidia-glx-177 (current) at the same time?


I need both drivers because I have an NVIDIA GeForce 8400 GS and an NVIDIA GeForce FX 5200. With nvidia-glx-177 currently installed, the following message appears in /var/log/Xorg.0.log:
> The NVIDIA GeForce FX 5200 GPU installed in this system is supported through the NVIDIA 173.14.xx Legacy drivers. Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for more information. The 177.82 NVIDIA driver **will ignore this GPU**.

---

### Post by colinrmitchell on 2010-12-08
I have been searching for an answer to the same question.

I just bought a new computer with an nVidia GT 320 card installed in it.  This computer replaced a really old one I had with two older nVidia cards (MX4000, MX440) which drove two monitors.  This worked fine with 9.10.

When I installed Ubuntu on the new computer, I installed the current nVidia driver (260.xx I think?).  I also tried installing the 96.xx legacy driver by Synaptic, but I don't know if it took or not.  I got xorg.conf set up for dual monitors as I had in my last box, but it doesn't recognize the card:

```

[    12.279] (WW) NVIDIA(0): The NVIDIA GeForce4 MX 4000 GPU installed in this system is
[    12.279] (WW) NVIDIA(0):     supported through the NVIDIA 96.43.xx Legacy drivers.
[    12.279] (WW) NVIDIA(0):     Please visit http://www.nvidia.com/object/unix.html for
[    12.279] (WW) NVIDIA(0):     more information.  The 260.19.06 NVIDIA driver will ignore
[    12.279] (WW) NVIDIA(0):     this GPU.  Continuing probe...

```I would like to get the MX4000 card working to run my second monitor ( which is small, 1024x768 ).

Is it possible to have the two cards running concurrently with the different drivers?  Or must I purchase a newer card that is supported by the current driver?

Thanks for any insight!

---

### Post by |{urse on 2012-03-24
Resurrecting, I would like to know how to do this also. Using the current nvidia driver plus the legacy driver for an older nvidia add-on card to run second monitor. Is it possible to install both drivers?

---

### Post by BicyclerBoy on 2012-03-24
AFAIK..you can't with driver that would reuse/overwrite same kernel modules & overwrite the GLX components.
Maybe if it were possible to re-compile one of the drivers with different module name/install path etc..
nVidia probably have not allowed this & can't believe twinview would work.
The nVidia driver is part open source & part closed binary so the question is whether the open source part & install scripts could be modified to allow 2 drivers to co-exist.

I think you can use one nVidia driver & intel/other together as one X server.
USB based display adapters' drivers work in conjunction with existing X driver.

You can have multiple X servers running on one machine but I think each is in-active when not selected so not so useful.

Multi-GPU:
GL/GLX load is all controlled by primary GPU & can load share to same/similar card.

Important note with nVidia:
Dual (or more) monitors on one card means the GPU stays in max performance/clock mode.

---

### Post by |{urse on 2012-03-24
Well that clears things up a bit, yeah I could just *gasp* buy a newer gfx card, It's a shame but industry marches forward. Thanks for shedding some light on that. ;)

---

### Post by BicyclerBoy on 2012-03-26
Just remember I could be wrong, have not made a study of the issue.
I just see a lot of roadblocks..

---

### Post by Sc4rry69 on 2012-04-02
BUMP....

I have been trying to install the latest Nvidia drivers on my pc for a week now...I have the Nvidia Geforce GT 545 and everytime I try to install them I get a error saying "You appear to be running a Xserver"

I have searched and found a bunch of questions but no answers that work...I am running Ubuntu 10.10

The reason I'm trying to install these is because when I try to use effects it doesn't allow me because it says my video card isn't good enough which I know is wrong :/ If anyone can help me with how to remove the xserver I would be extremely grateful. Thanks in advance.

---

### Post by UltimateCat on 2012-04-03
NVIDIA & AMD are leading suppliers of discrete graphics processors, they do not make video cards. ( Least that is what I have found so far) ( 3months of research)  Instead they create video card reference designs which the various card manufacturers use to develop their own specific cards.

Because a manufacturer can customize or modify the designs of 2 cards that use the same graphics chipset it may differ in features and in actual performance.

Maybe even cause compatibility issue's-

Reference:
Upgrading and Reparing PC's  20th Edition
By: Scott Mueller

---

### Post by BicyclerBoy on 2012-04-03
The PC component manufacturers basically just clone the reference design from nVidia.

 @Sc4rry69
You have to stop the X server & run the nVidia installer from console login..

The nVidia driver readme details this process.

You would be better to use launchpad ppa x-swat or xorg-edgers..

---

### Post by |{urse on 2012-04-03
Just for future reference "If you try to use an onboard geforce > || == 6100 and an addon < || == 5500fx, it will work in windows (unified nvidia driver) but on Linux (both fedora and ubuntu so far) it will not due to geforce fx support being removed from the newer driver and packaged legacy thus requiring 2 separate drivers for the same thing."   

That's the word from NVIDIA, I just called them. I have a ton of old pci geforce fx 5500's that are now useless as linux dual-display cards, if anyone happens to run across a unified solution please leave it here.  ):P

---

### Post by Sc4rry69 on 2012-04-03
@bicyclerboy thanks for the reply, although I have already stopped the xserver and ran the installer (the .run file in root terminal) but still get that error. I just cant seem to find out how to completely uninstall xserver :/ 

I will do some research on that and see what I can come up with. I am still relatively new to Linux although I've had this installed on my pc for over 2 years but never really got into it that much...thanks again.

---

### Post by BicyclerBoy on 2012-04-04
sudo service gdm stop
sudo service lightdm stop

---

### Post by Sc4rry69 on 2012-04-04
This will uninstall the xserver?

Should I run this in the desktop terminal or tty mode?

ok just ran this and sudo service lightdm stop is a unrecognized service?

---

### Post by pootan on 2012-04-04
lightdm and gdm are both display managers so you probably only have one or the other. Also I think stopping the xserver is only a requirement to install a driver manually. There shouldn't be a problem with it running afterwards.

---

### Post by Sc4rry69 on 2012-04-04
I am trying to install the driver manually and everytime I run it it tells me that I need to uninstall the xserver before this one will install, and I cant figure out how to uninstall it.

---

