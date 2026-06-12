---
title: "Ubuntu 8.04 has a networking bug"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by nobbone on 2009-03-17
There are some webservers that are not accessible with Ubuntu 8.04.
For instance 
[http://www.barsch-alarm.de]("http://www.barsch-alarm.de")
This is not accessible with ANY Ubuntu 8.04 installation. It is also not a browser issue, because no browser works.
The above site is accessible with earlier versions of Ubuntu and also with later versions.
Only 8.04 does not work.

More information:
disabling IPv6 does not help.

---

### Post by coffeecat on 2009-03-17
> **nobbone said:**
> This is not accessible with ANY Ubuntu 8.04 installation

Not so. I'm posting from Ubuntu 8.04 installed as a VM in VirtualBox (MacOS host) and using Firefox, and that link displays just fine.

I'll try from my ordinary Ubuntu 8.04 later.

**Edit:** posting now from Ubuntu 8.04 installed normally on a standard PC. The link displays fine (in Firefox).

I presume you like fishing? :wink:

---

### Post by nobbone on 2009-03-17
That's strange. It does not work from two of my machines. They are both dualboot and can display the site when booting XP. But not when booting 8.04. They both have the exactly same hardware though.
I can see TCP Checksum errors when running Wireshark (I tried disabling TCP checksum offload locally, but no luck).
Also all my other boxes can display the page (one runs Ubuntu 5.04 and one runs Ubuntu 7.10).

Yes, I like fishing :) Very much so. With "F" not "Ph" :D

---

### Post by ugm6hr on 2009-03-17
Confirmed.

Works just fine on my Dell Mini 8.04.

No bug here.

---

### Post by coffeecat on 2009-03-17
> **nobbone said:**
> That's strange. It does not work from two of my machines. They are both dualboot and can display the site when booting XP. But not when booting 8.04.

<snip>

Also all my other boxes can display the page (one runs Ubuntu 5.04 and one runs Ubuntu 7.10).

Very odd. Have you tried running 8.04 live from the CD on the various machines and seeing if the page will display in live mode?

I don't know quite what that would achieve, but it might be interesting.

---

### Post by nobbone on 2009-03-17
> **coffeecat said:**
> Very odd. Have you tried running 8.04 live from the CD on the various machines and seeing if the page will display in live mode?

I don't know quite what that would achieve, but it might be interesting.

Good idea, I will try that. Maybe it is a combination of hardware   / software that causes the error.
It is very hard to track, because I only know 1 website that does not work, everything else is fine.
And I can ping and DiG the server just fine.
Strange thing is the Wireshark protocol:
[http://nobbone.de/images/ScreenshotWireshark.jpg](http://nobbone.de/images/ScreenshotWireshark.jpg)
I assume that the server really produces wrong TCP checksums, but only when talking to my box.
Some networkcards are known to have faulty TCP checksum offloading, maybe this hits me here.

---

