---
title: "Samba + DMZ zone? Safe?"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by Twikkistep on 2010-11-02
Hi there,

Just checkin - since I don't know everything about networking. I installed a Ubuntu Server with samba enabled, and I'm able to browse my shares internally just great. However, I just got a fixed IP address from my ISP, and want to place this Ubuntu Server in the DMZ zone, so I can log in from the outside by just going to the IP address.

Now, my question: if I do that, should I worry about the Samba shares? Can someone else browse them by connecting to the IP? Is it best to not use the Sambe shares at all? Can someone give me some advice?

Thanks!

---

### Post by prshah on 2010-11-02
> **Twikkistep said:**
> want to place this Ubuntu Server in the DMZ zone, so I can log in from the outside by just going to the IP address.

Placing a machine in the DMZ zone effectively removes any protection the router gives it. Given that your machines samba ports (135,137,445,etc) will be open to the 'net, you can expect script kiddies targeting these known ports.

A better alternative would be to give a static INTERNAL IP to the samba server (eg 192.168.1.11), enable NAT in the router, put random numbers (range of 10000-30000) for outward ports and the correct internal port number (Eg 135) for the inward ports, and the internal IP address of your samba server. That will give you samba access over non-standard ports, which script kiddies are unlikely to stumble across.

However, I have no idea if samba access over non-standard ports is at all possible with windows clients.

There are other possibilities, post back if you want to discuss them.

Exposing samba's standard ports over the Internet is an invitation for trouble.

---

### Post by Twikkistep on 2010-11-02
Thanks for the info.

What if I only open ports 21 (FTP) and 22 (SSH) on the firewall? Do script kiddies have a change to reach my samba share?

I'll need to read up on port forwarding I suppose.

---

### Post by prshah on 2010-11-02
> **Twikkistep said:**
> only open ports 21 (FTP) and 22 (SSH) on the firewall? Do script kiddies have a change to reach my samba share?

They cannot reach your samba shares via your FTP/SSH ports, but then, neither can you (unless you specifically set your samba up to use these ports).

However, opening up ANY of the standard port numbers (Eg, port number less than 1024) will make your machine a target for wanna-be hackers. It's not as though having an accessible port will attract unwanted attention like a magnet attracts iron filings; it's just that most hacking attempts start by trying to find a responsive standard port. It becomes too time consuming to check the higher ports, so malcontent entities generally check the lower (standard) port ranges, then move on to the next target.

Open any higher ports (10000-30000) range, and will be safer than using the standard ports (not bulletproof, just safer).

Also, given that you are using a static IP, it makes sense to install and activate fail2ban to prevent multiple access attempts from a single IP. If a person tries 5 (or more, configurable) unsuccessful access attempts, fail2ban blocks the source IP address for a configurable time interval; if there are continued attempts, the time interval keeps increasing. So the "attacker" will have to keep changing his IP address for access attempts; mostly, he will give up and move on to less secure targets (of which there is no shortage, unfortunately).

Hope this helps in some measure; if you post what you are actually attempting to do, maybe we can give you some more specific tips.

---

### Post by CharlesA on 2010-11-02
Why do you want to expose samba to the internet?

There are better ways to access files remotely - SFTP or SCP to name a couple.

---

