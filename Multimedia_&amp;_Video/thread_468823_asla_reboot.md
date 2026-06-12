---
title: "asla reboot"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by tp21 on 2007-06-09
hi,
i am wondering if there is away to reboot asla. the reason is that i am having problems with sound after suspend/resume cycle, basically there is no sound coming when i play mp3 or doing any thing with sound.
i am running ubuntu 7.04 on IBM Thinkpad T21. 
thanks

---

### Post by Dirty Ole on 2007-06-09
Its alsa not asla.;)

Found this on the forums, don't know if it works. Not on a ubuntu comp right now.

In terminal 
```

sudo /etc/init.d/alsasound restart
```

If it doesn't work go to /etc/init.d and find scripts with alsa related names and restart them instead of alsasound.

---

### Post by tp21 on 2007-06-09
thanks a lot.
i found it, it is: /etc/apm/scripts.d/alsa
i am using apm not acpi, and this script can reload the modules which alsa needs. this is quite helpful for people like me who have troubles whith sounds after suspend/resume cycle.
to all tp21 users who suffer from the same problem, the answer is run the script after resume, so change the directory to /etc/apm/scripts.d and then type:
sudo ./alsa force-reload
and your sound is back.
hope that may help somebody
(ubuntu 7.04, thinkpad T21)

---

