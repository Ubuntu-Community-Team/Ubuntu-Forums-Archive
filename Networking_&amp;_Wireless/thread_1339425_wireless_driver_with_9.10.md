---
title: "wireless driver with 9.10"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by wildbluefaerie on 2009-11-27
I've just gotten a new laptop and upgraded to 9.10 at the same time. I've noticed many other people have had trouble with the wireless drivers in 9.10 as well, but I can't find anyone with this particular problem. It took me a while to get the correct driver installed and the wireless working (wireless card Broadcom BCM4312), but I managed it eventually at the wireless worked fine. The problem is that it disappears every time I reboot the system, and I have to reinstall the driver every time. Is there anyway to fix this?

The was thinking of just writing a start-up script that will handle the reinstallation for me, but the problem is the script needs root privileges. Is there any way to somehow include the password in the script or something like that? If I just put "sudo su" in the script, first is asks for a password, but then it just sits there with a root prompt, which is not helpful. Of course, if I could fix it permanently without having to write a script like this, that would be better...

Installation script:
```
rmmod b43
rmmod ssb
make clean
make
modprobe lib80211
insmod wl.ko
```

---

### Post by bkratz on 2009-11-27
You might want to look through this thread, it seems pretty complete.

[http://ubuntuforums.org/showthread.php?t=1266620&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=1266620&highlight=BCM4312)

---

### Post by wildbluefaerie on 2009-11-27
Hmm.... well, I just tried the instructions listed in that thread, and now I can't get the wireless to work at all. iwconfig still doesn't list the wireless driver. I even tried uninstalling those packages again, and it still doesn't work, even the way I was doing it before... please help??

---

### Post by bkratz on 2009-11-27
> **wildbluefaerie said:**
> Hmm.... well, I just tried the instructions listed in that thread, and now I can't get the wireless to work at all. iwconfig still doesn't list the wireless driver. I even tried uninstalling those packages again, and it still doesn't work, even the way I was doing it before... please help??

That still is a very active thread, perhaps if you post there I bet someone that really knows the card would be helpful.

---

### Post by wildbluefaerie on 2009-11-27
ok, I'll try that, thanks.

---

### Post by ublintu on 2009-11-27
After a clean install, I followed this guide: [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
and it`s working for me normally. Did you try this?

---

### Post by wildbluefaerie on 2009-11-27
It's working now, actually - I haven't a clue why, but it is, and in all my years of dealing with computers, I've learned not to question it when things suddenly and inexplicably work.

---

### Post by bkratz on 2009-11-27
> **wildbluefaerie said:**
> It's working now, actually - I haven't a clue why, but it is, and in all my years of dealing with computers, I've learned not to question it when things suddenly and inexplicably work.



You probably should use the thread tools at the top and mark it [solved], did you perhaps restart after the last attempt?

---

### Post by wildbluefaerie on 2009-11-27
Sorry, didn't realize I could mark it as solved. I have now.

Yes, it was after a reboot, but I'd already rebooted several times before after many different configurations. I booted into Windows to post, and when I rebooted into Ubuntu to try something different, it was working. I must have changed something before that reboot, but I don't know what.

---

