---
title: "video trouble| nVidia geForce EN8500GT SILENT"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by bjb.butler on 2007-08-01
I recently purchased this card, and it has problems working under linux. 

When i install ubuntu feisty on this machine, it goes fine. when i restart, i get a black page with a lot of white text, but the screen is off to the side (almost off of the page) and i cant read anything. Is there something special i have to do to get this card working?

---

### Post by tseliot on 2007-08-02
If you're looking for a quick way to solve the problem you might want to try Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

**NOTE: Envy is a 3rd party application and you should use it at your risk**

If you decide to use Envy you will have to follow these steps:
Boot in Recovery mode
type:
```
wget  http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu4_all.deb
```
```
sudo dpkg -i envy*.deb
```
```
sudo apt-get install -f
```

then run envy by typing:
```
envy -t
```

And install the Nvidia driver from there.

Then let Enyv reboot

Boot as usual

---

### Post by markvan on 2007-08-15
Hi Bjb

Did this fix work for you please? I want to by this card, but not if it it does not work after the fix.

Thanks
mark

---

### Post by zeldor on 2007-09-09
I dont know about this particular fix but I had slapped this card into an
already configured machine with the latest 100.14.11 drivers from nvidia
(not ubuntu's version) and it works just fine.
however it does make Xorg suck up a boatload of cpu time now.
my old 7300gs card had very little load.
(running 720p HD mythtv setup)
Of course my old 7300 card had the same issue until the addition of
Options "UseEvents" "true"
to my xorg.conf file. Maybe this just hasnt made it into the latest drivers
for this card.
But in any event since the newer 8500gt card helps me very little
over the 7300gs card its going back.

---

