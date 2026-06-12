---
title: "Nvidia GeForce fx 5200..... wont work!!"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by jrharvey on 2007-09-14
I have looked at other threads but none of them are using fiesty. When trying to install ubuntu with my nvidia card It froze up while booting up. I realized that if I switched to my onboard card then it worked fine. I installed ubuntu and and then downloaded the drivers that other threads said would work. After othrers claimed the process to work, mine came up with an error saying the X server cam't start and then went into a big black screen like the terminal. (((Excuse me b/c thats the only way I know how to describe it.)))) I found another thread that had the same problem and I tried to ask questions but nobody answered. Do I have to get a new card?

---

### Post by jrharvey on 2007-09-14
Ya know I was doing some reading and I think It may be because I am using fiesty. Oh well. I may be wrong and if I am then someone please correct me.

---

### Post by vpjr on 2007-09-14
hi,

may i help? i'm running edgy with compiz using NV34 [GeForce FX 5500] as my video card.  so far, i've had no problems.

please post this file:  

              xorg.conf 

can be located at:

              /etc/X11

regards,

ven

---

### Post by jrharvey on 2007-09-14
Yes I have heard that edgy runs this card ok but I havnt seen anything about fiesty. I knew I should have downloaded the supported version ;) Im not sure what you meant under your comment

---

### Post by vpjr on 2007-09-14
hi,

there's a file that sorts of configures the X windows to run on your hardware.  It's called_ xorg.conf_ and can be found at the directory: _/etc/X11_.  If you can, please post it on this thread, so I can study it.  Maybe I can find something to help you with.

best regards

---

### Post by Shlomir on 2007-09-14
I had a similar problem with my Nvidia FX5700 and spent nearly all weekend trying to figure it out.  Being a n00bie, people aren't very clear, I couldn't get Envy installed, but the following steps worked for me.

1. YOU MUST FIRST INSTALL the 'RESTRICTED DRIVERS MODULES' from command line like this:

```
apt-get update
apt-get install --reinstall linux-restricted-modules-2.6.20-16-generic
```

The Nvidia drivers and Ubuntu Kernel won't work properly without them!

2. Then install the NVIDA DRIVERS & KERNEL UPdates as shown in following[ link]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html")

You may have to uninstall and other junky driver, but the link will show you...just copy and paste the text, but you probably are in the terminal mode so you may hafta write it by hand (or print out!)

Reboot and if the star align correctly you'll get the Nifty NVIDIA splash screen before the grafix show and you're off and running..

It's quite freaky when the drivers break and the kernel drops you down to command line, when you've been used to pointing and clicking all your life! 

But the tinkering gives you a sense of achievement and makes you feel like some sort of two-bit genius when it works!!:guitar:

---

### Post by juststealthbabay on 2007-10-04
I was having the same problem myself.

Here's how I fixed it:
Under the "Screen" section of your /etc/X11/xorg.conf file, add the following line.
    Option         "NvAGP" "1"

Apparently there are problems with certain AGP graphics cards.
More information can be found [here]("http://en.opensuse.org/NVIDIA"). (under "Troubleshooting")

---

### Post by xpod on 2007-10-04
If the restricted drivers manager is not working in feisty then you could always try envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

Both methods work fine for me on feisty using an fx5500....mines an older pci type though.

---

