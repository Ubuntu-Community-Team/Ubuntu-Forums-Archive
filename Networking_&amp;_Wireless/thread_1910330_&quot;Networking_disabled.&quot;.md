---
title: "&quot;Networking disabled.&quot;"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by DigiTan on 2012-01-16
Ubuntu 10.04

I was minding my own business, looking at Open Office yesterday when I decided to suspend and Ubuntu apparently made the move permanent.  When I did a hard reset, I tried Firefox and was surprised to see that the networking icon and all its options were greyed out.  When I tried **ifconfig** and **iwconfig** my eth0 and wlan0 interfaces weren't even listed.

I googled what looked like a promising fix:

```
sudo gedit /etc/network/interfaces
```

add:
```
auto eth0
iface eth0 inet dhcp
```

```
sudo /etc/init.d/networking restart
```

This appeared to reset Network Manager, but the problem was 100% unaffected, even after a reboot.

1.  How do I restore my networking?
2.  This setup was problem-free all throughout 2011.  Why is Ubuntu suddenly tweeking and tinkering with vital settings without my authorization?

---

### Post by DigiTan on 2012-01-17
This is a real embarrassment.  Ifconfig, iwconfig, and lshw -C network don't even mention my wlan0 anymore and the only survivor seems to be the (lo) loopback.  The other OSes on this computer are still online.  It's like Ubuntu erased everything it knew about networking.

Key points:
1.  If a routine update has to interrupt a vital service (x.org, NetworkManager, ndiswrapper, acpi, printers, audio) the user should be advised so they can take precautionary measures.

2.  User settings should NOT just disappear.  God, there's nothing more grating than waking up with your settings defaulted, boot parameters gone, devices offline or unlisted, and your icons rearranged.  It's like going out to your car and finding it on cinder blocks.  It's like your sand castle got stepped on.  And the worse part?  You don't even know WHY they're gone!

3.  There should ALWAYS be an option to re-enable or reset networking.  Or something to point you in the right direction.  Desktops can't just Fn+F2 to get it back, and simply displaying "networking disabled" is just a check engine light for a bigger issue.  Give us something to work with!  

4.  That's the last time I try suspend mode.  More like suspense mode.
>:-D

---

### Post by DigiTan on 2012-01-18
I may have got it working.  I repeated the procedure in my first post and saw the changes I made weren't in there.  I also added in similar lines for wlan0.  When I reset the interface, the eth0 ethernet interface was able to reach the dhcp server and the ethernet works again.

Now both interfaces in the corner icon say "device not managed."  There are no wireless APs listed but at the ethernet works.  Not sure if that will be the case after a reboot.  So much valuable time lost on this today.

---

### Post by jetzhou on 2012-01-21
this fixed my problem.

[http://www.geekyard.com/os/linux-os/fix-network-manager-disabled-problem-in-ubuntu-10-04/](http://www.geekyard.com/os/linux-os/fix-network-manager-disabled-problem-in-ubuntu-10-04/)

and I agree, how this thing can just appear out of blue is completely stupid

---

