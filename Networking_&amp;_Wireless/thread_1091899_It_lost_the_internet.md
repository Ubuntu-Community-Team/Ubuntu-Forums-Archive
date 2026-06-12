---
title: "It lost the internet?"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by ChaosMuffins on 2009-03-09
This is a bit of a doozy, because I'm not sure what I did. I was trying to get my friend's Laptop (Acer AspireOne ZG5) to read its wireless internt card. I followed the little Wireless guide I found for it, did everything correctly in terminal, and it worked at first...then I ran an update on the system.

I'm on 8.10 (Ibex), and the computer is Dual-Boot with XP. on Windows, it reads both Wireless and Wired fine. On Linux...it reads *neither*. This makes me feel so dumb for asking, especially with the vagueness of my explanation, but any help would be appreciated.

NOTE: The update was just a big standard one; the internet connections worked right -after- I'd installed Ubuntu. Getting the wireless working was the first thing I did, and it was before I got the new system updates for it.

---

### Post by Iowan on 2009-03-10
I don't have 8.10 (probably get it after Jaunty comes out...), so I'm kinda working blind.  Network Manager stores it's settings in /etc/NetworkManager - */etc/NetworkManager/nm-system-settings.conf* in particular.  You can also check results of **lshw -C network** to see if both/either interface(s) has an alias (eth0).

---

### Post by ChaosMuffins on 2009-03-10
I may just reinstall the system, if worse comes to worse. It's a fresh Laptop with nothing on it, so I won't lose anything.

I'm running Hardy on my desktop, and it's hooked up to wired internet with no problems; does it do wireless with a little work? I know how to config wireless for Intrepid because I HAD it working before it failed royally...

---

### Post by younglemon on 2011-11-09
I don't know if I can expect a reply to this old thread or not. I have had my Ubuntu server running for more than a year and everything has worked fine. A few days ago I attempted to cancel an install operation while simultaneously attempting to adjust the keyboard position. I dropped it and in my attempts to catch it I pressed almost all the keys on the keyboard. Since that time I have not had an internet connection. I can ping other machines on the network and other machines can print, but I cannot reach the internet from the server. I do not have any available connetions from within the network connections list. I created one (both manual and DHCP) but it doesn't use them. I don't think that is what I need to do anyway though, as i didn't have to set any parameters to my wired connection previously. I think I may have somehow turned off the NIC port, is that possible? If so, how can I check and/or turn it back on again? I am on Ubuntu 11.10 Server 64. I don't know what I've done or what I'm missing. Thank you in advance for any input regarding this matter - kind regards to all.

---

