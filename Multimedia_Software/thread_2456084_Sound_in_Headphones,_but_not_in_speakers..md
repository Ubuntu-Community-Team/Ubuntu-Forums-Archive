---
title: "Sound in Headphones, but not in speakers."
date: 2021-01-04
forum: Multimedia Software
---

### Post by rosesylviap on 2021-01-04
So after installing and reinstalling Ubuntu several times, and messing with the settings several times, I decided it was time to slow down, stop messing with the settings, and do some detective work on my hp EliteBook 8540p running Ubuntu 20.04.1. I am a novice to ubuntu and linux in general and learning as I go. I feel way out of my depth, but idk it's how I learn.

The problem is sort of complex. At first, I just thought my speakers were broken, since I could hear audio when the headphones were plugged in, but no audio from the internal speakers when the headphones were unplugged. My initial fix for this was to use alsamixer. I unmuted the "Speaker" channel, turned the volume up, disabled auto-mute. ...And it worked, until i restarted it.

After that, I decided to try pavucontrol. It automatically defaults to "Headphones (Plugged In)" and for several weeks, I've simply had pavucontrol open automatically on startup so that I can just switch the output to "Speakers (unavailable)" and that worked just fine, but honestly, I want my sound to *just work*

so after a bit more digging, I discovered how to use "acpi -l" and discovered that acpi isn't registering when my headphones are plugged or unplugged. I have dedicated jacks, one for audio in- and one for audio out. apparently my computer isn't detecting when I insert/remove the headphone jack.

ideally, I'd like to find a software fix for this. If it's a hardware problem, I'd like to find a way (if at all possible) to disable my computer from using the headphone jack completely and act like it doesn't exist, so that I can simply connect headphones via bluetooth when I need them.

Thanks very much in advance.

-rose.proctor

---

### Post by slickymaster on 2021-01-04
Thread moved to **Multimedia Software** for a better fit

---

### Post by tea for one on 2021-01-04
> If it's a hardware problem, I'd like to find a way (if at all possible) to disable my computer from using the headphone jack

If the PC is reasonably new, you may be able to jump into the UEFI set up pages and de-activate/disable the device.

---

### Post by rosesylviap on 2021-01-04
It doesn't seem so simple, but I'm looking into doing this. Is there anything beyond simply a hardware problem that would prevent acpi_listen from detecting insertion/removal of the headphone jack?

---

### Post by rosesylviap on 2021-01-04
> **tea for one said:**
> If the PC is reasonably new, you may be able to jump into the UEFI set up pages and de-activate/disable the device.

I'm extremely annoyed at the fact that there are no Linux options for installing the usb UEFI boot tools. I think my laptop is a little too old - it's warranty expired in 2014, I just discovered.

---

### Post by tea for one on 2021-01-04
Your laptop must be 2012/2013 vintage and, as you mentioned, your sound works with headphones and speakers (albeit you have to select the desired device via pavucontrol).

I would be more than happy to have a 7 year old device working quite nicely.

UEFI firmware updates are controlled by the device manufacturer and are not controlled by Linux distributions.
Some vendors (Intel for example) allow their UEFI firmware updates to be OS agnostic.

HP is a member of the Linux Vendor Firmware Service [https://fwupd.org/](https://fwupd.org/), but I would expect that newer PCS would more likely be a priority for this service.

---

### Post by rosesylviap on 2021-01-04
@tea for one, thanks for the pointers! so I discovered a temporary solution to this issue. I installed HDAJackRetask and found the headphone jack and selected "Override" and from the drop-down menu, I chose "Not Connected"

This works for now, but I'm not satisfied with this solution because I really want to find out the cause of the problem, so I at least understand what's really happening with this. I'll look into the linux vendor firmware service right now, but I am hesitating to mark this issue as "Solved" because it certainly doesn't feel solved to me. It feels a bit more like a bandaid fix, as I haven't diagnosed the actual cause of the issue.

You are correct, my sound works with both headphones and speakers, however, the solution of overriding the headphone jack with hdajackretask is sort of a blunt fix to this, as it disables me completely from using my headphone audio jack. My goal here is to discover why my computer isn't detecting my headphone jack insertion, and if not fix it, at least understand the issue

---

### Post by rosesylviap on 2021-01-04
also, there is not available UEFI or BIOS update available through that service for my device, unfortunately.

---

