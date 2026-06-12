---
title: "witopia PPTP VPN Service"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by schenier on 2010-11-28
Hello,

I can't seem to find a solution to my problem. 

I got a service for VPN with witopia and I have no problem using it on my ipod touch. But when I try to make it work in Ubuntu 10.04, it always tells me that the connection failed.

I went in VPN Connections -> Configure VPN -> Add -> PPTP

I chose a name. added the server Gateway I got from them and added my user name and password. Kept Available for all user unchecked (if was not keeping the password) and that's it. IPv4 setting was left to automatic.

But it always fails to connect when I try to connect.

What am I missing?

Please help, and bear with me, I am new at all this.

thanks

---

### Post by JCMB1 on 2010-12-24
I stumbled into the answer to this one here:
[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

Go to terminal and use the command:
sudo apt-get install network-manager-openvpn

pick your the VPNs you want to set up and reboot.

And you should be good to go.

BTW, I am assuming that you copied the VPN connections by copying all the files  from **C:\Program Files\personalvpn\config\**.

---

### Post by Welly Wu on 2012-06-03
I signed up for WiTopia basic VPN service today and I had a problem connecting. I use GUFW and I deny incoming and outgoing traffic. I have a list of exceptions based on port numbers, TCP, and UDP protocols. I read the WiTopia FAQ and the conflicting software guide to open up port 1194 over UDP for SSL VPN and TCP 1723 and IP 47 (GRE) for PPTP VPN. That still did not work with GUFW and WiTopia VPN. So, I changed all outgoing traffic to allow and I can connect to WiTopia VPN successfully. It works now. WiTopia has a configuration guide for Firestarter, but it does not have anything for GUFW. You can not use both Firestarter and GUFW at the same time on Ubuntu.

---

