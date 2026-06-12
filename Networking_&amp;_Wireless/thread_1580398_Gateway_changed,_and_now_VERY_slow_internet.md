---
title: "Gateway changed, and now VERY slow internet"
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by oygle on 2010-09-23
Previously had 2 Ubuntu computers setup

Computer A (192.168.1.101) <=> Computer B (192.168.1.100) -> Internet

Computer B was the gateway, and it is dual boot, one drive Ubuntu, one drive XP. I'm using XP as the gateway now, but Computer A is extremely slow, virtually nothing getting through.

Have checked sysytem logs, verified /etc/hosts file, and all the network side of things. Can ping either IP adddresses from either computer. On the XP side, have modified hosts and lmhosts, and the XP computer has very fast internet connection.

Did have Commodo firewall running on the XP, disabled that, and checked that no Windooze firewall was running. Have restarted the network on both computers a number of times.

Can't figure out what the problem is. It's obviously on the XP side, as when I booted to Ubuntu (previously) on Computer B, the gateway worked just fine. Have checked the whole tcp/ip side of things on XP; seems to be okay.

Oygle

---

### Post by pedro_orange on 2010-09-23
Sounds like your gateway machine is not configured correctly. This is a Windows problem, so you might well be in the wrong place asking for help, however I did some Googling for you:

- [http://howto.techworld.com/operating-systems/536/building-a-windows-firewall-gateway/](http://howto.techworld.com/operating-systems/536/building-a-windows-firewall-gateway/)

- [http://www.home-network-help.com/ip-forwarding.html](http://www.home-network-help.com/ip-forwarding.html)

I would imagine the XP machine is not letting the Ubuntu box through because of the some security issue (Considering you said Firewalls are off etc) or it is refusing to port forward / route correctly. You could try connecting a Windows machine to the Windows gateway and see how that behaves.

Also the default gateway on Computer B, now correctly points to Computer A's IP addr? (Can never be too careful with DHCP!)

---

### Post by oygle on 2010-09-23
Thanks Pedro. It was an ICS option that wasn't enabled, and even then it wanted a particular IP assigned, so had to go and force that. It is working now, thanks.

Oygle

---

