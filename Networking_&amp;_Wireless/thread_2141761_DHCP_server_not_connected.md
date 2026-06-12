---
title: "DHCP server not connected"
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by Cavsfan on 2013-05-03
This is weird: I have Precise 12.04, Quantal 12.10, Raring 13.04, Linux Mint Cinnamon and Windows 7 installed.
Yesterday I borked an install and could only get the grub rescue prompt upon boot.
After trying many things I finally purged and reinstalled Grub on Precise with Boot-Repair from this page [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and that fixed it.

Many thanks to **YannBuntu** for that by the way.

Now Precise will not connect to the internet. All of the other installs connect fine including windows 7 but Precise will not connect no matter what I have tried.
I logged into my wireless router which is wired to my PC and when I tested the connection it gave "DHCP server not connected" error.

But, otherwise the router gave the public ip and all looked good with it but, it will not connect to the internet.

Strange how one install will not connect yet all of the others will.

Any help is muchly appreciated! :)

---

### Post by Iowan on 2013-05-03
I presume you have verified that the machine has an IP address (otherwise it couldn't log into the router). If it has one, I'm confused on why it would complain about the DHCP server. Not DHCP related, but can you ping internet sites by name or IP?

---

### Post by Cavsfan on 2013-05-03
> **Iowan said:**
> I presume you have verified that the machine has an IP address (otherwise it couldn't log into the router). If it has one, I'm confused on why it would complain about the DHCP server. Not DHCP related, but can you ping internet sites by name or IP?

Just logged into Precise and no internet what so ever. Tried to ping yahoo dot com and it failed. Have a conky that is dependent on internet for the weather and it fails when it boots up. Yes it has an ip address viewable on the conky on Quantal, Raring, Mint and so I know that it is only Precise that has the problem. Windows 7 also has no problem whatsoever with internet.

Maybe it has something to do with me purging grub and then re-installing it on Precise from a live-cd but, I cannot see what that would have to do with it.

Very perplexing to say the least. I cannot "google" answers on there as there is no internet and I totally am clueless on this one.

EDIT: It even shows the ip address when I login to the router but, when I test the connection it fails with the message in the title of the thread. And nothing internet related will connect period.

---

### Post by bab1 on 2013-05-03
No guessing; We need info to diagnose.

What is the IP address of the host?  Can you ping this address?  What is the LAN side address  of the router?  Can you ping this address?

What are the IPv4 Gateway setting for this interface in Network-Manager?  What DNS servers are you using?
Post post the output of this terminal command```
 ping -c4 91.189.94.12
```

FWIW -- The router doesn't hand out "public IP" addresses unless you specifically set this up,  Typically a home (or SOHO) router hands out "Private IP" addresses and uses NAT to manage connectivity to the wider world (e.g The Internet) through the the WAN side interface of the router.

---

### Post by Cavsfan on 2013-05-04
> **bab1 said:**
> No guessing; We need info to diagnose.

What is the IP address of the host?  Can you ping this address?  What is the LAN side address  of the router?  Can you ping this address?

What are the IPv4 Gateway setting for this interface in Network-Manager?  What DNS servers are you using?
Post post the output of this terminal command```
 ping -c4 91.189.94.12
```

FWIW -- The router doesn't hand out "public IP" addresses unless you specifically set this up,  Typically a home (or SOHO) router hands out "Private IP" addresses and uses NAT to manage connectivity to the wider world (e.g The Internet) through the the WAN side interface of the router.

The Buffalo router address is the typical 192.168.11.1 which I was able to successfully ping:
```
--- 192.168.11.1 ping statistics ---
63 packets transmitted, 63 received, 0% packet loss, time 62003ms
rtt min/avg/max/mdev = 0.572/0.725/8.486/0.985 ms
```
Had to press cntl c to get it to stop.

When I click on System info on the router is when it says "communicating" and shows the pulblic ip address. Everything looks perfectly fine at that point.
I know the public IP address as it shows on the other 3 Linux OSs conky as well as on an app on my adroid phone, but on Precise it is blank along with N/A on all of the conkywx weather info.

As you can see on this screenshot of Precise taken before the problem occurred (where it currently says 'Lol Lol Lol' prior to the Grub rescue, etc.

[IMG]http://ompldr.org/vaWE4cg/Screenshot%20from%202013-05-01.png[/IMG]

I can ping the lan ip address successfully: 192.168.11.5.

Here is the output you requested. It connects to the internet just fine.
```
cavsfan@cavsfan-desktop:~$ ping -c4 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_req=1 ttl=48 time=109 ms
64 bytes from 91.189.94.12: icmp_req=2 ttl=48 time=109 ms
64 bytes from 91.189.94.12: icmp_req=3 ttl=48 time=108 ms
64 bytes from 91.189.94.12: icmp_req=4 ttl=48 time=110 ms

--- 91.189.94.12 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 108.550/109.444/110.052/0.553 ms
```

It is when I click "check connection" on the router that it gets the "DHCP Server not detected" error.

Conky cannot get weather info, Firefox doesn't connect to any site and sudo apt-get update gets nothing but errors.

So it looks like it is connecting but just not all the way.

---

### Post by Cavsfan on 2013-05-04
Not sure if I made this clear. Only Precise has this problem. All of the other OSs in my signature have no problem whatsoever.

---

### Post by bab1 on 2013-05-04
> **Cavsfan said:**
> The Buffalo router address is the typical 192.168.11.1 which I was able to successfully ping:
```
--- 192.168.11.1 ping statistics ---
63 packets transmitted, 63 received, 0% packet loss, time 62003ms
rtt min/avg/max/mdev = 0.572/0.725/8.486/0.985 ms
```
Had to press cntl c to get it to stop.

When I click on System info on the router is when it says "communicating" and shows the pulblic ip address. Everything looks perfectly fine at that point.
I know the public IP address as it shows on the other 3 Linux OSs conky as well as on an app on my adroid phone, but on Precise it is blank along with N/A on all of the conkywx weather info.

As you can see on this screenshot of Precise taken before the problem occurred (where it currently says 'Lol Lol Lol' prior to the Grub rescue, etc.

I can ping the lan ip address successfully: 192.168.11.5.

Here is the output you requested. It connects to the internet just fine.
```
cavsfan@cavsfan-desktop:~$ ping -c4 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_req=1 ttl=48 time=109 ms
64 bytes from 91.189.94.12: icmp_req=2 ttl=48 time=109 ms
64 bytes from 91.189.94.12: icmp_req=3 ttl=48 time=108 ms
64 bytes from 91.189.94.12: icmp_req=4 ttl=48 time=110 ms

--- 91.189.94.12 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 108.550/109.444/110.052/0.553 ms
```

It is when I click "check connection" on the router that it gets the "DHCP Server not detected" error.

Conky cannot get weather info, Firefox doesn't connect to any site and sudo apt-get update gets nothing but errors.

This appears to be the case in your situation  -- The IP addressing is fine.  You have TCP/IP connectivity from 192.168.11.5 (the computer you are using) to itself, then the gateway (router -- 192.168.11.1) and also a host on the Internet ( 91.189.94.12 (ubuntuforums.org)).  

The problem appears to be a lack of DNS resolution.  I would check you settings for the name server you are using for DNS.  Conky, Firefox and APT repositories are dependent on DNS for name (FQDN) to IP address resolution.

[COLOR="#0000FF"]**Edit: **The DNS settings I'm referring to are specific to the OS you are running at any time.  They are configured at the host (computer) you are using, not the router.  The setting *may* be the routers IP address however. [/COLOR]

---

### Post by Cavsfan on 2013-05-04
> **bab1 said:**
> This appears to be the case in your situation  -- The IP addressing is fine.  You have TCP/IP connectivity from 192.168.11.5 (the computer you are using) to itself, then the gateway (router -- 192.168.11.1) and also a host on the Internet ( 91.189.94.12 (ubuntuforums.org)).  

The problem appears to be a lack of DNS resolution.  I would check you settings for the name server you are using for DNS.  Conky, Firefox and APT repositories are dependent on DNS for name (FQDN) to IP address resolution.

[COLOR=#0000FF]**Edit: **The DNS settings I'm referring to are specific to the OS you are running at any time.  They are configured at the host (computer) you are using, not the router.  The setting *may* be the routers IP address however. [/COLOR]

Thanks but, where do I go in Precise to do this?

---

### Post by bab1 on 2013-05-04
> **Cavsfan said:**
> Thanks but, where do I go in Precise to do this?
It really depends on what method the OS is using to manage you network.  It *could* be Network Manager if you are using Ubuntu.  I assume this is what you are using.  

To find NM you can look in DASH.  Type nm and the Network icon should appear.  Click on this and then select 'edit connections".  Select the interface you are using (wired or wireless).  Select the tab for IPv4 connections.  This should show you the settings.  What are all the settings listed.  At the very least what is the DNS server setting?

---

### Post by Cavsfan on 2013-05-06
> **bab1 said:**
> It really depends on what method the OS is using to manage you network.  It *could* be Network Manager if you are using Ubuntu.  I assume this is what you are using.  

To find NM you can look in DASH.  Type nm and the Network icon should appear.  Click on this and then select 'edit connections".  Select the interface you are using (wired or wireless).  Select the tab for IPv4 connections.  This should show you the settings.  What are all the settings listed.  At the very least what is the DNS server setting?

Yes, Precise is the only Linux OS that will not connect to the internet. 
Quantal Quetzal 12.10 connects just fine. 
Raring Ringtail 13.04 connects just fine. 
Linux Mint 14 connects just fine.

The network settings in Precise Pangolin 12.04.2 which _does not_ work are exactly the same as the network settings in Linux Mint 14:

[ATTACH=CONFIG]242266[/ATTACH] [ATTACH=CONFIG]242267[/ATTACH] [ATTACH=CONFIG]242268[/ATTACH]

---

### Post by bab1 on 2013-05-06
> **Cavsfan said:**
> Yes, Precise is the only Linux OS that will not connect to the internet. ...

Ah but it does connect to the internet.  This proves the point```

cavsfan@cavsfan-desktop:~$ ping -c4 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_req=1 ttl=48 time=109 ms
64 bytes from 91.189.94.12: icmp_req=2 ttl=48 time=109 ms
64 bytes from 91.189.94.12: icmp_req=3 ttl=48 time=108 ms
64 bytes from 91.189.94.12: icmp_req=4 ttl=48 time=110 ms

--- 91.189.94.12 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 108.550/109.444/110.052/0.553 ms
```...this is a successful ping of ubuntuforums.org.  See at the bottom where it shows 4 packets sent and 4 received.  What you don't have is successful DNS domain name resolution (e.g. the mapping of 91.189.94.12 to ubuntuforums.org).  What results do you get from this```
ping -c4 ubuntuforums.org
```

I wonder if your problems are in the DHCP configuration of your router getting messed up from you *borking* adventure as mentioned in you OP.  Usually the DHCP server is setup to provide you  with an IP address and the correct address of a designated DNS server.

We can see what address Precise is using with this command```

nslookup ubuntuforums.org

```... here is what I get when using nslookup 
```
nslookup ubuntuforums.org
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	ubuntuforums.org
```...the Server:   8.8.8.8 is Google's DNS public used DNS server.  We are looking up the IP address/ domain name pair I talked about above.

---

### Post by Cavsfan on 2013-05-08
> **bab1 said:**
> Ah but it does connect to the internet.  This proves the point```

cavsfan@cavsfan-desktop:~$ ping -c4 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
64 bytes from 91.189.94.12: icmp_req=1 ttl=48 time=109 ms
64 bytes from 91.189.94.12: icmp_req=2 ttl=48 time=109 ms
64 bytes from 91.189.94.12: icmp_req=3 ttl=48 time=108 ms
64 bytes from 91.189.94.12: icmp_req=4 ttl=48 time=110 ms

--- 91.189.94.12 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 108.550/109.444/110.052/0.553 ms
```...this is a successful ping of ubuntuforums.org.  See at the bottom where it shows 4 packets sent and 4 received.  What you don't have is successful DNS domain name resolution (e.g. the mapping of 91.189.94.12 to ubuntuforums.org).  What results do you get from this```
ping -c4 ubuntuforums.org
```

I wonder if your problems are in the DHCP configuration of your router getting messed up from you *borking* adventure as mentioned in you OP.  Usually the DHCP server is setup to provide you  with an IP address and the correct address of a designated DNS server.

We can see what address Precise is using with this command```

nslookup ubuntuforums.org

```... here is what I get when using nslookup 
```
nslookup ubuntuforums.org
Server:        8.8.8.8
Address:    8.8.8.8#53

Non-authoritative answer:
Name:    ubuntuforums.org
```...the Server:   8.8.8.8 is Google's DNS public used DNS server.  We are looking up the IP address/ domain name pair I talked about above.

```
cavsfan@cavsfan-desktop:~$ ping -c4 ubuntuforums.org 
ping: unknown host ubuntuforums.org 
cavsfan@cavsfan-desktop:~$ 
```

```
cavsfan@cavsfan-desktop:~$ nslookup ubuntuforums.org 
;; connection timed out; no servers could be reached 
cavsfan@cavsfan-desktop:~$  
```

However I can ping 8.8.8.8:
```
cavsfan@cavsfan-desktop:~$ ping -c4 8.8.8.8 
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data. 
64 bytes from 8.8.8.8: icmp_req=1 ttl=45 time=25.9 ms 
64 bytes from 8.8.8.8: icmp_req=2 ttl=45 time=27.0 ms 
64 bytes from 8.8.8.8: icmp_req=3 ttl=45 time=24.4 ms 
64 bytes from 8.8.8.8: icmp_req=4 ttl=45 time=27.5 ms 
 
--- 8.8.8.8 ping statistics --- 
4 packets transmitted, 4 received, 0% packet loss, time 3003ms 
rtt min/avg/max/mdev = 24.493/26.248/27.514/1.152 ms 

```
I can ping my public ip WAN address as well as my LAN address but, still cannot connect with firefox or terminal.

I was getting this error:
```
cavsfan@cavsfan-desktop:~$ sudo restart network-manager 
[COLOR=#ff0000]sudo: unable to resolve host cavsfan-desktop [/COLOR]
[sudo] password for cavsfan:  
network-manager start/running, process 3260 

```

I had populated my hosts file (/etc/hosts) with this [http://someonewhocares.org/hosts/](http://someonewhocares.org/hosts/)
But, I restored it to original but somehow my hosts file contained this afterwards:
```
127.0.0.1 localhost 
127.0.1.1 [COLOR=#ff0000]ubuntu[/COLOR]
 
# The following lines are desirable for IPv6 capable hosts 
::1 ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts
```

So I changed the 2nd line to match /etc/hostname which is "cavsfan-desktop" and that got rid of the error [COLOR=#ff0000]sudo: unable to resolve host cavsfan-desktop [/COLOR]
```
127.0.0.1 localhost 
127.0.1.1 cavsfan-desktop 
 
# The following lines are desirable for IPv6 capable hosts 
::1 ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts
```

When I enter sudo apt-get update I get these errors:
```
Err http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libnm-gtk-common all 0.9.4.1-0ubuntu2.3 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname) 
Err http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libnm-gtk0 amd64 0.9.4.1-0ubuntu2.3 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname) 
Err http://us.archive.ubuntu.com/ubuntu/ precise-updates/main network-manager-gnome amd64 0.9.4.1-0ubuntu2.3 
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname) 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/libnm-gtk-common_0.9.4.1-0ubuntu2.3_all.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname) 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/libnm-gtk0_0.9.4.1-0ubuntu2.3_amd64.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname) 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.9.4.1-0ubuntu2.3_amd64.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname) 
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

I don't have dnsmasq installed (default I believe) but dnsmasq-base is and when I entered sudo dnsmasq -h (--no-hosts) it returned this error:
```
dnsmasq: failed to create listening socket for port 53: Address already in use
```

There are 3 files waiting to be updated and one of them is network-manager-gnome, but can't get the update.

I've googled everything and can only paste stuff to a text file and while in Precise, then update it when in Raring.

---

### Post by Cavsfan on 2013-05-08
Oh, I also get "[SIZE=3][COLOR=red]**DHCP Server not detected"**[/COLOR][/SIZE] when checking the connection on my Buffalo Router while logged into Raring and Windows 7 as well.
But, only in Precise Firefox does not go anywhere; all of the other 4 OSs do not have any problem connecting to anything.

EDIT: I just checked it again in Raring and it did not get any error whatsoever.

---

### Post by pangeh on 2013-05-08
Hi Bab1,

As Cavsfan pointed out it could be your DNS settings on the problem machine. If you go into network manager and select the network your using (there are tabs for wired network, wireless etc) then press edit. 

In the pop up box that appears click the IPv4 tab, what settings are listed here? Also is the ubuntu box your using causing you trouble set for DHCP or a static IP address?

Just for clarity your set up is:

- You have a router which connects to the internet and also serves as DNS and the DHCP server for your local network
- You have 4 machines which connect via the router to the internet
- 1 of the machines, the Ubuntu 12.04 machine no longer connects to the internet

---

### Post by pangeh on 2013-05-08
oops, please ignore my last post as did not read the 2nd page of this thread.

But for a test - you could change your Ubuntu machine to use static address settings so that you manually enter your DNS, IP, Gateway etc and see what results you get. This would help identify what is causing the issue. But it sounds like a DNS issue as pointed out.

---

### Post by bab1 on 2013-05-08
> **Cavsfan said:**
> 
I don't have dnsmasq installed (default I believe) but dnsmasq-base is and when I entered sudo dnsmasq -h (--no-hosts) it returned this error:
```
dnsmasq: failed to create listening socket for port 53: Address already in use
```
Let's see what process is listening at port 53.  What's the output of ```
sudo netstat -tuanp|grep 53
```
> 
There are 3 files waiting to be updated and one of them is network-manager-gnome, but can't get the update.

I've googled everything and can only paste stuff to a text file and while in Precise, then update it when in Raring.
I'm not sure what you are doing here.

---

### Post by bab1 on 2013-05-08
> **pangeh said:**
> oops, please ignore my last post as did not read the 2nd page of this thread.

But for a test - you could change your Ubuntu machine to use static address settings so that you manually enter your DNS, IP, Gateway etc and see what results you get. This would help identify what is causing the issue. But it sounds like a DNS issue as pointed out.

Let's not start over at the beginning again.  It *is* a DNS problem.

---

### Post by matt_symes on 2013-05-08
Hi

Some more diagnostic information for you to post as well as from the last post.

```
ps aux | grep dns
```

```
dpkg -l | grep dns
```

```
ls -ld /etc/dhcp*
```

```
cat /etc/dhcp/dhclient.conf
```

```
cat /etc/NetworkManager/NetworkManager.conf
```

Did you follow any other random guides from the Internet ? 

If you did then please post the links here.

Kind regards

---

### Post by The Cog on 2013-05-08
Can I add to that list of info we would like to see please? It would help to see the output of these two commands:
```
sudo netstat -lnpu
cat /etc/resolv.conf
```

---

### Post by Cavsfan on 2013-05-08
> **bab1 said:**
> I'm not sure what you are doing here.

What I am doing as there are no other alternatives is copy the text from this thread into a gedit file and save that on my USB drive, 
then login to Precise with no internet bring up the text file try whatever you have suggested and copy and paste that to the text file.
Then reboot into Raring and open up that text file and copy it and paste it into this thread.

Thanks for your help. I will try that and report back.

Actually **matt_symes**, it was not a random guide. I got it from this forum although it was not real recent. 
[COLOR="#0000FF"]It all worked just fine too until a week or so ago when I was installing Debian Squeeze and thought it took a wrong turn and I pressed reset on my PC and that caused this problem.[/COLOR]

Here is the post I used to add the hosts file and while it is dated 2006, it still worked [http://ubuntuforums.org/showthread.php?t=241460](http://ubuntuforums.org/showthread.php?t=241460)

**pangeh**, as you can see from my signature, I have 5 operating systems installed on this PC; they all connect to the internet just fine except Precise.
It connects as in ping but, Firefox and Ubuntu cannot.

I will reboot into Precise and try all of these commands and report back as soon as I can.
Thanks!

---

### Post by matt_symes on 2013-05-08
Hi
> 
#These may be on one line or multiple lines
127.0.0.1       localhost 
127.0.0.1       Ubuntu  **# Change Ubuntu to your hostname**

The guide did specify that Ubuntu should be changed to your host name. That is why you had one error.

If you post the diagnostic information asked for then, hopefully, we can get your system back up and running.

Kind regards

---

### Post by Cavsfan on 2013-05-08
Here is the output of all the commands:

```
cavsfan@cavsfan-desktop:~$ sudo netstat -tuanp|grep 53 
[sudo] password for cavsfan:  
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1233/dnsmasq     
udp        0      0 127.0.0.1:53            0.0.0.0:*                           1233/dnsmasq     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           851/avahi-daemon: r 
udp        0      0 0.0.0.0:55336           0.0.0.0:*                           851/avahi-daemon: r 
udp6       0      0 :::5353                 :::*                                851/avahi-daemon: r 

```

```
cavsfan@cavsfan-desktop:~$ ps aux | grep dns 
nobody    1233  0.0  0.0  28820  1292 ?        S    12:59   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.0.1 --conf-file=/var/run/nm-dns-dnsmasq.conf --cache-size=0 --proxy-dnssec 
cavsfan   3135  0.0  0.0   9388   924 pts/1    S+   13:23   0:00 grep --color=auto dns 
```

```
cavsfan@cavsfan-desktop:~$ dpkg -l | grep dns 
ii  dnsmasq-base                                  2.59-4ubuntu0.1                                     Small caching DNS proxy and DHCP/TFTP server 
ii  dnsutils                                      1:9.8.1.dfsg.P1-4ubuntu0.6                          Clients provided with BIND 
rc  libdns64                                      1:9.7.0.dfsg.P1-1ubuntu0.8                          DNS Shared Library used by BIND 
ii  libdns81                                      1:9.8.1.dfsg.P1-4ubuntu0.6                          DNS Shared Library used by BIND 
ii  libkdnssd4                                    4:4.8.5-0ubuntu0.1                                  DNS-SD Protocol Library for the KDE Platform 
ii  libnss-mdns                                   0.10-3.2                                            NSS module for Multicast DNS name resolution 
```

```
cavsfan@cavsfan-desktop:~$ ls -ld /etc/dhcp* 
drwxr-xr-x 4 root root 4096 Feb 14 15:12 /etc/dhcp 
drwxr-xr-x 4 root root 4096 Sep 19  2012 /etc/dhcp3
```

```
cavsfan@cavsfan-desktop:~$ cat /etc/dhcp/dhclient.conf 
# Configuration file for /sbin/dhclient, which is included in Debian's 
#    dhcp3-client package. 
# 
# This is a sample configuration file for dhclient. See dhclient.conf's 
#    man page for more information about the syntax of this file 
#    and a more comprehensive list of the parameters understood by 
#    dhclient. 
# 
# Normally, if the DHCP server provides reasonable information and does 
#    not leave anything out (like the domain name, for example), then 
#    few changes must be made to this file, if any. 
# 
 
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8; 
 
send host-name "<hostname>"; 
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c; 
#send dhcp-lease-time 3600; 
#supersede domain-name "fugue.com home.vix.com"; 
#prepend domain-name-servers 127.0.0.1; 
request subnet-mask, broadcast-address, time-offset, routers, 
    domain-name, domain-name-servers, domain-search, host-name, 
    netbios-name-servers, netbios-scope, interface-mtu, 
    rfc3442-classless-static-routes, ntp-servers; 
#require subnet-mask, domain-name-servers; 
#timeout 60; 
#retry 60; 
#reboot 10; 
#select-timeout 5; 
#initial-interval 2; 
#script "/etc/dhcp3/dhclient-script"; 
#media "-link0 -link1 -link2", "link0 link1"; 
#reject 192.33.137.209; 
 
#alias { 
#  interface "eth0"; 
#  fixed-address 192.5.5.213; 
#  option subnet-mask 255.255.255.255; 
#} 
 
#lease { 
#  interface "eth0"; 
#  fixed-address 192.33.137.200; 
#  medium "link0 link1"; 
#  option host-name "andare.swiftmedia.com"; 
#  option subnet-mask 255.255.255.0; 
#  option broadcast-address 192.33.137.255; 
#  option routers 192.33.137.250; 
#  option domain-name-servers 127.0.0.1; 
#  renew 2 2000/1/12 00:00:01; 
#  rebind 2 2000/1/12 00:00:01; 
#  expire 2 2000/1/12 00:00:01; 
#}
```

```
cavsfan@cavsfan-desktop:~$ cat /etc/NetworkManager/NetworkManager.conf 
 
[main] 
plugins=ifupdown,keyfile 
dns=dnsmasq 
 
no-auto-default=00:24:21:51:21:3A, 
 
[ifupdown] 
managed=false
```

sudo netstat -lnpu 
(see above the 1st bit of text)

```
cavsfan@cavsfan-desktop:~$ cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver 127.0.1.1 
search cfl.rr.com
```

Thanks for the help! :)

---

### Post by Cavsfan on 2013-05-08
After trying these same commands on Raring which does connect w/o a problem I see this:
```
cavsfan@cavsfan-MS-7529:~$ cat /etc/dhcp/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

#send host-name "andare.fugue.com";
send host-name = gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    dhcp6.name-servers, dhcp6.domain-search,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers,
    [COLOR=#ff0000]dhcp6.fqdn, dhcp6.sntp-servers;[/COLOR]
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```
The red line does appear in Raring but, does not appear on Precise.

```

cavsfan@cavsfan-desktop:~$ cat /etc/NetworkManager/NetworkManager.conf    
[main]  
plugins=ifupdown,keyfile  
dns=dnsmasq    

[COLOR=#ff0000]no-auto-default=00:24:21:51:21:3A, [/COLOR]   

[ifupdown]  managed=false
```

The red line above does appear in Precise but, does not appear on Raring.
That is about the extent of my 2 cents.

---

### Post by bab1 on 2013-05-09
A couple of thoughts come to mind...

> [COLOR="#0000FF"]It all worked just fine too until a week or so ago when I was installing Debian Squeeze and thought it took a wrong turn and I pressed reset on my PC and that caused this problem.[/COLOR]

The problem may never be fixed by update configuration files.  As you stated the OS is "borked"  The efficient way would be to reinstall 12.04.

That being said there are some inconstancies.  The local DNS server (dnsmasq-base) is located at 127.0.0.1 ```
udo netstat -tuanp|grep 53 
[sudo] password for cavsfan:  
tcp        0      0 [COLOR="#FF0000"]127.0.0.1[/COLOR]:53            0.0.0.0:*               LISTEN      1233/dnsmasq     
udp        0      0 [COLOR="#FF0000"]127.0.0.1[/COLOR]:53            0.0.0.0:*                           1233/dnsmasq    
```...but the resolv.conf shows something slightly different```
cat /etc/resolv.conf 
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8) 
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN 
nameserver [COLOR="#800080"]127.0.1.1[/COLOR] 
```

This should be set by the dhcp3 configuration file```
cat /etc/dhcp/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

#send host-name "andare.fugue.com";
send host-name = gethostname();
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
[COLOR="#008000"]#prepend domain-name-servers 127.0.0.1;[/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    dhcp6.name-servers, dhcp6.domain-search,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers,
    dhcp6.fqdn, dhcp6.sntp-servers;
#require subnet-mask, domain-name-servers;
```...but this is commented out.  It may use a default or this configuration file is not used at all.  It could be that the working dhcp server is dnsmasq-base and the config is the /etc/hosts file which does show 127.0.1.1```
127.0.0.1 localhost 
[COLOR="#FF8C00"]**127.0.1.1 cavsfan-desktop**[/COLOR]
```

But this also may be a moot point as 127.0.1.1 and 127.0.0.1 are in fact the same interface (the loopback (lo)).

I think I would start by reconfiguring Network Manager ```
sudo dpkg-reconfigure resolvconf
```...see [**[COLOR="#FF8C00"]here[/COLOR]**]("http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf") for information on the above command.  I would try changing the address  127.0.0.1 and see if you get DNS resolution.

---

### Post by Cavsfan on 2013-05-09
> **bab1 said:**
> ```
sudo dpkg-reconfigure resolvconf
```

That fixed it! :D I got into Unity to execute the above command and just gave "yes" answers and rebooted.
It fixed resolv.conf:
```
cavsfan@cavsfan-desktop:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver [COLOR=#ff0000]127.0.0.1[/COLOR]
search cfl.rr.com
```

Viola, I am back in Precise with a working internet! 

:guitar:

Thanks a lot for all of your help especially **bab1**!

Lessons learned:
1) Never press the reset button when doing an install. Do'h! :redface:
2) Never install Debian Squeeze as there are too many things to do to get it where it needs to be. It came with Iceweasal version 3.5 and it took me forever to figure out how to get it to update as Firefox does.
Then I installed a nvidia driver and the system hung. I was doing my 2nd install when this happened. Linux Mint 14 is based on Ubuntu 11.10 so it is easy to get used to or vice versa not sure.

