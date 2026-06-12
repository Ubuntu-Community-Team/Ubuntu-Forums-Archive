---
title: "Just installed Ubuntu Server 12.04, but can't connect to it."
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by HunterDX77M on 2012-05-30
WARNING: I know almost nothing about networking or servers, so speak slowly and don't use big words. :)

I installed Ubuntu Server 12.04 on an old machine hoping to use it as, well, a server and I used the directions on this site:

[http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html]("http://www.ubuntugeek.com/step-by-step-ubuntu-11-04-natty-lamp-server-setup.html")

I think everything is up and running okay and I ran /sbin/ifconfig to find that the server's IP address is 172.19.0.10.

Using this information, however, I can't connect to the server via Putty, Filezilla or the ssh in the terminal. In Putty, I am told that "Network is unreachable," Filezilla just continuously tries to connect and doesn't get anywhere, and when I run:

```
ssh username@172.19.0.10
```

in the terminal, I get that it is unreachable, as well.

Immediately after installing the server, I remember it had a different IP address and I was able to successfully FTP a file for a test, but now nothing seems to work. Yes, the server is connected to my router via ethernet. Any suggestions?

---

### Post by linuxman94 on 2012-05-30
You need to set the IP address of the server so that it is on the same network as your router.  Most routers use 192.168.1.1 or 192.168.0.1 as their IP, so the device address is 192.168.1.100, for example.  To configure the static IP, your /etc/network/interfaces file should look like this (assuming a router IP of 192.168.1.1).

```
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1
```You can then ssh on 192.168.1.10.

---

### Post by HunterDX77M on 2012-05-30
I believe my router's address is 192.168.2.1. I'll try that and let you know.

---

### Post by HunterDX77M on 2012-05-30
Okay, great. This seems to work fine with Putty and Filezilla, but only when I provide the address 192.168.2.10 (the address of the server). I can't seem to connect to the server by just giving either of these programs the hostname of the server. Is that possible or is this as good as it's gonna get?

---

### Post by papibe on 2012-05-31
> **HunterDX77M said:**
> I can't seem to connect to the server by just giving either of these programs the hostname of the server.

Hi HunterDX77M.

The problem might be that your router doesn't provide DNS to your LAN (translate names into address). Windows machines use a broadcasting system to let each other its names, and IPs.

Although Ubuntu uses a different kind of broadcasting, you can install a package called 'samba' to add the Windows-style broadcasting. That will allow you to use the Ubuntu server's hostname from the Windows clients.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by HunterDX77M on 2012-05-31
> **papibe said:**
> Although Ubuntu uses a different kind of broadcasting, you can install a package called 'samba' to add the Windows-style broadcasting. That will allow you to use the Ubuntu server's hostname from the Windows clients.

Okay, I think Samba was already installed when the server software was being installed (I recall seeing something called Samba) and I read online that it comes by default on GNU/Linux. Umm, so what can I do knowing it is there. I guess my question is how do I use Samba?

---

### Post by papibe on 2012-05-31
Then, it should be a service running in the background broadcasting your name.

Could you post the result of this command?
```
ps aux | grep nmbd
```

Regards.

---

### Post by HunterDX77M on 2012-05-31
Okay, here it is. I hope you can make more sense of this than I can . . .

```
username   1320  0.0  0.3   4364   812 pts/0    S+   15:14   0:00 grep --color=auto nmbd
```

---

### Post by papibe on 2012-05-31
The service is not running.

Let's see if you have samba installed. Could you post the result of this command:
```
apt-cache policy samba
```
If it is installed, it should look similar to this:
```
samba:
  **[COLOR="Red"]Installed: 2:3.4.7~dfsg-1ubuntu3.10[/COLOR]**
  Candidate: 2:3.4.7~dfsg-1ubuntu3.10
  Version table:
 *** 2:3.4.7~dfsg-1ubuntu3.10 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Packages
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-security/main Packages
        100 /var/lib/dpkg/status
     2:3.4.7~dfsg-1ubuntu3 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages

```
If there's no version besides 'Installed', it is not.

To install it:
```
sudo apt-get install samba
```
Then check again the previous 'grep' command to see if now it's different.

Tell us how it goes.

---

### Post by HunterDX77M on 2012-05-31
My apologies, it looks like it wasn't installed in the first place. #-o

After installing it, here are the outputs:

To see if it's running:
```

root      3144  0.0  0.7  13304  1780 ?        Ss   15:27   0:00 nmbd -D
username   3158  0.0  0.3   4364   812 pts/0    S+   15:28   0:00 grep --color=auto nmbd

```

To see if it's installed:
```

samba:
  [COLOR="Red"]Installed: 2:3.6.3-2ubuntu2.1[/COLOR]
  Candidate: 2:3.6.3-2ubuntu2.1
  Version table:
 *** 2:3.6.3-2ubuntu2.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
        100 /var/lib/dpkg/status
     2:3.6.3-2ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages


```

