---
title: "PPPOE not working in Ubuntu 11.10"
date: 2011-12-10
forum: Networking &amp; Wireless
---

### Post by debarshi.nayak on 2011-12-10
Hello,

I am using Ubuntu 10.10 for a long time and I didn't have any problem connecting to the Internet through DSL (PPPoE) connection :D.

But recently, after I upgraded my Ubuntu to 11.10 version, I found that I am unable to connect to the internet (I still have the same ISP, and it is working fine on my XP system)

I followed the same process to create a new connection, but still nothing. It isn't helping:(.

So if anyone here is experiencing the same problem, or has a solution to the problem, I will be glad to have a response

Thanks

---

### Post by debarshi.nayak on 2011-12-11
Am i the only one with this problem? please, can someone help me on it?

---

### Post by dineshs on 2011-12-12
> I followed the same process to create a new connection, but still nothing. It isn't helping
Did you try [this]("http://ubuntuforums.org/showpost.php?p=9611335&postcount=9") ?
Can you post the result of ```
sudo lshw -C network
```
What result do you get for the command ```
ipconfig /all
``` in [COLOR="Red"]WINDOWS[/COLOR] when connection is working

---

### Post by debarshi.nayak on 2011-12-13
Yes, I did the same process as shown in the two pics above.

And in windows, That command is giving me really long list of responses. Aroung 6 to 7 images if i print screen whole screen of mine

How do I show that to you?

---

### Post by dineshs on 2011-12-13
Is it a wired connection or wireless?
> And in windows, That command is giving me really long list of responses. Aroung 6 to 7 images if i print screen whole screen of minePlease post the result of *sudo lshw -C network* in ubuntu

---

### Post by debarshi.nayak on 2011-12-17
It is a wired connection

---

### Post by RISHIKESHGAWADE on 2011-12-21
> **debarshi.nayak said:**
> It is a wired connection

I am also facing the same problem with BSNL broadband.
I tried sudo pppoeconf and pon dsl-provider
it says error: only members of 'dip' group can use this command

then i tried sudo adduser XXXX dip
still no success

---

