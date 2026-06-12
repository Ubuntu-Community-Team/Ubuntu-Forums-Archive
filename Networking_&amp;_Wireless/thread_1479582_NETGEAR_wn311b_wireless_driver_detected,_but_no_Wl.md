---
title: "NETGEAR wn311b wireless driver detected, but no Wlan0, 10.04"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by T.Rebel on 2010-05-10
Hi all, 

I hope you can help with this, its got me a little irritated. 

so first off i installed ndiswrapper and ndisgtk, then using my thumb drive installed my .inf file (tried in the terminal as well as ndisgtk and both worked succesfully). when i run "sudo ndiswrapper -l" my wn311b device is shown, and the chipset to be working properly. now when i run "iwconfig", Wlan0 is not listed. 

also i blacklisted the suggested drivers "b43, b43legacy, ssb, and  bcm43xx", could this be the issue? 

im running the newest build of ubuntu which i installed today on this computer for a dual boot drive with vista.

ill try to copy the terminal messages to my thumb drive to post if need be.. i am rather new to command line and linux so bear with me a little..

---

### Post by T.Rebel on 2010-05-10
is no one willing to help??

---

### Post by nuehara on 2010-08-28
I am having the same problem with a netgear GW311v3 PCI card.... any ideas?

---

### Post by trjepp on 2010-10-06
Ditto. 

ndiswrapper -l tells me:
wn311b driver installed, hardware present
sudo modprobe ndiswrapper (no errors there either)
iwconfig (no wlan0)

cmon, this was originally posted in may?

---

### Post by basilwatson on 2010-10-06
Same and I am getting .... yes well

I have a logitec  lan w150n/u2 lan adapter 

s@s-desktop:~/software/wifi$ 
s@s-desktop:~/software/wifi$ ndiswrapper -l
net8192su : driver installed
s@s-desktop:~/software/wifi$ sudo modprobe ndiswrapper
[sudo] password for s: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
s@s-desktop:~/software/wifi$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

s@s-desktop:~/software/wifi$ 

s@s-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 192f:0416 Avago Technologies, Pte. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0789:0168 Logitec Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


how the F"#$#"$#%$$%&&'&'' hell can I get these things to work 

Stephen

---

### Post by mesoptafel on 2010-10-29
Hello,

I also have the netgear wn311b adapter.

I installed the STA-driver in ubuntu 10.04:
Choose in the menu: system -> administration - > 'third party programs'
I am not sure if 'third party programs'is the correct name. I use the dutch language in ubuntu.

You need a wired connection.
In  my case Ubuntu found two drrivers. I used the STA-driver.

It works fine. The maximun speed is 54mbs. Under windows it does 270mbs.

Peer

---