Again, sorry for my stupidity.

---

### Post by papibe on 2012-05-31
Don't worry.

Now, try using the Server's hostname on the Windows machine.

Regards.

---

### Post by HunterDX77M on 2012-05-31
> **papibe said:**
> Now, try using the Server's hostname on the Windows machine.

Well, I'm not using any Windows machine. I was using Putty on my laptop which also runs Ubuntu.

When I try to connect via Putty with just the hostname and not the IP address, I get a blank terminal window (doesn't even ask for login) that doesn't respond to any keystrokes.

---

### Post by papibe on 2012-05-31
Open a Windows command (cmd) and try pinging the server:
```
ping Ubuntu_hostname
```
What does it say?

Regards.

---

### Post by papibe on 2012-05-31
It may be necessary to change one line on the samba configuration file. Open the file like this:
```
sudo nano /etc/samba/smb.conf
```
The look for a line that looks like this:
```
;	name resolve order
```
And change it for:
```
name resolve order = bcast
```
Not that the semicolon is gone.

Then restart samba:
```
sudo service smbd restart
```
Tell us how it goes.
Regards.

---

### Post by HunterDX77M on 2012-05-31
Ah, very interesting. If I ping the IP address of the server, all the packets get there just fine, as expected.

When I ping the hostname of the server, it goes to some other IP and the entire thing just hangs up with none of the packets getting through.

```
PING Server_hostname [COLOR="Red"]**(63.251.179.13)**[/COLOR] 56(84) bytes of data.
```

That IP highlighted in red is **not** the IP of the server. I don't know who's IP that is.

---

### Post by HunterDX77M on 2012-05-31
Woo! After changing the config file, I was able to ping the server by hostname and none of the packets got lost. Let me check my other programs and get back to you.

---

### Post by HunterDX77M on 2012-05-31
Darn! Although the pinging works, I still can't connect to the server with the hostname alone in Putty. And I just noticed something:

```
64 bytes from Server_hostname [COLOR="Red"]**(199.101.28.20)**[/COLOR]: icmp_req=7 ttl=56 time=26.8 ms

```

That's still not the right IP address. And the hostname wasn't capitalized like my server's name is.

---

### Post by papibe on 2012-05-31
I think we are very close.

If you can, try restart your Windows machine and see how it goes.

Regards.

---

### Post by HunterDX77M on 2012-05-31
I'll try restarting it. If it works, I'll let you know. If not, I won't post and I'm going to take a break and come back to it a bit later. I'm in no rush to get this working (it's all really to satisfy my curiosity and see *if* I could do it). But thanks for all your help so far.

---

### Post by HunterDX77M on 2012-06-01
> **papibe said:**
> I think we are very close.

If you can, try restart your Windows machine and see how it goes.

Regards.

Hey papibe,

Okay, I've restarted everything (modem, router, laptop and server), but I'm still having the same problem. When I ping Server_hostname, it hits something that happens to have my server's hostname, but the IP address is still wrong. Whatever the IP is, it seems to be something random every the server is restarted. Any ideas?

---

### Post by papibe on 2012-06-01
What name are you using to ping and access your server?

I just wanted to make sure you use the actual name (Server_hostname was just an example).

Could you post the result of these commands on the server?
```
ps aux | grep nmbd

sudo smbtree
```

Regards.

---

### Post by HunterDX77M on 2012-06-01
Oh, I know Server_hostname is just an example. I was calling it that so we don't get confused in the context of this problem. My actual server's name is Chimaera.

Here are the results of the first command:
```
root       721  0.0  0.6  13304  1516 ?        Ss   20:51   0:00 nmbd -D
username   1330  0.0  0.3   4368   812 pts/1    S+   20:51   0:00 grep --color=auto nmbd

```

But for the second, it told me it couldn't find "smbtree." Is there a typo there?


And for the purpose of clarity, I am hiding my actual name with the word "username"

---

### Post by papibe on 2012-06-01
> **HunterDX77M said:**
> But for the second, it told me it couldn't find "smbtree." Is there a typo there?

My bad, that is on another samba package:
```
sudo apt-get install smbclient
```
Regards.

---

### Post by HunterDX77M on 2012-06-01
Here's the output
```
WORKGROUP
	\\SECOND-LAPTOP 		
	\\CHIMAERA       		Chimaera server (Samba, Ubuntu)
		\\CHIMAERA\IPC$           	IPC Service (Chimaera server (Samba, Ubuntu))
		\\CHIMAERA\print$         	Printer Drivers

```

---

### Post by HunterDX77M on 2012-06-03
Thread bump.

---

