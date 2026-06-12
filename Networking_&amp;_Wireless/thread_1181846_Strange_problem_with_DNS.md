---
title: "Strange problem with DNS?"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by Silverboy on 2009-06-08
Hi,
I (probably) have a problem with my DNS. Yesterday I have installed kubuntu 9.04 and I have configuerd manually my network and DNS.
If I ping my router or my DNS server ```
ping 192.168.1.1
``` or ```
ping 208.67.222.222
``` it's works.
With KPackageKit I can download any updates and programs (e.g. Firefox) so it seems linux can resolv the repositories' url (and everything seems to work), but if I try to surf on internet with a browser (or akregator) I can't open any page.:confused::confused::confused:
I don't believe this is a problem due to my browsers because if I try to go on [http://209.85.171.100](http://209.85.171.100), it appears the google page.

This is my /etc/resolv.conf file:
> 
nameserver 208.67.222.222
nameserver 208.67.220.220
This is my /etc/network/interfaces file:
> 
# We always want the loopback interface.
#
 auto lo
 iface lo inet loopback

# An example ethernet card setup: (broadcast and gateway are optional)
#
 auto eth0
 iface eth0 inet static
     address 192.168.1.3
     network 192.168.1.0
     netmask 255.255.255.0
     # broadcast 192.168.0.255
     gateway 192.168.1.1
This is the result of "ifconfig":
> 
eth0      Link encap:Ethernet  HWaddr 00:1a:80:24:69:6f  
          inet indirizzo:192.168.1.3  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::21a:80ff:fe24:696f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:2 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:472 (472.0 B)  Byte TX:3807 (3.8 KB)
          Interrupt:16 

