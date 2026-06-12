---
title: "howto?? soundcard broken - can`t boot"
date: 2005-11-26
forum: Multimedia &amp; Video
---

### Post by mboto on 2005-11-26
hi,

i have an old dell latitude laptop with a broken sound card.
i just installed kubuntu and now when i restart kubuntu always stops when it ries to start the hotplug subsystem.

with a knoppix cd i could solve this porblem by typing in the boot option:
linux noaudio,
linux nosound,
or 
linux nohotplug

is there a similar possibility with ubuntu??
maybe someway to tell grub not to start hotplug.

with a slackware distro and kde on that i could then solve it finally in the kde options where i could tell the system that there is no sound card.

any help would be great

regards

---

### Post by cvmostert on 2006-01-12
hi there, i also have a soundcard that makes my system halt... luckaly i could just take the card out... is there no way of not loading the modules for the card? 

hope you get it fixed.

---

### Post by FarEast on 2006-01-12
Hi,

I found a file 'blacklist' in /etc/hotplug .
On the top of it, the following is written:

# Listing a module here prevents the hotplug scripts from loading it.
# Usually that'd be so that some other driver will bind it instead,
# no matter which driver happens to get probed first.  Sometimes user
# mode tools can also control driver binding.

How about describing the module for the broken sound card?
If you are not sure which module it is, visit the web below.
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)

Regards;)

---

