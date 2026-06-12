---
title: "Nvidia drivers go blah"
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by JNowka on 2006-11-08
I have used both method 1 and method 2 of tseliot's guide.  I followed each step closely.  Yet there is not problems section for what I am experiancing.  I have tried all the nvidia commands, and still get naught.  I installed 8776 using method 1 and it worked, till I rebooted.  Then I recieved a Version mismatch error.  It said that the X Driver and the GLX module had two differant versions.  So I wasted one day trying to figure out what was happening.  I had one guy tell me I should install the new drivers from the nvidia website.  So I went and downloaded those.  Followed the guide, and installed the driver from scratch.  Everything went through without a hitch, restarted gdm, and it worked ... till I rebooted.  Then I get the same error.  That the X Driver and the GLX module had two differant versions.  Thing is all 4 versions that were reported in the mismatch errors the entire time, were different.  Can any one help me out here?

---

### Post by tseliot on 2006-11-08
Try envy 0.7.1:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by daller on 2006-11-08
Just posting to get a message on replies! - Sorry! :)

I have problems even getting the nvidia-driver to work in edgy!

---

### Post by daller on 2006-11-08
tseliot>

I can't access the file:

```
daniel@dallap:~$ wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.1-0ubuntu2_all.deb
--22:17:05--  http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.1-0ubuntu2_all.deb
           => `envy_0.7.1-0ubuntu2_all.deb'
Resolving albertomilone.com... 68.178.232.90
Connecting to albertomilone.com|68.178.232.90|:80... connected.
HTTP request sent, awaiting response... 404 /ubuntu/nvidia/scripts/envy_0.7.1-0ubuntu2_all.deb
22:17:06 ERROR 404: /ubuntu/nvidia/scripts/envy_0.7.1-0ubuntu2_all.deb.

```

...and it doesn't work in konqueror either!

---

### Post by JNowka on 2006-11-08
After some messing, I just went through and uninstalled a bunch of stuff, and then installed the drivers via method 2.  Everything works fine now, even when I restart my computer.  Thanks.

---

