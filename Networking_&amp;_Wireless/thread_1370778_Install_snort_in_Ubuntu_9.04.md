---
title: "Install snort in Ubuntu 9.04"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by jenaniston on 2010-01-02
The yum install snort in fedora is so easy . . . yet with the Ubuntu corresponding command . . .

$ sudo apt-get install snort 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package snort

is it a slightly different name or something in Ubuntu ?
is there something like Yum Extender that gives available packages in a GUI ?

Thank you.

---

### Post by puppywhacker on 2010-01-02
The package is also named snort, although there is also a packge called snort-mysql which uses mysql as backend.

[https://help.ubuntu.com/community/SnortIDS](https://help.ubuntu.com/community/SnortIDS)

If the packages can't be found you can always update the apt packages with

apt-get update

If apt can't find snort in the first place the appropriate repositories are probably not enabled.

A GUI for APT is Synaptic and you could also use the textbased aptitude. You can enable the repositories from the preferences there or edit the /etc/apt/sources.list file

---

### Post by jenaniston on 2010-01-02
Thanks for the link . . .
It all started out ok with . . .

```
sudo tasksel install lamp-server
```Installed as expected prompting for password, then . . .

```
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 33
Server version: 5.0.75-0ubuntu10 (Ubuntu)

mysql> create database snort;
Query OK, 1 row affected (0.00 sec)

mysql> GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES ON snort.* TO 'snort'@'localhost' IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.01 sec)

mysql> quit
Bye
```But then - as the link instructions said - but once again . . .

```
sudo apt-get -y install snort-mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package snort-mysql
root@ubuntu:/home/ubuntu# 
```
Uggh . . .

---

### Post by puppywhacker on 2010-01-03
And that is where the second part comes in. You still need to enable the "universe" repository in APT. To do this you only need to follow the first 2 screenshots from the link below

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by jenaniston on 2010-01-03
ok thanks for letting me know I'm still on the right track -
and I'm back at it this afternoon.

I'm  only trying to use snort to pick up a "thin" client MAC  address for the dhcp server declarations for a diskless LAN boot -
the  "thin" client laptop is the only ethernet connection.

I was using snort in Fedora 11 Live - but the MAC obtained so far with snort then - of the packets sent to client - 
only registers as the generic  > F:F:F:F:F:F :67 
port 67 and only UDP packets sent I get alright with snort, but I doubt if that generic MAC can be used for the 
hardware ethernet MAC; dhcp3.conf file declaration needed for a fixed address boot.

I tried Ubuntu for the dhcp server and it seems like that part it'll be easier in U9.04 vs. F11 -
 so snort running in the background to pick up the MAC address will be helpful in Ubuntu.

Thanks again.
Any other suggestions for getting the bootp/dhcp **client **MAC address (_before_ it boots up) will be appreciated
(as the ifconfig utility is only for the system running from, snort does both sides but maybe other utilities can do that as well ?).

---

### Post by puppywhacker on 2010-01-03
hangon, I can't completely follow what you are trying to do. I wonder why you need the mac address during bootup, does it change all the time and therefor also the ipaddress changes?

If you only want to list the MAC address than you can check the arp table or make a network trace (something that snort does as well, but then with the bells and whistles)

```
arp -a
tcpdump -i eth0 -s 0 -v

```

FF:FF:FF:FF:FF:FF is the broadcast mac-address used initially to find the dhcpd server.

you can check the dhcp lease file to see which ip-address is used for which ip-address. 
/var/lib/dhcp3/dhcpd.leases

---

### Post by noway2 on 2010-01-03
Check out this thread:[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

It is an excellent, step by step how to for installing snort with mysql, and a set of web based administration tools.

---

### Post by jenaniston on 2010-01-03
> **puppywhacker said:**
> . . . I wonder why you need the mac address during bootup, does it change all the time . . .?

If you only want to list the MAC address than you can check the arp table or make a network trace (something that snort does as well, but then with the bells and whistles)

```
arp -a
tcpdump -i eth0 -s 0 -v

```FF:FF:FF:FF:FF:FF is the broadcast mac-address used initially to find the dhcpd server.

you can check the dhcp lease file to see which ip-address is used for which ip-address. 
/var/lib/dhcp3/dhcpd.leases

Yes, as I have understood I will need the MAC address of the *client *for booting to assign IP address
 - it does not change but I don't know what it is for the dhcp client laptop -yet.

the follwing is from [http://linux-sxs.org/internet_serving/pxeboot.html](http://linux-sxs.org/internet_serving/pxeboot.html)
```

ddns-update-style interim;
  subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.10 192.168.0.254;
  default-lease-time 3600;
  max-lease-time 4800;
  option routers 192.168.0.1;
  option domain-name-servers 192.168.0.1;
  option subnet-mask 255.255.255.0;
  option domain-name "llama.net";
  option time-offset -8;
  }
 
  host llama0 {
  hardware ethernet 04:4B:80:80:80:03;
  fixed-address 192.168.0.254;
  option host-name "llama0";
  filename "pxelinux.0";
}

```  In a nutshell, this sets up a DNS server that will assign IP address 192.168.0.254 to your client box that
 has MAC address 04:4B:80:80:80:03 assigned to its PXE-boot capable NIC. Another thing to note is that we're
 reserving the private 192.168 subnet for this setup.
 The only thing you need to change in the above, is the MAC address to match that of the NIC on your client box.
__________________________________________________________________________________

If the broadcast MAC of FF:FF:FF:FF:FF:FF were sufficient then fine . . .

In both snort and the tcpdump command I get the (oui unknown) message.

I have learned today that "The oui is the first 6 digits of a MAC address"
[http://digg.com/hardware/MAC_Address:_Do_you_know_what_the_OUI_is_](http://digg.com/hardware/MAC_Address:_Do_you_know_what_the_OUI_is_)

and these first six hex digits tell you know who really made that NIC

00:12:3F:XXXXXX is the known MAC address for the server 
[http://standards.ieee.org/regauth/oui/oui.txt](http://standards.ieee.org/regauth/oui/oui.txt)

and that ***is ***a Dell.

Interesting that the
```
tcpdump -i eth0 -s 0 -v
```command you provided has resulted in some insightful  output - maybe I won't need MAC to boot if I don't use a fixed address at first try.

If snort runs in the background, it will get that MAC even if the boot is unsuccessful I think.

Thanks for the leads and links so far.

---

### Post by puppywhacker on 2010-01-04
It always makes me happy to see that you have done your homework on PXE and OUI-48 and have described them very well. good job!

The thing is that a PXE client will fetch an ip-address twice. The first time is done immediately by the PXE bios in the network card, to fetch the kernel and the initrd. But as soon as both are running linux is alive and as part of the networking the dhcp request will be done again. This time permanently. It's the last time that really counts, although the dhcp server is smart enough to remember to assign the same address as last time. So the ip-address doesn't change frequently.

A MAC address is usually permanent. That is why in your example you can force the dhcp server to handout a fixed ip address to a certain mac hardware address. You only have to configure it once and your set for life

hardware ethernet 00:C0:4F:80:80:03;
fixed-address 192.168.0.254;

FF:FF:FF:FF:FF:FF is not sufficient, but you might get the same ip-address over and over again without configuring it in dhcpd.conf

no need to use snort (although snort is fun too :) )

And since you have done your homework and understand tcpdumo, I'll do my homework too. Below command will show you the oui's on the network.

```
tcpdump -i eth0 -s 30 -e | cut -f1 -d','
Use CTRL-C to break
```

The first 30 bytes of each packet that goes out or comes in from interface eth0. Show the ethernet field. Pipe it into cut print field1 until the comma.

On the line you will see FF:FF:FF:FF:FF:FF the other OUI is the one from your thin client.

Goodluck

---