Any way, problem solved! And I am glad because I have had that install since Lucid and upgraded from that to Precise. Would have hated to backup everything and do a clean install.

Thanks again **bab1**!

---

### Post by The Cog on 2013-05-09
> **Cavsfan said:**
> Would have hated to backup everything and do a clean install

Oh good grief! Get a backup before something unfortunate happens. Hard drive failures and installer screw-ups usually happen without adequate warning.

---

### Post by Cavsfan on 2013-05-09
> **The Cog said:**
> Oh good grief! Get a backup before something unfortunate happens. Hard drive failures and installer screw-ups usually happen without adequate warning.

It's not that I couldn't do the clean install it's just that I have done enough of them that I was glad to get out of needing to do one this time. :)

---

### Post by bab1 on 2013-05-09
> **Cavsfan said:**
> It's not that I couldn't do the clean install it's just that I have done enough of them that I was glad to get out of needing to do one this time. :)

I think @The Cog is reacting to your comment > Would have hated to backup everything....

I would ask; Do you have your data backed up on a regular basis.  I do, but some folks don't and then complain if the OS becomes, as you say,  *borked*.  I only backup a few config files,  but I do document everything that I do.  What did you mean by your comment above?

---

### Post by Cavsfan on 2013-05-10
> **bab1 said:**
> I think @The Cog is reacting to your comment 

