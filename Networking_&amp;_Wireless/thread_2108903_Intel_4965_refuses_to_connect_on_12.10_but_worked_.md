---
title: "Intel 4965 refuses to connect on 12.10 but worked just fine on 11.04"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by argie on 2013-01-25
Hello, everyone,

I've upgraded because of the endless prompts telling me that it was time to do so. Well, as a consequence of this, I've lost the ability to use Wifi on my laptop which has an Intel 4965 card in it. When I try to connect to an access point, nothing happens. 3 other devices next to the laptop can all connect (moving them away does nothing), and the Windows 8 installation works just fine as well.

I have tried the following:

* Disable n-mode: I can connect, but connectivity is intermittent with many dropped packets.

* Installed all updates: No luck.

Essentially, if I could've kept what I had earlier (11.04) everything would've been fine. Is it possible for me to run that kernel with Ubuntu 12.10. Ubuntu 11.04 has me connect to access points all over the world perfectly with not the slightest problem (even on 11n where it says I have 72 Mbps).

What do you recommend?

---

### Post by mikewhatever on 2013-01-25
Intel's 4965 pro driver for Linux has been badly broken for years. Consider yourself lucky it had worked so far. There are a few threads here, [one]("http://ubuntuforums.org/showthread.php?t=2020541") started by myself, but actually is very little help. The 2.38 kernel from 11.04 is unsupported as well as the release itself. It's possible to use it, but then, you might as well reinstall 11.04.

---

### Post by ahallubuntu on 2013-01-25
Have you tried 12.04 LTS?

Both 12.04 and 12.10 use a much newer kernel, the 3.x kernel (instead of 2.x used in 11.04 and earlier).  There were significant changes in some modules between the kernels and that fixed some things and broke others.  Still, it's worth trying 12.04.  As it will be supported until 2017 (unlike 12.10, supported only until 2014), I personally think 12.04 is a better choice anyway, if I have the option to use either one.

You could also look at this post and try the suggestion though it doesn't apply exactly to your problem, but it might fix problems with an Intel card:

[http://ubuntuforums.org/showthread.php?t=2108163](http://ubuntuforums.org/showthread.php?t=2108163)

---

### Post by ahallubuntu on 2013-01-25
Depending on the type of laptop, it might be fairly easy just to replace this Intel card with a newer one, the Intel WiFi Link 5100.  I have upgraded to this card with great success from 10.04 through 12.04 in several Dell and Acer laptops, which do not restrict which wireless cards you can use.  If you are using a Lenovo or HP laptop, though, you will be limited by whitelisting in the BIOS, so you can only install very specific wireless cards, otherwise the laptop won't even POST.

---

### Post by mikewhatever on 2013-01-25
> **ahallubuntu said:**
> Depending on the type of laptop, it might be fairly easy just to replace this Intel card with a newer one, the Intel WiFi Link 5100.  I have upgraded to this card with great success from 10.04 through 12.04 in several Dell and Acer laptops, which do not restrict which wireless cards you can use.  If you are using a Lenovo or HP laptop, though, you will be limited by whitelisting in the BIOS, so you can only install very specific wireless cards, otherwise the laptop won't even POST.

Hm..., and i thought, having seen quite a few questions [like this]("http://askubuntu.com/questions/66810/very-slow-connection-on-an-intelr-wifi-link-5100-agn"), that Intel WiFi Link 5100 AGN was even worse. 
Anyway, how would one know for sure about replacing the wireless card? Is there any way to check?

---

### Post by ahallubuntu on 2013-01-25
If you have a Dell using the 4965, I'd bet money the 5100 will work in place of it, just because I've upgraded a number of different model Dell laptops to that card.  You can be certain it will work if by chance the manufacturer itself sold your model laptop with that card as an option (if someone has say a Broadcom card but that same laptop was also sold with the 5100).

Otherwise, you'll just have to try it and see.  If you're lucky, you can probably get a used 5100 for under $10 USD on eBay as I've done a few times.  At worst you're out $10 if it doesn't work.  If you have a 4965 now, you need the FULL HEIGHT card (not the HALF height 5100).  Actually the half height version will work too, but you'll need an adapter to screw it in to the laptop.  Don't get a Lenovo/HP version of the 5100 if you don't have a Lenovo/HP laptop.

But as I said, Lenovo and HP laptops are special cases and wireless card upgrade options are severely limited, anyway.  Even if you get a Lenovo version of the 5100, it won't work in your Lenovo laptop unless the BIOS has that card approved in the whitelist.

As for me, having has such excellent luck with 5100 cards in several laptops and various versions of Ubuntu, I'll keep using them.  Almost the first thing I do if I inherit a laptop with a Broadcom wireless card is replace it with a 5100 (if possible), so I never have to deal with driver issues in the future.

---

### Post by steeldriver on 2013-01-25
I know it's only one data point, but the 4965 in my Thinkpad works OK under 12.04 with 11n_disable=1

---