### Post by papibe on 2012-06-04
Could you post the result of this on the server?
```
nmblookup CHIMAERA
```
And these ones on the Windows machine?
```
net view \\CHIMAERA

net view \\172.19.0.10
```
Regards.

---

### Post by HunterDX77M on 2012-06-04
Well from the server I got this:

```
querying CHIMAERA on 192.168.2.255
192.168.2.10 CHIMAERA<00>

```

On my laptop, I got that 'net view' was an invalid command. Is that from a separate package?

---

### Post by papibe on 2012-06-04
It looks like either you change your IP range, or the server it is not actually on 172.19.0.10, but 192.168.2.10

Do you have another subnet? By any chance there's another machine with the name CHIMAERA?

Regards.

---

### Post by HunterDX77M on 2012-06-05
> **papibe said:**
> It looks like either you change your IP range, or the server it is not actually on 172.19.0.10, but 192.168.2.10

Do you have another subnet? By any chance there's another machine with the name CHIMAERA?

Regards.

If you look back at post #2 of this thread, I did change the IP to 192.168.2.10 on purpose. It should have that IP, and I'm fine with that. 

I'm not sure what a subnet is. There is no other machine with the name Chimaera.

---

### Post by papibe on 2012-06-05
Ok.

Do you know if your router supports DHCP reservation? That is, that you left the server configuration as default (ask the router for an address), but the router gives always the same address to it?

Also, could you post the result of these commands on the server?
```
ifconfig

route -n

nslookup ubuntu.com
```

And this on the Windows machine:
```
ipconfig /all
```
Regards.

---

### Post by HunterDX77M on 2012-06-05
No, I think the router gave an address dynamically, based on the order of machines connecting to the router. This is why I set the IP statically on the server so I would always know the IP of the server to connect to it via ssh.

For ifconfig on the server:
```
eth0      Link encap:Ethernet  HWaddr 00:08:74:c4:f2:a6  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fec4:f2a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:206104 (206.1 KB)  TX bytes:20758 (20.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2774 (2.7 KB)  TX bytes:2774 (2.7 KB)

```

The router command:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

For nslookup:
```
Server:		127.0.0.1
Address:	127.0.0.1#53

Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156


```

On my machine, ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:23:ae:33:50:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6263 (6.2 KB)  TX bytes:6263 (6.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:4c:b0:92  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:fbff:fe4c:b092/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10966458 (10.9 MB)  TX bytes:3885827 (3.8 MB)

```

Thanks.

---

### Post by papibe on 2012-06-05
Say What?! ... your client is running Linux?

I'm afraid I misunderstood your main concern, and I've been providing tips to connect to Windows clients. I apologize.

The only reason I can think of two Linux not resolving its names, is that your router is not providing DNS.

That would be confirm if the content of these files doesn't have local IP address:

On server:
```
/etc/resolv.conf
```
and on the client:
```
/var/run/nm-dns-dnsmasq.conf
```

A solution for that case it is to install Ubuntu's broadcasting system, and use the '.local' domain to resolve local addresses.

Chances are the service is already configured. Try pinging and connecting using this name:
```
chimaera.local
```

Regards.

---

### Post by HunterDX77M on 2012-06-05
Oh, don't apologize. The fault is mine. You see, when you referred to a windows machine, I thought you were just using a generalized term for what the client was. I should have been more insistent that the client was Linux, also. But now that that is cleared . . .

The [FONT="Courier New"]/etc/resolv.conf[/FONT] file was empty (with the exception of a couple of comments). The file [FONT="Courier New"]/var/run/nm-dns-dnsmasq.conf[/FONT] doesn't exist, apparently. If I [FONT="Courier New"]ping chimaera.local[/FONT], it tells me that host doesn't exist. So what is it that I have to install?

---

### Post by papibe on 2012-06-05
Check if the avahi services are installed:
```
apt-cache policy avahi-utils
```
If not installed, do it  both machines:
```
sudo apt-get install avahi-utils
```

Then, you can check if the service is running by doing:
```
ps aux | grep avahi
```
If it's not, you can start it by doing:
```
sudo service avahi-daemon start
```
Once is up and running, the machines should be able to reference each other using the .local domain.

Regards.

---

### Post by HunterDX77M on 2012-06-06
After installing on the server, here is the result of [FONT="Courier New"]ps aux | grep avahi:[/FONT]

```
avahi     1886  0.0  0.5   3436  1312 ?        S    13:39   0:00 avahi-daemon: running [Chimaera.local]
avahi     1888  0.0  0.1   3436   436 ?        S    13:39   0:00 avahi-daemon: chroot helper
username   1906  0.0  0.3   4364   812 pts/1    S+   13:40   0:00 grep --color=auto avahi

```

I am now able to connect with:
```

ssh username@chimaera.local

```

---

