---
title: "I have to type &quot;sudo modprobe ath5k&quot; everytime I want to use my wireless card"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by ucof on 2010-01-07
Hi everyone,

I upgraded to 9.10 on the day it was released, and since then, my wireless has given me nothing but problems on my laptop (been having to use Windows just for wireless).

I have finally managed to get it to the stage where I can at least use and connect via wireless by typing "sudo modprobe ath5k".

How can I get it to use this by default everytime Ubuntu loads up please?

I'm a Linux noob, but this seems like an easy fix to me.... I just don't know how to do it! 

Thanks in advance.

---

### Post by ucof on 2010-01-08
Not entirely sure what I did, but all is working now.
I followed these instructions, [http://www.ubuntugeek.com/how-to-get-ath5k-working-on-jaunty-with-compat-wireless-and-a-self-compiled-kernel.html:](http://www.ubuntugeek.com/how-to-get-ath5k-working-on-jaunty-with-compat-wireless-and-a-self-compiled-kernel.html:)

>  Sir Eliah says:
August 8, 2009 at 11:52 am

It works for Presario f755us with the same ethernet device. I compiled kernel 2.6.30.4 and installed that compat-wireless and it seems to be ok.

There were only two problems: 1) it was necessary to type &#8220;sudo modprobe ath5k&#8221; every time after reboot, but I solved it by adding &#8220;ath5k&#8221; in file &#8220;/etc/modules&#8221;.
2) network-manager-gnome were a bit irritating constantly asking for a key to the key database or something, solved it by installing wicd. :D

Now wireless works excellent, thx for tutorial!

...but they didn't seem to work - only after the 2nd reboot of the laptop did I notice that the wireless was connecting again.


Just hope this helps anyone who has a similar problem.

---

