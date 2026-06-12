---
title: "USB sound card advertised as Linux compatible doesn't plug and play..."
date: 2010-11-09
forum: Multimedia Software
---

### Post by aaronchall on 2010-11-09
Greetings!

I bought a USB sound card with two jacks, one for headphones and one for microphone. It was advertised as working with Linux without additional drivers, but when I plug it in with headphones, it doesn't work, instead sound keeps coming out of the laptop speakers.

I'm running 9.10, though I expect to upgrade to 10.10 soon. The reason I bought it is that the jacks built onto the motherboard of my laptop don't work. I contacted the seller, but haven't heard back from him. The device description is here: [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170389801700](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170389801700) , where it specifically states it works with Linux.

Thanks!

Aaron

---

### Post by RaumTrug on 2010-11-09
have you tried telling ubuntu to use it, system-preferences-sound, if it's a "good" card you should be able to choose there...

man, plug&play means "no need to load/install drivers", not that the system reads your mind on what soundcard you wish to currently use ;)

if it isn't in the list, open a terminal & show the people here what "lsusb" and "cat /proc/asound/cards" will spit out for a start...

---

### Post by aaronchall on 2010-11-10
> **RaumTrug said:**
> have you tried telling ubuntu to use it, system-preferences-sound, if it's a "good" card you should be able to choose there...

That got it!!! Thanks!!

Aaron

---

