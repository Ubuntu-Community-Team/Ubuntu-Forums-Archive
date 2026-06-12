---
title: "MediaTomb - cannot login on web interface - it seems wrong credentials"
date: 2017-06-25
forum: Multimedia Software
---

### Post by rrozman on 2017-06-25
Hi,

I've installed MediaTomb and enabled web interface. I'm allowed to connect, but it asks me first for username and password.
And whatever I enter (nothing or credentials set in config.xml) and press Login button - nothing happens...

I've checked twice all credentials, also tried with no user and no success.

I must be doing something wrong- but what ?

Thanks in advance,
regards,
Bulek.

---

### Post by deadflowr on 2017-06-25
From here:
[https://help.ubuntu.com/community/MediaTomb]("https://help.ubuntu.com/community/MediaTomb")
check and see if 
```
<accounts enabled="no" session-timeout="30">
```
is set to no then make it is set to yes.
But maybe you did that already...

---

### Post by rrozman on 2017-06-26
> **deadflowr said:**
> From here:
[https://help.ubuntu.com/community/MediaTomb]("https://help.ubuntu.com/community/MediaTomb")
check and see if 
```
<accounts enabled="no" session-timeout="30">
```
is set to no then make it is set to yes.
But maybe you did that already...

Thanks for suggestion, but did try it... 
It seems that MediaTomb is not running properly and it doesn't have any proper message to tell this...

Not sure what to check....

Regards,

---

### Post by deadflowr on 2017-06-26
Ubuntu 16.04? (or newer)
If so, perhaps it needs to restart using the systemd controls
look at what
```
systemctl status mediatomb
```
tell you.
you can restart with
```
sudo systemctl restart mediatomb
```
Unless, of course, you're running it non-service mode (manually)

But I'm just throwing things out there.

---

