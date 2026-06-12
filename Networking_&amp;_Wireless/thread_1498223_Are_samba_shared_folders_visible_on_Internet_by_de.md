---
title: "Are samba shared folders visible on Internet by default?"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by ario on 2010-05-31
Hi.
I have created a shared folder in my ubuntu. And checked allow guest user access. I can access this folder with my other ubuntu computer connected trough LAN.
The question is if anyone have my IP address can he/she access to my shared folder?
Are samba shared folders shared over internet too? If so, This will be a very dangerous security problem.
Thanks for your answer.

---

### Post by sanderj on 2010-05-31
> **ario said:**
> Hi.
I have created a shared folder in my ubuntu. And checked allow guest user access. I can access this folder with my other ubuntu computer connected trough LAN.
The question is if anyone have my IP address can he/she access to my shared folder?

If you have a LAN, you're probably behind a router/modem doing NAT. If so, all traffic to your public IP address is dropped by your NAT, and your local LAN IP address (something like 192.168.x.x or 10.x.x.x) is useless on Internet.

If you *want* your shared folders to be accessible from Internet, you have to do port forwarding, or start using IPv6.

> **ario said:**
> 

Are samba shared folders shared over internet too? If so, This will be a very dangerous security problem.
Thanks for your answer.



See above. And, no, not a security problem; you're in charge of it.

---

### Post by ario on 2010-06-01
Thanks sanderj.
So you mean my shared folders are not visible on internet, and I guess I do not need IPv6 thaw.
Ok... .

---

### Post by ario on 2010-06-04
Man! It seems to be really shared on Internet without asking me for! Whenever I share a folder on my Ubuntu, and while I'm connected to Internet, There will be two unwanted files created suddenly:
```
khw
and **vsoagw.exe**
```
The second seems to be a windows virus. I'm not worry about that virus now, but it seems that this little piece of code can see my shared folder trough Internet, because I have no windows computer connected to my home network. If a simple windows virus can see it, then everybody can see and even modify it.
This is a very dangerous security issue. I think it's a bug!
Any suggestions?

---

### Post by llawwehttam on 2010-06-04
I have been using samba shares for a long time. It is not up to samba where the folder is shared so the means it cannot be a bug. It is only shared on your local network as long as you are behind a firewall router. Because of this I think you have a windows computer on the network somewhere that is infected.

---

### Post by ario on 2010-10-02
By the way, I created a user and password for my samba shares using smbpassws or the samba-config-samba GUI utility and now I don't care if anyone can see my shared folders on the Internet. Because they're now protected with password!:)

---

