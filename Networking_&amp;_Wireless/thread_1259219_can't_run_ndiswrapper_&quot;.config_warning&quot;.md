---
title: "can't run ndiswrapper &quot;.config warning&quot;"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by Keatoru on 2009-09-06
I followed a guide on here to install ndiswrapper and the drivers for the WPN111 wireless usb.
```
http://ubuntuforums.org/showthread.php?t=652910
```

When I did first followed the guide everything went perfect, everything installed correctly and everything ran correctly. Only part that didn't go right was the very end when it told me to, so that ndiswrapper started on boot, run
```
nano /etc/modules
```

and then add ndiswrapper to the end of the list. I ran the command and it opened the list, I went to the end and typed 'ndiswrapper' (w/o '' ofcourse). After that though, since I have very little clue to what to do in terminal I couldn't figure out how to save it. I pushed ctrl+x to close then y to accept changes but then I didn't know what to do from there so I just closed it all and hoped for the best.

Since everything ran fine I connected to the updates and installed the many updates that I needed (it's a clean install so it needed a ton) after the updates i reset the computer so they would take effect and when it turned back on wpn0 wasn't on. I couldn't figure out why as in the manage connections I could go to the wireless tab and mess with the connection but it would never connect. So it came back to me not adding ndiswrapper to that list and I looked for a way to turn ndiswrapper on. I assumed this command turns it on:
```
sudo modprobe ndiswrapper
```

but when I ran this command I got back a warning. It said something along the lines of "*WARNING* All config files must have .config this will be ignored in future updates"

so I'm assuming from that, that ndiswrapper won't run because in etc/modprobe.d it is just ndiswrapper and not ndiswrapper.conf and since that is in root i guess I can't add .conf to it.


I know that was a lot to read but I wanted to cover all bases for my question. The question being, How can I get this to work again?

---

### Post by adamlen on 2009-09-06
I read in another post that someone else had that message as well(I got it too.) and the staff member that helped him disregarded it and stated that all went well. It looks like that may just be "one of those things".

---

### Post by chili555 on 2009-09-06
The warning is, indeed, mostly harmless. You can fix it with:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```I also suggest checking to see if your change to /etc/modules stuck (I doubt it did) with:```
cat /etc/modules
```If you do not see 'ndiswrapper' listed, then your change did not take. You might then do:```
sudo kate /etc/modules
```kate is an easier text editor that clearly has a 'Save' button. Add ndiswrapper on its own line, proofread, save and close.

Let us know how you make out.

---

### Post by uylug on 2009-09-06
> **chili555 said:**
> You might then do:```
sudo kate /etc/modules
```kate is an easier text editor that clearly has a 'Save' button. Add ndiswrapper on its own line, proofread, save and close.
Most Ubuntu users don't have Kate installed.

You can also use Gedit:


```
sudo gedit /etc/modules
```

---

### Post by Keatoru on 2009-09-06
my change to /etc/modules didn't work

I tried gedit
```
sudo gedit /etc/modules
```
but it said command not found, i guess because I'm using kubuntu?

In any case though, I finally figured out how to save in nano and then after restarting my computer it worked properly.

thanks for helping everyone

---

