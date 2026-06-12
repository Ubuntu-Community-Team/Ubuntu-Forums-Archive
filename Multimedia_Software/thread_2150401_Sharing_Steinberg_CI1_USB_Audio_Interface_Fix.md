---
title: "Sharing Steinberg CI1 USB Audio Interface Fix"
date: 2013-05-31
forum: Multimedia Software
---

### Post by ProgenitorVirus on 2013-05-31
Hi all,

I've recently decided to revisit Ubuntu, and found that my Steinberg CI1 USB Audio Interface was not being recognized.

Doing some sleuthing for a fix, I found many users with the same problem, having to return the device for a more Linux-friendly brand or model.  I want to share my experience in fixing this issue for whoever may be affected, as I have found a fix that seems to work and may alleviate (or cause :p) someone a headache.

I'm going to start out and say that while I'm familiar with Linux, and am a programmer, I'm not going to pretend I've come up with any of this information.  I've just found the information and applied some common sense is all :)

So, the problem will manifest itself with no audio.  On closer inspection:

```
$ aplay -l
(yeilds no results)


$ lsusb
...
Bus 002 Device 016: ID 0499:1501 Yamaha Corp.
... 
```


So it is recognized at least.  $ lsusb -v -d 0499:1501 will show more information.


So I came across this post in regards to a similar device:  [http://linux-audio.4202.n7.nabble.com/Support-for-Steinberg-UR22-Yamaha-USB-chipset-0499-1509-td82888.html](http://linux-audio.4202.n7.nabble.com/Support-for-Steinberg-UR22-Yamaha-USB-chipset-0499-1509-td82888.html)

On there, a helpful user Clemens Ladisch posted a fix:


> 
Please try adding the following entry somewhere in sound/usb/quirks-table.h: 

{
        **USB_DEVICE(0x0499, 0x1509),**
        .driver_info = (unsigned long) & (const struct snd_usb_audio_quirk) {
                /* .vendor_name = "Yamaha", */
               ** /* .product_name = "Steinberg UR22", */**
                .ifnum = QUIRK_ANY_INTERFACE,
                .type = QUIRK_COMPOSITE,
                .data = (const struct snd_usb_audio_quirk[]) {
                        {
                                .ifnum = 1,
                                .type = QUIRK_AUDIO_STANDARD_INTERFACE
                        },
                        {
                                .ifnum = 2,
                                .type = QUIRK_AUDIO_STANDARD_INTERFACE
                        },
                        {
                                .ifnum = 3,
                                .type = QUIRK_MIDI_YAMAHA
                        },
                        {
                                .ifnum = 4,
                                .type = QUIRK_IGNORE_INTERFACE
                        },
                        {
                                .ifnum = -1
                        }
                }
        }
},


All I did was change the bolded lines to:

```
USB_DEVICE(0x0499, 0x1501),

and

/* .product_name = "Steinberg CI1", */ 
```


In the end, all I had to do was download the latest kernel for 12.04.2, add the modified above lines to the sound/usb/quirks-table.h file, compile the kernel, install it, and rebooted.  And everything seems to be in working order now :)


This was the first time I've had to tweak the kernel, but the changes I needed to make were pretty basic, so I just followed this guide:

[https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)


If anybody needs a step-by-step I'll certainly do my best to help!


- Cheers

---

### Post by derwojetztdaist on 2013-07-11
hej pro,
i've the exactly same problem with the steinberg ci1, is it possible to get a step-by-step from you? i'm a total beginner in ubuntu...

---

### Post by pedram2 on 2013-10-07
Looks like Kernel 3.11.2 (and possibly earlier?) now support the Steinberg CL1. I had it plugged into my computer and would boot into Windows for anything requiring sound. Just today I noticed sound started coming out of my speakers when I was running Linux. Looks like snd_usb_audio is the key module. I didn't install or configure anything. I'm running Arch Linux but thought I'd share. I was pretty close to selling the device until now.

---

### Post by Bucky Ball on 2013-10-13
Incidentally, you should find a couple of /sound/usb/quirks-table.h files by running:

```
locate /sound/usb/quirks-table.h
```

You just need to figure which one to change.

---

### Post by Bucky Ball on 2013-10-13
Rather than reinstall the entire OS (from a stable one to a fresh release which may be problematic and has only nine months support) you can simply install the 3.11 kernel in 12.04 and choose it at boot to see if that works:

[http://ubuntuhandbook.org/index.php/2013/09/linux-kernel-3-11-released-install-upgrade-in-ubuntu-13-0412-04/](http://ubuntuhandbook.org/index.php/2013/09/linux-kernel-3-11-released-install-upgrade-in-ubuntu-13-0412-04/)

No different, reboot and choose the stable kernel again.

---

### Post by 8rfAAn7 on 2013-10-13
ProgenitorVirus, I'm trying to do the same thing with the UR22, but I can't find the sound/usb/quirks-table.h file... could you be more specific as where to find it?  

Thanks a lot!

---

### Post by Bucky Ball on 2013-10-13
> **8rfAAn7 said:**
> ... I can't find the sound/usb/quirks-table.h file... 

Read the posts:

```
locate /sound/usb/quirks-table.h
```

You'll find two or three. They will be inside other folders, NOT in /sound/usb by itself. No such.

---

