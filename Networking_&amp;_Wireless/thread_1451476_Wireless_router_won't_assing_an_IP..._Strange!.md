---
title: "Wireless router won't assing an IP... Strange!"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by pro003 on 2010-04-10
I have a wireless router HG520s. I have enabled a hidden (nonbroadcast) mode on channel 1 with WEP encryption (64bit / 10 hexadecimal chars). Mac filter is not enabled. Name of ESSID is "homenet", everythig else is usually by default.
Now, when I try to connect with my laptop (os=winxp) I can't see the essid (because it's hidden). Well I know I have to set it manually. I open windows wlan manager and go advanced (win-firewall is disabled) and create new wlan network profile to connect with, I set up the credentials, name of ap, enc wep, and the rest of stuff (I assume you know how 'hard' it is) and then I can see when refresh wireless network my own network, but the PROBLEM is that I have a Limited Access or/and no access to internet. I remind you that router is well connected and there is internet on lan ports, but I can't access through wireless with my laptop.
In fact I can only see my essid and that broadcasting is active, pwr is good, distance is not the problem. My laptop cannot get ip assigned and the same problem is with my E51 nokia (No Gateway Reply!).

I think I said enough. Now any of you guys please try to explain me how's this possible?

Thank you for reading my post and hopefully someone will reply on it.


P.S. The problem is same with ubuntu. My wife is using Win7, I'm on Ubuntu and my son he's on laptop with XP installed. So please don't reply me with "you should post your problem on some windows forum". Thanks.


Cheers

---

### Post by gordintoronto on 2010-04-10
Is the router set to be a DHCP host? Have you tried using a static IP address (such as 192.168.1.14), where you specify (in network manager) the DNS server addresses?

---

### Post by pro003 on 2010-04-11
> **gordintoronto said:**
> Is the router set to be a DHCP host? Have you tried using a static IP address (such as 192.168.1.14), where you specify (in network manager) the DNS server addresses?

thank you gordiontoronto for your reply.

well the router is set by default to be a dhcp host. it always worked like that... and yes I tried set ip manually through **ifconfig <interface> <xxx.xxx.xxx.xxx>** and **route add default gw <xxx.xxx.xxx.xxx>** and still "network is unreachable" when I try to ping gateway.

I used wireshark to analyse the protocols and data packets and I can clearly see that network is active on my router and my pc which is connected through lan port to the router.

I exhausted my knowledge of networking and I wanted to share this with the forum I have spend the most of the time of all forums.

If any idea anyone, you're welcome, and thanks.

---

### Post by Iowan on 2010-04-11
I've read that hidden ID's can be troublesome. Have you tried (or could you try) "unhiding" the router?

---

### Post by pro003 on 2010-04-12
> **Iowan said:**
> I've read that hidden ID's can be troublesome. Have you tried (or could you try) "unhiding" the router?

Thank you for your reply Iowan. 

Yes, tried that too. Forgot to mention it, but yes. Problem still remains.

---

### Post by Iowan on 2010-04-12
Probably won't help, but [here]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") is a kludge you can try.

---

### Post by pro003 on 2010-04-13
> **Iowan said:**
> Probably won't help, but [here]("http://ubuntuforums.org/showpost.php?p=8703594&postcount=26") is a kludge you can try.

will try... post results later...

thanks again ;)

---

### Post by Kevbert on 2010-04-13
It suggests that your received signal strength or quality may be poor. Do you have anything nearby operating around 2.4GHz such as a cordless phone or even a microwave as some work at the same frequency? Also what is the output in Ubuntu terminal of
```
iwlist scanning
```

---

