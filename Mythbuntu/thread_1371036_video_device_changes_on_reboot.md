---
title: "video device changes on reboot"
date: 2010-01-02
forum: Mythbuntu
---

### Post by davidstoll on 2010-01-02
When I reboot, one of my USB recording devices (HDPVR 1212) changes from /dev/video0 to something else...1,2,3...whatever it wants to shuffle around with my other devices.

I know you can make a udev rule, but as far as I can tell, it only makes an alias...which I have done.  /dev/videoHDPVR

However, mythtv does not recocnise this.  It only looks for /dev/video#  and not any symbolic links.

How can I fix this device to video0?

Thanks!

---

### Post by azmyth on 2010-01-02
I believe you need to change the device in mythtv-setup so change it from say /dev/video0 to /dev/videoHDPVR.

---

### Post by davidstoll on 2010-01-03
I wish I could, but it only has /dev/video#'s available (0,1,2...) to select from, not aliases.  

However, I did go back in and manually typed it in...and it allowed me to.  It seems as though it will work.

Now I have a separate issue.  This video device is the default.  When I start live TV, flashes video for a second and then the frontend just quits.

I think it is not related to the topic issue because it seems like this happened as soon as I upgraded to 9.10 and the HDPVR 1212 became supported.

So, thank you azumuth, I think the topic has been solved.

Anybody else experiencing this crash?  (or should a new thread possibly be started?)

Here is some of my error log from my frontend...
[http://pastebin.com/f38881990](http://pastebin.com/f38881990)



> **azmyth said:**
> I believe you need to change the device in mythtv-setup so change it from say /dev/video0 to /dev/videoHDPVR.

---

