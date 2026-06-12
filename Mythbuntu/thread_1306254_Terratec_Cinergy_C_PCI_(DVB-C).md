---
title: "Terratec Cinergy C PCI (DVB-C)"
date: 2009-10-30
forum: Mythbuntu
---

### Post by Juzz on 2009-10-30
Hi there,

I am running myth 0.21.0+fixes19961-0ubuntu8

I used to have some hauppage 500 cards in my machine, but they have now been replaced by two of the abovementioned cards.

I have managed to compile the mantis driver as a DKMS module as per this page:
[http://www.linuxtv.org/wiki/index.php/Mantis_with_DKMS]("http://www.linuxtv.org/wiki/index.php/Mantis_with_DKMS")

However if I go into "Capture Card Setup" in mythbuntu setup and then I choose "DVB DTV capture card (v3.x)" I can choose device 0 and device 1, but both deliver this error in
```
Frontend ID: Could not get card info for card #0 Subtype:    Unkno
```

Should I do something special with the driver to inform about DVB-C?

Hope you can help.

Cheers
Juzz

---

### Post by Juzz on 2009-10-30
I forgot to ask - will the old ivtv drivers interfere - and how can I stop them from loading?

---

### Post by Juzz on 2009-10-30
I've now tried to pull out one of the cards - no dice however.

In dmesg I've discovered this sorry message:

```
mantis_frontend_init (15): Probing for CU1216 (DVB-C) 
mantis_frontend_init (15): !!! NO Frontends found !!!
```

:(

---

### Post by Juzz on 2009-10-31
From what I can guess - the card doesn't claim the tda10023 driver.

How can it be made to claim it?

---

### Post by joshoekstra on 2009-10-31
Why don;t you try out a more recent kernel? S2API started to work well after 2.6.29 or 30. You can either go to 9.10 to get a later kernele or try the mainline-kernel ppa:
[PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
I got 2.6.30.6 running on 9.4, but I'd skip over to 9.10 if I were you to also use the fixed DVB-issues.

---

### Post by Juzz on 2009-11-01
OK, trying to do an upgrade to karmic.

[EDIT]: Is EVERYONE upgrading today? I am getting annoyingly low speeds on the package downloads...

---

### Post by Juzz on 2009-11-01
compile errors...

Both when trying to build a dkms package and when trying to follow the "Current s2api driver" here
[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C]("http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_C_DVB-C")

:(

---

### Post by Juzz on 2009-11-01
By making it skip firewire drivers - it compiled...

kernel panic under boot :(

---

### Post by joshoekstra on 2009-11-01
Maybe [this]("http://ubuntuforums.org/showthread.php?t=857524") helps, otherwise shoot a mail to the linuxtv-mailinglist...

---

### Post by Juzz on 2009-11-05
I haven't been able to make it claim the card.

I've been so desperate that I took a look at the sources - however since I am not big in C coding all I've been able to do is insert some debug messages at a few places.
It does try the function tda10023_attach(), but somehow it fails on the id of the card (even though my lspci is excactly as the linuxtv wiki) - which returns an id of 255.

I'm guessing that I have to try the linuxtv mailing list...

---

### Post by Juzz on 2009-11-05
*sigh* and the linuxtv mailinglist has been deprecated - which you only get a message about when you try to send a mail to the list...
It isn't mentioned anywhere in the registration process...

---

### Post by joshoekstra on 2009-11-05
You followed the instructions of:
[http://linuxtv.org/lists.php](http://linuxtv.org/lists.php)   ?
Those are the right instructions, I'm subscribed in the same way...

---

### Post by Juzz on 2009-11-05
Well I am now...

---

