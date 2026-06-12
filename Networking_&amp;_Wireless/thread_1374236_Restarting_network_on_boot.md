---
title: "Restarting network on boot"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by PaulStat on 2010-01-06
Hi Guys,

I'm wanting my linux machine to set it's network settings during boot, so I've done the following

Changed my /etc/network/interfaces to
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
wireless-essid xxxxxx
wireless-key xxxxxxxxxxxx
wireless-channel 13
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

```

Created a script like so
```

sudo gedit /etc/init.d/wireless-network

```

With this content
```

	 	 		 			 				/etc/init.d/networking restart 			 		

```

Set it's permissions
```

			 				sudo chmod +x /etc/init.d/wireless-network

```

Created a symbolic link
```

sudo ln -s /etc/init.d/wireless-network /etc/rcS.d/**[COLOR=Red]S40[/COLOR]**wireless-network 			 		

```

Rebooted
```

reboot

```

Ok so it boots up ok and it's sitting on the login screen, when I try to ping it however it doesn't reply! What's wrong??

Thanks,
Paul

---

### Post by gordintoronto on 2010-01-06
Wouldn't it be easier to have the computer set to auto-login?  Then the networking would be running automatically.

I can't imagine that it is relevant, but I noticed that you didn't specify a DNS server in /etc/network/interfaces 

You presented so much of what you did as "code," but not the ping command.  I assume you went to another computer on the network and entered the command: 
ping 192.168.0.3

Do you have any firewalls running?

---

### Post by PaulStat on 2010-01-07
Yup a simple ping 192.168.0.3 from my Vista laptop.

I know this works as I get a reply after I login and the IP has been assigned.

---

### Post by gordintoronto on 2010-01-07
Sorry, I'm now out of my depth.  If it were me, I would set the system to autologon.

---

### Post by PaulStat on 2010-04-19
Bit of a late reply but, I did a bit of debugging of my script and my re-directed output looks like. Did an ifconfig as well

```

 * Reconfiguring network interfaces...
   ...done.
eth0      Link encap:Ethernet  HWaddr 00:01:2e:27:bc:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

So when it runs the script, wlan0 hasn't registered yet, suggestions?

---

### Post by klemes on 2010-04-19
Sorry but I must miss something here.
Why exactly you need a script that basically restarts networking when you have edited your /etc/network/interfaces file and given all your network settings and that is that,,you've done it once and for all ,no need to restart networking or anything else for taht matter.If the settings are correct the wlan0 interface should be up and running after boot without any need from you taking any other measures.
And why not use the network manager or wicd to manage your wireless connection both of which are much simpler?

---

### Post by PaulStat on 2010-04-19
> **klemes said:**
> 
And why not use the network manager or wicd to manage your wireless connection both of which are much simpler?

Because as far as I can tell those don't "activate" their settings until I log in.

---

### Post by arjuntank on 2010-04-19
it seems that you want to restrict access while you share data on the network? is that what you want? you can lock the screen AFTER you login if thats the case

---

### Post by PaulStat on 2010-04-20
> **arjuntank said:**
> it seems that you want to restrict access while you share data on the network? is that what you want? you can lock the screen AFTER you login if thats the case

No, right let's start again. I am wanting to use my linux machine as a media server sitting underneath my TV, but here's the problem. I don't want a keyboard and mouse constantly connected to it and my TV doesn't have the right connections for me to display the linux desktop on. I'm sharing the media via fuppes so my Xbox 360 has access to it.

So what I want is to be able to control the linux machine with my laptop via NX. So naturally when I turn it on I don't want to have to connect up a monitor, keyboard and mouse in order for me to access it. (Like I said before when I turn the linux machine on and it gets to the login screen at this stage no IP details have been assigned {I can't ping it, and my router can't see it as a connected device} so therefore I cannot access it via NX)

So I did a bit of further debugging with my startup script last night, here's what the script looks like now:

```

date > /home/paul/debug_script.txt
ifconfig wlan0 >> /home/paul/debug_script.txt
/etc/init.d/networking restart >> /home/paul/debug_script.txt
ifconfig wlan0 >> /home/paul/debug_script.txt
echo "PINGING ROUTER" >> /home/paul/debug_script.txt
ping -c 6 192.168.0.1 >> /home/paul/debug_script.txt
echo "PINGING GOOGLE" >> /home/paul/debug_script.txt
ping -c 6 www.google.com >> /home/paul/debug_script.txt
```

And now I get this output

```

Mon Apr 19 21:54:36 BST 2010
wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:cd:a0:b9  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 * Reconfiguring network interfaces...
   ...done.
wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:cd:a0:b9  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

PINGING ROUTER
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=1 Destination Host Unreachable
From 192.168.0.3 icmp_seq=2 Destination Host Unreachable
From 192.168.0.3 icmp_seq=3 Destination Host Unreachable
From 192.168.0.3 icmp_seq=4 Destination Host Unreachable
From 192.168.0.3 icmp_seq=5 Destination Host Unreachable
From 192.168.0.3 icmp_seq=6 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
6 packets transmitted, 0 received, +6 errors, 100% packet loss, time 5031ms
, pipe 3
PINGING GOOGLE

```

So as you can see even though ifconfig reports that the wlan0 is setup with the correct IP details, it can't ping my router and it can't ping the outside world.

---

