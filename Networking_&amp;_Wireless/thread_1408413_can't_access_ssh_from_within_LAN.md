---
title: "can't access ssh from within LAN"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by max-power2717 on 2010-02-16
G'day,

I'm having trouble accessing my ssh server from within my LAN by specifying it's public hostname.

At home, I've got a Ubuntu Server 9.10 machine and an WinXP machine connected to a DLink ADSL Router (the situation is illustrated below). I have installed an SSH Server on the Ubuntu machine, and using putty from the WinXP machine I can connect to the server without problems when I type the LAN IP address of the server. 

[IMG]http://i48.tinypic.com/nvqx5z.jpg[/IMG]
I have also used the no-ip.org free dynamic DNS service to set up a hostname for my server (I'll call it... max-powers-hostname.noip.org... for the purpose of this post). I have configured the router to redirect traffic coming in on port 22 to the server. This works well; from outside my LAN, I can access the SSH service hosted on my server by pointing the client to max-powers-hostname.noip.org.

From within the LAN however, when I point putty on the WinXP machine to max-powers-hostname.noip.org, the connection fails. Putty reports "Connection reset by peer." and ssh from the ubuntu server reports "Connection refused". However, I can ping the server from within the LAN by the public hostname, and I can also trace to it (there's only one hop, which appears to be the router).

I'm confused... I'm obviously missing something in my understanding of TCP/IP. The connection seems fine, yet something prevents an ssh connection being made. I've had this problem for some time. A while back I assembled a LAMP server which functioned fine when accessed through the public hostname from outside my LAN, and from within my LAN I could access it fine by specifying the IP address, but I could not make a HTTP (or indeed an SSH) connection with the machine from within the LAN by specifying the public hostname. 

Is my scenario of trying to connect to the ssh service from within the LAN by specifying the external hostname a bit more complicated than the straight forward scenario of accessing the service from outside my LAN? If so, then, is there any sort of work around solution for my problem? One idea that came to mind is installing a DNS on the server, but the more I review the DNS system, the more I'm wondering if that's going to help me (I mean, my public hostname is already registered with no-ip.org and it's working fine from outside and inside my network).

Sorry for another long winded post. Cheers in advance for any input.
Max.

---

### Post by 2hot6ft2 on 2010-02-16
Strange. I had to scribble on your illustration to visualize just what you're describing. The blue represents the url. The green paths connect but the red doesn't.

So client to server on LAN works
Remote client to url to server works
Local client to url to server fails.

It should work without a hitch. I'm not seeing where the problem is. I did the same thing but using FreeNX instead of PuTTy and it's working fine (see my sig). I'm going to have to think on this one.

---

### Post by max-power2717 on 2010-02-16
Hi 2hot,

Thanks for concerning yourself with my problem. 
Your summary of my problem is accurate and is illustrated well on the diagram. One other detail to add to your summary: local client to url to server fails even when the client process is on the server (so a red can be drawn from the server machine, out to the router and back to the server machine, same way as you've done WinXp to Server). But, from the server machine, ping and trace to the url does work.

I skimmed through your how-to for FreeNX and DD-WRT, very interesting - well done! 

First thing that strikes me as different in my situation is the system driving the router. I looked into DD-WRT briefly and my router is not in the list of supported devices. The OS of the router I'm using (A DLINK device) is the one that was originally on the device when my ISP provided it to me about 5 years ago. With it I have always been able to achieve what I needed for my network. 

A friend of mine who looked at my situation a couple of months ago (when I was running a ubuntu-desktop machine I configured as a LAMP server) was baffled by the problem as well, and he suggested that perhaps my router has some sort of bug that's preventing the connections from being established. At the time we made loose plans for him to bring his router around to rule out a device issue, but he's gone away on holiday and we haven't got around to that yet. 

However, that got me thinking: ping and tracepath are working fine from within my LAN, indicating that the network layer is functioning correctly. It seems to be the transport layer that is breaking down because the problem affects SSH and HTTP. As far as I'm aware, the router is a network layer device, and so it shouldn't have any effect on the transport layer protocols that are operating on top of it (TCP I believe is used for SSH and HTTP). So, I figure, since the network layer is working, then the router is performing it's duty and it can be discounted as the cause of the problem. Is there a flaw in my logic here anyone?

Any thoughts / further input would be greatly appreciated. 

Thanks.

---

### Post by max-power2717 on 2010-02-26
<bump />

---

### Post by 2hot6ft2 on 2010-02-26
> **max-power2717 said:**
> Hi 2hot,

Thanks for concerning yourself with my problem.
You're welcome
> **max-power2717 said:**
> One other detail to add to your summary: local client to url to server fails even when the client process is on the server (so a red can be drawn from the server machine, out to the router and back to the server machine
So the serv2serv pic below doesn't work either.
> **max-power2717 said:**
> same way as you've done WinXp to Server).
No WindowsXP (I think you mean FreeNX) in my setup just 2 Ubuntu machines and a router.
> **max-power2717 said:**
> 
I skimmed through your how-to for FreeNX and DD-WRT, very interesting - well done!
Thanks
> **max-power2717 said:**
> 
First thing that strikes me as different in my situation is the system driving the router. I looked into DD-WRT briefly and my router is not in the list of supported devices. The OS of the router I'm using (A DLINK device) is the one that was originally on the device when my ISP provided it to me about 5 years ago. With it I have always been able to achieve what I needed for my network. 

A friend of mine who looked at my situation a couple of months ago (when I was running a ubuntu-desktop machine I configured as a LAMP server) was baffled by the problem as well, and he suggested that perhaps my router has some sort of bug that's preventing the connections from being established. At the time we made loose plans for him to bring his router around to rule out a device issue, but he's gone away on holiday and we haven't got around to that yet. 

However, that got me thinking: ping and tracepath are working fine from within my LAN, indicating that the network layer is functioning correctly. It seems to be the transport layer that is breaking down because the problem affects SSH and HTTP. As far as I'm aware, the router is a network layer device, and so it shouldn't have any effect on the transport layer protocols that are operating on top of it (TCP I believe is used for SSH and HTTP). So, I figure, since the network layer is working, then the router is performing it's duty and it can be discounted as the cause of the problem. Is there a flaw in my logic here anyone?

Any thoughts / further input would be greatly appreciated. 

Thanks.
It shouldn't matter which firmware you're running on your router as long as you can forward the port in the routers configuration. Mine just happens to be running dd-wrt so it was include in the instructions.

I thought I had asked this before but I see that wasn't the case.
Is your firewall on the server set to allow connections from "only the ip address of the client on the LAN, the LAN only, or anyone which would include connection attempts from outside the LAN (the internet)"?

Since connecting to it from outside your LAN would mean that your ip address would not be seen as the same as it is on the LAN. Actually I think it would be seen as your public ip address when trying to connect thru the url from your LAN as in the pics.

---

### Post by 2hot6ft2 on 2010-02-27
> **max-power2717 said:**
> I didn't even consider firewall. I'm looking into the matter now. Hopefully I'll uncover the answer, or at least rule the firewall as the soruce of the problem.

I have already confirmed that ufw wasn't enabled on the server (but I've enabled it now). I don't know if ubuntu server 9.04 runs some other sort of firewall service by default which might have interfered with the connection, but it couldn't have been ufw blocking the connection since it wasn't even enabled from fresh OS installation.

Anyway, thanks again. When I know more I will post in the thread.
UFW just manages the iptables and by default they are set to deny incoming connections in ubuntu desktop edition (I'm not sure about the server edition). If you need a GUI for the iptables you can use either GUFW, Firestarter, Shorewall or any number of others.

Firestarter is real easy to use but hasn't been maintained for quite some time now.

GUFW is similar but lacks a viewer to see current connections but it is maintained and being developed. IPV6 is is not supported yet but they are working on it.

Shorewall I haven't tried setting up yet but it is still being developed AND there is Shorewall6 for managing ip6tables so if you're going to get into running servers you may want to go the shorewall route so you can start setting things up for the IPV6 protocol as well.

All of these GUFW, Firestarter, Shorewall and Shorewall6 are in the repos and can be installed thru synaptic of via the console using:
(all letters should be in lowercase)
```
sudo apt-get install <name of app>
```
There are others but these 3 are commonly mentioned in the forum.

---

### Post by max-power2717 on 2010-02-28
Thanks once again 2hot.

> So the serv2serv pic below doesn't work either.Correct.

> No WindowsXP (I think you mean FreeNX) in my setup just 2 Ubuntu machines and a router.I do beg your pardon! :)

> Is your firewall on the server set to allow connections from "only the ip address of the client on the LAN, the LAN only, or anyone which would include connection attempts from outside the LAN (the internet)"?I believe the firewall will allow connections to port 22 from any address now, and I still have the same problem. Before you brought up the firewall, ufw wasn't enabled, but now it is. I've added rules that I believe will enable connections to port 22 from any IP Address. Here is the numbered status of ufw:

```

max-power@hostname:~$ sudo ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     ALLOW IN    192.168.1.0/24
[ 2] 22/tcp                     ALLOW IN    Anywhere

```So, are these rules configured correctly for the connection I'm trying to make? And if they are, is there anything else you can think of which may be causing the connection to break down?

I'm still baffled by this problem. I'm starting to think that I may have to read up about etheral and perform some deep packet analysis to work out where my connections are breaking down.

---

### Post by dmizer on 2010-02-28
> **max-power2717 said:**
> However, I can ping the server from within the LAN by the public hostname, and I can also trace to it (there's only one hop, which appears to be the router)

What does the ping look like?

> **max-power2717 said:**
> From within the LAN however, when I point putty on the WinXP machine to max-powers-hostname.noip.org, the connection fails. Putty reports "Connection reset by peer." and ssh from the ubuntu server reports "Connection refused".

What you're trying to do here is shoot at yourself while the gun is pointed away from you. In other words, you're trying to do a loopback (reroute re-route traffic for your public IP back to your LAN)  for SSH. Most retail level routers are incapable of this, and this is probably your problem.

You can either:
1) Edit the [XP hosts]("http://en.wikipedia.org/wiki/Hosts_file#Content_and_location") file, so that max-powers-hostname.noip.org points to your ssh server's LAN IP instead of it's WAN IP addres.
- or -
2) Install and configure a local DNS server so that your max-powers-hostname.noip.org resolves to your SSH server's LAN IP address for any computer connected to your LAN.

Solution 1 would involve editing the hosts files for all the comptuers on your LAN. Solution 2 would involve editing the DNS entries on all the computers on your LAN.

Edit:
I highly suggest removing all your firewall edits and port forwards not directly related to WAN to LAN ssh access.

Edit 2:
More detailed information here -> [http://www.dyndns.com/support/kb/loopback_connections.html](http://www.dyndns.com/support/kb/loopback_connections.html) This example talks about a web server, but the same applies to an SSH server.

---

### Post by max-power2717 on 2010-03-07
Thank you dmizer and 2hot for all your help.

Sorry it's been so long since I posted an update. I had a power surge which knocked out the windows XP machine, and upset my server for a bit. 

Following from your information dmizer, I was going to go down the DNS server path with my problem, but while I was reading all about how to set one up it occurred that the hosts file solution would be more than adequate for my immediate purposes (besides, there are plenty of other things I want to set up before a DNS server for my tiny LAN). The hosts file solution hadn't even occured to me, and I was aware of this functionality, so it should've really. Oh well, thanks for giving me the solution to my problem. __

I havn't yet had the opportunity to try the hosts file solution out on a windows since the only one I had is no longer working after the power surge, but the hosts file solution works a treat from a ubuntu desktop machine running in place of the win xp machine.

---

### Post by dmizer on 2010-03-09
> **max-power2717 said:**
> I havn't yet had the opportunity to try the hosts file solution out on a windows since the only one I had is no longer working after the power surge, but the hosts file solution works a treat from a ubuntu desktop machine running in place of the win xp machine.

I am certain that the hosts file solution will also work in Windows, as I have used it many times myself. Glad to hear things are working satisfactorily!

---

### Post by 2hot6ft2 on 2010-03-11
> **max-power2717 said:**
> Thank you dmizer and 2hot for all your help.

Sorry it's been so long since I posted an update. I had a power surge which knocked out the windows XP machine, and upset my server for a bit. 

Following from your information dmizer, I was going to go down the DNS server path with my problem, but while I was reading all about how to set one up it occurred that the hosts file solution would be more than adequate for my immediate purposes (besides, there are plenty of other things I want to set up before a DNS server for my tiny LAN). The hosts file solution hadn't even occured to me, and I was aware of this functionality, so it should've really. Oh well, thanks for giving me the solution to my problem. __

I havn't yet had the opportunity to try the hosts file solution out on a windows since the only one I had is no longer working after the power surge, but the hosts file solution works a treat from a ubuntu desktop machine running in place of the win xp machine.
It's been a while since I used this browser so I'm sorry as well for the long delay. I'm glad you got it straightened out. It's been years since I've played with a windows host file and I would have probably never thought of it. So thanks dmizer for dropping in with that.

---

### Post by dggomes on 2012-03-19
Hi guys, I'm having exactly the same problem but the hosts trick didn't help... any other advice?

---

