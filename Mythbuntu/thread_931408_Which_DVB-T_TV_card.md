---
title: "Which DVB-T TV card?"
date: 2008-09-27
forum: Mythbuntu
---

### Post by alexeix on 2008-09-27
Hi,

I'm trying to set up Mythbuntu, but neither of my existing DVB-T TV cards seems to work out of the box.

The cards I've tried, are:  Hauppauge WinTV Nova-T-500 and the Compro Videomate DVB-T300.

Can anyone recommend a dual tuner DVB-T card which will 'just work' out of the box or alternatively, is there a straightforward way to get my Hauppauge card working?

I found a possible solution online, but some say it works and others say it doesn't...

I'm not sure how to check the version of Mythbuntu I'm running, but I downloaded and installed it within the last 6 months.

I'm not an advanced Linux user, but have some command line skills (from Unix days), e.g. I can interpret instructions and apply them!

Thanks in advance...

---

### Post by nasha on 2008-09-27
Here's the install guide for the Hauppauge:
[HTML]http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI#Installing[/HTML]

---

### Post by alexeix on 2008-09-27
I tried those instructions, but they had a drastic effect on my PC; it shut itself down and when I re-booted, nothing happened.

Disconnected the power cable from the PC and I was able to boot up, but the TV card still didn't work.

Can anyone suggest a UK dual DVB-T card which just works out of the box in Mythbuntu?

There must be a few, surely?

---

### Post by alexeix on 2008-09-27
By the way, I'm running Mythbuntu 8.0.4.

Hoping for some card suggestions or advice on how to install this card correctly.
It's a fairly common card in the UK, so I was hoping it would have been included automatically.

Thanks!

---

### Post by alexeix on 2008-09-28
Figured out what I did wrong and correctly configured Mythbuntu.

Scanned for channels on both tuners and was able to watch TV.

However, I shut down the PC and when I switched it on again later, Mythbuntu couldn't see either tuner on the card.

I've tried re-booting again and re-running the set-up, but Mythbuntu just doesn't see the card.

Anybody know why this might be?

Help! :(

---

### Post by amphibem on 2008-09-29
> **alexeix said:**
> Figured out what I did wrong and correctly configured Mythbuntu.

Scanned for channels on both tuners and was able to watch TV.

However, I shut down the PC and when I switched it on again later, Mythbuntu couldn't see either tuner on the card.

I've tried re-booting again and re-running the set-up, but Mythbuntu just doesn't see the card.

Anybody know why this might be?

Help! :(

Not certain what you are doing, but I do know that to load the firmware it is necessary to do a full shutdown then startup. 

Although re-reading, it sounds that is what you are doing. 

Going back to the setup stuff, you don't need most of that in the guide now. Just 

```
sudo gedit /etc/modprobe.d/options
Add: options dvb-usb-dib0700 force_lna_activation=1

```

I also add a line to prevent the card from going to sleep, can't remember exactly what it is.


This card should work straight out of the box, this command should tell you if it is loaded properly:

```
dmesg | grep -i dvb
```

Sorry for being all over the place, hope that helps.

---

### Post by alexeix on 2008-09-29
Thanks for the advice.  I did a re-install from scratch and it subsequently worked.

I think this was definitely down to 'user error'. 

Next problem: I think I downloaded the 64 bit image, meaning that I'm having a number of issues running Flash, etc.

Time to download the 32 bit ISO...

Thanks again!

---

