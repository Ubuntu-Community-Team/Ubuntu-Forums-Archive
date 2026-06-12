---
title: "MythTV and USB-UIRT"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by basketcase on 2007-02-11
Okay...I plugged my USB-UIRT in, ran the setup in lirc-0.8.1 to configure a USB device, then USB-UIRT.  I press the buttons on my remote, I get a red-light, so makes me think that part is working.  

I do cat /dev/ttyUSB0 and start pressing buttons, I get: 
> cat /dev/ttyUSB0

Â
%-ü
^X
Which makes me think it is seeing the buttons being pressed.  Do I just need to do an irrecord /dev/ttyUSB0?  

I created this post more so to get discussion relevant to Ubuntu and USB-UIRT and to see if anyone had an experience.  

Will report back as I find more.

Also what I'd like to do is get USB-UIRT to control my Motorola DTC-2244 cable box, so that would be the next step.  

Do I need to put something in /etc/lirc/hardware.conf?  only module is loading now is lirc_ir2.

---

### Post by sapg on 2007-03-29
I'm trying to get this to work also, I want to use it with Mythtv, I have a Hauppauge Nova-T-500 PCI TV tuner but the built in IR receiver on that does not seem to be supported yet so I bought a USB-UIRT thinking it would be easy.

I can't figure out what I supposed to do.  Does anyone have any instructions for a dummy?

Thanks,
Sapan

---

### Post by basketcase on 2007-03-29
> **sapg said:**
> I'm trying to get this to work also, I want to use it with Mythtv, I have a Hauppauge Nova-T-500 PCI TV tuner but the built in IR receiver on that does not seem to be supported yet so I bought a USB-UIRT thinking it would be easy.

I can't figure out what I supposed to do.  Does anyone have any instructions for a dummy?

Thanks,
Sapan


I haven't had much time to play with my box lately, but everything I have found points me to buying a serial-UIRT.  

I did find a brief discussion regarding the USB-UIRT over on MythtvTalk website with Fedora, but I haven't gone as far with Ubuntu yet.  I'd only hope with Fiesty Fawn on it's way out the support is there.

---

### Post by sapg on 2007-04-09
I hate to tell you this but I am running the beta version of Feisty Fawn (amd64).  Maybe something will change with the official release. :-)

---

### Post by djsaltarelli on 2007-05-13
I figured this out yesterday and wrote a documentation page. the usb-uirt is a great solution, but there was NOTHING out there telling one how to set it up on Ubuntu. Here you go:

[Lirc_USB-UIRT]("http://help.ubuntu.com/community/Lirc_USB-UIRT")

Enjoy

/djsaltarelli

---

### Post by sapg on 2007-05-15
Thanks so much!  With your help I have my remote working, now I just have to figure out why my volume buttons don't seem to do anything.

:-)

---

### Post by nswint on 2007-08-22
> **sapg said:**
> Thanks so much!  With your help I have my remote working, now I just have to figure out why my volume buttons don't seem to do anything.

:-)

sapq and anyone who got this to work.  Would you share your lircd.conf and .lircrc files.  I've followed the setup in [https://help.ubuntu.com/community/Lirc_USB-UIRT](https://help.ubuntu.com/community/Lirc_USB-UIRT)  but I'm not receiving any ir signals on /dev/ttyUSB0

---

### Post by nswint on 2007-08-23
I got it to work.  I have the latest USB-UIRT with the additional 56KHz IR Sensor so I don't  know if that makes a difference.  In my hardware.conf file I made the following change.

```

DRIVER="usb_uirt_raw"

```

I restarted lirc and then ran irw and I saw codes from my Happauge_350 remote.  I'll make an addition to the community guide page with a note to users that newer models may require usb_uirt_raw instead of uirt2_raw

---

### Post by nswint on 2008-04-20
Anyone with a broken usb-uirt on gutsy can now get ir control back with lirc-0.8.3pre2

I'm using it on hardy heron rc and i've regained use of my beloved usb-uirt

---

