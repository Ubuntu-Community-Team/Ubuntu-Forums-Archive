---
title: "can not access https sites"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Vahids on 2008-12-29
I can't visit http**s** sites;
for EXAMPLE : [https://addons.mozilla.com/](https://addons.mozilla.com/) 
after some minutes show me:
```
**Network Timeout**
The server at addons.mozilla.org is taking too long to respond.

```My web browser is: (Firefox 3.0.5)
what can i do?! :confused:
I can't install addons anyway ....:(

---

### Post by gettinoriginal on 2008-12-29
It just loaded fine for me, are you sure you didn't just catch it at a bad time (servers loaded)??  But have you tried just going to tools, addons, and see what happens there??  Also, have you installed a firewall of any kind ??  You also need to check firefox preferences for your certificate settings.  You might also try clearing you cache and emptying cookies.

---

### Post by Vahids on 2008-12-29
mozilla is not only my problem!!!
my problem is some HTTPS
i have Netowork Timeout in this sites:
[https://www.cia.gov](https://www.cia.gov)
[https://www.pcisecuritystandards.org/](https://www.pcisecuritystandards.org/)
[https://addons.mozilla.com/](https://addons.mozilla.com/)
[https://www.grc.com](https://www.grc.com)
.
.
.

but it this sites i don't have problem:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
[https://www.trustedcomputinggroup.org/home](https://www.trustedcomputinggroup.org/home)
[https://www.dtv2009.gov/](https://www.dtv2009.gov/)
.
.
.
I can't understand my problrm!

---

### Post by halovivek on 2008-12-29
> **Vahids said:**
> mozilla is not only my problem!!!
my problem is some HTTPS
i have Netowork Timeout in this sites:
[https://www.cia.gov](https://www.cia.gov)
[https://www.pcisecuritystandards.org/](https://www.pcisecuritystandards.org/)
[https://addons.mozilla.com/](https://addons.mozilla.com/)
[https://www.grc.com](https://www.grc.com)
.
.
.

but it this sites i don't have problem:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)
[https://www.trustedcomputinggroup.org/home](https://www.trustedcomputinggroup.org/home)
[https://www.dtv2009.gov/](https://www.dtv2009.gov/)
.
.
.
I can't understand my problrm!

you have accept the certification of the sites. In firefox go to advance - encryption - select both use ssl 3.0 and TLS 1.0 . then try . and please post the result.

---

### Post by Vahids on 2008-12-29
> **halovivek said:**
> you have accept the certification of the sites. In firefox go to advance - encryption - select both use ssl 3.0 and TLS 1.0 . then try . and please post the result.

both was selected. :(

---

### Post by Vahids on 2008-12-29
<<** bump **>>

---

### Post by gettinoriginal on 2008-12-29
Aside from emptying cache and cookies to make sure there are no conflicts, check your date and time (if they are not correct, sites won't connect), do you use a proxy ??  If all else fails, you may try unplugging your router, wait 5 sec then plug it back in to reset your IP

---

### Post by halovivek on 2008-12-29
> **Vahids said:**
> both was selected. :(

you can see below.
[http://support.mozilla.com/en-US/kb/Secure+Connection+Failed](http://support.mozilla.com/en-US/kb/Secure+Connection+Failed)

---

### Post by Vahids on 2008-12-29
noting hapiness event !!!
i have this error on Opera too! , so this is a Error from my UBUNTU is not it ?

---

### Post by cariboo on 2008-12-29
It may be a dns problem, try [Opendns]("http://www.opendns.com/dashboard/signin"), and see if that makes any difference.

Jim

---

### Post by Vahids on 2008-12-29
> **cariboo907 said:**
> It may be a dns problem, try [Opendns]("http://www.opendns.com/dashboard/signin"), and see if that makes any difference.

Jim
i have this error again. :( 
> Network Timeout
The server at [www.opendns.com](www.opendns.com) is taking too long to respond.

is it opendns problem?! what can i do now?!

---

### Post by halovivek on 2008-12-30
> **Vahids said:**
> i have this error again. :( 


is it opendns problem?! what can i do now?!

have you installed more than one network configuration tool in ubuntu ?
it may also give the problem.

---

### Post by Vahids on 2008-12-30
> **halovivek said:**
> have you installed more than one network configuration tool in ubuntu ?
it may also give the problem.
no, i did't install network tools! i use the default ubuntu tools.

but, my "NetworkManager Applet 0.7.0" not work and i use pppoe to connect to internet, after update my ubuntu it show me: device in unmanaged!

---

### Post by halovivek on 2008-12-31
> **Vahids said:**
> no, i did't install network tools! i use the default ubuntu tools.

but, my "NetworkManager Applet 0.7.0" not work and i use pppoe to connect to internet, after update my ubuntu it show me: device in unmanaged!

1. Can you post full configuration of the computer?
2. can you post this result ? sudo lshw -C network (type in terminal)
3. can you post this result ? cat /etc/resolv.conf (type in terminal)
4. can you post this result ? route -n (type in terminal)
5. or try this one --it seems that there's something wrong with NetworkManager on Ubuntu. i encountered some problems before, but the network's just fine after i installed wicd to replace the build-in NetworkManager. maybe you should give it a try: [http://www.wicd.net/download.php](http://www.wicd.net/download.php)

could you please post all the result?

---

### Post by Vahids on 2008-12-31
> **halovivek said:**
> 1. Can you post full configuration of the computer?
2. can you post this result ? sudo lshw -C network (type in terminal)
3. can you post this result ? cat /etc/resolv.conf (type in terminal)
4. can you post this result ? route -n (type in terminal)
5. or try this one --it seems that there's something wrong with NetworkManager on Ubuntu. i encountered some problems before, but the network's just fine after i installed wicd to replace the build-in NetworkManager. maybe you should give it a try: [http://www.wicd.net/download.php](http://www.wicd.net/download.php)

could you please post all the result?
1: by what command can i do it?
---------------------------------------

2:
```

*vahid@ubuntu:~$ sudo lshw -C network*
  *-network               
       description: Network controller
       product: B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
       vendor: Techsan Electronics Co Ltd
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b2c2_flexcop_pci latency=32 module=b2c2_flexcop_pci
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 0a:1e:8c:71:bd:b2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=yes multicast=yes


```

----------------------------------------------

3:
```

*vahid@ubuntu:~$ cat /etc/resolv.conf*
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 4.2.2.3
nameserver 89.165.0.13

```
-----------------------------------------
4:
```

vahid@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
89.165.60.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.101.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
172.16.98.0     0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
0.0.0.0         89.165.60.1     0.0.0.0         UG    0      0        0 ppp0

```
----------------------------------------
5:
i instaled wicd, but i can't visit addons.mozilla.com and ...
after install wicd, how do i connect to internet by a pppoe account?! after press connect button in wicd it only knew my Wired but i used pon and dsl-provider in terminal. is it right, or i have to connecet by another way?

---

### Post by Vahids on 2008-12-31
news:

i could visite addons.mozilla.com right now but by Proxy Tools! +>(Ulterasurf):)
but after OFF proxy tool, Network Timeout again!:(

---

### Post by halovivek on 2009-01-01
code:-
1: by what command can i do it?
---------------------------------------
 what is the general configuration. what hard disk you use, processor , ram and general details.

Now you can able to connect to the internet with https sites?

---

### Post by albinootje on 2009-01-01
> **Vahids said:**
> noting hapiness event !!!
i have this error on Opera too! , so this is a Error from my UBUNTU is not it ?

Are you using firewall software on Ubuntu and/or on your router or modem ?

Normal webpages use port 80, but https uses port 443 ...
Make sure you can access port 443 to the outside

---

### Post by Vahids on 2009-01-01
> **halovivek said:**
> code:-
1: by what command can i do it?
---------------------------------------
 what is the general configuration. what hard disk you use, processor , ram and general details.

Now you can able to connect to the internet with https sites?
ooooh yeah,.... ;)

RAM = 512 DDR × 2
CPU = Intel 2400 Celeron
H.D.D = 250 Gig SATA + 80 GIG IDE +(some bad sectors ;) )
VGA = Geforce NVIDIA FX 5500 -- 256 MB
Mainborad = Giga 8IE2004

--------------

i can able to connect all https only by Proxy Tool !!! :)
but without PROXY TOOL, i come back to past :(

---

### Post by Vahids on 2009-01-01
> **albinootje said:**
> Are you using firewall software on Ubuntu and/or on your router or modem ?

Normal webpages use port 80, but https uses port 443 ...
Make sure you can access port 443 to the outside
NO, I never used Firewall.

---

### Post by albinootje on 2009-01-01
> **Vahids said:**
> 
i can able to connect all https only by Proxy Tool !!! :)
but without PROXY TOOL, i come back to past :(

Do you mean with "PROXY TOOL" some Linux software, or is this on your router/modem ?
Or is it the proxy settings in Firefox and Opera ?
Or some Firefox add-on ?

---

### Post by Vahids on 2009-01-02
> **albinootje said:**
> Do you mean with "PROXY TOOL" some Linux software, or is this on your router/modem ?
Or is it the proxy settings in Firefox and Opera ?
Or some Firefox add-on ?
it's Ulterasurf.exe, i run it with WINE and then i set settings in Network Proxy Setting in Firefox or Opera or any Web Browser.

---

### Post by Vahids on 2009-01-03
[SOLVED]

it was from my ISP, thanks to all. and Thank Great UBUNTU ;)

---

