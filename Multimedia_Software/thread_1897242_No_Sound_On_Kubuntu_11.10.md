---
title: "No Sound On Kubuntu 11.10"
date: 2011-12-18
forum: Multimedia Software
---

### Post by Maleificus on 2011-12-18
I tried to start playing media on my system after doing a restart and I have no sound coming from my external speakers. Everything is plugged in properly and I have checked all the volume levels. The only thing that changed on the system was I tried to install the ATI proprietary driver and it slowed down my system so I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx) Then I restarted. That is when the problem occurred.

---

### Post by inobe on 2011-12-18
go to system settings> multimedia> phonon.

what device is listed?

also include if your system has an hdmi connection.

does your system speakers connect with a pin jack?

---

### Post by Maleificus on 2011-12-18
VT1720/24 [Envy24PT/HT] is the device listed, there is also one under it that I disabled when I first installed Kubuntu about a week ago and that one is HDMI but like I said it is disabled and not the one that I have set up to be preferred.

---

### Post by inobe on 2011-12-18
if the profile for hdmi is off, you should have sound, to verify this get pavucontrol from package manager and run it, select your device there.

make sure nothing is muted, run alsamixer in terminal.

the best i have.

i'm ignoring the fact that what you've done may have broken the sound, and attempting to get around the technical stuff.

---

### Post by Maleificus on 2011-12-18
The System Sounds level was turned all the way down, i turned it up, sound works now. Thank you!

---

### Post by inobe on 2011-12-18
your welcome.

---

