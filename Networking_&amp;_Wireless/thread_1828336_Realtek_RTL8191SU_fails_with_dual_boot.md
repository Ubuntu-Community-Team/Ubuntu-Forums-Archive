---
title: "Realtek RTL8191SU fails with dual boot"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by KozyMatt on 2011-08-18
I purchased a Rosewill RNX-N180UBE which uses Realtek RTL8191SU. I chose this particular device because the reviews seem to agree that it works out of box on Linux and Windows 7. Upon booting the PC into Ubuntu 11.04, the device worked perfectly. When rebooting into Windows 7, the device would not find any networks. After talking with Rosewill technical support, I was informed that the device would not work with two operating systems on the same hard drive. I did not believe this at first but I tried the device on a netbook in the reverse order. It immediately functioned in Windows 7. However, when I rebooted into Ubuntu, it has the message "device not ready" under "Wireless Network (Manufacturer Realtek RNX-180UBE)".

I cannot make any sense of this. Is there some kind of internal memory on this device that records the first OS you used it on per hard drive and rejects anything else? If so, there must be a way of clearing it. I just find this entire situation illogical. Does anyone have any insight?


~Kozy

---

### Post by dandnsmith on 2011-08-19
The fact that you can use it with both OS, albeit under somewhat restrictive conditions, makes it no odder than some other hardware I've had through my hands. It obviously needs a hard reboot rather than a soft reboot, allowing the powerdown/powerup to reset something - if it were in some persistent memory, then you'd have a much worse job.

What you really need is the designer to tell you exactly what gets saved, and whether it can be reset by software (of a special type). It's just possible that it might be possible to set things up so that the device is sufficiently fooled - but that would need designers comments and info.

Good luck in your search

---

### Post by walt.smith1960 on 2011-08-19
If this device is accessible, you might try unplugging, wait a second and plug it back in.  Resuming after suspend is another issue but it doesn't sound like that is your problem.

---

### Post by KozyMatt on 2011-08-19
After talking with Rosewill technical support again in order to obtain the information regarding the specifics of this problem. The tech insisted it was on the OS level. I asked how that could be possible if the 2 OSs don't see each other. He spouted some nonsense, then suggested I try Realtek support instead. After further investigating, I found that the device does work on both OSs on the netbook. Because the netbook is not using 11.04 yet, it needed the fix found here [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html) to make it function. With this information, I decided to try this device on another PC with the same version of Windows. It failed, even though I had not tried it on the Linux installation for that computer. I have now determine that Ubuntu is perfectly fine, Windows 7 Starter is also fine, and Windows 7 Ultimate will not use the device. Looks like I'll need to take this up with Realtek and/or Microsoft. At least it works on all of the Ubuntu installations though, that's the only thing I consider mandatory. Thanks everyone XD


~Kozy

---

### Post by dandnsmith on 2011-08-20
Best of luck with your chases.
Perhaps you should mark this one SOLVED.

---

### Post by walt.smith1960 on 2011-08-20
> **KozyMatt said:**
> 
<snip>
 With this information, I decided to try this device on another PC with the same version of Windows. It failed, even though I had not tried it on the Linux installation for that computer. I have now determine that Ubuntu is perfectly fine, Windows 7 Starter is also fine, and Windows 7 Ultimate will not use the device. Looks like I'll need to take this up with Realtek and/or Microsoft. At least it works on all of the Ubuntu installations though, that's the only thing I consider mandatory. Thanks everyone XD


~Kozy

It doesn't work in Windows Ultimate using Rosewill or Realtek's driver?  I'd hope Microsoft and/or Rosewill would want to know about that.  I have two rtl8192su devices that I use on older laptops.  The only issues I've had with them is not wanting to resume after suspend. Chili555 found a cure for that problem.

---