lo        Link encap:Loopback locale  
          inet indirizzo:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:6248 (6.2 KB)  Byte TX:6248 (6.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:2b:7d:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-2B-7D-C7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
This is the result of "host www.google.com":
> 
;; connection timed out; no servers could be reached
And this is the result of "route":
> 
[FONT=Verdana]Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0[/FONT]
Can anyone help me?:(
thanks,
rino:smile:

PS:I have tried to change the way to set the DNS using the "resolvconf" package and adding the option "dns-nameservers" in interfaces, but the problem persists. I have tried to reinstall kubuntu too. With the past releases of kubuntu I used internet without any problem.

---

### Post by superprash2003 on 2009-06-08
post output of **nslookup google.com**

---

### Post by brabo on 2009-06-08
or just try to add the nameservers to the interfaces file as i do.

so at the end append the dns line:
# broadcast 192.168.0.255
gateway 192.168.1.1 
dns-nameservers 208.67.222.222 208.67.220.220

then do:
sudo /etc/init.d/networking restart

now your system should find the opendns servers.
hope this helps!
brabo.

---

### Post by Silverboy on 2009-06-08
[B]@ superprash2003:
[/B]
Nothing, actually only kpackagekit seems to work:
```

;; connection timed out; no servers could be reached

```**@ brabo:**

I had yet tried this way, but installing the **resolvconf **package that I red should support the **dns-nameservers** option in /etc/network/interfaces. Had you used this option without the **resolvconf **package?

---

### Post by brabo on 2009-06-08
it works fine on my systems without resolvconf being installed.

grtz,
brabo.

---

### Post by Silverboy on 2009-06-08
> **brabo said:**
> it works fine on my systems without resolvconf being installed.

grtz,
brabo.

Sorry, but on my laptop if I append the line **dns-nameservers 208.67.222.222 208.67.220.220** on /etc/network/interfaces, remove the /etc/resolv.conf and type **sudo /etc/init.d/networking restart** I have this error:
```

rino@Antares:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...grep: /etc/resolv.conf: No such file or directory
grep: /etc/resolv.conf: No such file or directory
                                                                                                               [ OK ]
rino@Antares:~$

```

Without the resolvconf package your method doesn't work (and with the "resolvconf", the problem persists). I'm starting to think that this is not a setting problem of the dnsserver but a kind of kernel bug

---

### Post by brabo on 2009-06-08
i just see that that i have in interfaces dns servers that aren't used.
it seems the dns address in /etc/resolv.conf is the active one.
i missed that before, sorry!
so if you put both addresses each on a line in that file it should work.
hopefully.. ^^

grtz,
brabo.

---

### Post by Silverboy on 2009-06-08
> **brabo said:**
> 
...
i missed that before, sorry!

Don't worry! :D

> **brabo said:**
> 
so if you put both addresses each on a line in that file it should work.
hopefully.. ^^

grtz,
brabo.

sorry, but I don't understand. Should I change the /etc/resolv.conf file?

Are you sure that my problem is a dns-server setting problem? I'm not sure is it, because with apt-get and kpackagekit Kub resolves the urls, so it seems kub "knows" who are the dns server...

---

### Post by brabo on 2009-06-08
i kinda think it is a dns problem, since when you browse to google's ip address it works, and with the url it doesn't.

i think you should recreate the resolv.conf file and put the dns server addresses in it like:

208.67.222.222
208.67.220.220

then restart networking and see if it works out.

grtz,
brabo.

---

### Post by Silverboy on 2009-06-08
I had tried different configuration of resolv.conf:
```
208.67.222.222
 208.67.220.220
``````
nameserver
208.67.222.222
  nameserver
208.67.220.220
```but the only one that works is the one in my first post.

> **brabo said:**
> i kinda think it is a dns problem, since when you browse to google's ip address it works, and with the url it doesn't.
...
Yes, but we shouldn't forget that the urls' resolution works with apt-get, while it doesn't work if I use one of the above configuration of resolv.conf. I believe is a dns problem too, but I don't believe the problem is resolv.conf. Probably, we should see in a different direction 

rino

---

### Post by brabo on 2009-06-08
hm.. weird.. with me, it's just one ip address in the resolv.conf file and it works as well.

but that aside, you do have a valid point about apt. i would further dare to speculate that the problem isn't in your interfaces file either.

what is is eludes me at this time.

i hope someone else passes by who has more insight so you can be helped.

grtz!
brabo.

---

### Post by Silverboy on 2009-06-08
don't worry and thanks a lot for your help! ):P

---

### Post by superprash2003 on 2009-06-09
are you sure you are able to ping?? post output of the pings of any external ip..

---

### Post by Silverboy on 2009-06-09
> **superprash2003 said:**
> are you sure you are able to ping?? post output of the pings of any external ip..

Yes, I'm sure:
```

rino@Antares:~$ ping 209.85.171.100
PING 209.85.171.100 (209.85.171.100) 56(84) bytes of data.
64 bytes from 209.85.171.100: icmp_seq=1 ttl=229 time=242 ms
64 bytes from 209.85.171.100: icmp_seq=2 ttl=229 time=265 ms
64 bytes from 209.85.171.100: icmp_seq=3 ttl=229 time=256 ms
64 bytes from 209.85.171.100: icmp_seq=4 ttl=229 time=256 ms
64 bytes from 209.85.171.100: icmp_seq=5 ttl=229 time=251 ms
^C
--- 209.85.171.100 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 242.821/254.541/265.770/7.522 ms
rino@Antares:~$ ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=45 time=100 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=45 time=98.3 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=45 time=100 ms
64 bytes from 208.67.222.222: icmp_seq=4 ttl=45 time=91.6 ms
64 bytes from 208.67.222.222: icmp_seq=5 ttl=45 time=89.9 ms
^C
--- 208.67.222.222 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 89.955/96.152/100.639/4.481 ms
 

```Of course, I stopped the pings with CTRL+C. Besides, I can update the package list and install new softare too, but I can't do anything.
```

rino@Antares:~$ sudo apt-get update
Hit http://it.archive.ubuntu.com jaunty Release.gpg
Get:1 http://security.ubuntu.com jaunty-security Release.gpg [189B]                        
Ign http://security.ubuntu.com jaunty-security/main Translation-it                          
Ign http://security.ubuntu.com jaunty-security/restricted Translation-it                    
Ign http://security.ubuntu.com jaunty-security/universe Translation-it                      
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-it                    
Get:2 http://security.ubuntu.com jaunty-security Release [49,6kB]                           
Hit http://it.archive.ubuntu.com jaunty/main Translation-it                                 
Hit http://it.archive.ubuntu.com jaunty/restricted Translation-it                            
Hit http://it.archive.ubuntu.com jaunty/universe Translation-it                                 
Get:3 http://security.ubuntu.com jaunty-security/main Packages [28,3kB]                         
Hit http://it.archive.ubuntu.com jaunty/multiverse Translation-it                               
Get:4 http://it.archive.ubuntu.com jaunty-updates Release.gpg [189B]                             
Get:5 http://security.ubuntu.com jaunty-security/restricted Packages [14B]                       
Get:6 http://security.ubuntu.com jaunty-security/main Sources [8965B]                                            
Get:7 http://security.ubuntu.com jaunty-security/restricted Sources [14B]                                        
Get:8 http://security.ubuntu.com jaunty-security/universe Packages [9226B]                                       
Get:9 http://security.ubuntu.com jaunty-security/universe Sources [1941B]                                          
Get:10 http://security.ubuntu.com jaunty-security/multiverse Packages [14B]                                          
Get:11 http://security.ubuntu.com jaunty-security/multiverse Sources [14B]                                           
Ign http://it.archive.ubuntu.com jaunty-updates/main Translation-it                                                  
Ign http://it.archive.ubuntu.com jaunty-updates/restricted Translation-it                                            
Ign http://it.archive.ubuntu.com jaunty-updates/universe Translation-it                                              
Ign http://it.archive.ubuntu.com jaunty-updates/multiverse Translation-it                                            
Hit http://it.archive.ubuntu.com jaunty Release                                                                      
Get:12 http://it.archive.ubuntu.com jaunty-updates Release [49,6kB]                                                  
Hit http://it.archive.ubuntu.com jaunty/main Packages                                                                
Hit http://it.archive.ubuntu.com jaunty/restricted Packages                                                          
Hit http://it.archive.ubuntu.com jaunty/main Sources                                                                 
Hit http://it.archive.ubuntu.com jaunty/restricted Sources                                                           
Hit http://it.archive.ubuntu.com jaunty/universe Packages                                                            
Hit http://it.archive.ubuntu.com jaunty/universe Sources                                                             
Hit http://it.archive.ubuntu.com jaunty/multiverse Packages                                                          
Hit http://it.archive.ubuntu.com jaunty/multiverse Sources                                                           
Get:13 http://it.archive.ubuntu.com jaunty-updates/main Packages [69,6kB]                                                                                                           
Get:14 http://it.archive.ubuntu.com jaunty-updates/restricted Packages [14B]                                                                                                        
Get:15 http://it.archive.ubuntu.com jaunty-updates/main Sources [22,7kB]                                                                                                            
Get:16 http://it.archive.ubuntu.com jaunty-updates/restricted Sources [14B]                                                                                                         
Get:17 http://it.archive.ubuntu.com jaunty-updates/universe Packages [19,9kB]                                                                                                       
Get:18 http://it.archive.ubuntu.com jaunty-updates/universe Sources [5564B]                                                                                                         
Get:19 http://it.archive.ubuntu.com jaunty-updates/multiverse Packages [675B]                                                                                                       
Get:20 http://it.archive.ubuntu.com jaunty-updates/multiverse Sources [639B]                                                                                                        
Scaricato 267kB in 7s (37,2kB/s)                                                                                                                                                    
Lettura della lista dei pacchetti in corso... Fatto                                                                                                                                 
rino@Antares:~$ host www.google.com                                                                                                                                                 
;; connection timed out; no servers could be reached    

```

---

### Post by superprash2003 on 2009-06-10
post output of **sudo iptables -L** from the terminal

---

### Post by Silverboy on 2009-06-10
```
rino@Antares:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
 

```

---

### Post by superprash2003 on 2009-06-11
go to system->admin->software sources and under Download from , select Main server , if still doesnt work , select BEST SERVER under OTHER

---

### Post by Silverboy on 2009-06-11
Nothing, I have tried with "MAIN SERVER" and the problem persists. I have tried with "BEST SERVER" too, but KpackageKit seems to crash. 

I'm thinking: Could my problem be a bug dued to a bad IPv4 and IPv6 addresses management? I had this idea seeing my **ifconfig **output, where my eth0 have both inet and inet6 address.

---

### Post by Silverboy on 2009-06-11
Usually, I try to solve problems considering the worst case (this is the explanation of my previous post :)). 

Trying to reconsidering my problem, I thought that Firefox, Konqueror, Akregator and KPackageKit should have the same way to resolve the urls and, accordingly, my DNS problem is misleading.

So, I have focused on the real differences in these programs and I have concluded that the only difference is that KPackageKit is used with administrator privileges! 
Infact, If I type **sudo konqueror**, I can surf on internet! (I can access to DNS with these applications)

Now, I know I should change some privileges, but such privileges?

---

### Post by Silverboy on 2009-06-11
\\:D/\\:D/\\:D/
Typing in a shell ```
sudo chmod 774 /etc/resolv.conf
``` I solved my problem.
Thanks to all for the help!:D

---

