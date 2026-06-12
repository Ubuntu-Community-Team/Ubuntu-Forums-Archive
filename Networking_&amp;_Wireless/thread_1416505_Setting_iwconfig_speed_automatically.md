---
title: "Setting iwconfig speed automatically"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by OmahaVike on 2010-02-26
hello.  TIA for any and all assistance, guidance and blessings.

i've had problems with a laptops wireless card (using 8.04).  i can connect to my network but only at 1mpbs.  so, searching through the forums, i found a post that said to issue this command:

```
sudo iwconfig wlan1 rate 11M
```

and that seemed to solve my problem, temporarily.

now i'm growing tiresome of doing disabling wireless, issuing the command, and then bringing the wireless card back up.  is there a way i can do this automatically upon boot?  

i checked out my interfaces file, but it only has the loopback setting in there.  

i'm also not confident that creating a script to: 
```

iwconfig wlan1 down
sudo iwconfig wlan1 rate 11M
iwconfig wlan1 up

```
would work.

is there a config file somewhere that i can set the rate of the wireless card manually?

thanks a ton.

---

### Post by richdf on 2010-03-03
Hi OmahaVike,

The solutions I have found to be easiest to implement (& had to just dig-out following a router reconfiguration!) can be found here :

[http://ubuntuforums.org/showthread.php?t=816541](http://ubuntuforums.org/showthread.php?t=816541)

Despite my contradicting post on that thread, I prefer the option under last post, courtesy of cc_humbry ;)

Following that suggestion, my rc.local file simply looks like this:

...
[B]# By default this script does nothing.
iwconfig wlan1 rate 54M
exit 0[/B]

and this works for me! :D

Good luck.

---

### Post by OmahaVike on 2010-03-04
the thought never occurred to me.

worked like a charm.

thanks!

---

