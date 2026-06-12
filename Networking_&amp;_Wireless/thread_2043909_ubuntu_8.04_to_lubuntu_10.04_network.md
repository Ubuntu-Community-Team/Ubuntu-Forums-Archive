---
title: "ubuntu 8.04 to lubuntu 10.04 network"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by Cu Rua on 2012-08-17
I have an ancient computer with Ubuntu 8.04 containing files I want to transfer to a newish computer with Lubuntu 10.04. It seemed most efficient to network the two together and just copy-paste. I managed to stumble up to the point where pings were working just fine with a direct connection through an ethernet cable, but now I have no idea how to access one computer's files from the other. As far as I can tell, the computers are talking to each other, but won't let me in on the conversation. 
I would love a step-by-step tutorial on basic Linux networking and some tips on how to get this particular system to work. Thanks!

---

### Post by Kleenux on 2012-08-17
Google can certainly give you a lot of networking tutorial.
(e.g. some [tips]("http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-networking-tips-and-tricks/") that most of them should apply to 08 and 10 versions.

To exchange files between 2 Ubuntues, I found 'nfs' to be safe and convenient
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

You can also use 'samba'
[http://www.abclinux.com.pl/linux-samba-en/]("http://www.abclinux.com.pl/linux-samba-en/")

Or of course use a USB stick (or DVD etc...).

But one side is 8.04 and I don't know what was available at the time.
You can probably upgrade 8.04 to 8.10 then to 9.04, 9.10, 10.04 so that your two boxes have the same tools.

---

### Post by Cu Rua on 2012-08-18
alright, thanks for all the links, i'll take a look a them. 
the reason why i got a newish computer is because the old one is 12 years old ^^; it's simply too ancient and retarded to handle anything newer than 8.04 and i crashed it a great deal trying to upgrade it. i don't think the problem is lack of tools, it's the fact i don't know how to use them ^^;

---

