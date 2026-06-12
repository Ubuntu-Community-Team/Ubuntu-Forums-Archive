---
title: "Laptop Volume media keys stay pressed"
date: 2015-06-16
forum: Multimedia Software
---

### Post by Nahuel_ on 2015-06-16
[COLOR=#111111][FONT=Ubuntu]This is a problem I've had before on an old HP laptop. Now I have a Lenovo Z470. These are the keys I mean: 

[/FONT][/COLOR][http://i.stack.imgur.com/hJJJI.jpg](http://i.stack.imgur.com/hJJJI.jpg)
[COLOR=#111111][FONT=Ubuntu]
They seem to be capacitive buttons. When I press volume down for example, the volume goes all the way down and it keeps trying to go down (as if I'd kept pressing the key). Same thing happens for volume up and mute. I press ESC and it stops.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This does not happen if I use FN+DOWN (volume down) for example. So I'm guessing it's driver issues.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I found this, but it's really old and I've tried finding the code he's referring to but I couldn't: [http://ubuntuforums.org/showthread.php?t=974723](http://ubuntuforums.org/showthread.php?t=974723)[/FONT][/COLOR]

---

### Post by sandyd on 2015-06-16
Symptoms are similar to [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1245189](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1245189)

You may want to file another bug.

---

### Post by Nahuel_ on 2015-06-16
Thank you!

I opened /lib/udev/hwdb.d/60-keyboard.hwdb and the patch they mention was there, so it's been added. 

I added these lines below the ones for Z370 hoping it would work, but no :P (I just changed Z370 for Z470)

```
keyboard:dmi:bvn*:bvr*:svnLENOVO*:pn*IdeaPad*Z470*:pvr*
 KEYBOARD_KEY_a0=!mute
 KEYBOARD_KEY_ae=!volumedown
 KEYBOARD_KEY_b0=!volumeup

```

What's the right way of doing it?

Also, how would I file a bug? I never did that.

---

### Post by Nahuel_ on 2015-06-16
Well, apparently I had to run:

```
sudo udevadm hwdb --update
```

Now it works. How would I file a bug report? Thanks!

---

