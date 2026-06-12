---
title: "Help with intermittent Xorg / openbox startup problem"
date: 2017-08-01
forum: Multimedia Software
---

### Post by johnnycee on 2017-08-01
I am using Ubuntu Server 16.04.2 LTS for an information kiosk application. The device is an Asus VivoMini UN65H. I am a long-time dev but I have relatively little Linux experience. I followed some cookbook methods found on StackOverflow and blogs to get the software I need installed and customized, and now my kiosk app boots into Chrome on startup and life is good, except...

There is an intermittent problem where X doesn't start. I see a message: **Unable to connect to X server: Connection refused**. When I look in the Xorg log, the main problem appears to be this:

```

[     4.409] (EE) Screen(s) found, but none have a usable configuration.
[     4.409] (EE) 
Fatal server error:
[     4.409] (EE) no screens found(EE)
```

However, if I restart, things will usually start fine. Because the problem is intermittent, I suspect there is some timing problem. I've done some googling, but I have not found anything that helps.

When I review the log after X starts normally, I see this:

```
[     4.433] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.451] (**) modeset(0): claimed PCI slot 0@0:2:0
[     4.451] (II) modeset(0): using default device
```

However, when X does not start, the messages that follow the "kms" messages are:

```
[     4.391] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     4.409] (WW) Falling back to old probe method for modesetting
[     4.409] (II) modeset(2): using default device
[     4.409] (II) modeset(2): using default device
[     4.409] (EE) Screen 0 deleted because of no matching config section.
```

I don't know if those log message differences are significant or not.

I can supply the full logs for the error case and the success case. If there is something else I can supply, or something else for me to investigate, please let me know!

---

