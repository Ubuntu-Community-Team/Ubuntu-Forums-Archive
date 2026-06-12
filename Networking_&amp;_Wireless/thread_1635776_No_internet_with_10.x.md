---
title: "No internet with 10.x"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by laidback on 2010-12-02
I installed a copy of 10.04LTS but am unable to access the internet (WWW). I can ping, i.e. Google.com, and any other address I want, but I get no response in Firefox, just timed out, with either DHCP or manual settings.

So I also tried 10.10, just the same.

Now this is very worrying as I've been using Ubuntu since V6.x and have always thought it to be wonderful. So what's going wrong?

Strangely I tried Mint v9, which I believe to be based on Ubuntu 10.04LTS, and that works with no problem.

I've even tried the Live CDs on another older pc (different NIC), with the same result, v10.x gives no internet but v9.04 Live CD goes straight on!

So I don't think it's the NIC as they differ between the 2 PCs. It's not my connection as my regular v9.04 is fine, as is PCLinuxOS 2010 and my wife's Windows pc etc.

I'm lost...any suggestions.

Many thanks

Laidback

---

### Post by wojox on 2010-12-02
>    1. Type about:config in the address bar, press Enter.
   2. Find network.dns.disableIPv6 in the list.
   3. Right-click -> Toggle.
   4. Restart Firefox and try again.


[Firefox Tutorials]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")

---

### Post by laidback on 2010-12-02
Oh you lovely person. 
Works for DHCP connections but not manual, not that I need a manual setting. Also works on the Live Cds that I have.

But why has this setting altered to give some users a problem? beats me.

Many thanks for your time.

Laidback

---

