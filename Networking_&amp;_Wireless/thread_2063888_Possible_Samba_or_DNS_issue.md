---
title: "Possible Samba or DNS issue"
date: 2012-09-28
forum: Networking &amp; Wireless
---

### Post by wt9bind on 2012-09-28
Hi,

I had to shut my Ubuntu Server down to install some more RAM and since I have, I can't connect to Samba shares via my Mac or via my WD TV Live Media Players.

If I try via the Media players it says The network share cannot be accessed and via my mac it says: There was a problem connecting to the server.

The plot thickens (and why I think it is DNS) as if I connect to smb://192.168.1.82 (reserved via netcomm NB6 adsl router) it works.

I have restarted the smbd and nmdb with no joy, I have also completely restarted the server.

I guess this is a multiple question thread, firstly being, 
[LIST=1]
[*]Why wouldn't this working now? 
[*]Should I look at making my Ubuntu server the DNS server for my home network or is that overkill (with 2 computers, 3 iOS Devices, Android and 3 media players)
[/LIST]

Thanks for any help with this matter

---

### Post by bab1 on 2012-09-28
> **wt9bind said:**
> Hi,

I had to shut my Ubuntu Server down to install some more RAM and since I have, I can't connect to Samba shares via my Mac or via my WD TV Live Media Players.

If I try via the Media players it says The network share cannot be accessed and via my mac it says: There was a problem connecting to the server.

The plot thickens (and why I think it is DNS) as if I connect to smb://192.168.1.82 (reserved via netcomm NB6 adsl router) it works.

I have restarted the smbd and nmdb with no joy, I have also completely restarted the server.

I guess this is a multiple question thread, firstly being, 
[LIST=1]
[*]Why wouldn't this working now? 
[*]Should I look at making my Ubuntu server the DNS server for my home network or is that overkill (with 2 computers, 3 iOS Devices, Android and 3 media players)
[/LIST]

Thanks for any help with this matter

#1 We don't have enough information to answer this

#2 If the only host (device with an IP address) with a static IP address is the server then you only need to resolve that hostname to its IP address.  If only Samba is needed (browsing) then that is the only host that needs configuration using the /etc/hosts file on Ubuntu.  From the server CLI, post the output of ```
cat /etc/hosts
```...can you ping the Ubuntu server by name from the same CLI?  What output do you get doing that?

---

### Post by wt9bind on 2012-09-28
Yes, sorry Bab, I remind myself of an end user. You Reply should have been "sorry my crystal ball is broken right now" :)

Anyway, here is the output of /etc/hosts

Cheers

```

cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	BINSVR1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

So I guess, add 192.168.1.82 BINSVR1 into the hosts file and my problem may resolve?

---

### Post by bab1 on 2012-09-28
> **wt9bind said:**
> Yes, sorry Bab, I remind myself of an end user. You Reply should have been "sorry my crystal ball is broken right now" :)

Anyway, here is the output of /etc/hosts

Cheers

```

cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	BINSVR1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

So THe /etc/hosts file should be like this



Yes. Don't add it, change it!  The host BINSVR1 should have an /etc/hosts file like this 
```

cat /etc/hosts
127.0.0.1	localhost
[B][COLOR="Red"]192.168.1.82	BINSVR1
[/COLOR][/B]
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

---

### Post by wt9bind on 2012-09-28
Thanks Bab, that has it pinging now, however Samba still is not working via DNS.

Via IP it is fine however my media players don't allow typing of IP and they discover the DNS name themselves.

I have tried on my Mac so far to put the mac into the same samba workgroup, changed my search domain in my adsl modem to match the workgroup name and stopped the samba service on the ubuntu server for 10 minutes before starting it back up.

Do you know anything else I could try?

I just need to say, all I did was shut the ubuntu server down, install 4GB RAM, switched it back on (without the network cable in it) made sure it recognised the new RAM, shut it down, plugged it back into the network and turned it back on.

Thanks

---

