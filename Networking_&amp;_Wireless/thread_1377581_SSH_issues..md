---
title: "SSH issues."
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by redlinethecar on 2010-01-10
I have two computers one Desktop Compaq SR1720NX ```
**Base processor ** 
 Sempron (P) 3500+ 2.0 GHz
 
[LIST]
[*]1600 MT/s (mega transfers/second)
[*]Socket 939
[/LIST]
 
 
 **Chipset** 
                          ATI Radeon Xpress 200                     
 
 **Motherboard** 
 
[LIST]
[*]Manufacturer: Asus
[*]Motherboard Name: A8AE-LE
[*]HP/Compaq motherboard name: AmberineM-GL6E
[/LIST]
 
 
 **Memory** 
 Component  Attributes   Memory Installed 512 MB (2 x 256)  Maximum allowed 4 GB* (4 x 1 GB)  requires the replacement of the installed 256 MB DIMMs

*Actual available memory may be less  Speed supported PC3200 MB/sec  Type 184 pin, DDR SDRAM  DIMM slots Four  Open DIMM slots Two    
 
 **Hard drive** 
 
[LIST]
[*]160 GB
[*]7200 rpm
[/LIST]
 
 
 
```running Ubuntu 9.10 and a laptop DV4-2049wm ```
Processor Brand:   AMD     Processor Type:   AMD Turion II Ultra Dual-Core     Hard Drive Size:   500GB     Resolution:   1280 x 800     System Ram:   4GB    Shipping Weight (in pounds):  8.5 
```this also running Ubuntu 9.10.  I have my desktop setup through a netgear router with IP 10.0.0.4 and my laptop with IP 10.0.0.7.  Desktop is plugged in directly into the router and I access the router with my laptop using wireless. I'm also using vncviewer and remote desktop on the desktop that way I can enter the command in the terminal to get ssh up and going without having to plug in the monitor.  I set up ssh on the desktop using. ```
sudo apt-get install openssh-server
```After installation I could connect to desktop with 
```
ssh -l server 10.0.0.4
```it would then ask for a passphrase and after entered I was ok to go.  Then I would try to transfer files to the desktop using scp but I would get an error saying connection refused.  So thinking that maybe if I restart my desktop everything would probably work fine I did that now i get an error when trying to connect
```
ssh -l server 10.0.0.4
Read from socket failed: Connection reset by peer
```After searching google for hours about how to fix this issue ive read that i need to use 
```
/usr/sbin/sshd
```after entering this into the desktop/server i get 
```
sudo /usr/sbin/sshd
[sudo] password for server:
could not load host key: /etc/ssh/ssh_host_rsa_key
could not load host key: /etc/ssh/ssh_host_dsa_key
```After a few more hours of google searching I find I have to use ssh-keygen so i do
```
sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N "my passphrase"
```i get

```
 [sudo] password for server:
Generating private/public rsa pair key
Your identification has been saved in /etc/ssh/ssh_host_rsa_key.
Your public key has been saved in /etc/ssh/ssh_host_rsa_key.pub.
The key fingerprint is:
XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX root@server-desktop
the keys randomart image is 
IMAGE HERE

```now i run sshd and i get guess what
```
sudo /usr/sbin/sshd
[sudo] password for server:
could not load host key: /etc/ssh/ssh_host_rsa_key
could not load host key: /etc/ssh/ssh_host_dsa_key
```Any help would be greatly appreciated.  Usually all my problems are solved on here so thank you in advance for reading and replying to my post.

---

