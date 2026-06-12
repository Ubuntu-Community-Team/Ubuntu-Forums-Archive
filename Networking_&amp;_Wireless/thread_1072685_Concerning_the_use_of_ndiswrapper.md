---
title: "Concerning the use of ndiswrapper"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by Professor Bacon on 2009-02-17
Greetings, Ubuntu community. I have a question about the utility known as ndiswrapper, which allows you to install Windows wireless drivers on Linux. The card in question is an Atheros Wireless a/b/g/n card, and the driver I've installed is the 32-bit Windows Vista version. The utility is informing me that the hardware is present, however, when I click the "Configure Network" button, I get an error which states "Could not find a network configuration tool." Is there perhaps some software I should have installed?

---

### Post by Ketara on 2009-02-17
Have you gone through the steps in [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) ?

Also, which Atheros card are you using specifically?

Ndiswrapper will not work unless you have exactly the right driver, and having a driver that is almost correct but not exactly correct can produce weird results like what you're getting in my experience.

---

### Post by kevdog on 2009-02-17
prof

lspci -nnm will tell you your Atheros chipset.  My bet you will need to install the ath5k driver for your need found in the linux-backports repository if you have a 242x or 5007eg.

---

### Post by Ketara on 2009-02-17
You can get a 5007EG to work using ndiswrapper. I do this because the backports modules make my graphics card stop working.

Either way really, although the ath5k way is much less work-intensive.

Kevdog, is there any news on whether or not these cards are going to 'just work' in Jaunty? I've had headaches with my card both in Hardy and Intrepid, and I really hope it's something that's being worked on since there are new posts here about Atheros cards every day.

---

### Post by kevdog on 2009-02-17
You can also used a patched version of madwifi other than ath5k which will also work and avoid the backports repository.  There are various threads how to do this also, and if you don't mind a little compiling and patching is a very viable solution too.  ndiswrapper also is a solution, but if you want to run your card in monitor mode it will not work.

---

### Post by Professor Bacon on 2009-02-17
> **Ketara said:**
> Have you gone through the steps in [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) ?

Also, which Atheros card are you using specifically?

Ndiswrapper will not work unless you have exactly the right driver, and having a driver that is almost correct but not exactly correct can produce weird results like what you're getting in my experience.

The card is an Atheros AR928x. I've checked that thread and followed the instructions, but it would seem that the good folks behind ndiswrapper have no information about that specific model.

I've tried madwifi before, but that didn't seem to work too well. I'll give it another try and see how it goes.

I'm in no hurry at any rate, this is a dual-booting machine :)

---

### Post by Ketara on 2009-02-17
Have you tried the backports fix?

Unfortunately we don't have the same Atheros chipset, so I can't just upload the driver I use for you.

Where exactly in the troubleshooting guide did you get to? Was it any help at all?

---

### Post by kevdog on 2009-02-17
Atheros AR928x


Interesting I think there is also an ath9k driver (very rare chipset).  I don't have a lot of experience with this driver, however do a search in google for ath9k

---

### Post by Ketara on 2009-02-17
When you enable backports it should give you two, ath5k and ath9k.

The big problem with trying to find a proper driver is that Atheros doesn't make it simple and easy. I got mine for the 5007 off of some Korean website or something.

---

### Post by Professor Bacon on 2009-02-18
After researching ath9k, I came across a wonderful package called compat-wireless that seems to have solved my problem :D Now if only this forum had a rep system so I could give you all a positive review.

---

### Post by kevdog on 2009-02-19
Link please!

---

### Post by Professor Bacon on 2009-02-19
> **kevdog said:**
> Link please!

Here's the link to the informational site:

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

And a direct link to the download:

For kernel 2.6.27 and above:
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

Kernel 2.6.26 and below:
[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)

---

