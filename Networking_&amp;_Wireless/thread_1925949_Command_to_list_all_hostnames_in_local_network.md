---
title: "Command to list all hostnames in local network?"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by hongquan1987 on 2012-02-15
Hi all,
Please let me know if there is a command to list all the hostnames of the computer in a local network.
That is similar to the case of Windows, when we enter Network Places, we can see the name of all other machine in the network.

---

### Post by jonobr on 2012-02-15
Hello


AFAIK the way that windows does its networking is that Netbios over TCP/IP is used to transmit the name over the network and when in a workgroup you can see and attach to other devices on the network.

In linux/ubuntu the approach is a bit different leading to confusion.

The way its done is using Samba [here is an article that might help]("http://www.ghacks.net/2010/12/27/setup-ubuntu-to-browse-windows-network-by-hostname/")

---

### Post by josephmills on 2012-02-15
autoscan ? [http://autoscan-network.com/](http://autoscan-network.com/)
angry ip ? [http://www.angryip.org/w/Home](http://www.angryip.org/w/Home)
nmap/zenmap 
log into router. 
there are tons of tools out there for just that. I hope that this helps

---

### Post by Morbius1 on 2012-02-15
>  That is similar to the case of Windows, when we enter Network Places, we can see the name of all other machine in the network.Windows does that by running the command "net view". The functional equivalent in Linux would be:
```
smbtree
```Another way to get this would be to run:
```
sudo nbtscan 192.168.0.100-192.168.0.150
```Where the 2 ip addresses cover the range of if addresses in your network. nbtscan will also output that machines ip address and the mac address of that machine's nic.

---

### Post by hongquan1987 on 2012-02-16
> **Morbius1 said:**
> Another way to get this would be to run:
```
sudo nbtscan 192.168.0.100-192.168.0.150
```Where the 2 ip addresses cover the range of if addresses in your network. nbtscan will also output that machines ip address and the mac address of that machine's nic.
Sorry, but:
```
sudo nbtscan 192.168.1.100-192.168.1.150
sudo: nbtscan: command not found
```
I'm using Ubuntu 11.10

---

### Post by hongquan1987 on 2012-02-16
Sorry for leading to misunderstanding.
I want a hostname in Linux style, not Windows style, e.g the hostname so that instead of having to type:
```
ssh user@192.168.1.150
```
or
```
ftp://user@192.168.1.150
```
I can do easier:
```
ssh user@hostname
```
or
```
ftp://user@hostname
```
(Don't have to remember the IP because it may change)
The hostname got via Samba is Windows style (and only retrievable if that machine is installed Samba)  and can not be used in my example.

---

### Post by drdos2006 on 2012-02-16
Then install nbtscan from the repositories, or from a terminal run :
sudo apt-get install nbtscan

What IP range does your modem/router give you ?
Is it 192.168.0.1 to 192.168.0.254 ?

Then run : sudo nbtscan 192.168.0.1-192.168.0.254 to get your computer NETBIOS name.

Then you can run :
ssh  my_user_name@my_NETBIOS_name

regards

---

### Post by flash63 on 2012-02-16
Hello,
you can use nmap
```
sudo apt-get install nmap
```
```
nmap -sP <IP-Range>
# example
nmap -sP 192.168.178.0/24
```

---

### Post by hongquan1987 on 2012-02-17
Thank you all for your interest.
The nbtscan is the most suitable tool I'm looking for.

---

### Post by Iowan on 2012-02-18
I have **dnsmasq** as my DHCP server. It ties DNS and DHCP together, so I can ping and SSH by hostname - similar to what you want... dunno if that is an option in your case.

---

