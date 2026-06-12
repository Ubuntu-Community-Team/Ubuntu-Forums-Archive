---
title: "Upgrading from 9.10 to 10.04 with static ips no more network on ubuntu server"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by ratius on 2010-05-02
Hi there, I recently upgraded from Karmic to Lucid and I suddenly lost all network access. Let me explain my little experience:

At first I had a 8.04 LTS that used a static ip with the dhcp-client package removed that I upgraded all the way to Karmic. On every upgrade everything went fine. Recently I wanted to get my hands on a release candidate of Ubuntu lucid so I did a do-release-upgrade -d to find out that after installation I had no more networking. Since it didn't work after some trials and errors, I decided that my server needed some freshness anyways and directly installed lucid by reformatting everything. That didn't seem to work either. I went back to Karmic and decided I would wait for the public release of lucid. Now, I have installed the new release and it is still happening. I am still using a static ip with the dhcp-client removed. As it anything to do with this? Even though it worked fine on Karmic?

Here's my /etc/network/interface file:

```
auto lo
auto eth0 

iface lo inet loopback

iface eth0 inet static
address 192.168.1.51
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 24.200.241.37 24.201.245.77 24.200.243.189
```

I have also put my dns nameservers in /etc/resolv.conf.

ifconfig output does output eth0 with the ip on 192.168.1.51 but I can't ping anything not even my other network computers.

Of course I tried restarting the networking (/etc/init.d/networking restart), the ifup and ifdown on eth0 too but the internet is still unreachable.

I am no expert using Ubuntu but I can get my way around with your guidance with the terminal, since this is happening on ubuntu server and I have not installed any GUI on that computer.

Any help or topic redirection if this is already solved would be appreciated. Thanks!

---

### Post by Iowan on 2010-05-02
Can you ping the gateway?

---

### Post by ratius on 2010-05-02
No I cannot. Pinging 192.168.1.1 (my gateway) outputs destination host unreachable. I'm pretty sure that as soon as the connection will be made to the router everything will be fine again. I tried restarting the router for good measure to no avail. Anything else you want me to do?

---

### Post by ratius on 2010-05-04
Bump, any ideas? I'm guessing it might be a driver problem since it was working A1 on Karmic but I would like to fix this without having to rollback to any previous version.

---

### Post by davec64 on 2010-05-04
Hi Ratius,

I've got a similar problem with the standard 64 bit desktop edition of Lucid. Works fine through the DHCP server but if I try to set a static IP using Network Manager it subsequently fails to connect to the Internet. Previous versions worked fine!
I'm going to remove Network Manager and edit the files underneath to see what happens. If the static IP fails this could indicate a problem across both editions.

Just out of interest what's your network card?

---

### Post by davec64 on 2010-05-04
Strange!

My problem seems to be Network Manager which I've now removed and set a static IP editing /etc/network/interfaces. This works fine for me.

Sorry, not much help to you with the server edition!

---

### Post by HiDef4Ever on 2010-05-04
I'm having similar issues with 9.10 server since last weeks updates. Using tracepath to any ip address outside my subnet would fail to list the local gateway and take a few moments longer to complete the trace. 

I've had success in moving the line 'auto eth0' to the line just above 'iface eth0 inet static'. The tracepath now lists the gateway and dhcpd and squid are much happier.

---

### Post by Bats72 on 2010-05-04
i got exactly the same issue with lucid server edition even if i remove network manager ...

if i do ifconfig after editing /etc/network/interfaces 

it show me only the loop  (lo) eth0 is not there ...

on a fresh install and dhcp network works ! as soon i change /etc/network/interfaces  no network .. of couse restart  and remove manager do nothing more .... 

thanks helping us out

p.s. to ratius you from quebec ?? it seem videotron dns ip's ...just to say me too :D

---

### Post by ratius on 2010-05-04
> **davec64 said:**
> Just out of interest what's your network card?

It's integrated into my motherboard, an old so hated eMachine that got transformed into a server as soon as I saw it wouldn't run a thing that has graphics. Anyway, lspci outputs **Realtek Semiconductor Co., Ltd. RTL-8139/8139C/80139C* (rev 10)**

> **HiDef4Ever said:**
> I've had success in moving the line 'auto eth0' to the line just above 'iface eth0 inet static'. The tracepath now lists the gateway and dhcpd and squid are much happier.

I tried just that after you said it, being super pumped up that it might work and being super pissed that it did not for me.

> **Bats72 said:**
> p.s. to ratius you from quebec ?? it seem videotron dns ip's ...just to say me too

Yes I am, I hope we both succeed into this network connection issue.

The thing is, I removed the dhcp client and I don't have a network connection. I know I should try to get the package on a USB key but even if it worked after it is installed I wouldn't want any dhcp addressed ips, since my server relies on a static ip for everything to work properly.

Formatting and putting back Karmic seems to me to be the "reboot option" which won't correct the error and won't assure that it won't appear again if I ever try to redo a release-upgrade.

Again, I do not claim to be an expert, so if anyone could assist in trying to solve this, I will post any output requested.

Edit: looks like someone with same Ethernet controller stumbled on the same issue [here]("http://ubuntuforums.org/showthread.php?t=1422118").

---

### Post by ratius on 2010-05-04
Ah got it! You need to add the noapic option into the grub.

For grub2 users, vi into /etc/default/grub and change:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```

I have removed the quiet and splash since I prefer having ouput telling me if I have any startup script that goes wrong and pinging the gateway, a DNS such as google.ca or another network connection worked again!

Thx for the support guys.

---

### Post by Bats72 on 2010-05-05
wow gj ill try that and see if it works for me  :D

---

### Post by Bats72 on 2010-05-05
thanks ratius it is in deed working :D

---

