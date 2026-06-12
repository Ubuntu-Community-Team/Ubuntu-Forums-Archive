---
title: "Hauppauge remote is sending key presses."
date: 2010-05-05
forum: Multimedia Software
---

### Post by meatychunks on 2010-05-05
Hi,

I've got a strange problem with my Hauppauge card; I've just undertaken a clean install of Mythbuntu 10.04, and the built in Hauppauge remote for my Nova S2 HD card is intercepting remote signals from the number and direction keys and sending them as keypresses to the terminal - even when lirc isn't running.

I didn't have this issue under 9.04 - but it seems that whatever is intercepting the IR signal is preventing LIRC from getting a look-in as it makes no difference whether lirc is running or not.

I found this thread: [http://ubuntuforums.org/showthread.php?t=715257](http://ubuntuforums.org/showthread.php?t=715257) but the link to the explanation is dead and my attempts to blacklist lirc_i2c and gpio_keys have made no difference.

Any assistance greatly appreciated.

---

### Post by meatychunks on 2010-05-06
A little more digging and it seems that in previous Ubuntu releases this problem was avoided by having an info.ignore line for "cx88 IR" in a lirc.fdi file.

However, since 10.04 is now HAL-free it seems this now has no effect.

Is there a work-around to prevent whatever it is from taking control of the Hauppauge IR receiver before LIRC can get to it?

---

### Post by xc3RnbFO8P on 2010-05-06
Do you have multimedia keyboard?

---

### Post by meatychunks on 2010-05-06
No, I've got a normal wireless keyboard on a usb dongle...

---

### Post by rafe101 on 2010-06-12
I'd really appreciate help with this too.
It sounds like my situation is identical.

---

