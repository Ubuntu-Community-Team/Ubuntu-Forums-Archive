---
title: "How do I get a new video card working?"
date: 2008-06-07
forum: Multimedia Software
---

### Post by Eric Weir on 2008-06-07
I just put a video card in my system. ***Card: ***nVIDIA e-GeForce FX 5200 128 Mb AGP ***System: ***P4 1.6 Ghz, 512 Mb, Amprton 925 ATX, 40 Gb.

Naive me. Assumed that's all I had to do. Forgot, this is Linux and I'm a Linux ignoramous.

What do I do? I take it reconnect the monitor to the onboard processor. Install a driver. What driver? How? Tweak some file. What file? How?

I checked the sticky thread on this but the posts were pretty old. 

Pointers would be appreciated.

Thanks,

---

### Post by Metaleks on 2008-06-07
The driver you are looking for can be found on nVidia's website.  A direct download can be found here:

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/NVIDIA-Linux-x86-173.14.05-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/NVIDIA-Linux-x86-173.14.05-pkg1.run")

Once you've downloaded it, go into the directory that it's in and type ```
sh NVIDIA*
```
into the terminal.  You first may need to stop X11 from running.  If you get some sort of message like that, to stop X11, enter:
```
sudo /etc/init.d/gdm stop
```
After this, you'll be in terminal mode (there will be no GUI).  Then just enter the command above that deals with running the driver.  Just follow the instructions.  After everything is done, to get your gdm back up and running, enter:
```
sudo /etc/init.d/gdm start
```

That's about it!

---

### Post by Eric Weir on 2008-06-07
> **Metaleks said:**
>  . . . . just enter the command above that deals with running the driver.  Just follow the instructions. . . .
Thanks, Metaleks. After posting my plea for help I checked the Ubuntu how-to's which lead me to the nVIDIA website. The instructions there were relatively clear. Your's are a lot clearer.

Thanks much.

Sincerely,

---

### Post by Metaleks on 2008-06-07
> **Eric Weir said:**
> Thanks, Metaleks. After posting my plea for help I checked the Ubuntu how-to's which lead me to the nVIDIA website. The instructions there were relatively clear. Your's are a lot clearer.

Thanks much.

Sincerely,
No problem.  Glad it worked out for you. ;)

---

### Post by Eric Weir on 2008-06-18
> **Eric Weir said:**
> Thanks, Metaleks. After posting my plea for help I checked the Ubuntu how-to's which lead me to the nVIDIA website. The instructions there were relatively clear. Your's are a lot clearer.
I spoke too quickly. The instructions are clear. Unfortunately, they assume that I have a display after installing the card. That turns out not to be the case. I can't see anything. Can't even get to the bios, let alone the command line in grub. 

I seem to be in a double-bind. Can't do anything I've seen suggested for getting the driver installed.

Any help would be appreciated.

Thanks,

---

### Post by horan116 on 2008-06-18
just to make it clear your stating after the attempt to install the driver you no cannot get grub to even boot?

---

### Post by Pjotr123 on 2008-06-18
Do this:
[http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)

---

### Post by Eric Weir on 2008-06-18
> **horan116 said:**
> just to make it clear your stating after the attempt to install the driver you no cannot get grub to even boot?
No. After installing the card I can't see anything. Can't even boot into bios -- or maybe I can, I just can't see whether I have or not. 

No display whatever after installing card.

Thanks for asking.

Sincerely,

---

### Post by Eric Weir on 2008-06-18
> **Pjotr123 said:**
> Do this: [http://ubuntutip.googlepages.com/nodisplay](http://ubuntutip.googlepages.com/nodisplay)
The suggestion is this: > [SIZE=2]Boot your computer in Recovery Mode. That's the second option in the Grub boot menu. When you don't normally get to see the Grub menu, render it visible by pressing the Esc (escape) key several times when the BIOS screen turns up.[/SIZE]
That assumes I can see the grub menu. I can't. I can't see anything.

E.g., my monitor is in sleep mode before booting. Normally, as soon as the boot process starts, the monitor wakes up. With the new card installed nothing happens. Monitor continues to snooze. Can't get to bios. Can't get to grub menu. It's as is if I had no monitor at all.

Thanks for the suggestion nevertheless.

Sincerely,

---

### Post by Pjotr123 on 2008-06-18
Are you sure that you've connected the monitor correctly *physically*? It sounds as if it's disconnected.

---

### Post by Eric Weir on 2008-06-18
> **Pjotr123 said:**
> Are you sure that you've connected the monitor correctly *physically*? It sounds as if it's disconnected.
I'll double check. But I've connected and disconnected the cable several times, now. I believe at least once I've screwed both screws down almost tight. Will check again, though.

Thanks,

---

### Post by Eric Weir on 2008-06-18
> **Eric Weir said:**
> I'll double check.
Nope. Being careful to make sure the connector is fully seated, screwing the screws down tight, still no display.

Called the shop that made the machine -- in 2002 -- and sold me the card -- a couple weeks ago. They pointed me to the place in the bios to change the primary graphics processor setting to agp. It was already set to agp.

They suggested leaving the card in but connecting the monitor to the onboard processor, then download and install the driver, then rebooting after connecting the monitor to the card.

Even with the monitor connected to the onboard processor, with the card in, there is no display.

Their fall-back option after that is "Bring the machine in." May have to do that.

Thanks again.

Sincerely,

---

### Post by Metaleks on 2008-06-18
I actually had a problem with my monitor not too long ago.  It turns out that some fuse blew (or something) and that that was the reason it wouldn't turn on.  If you can, test the monitor on another system.  That way we can see if the problem is the monitor itself, or your current system.  I'm betting it's the monitor.

---

### Post by Eric Weir on 2008-06-18
> **Metaleks said:**
> If you can, test the monitor on another system.
Thanks, Metaleks. You lose. The monitor works fine if I use the onboard processor.

I've spoken again with the shop that made my machine. They think now that the motherboard may not be able to work with a video card with more the 64 Mb of memory. The one I'm trying to install has 128.

I should just give in and buy a new machine. It wouldn't be that expensive. But I want to get a decent installation of Linux running on the machine I have -- p 4, 1.6 ghz, 512 mb ram; not state of the art, for sure, but it should be able to handle it; so far I've only been able to get a very sluggish installation; graphics processing has been a suspect -- before I make even that investment. 

I appreciate the suggestion though.

Sincerely,

---

