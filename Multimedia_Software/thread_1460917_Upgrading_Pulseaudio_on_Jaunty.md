---
title: "Upgrading Pulseaudio on Jaunty??"
date: 2010-04-23
forum: Multimedia Software
---

### Post by JamesSmith on 2010-04-23
Hi, can anyone help with this: I need to upgrade Pulseaudio to a version better than 0.9.14 (i.e. at least 0.9.15) in order to get the Pulseaudio plugin in Blueman to work, but despite following [these instructions]("http://www.webupd8.org/2009/05/how-to-install-latest-pulseaudio-0915.html") to add the PPA it will not be upgraded!

Thanks in advance! James

---

### Post by WinterRain on 2010-04-23
What is the error you get?

---

### Post by JamesSmith on 2010-04-23
No error at all, but when it reloads the sources it completes fine but pulseaudio 0.9.15 doesn't show up in Synaptic.  Its thinks that there are no upgrades available.

Is this PPA dead for Jaunty now do you think? Cheers :)

---

### Post by WinterRain on 2010-04-23
If it's any consolation, ubuntu 10.04 has pulse audio 0.9.22

You might want to try that when it comes out next week.

---

### Post by stefan73 on 2010-04-23
I activated the karmic-backports and then did a dist-upgrade. I now have version 0.9.22 on Karmic. I don't know if this is save, but it worked for me :-)

Been trying to find the howto I followed, but can't find it right now. Sorry.

---

### Post by JamesSmith on 2010-04-23
No worries.  I could solve it all by upgrading to Lucid when it's released, but in order to do that I will need to upgrade to Karmic first but I'm too afraid of things breaking on a system that I have set up how I want it!

I think there might be another way to get bluetooth audio working via Bluez without the need for pulseaudio but I need to read up on it first.

Ta

---

### Post by JamesSmith on 2010-04-23
According to this [thread]("http://ubuntuforums.org/showthread.php?t=1066212&page=8"), in April 2009, 0.9.15 is no longer available.  So is there a later version available for Jaunty somewhere.?

I don't know how to search for these things!

---

### Post by lidex on 2010-04-23
This do the trick?
[https://launchpad.net/~ulissesf/+archive/btwork]("https://launchpad.net/~ulissesf/+archive/btwork")

---

