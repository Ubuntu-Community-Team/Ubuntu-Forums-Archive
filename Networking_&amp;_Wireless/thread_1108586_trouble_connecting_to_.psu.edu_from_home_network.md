---
title: "trouble connecting to .psu.edu from home network"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by lmm5247 on 2009-03-27
here's my issue

i can't connect to the .psu.edu domain from my laptop on my home network, but i can get on any other website. and i can get on it from a windows computer on the same home network.  and even weirder, if i go to school and try to get on the .psu.edu domain from my laptop, it works. so the problem is with my laptop on my home network and its only with the .psu.edu domain.

any ideas would be appreciated

running 8.10 with wicd

---

### Post by lmm5247 on 2009-03-29
anyone?

---

### Post by mech_tigerhawk on 2009-03-29
I'm having the same exact problem, and literally posted earlier today on this, but have yet to find a solution. Can you ping the IP address? Will pinging the domain sometimes work? What wireless card, what router?

---

### Post by lmm5247 on 2009-03-29
> **mech_tigerhawk said:**
> I'm having the same exact problem, and literally posted earlier today on this, but have yet to find a solution. Can you ping the IP address? Will pinging the domain sometimes work? What wireless card, what router?

its driving me crazy because i have to go downstairs to check my email!

system>administration>network tools>ping
     the screen just goes gray and freezes so i guess i cant ping it


wireless card
     Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


router
     d-link dir-655

---

### Post by mech_tigerhawk on 2009-03-30
Ping it from a terminal. Just run the command:
ping -c 5 146.186.15.17

This simply does the same thing as that but is a little better. 146.186.15.17 is psu.edu's IP address, -c 5 pings 5 times. Also try pinging psu.edu instead. Sometimes it would ping it, but most of the time it would just say unknown host.

I'm also assuming that it isn't hardware, because I have an Atheros card and a Netgear router, and at first I was assuming it was the crappy Netgear router.

The other thing I should point out is that it seems to be a DNS problem, but every other computer connected to the network can find PSU sites just fine, and since the router gets domains resolved from the ISP, it doesn't quite make sense that it singles out one computer.

---

### Post by BkkBonanza on 2009-03-30
Just to be clear - are you typing psu.edu or .psu.edu? The second one is an invalid name because of the leading dot. If you are typing a valid name then try a name lookup from the terminal, 

nslookup nsu.edu

If that gives a valid ip address then FF should also work. If that gives something wonky then you have a problem with DNS. If so, post your /etc/resolv.conf and  /etc/hosts file here.

---

### Post by lmm5247 on 2009-03-30
> **mech_tigerhawk said:**
> Ping it from a terminal. Just run the command:
ping -c 5 146.186.15.17

This simply does the same thing as that but is a little better. 146.186.15.17 is psu.edu's IP address, -c 5 pings 5 times. Also try pinging psu.edu instead. Sometimes it would ping it, but most of the time it would just say unknown host.

I'm also assuming that it isn't hardware, because I have an Atheros card and a Netgear router, and at first I was assuming it was the crappy Netgear router.

The other thing I should point out is that it seems to be a DNS problem, but every other computer connected to the network can find PSU sites just fine, and since the router gets domains resolved from the ISP, it doesn't quite make sense that it singles out one computer.


logan@logan-laptop:~$ ping -c 5 146.186.15.17
PING 146.186.15.17 (146.186.15.17) 56(84) bytes of data.
64 bytes from 146.186.15.17: icmp_seq=1 ttl=248 time=12.0 ms
64 bytes from 146.186.15.17: icmp_seq=2 ttl=248 time=15.7 ms
64 bytes from 146.186.15.17: icmp_seq=3 ttl=248 time=15.4 ms
64 bytes from 146.186.15.17: icmp_seq=4 ttl=248 time=13.2 ms
64 bytes from 146.186.15.17: icmp_seq=5 ttl=248 time=12.9 ms

--- 146.186.15.17 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4014ms
rtt min/avg/max/mdev = 12.060/13.884/15.760/1.447 ms
logan@logan-laptop:~$

the ping works but i still cant get onto the site =/

---

### Post by lmm5247 on 2009-03-30
> **BkkBonaza said:**
> Just to be clear - are you typing psu.edu or .psu.edu? The second one is an invalid name because of the leading dot. If you are typing a valid name then try a name lookup from the terminal, 

nslookup nsu.edu

If that gives a valid ip address then FF should also work. If that gives something wonky then you have a problem with DNS. If so, post your /etc/resolv.conf and  /etc/hosts file here.

i'm typing psu.edu (the main site) but there are also lots of other sites like:
webmail.psu.edu
cms.psu.edu
webaccess.psu.edu

that is why i left the dot on the beginning but ya i understand what you're saying heres the results of nslookup psu.edu


logan@logan-laptop:~$ nslookup psu.edu
;; Got recursion not available from 128.118.25.3, trying next server
;; Got recursion not available from 130.203.1.4, trying next server
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	psu.edu
Address: 146.186.15.17
Name:	psu.edu
Address: 146.186.16.57
Name:	psu.edu
Address: 128.118.142.105
Name:	psu.edu
Address: 128.118.142.114
Name:	psu.edu
Address: 128.118.146.130
Name:	psu.edu
Address: 128.118.146.135
Name:	psu.edu
Address: 146.186.157.8

