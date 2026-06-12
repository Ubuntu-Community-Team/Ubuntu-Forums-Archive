---
title: "Network connects - but does it?"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by lonewolf88 on 2011-12-07
Lubuntu 11.10; Atheros AR8132 PCI-E Ethernet card; Realtek RTL8191SE Wireless Lan 802.11n PCI-E NIC. Toshiba laptop Satellite T110.

Until this morning, no connection issues either by wireless or Ethernet.

Now, the connection indicator shows as connected for either (depending of course on which one I select to be active), and shows in case of the wireless the signal strength, but in actual fact cannot browse, get mail etc etc.

Firefox & others come up with "no network connection" sort of error.

Dual boot, no such issue with Windoze.

Would appreciate assistance getting both cards up again in Lubuntu, also some sort of idea why this happened.

And, as usual, thanks in advance!

---

### Post by BC59 on 2011-12-07
I found this post for your WIFI:

> I have a Toshiba Satellite L505 and here is what worked for me: run terminal and type 
"sudo apt-get install ndisgtk" and after that is done go here and get the win2k driver.
Then I just unzipped the driver file into the download file. Then I clicked 
system-administration-windows wireless driver, and searched for
for downloads - rtl8191 (the file that you unzipped)-91_92_SE_Driver-win2k-net8192se.inf 
and click install and close. Worked for me hope it works for you! I had to use WPA Personal
and tkip algorithms to make it all work, but it is working good for me.

---

### Post by marinara on 2011-12-07
activate your wired connection,
do first line, and the second from terminal
$ sudo dhclient -r

 $ sudo dhclient 

try pinging the router also.

any info you can provide will help

---

### Post by BC59 on 2011-12-07
> **marinara said:**
> activate your wired connection,
do first line, and the second from terminal
$ sudo dhclient -r

 $ sudo dhclient 

try pinging the router also.

any info you can provide will help

It's better to start your own thread and provide more information about your problem, specifications about your computer, the OS you installed etc.

---

### Post by lonewolf88 on 2011-12-07
> **marinara said:**
> activate your wired connection,
do first line, and the second from terminal
$ sudo dhclient -r

 $ sudo dhclient 

try pinging the router also.

any info you can provide will help

Thanks for the help.

no response from first line, second line comes back RTNETLINK.  Answer:  File exists.

Didn't ping the router, as not sure how to do this (Help accepted 
 :D ) but issue now also happening at other locations, not only on wireless but also wired.  :confused:

---

### Post by lonewolf88 on 2011-12-07
Apologies, too early in the morning!  Did some research, running ifconfig shows all RX & TX as errors, and I can ping the router ok.

On reflection, what happened yesterday was that I had to rush to catch a flight, the laptop had been on all night, and was locked up in a screensaver, no response.  I had to press the on/off key to shut down.  Maybe this caused the issue?

---

### Post by marinara on 2011-12-08
please explain "happening at other locations"

---

### Post by marinara on 2011-12-08
does your laptop have a button to turn networking off?

---

### Post by lonewolf88 on 2011-12-09
> **marinara said:**
> please explain "happening at other locations"

I travel extensively.  Same issue at multiple locations - 'doze networking works both wired & wireless, Lubuntu says it is connected, but somehow isn't.

At home at present, again same issue - posting this through Windoze.

---

### Post by lonewolf88 on 2011-12-09
> **marinara said:**
> does your laptop have a button to turn networking off?

Unfortunately not, but in any case why would it work in Windoze, but not Lubuntu?

---

### Post by marinara on 2011-12-09
please post output of "sudo ifconfig"

and post your 
/etc/network/interfaces 
file.

Thanks. 
If neither of these suggest any sort of corruption, then I am out of ideas for you.

---

### Post by lonewolf88 on 2011-12-10
> **marinara said:**
> please post output of "sudo ifconfig"

and post your 
/etc/network/interfaces 
file.

Thanks. 
If neither of these suggest any sort of corruption, then I am out of ideas for you.

Thanks guys for the help!

/etc/network/interfaces reads:

auto lo
iface lo inet loopback

From ifconfig:-

eth0      Link encap:Ethernet  HWaddr 00:26:9e:59:f7:e8  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::226:9eff:fe59:f7e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:992 (992.0 B)  TX bytes:498 (498.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2140 (2.1 KB)  TX bytes:2140 (2.1 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:39:f4:2a  
          inet addr:10.1.1.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::721a:4ff:fe39:f42a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5926 (5.9 KB)  TX bytes:740 (740.0 B)
Errors showing in TX & RX packets are the problem, perhaps?

---

### Post by lonewolf88 on 2011-12-10
> **marinara said:**
> please post output of "sudo ifconfig"

and post your 
/etc/network/interfaces 
file.

Thanks. 
If neither of these suggest any sort of corruption, then I am out of ideas for you.

Doh, it is a firewall issue.

Running Gufw graphical firewall set up, allow all in, none out, except for 6881 for (cough cough) file transfers.

When I turn firewall off in Gufw, no issues.

Turn back on, same problems as before.

However Iptables reads as follows:-

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

I haven't touched the firewall set up at all, and being dumb at all of this, politely asking how to fix, please!

And wondering what has gone wrong with Gufw?

Thanks once again!

---

