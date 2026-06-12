---
title: "No Sound with Second Hard Drive"
date: 2009-04-15
forum: Mythbuntu
---

### Post by milpool on 2009-04-15
I am having a strange problem with my mythbunutu. I am using a HVR-1600 card for capture, it works fine with only one hard drive plugged in, however when I went to install a second hard drive, if I just plug in the drive and not even mount it I get no audio from my capture card, video works fine. If i unplug the drive again I get sound again. Does any one have any idea why this might be happening, it almost sounds like It might be a power issue or something. 

Thanks

---

### Post by AlecJ on 2009-04-15
Are these usb drives?

---

### Post by milpool on 2009-04-15
no, they are sata drives one is /dev/sda the other /dev/sdb

---

### Post by nickrout on 2009-04-15
Is your power supply up to the extra hardware? perhaps the capture card is slightly down on power and malfunctioning. Seems odd but odd things happen!

---

### Post by milpool on 2009-04-15
> **nickrout said:**
> Is your power supply up to the extra hardware? perhaps the capture card is slightly down on power and malfunctioning. Seems odd but odd things happen!

This was sort of what I was thinking, although i think that I should have enough power its a 380W power supply.

---

### Post by AlecJ on 2009-04-16
don't sound like that to me, sounds more like the extra hardware has kidnapped the device input address.
If a power supply is under load they tend to just shut down, but your bios has normally beeps an under voltage alarm at you first. It can't decide to just shut down functions due to a suppected lack of power (nice idea though).
You should be looking at the dsmeg output with and without the extra drive attached.

---

### Post by nickrout on 2009-04-16
> **AlecJ said:**
> don't sound like that to me, sounds more like the extra hardware has kidnapped the device input address.
If a power supply is under load they tend to just shut down, but your bios has normally beeps an under voltage alarm at you first. It can't decide to just shut down functions due to a suppected lack of power (nice idea though).
You should be looking at the dsmeg output with and without the extra drive attached.

Agree with what you are saying about power, which is why I would say it is odd if that were happening. 

But plugging in an extra drive does not steal any "device input address", unless there is an extra sata or ide card involved.

I am intrigued to know whether it is sound from the tuner card or sound from the sound card that stops working. ie will downloaded or pre-recorded material still play with sound?

---

### Post by AlecJ on 2009-04-17
very true, I guess when there is no sound you still get video?

---

### Post by milpool on 2009-04-17
Yeah, I still get video on live tv, and sound on previously recorded material works fine which means the sound card is fine, but something is wrong with the sound tuner I guess.

---

### Post by EnglishSparrow on 2009-04-17
Sounds like the hard drive is stealing your capture card's IRQ. The bios is in control of this so maybe changing kernel will help?

---

