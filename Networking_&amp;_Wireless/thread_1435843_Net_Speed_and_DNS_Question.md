---
title: "Net Speed and DNS Question"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by Topher88 on 2010-03-22
I have a really n00by question about Internet speeds and DNS servers...

I am dual-booting Karmic and Windows 7, and for a while now I've noticed that my internet is typically faster in 7 than in Ubuntu.  This includes page load speeds and upload/download speeds.  Earlier today I decided to see if I could find a solution, and I found that manually defining OpenDNS' server instead of using the default server dramatically increased the speed, but that begs the question...  Since 7 still uses whatever the default is and the Internet runs just fine, doesn't that mean that whatever the problem was in Ubuntu initially hasn't actually been fixed?  Or am I misunderstanding something?

Also, I've already disabled IPv6 in about:config in Firefox, so that isn't part of the issue.

Thanks!

---

### Post by johngreth on 2010-03-22
> Also, I've already disabled IPv6 in about:config in Firefox, so that isn't part of the issue.
Disabling IPv6 only makes Jaunty faster. Jaunty automatically uses ipv6 and most ISP's don't support it, so it wastes time to try to use IPv6 when it cant be used in the end. This was fixed in Karmic, so it doesn't matter.

As for the internet problem, what is your ISP, and are you using 32 or 64 bit Ubuntu and 32 or 64 bit windows? How are you connecting to the internet and what security settings are you using? All these factors can cause the spped to be different in both operating systems. Although Ubuntu is usually faster, Windows may have better support for your hardware/configuration.

> I found that manually defining OpenDNS' server instead of using the default server dramatically increased the speed

If this is the case, switching the DNS should also improve your speed in Windows.

---

### Post by Linuxforall on 2010-03-31
Find the fastest dns servers in your area with namebench which can be found here at [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

Don't worry about ipv6 issue, that has been addressed with an update to Karmic a while back. Finding fastest dns servers will give you speed back to your net, if you want to make it even faster, check out how to install pdnsd from jonthysell's post here at [http://ubuntuforums.org/showthread.php?p=8954259&highlight=pdnsd#post8954259](http://ubuntuforums.org/showthread.php?p=8954259&highlight=pdnsd#post8954259)

---

