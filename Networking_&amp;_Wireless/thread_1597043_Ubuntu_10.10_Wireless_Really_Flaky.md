---
title: "Ubuntu 10.10 Wireless Really Flaky"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by Chief_runningwater on 2010-10-14
I have an Asus EeePC 1005HA and I remember there was a way to fix this problem in the older version of Ubuntu but since this is the latest how would I go about fixing this problem?

---

### Post by Chief_runningwater on 2010-10-16
Still looking for help.

---

### Post by ario on 2010-10-17
> **Chief_runningwater said:**
> Still looking for help.

What is your problem Exactly?!?

---

### Post by Chief_runningwater on 2010-10-17
> **ario said:**
> What is your problem Exactly?!?
The wireless in ubuntu 10.10 is really bad I can be one wall or even on the other side of the room and I will keep losing connection from my router.

---

### Post by rajadain on 2010-10-17
I had same problem in Ubuntu 10.04 LTS Lucid Desktop (on my laptop). The following fix worked:

Open terminal. Type in:

```
sudo gedit /etc/NetworkManage/nm-system-settings.conf
```

and change the value of [ifupdown] managed to true:

```
[ifupdown]
managed=true
#managed=false
```

And if that isn't good enough, try adding individual cases:

```
[ifup]
managed=true

[ifdown]
managed=true
```

Save. Reboot. Done. :)

---

### Post by Chief_runningwater on 2010-10-18
> **rajadain said:**
> I had same problem in Ubuntu 10.04 LTS Lucid Desktop (on my laptop). The following fix worked:

Open terminal. Type in:

```
sudo gedit /etc/NetworkManage/nm-system-settings.conf
```

and change the value of [ifupdown] managed to true:

```
[ifupdown]
managed=true
#managed=false
```

And if that isn't good enough, try adding individual cases:

```
[ifup]
managed=true

[ifdown]
managed=true
```

Save. Reboot. Done. :)
I did what you said but the minute i got into the file it's blank?

---

### Post by darth62969 on 2010-10-19
i have the same issue. have a dell 1440 with a intel wifi pci chip and am running the desktop edition of Ubuntu. i need a solution be for tomorrow at 7:00 am eastern i cannot download the update or find out the answer during school. it is urgent that this gets resolved asap.
did what it said it brought up a blank screen and copied and pasted the info and tryed to save it showed a error. 
please try to fix this over night 
thanks,
darth62969

---

### Post by darth62969 on 2010-10-20
fixed my issue. the wireless got turned off and i was to "it just updated so it must be the os" to press th Fn key along with the F2 key (mine is actualy setup so that the multimedia keys are before the F keys). maybe you do that or if the wireless is a switch turn it on maybe that would work? ](*,)

---

### Post by Chief_runningwater on 2010-10-20
Tried that didn't work am I hooped?

---

### Post by patthew on 2010-10-20
I think rajadain made a typo, the file is actually located in "NetworkManager," not "NetworkManage."


So to make these changes, fire up your terminal and enter

```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

At that point I did what rajadain suggested and changed the contents to the following:

```

[ifup]
managed=true

[ifdown]
managed=true

```


It's working so far for me. Fingers crossed!

---

### Post by Leejin on 2010-12-25
patthew!

I can confirm the positive effect of those changes. (Applied on Ubuntu Network Remix 10.10).

Best Thanks and a nice chrimas-time

Lee

---