logan@logan-laptop:~$ 


is that normal?

---

### Post by BkkBonanza on 2009-03-30
It's the same answer I get here (but different order, probably due to round robin setup at DNS).
Try posting your /etc/hosts file, or at least checking if there is anything at all in there related to psu.edu.
If you type any of the ips given by nslookup into the browser do they work correctly?
I checked the domain on opendns.com cache check and it says the result is valid.
I'm curious if one of the ips is having trouble and for some reason just your laptop is using the bad one.

btw I don't get any results about recursion not available - so not sure what's up with that.
also nslookup appears to be asking your router (192.168.0.1) which presumably is configured to ask your isp nameserver. It may be good to check just what the router is asking. If some exploit was perpetrated that poisoned the dns ip then you could be getting "bad" ips for any number of names - most worrisome being ones for banks and paypal etc.

---

### Post by lmm5247 on 2009-03-30
> **BkkBonaza said:**
> It's the same answer I get here (but different order, probably due to round robin setup at DNS).
Try posting your /etc/hosts file, or at least checking if there is anything at all in there related to psu.edu.
If you type any of the ips given by nslookup into the browser do they work correctly?
I checked the domain on opendns.com cache check and it says the result is valid.
I'm curious if one of the ips is having trouble and for some reason just your laptop is using the bad one.

btw I don't get any results about recursion not available - so not sure what's up with that.
also nslookup appears to be asking your router (192.168.0.1) which presumably is configured to ask your isp nameserver. It may be good to check just what the router is asking. If some exploit was perpetrated that poisoned the dns ip then you could be getting "bad" ips for any number of names - most worrisome being ones for banks and paypal etc.



heres the etc/hosts file

127.0.0.1	localhost
127.0.1.1	logan-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

i cant try those other ip addresses right now cause i'm at school and it will work. so i'll go home later tonight and try.

also, what do you mean by this?

> **BkkBonaza said:**
> 
also nslookup appears to be asking your router (192.168.0.1) which presumably is configured to ask your isp nameserver. It may be good to check just what the router is asking. If some exploit was perpetrated that poisoned the dns ip then you could be getting "bad" ips for any number of names - most worrisome being ones for banks and paypal etc.

---

### Post by BkkBonanza on 2009-03-30
The output you gave from nslookup showed that it asked 192.168.0.1 for the name psu.edu. I assume that is your router or a machine on your network that is acting as router. Routers don't generally do much nameserving, they generally just forward the name request onto an actual nameserver. Usually it would be configured to pass the request onto your isp nameserver but it could actually ask any nameserver that is open to public use. For example, you can change your nameserver at your router or even in your /etc/resolv.conf file to use the opendns.com public nameservers. They are good and fast and don't go down when your isp has failures (and mine tends to have them). opendns nameservers are 208.67.222.222 and 208.67.220.220. You could try them out to see if your nameserver is causing your problem.

So what I meant above is that if someone hacked your router and changed the nameserver then it could be made to point to a "rogue" nameserver that returns incorrect ips for some names. This type of malicious behaviour falls into a category called dns poisoning. Imagine that some nameserver gives you the wrong ip for paypal or your bank... you would be logging into their page without knowing it was at the wrong server and they could be collecting your password info. Dangerous. And why it's important to make sure your nameservers are not mucked around with.

---

### Post by mech_tigerhawk on 2009-03-30
I think I might have found the problem. Here's my resolv.conf file:

/etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 128.118.25.3
nameserver 130.203.1.4
nameserver 192.168.0.1
search mobility.up.psu.edu

The nameservers are DNS lookup servers. 128.118.25.3 and 130.203.1.4 are both DNS servers hosted by PSU, 192.168.0.1 is one of my friend's routers on campus (NOT the one giving me a problem), and mobility.up.psu.edu is the address that the VPN service uses for on-campus wireless. Now here's an article I found:

[http://tns.its.psu.edu/networking/recursivedns.cfm](http://tns.its.psu.edu/networking/recursivedns.cfm)

In this case, we're looking at the nameservers, where we get the DNS info. This is probably why you were getting the recursion, probably the reason I could rarely access the web page (experiencing unpredictable results), and had no problem accessing with the IP address. I'm going to try to reconfigure it when I get back tonight (I have class until 9) and let you know what I did, if this works.

---

### Post by mech_tigerhawk on 2009-03-30
OK, so changing my DNS servers didn't change anything. I added a prepend to dhclient.conf to add one of the openDNS servers, it correctly showed in resolv.conf after restarting my connection, and still did not allow me to visit sites from the psu.edu domain. A name server lookup resulted in something similar, with 2 complaints about recursion with the PSU DNS servers, as expected. I'm gonna assume your resolv.conf looks exactly like mine, since the name server lookup used the same IP's as mine. 

Right now, I'm kind of lost, and I'll probably read up on the resolv.conf man page later to find out what search does. It probably shouldn't be pointed at our VPN server.

---

### Post by BkkBonanza on 2009-03-30
Ideally the /etc/resolv.conf should be managed by NetworkManager which updates the listed nameservers according to which network you're connected to. I have seen posts about it not working too well for multiple networks though. I know for my use I found Wicd to be an easier and more reliable replacement for NetworkManager and it has settings for each network you connect to and then alters the /etc/resolv.conf depending on your current connection. If you have success with your settings but problems with connection changes then you may want to try out Wicd as it could make switching connections as you move around more automated.

---

### Post by lmm5247 on 2009-03-31
i tried webaccess.psu.edu and it worked! :) (see attached image)

