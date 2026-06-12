---
title: "Login Music... when I plug in my speakers?"
date: 2008-05-11
forum: Multimedia Software
---

### Post by dustingram on 2008-05-11
Hi all,

I've been having a bit of an issue with Hardy and my USB speakers. I've had the Logitech v20 speakers since Edgy, and while they've given me a fair share of trouble over the years, things have been working pretty well in 8.04 - except for one problem.

Whenever I plug these USB speakers in, they immediately play, at full volume, the default Ubuntu login music. This baffles me because not only do I have that login sound disabled (when it's *supposed* to play) but all other system sounds as well.

To be clear, this became an issue as soon as I upgraded to Hardy. I haven't the slightest idea where to start. Any help would be most appreciated.

Thanks!

---

### Post by peacewithall on 2008-05-12
As you have had no reply, I will offer some advice, I'm still new to Ubuntu so I would recommend the following to be done at your own risk (In other words, backup, although I'm sure it won't do any harm, and is easily reversible).

Pulseaudio plays the default sound (startup3.wav), at startup. So you could try commenting it then reboot, it should then be disabled.

Type in terminal,

```
sudo gedit /etc/pulse/default.pa
```

then comment the following line,

```
load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
```

So it looks like,


```
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
```

Save and reboot.

I hope this helps.

---

### Post by dustingram on 2008-05-12
Worked perfectly. Thank you!

---

