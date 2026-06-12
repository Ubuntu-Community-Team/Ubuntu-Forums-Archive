---
title: "dhcp vs static ip: ssh problem ubuntu 11.10"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by LiefhebberLinux on 2012-03-13
I set-up my ubuntu-server 11.10 out of the box and changed the interfaces settings to 

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

However, I kept getting Write failed: Broken pipe issues. It worked for about 30s and than it broke. Moving it back to the original settings

iface eth0 inet dhcp

resolved the issue and I can ssh into my server and the sessions last until I close them. Unfortunately, it is far from ideal to have a dynamic ip for a server. I am wondering what I am doing wrong in my set-up of the static ip. The address is the same as the server sets in the set-up file. Gateway is the ip of the router. Not sure about netmask, broadcast, network, but the above seem to be the standard settings.

Any idea on the Write failed: Broken pipe  

appreciate the help

---

### Post by wyliecoyoteuk on 2012-03-13
You might need to change the keepalive intervals

e.g.
on the client.

ServerAliveInterval 25

on the server 

ClientAliveInterval 30

I expect that DHCP traffic is keeping it alive otherwise.

---

### Post by chili555 on 2012-03-13
I suggest the following:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
```Then get the system to re-read the file with:```
sudo ifdown eth0 && sudo ifup eth0
```Where exactly does Write failed: Broken pipe appear?

Did you fill in /etc/resolv.conf? It probably has acceptable but not ideal settings from your DHCP connections.

---

### Post by wyliecoyoteuk on 2012-03-13
> **chili555 said:**
> Where exactly does Write failed: Broken pipe appear?



I assumed it was in his SSH session, dropping because of lack of keepalive packets.

---

### Post by LiefhebberLinux on 2012-03-13
Thanks for the pointers: Here is what I tried.

My /etc/resolve.conf reads

nameserver 194.168.4.100
nameserver 194.168.8.100

which indeed is probably not ideal. I have added ClientAliveInterval 30 to /etc/sshd_config and changed interfaces to

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
```

I ran ```
sudo ifdown eth0 && sudo ifup eth0
```

and even restarted the server. I managed to ssh into the server again. However after about a minute it came back with 

Write failed: Broken pipe

Trying to ssh in again gives: Connection refused

---

### Post by wyliecoyoteuk on 2012-03-13
try running

top 

when logged in to the server.
If the link stays up, it is a timeout issue.
If it fails, it must be something else

---

### Post by chili555 on 2012-03-13
After you get a broken pipe, can you ping the server?```
ping -c3 192.168.0.100
```

---

### Post by LiefhebberLinux on 2012-03-13
yes, I can ping it fine.

Also, after letting it rest for a while I can ssh in again. However, after a 30s it gives 

Write failed: Broken pipe 

again. So it seems that it blocks the port after a broken pipe and opens it after a certain time period.

---

### Post by chili555 on 2012-03-13
> I have added ClientAliveInterval 30 to /etc/sshd_config I'm not at all an ssh wizard; I think wyliecoyoteuk is your guru. However, this seems interesting: [https://bbs.archlinux.org/viewtopic.php?id=97003](https://bbs.archlinux.org/viewtopic.php?id=97003)

---

### Post by LiefhebberLinux on 2012-03-14
Hi wyliecoyoteuk

so far I have not been able to ssh in again in order to try "top". The last I got from ssh -vvv jack@server was

...
jack@server's password: 
debug3: packet_send2: adding 64 (len 60 padlen 4 extra_pad 64)
debug2: we sent a password packet, wait for reply
Write failed: Connection reset by peer

retrying gives

OpenSSH_5.9p1 Debian-3ubuntu1, OpenSSL 1.0.0g 18 Jan 2012
debug1: Reading configuration data /home/jack/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to server [192.168.0.100] port 22.
debug1: connect to address 192.168.0.100 port 22: Connection refused
ssh: connect to host server port 22: Connection refused

I would expect that if it is a timeout issue I could ssh in straight after again which is not the case.

Could it be that I have to change my ip address on the server?

---

### Post by LiefhebberLinux on 2012-03-14
Another piece of information.

I have a web-based service running on port 8085

this also does not work consistently. It works after the server is started and quickly dies. Reloading gives

could not connect to 192.168.0.100:8085

Any help would be appreciated

---

### Post by LiefhebberLinux on 2012-03-14
I found something else which is interesting

Following my connection times on the router I noticed that the connection is fine if the server is idle. Basically, the connection keeps running al this time e.g. several hours. After I visit my web-application on 8085 the connection quickly breaks and restarts. The same happens after I ssh in. Within 30secs the connection dies (broken pipe) and the server's connection to the router restarts.

So it seems that as soon as something tries to communicate with the server it reacts and closes the connection. Maybe some authorization issue?

Any ideas?

---

### Post by wyliecoyoteuk on 2012-03-14
Seems like it is not a timeout issue.
Not sure why it would work on DHCP but not static.

I am not an ssh expert unfortunately.

A few ideas:
Are the time and date synced on the server and client?
Are you sure that there is not another device with the same IP on the network?
Is there any sort of proxy inbetween?

---

### Post by wyliecoyoteuk on 2012-03-14
Certainly sounds like a permissions issue.
What group are you using for the web app?

---

### Post by jerome1232 on 2012-03-14
This might be working around the problem but why not setup a reserved dhcp address for the server in the router so that it [the server] will always pull the same address from the router. This would be very similar to a static, and it would workaround the issue you're having.

---

### Post by papibe on 2012-03-14
> **LiefhebberLinux said:**
> 
debug1: Reading configuration data /home/jack/.ssh/config
I see that you have a custom ssh config file there. What's in it?

Regards.

---

### Post by wyliecoyoteuk on 2012-03-15
> **jerome1232 said:**
> This might be working around the problem but why not setup a reserved dhcp address for the server in the router so that it [the server] will always pull the same address from the router. This would be very similar to a static, and it would workaround the issue you're having.

Looks lik a good idea to me

---

### Post by LiefhebberLinux on 2012-03-15
Thanks for the pointers. This is sorted now. By trying to set-up the DHCP reservation (which indeed works in the same way as static for all practical purposes), I figured out that I had made the beginner mistake of thinking that the mac address of the PC equalled the eth0. Hence, I kept putting the ip address in interfaces equal to computer's rather than setting one for eth0.

Now it also works for static ip without problems.

---

### Post by MatiasBarone on 2012-06-08
I have the same problem with UBUNTU SERVER 12.04 with IP Static.
We found that the problem appear after connecting a notebook.
When i go to DHCP client list that notebook had 192.168.1.3&"·$%% (and more symbols) in the IP number. When we disconnect that machine the problem disappear.
The server has static IP and the problematic notebook use DHCP. 

I hope this info help.

---

