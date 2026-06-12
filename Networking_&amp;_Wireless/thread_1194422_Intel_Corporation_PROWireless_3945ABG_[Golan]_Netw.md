---
title: "Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) stumped!"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by nothingspecial on 2009-06-22
I cannot get this stupid thing to work.

It worked in Gutsy and Hardy and for a bit in Intrepid. Then it broke. No problem, I just used my usb wireless thingy. I would like to use it for something else now.

I have found 2 solutions -

Use wicd - not working.

and 

wget [http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-3945-ucode-15.32.2.9.tgz)

add it to /lib/firmware

no go

I have tried blacklisting iwlcore and adding iwl3945 to /etc/modules without success.

Is there a fix for this?

Thanks.

---

### Post by nothingspecial on 2009-06-24
It will connect to the internet and I can browse for a bit but then it just stops working. Try to download anything and it will give up in seconds.

Both network manager and wicd think it`s still connected but I can`t ssh to it or ping from it.

---

### Post by nothingspecial on 2009-06-27
Bunp!

---

### Post by nothingspecial on 2009-07-03
Bump

---

### Post by nothingspecial on 2009-07-06
ouch

---

### Post by aaronLund on 2010-11-28
i've got it too.

10.4

worked great in hardy.

balls.

---

### Post by nothingspecial on 2010-11-28
works in 10.10

---

### Post by ndxtg on 2010-11-28
No there is disconnecting issues in 10.10
[http://ubuntuforums.org/showthread.php?t=1619428](http://ubuntuforums.org/showthread.php?t=1619428)

and thanks aaronLund for digging up a dead thread from > a year ago :@

---

