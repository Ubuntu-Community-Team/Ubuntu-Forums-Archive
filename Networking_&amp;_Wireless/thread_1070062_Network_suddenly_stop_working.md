---
title: "Network suddenly stop working"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by slamelov on 2009-02-14
Hi

I don't know why, but cable network stop working in my Acer Aspire One. But it's very strange because if I start Ubuntu with the USB in Demo Mode, the network works perfect, but not in the installed system. 

In fact, I have reinstalled the system and set up the network. It workwd, but after upgrade and reboot, stop again from working.

I don't Know what's happening

---

### Post by slamelov on 2009-02-15
More strange things...

- I opened Network Manager and deleted eth0 entry
- I pressed add and created a new entry called "Wired Connection 1"
- Set up IP4 to my settings
- click on "system settings"
- reboot
- Now network works and appears 2 entrys, Wired connection 1 and eth0
- After rebooting, internet stop to working again, but network manager says that Wired Connection 1 is connected
- If I run Firefox, appears the url [http://start.ubuntu.com/8.10](http://start.ubuntu.com/8.10) but can't connect to any other URL

Please, any help or tip?

---

### Post by odium1 on 2009-02-15
what kernel are you running?

type this in the terminal and post the output:
```
uname -a
```

i'm curious to see if it is related to the 2.6.27-11 kernel bug affecting ethernet connection

---

### Post by superprash2003 on 2009-02-15
post output of ifconfig from the terminal

---

### Post by slamelov on 2009-02-15
Uname -a:

> 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

ifconfig

> ath0      Link encap:Ethernet  direcciónHW 00:23:4d:9a:be:a7  
          dirección inet6: fe80::223:4dff:fe9a:bea7/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  direcciónHW 00:23:8b:01:93:ae  
          inet dirección:192.168.1.6  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::223:8bff:fe01:93ae/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:536870880 overruns:0 frame:0
          TX packets:0 errors:0 dropped:92 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:219 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:5105 (5.1 KB)  TX bytes:5105 (5.1 KB)

wifi0     Link encap:UNSPEC  direcciónHW 00-23-4D-9A-BE-A7-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:6246 errors:0 dropped:0 overruns:0 frame:581
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:280 
          RX bytes:556472 (556.4 KB)  TX bytes:5244 (5.2 KB)
          Interrupción:18 


---

### Post by Desimal on 2009-02-15
Having similar problems here with a Dell Inspiron 530N that came pre-installed w/ 8.04.  A recent upgrade resulted in the net connection rarely working.  I get it working and then it stops working again.

I'm currently upgrading to 8.10 as I'm running that on another machine and it's not having any problems.

---

### Post by slamelov on 2009-02-16
May be the solution be Mandriva

---

### Post by superprash2003 on 2009-02-16
set back your eth0 to dhcp mode.. and enter **sudo dhclient et**h0 to get an ip from router..

---

### Post by dannyboy79 on 2009-02-16
> **superprash2003 said:**
> set back your eth0 to dhcp mode.. and enter **sudo dhclient et**h0 to get an ip from router..

I believe by his posting he has a valid IP address from his router. it states; 192.168.1.6. It's possible that his router isn't forwarding the DNS requests. Also, just so you know you're always going to be able to view [http://start.ubuntu.com/8.10](http://start.ubuntu.com/8.10) because I believe that's stored somewhere locally on everyones machine when you install Ubuntu, don't quote me on that though. What does this return:
```
route
```
You amy want to look into DNS thread issues.

---

### Post by Dunnix on 2009-02-16
The -11 Kernel broke most peoples Networking devices for Aspire ones, the only solution I know of is recompile your Network Drivers. Or in Grub use an older Kernel.... Should work. 

I apologize if this is a different issue.

---

### Post by slamelov on 2009-02-16
> **Dunnix said:**
> The -11 Kernel broke most peoples Networking devices for Aspire ones, the only solution I know of is recompile your Network Drivers. Or in Grub use an older Kernel.... Should work. 

I apologize if this is a different issue.

I think this is the problem. If I install 8.10 without upgrading, everything works. 

It's not a problem from my setup. I have three computers in my network, four with the aspireone, and all of them working except the aspire since last upgrade.

Thanks for your answers, at least I know what's the problem, and that's important.

---

### Post by slamelov on 2009-02-16
> **dannyboy79 said:**
> I believe by his posting he has a valid IP address from his router. it states; 192.168.1.6. It's possible that his router isn't forwarding the DNS requests. Also, just so you know you're always going to be able to view [http://start.ubuntu.com/8.10](http://start.ubuntu.com/8.10) because I believe that's stored somewhere locally on everyones machine when you install Ubuntu, don't quote me on that though. What does this return:
```
route
```
You amy want to look into DNS thread issues.

The command route:

```
destino         Pasarela        Genmask        Indic Metric Ref Uso Inter
192.168.1.0     *               255.255.255.0  U     1      0   0   eth0
link-local      *               255.255.0.0    U     1000   0   0   eth0
default         192.168.1.100   0.0.0.0        UG    0      0   0   eth0
```

---

### Post by slamelov on 2009-02-16
Here is the bug report
[https://bugs.launchpad.net/ubuntu/+bug/313866](https://bugs.launchpad.net/ubuntu/+bug/313866)

---

### Post by superprash2003 on 2009-02-17
> **dannyboy79 said:**
> I believe by his posting he has a valid IP address from his router. it states; 192.168.1.6. It's possible that his router isn't forwarding the DNS requests. Also, just so you know you're always going to be able to view [http://start.ubuntu.com/8.10](http://start.ubuntu.com/8.10) because I believe that's stored somewhere locally on everyones machine when you install Ubuntu, don't quote me on that though. What does this return:
```
route
```
You amy want to look into DNS thread issues.
 
he said he tried configuring static ip.. so usually if dhcp is enabled in router .. 192.168.1.6 is in most cases within the DHCP range of router... which is why configuring 192.168.1.6 wouldnt quite work..

---

### Post by dannyboy79 on 2009-02-17
> **superprash2003 said:**
> he said he tried configuring static ip.. so usually if dhcp is enabled in router .. 192.168.1.6 is in most cases within the DHCP range of router... which is why configuring 192.168.1.6 wouldnt quite work..not really following you here. first you say that, "192.168.1.6 is in most cases within the DHCP range of router" but then you say, "which is why configuring 192.168.1.6 wouldnt quite work" those 2 sentences contradict each other. Also, it all depends on how the router was setup. for example, my dhcp setup on my router only allows for 5 ip addresses and my 3 computers and 2 xboxs are static ip's, so if someone did crack my WEP wifi, they wouldn't get an ip because there's no more to give out.

it doesn't matter anyway as I believe someone identified the bug and he has the solution.

---

### Post by kev000 on 2009-02-22
also effects 2.6.27-12.

---

### Post by tjapko on 2009-02-27
The same problem with both 2.6.27-11 and 2.6.27-12.

command route is empty.

eth0 is present.

booting with 2.6.27-7 is fine

---

### Post by Liviu-Theodor on 2009-02-27
It happens sometimes to me, but I solve using this command in a terminal:
```
sudo service NetworkManager restart
```
For me this is happening when the internet connection is lost, with any cause (server, router, provider).

---

### Post by dimmat on 2009-03-17
I had the same problem with Advent 4211 and Ubuntu 8.10. After updating, the LAN card stopped functioning. There seems to be a problem with the new kernel that is installed after the update (2.6.7.11). Try this link:

[http://people.ubuntu.com/~smb/bug326891/](http://people.ubuntu.com/~smb/bug326891/)

Download and install the latest kernel.
(linux-image-2.6.27-11-generic_2.6.27-11.27b326891v2_i386.deb worked for me)

LAN card works again!

Enjoy!!

PS: The resolution also applies for MSI Wind U100 since it has the same hardware as Advent 4211.

---