### Post by bab1 on 2012-09-28
> **wt9bind said:**
> Thanks Bab, that has it pinging now, however Samba still is not working via DNS.

Via IP it is fine however my media players don't allow typing of IP and they discover the DNS name themselves.

I have tried on my Mac so far to put the mac into the same samba workgroup, changed my search domain in my adsl modem to match the workgroup name and stopped the samba service on the ubuntu server for 10 minutes before starting it back up.

Do you know anything else I could try?

I just need to say, all I did was shut the ubuntu server down, install 4GB RAM, switched it back on (without the network cable in it) made sure it recognised the new RAM, shut it down, plugged it back into the network and turned it back on.

Thanks
What do you get from the CLI of BINSVR1 with this command```
pgrep -l mbd
```

What is the output of ```
ping BINSVR1
```...from the CLI of BINSVR1.  The fact that you have IP connectivity is good but ultimately samba turns that into NETBIOS names.  It can do it via DNS.  The machine can use /etc/hosts is a "DNS primitive' to resolve hostnames which is all you should need.  

What is the output of this from the server CLI```
hostname
```What workgroup is the server is in is not a factor in browsing.

I'm looking past what physical hardware that you installed.  I agree adding RAM should not affect the IP name resolution.

---

### Post by wt9bind on 2012-09-28
Here is the output:

```
daniel@BINSVR1:~$ pgrep -l mbd
8972 nmbd
8986 smbd
8988 smbd
9341 smbd
9342 smbd
daniel@BINSVR1:~$ 
```

```
daniel@BINSVR1:~$ ping binsvr1
PING BINSVR1 (192.168.1.82) 56(84) bytes of data.
64 bytes from BINSVR1 (192.168.1.82): icmp_req=1 ttl=64 time=0.035 ms
64 bytes from BINSVR1 (192.168.1.82): icmp_req=2 ttl=64 time=0.038 ms
64 bytes from BINSVR1 (192.168.1.82): icmp_req=3 ttl=64 time=0.042 ms
64 bytes from BINSVR1 (192.168.1.82): icmp_req=4 ttl=64 time=0.042 ms
^C
--- BINSVR1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.035/0.039/0.042/0.005 ms
daniel@BINSVR1:~$ 

```

```
daniel@BINSVR1:~$ hostname
BINSVR1
daniel@BINSVR1:~$ 

```

From My mac, when I ping BINSVR1 I get:

```
ping binsvr1
PING binsvr1.local (192.168.1.82): 56 data bytes
64 bytes from 192.168.1.82: icmp_seq=0 ttl=64 time=0.481 ms
64 bytes from 192.168.1.82: icmp_seq=1 ttl=64 time=0.284 ms
^C
--- binsvr1.local ping statistics ---
2 packets transmitted, 2 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.284/0.382/0.481/0.099 ms
```

---

### Post by bab1 on 2012-09-29
Please post the complete /etc/samba/smb.conf file.  You can do that with this command```
cat /etc/samba/smb.conf > smb.conf.txt 
```...This should put a text file with the name smb.conf.txt in your home directory.  Just attach that to the reply.

Also post the output of this command```
smbtree
```...and use your password.  This might be the same command in OSX, but I don't know for sure.  I have no experience with Apple products.

---

### Post by wt9bind on 2012-09-29
smb.conf.txt attached.

This is from Ubuntu:

smbtree
Enter daniel's password: 
WORKGROUP
	\\DANIELS-IMAC   		Daniel's iMac
	\\DANIEL-VM      		
	\\BINSVR1        		BINSVR1 server (Samba, Ubuntu)
		\\BINSVR1\IPC$           	IPC Service (BINSVR1 server (Samba, Ubuntu))
		\\BINSVR1\TV             	Television Episodes
		\\BINSVR1\Music          	
		\\BINSVR1\MusicVideos    	
		\\BINSVR1\Kids           	
		\\BINSVR1\Movies         	
		\\BINSVR1\print$         	Printer Drivers


