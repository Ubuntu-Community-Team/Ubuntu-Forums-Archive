---
title: "Upgrade to Gutsy: Lirc with serial receiver not working"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2007-11-30
HI folks,

I just upgraded to Gutsy last night.  I had lirc working on Feisty but have not been able to get things up and running at all with Gutsy.

As there is little help for serial receivers in the Gutsy community documentation, I've been working off of the Feisty page: 

[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

I believe I've done everything needed to get the serial receiver up and running.  The lirc daemon will run:
```
sudo /etc/init.d/lirc start
```

When when I try to test it out with IRW it doesn't see any key-presses.

Here is the output of: dmesg | grep lirc:
```
[   83.708488] lirc_dev: IR Remote Control driver registered, at major 61
[   84.016486] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[   84.519093] lirc_serial: auto-detected active high receiver
[   84.519099] lirc_dev: lirc_register_plugin: sample_rate: 0

```

any ideas where I'm going wrong?  Thanks!

---

### Post by barney_1 on 2007-11-30
Well, it appears I had nothing set wrong.  I failed to replace /etc/lirc/lircd.conf with the appropriate file containing my remote codes.  Now that I have it in place everything is working again.

---

