---
title: "Kubuntu 9.10 internet is slow"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by tmray on 2009-12-19
I just bought a limbo tower with kubuntu 9.10 from zareason.com [http://www.zareason.com/shop/product.php?productid=16211&cat=249&page=1](http://www.zareason.com/shop/product.php?productid=16211&cat=249&page=1) and everything on it runs great but the internet browsing, specificly anything streaming, like last.fm, mp3tunes.com seems really slow. So much so that it takes a couple of times of reloading it to get it to even work.

Any suggestions?

---

### Post by bqm3043 on 2009-12-19
The problem is a dns issue. Change the dhcp to address only, then type in the dns address. Reboot and the problem will be fixed.

---

### Post by tmray on 2009-12-20
That didn't seem to help. I even tried switching to google dns on my router but same results

---

### Post by tmray on 2009-12-27
Still having this problem. 
It takes a lot of time to resolve the host, then after about 10 seconds it does, then loads the page like normal. 
I have a ubuntu netbook running the easy peasy OS on the same router and have no problems. 
Is there a driver or setting for the eth connection I'm missing maybe?

---

### Post by dimoftheyard on 2009-12-28
This sounds like the IPv6 problem. Try turning that out in firefox. Enter about:config in the address bar, promise to be careful, and set network.dns.disableIPv6 to true.
If that makes firefox work normally you should turn it off system wide. When you google that issue you find a lot of solutions saying that you should blacklist some kernel modules, but that never worked for me. I had to add ipv6.disable=1 as a kernel option in /boot/grub/menu.lst

---

### Post by cozski on 2009-12-29
> **dimoftheyard said:**
> This sounds like the IPv6 problem. Try turning that out in firefox. Enter about:config in the address bar, promise to be careful, and set network.dns.disableIPv6 to true.
If that makes firefox work normally you should turn it off system wide. When you google that issue you find a lot of solutions saying that you should blacklist some kernel modules, but that never worked for me. I had to add ipv6.disable=1 as a kernel option in /boot/grub/menu.lst

Hey, I had the exact same problem and your suggestion appears to have worked for me. How do I turn it off system wide? And are there are consequences to it that I may need to be mindful of? Thanks.

---

### Post by tmray on 2009-12-29
> **dimoftheyard said:**
> This sounds like the IPv6 problem. Try turning that out in firefox. Enter about:config in the address bar, promise to be careful, and set network.dns.disableIPv6 to true.
If that makes firefox work normally you should turn it off system wide. When you google that issue you find a lot of solutions saying that you should blacklist some kernel modules, but that never worked for me. I had to add ipv6.disable=1 as a kernel option in /boot/grub/menu.lst

Thanks! That worked for firefox and I needed it to work for internet across the board and I found this and now my internet is almost too fast :)

```
Edit /etc/default/grub file

sudo kate /etc/default/grub

Change

GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”

to

GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash”

Save and exit the file

Update the grub from the command line

sudo update-grub
```

courtesy of this site
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html")

---

### Post by waster on 2010-01-29
i've been suffering with this for a while. dial-up speeds.
the ipv6 stuff does not solve it. Have got the kernel command line set, and for good measure removed firefox ipv6 lookups.

"dig" shows reasonably fast lookups, but the throughput with any network activity is terrible. Nothing hogging bandwidth according to iftop, and b43 4306 network signal is fine. I repeat, all network traffic is slow.

ping to various hosts over the internet is normal, but there is >50% packet loss.

This is all due to a new feature in karmic which is proving very unpleasant, and I've yet to find any more avenues to persue, apart from regressing to jaunty or switching distro.

---

