---
title: "Lost the internet, could I have turned off the network interface?"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by younglemon on 2011-11-10
I have had my Ubuntu server running for more that a year and everything has worked fine. 
 
A few days ago I attempted to cancel an install operation while simultaneously attempting to adjust the keyboard position. I dropped it and in my attempts to catch it I pressed almost all the keys on the keyboard. 
 
Since that time I have not had an internet connection. I can ping other machines on the network and other machines can print, but I cannot reach the internet from the server. I do not have any available connetions from within the network connections list. I created one (both manual and DHCP) but it doesn't use them. I don't think that is what I need to do anyway though, as i didn't have to set any parameters to my wired connection previously. 
 
I think I may have somehow turned off the NIC port, is that possible? If so, how can I check and/or turn it back on again? I am on Ubuntu 11.10 Server 64. I don't know what I've done or what I'm missing. Thank you in advance for any input regarding this matter - kind regards to all.

---

### Post by RedSingularity on 2011-11-10
Well if you can ping other machines on the network from the server then its not the NIC.  Can you ping something like [www.google.com](www.google.com)

---

### Post by docbop on 2011-11-10
So you can get to your local network, but not the internet.  Can any of the other computers on your local net get to the internet?  That would mean your net is fine, so maybe you screwed your routing info.

---

### Post by RedSingularity on 2011-11-10
What is the output of:

cat /etc/network/interfaces

---

### Post by younglemon on 2011-11-10
Thank you for replying and giving input regarding my mistake.  
 
-I cannot ping [www.google.com]("http://www.google.com") - I get 'The address cannot be found'
 
-That's right, it can't be the NIC as I can ping other systems locally.  Yes, other systems can reach the internet
 
-The output of 
cat /etc/network/interfaces is as follows (no comments):
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
     address 192.168.1.103
     netmask 255.255.255.0
     network 192.168.1.0
     broadcast 192.168.1.255
     gateway 192.168.1.1
 
As I'm looking at this I wonder, do I have both static IP and DHCP specified, could that be the problem?  If so, would I simply comment out the 'auto' lines listed above?  Thank you again for your replies and input, I remain grateful.

---

### Post by RedSingularity on 2011-11-10
Auto eth0 should be there even for a static connection.

Whats the output of: route -n

---

### Post by younglemon on 2011-11-11
~$ route -n
 
Kernel IP routing table
 
Destination    Gateway Genmask     Flags Metric Ref Use Iface
 
192.168.1.0    0.0.0.0   255.255.255.0 U    0 0 0     eth0
 
192.168.122.0 0.0.0.0   255.255.255.0 U    0 0 0     vibrbr0

---

### Post by RedSingularity on 2011-11-11
Run this:

sudo route add default gw 192.168.1.1 eth0
(This is assuming 192.168.1.1 is your gateway which looks like is the case)

Then post the output of route -n again.

---

### Post by younglemon on 2011-11-12
Now it shows the following:
 
Kernel IP routing table
 
Destination Gateway Genmask Flags Metric Ref Use Iface
 
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
 
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
 
192.168.122.0 0.0.0.0 255.255.255.0 U 0 0 0 vibrbr0
 
 
Thanks much for your continued support, I remain grateful.

---

### Post by RedSingularity on 2011-11-12
No problem.  That info looks good.  Try this command:

sudo /etc/init.d/networking restart

The try pinging [www.google.com](www.google.com)

---

### Post by younglemon on 2011-11-12
The suggested command returns the following:
 
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
RTNETLINK answers: No such process
ssh stop/waiting
ssh start/running, process 24840
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
 
~$ ping [www.google.com]("http://www.google.com")
ping: unknown host [www.google.com]("http://www.google.com")
~$
 
I am starting to feel like the old Bartles & James commercials, "...thank you for your support."

---

### Post by RedSingularity on 2011-11-12
Lol.  Are your interfaces listed at all?  Does ifconfig output anything?

---

### Post by younglemon on 2011-11-12
~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:30:67:9c:f7:11 
inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::230:67ff:fe9c:f711/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:285212 errors:0 dropped:0 overruns:0 frame:0
TX packets:52032 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:20945941 (20.9 MB) TX bytes:7036221 (7.0 MB)
Interrupt:45 Base address:0x4000 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:155167 errors:0 dropped:0 overruns:0 frame:0
TX packets:155167 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:23759141 (23.7 MB) TX bytes:23759141 (23.7 MB)
 
virbr0 Link encap:Ethernet HWaddr a2:3d:9f:06:a1:76 
inet addr:192.168.122.1 Bcast:192.168.122.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
~$
 
I think the eth0 is my interface. The results of the previous command showed two of these though

---

### Post by RedSingularity on 2011-11-12
Lets try a DHCP setting to see if that gives you any sort of connectivity:

In the file /etc/network/interfaces

Comment out the lines so it looks like this:
(And add the DHCP option)

auto eth0
iface eth0 inet dhcp
     #address 192.168.1.103
     #netmask 255.255.255.0
     #network 192.168.1.0
     #broadcast 192.168.1.255
     #gateway 192.168.1.1

Then run:   sudo /etc/init.d/networking restart

and try pinging again.

---

### Post by younglemon on 2011-11-12
Ok so I did as you suggested and was sucessful pinging and can reach the internet from the browser now. The results were as follows:
 
