---
title: "No sound after Hibernate"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by lijiang on 2006-09-01
I've installed Ubuntu 6.06 dapper on my Desktop PC smoothly. But since the last time I hibernated ubuntu, and the resume fall,  my headphone dosen't make any sound at all. I've tried every option of the volume controller, but nothing changed. What should I do?

---

### Post by cholly on 2006-09-01
Similar problem here.

--3715-EH1 Averatec Laptop
--Dapper LTS install near a week ago with out any problems until yesterday.
--2.6.15-26-k7 kernel image installed today as an recommeneded attempt from some bugzilla google hit.
EDIT:
--lspci
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50) : device shows up in all sound control panels etc in gnome as if it were working.

EDIT: 
It turned out not to be 'buzilla' but this was the hit: [https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/25896](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/25896)

--Important note: 
I tend NOT to use hibernate, just becuse I don't know how long I will have the laptop in the bag. So I am near 100% sure my issue with this is not because of hibernate.

--Also occured with 5.10
--Details
I have had Dapper installed for near a week before this and it was working through restarts. When I had Breezy installed the machine was a dual-boot with wondows and I would just reboot into windows and log out and it would 'fix' the sound card with an audible "pop" and when I rebooted ubuntu it would work fine for a while then a shutdown/boot would break it again. Somtimes it seems like a restart would break it.

---

### Post by lijiang on 2006-09-02
My computer is still silent :( . I find some tricks in this forum but seems they didn't take effect.  I guess I have to wait for another release, hopefully when it will make a change if  I update the ubuntu. :biggrin:

---

### Post by sebastfr on 2006-09-02
hello

Have you tried this command after returning from hibernation:

~> sudo /etc/init.d/alsa-utils restart

I need to do this to have the sound working again after hibernating.

Seb

---

### Post by lijiang on 2006-09-04
Hehe, thanks for your suggestion, I've tried it before but didn't worked. After all, I've solved the problem, :mrgreen: :mrgreen: :mrgreen: , I followed the  "Comprehensive Sound Problem Solutions Guide v0.5e" in the sticky threads step by step and finally get the sound out. 
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
so it should be a good habit to have a look at the sticky threads always, each of them are really great of help, thanks for all those editors

---

### Post by apiper on 2006-09-11
I just ran into the same "no sound after hibernating" problem. I eventually discovered that there were 2 "esd" processes running for some reason, so I ran the following commands and voila! Working sound again!
```
killall -9 esd
/etc/init.d/alsa-utils restart
```
Of course, I now have *no* esd processes running, but at least I have sound for the time being ;)

---

