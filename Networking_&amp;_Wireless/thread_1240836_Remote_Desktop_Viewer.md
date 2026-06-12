---
title: "Remote Desktop Viewer"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by andrew.co.za on 2009-08-15
What do i need to do to get Remote Desktop Viewer to a usable state. I can connect to the other PC but the desktop takes 10 minutes to display completely. The mouse cursor only refreshes every 2 seconds and the desktop never refreshes but things are happening on the other side.

Why is it not refreshing? Surely Canonical wouldn't package something that is, quite frankly, useless? So what am i doing wrong?

---

### Post by wojox on 2009-08-15
Open  a terminal:

```
vinagre --help-all
```

Looks like a sync problem.

---

### Post by andrew.co.za on 2009-08-15
```
vinagre --sync
```

That just brings the Remote Desktop Viewer window into focus. Still non existant refresh rate though.

---

### Post by andrew.co.za on 2009-08-15
Clearly i'm not the only one with this problem:
[https://answers.launchpad.net/ubuntu/+source/vinagre/+question/74861](https://answers.launchpad.net/ubuntu/+source/vinagre/+question/74861)

Seems like i acctually have two problems though, 1) not refreshing, 2) very slow connection. I'm using wireless lan that seems to be working fine so i can't understand why it would be so slow.

---

### Post by superprash2003 on 2009-08-15
try disabling desktop effects by going to system->preferences->appearance->visual effects

---

### Post by andrew.co.za on 2009-08-29
I had given up on this but i would really like to get remote desktop viewer working. Disabling visual effects worked to a degree, it's now useable but still very slow. Is there a way to lower the quality that's being sent? I really just need to be able to control the other PC it doesn't need to look good. As i said it is useable but can be very tedious.

---

### Post by andrew.co.za on 2009-08-29
it seems like this is an official bug; [https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/203782](https://bugs.launchpad.net/ubuntu/+source/vinagre/+bug/203782)

---

### Post by mavila on 2009-09-12
Just noticed the same behavior after upgrading the TARGET machine from 8.10 to 9.04.

It worked fine (the source machine is 9.04) before the upgrade.... now I actually have to walk to the other room to assist my wife with any issues. Anyway, just started looking for a solution.

---

### Post by v_2ryann on 2010-07-30
> **mavila said:**
> Just noticed the same behavior after upgrading the TARGET machine from 8.10 to 9.04.

It worked fine (the source machine is 9.04) before the upgrade.... now I actually have to walk to the other room to assist my wife with any issues. Anyway, just started looking for a solution.

Here is the answer guys, on how to do it without changing the effects:

1) Open a terminal o press ALT+F2, then run/type: gconf-editor
2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I found it found here:
[http://swiss.ubuntuforums.org/showthread.php?t=1496368](http://swiss.ubuntuforums.org/showthread.php?t=1496368)

---

### Post by digitaltruth on 2012-02-29
I have noticed this is an issue while using the fglrx (ATI proprietary drivers). To get around this if you run the ATI Catalyst admin control program and enable the "tear free" option it resolved the issue for me immediately.

---

### Post by subdigit on 2012-10-19
> **digitaltruth said:**
> I have noticed this is an issue while using the fglrx (ATI proprietary drivers). To get around this if you run the ATI Catalyst admin control program and enable the "tear free" option it resolved the issue for me immediately.

excellent!  This worked for me in Ubuntu 12.10 on an ATI card.  I never saw the disable_xdamage variable listed so it wasn't an option for me.

Thanks!

---

### Post by ggallozz on 2012-10-28
After googling around for few (!) days, I've also followed the v_2ryann path, and found that in **GconfEditor**, in
 **/desktop/gnome/remote_access/**

that damn parameters must be hand-set:
 /desktop/gnome/remote_access/alternative_port (ie)  -> 5901 (just in case ...)
 /desktop/gnome/remote_access/authentication_methods  -> [vnc]
 /desktop/gnome/remote_access/enabled  -> [checked]/usr/lib/vino/vino-server
 /desktop/gnome/remote_access/network_interface  -> [**empty** !!!]
 /desktop/gnome/remote_access/vnc_password   ->  keyring

Set other options at your taste.

In any case, to get it still working, have to run 
 # /usr/lib/vino/vino-server
manually .... ?!
 :-(

---

