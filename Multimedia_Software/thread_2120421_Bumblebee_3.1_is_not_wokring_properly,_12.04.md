---
title: "Bumblebee 3.1 is not wokring properly, 12.04"
date: 2013-02-26
forum: Multimedia Software
---

### Post by zaebo on 2013-02-26
Hellou,

I read now a lot of threads concerning bumblebee, but unfortunately
nothing helped me so far.

The problem:

optirun -vv glxspheres causes
```

[ 3027.301326] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 3027.301899] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[ 3027.301936] [DEBUG]Socket closed.
[ 3027.301966] [ERROR]Could not connect to bumblebee daemon - is it running?

```.

What I did prior:

[LIST]
[*]installing nvidia-current from x-swat ppa
[*]installing linux-headers-generic
[*]installing bumblebee, bumblebee-nvidia, bbswitch
[/LIST]

One time, version 3.1 did work, when
[LIST=1]
[*]purge bbswitch
[*]reinstall nvidia-current
[*]install bbswitch
[/LIST]
I had to add me to the bumblebee group, which I never had to do
before, but it was working to the next reboot.

Before, bumblebee 3.0 was working on 12.10 and 12.04 perfect.

I'm thankful for any advice.

_Update:_
It is now working, when I start the bumblebee service manually.

```
sudo start bumblebeed
```

I played a lot around before I stumbled upon this solution posted
in the bumblebee-wiki. ([https://github.com/Bumblebee-Project/Bumblebee/issues/335]("https://github.com/Bumblebee-Project/Bumblebee/issues/335"))
But I mainly repeated all the steps I did before again, and again..
I really hate fans.

But now its working. Manually.

---

### Post by porzech on 2013-02-26
Hi zaebo,

the workaround from [here]("https://github.com/Bumblebee-Project/Bumblebee/issues/337") has helped in my case.

Regards,
Piotr

---

### Post by zaebo on 2013-02-27
Ah, thank you Piotr.

I will definitely try this.

---