i didn't do anything, didn't change any settings or anything. i just got home from school and it worked.


here is my resolv.conf file anyway

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.0.1
search hsd1.pa.comcast.net.


BkkBonaza, i have a question.
when i type in a url, it sends a request to my router (nameserver) which sends a request to search comcast to direct me to the correct website? is that how it works? and using opendns would make my router ask opendns for a website instead of comcast?

mech_tigerhawk, you should switch to wicd and see if that does it for you.  like BkkBonaza said, wicd is way more reliable than networkmanager.  for me, it doesnt ever lose the connection and provides much faster speeds. check it out and post back

---

### Post by BkkBonanza on 2009-03-31
My understanding is the process is like below (and I could be slightly off):

Web browser checks it's name cache and if old then makes a system call for name lookup.

System checks /etc/resolv.conf and tries nameservers in order listed. If a server fails then it continues to next in list.

Your first nameserver is 192.168.0.1 so system send name request to port 53 at that ip. Assuming that is your router, the router will now resolve the name. That may be either an ip in it's cache (if recent) or checking it's own resolv.conf to decide who to ask. It would forward it's request to a nameserver in a way similar to your own system. This is recursion and a normal part of dns lookups.

When a final name is found it could be either authoritative (if the nameserver has authority, which means that it is a known reliable answer) or not (if there is possible uncertainty). At that point the ip is returned through each step of the way to your system and to the browser.

The browser then opens a tcp connection to that ip and sends an http request.

If you put opendns as your preferred nameserver then, yes, your system would ask opendns for names -> ip lookups, not comcast. If you give your router the opendns address then all systems using it on your LAN would have name requests sent there. I sometimes do that here because the local isp nameserver goes down often and then you have net access but can't get anything for lack of name lookup. I keep a commented line in my /etc/resolv.conf and if the local one fails I just pop in and uncomment it.

---

### Post by mech_tigerhawk on 2009-04-01
lmm5247, I'm assuming your resolv.conf refreshed itself, because your name server resolution did NOT match the resolv.conf you posted.

EDIT: Never mind now. My resolv.conf now refreshed properly and I can access the sites. Thanks for all the help!

---

### Post by lmm5247 on 2009-04-02
just now i'm having the same problem again. anything on the psu.edu domain won't load =(

---

### Post by mech_tigerhawk on 2009-04-08
It's all because our DNS serveers keep changing. Mine started working and then stopped like yours. Do you connect to the PSU wireless too?

---

### Post by BkkBonanza on 2009-04-08
Wicd has per connection options for static dns ip. Click the little side-arrow next to the network name on it's control panel to reveal additional settings. If the dns on any connection you have is flaky then you can try setting that one to use a reliable dns like opendns.com - just put in their dns ips for that connection to bypass the one assigned default by dhcp during connection. Opendns ips are listed on their site for public use, see how-to there.

---

### Post by mech_tigerhawk on 2009-04-14
> **BkkBonaza said:**
> Wicd has per connection options for static dns ip. Click the little side-arrow next to the network name on it's control panel to reveal additional settings. If the dns on any connection you have is flaky then you can try setting that one to use a reliable dns like opendns.com - just put in their dns ips for that connection to bypass the one assigned default by dhcp during connection. Opendns ips are listed on their site for public use, see how-to there.

The main problem might be hibernation. I noticed that when I come back and start my computer from hibernation, it keeps the resolv.conf from using the VPN client. You might not need to set up a static DNS.

---

### Post by dreamzinc on 2009-04-15
i have been facing the exact same problem since I installed vpnc from synaptic manager last week, to connect to itsatup and such other servers from off-campus.
I have tried changing the DNS server to the opendns as suggested above, and ensured that the /etc/resolv.conf updates accordingly upon a new connection restart.
I have also uninstalled the vpnc client now...

nothing works :(

my /etc/resolv.conf says:
> # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 128.118.141.32
nameserver 128.118.25.3
nameserver 192.168.0.1
search psu.edu hsd1.pa.comcast.net.

why does it list psu.edu before pa.comcast.net in the search field?

any other pointers...?

---

### Post by mech_tigerhawk on 2009-04-25
I'm 99.9% sure that it's hibernation. If I shut down instead of hibernating all the time, it seems to pick up the resolv.conf file properly. Just don't hibernate when you're going home.

---

### Post by dreamzinc on 2009-04-25
I never hibernate my m/c! 
I always shut it down... @ mech_tigerhawk, are you sure its got to do with hibernate?

---

