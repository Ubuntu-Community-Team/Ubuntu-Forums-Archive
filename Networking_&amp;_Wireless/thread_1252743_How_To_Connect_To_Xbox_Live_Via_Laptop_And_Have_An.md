---
title: "How To Connect To Xbox Live Via Laptop And Have An Open NAT"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by fuzzman54 on 2009-08-29
**_[SIZE=6][COLOR=Red]This Howto is outdated and was poorly written to begin with. The method described in this [post]("http://ubuntuforums.org/showpost.php?p=10277612&postcount=18") looks like it should work, I'll update this soon.[/COLOR][/SIZE]_**




This tutorial should help you make your laptop to share it's wireless connection to your 360 and forward the ports so you don't have any NAT problems. Before you go through this though, you need to find out what ip your router uses.

Open a Terminal and run this:

```
sudo ifconfig | grep 'inet addr:192.168.'

```if it says "192.168.1.*" (With the * being a number) then this will work for you, if it says "192.168.2.*" you're going to have to use that instead of the [FONT=Arial]"192.168.1.*"[/FONT][FONT=Arial] that I use throughout this thing.[/FONT]

  [FONT=Arial]
[/FONT][FONT=Arial][SIZE=2]_**Assign a permanent ip to eth0**_[/SIZE][/FONT][FONT=Arial]

Open a Terminal and run this:

```
gksu gedit /etc/network/interfaces
```add the lines
[/FONT]
```
[FONT=Arial][COLOR=Black]auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0[/COLOR][/FONT][FONT=Arial]
[/FONT]
``` [FONT=Arial][SIZE=2]

and save.

_**Configure the Xbox 360.**_[/SIZE][/FONT][FONT=Arial]

Go to **System Settings-->Network Settings-->Configure Network** and put the following

[/FONT]```
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
Gateway: 192.168.1.1

```[FONT=Arial]
[/FONT][LEFT][FONT=Arial]
To get the DNS addresses put this into a terminal
[/FONT]
```
[COLOR=Black]cat /etc/resolv.conf[/COLOR]
```[COLOR=Black]

and use the adress that it gives you for both Primary and Secondary DNS[/COLOR][FONT=Arial][COLOR=Black].
[SIZE=2]
_**Forward the ports with Firestarter**_[/SIZE] 

[/COLOR][/FONT]                                  [FONT=Arial]Run this in a terminal.[/FONT][FONT=Arial]

```
sudo apt-get install firestarter
```[/FONT]
[LEFT][FONT=Arial]
Run through the Wizard. Then go to     [/FONT][FONT=Arial]**Policy**[/FONT] [FONT=Arial]and     right-click in the bottom box, click [/FONT][FONT=Arial]**Add     Rule**[/FONT][FONT=Arial], and forward the port [/FONT][FONT=Arial]*53*[/FONT]     [FONT=Arial]using [/FONT][FONT=Arial]*192.168.1.10*[/FONT]     [FONT=Arial]as the ip and repeat for the ports[/FONT] [FONT=Arial]*80,     88*[/FONT][FONT=Arial], and [/FONT][FONT=Arial]*3074*[/FONT][FONT=Arial].

[SIZE=2]_**Reboot and see if your work paid off**_[/SIZE]

Restart your computer, then start Firestarter's Firewall and test your xbox. If it worked, be sure to post so that I know that I actually helped someone, and if it didn't, be sure to post because I actually do want to help. :D
[/FONT][/LEFT]
  [/LEFT]

---

### Post by NastyT23 on 2009-08-29
what do you select for name when your trying to add rule in firestarter to forward the ports?

---

### Post by NastyT23 on 2009-08-29
I selected http and put all the ports in and the ip address. I followed everything but i still can't connect to xbox live, please help this is annoying.

---

### Post by fuzzman54 on 2009-08-29
I combed through your older posts and found an old ifconfig output post that had a bridge. Is that still your setup?

---