I would ask; Do you have your data backed up on a regular basis.  I do, but some folks don't and then complain if the OS becomes, as you say,  *borked*.  I only backup a few config files,  but I do document everything that I do.  What did you mean by your comment above?

I have a 1TB FANTOM USB drive that I backup to.

---

### Post by Cavsfan on 2013-05-10
Also noticed that my swap file was not being mounted. Looked in fstab and it did not match the UUID of the swapfile.
Just editted it and rebooted and it's good now.

---

### Post by bab1 on 2013-05-10
> **Cavsfan said:**
> Also noticed that my swap file was not being mounted. Looked in fstab and it did not match the UUID of the swapfile.
Just editted it and rebooted and it's good now.

You have to wonder what *other* subtle destruction has gone on since you hit the reset button.  ;-)

---

### Post by Cavsfan on 2013-05-10
> **bab1 said:**
> You have to wonder what *other* subtle destruction has gone on since you hit the reset button.  ;-)

Yup. Haven't seen anything unfixable except the internet thingie. Which is now fixed.
Not too worried though if this system holds up, which it looks like it will, this will be the *first time* I ever upgraded from one version to another (an LTS to and LTS).
I have always done clean installs prior to this time. I will never touch opensuse or debian again though that is for sure. Definitely not my cup of tea so to speak.
I mainly did the upgrade on Drs305's advice. He said he always did LTS to LTS upgrades or else I probably would have done a clean intstall there too.

I had seen where this distro called Fuduntu was the most popular distro for 2013 so I got the iso and almost installed it.
Seen a message on it that said they were folding. Lack of money to develop. Someone was complaining about the forum already being closed.
I could not format that DVD-RW fast enough! :wink:

Guess we had better let this thread go as it is resolved. Thanks again **bab1** for the **sudo dpkg-reconfigure resolvconf** command! Saved me!
Peace be unto you. :)

---

