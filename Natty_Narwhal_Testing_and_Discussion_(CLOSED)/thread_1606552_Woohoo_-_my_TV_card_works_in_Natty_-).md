---
title: "Woohoo - my TV card works in Natty :-)"
date: 2010-10-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-10-26
I couldn't get it to work in Lucid and I think I tried everything. In Natty I installed TVTime and it picked it up straight away :-) Happy days!
BTW it's a Phillips semiconductor (Avermedia) SAA7134

---

### Post by VMC on 2010-10-26
> **Quackers said:**
> I couldn't get it to work in Lucid and I think I tried everything. In Natty I installed TVTime and it picked it up straight away :-) Happy days!
BTW it's a Phillips semiconductor (Avermedia) SAA7134

Has there already been that much of a change in video drivers for Natty to pick up you tv card and Marverick couldn't?

I'm waiting for first alpha, then I will use zsync from then on.

---

### Post by Quackers on 2010-10-26
I'm not sure there have been any yet. All I know is the card wouldn't work in 10.04 but it does now. Maybe somebody could enlighten me?

---

### Post by coffeecat on 2010-10-26
From what I remember from my incoherent fumblings with a Hauppage  TV tunercard with a Phillips chipset is that it needed the linux-firmware-nonfree package to work. But that was in the transition from Jaunty to Karmic iirc. All the firmware was lumped together in Jaunty and I was nonplussed when I installed Karmic and the card failed to work. Until I found the nonfree package, that is.

I'm not in what passes for Natty atm - posting from Lucid - so I can't check, so do you have the nonfree package installed already? Or perhaps the 2.6.36 kernel drivers don't need the firmware.

Or perhaps I'm talking a load of cobblers. :redface:

---

### Post by ranch hand on 2010-10-26
I have never had a TV card but really want one.

What I do know is that the driver from ATI for my card did not exist until 9.04.  At that time it was equal to the FOSS driver.  Since then the FOSS  drivers get better with each kernel while the ATI driver does not.

The FOSS drivers are improving by leaps and bounds.  Great stuff.

I would bet this is the reason for the card working.

---

### Post by Quackers on 2010-10-26
I was browsing threads earlier and had occasion to look at this page
[http://packages.ubuntu.com/en/maverick/i386/linux-image-2.6.35-22-generic-pae/filelist](http://packages.ubuntu.com/en/maverick/i386/linux-image-2.6.35-22-generic-pae/filelist)
and noticed the following entries 
```
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/video/saa7134/saa7134-alsa.ko
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/video/saa7134/saa7134-dvb.ko
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/video/saa7134/saa7134-empress.ko
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/video/saa7134/saa7134.ko

```
Hmm I thought, I don't know if these were in Lucid but I'll give it a try, et voila!

Edit: Actually I only tried getting the card to work in Lucid, I think. This seems to suggest it would have worked in Maverick, if I had tried it.

---

### Post by cariboo on 2010-10-27
I've had an saa-7134 (MSI TV@nywhere plus) based card for years, I've always managed to get it to work on whatever version I've been using, it's always been a matter of picking the correct card number.

I live in an area where there is only two over the air analog tv stations, so I've always connected it to one of my satellite receivers via S-video.

---

### Post by Quackers on 2010-10-27
> **cariboo907 said:**
> I've had an saa-7134 (MSI TV@nywhere plus) based card for years, I've always managed to get it to work on whatever version I've been using, it's always been a matter of picking the correct card number.

I live in an area where there is only two over the air analog tv stations, so I've always connected it to one of my satellite receivers via S-video.

Hmm, interesting.
In Lucid I kept getting a modprobe error (I think it was) and TVTime just started then closed immediately. 
Also in Lucid whenever I shutdown the laptop I would get modprobe errors shown listing SAA7134.
In the logs it would say something like SAA7134 failed and would be ignored.
Not so now with Natty.

---

### Post by cariboo on 2010-10-27
Before Maverick, you usually had to create a conf file in /etc/modprobe.d with the parameters your card needed to work. This is what I used:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

In Natty it gets detected as card=85, and there isn't a need for the configuration file.

---

### Post by Quackers on 2010-10-27
Aha! The missing link! That would be why then :-)
Thank you for that.

---