### Post by NastyT23 on 2009-08-30
i have a new laptop and yes i tried the bridging method again but still with no success:
```
terry@terry-laptop ~ $ ifconfig
br0       Link encap:Ethernet  HWaddr 00:23:8b:7a:b8:fd  
          inet6 addr: fe80::223:8bff:fe7a:b8fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:366506 (366.5 KB)

br0:avahi Link encap:Ethernet  HWaddr 00:23:8b:7a:b8:fd  
          inet addr:169.254.10.121  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:23:8b:7a:b8:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4326052 (4.3 MB)  TX bytes:4326052 (4.3 MB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:20:7c:1c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe20:7c1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:132436 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:184765103 (184.7 MB)  TX bytes:9634490 (9.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-6B-20-7C-1C-63-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by NastyT23 on 2009-08-30
i dont need the bridges if i can get it to work some other way, i don't really know how to remove them though

---

### Post by fuzzman54 on 2009-08-30
The command ```
sudo brctl delbr br0
``` is what I would use for deleting the bridge. But you might have to remove the interfaces from it before you can delete it by putting in ```
sudo brctl delif br0 eth0
``` and with wlan0 too. Try doing that and then running back through my tutorial and telling me if it worked this time.

---

### Post by NastyT23 on 2009-08-31
```
terry@terry-laptop ~ $ sudo brctl delbr br0
[sudo] password for terry: 
bridge br0 is still up; can't delete it
terry@terry-laptop ~ $ sudo brctl delif br0 eth0
terry@terry-laptop ~ $ sudo brctl delbr br0
bridge br0 is still up; can't delete it
terry@terry-laptop ~ $ 

