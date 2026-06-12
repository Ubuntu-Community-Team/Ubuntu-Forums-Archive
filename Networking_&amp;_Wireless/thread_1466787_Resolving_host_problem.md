---
title: "Resolving host problem"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by Tricast on 2010-04-30
I have a strange problem with wireless internet connection. We have 3 computers, 2 of them with Win 7 and 1 with Ubuntu 9.10 + Win XP.

Now if all three computers are connected to the internet through wireless router, the computer with Ubuntu 9.10 frequently fails to resolves hosts using various web browsers. I have to disconnect and reconnect to the router to get internet back but it only works for a maximum of 1 minute before it fails again. If the 2 computers with Win 7 logs out from wireless connection then the Ubuntu 9.10 machine works just fine for long periods.

If i boot with Win XP internet works perfect even when the other computers are connected but i really want to use Ubuntu 9.10.
The wireless chip is an Atheros 9285.

Any solution?

---

### Post by Iowan on 2010-04-30
Nothing changes (as far as DNS, route, etc) before/after or with/out Windows box(es) attached?

---

### Post by Tricast on 2010-04-30
Not that i know of. I have tried both with static and dynamic assigned IP. Any suggestions what i should look for and how to do it would be appreciated.

Thanks in advance!

---

### Post by deusdies on 2010-05-14
I have the identical problem. I would be downloading something and that continues to download, but when during the download I try to access a website, Chrome says "Resolving host..." and Firefox says "Looking up" for about 30 seconds - then the website loads.

Also, FileZilla says "resolving server"

---

### Post by stuzart on 2010-05-17
I have also started encountering this problem since upgrading to Lucid Lynx. 

Its the same as described above. I can be doing a download, or listening to streamed music fine, but contacting a website very often leads to a long wait to resolve the host. Often it fails entirely with an error.

I know this isn't a problem with my network since other Windows computers works fine, as does rebooting to Windows 7 on the PC I have problems with.

---

### Post by bedjo on 2010-09-28
Agree, my other older cpu (w/ Vista + firefox) is much faster for browsing than lucid lynx. I installed 2 browsers and got the same result. so, my guess, the problem is in the kernel.

oh btw, i did disable ipv6 on the system & firefox. It is still showing me "page load error" :(

so sad, I have been using ubuntu daily for 8 years now. Dont want to go back to my ex (windows)

---

