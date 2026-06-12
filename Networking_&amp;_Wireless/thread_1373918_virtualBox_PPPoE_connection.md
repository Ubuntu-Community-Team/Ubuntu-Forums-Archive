---
title: "virtualBox PPPoE connection"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by maruf10 on 2010-01-06
Hello
I have just installed ubuntu 8.04 in virtualBox ... i have a PPPoE connection ... its not working in virtualBox ... how can i configure virtualBox ??
Plese do help ...

---

### Post by suseendran.rengabashyam on 2010-01-06
Hi,

Please try the following steps:


[LIST]
[*]Power off your virtual machine before you start doing this.
[*]Right Click on your Virtual Machine->Settings->Network->Adapter 1
[*]Check "Enable Network Adapter"
[*]"Attached to:" should be Bridged Adapter.
[*]Then click "Ok"
[*]Start the VM and Check whether you are able to make a PPPoE connection.
[/LIST]

---

### Post by maruf10 on 2010-01-06
it's not working ... 
any more suggestions ?? :(

---

### Post by SecretCode on 2010-01-06
What is the host operating system and how is it connected to the internet? Post its IP configuration (output of *ifconfig* if it's a linux host, *ipconfig* if it's a windows host).

I presume you can make a PPPOE connection from the host.

Also post the output of *ifconfig* from the ubuntu guest OS.

---

### Post by maruf10 on 2010-01-08
sorry for late reply . i was out of network

host  : xp
guest : ubuntu

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Autoconfiguration IP Address. . . : 169.254.195.87
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

PPP adapter big:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 172.16.0.145
        Subnet Mask . . . . . . . . . . . : 255.255.255.255
        Default Gateway . . . . . . . . . : 172.16.0.145


i have attached the ifconfig result of ubuntu as a .bmp file .. please see it ..

---

### Post by SecretCode on 2010-01-08
So ... your host only connects via ppp. I think with the vbox bridged interface, you should be able to use ppp, but I haven't worked with that for a while.

Meanwhile, if you set up the vm to use NAT (in the virtualbox settings for the machine - with it powered off), can you connect to the internet?

---

### Post by maruf10 on 2010-01-09
no

---

### Post by SecretCode on 2010-01-09
Well, I think that's odd ... but I don't have a setup like that to test on.

Try this: set the guest back to bridged networking and reboot. Open a terminal window in the guest and running *sudo pppoeconf*. Follow the prompts.

Do you know if your ISP allows more than one concurrent pppoe connection?

---

### Post by yafes on 2010-01-09
> **maruf10 said:**
> Hello
I have just installed ubuntu 8.04 in virtualBox ... i have a PPPoE connection ... its not working in virtualBox ... how can i configure virtualBox ??
Plese do help ...

best way is the port forwarding, check that: [http://sk.c-wd.net/wp/2008/01/05/virtualbox-port-forwarding-with-linux-host/](http://sk.c-wd.net/wp/2008/01/05/virtualbox-port-forwarding-with-linux-host/)

---

### Post by suseendran.rengabashyam on 2010-01-12
Hi,

You should able to connect to the Internet if you set up the VM to use NAT.

After setting the NIC to NAT in the Virtual Machine settings, power on the VM and check the output of ifconfig after your Hardy guest boots. If the interface does not have an IP attached, try the following command:

dhclient eth0

in the guest, check if you are able to get an IP from the DHCP server of the Virtual Box and if you are able to connect to the net.

---

### Post by maruf10 on 2010-01-12
> in the guest, check if you are able to get an IP from the DHCP server of the Virtual Box and if you are able to connect to the net.
what does this mean ??

---

### Post by suseendran.rengabashyam on 2010-01-13
Hi,

1) Try the following command in guest OS (Ubuntu) 
   # ifconfig eth0

2) See if the output of the above shows an IP address attached to eth0.

3) If you don't see an IP address, run the following command
   # dhclient eth0

4) Run
   # ifconfig eth0
   To check if eth0 has got an IP now.

---

