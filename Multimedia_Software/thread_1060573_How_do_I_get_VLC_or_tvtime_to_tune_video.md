---
title: "How do I get VLC or tvtime to tune video?"
date: 2009-02-04
forum: Multimedia Software
---

### Post by aprete on 2009-02-04
I have a Pinnacle PCTV HD Stick (801eSE) which I can use to watch TV using kaffeine.  I would like to set up VLC or tvtime to watch TV.  I'm having a couple of problems.

First:  Once I load the drivers ("cd v4l-dvb" followed by "sudo make load"), /dev/video0 comes into existence.  But I have to "sudo chmod 777 /dev/video0" before VLC or tvtime will recognize it.  Or, I can run tvtime under sudo (VLC won't run under sudo).  I shouldn't have to do this.

Second:  Once VLC or tvtime is able to access the device, all I get are a series of multicolored vertical bars moving from right to left.  Where do I put tuning information for either of these programs?  What is the format of the tuning information?  Some programs use ~/.xine/channels.conf; I don't remember where kaffeine gets the information.

Thanks.

---

