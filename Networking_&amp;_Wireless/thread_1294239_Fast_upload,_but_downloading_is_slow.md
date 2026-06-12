---
title: "Fast upload, but downloading is slow"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by gyzer on 2009-10-18
I am running Ubuntu 8.04. I use my ubuntu machine for web surfing, email, and I also keep my music on there and run a ampache and samba server off of it. 

After I was able to get samba working I found that my transfer speeds along my gigabit LAN were really slow. I double checked that my onboard nic was a gigabit nic and it was. After that I found that I could get some new linux based drivers for my onboard nic and installed them. That helped.

 I also found this article [http://www.enterprisenetworkingplanet.com/nethub/article.php/3485486](http://www.enterprisenetworkingplanet.com/nethub/article.php/3485486) and that really helped. My upload speed from the server can reach up to approximately 35MB/s, but still, my download speeds never even reach 3MB/s.

I'm not sure if this is a samba problem or if this is a general network problem. I just want to know how I can increase my download speeds to get them near my upload speeds.

I know my upload speed is still very low for gigabit, but the mobo I'm using is very old and the nic is on a PCI bus along with a few other PCI cards.

My NIC is a Realtek RTL-8169 Gigabit Ethernet (rev 10)

So any help with this would be greatly appreciated.

---

### Post by dustgrain on 2009-10-18
Can you please specify the interface you're using (wifi, wired) your uname -a output, your wifi card model, the speed you should get and the speed you're getting..
I'm afraid it's bad news if you use the Intel Pro Wireless iwl3945 because there's a serious bug that causes the download rate on wifi connection to be very slow...
I got that problem and been trying to fix it for weeks now. Apparently all users who have the Intel 3945 chipset are out of luck since no one is addressing this issue so it's either replace the hardware or replace distro for us... 
shameful but that's how it is.

---

### Post by jward3010 on 2009-10-18
And what bugs me the most in regards that problem is that Intel drivers are actually OPEN SOURCE!

---

### Post by Denny Johnson on 2009-10-18
Dustgrain..........I'm not the OP, but may have the problem you mention. I have a 1420n, 8.04, and the Intel 3945. [don't know how to access the uname -a output]
Problem is recent and occurs wired or wifi thru a Linksys WRT54GX2 router, inconsistent download speed in the 1 - 3 meg range. Upload still good.
Download speed wired from the cable modem is a consistent 9.5 - 10.
I assumed it was a problem w the router, but your post has me wondering.

---

### Post by gyzer on 2009-10-18
uname -a output:

```
Linux *computer_name* 2.6.24-24-generic #1 SMP Sat Aug 22 01:06:14 UTC 2009 i686 GNU/Linux
```

My NIC is a wired Realtek RTL-8169 Gigabit Ethernet (rev 10). The speeds that I am getting are based on file sharing via samba with other computers, either Windows XP or Windows Vista all with gigabit nics. My router is a D-Link DIR-825 with gigabit interfaces.

My upload speed on my Ubuntu machine is around 35MB/s, while my download speed on the same machine can't even reach 3MB/s.

---

### Post by dustgrain on 2009-10-18
> **Denny Johnson said:**
> Dustgrain..........I'm not the OP, but may have the problem you mention. I have a 1420n, 8.04, and the Intel 3945. [don't know how to access the uname -a output]
Problem is recent and occurs wired or wifi thru a Linksys WRT54GX2 router, inconsistent download speed in the 1 - 3 meg range. Upload still good.
Download speed wired from the cable modem is a consistent 9.5 - 10.
I assumed it was a problem w the router, but your post has me wondering.

Yes, I'm afraid its the problem card that you have.
you can read about this here: [https://bugs.launchpad.net/linux/+bug/340418](https://bugs.launchpad.net/linux/+bug/340418)
and similar issue here: [https://bugs.launchpad.net/intellinuxwireless/+bug/176271](https://bugs.launchpad.net/intellinuxwireless/+bug/176271)
and probably same mysterious problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271463](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271463)

I'm getting desperate and seriously considering leaving ubuntu because of this.
I got one month to wait before I'll have no choice (I use a wired interface now).

---

### Post by Denny Johnson on 2009-10-18
Thanks for the links.

---