```

It wont let me delete the bridge for some reason, still up and running apparantly...?

---

### Post by fuzzman54 on 2009-08-31
Uh.. Sorry about that. I'm learning as well, but I installed bridge-utils and made a bridge just like yours and these commands worked to get rid of it.

```
sudo ifconfig br0 down
``````
sudo brctl delif br0 eth0
``````
sudo brctl delif br0 wlan0
``````
sudo brctl delbr br0
```

---

### Post by NastyT23 on 2009-08-31
Alright sweet it looks like that worked to get rid of the bridge right?:

```
terry@terry-laptop ~ $ sudo ifconfig br0 down
[sudo] password for terry: 
terry@terry-laptop ~ $ sudo brctl delif br0 eth0
terry@terry-laptop ~ $ sudo brctl delif br0 wlan0
device wlan0 is not a slave of br0
terry@terry-laptop ~ $ sudo brctl delbr br0
terry@terry-laptop ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:7a:b8:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:43438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1829108 (1.8 MB)  TX bytes:1829108 (1.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:20:7c:1c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe20:7c1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23431 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42026738 (42.0 MB)  TX bytes:2878781 (2.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-6B-20-7C-1C-63-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

terry@terry-laptop ~ $ 

```

---

### Post by NastyT23 on 2009-08-31
alright i tried connecting the xbox to it but still wont get me connected to my network or live. linux is showing my ethernet cabled connection as not being managed after i followed one of your delete commands for the bridge that you posted the first time, here's a screenshot of what i'm talking about:

[IMG]http://img188.imageshack.us/img188/9263/screenshotjit.png[/IMG]

---

### Post by fuzzman54 on 2009-08-31
Did you redo the steps? This is taking forever to do over the forum, do you have an instant messenger?  I wouldn't want to take a week to get my crap working, heh.

---

### Post by NastyT23 on 2009-09-01
Yep i followed everything you said, my interfaces file looks like this:
```
auto lo
iface lo inet loopback

auto eth0
        iface eth0 inet static
        address 10.0.0.1
        netmask 255.0.0.0
        network 192.168.1.0
        broadcast 10.255.255.255
        gateway 192.168.1.1

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1
```

My xbox still cannot connect...my instant messanger for aim is: NastyT23
Thanks for all your help with this.

---

### Post by fuzzman54 on 2009-09-01
Okay. I sent some messages to your AIM. I'll stay signed in, just send me a message when you get on next and we'll get everything worked out. :D

---

### Post by Canto39 on 2009-10-11
I'm using Xubuntu and I tried doing this, and after changing the interface file and rebooting, nothing on my laptop will work. I tried opening firestarter and it never opened, I tried opening Firefox and it takes forever and when it does open I cant do anything on it. I checked System Monitor and it says the status for everything is 'sleeping'. I tried opening interfaces again to change it back but when I try to open it its just an empty window for a really long time then eventually the text appears, then eventually I am allowed to change it, but when I try to save it just freezes. What the hell did this do to my computer?

---

### Post by fuzzman54 on 2009-10-16
It wasn't this that caused your problems. What else have you been screwing around with that you don't know anything about? Whatever it is, that is what caused your problems.

---

### Post by Hoyland84 on 2009-10-23
So 

```
sudo ifconfig | grep 'inet addr:192.168.'
```

posts back this:

```
inet addr:192.168.0.193  Bcast:192.168.0.255  Mask:255.255.255.0
```

Does this means that what I should add to "/etc/network/interfaces" should look like this?

```
auto eth0
iface eth0 inet static
address 192.168.1.193
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
```

I assumed this and continued the process.

I configured the network settings on my PS3 (I don't think there should be any significant difference from an Xbox)

```
IP Address: 192.168.1.10
Subnet Mask: 255.255.255.0
Standard Router: 192.168.1.193
Primary DNS: 192.168.0.1
Secondary DNS: 0.0.0.0
```

Btw, this is the full output of the command 
```
cat /etc/resolv.conf
```

```
# Generated by NetworkManager
domain alfanett.no
search alfanett.no
nameserver 192.168.0.1
```

There's a good chance that I have messed something up already, but anyway, I continue running Firestarter wizard. I use my wlan0 device
as my "Internet connected network device", enables internet connection sharing and selects eth0 as the device. Starting the firewall I get the message: "The device eth0 is not ready."

Testing the connection on my PS3 gives me success on the first step; IP-adress, but it fails on the next; Internet connection.

So, what am I missing here? Thanks for your support. :)

---

### Post by fuzzman54 on 2009-10-25
Ah. I thought I had everything set up right in my howto, but I didn't. If it weren't for you, I wouldn't have known, thanks! It's only right for people with a setup close to mine, so I'll have to edit it now. Anyways, I think your interfaces file should look like this. 

```
auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
```
After you change it to that, run this command

```
sudo /etc/init.d/networking restart

```And I think that your PS3 setting should have these settings.

```
IP Address: 192.168.0.300
Subnet Mask: 255.255.255.0
Standard Router: 192.168.0.1
Primary DNS: 192.168.0.1
Secondary DNS: 192.168.0.1
```
And in Firestarter, instead of forwarding the ports that the Xbox needs forwarded, forward the ones the PS3 needs. Those are 80,443,5223,3478,3479, and 3658.

After you've done all of that, come back and tell me if it worked out or not, and which step it failed on if it didn't.

---

### Post by Hoyland84 on 2009-10-25
OK, I've tried this, and I am sorry to say; still no success.

If I change my interface file to your latest suggestion I loose my internet connection fully. I am still connected to my wireless router, but firefox won't find any webpages for me. I've also tried rebooting. So I am back to my first settings:

```
auto eth0
iface eth0 inet static
address 192.168.1.193
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
```

This might be wrong, but at least now my internet works. As NastyT23 posted earlier my "Wired Network" posts "device not managed", with this setting.

There's probably something wrong already, but I tried continuing the process anyway. I changed the PS3 settings, according to your instructions, except that I had to set the IP address to 192.168.0.255 as I could not go as high as 300. 255 was the limit.

I also want to say that there's some other steps in the Network Connections process on the PS3, in case you didn't know. I don't know how this is on the Xbox. Anyway, they are listed here, with the options of my choice:
Speed and Duplex: Auto-Detect
MTU: Automatic
Proxy Server: Do not use
UPnP: Enable

Any further ideas? Thanks for trying anyway.

Btw, here's my ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:85:7d:2f  
          inet addr:192.168.1.193  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe85:7d2f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9144 (9.1 KB)  TX bytes:3405 (3.4 KB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8308 (8.3 KB)  TX bytes:8308 (8.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:7e:95:2e:59  
          inet addr:192.168.0.193  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7eff:fe95:2e59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4604333 (4.6 MB)  TX bytes:653383 (653.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-7E-95-2E-59-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Hoyland84 on 2009-10-25
And also:

I am not getting any error messages from Firestarter anymore, even though I have the same settings as I started with. That's good news, but I am not quite sure how to add the rules under Policy

I give no input to the Name field. For port 80 and 443 the names are automaticly given as HTTP and HTTPS. For the rest they're just listed as "Unknown". I wrote the same Port number in both Port fields (the ones you listed in your last post) and put in "IP or host" i put in 192.168.1.10.

Was this the right way to do it?

---

### Post by fuzzman54 on 2009-10-26
I'm not sure of why the settings I gave mucked up your internet access, but Network Manager says "Device not managed" because Network Manager isn't taking care of it anymore, you're giving it your own settings without using Network Manager.

I didn't know that the PS3 had those other options, but your settings for them look alright to me.
 
The way you set the ports was right, but I forgot to tell you that you should use the new ip.

Instead of continuously giving you wrong solutions, I'm just going to catch you on MSN Messenger tomorrow and we'll work it out and then post the way that worked for future people.

---

### Post by Hoyland84 on 2009-12-12
Old thread, but for what it's worth to whomever might search this up.

I have successfully created a bridge between two routers and that way I have a cable connection between my PS3 and my PC. That means that I did not succeed letting the PS3 use my computers wireless card for connection. However, I do think this is possible. You just simply have to know your way around network settings better than I do.

Thanks for your support fuzzman54.

---