As for Mac OS X, I have installed Mountain Lion and in Apples wisdom, they have ditched the smbtree command.

---

### Post by bab1 on 2012-09-29
> **wt9bind said:**
> smb.conf.txt attached.

This is from Ubuntu:

smbtree
Enter daniel's password: 
WORKGROUP
	\\DANIELS-IMAC   		Daniel's iMac
	\\DANIEL-VM      		
	\\BINSVR1        		BINSVR1 server (Samba, Ubuntu)
		\\BINSVR1\IPC$           	IPC Service (BINSVR1 server (Samba, Ubuntu))
		\\BINSVR1\TV             	Television Episodes
		\\BINSVR1\Music          	
		\\BINSVR1\MusicVideos    	
		\\BINSVR1\Kids           	
		\\BINSVR1\Movies         	
		\\BINSVR1\print$         	Printer Drivers


As for Mac OS X, I have installed Mountain Lion and in Apples wisdom, they have ditched the smbtree command.
At first glance the smb.conf file looks fine and the output of smbtree reflects that,

It shows 3 hosts:
  \\DANIELS-IMAC
  \\DANIEL-VM
  \\BINSVR1       		

It looks like there are no shares configured on:
  \\DANIELS-IMAC  or \\DANIEL-VM 

The shares configured on \\BINSVR1 are:
   \\BINSVR1\TV             	Television Episodes
   \\BINSVR1\Music          	
   \\BINSVR1\MusicVideos    	
   \\BINSVR1\Kids           	
   \\BINSVR1\Movies      

This is what you have in your smb.conf file, so that is good.  Ubuntu is for sure resolving the DNS (hosts file) correctly too.

I have heard that there are problems with OSX and Samba.  Apple has started to implement their own version of CIFS.  From what I can gather you can see what commands are available at the CLI in OSX with this command```
smbutil
```

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zdnet.com/samba-growing-pains-continue-in-os-x-lion-7000001353/") for more info.  The google search that I ran provides [**_[COLOR="Blue"]these listings[/COLOR]_**]("https://www.google.com/search?q=osx+Mountain+Lion++samba&btnG=Go!")

How do would you browse for shares from the WD TV Live Media Players?  I've never done that.

Is the Ubuntu host a terminal only Server Edition (SE) or are you running Samba on a Desktop Edition (DE)?  If it is a DE, what version of desktop is it?  I run Samba servers on both the SE and DE.

Do you have a firewall running that would block ports 137 - 139 and 445?  These are needed to run Windows sharing (CIFS).  If so, try temporarily disabling the firewall(s).

---

### Post by wt9bind on 2012-09-29
I believe I have found the issue.

With the command you gave me in OSX of smbutil, I typed sumbutil lookup binsvr1, it resolved to my copiers IP of 192.168.1.10

In the SMB settings of my My Ricoh MP2000, had been configured with the Host name of BINSVR1 in host name in SMB. I have changed the host name and done another smbutil lookup binsvr1  but now it is saying No route to host.

I imagine it will take some time to refresh and can't see a way to force it.

What I can't work out is how the WD or Mac has ever been able to see binsvr1's smb shares?

As for your question on the WD TV Live's I have no idea how they work, I choose Video --> Network and SMB Shares are displayed in there. Luckily I am trying to get away from SMB all together and have Mediatomb running (well sorta) thread for my stuff up can be found here: [http://ubuntuforums.org/showthread.php?t=2064080](http://ubuntuforums.org/showthread.php?t=2064080)

Either way Bab, with your help, I believe we have found the issue, now I play the waiting game.

Cheers

EDIT: That was quick, IT IS WORKING AGAIN!!!!!!! Thanks so very much Bab, you have really helped me out!

---

### Post by bab1 on 2012-09-29
> **wt9bind said:**
> I believe I have found the issue.
...

EDIT: That was quick, IT IS WORKING AGAIN!!!!!!! Thanks so very much Bab, you have really helped me out!

Glad you got it worked out.

---

