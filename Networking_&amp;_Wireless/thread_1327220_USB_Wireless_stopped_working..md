---
title: "USB Wireless stopped working."
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by benrufus on 2009-11-15
Hi

I recently bought an LM001 wireless usb stick on the internet because i was told it worked out of the box with ubuntu, but the one they sent me was not this it was an unbranded one, dunno if it was the same chipset because it worked perfectly out of the box so i didnt complain and i kept it. I have been using it with no problems for about two weeks and yesterday it starting working intermittently and then my computer stoped picking it up altogether. i can not see any wireless when i go to network manager on top panel. my computer dosent have any wireless built in, ethernet works fine, i am running 9.04. Please help!!!!!!!........ Thanks

---

### Post by benrufus on 2009-11-23
> **benrufus said:**
> Hi

I recently bought an LM001 wireless usb stick on the internet because i was told it worked out of the box with ubuntu, but the one they sent me was not this it was an unbranded one, dunno if it was the same chipset because it worked perfectly out of the box so i didnt complain and i kept it. I have been using it with no problems for about two weeks and yesterday it starting working intermittently and then my computer stoped picking it up altogether. i can not see any wireless when i go to network manager on top panel. my computer dosent have any wireless built in, ethernet works fine, i am running 9.04. Please help!!!!!!!........ Thanks

Hi posting this again because no replies - please please help!!!!!!!!!!!!!!!!!!!

---

### Post by theozzlives on 2009-11-23
do ```
lsusb
```and post the output so we can find out the chipset.

---

### Post by benrufus on 2009-11-23
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


im just getting this so i suppose it means its not even detecting the usb adapter anymore

---

### Post by benrufus on 2009-11-23
ok now i have it

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 007: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by benrufus on 2009-11-23
it took me ages swapping the adapter to different usb slots to get the output showing the ralink chipset. now i cant pick it up again

---

### Post by coffeecat on 2009-11-23
Your problem with intermittent wireless is not a wireless problem.

> **benrufus said:**
> it took me ages swapping the adapter to different usb slots to get the output showing the ralink chipset. now i cant pick it up again

It sounds as though you have a hardware problem with your USB interface.

> **benrufus said:**
> Bus 004 Device 007: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

That Ralink chipset should work just fine with a stable connection - this indeed was your experience for 2 weeks. Sorry - the problem is probably with the USB ports.

---

### Post by bkratz on 2009-11-23
> **benrufus said:**
> ok now i have it

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 007: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



It probably is worth looking at this thread, especially post number 8

[http://ubuntuforums.org/showthread.php?p=7716964#post7716964](http://ubuntuforums.org/showthread.php?p=7716964#post7716964)

---

### Post by benrufus on 2009-11-23
> **coffeecat said:**
> Your problem with intermittent wireless is not a wireless problem.



It sounds as though you have a hardware problem with your USB interface.



That Ralink chipset should work just fine with a stable connection - this indeed was your experience for 2 weeks. Sorry - the problem is probably with the USB ports.

im really confused now!!! my usb ports work with all other usb devices just not the usb wi fi adapter. (It originally worked plug and play straight out of the box) could any of the updates i installed have done something.

---

### Post by benrufus on 2009-11-23
sorry im probably not giving right info for you, im just getting used to ubuntu. my usb works for all other things, external hdd etc but not wi fi adapter. last week wi fi adapter worked perfectly. what can i do. please help!!!! let me know what info you need.....Thanks

---

### Post by coffeecat on 2009-11-24
OK - I misunderstood you. Apologies. If other USB devices are working fine then obviously you don't have a problem with USB. But what I am understanding you to say is that sometimes the wireless USB stick shows up with lsusb, and sometimes not. I wonder if the wireless device itself is faulty?

Do you have access to another computer on which you could run the Ubuntu desktop CD? If so, boot up with the live CD and when you get into the desktop, plug the wireless device in and run lsusb. Is it seen? If you get the same behaviour - sometimes seen and sometimes not - then you definitely have a faulty device.

---

### Post by benrufus on 2009-11-24
Cheers Coffeecat. I just tried **lsusb** booting up on a live usb and it still didnt pick up the adapter. the reason i bought that one was because it had the ralink chipset which was supposed to be good with ubuntu. anyway i have managed to get a different adapter working with ndiswrapper. Thanks for all your help!

---

