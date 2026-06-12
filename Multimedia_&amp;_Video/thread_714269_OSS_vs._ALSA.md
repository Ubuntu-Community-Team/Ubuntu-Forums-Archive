---
title: "OSS vs. ALSA"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by Mauler5858 on 2008-03-03
I am using .wine to run ventrilo and world of warcraft.  OSS drivers were setup by default and seem to work ok.  I was wondering any input on this, if ALSA drivers were generally better and if so any tips for configuring them.

---

### Post by Mauler5858 on 2008-03-04
Bump

---

### Post by SunnyRabbiera on 2008-03-04
both can do a respectful job, I personally find alsa works better but it depends on the distro

---

### Post by Yellow Pasque on 2008-03-04
I'm assuming you have the default Ubuntu setup with ALSA 1.0.14 and OSS 3.x
In that case, I'd say use the ALSA drivers, because ALSA can emulate basic OSS functions if you install the alsa-oss package. Ideally, you would want to upgrade to ALSA 1.0.16 or use OSSv4, and I can give you more info if you're interested in that.

What kind of sound device do you have?

---

### Post by Mauler5858 on 2008-03-04
I have an asus a7n8x deluxe mobo so its a realtek sound processor i believe.  And yes i have not changed any of my sound settings in Ubuntu(one of the very few things that i havent touched)

---

### Post by Yellow Pasque on 2008-03-04
Ah, that's a Realtek ALC650 (AC'97 compliant) chip. I would not bother upgrading ALSA since there haven't been a lot of changes to that driver of late.

Basically, you should choose the ALSA driver and install the alsa-oss package, and you should be good to go.

---

### Post by Mauler5858 on 2008-03-04
So if im using OSS with wine and it "works".  Should i leave it as OSS and let alsa-oss take care of it, or try to move it over to native alsa support?

---

### Post by Yellow Pasque on 2008-03-04
> **Mauler5858 said:**
> So if im using OSS with wine and it "works".  Should i leave it as OSS and let alsa-oss take care of it, or try to move it over to native alsa support?
If it ain't broke, don't fix it.

---

### Post by dondcs on 2008-03-06
> **Temüjin said:**
> If it ain't broke, don't fix it.

Well mines broke (the sound). I'm using the same A7N8X (Realtek ALC650E) and was going to try using OSS4 but I don't see ALC650E listed in the device list from your Sig. so I guess I should try installing alsa-oss?

Installed Gutsy about a week or more now and have never had sound but this is a secondary PC so I am taking my time sorting out bugs while learning a whole new OS (at least from an owner standpoint).  I know there are a bunch more things I need to follow to try to fix this sound but I saw my mobo mentioned.

---

### Post by Yellow Pasque on 2008-03-07
> **dondcs said:**
> Well mines broke (the sound). I'm using the same A7N8X (Realtek ALC650E) and was going to try using OSS4 but I don't see ALC650E listed in the device list from your Sig. so I guess I should try installing alsa-oss?

Installed Gutsy about a week or more now and have never had sound but this is a secondary PC so I am taking my time sorting out bugs while learning a whole new OS (at least from an owner standpoint).  I know there are a bunch more things I need to follow to try to fix this sound but I saw my mobo mentioned.
You could still try OSS4. They list devices by driver/south bridge. Here's yours on the list.
> ich     pci10de,6a      Nvidia nForce2

---

### Post by dondcs on 2008-03-08
Ok thanks I'll give it a try.

---

### Post by dondcs on 2008-03-08
So now I have sound with OSS4. Fixed a problem and got an upgrade all in 1...thanks.

---

### Post by dondcs on 2008-03-12
SOmehow my audio devices have disappeared. FIrst it was working then it stopped within the same session (maybe after going to sleep?). After restarting it would be back and the BIOS seems to find the sound card fine during boot up but now seems like the sound card is not being detected or doesn't have the drivers installed? I was watching U-tube and it seemed ok but then crashed firefox a couple times. Now rebooting doesn't help and it's stuck without the sound device.

**After running ossinfo:**
[INDENT]Number of audio devices:        0
Number of audio engines:        0
Number of mixer devices:        0


Device objects
 0: osscore0 OSS core services
 1: ossusb0 USB audio core services
 2: vmix0 OSS transparent virtual support


Mixer devices

Audio devices[/INDENT]

I'm not seeing any sound card when I run **lspci -v**

---

### Post by Yellow Pasque on 2008-03-12
Try running:
```
ossdetect
```

---

### Post by dondcs on 2008-03-12
I ran ossdetect from the Terminal
> bash: /usr/sbin/ossdetect: Permission denied
 

sudo ossdetect
that didn't work either and just goes straight back to the command prompt (just tried that for no reason)

Ran ossdetect -v
> Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture

---

### Post by dondcs on 2008-03-12
Is there any way to manually install the oss4 driver for my onboard sound?
I uninstalled >  sudo dpkg -r oss-linux then reinstalled it but same result with no device detected.

I'm guessing if I reinstall ALSA it will come back...

---

### Post by Yellow Pasque on 2008-03-12
If the OS, or in Ubuntu's case, HAL (Hardware Abstraction Layer) can't see the device, I doubt manually installing a driver would do the trick, regardless of if it's OSS or ALSA. This sounds like a hardware issue to me.

Maybe try disabling/enabling the onboard audio in BIOS?

---

