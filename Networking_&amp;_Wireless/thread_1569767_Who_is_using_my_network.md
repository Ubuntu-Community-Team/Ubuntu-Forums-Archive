---
title: "Who is using my network ?"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by kema_u on 2010-09-07
Hi!
My wireless has not a password and everybody can use it here in the area i am. But we need to see who are using our wireless. I check every time from browser from modem interface but this is not a good idea. I need to look it every time and updated. Is there any application which shows me who is using my internet (wireless) with computer-name, ip, and mac id as i can see it from mode interface ?

Thanks!

---

### Post by BkkBonanza on 2010-09-07
If your wifi router has a telnet/ssh interface it may be fairly easy to use a script to monitor the dhcp leases. What make/model wifi do you have?

Also you can automate the web page retrieval processing in a similar way. It just depends how much effort you want to put into doing it. I know it could be done in a few lines in python/php/perl. But I'm not aware of a gui type tool that will do this - and each model wifi tends to be different in how they present the info.

Do you just want to log the data or have it show on screen real time?

Some devices have snmp but I'm not sure how much info you can get from that.

---

### Post by wesleybailey on 2010-09-07
This could be accomplished from command line with nmap. It is a powerful network security tool. That can be used in this case.

Install command-line nmap
```
sudo apt-get install nmap
```

or install graphical nmap
```
sudo apt-get install nmapfe
```

Once nmap is installed, you can scan for all the computers on your subnets with this command

```
nmap -sP 192.168.1.1/24
```

and it would output something like this
```

Starting Nmap 4.53 ( http://insecure.org ) at 2008-03-15 12:51 GMT Standard Time

Host 192.168.1.1 appears to be up.
MAC Address: 00:19:E0:66:06:D0 (Router)
Host 192.168.1.2 appears to be up.
Host 192.168.1.3 appears to be up.
MAC Address: 00:1B:24:DE:AB:26 (Computer)
Host 192.168.1.4 appears to be up.
MAC Address: 00:90:F5:61:25:4F (CO.)
Host 192.168.1.5 appears to be up.
MAC Address: 00:0F:B0:F0:FE:BA (Comp)
Host 192.168.1.6 appears to be up.
MAC Address: 00:16:D3:FC:6B:83 (Comp)
Host 192.168.1.7 appears to be up.
MAC Address: 00:1D:60:EC:6A:0E (Computer 9)
Host 192.168.1.8 appears to be up.
MAC Address: 00:11:2F:1B:FE:31 (Computer 8)
Host 192.168.1.9 appears to be up.
MAC Address: 00:A0:D1:D5:93:2B (Comp 9)
Host 192.168.1.10 appears to be up.
MAC Address: 00:15:58:35:33:94 (Comp 10)
Nmap done: 256 IP addresses (10 hosts up) scanned in 42.156 seconds

```


Latest Tutorial: [open source convert .uif to .iso]("http://wesleybailey.com/articles/uif-to-iso-converter")

---

### Post by kema_u on 2010-09-08
BkkBonaza i want to show the data real time . I think it is not important the router that i have. At least for this (simple) situation nmap can do that.

wesleybailey the output from nmap its true. but it is complicated. I mean there are many many people who use our wireless. It is really needed a simple output. Also client name is important. 

For example this would be nice : [http://yfrog.com/eltlwr741n1283934656126p](http://yfrog.com/eltlwr741n1283934656126p)

---

### Post by BkkBonanza on 2010-09-08
nmap works for this as long as the user doesn't want to avoid being seen.

The -sP option works as long as the user doesn't drop ICMP pkts.
You may want to use -sS or -sT with -PN (thought this will run slower) or some other choice depending on what you find works best.

You can reformat the output from nmap with a pipe to awk or sed to break it down to simpler results. This will take a bit of figuring out but will work.

You probably aren't going to sit there watching all day so it may make more sense to log the output for later parsing.

eg. 

**while 1; do nmap -sP 192.168.1.1/24 >> wifi-user.log; sleep 60; done**

Which repeats once a minute. Add a & if you want it to drop into the background.

Then you can view the log for some host at any time with,

**grep hostname wifi-user.log |less** 

Well, you know along that lines. Many things are possible but getting the info directly from the dhcp server leases file is more reliable.

---

### Post by kema_u on 2010-09-08
Ohh ! :( That is complicated. I just wanted a simple software with GUI. Anyway i will not do it from terminal. 

Thank for your interest.

---

