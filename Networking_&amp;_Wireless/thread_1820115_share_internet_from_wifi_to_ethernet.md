---
title: "share internet from wifi to ethernet"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by mafi127 on 2011-08-07
Hello, I tryed to get network work like this share internet from wifi (wlan0) to ethernet (eth0). So the internet connection comes from the wifi and we share to other computer via ethernet.

I used this tutorial [http://www.isnull.com.ar/2011/05/share-internet-with-ubuntu-1104.html](http://www.isnull.com.ar/2011/05/share-internet-with-ubuntu-1104.html)

But when I restarted my pc then it dont work and network says "wired network device not managed" How can I get it work aigan ?:confused:

-EDIT-
Got it working thanks to zanginator [http://ubuntuforums.org/showpost.php?p=10741873&postcount=9](http://ubuntuforums.org/showpost.php?p=10741873&postcount=9)

Now I have anohter problem when I connect autoeth then the wireless network dosent work anymore, I have to disconnect eth0 to have wirelles network working. how can I manage to get the bowh to work?

---

### Post by mafi127 on 2011-08-07
Now when I connect ifupdown(eth0) then my wireless network dosent work and when I ping whit another computer witch I want to have internet connection it says this error

[PHP]C:\Documents and Settings\Server-Telekas>ping www.google.com

Pinging www.l.google.com [209.85.149.105] with 32 bytes of data:

Reply from 10.0.0.1: Destination host unreachable.
Reply from 10.0.0.1: Destination host unreachable.
Reply from 10.0.0.1: Destination host unreachable.
Reply from 10.0.0.1: Destination host unreachable.

Ping statistics for 209.85.149.105:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms[/PHP]

I allso tryed whit my other wireles usb card but this as the same problem, it will say that it is connected to wireless network, but I cant surf in internet. How can I get things work aigan

---

### Post by solitaire on 2011-08-11
> **mafi127 said:**
> Now when I connect ifupdown(eth0) then my wireless network dosent work and when I ping whit another computer witch I want to have internet connection it says this error

[PHP]C:\Documents and Settings\Server-Telekas>ping www.google.com

Pinging www.l.google.com [209.85.149.105] with 32 bytes of data:

Reply from 10.0.0.1: Destination host unreachable.
Reply from 10.0.0.1: Destination host unreachable.
Reply from 10.0.0.1: Destination host unreachable.
Reply from 10.0.0.1: Destination host unreachable.

Ping statistics for 209.85.149.105:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms[/PHP]I allso tryed whit my other wireles usb card but this as the same problem, it will say that it is connected to wireless network, but I cant surf in internet. How can I get things work aigan

I'm having the same problem
It's because the ifupdown(eth0) is set as default connection so it will override the Wireless.

(This is a MAJOR sticking point with ICS, In Windows it's very easy it's a couple of tick boxes! but in Ubuntu and other *nix's it's a major annoying painful loosing battle at the best of times!)

---

