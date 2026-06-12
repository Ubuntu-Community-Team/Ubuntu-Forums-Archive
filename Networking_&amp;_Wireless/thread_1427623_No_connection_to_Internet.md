---
title: "No connection to Internet"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Jen-Jen on 2010-03-11
So, I'm more or less a beginner with ubuntu. I installed 9.10 a few hours ago and have tried to get the Internet connection to work. It doesn't connect at all. I've tried to find a solution on my own by searching in these forums, but I haven't found one yet.
Because I'm such a newbie I can't help but wonder if the computer might be too old for 9.10. :/ Or maybe it's the drivers?
Anyway, here's some info for you:

ubuntu 9.10
Intel Pentium III processor
LAN

Ask if there's anything you'd need to know. I don't really know what you'd need to know to help.

Thank you in advance for the help.


Solution for this problem in the end of the thread.

---

### Post by sdpiowa on 2010-03-11
Can you verify that your NIC (network adapter) is being recognized by Ubuntu?  You should have a connection indicator in the bar at the top of the screen (if left in its default position).

Does your network activity light flash, or is it consistently off?

---

### Post by Jen-Jen on 2010-03-11
**sdpiowa: **It's constantly off and have been since I installed ubuntu.

---

### Post by isee on 2010-03-11
Hi Jen-Jen!

If is as simple as making the connection, try the end of this thread:

[http://ubuntuforums.org/showthread.php?t=1427279&page=2](http://ubuntuforums.org/showthread.php?t=1427279&page=2)

I struggled a bit to make a DSL connection when I unplugged my DLink router and was trying to connect directly to my ISP modem.  I had to create a DSL connection.

Hope this helps!

---

### Post by sdpiowa on 2010-03-11
Do you get an icon similar to the one in the attached image?  If not, I would recommend going into your network connection settings and verifying that your adapter is listed.

---

### Post by Jen-Jen on 2010-03-11
**isee: **Why would I try making a DSL connection?

**sdpiowa: **I need to ask... What do you mean "adapter"?

---

### Post by mark bower on 2010-03-11
doubt i can help, but are you talking laptop or pc.  and are you trying to connect wirelessly to a router or access point.  PIII is not the problem as I use Ubuntu 9.10 on a laptop with a PIII at 1Ghz.

mark

---

### Post by Jen-Jen on 2010-03-11
The PIII is a PC. And it's access point I guess (?), not wireless.

---

### Post by isee on 2010-03-11
So are you trying to connect to your ISP's modem in your home via a wired connection?  Your computer is not connected to a Router first, and then your ISP's modem?

---

### Post by Jen-Jen on 2010-03-11
**isee: **Maybe I got a bit confused by something? I am not very good with computers. Or rather, I'm not very good with internet connections.
But yes, I'm trying to connect to a router.

---

### Post by isee on 2010-03-11
What kind of router are you trying to link to?  My computer is connected with a wire to my DLink router, which is then connected to my ISP's modem.  I use the DLink router because it has wireless capabilities so I can connect wirelessly to the internet with my laptop.

My Dlink router is what actually connects to the internet.  My ISP username and password is stored on my router.  My computer connects to my router using the Auto eth0 connection, no username or password needed.

If I completely unhook my DLink and connect directly to my ISP's modem, I needed to create a DSL connection using my network manager.  The DSL connection I created stores my username and password.

If you open a web browser like Firefox and enter this into the address bar, do you connect to anything?
[http://192.168.0.1/](http://192.168.0.1/)
Thats a common address used by routers.

---

### Post by Jen-Jen on 2010-03-11
**isee: **I had to ask my brother what kind of router I was connected to. Apparently I'm connected first to a SMC router, then a second router - a NetGear.

I can't connect to that address.

Edit: I forgot to mention, the Netgear router has wireless connection. However, the computer I've installed ubuntu on doesn't support wireless.

---

### Post by isee on 2010-03-11
Well I don't think I can help much to figure out the way through two routers.  Why two routers?  Can you plug in to the netgear?

I would have to ask if you know whether your computer is connected to the SMC?  I enter that address above into my Firefox and it takes me to my router login screen.  If I get an error I know I don't have a connection to my router, and therefore won't be able to connect to the internet.

If I could logon to my router at 198.162.0.1 but couldn't logon to the internet, then I would know the connection problem is between my router and my ISP's modem or network, so it would be router settings, not computer settings, that would be causing the problem.

I hope that makes sense.  So then with your setup there could be a misconnection between the SMC and the Netgear.  So can you get a connection plugging in to the Netgear?

---

### Post by isee on 2010-03-11
Go to System---> Preferences --> Network Connections

Do you get the Network Connections GUI?

---

### Post by Jen-Jen on 2010-03-11
**isee: **Most of the time there are at least 6 or more computers connected  with the routers at the same time. Now the thing is that even if I could  plug into the Netgear, the cable from the Netgear is too short to reach  this particular computer.
Since all other computers work, I don't think it's a problem between the  SMC and Netgear, or the Netgear and the Network.
It is plugged into the SMC router, but can't connect.

**Edit:** This is what it looks like

---

### Post by Jen-Jen on 2010-03-12
Please, I need still help.

---

### Post by Naggobot on 2010-03-12
Basic checks

1. Make sure that you have **not** connected your computer to WAN port of the first router
2. Move your computer temporarily so that you can connect directly to the first router
3. Change cable
4. Check that the network is set to connect automatically (right click the network icon -> select edit connections -> select interface -> click edit 

on top part of the dialog there is a check box for connect automatically

Now we often automatically assume that the problem lies with the software but wired network of Ubuntu in my short experience is extremely robust so first check the hard ware. 

Thirdly open terminal and run ifconfig command and post the reults here so that those who understand more about the software can give advice. 

Below you see what my output looks like. Now the part to look at (and this is partially a guess) is "HWaddr 00:0a:f4:e3:e5:0e" since this indicates that there actually is some hardware present (i.e. software sees it and it is at least to some extent alive).

To get this select Applications -> accessories -> terminal

and to terminal type

```
ifconfig

```You can paint the output with mouse and select copy from the top menu of the window. ctrl+c does not work. After this you can post the result to this forum 

eth0      Link encap:Ethernet  HWaddr 00:0a:f4:e3:e5:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x8400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4700 (4.7 KB)  TX bytes:4700 (4.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:a4:04:ac:a6  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe07:aba6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46837667 (46.8 MB)  TX bytes:3361670 (3.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-A4-09-AB-A6-30-33-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

edit: From the picture it can be fathomed that neither of the network interfaces have never connected to anywhere. I do not know why there are two, I have only one. You may have multiple network devices. Never indicates that the computer has not even retrieved any information (IP adress) from your local network i.e it has never discussed with your router. This could indicate that you have connected the computer to WAN port or that the hardware is not "present".

---

### Post by isee on 2010-03-12
I'd like to comment Naggobot that just because the screenshot shows "never" under connections for the Auto eth0 and the other one, if I go to Edit Connections my Auto eth0 always reads "never", while my DSL connection does list the last logon.  Just thought I'd mention that.

Jen-Jen run the ifconfig command in a terminal.  Ask if you don't know how.

This may sound simple but you've clicked Auto eth0 in your NetworkManager icon in your panel to activate the connection right?

---

### Post by Jen-Jen on 2010-03-13
**isee: **Yes, I've activated the connection.

Here is what I receive when I write ifconfig in Terminal:

eth0 Link encap:Ethernet HWaddr 00:01:80:04:50:0d
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

eth1 Link encap:Ethernet HWaddr 00:04:76:22:9a:3a
inet6 addr: fe80::204:76ff:fe22:9a3a/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:75 errors:18 dropped:0 overruns:0 frame:19
 TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:9136 (9.1 KB) TX bytes:1152 (1.1 KB)
Interrupt:10 Base address:0x2000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

---

### Post by Jen-Jen on 2010-03-13
I got some help by a friend and I did the following:
I pinged the router for an IP.
Then pinged a website to make sure I got an IP.
That was all to get internet to work.

After that my friend noticed I was missing Network Manager Gnome, so I fixed that too by writing in Terminal:
```
sudo get-apt upgrade
```
After that I installed it by writing
```
sudo get-apt install network-manager-gnome
```
Then checked for upgrade again.
After that I had to write some other command line, which I sadly have forgotten for an interface, I believe, to make sure the connection would be work after a reboot.

---