:~$ sudo /etc/init.d/networking restart
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
Reconfiguring network interfaces...
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
Rather than invoking init scripts through /etc/init.d, use the service(
utility, e.g. service smbd reload
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(utility, e.g. reload smbd
Rather than invoking init scripts through /etc/init.d, use the service(
utility, e.g. service smbd reload
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(utility, e.g. reload smbd
ssh stop/waiting
ssh start/running, process 28013
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
[ OK ]
~$ ping [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (72.14.204.147) 56(84) bytes of data.
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=1 ttl=52 time=23.0 ms
64 bytes from iad04s01-in-f147.1e100.net (72.14.204.147): icmp_req=2 ttl=52 time=24.8 ms
 
 
So thank you for that, I am grateful. Now I'm not sure what to as far as setting back to static. Any further thoughts?

---

### Post by RedSingularity on 2011-11-13
Lets compare the new network info to the static info.  

Post the output of ifconfig again.

---

### Post by younglemon on 2011-11-13
[COLOR=black][FONT=Verdana]Sorry for not just doing that, whoops. Thank you for your perseverance :) [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The results of ifconfig are as follows:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]~$ ifconfig[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]eth0 Link encap:Ethernet HWaddr 00:30:67:9c:f7:11 [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]inet6 addr: fe80::230:67ff:fe9c:f711/64 Scope:Link[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]RX packets:9968 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]TX packets:5155 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]collisions:0 txqueuelen:1000 [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]RX bytes:7309241 (7.3 MB) TX bytes:627653 (627.6 KB)[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]Interrupt:45 Base address:0xe000 [/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]lo Link encap:Local Loopback [/FONT][/COLOR]
[FONT=Verdana][COLOR=black]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]inet6 addr: ::1/128 Scope:Host[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]RX packets:926 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]TX packets:926 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]collisions:0 txqueuelen:0 [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]RX bytes:233594 (233.5 KB) TX bytes:233594 (233.5 KB)[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]virbr0 Link encap:Ethernet HWaddr 8e:bb:66:f4:c7:e6 [/FONT][/COLOR]
[FONT=Verdana][COLOR=black]inet addr:192.168.122.1 Bcast:192.168.122.255 Mask:255.255.255.0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]UP BROADCAST MULTICAST MTU:1500 Metric:1[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]collisions:0 txqueuelen:0 [/COLOR][/FONT]
[FONT=Verdana][COLOR=black]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]~$[/FONT][/COLOR]

---

### Post by RedSingularity on 2011-11-13
Sorry for the delays:

Output of 'route -n' again.

I should have just asked for that the first time as well ;)

---

### Post by younglemon on 2011-11-14
~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 100 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
192.168.122.0 0.0.0.0 255.255.255.0 U 0 0 0 virbr0
:~$
 
Are there supposed to be two eth0 records? Should I be the one answering that? Sorry we have to go through this, thanks for doing so though. I remain grateful.

---

### Post by RedSingularity on 2011-11-14
Happy to help.  Gateway looks good.  Now edit the file again so it looks like this:
(note the network is commented out)

auto eth0
iface eth0 inet static
     address 192.168.1.103
     netmask 255.255.255.0
     #network 192.168.1.0
     broadcast 192.168.1.255
     gateway 192.168.1.1

Then run:  sudo /etc/init.d/networking restart

Then try pinging google.

---

### Post by hansdown on 2011-11-14
Good job, RedSingularity.

You rock!

---

### Post by RedSingularity on 2011-11-14
Your still out there man?!?!?!  Let me send you a PM.

---

### Post by younglemon on 2011-11-15
~$ sudo /etc/init.d/networking restart
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces... postconf: fatal: open /etc/postfix/main.cf: No such file or directory
ssh stop/waiting
ssh start/running, process 13918
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
[ OK ]
~$ ping [www.google.com]("http://www.google.com")
PING [www.l.google.com]("http://www.l.google.com") (72.14.204.99) 56(84) bytes of data.
64 bytes from iad04s01-in-f99.1e100.net (72.14.204.99): icmp_req=1 ttl=52 time=19.0 ms
64 bytes from iad04s01-in-f99.1e100.net (72.14.204.99): icmp_req=2 ttl=52 time=20.7 ms
 
And that will do it, thank you very much. I can reach the internet and the network.
 
So, what switch did I manage to flip when I pressed all keys on the keyboard, I missed it and I am still not sure what exactly happened. I think it was, as docbop mentioned early on, I screwed my routing info. Thankfully you graciously supplied the means to reset or restart the network connections. Unfortunately, there was an incorrect (or deprecated) parameter set in the interfaces file and the network was still partially removed. Do you think that closely resembels what may have happened? I wonder what shortcut keys were pressed to have caused this issue.
 
As hansdown says before me, "You rock!". If you drink beer and like a good IPA, I'd pour you a cold Hoptical Illusion (Blue Point Brewing) in a frozen glass. I remain grateful, thank you very much.

---

### Post by RedSingularity on 2011-11-15
I am not sure the dropping of the keyboard did anything.  Unless of course you had a editor open on a system file when it happened, which I doubt.  I wonder if the dropping of the keyboard and internet loss, at the same time, was just a coincidence...?  

If you lived in NY, I would take you up on that beer ;)  Anyway, I am happy to help!!  Glad we got it working.

---

### Post by younglemon on 2011-11-15
Really, how odd, so sometimes the internet can just flake out and you have to restart the connections...interesting.
 
I'm close to Atlantic City about two and a half hours south of NYC, love to buy you a beer sometime, thanks again.

---

### Post by younglemon on 2012-01-29
Hello RedSingularity,
 
   This just happened to me once again and I was able to reset it by following the steps you provided in this thread.  First I gave myself edit access to the interfaces file and commented everything so it was DHCP.  Then I restarting the network connections and was able to ping and connect.  Then I edited the file back to the way it was and once again restarted the connections and now I am once again back in business.   
 
:p Thanks much again.

---

