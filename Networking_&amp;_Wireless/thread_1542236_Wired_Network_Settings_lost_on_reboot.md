---
title: "Wired Network Settings lost on reboot"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by mainak_sen on 2010-07-30
I have installed Lucid in a new laptop. Things are running OK except for the following problem:

I connect to the network/Internet using Wired ethernet (TCP/IP) with static IP. Everytime I reboot/restart my network configurations are lost and I have to re-configure. I have googled this problem and have seen a few posts/bugs in launchpad etc. for what appears to be the same issue...but unfortunately I am not getting a clear solution to this problem.

Just for clarity, I am using the following commands to re-configure my network everytime:

sudo ifconfig eth0 192.168.1.231 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.254

Also note that I have already tried editing the /etc/network/interfaces and the /etc/resolv.conf files. But it seems that these are not being picked or are being overridden.

I shall appreciate any help.
Thanks in advance.

---

### Post by dineshs on 2010-07-30
please try this
First backup your /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
```
gksudo gedit /etc/network/interfaces
```
Edit the file so that it contains only these two lines
```
auto lo
iface lo inet loopback

```
save the file and close
Right-click on the NM icon(two opposite arrows on top right) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection you want and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.231
mask 255.255.255.0 
gateway 192.168.1.254
then hit enter 
DNS 4.2.2.1
(You can any working  DNS)
then click apply

---

### Post by Iowan on 2010-07-30
I've seen results both ways on */etc/netowrk/interfaces* - sometimes it solves the problem, sometimes NM seems to overwrite it. **dineshs** has more detailed instructions - you should be able to use Network Manager to configure a static address.  Sometimes it's a bit tricky to get information to "stick" - apparently you need to hit [ENTER] after entering data (as mentioned - gateway in particular). Just clicking on the next field *looks* like it took, but data doesn't get saved.

---

