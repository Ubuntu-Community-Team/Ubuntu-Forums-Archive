---
title: "Help with Network-manager and ICS"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by Objekt on 2010-01-29
I have been having a similar problem.  My Ubuntu 9.10 (64 bit regular old desktop version) machine has two NICs, eth0 and eth1.  eth0 does not connect to my router (and thus the Internet) automatically.  I have to manually click on it in the NetworkManager applet after every reboot.

Internet connection sharing has also been impossible.  I gave up trying to do that after about 2 weeks.  I was simply trying to share my Internet connection with a Windows XP machine over eth1, but it never worked.  I could ping one machine from the other, but couldn't get to the Internet from the Win XP machine.

Removing NetworkManager may be the ticket.  Most of the tutorials for Internet connection sharing tell you to enter commands in the console.  Maybe one of them will work once I remove the NetworkManager applet.

---

### Post by dmizer on 2010-01-29
Your problem was something else entirely. So I created a new thread.

You could install gnome-network-admin, uninstall network-manager-gnome, and manage your network from system > administration > network. However, NetworkManager does have some nice tools for ICS, so you should consider this carefully.

---

### Post by Objekt on 2010-02-01
Glad yours is fixed.  I still can't get Internet connection sharing to work, no way no how.

I did replace NetworkManager with the Gnome Network Admin.  I temporarily lost all ability to connect to anything, but all was well after a reboot.  More importantly, eth0 now comes up automagically every time I log in, which is one problem solved.

FWIW, the symptoms are the same, regardless of whether I use an Ethernet crossover cable or regular Ethernet cable: a Windows machine connected to my desktop's 2nd NIC cannot get to the Internet.  I can jolly well ping each machine from the other all day long, but I cannot convince Ubuntu 9.10 to forward any traffic from the Windows client.  It Simply.  Won't.  Work.  No Way.  No How.

Meanwhile, I can browse the Interwebs from eth1 as much as I like, as long as my desktop's running Windows XP or 7 with eth0 and eth1 bridged.

---

### Post by dmizer on 2010-02-01
> **Objekt said:**
> Glad yours is fixed.  I still can't get Internet connection sharing to work, no way no how.

I did replace NetworkManager with the Gnome Network Admin.  I temporarily lost all ability to connect to anything, but all was well after a reboot.  More importantly, eth0 now comes up automagically every time I log in, which is one problem solved.

FWIW, the symptoms are the same, regardless of whether I use an Ethernet crossover cable or regular Ethernet cable: a Windows machine connected to my desktop's 2nd NIC cannot get to the Internet.  I can jolly well ping each machine from the other all day long, but I cannot convince Ubuntu 9.10 to forward any traffic from the Windows client.  It Simply.  Won't.  Work.  No Way.  No How.

Meanwhile, I can browse the Interwebs from eth1 as much as I like, as long as my desktop's running Windows XP or 7 with eth0 and eth1 bridged.

As I indicated earlier, your problem is something else entirely and you should post a new thread. You should also return to using NetworkManager as it has better GUI tools for internet connection sharing.

---

### Post by Objekt on 2010-02-03
> **dmizer said:**
> As I indicated earlier, your problem is something else entirely and you should post a new thread. **You should also return to using NetworkManager** as it has better GUI tools for internet connection sharing.

I took your advice, uninstalled gnome-network-admin and reinstalled NetworkManager.

Now something really, really odd is happening: NetworkManager shows no connections, just the names of the two NICs and the words "device not managed" grayed out.  I can't find any way to make NetworkManager show the active NIC, eth0.

At the same time, I do have an active network connection over eth0, or I wouldn't be able to post this.

However, I'm pretty sure I found a solution here:
[http://ubuntuforums.org/showthread.php?t=1109585](http://ubuntuforums.org/showthread.php?t=1109585)

---

### Post by dmizer on 2010-02-03
Edit /etc/network/interfaces and make sure you delete everything except the lo adaptor, so it looks like this:
```
auto lo
iface lo inet loopback
```

---

### Post by dmizer on 2010-02-03
Once you have fixed network-manager, take a look at these directions for how to configure ICS: [http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)

---

### Post by Objekt on 2010-02-08
> **dmizer said:**
> Once you have fixed network-manager, take a look at these directions for how to configure ICS: [http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)

I definitely have dnsmasq installed, as mentioned in the tutorial you linked, but I still can't share the connection.

For one thing, I can't adjust any of the properties of the eth1 connection.  In fact the names are messed up too.  Instead of "eth0" and "eth1" I have "ifupdown (eth0)" and "ifupdown (eth1)."  I cannot adjust any properties for either connection.  Fortunately, "ifupdown (eth0)" works automatically, connecting me to my network upon login.  I can't do anything with "ifupdown (eth1)."  Selecting it in NetworkManager doesn't work - the connection never occurs, even though I have a cable plugged into another computer which is turned on.

I don't understand why I can't change any properties of the two possible connections (ifupdown eth0 and eth1) shown in NetworkManager.

If I create another connection using the MAC of eth1, I can change the properties all I like.  However, I'm in the same situation as before.  By manually assigning a static IP address to eth1 and another to the client machine in its OS (Windows XP), I can get the two machines to send pings back and forth.  However, I absolutely CANNOT get to the Internet from the client machine, no matter what I do!  In short, I am stuck exactly where I was wheN I started trying to do this, 3 weeks ago!

---

### Post by dmizer on 2010-02-08
> **Objekt said:**
> I definitely have dnsmasq installed, as mentioned in the tutorial you linked, but I still can't share the connection.

For one thing, I can't adjust any of the properties of the eth1 connection.  In fact the names are messed up too.  Instead of "eth0" and "eth1" I have "ifupdown (eth0)" and "ifupdown (eth1)."  I cannot adjust any properties for either connection.  Fortunately, "ifupdown (eth0)" works automatically, connecting me to my network upon login.  I can't do anything with "ifupdown (eth1)."  Selecting it in NetworkManager doesn't work - the connection never occurs, even though I have a cable plugged into another computer which is turned on.

I don't understand why I can't change any properties of the two possible connections (ifupdown eth0 and eth1) shown in NetworkManager.

If I create another connection using the MAC of eth1, I can change the properties all I like.  However, I'm in the same situation as before.  By manually assigning a static IP address to eth1 and another to the client machine in its OS (Windows XP), I can get the two machines to send pings back and forth.  However, I absolutely CANNOT get to the Internet from the client machine, no matter what I do!  In short, I am stuck exactly where I was wheN I started trying to do this, 3 weeks ago!

Please post the contents of /etc/network/interfaces

---

### Post by Objekt on 2010-02-08
Contents of interfaces file:
```
auto lo
iface lo inet loopback

#iface eth0 inet static
#	address 10.0.0.1
#	netmask 255.255.255.0
#	network 10.0.0.0
#	broadcast 10.0.0.255
#	gateway 10.0.0.1

#iface eth1 inet dhcp


iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp

auto eth1
```

The commented-out section is left from an earlier attempt to get ICS working, which also didn't succeed.

---

### Post by Iowan on 2010-02-08
To make your */etc/network/interfaces* file look like the one in post #6, you need to delete (or comment out) the other 4 lines.  It's *possible* that you may need to add back the one for your WAN connection (Network Manager ordinarily manages only one interface at a time - unless that's changed recently).

---

### Post by Objekt on 2010-02-08
> **Iowan said:**
> To make your */etc/network/interfaces* file look like the one in post #6, you need to delete (or comment out) the other 4 lines.  It's *possible* that you may need to add back the one for your WAN connection (Network Manager ordinarily manages only one interface at a time - unless that's changed recently).

No no no...that is no good.  If I do that, I get no network connection!

However, commenting out the lines beginning with "iface" made it so I can edit settings for auto eth0 and auto eth1, for some reason.  I guess that's some progress.

---

### Post by dmizer on 2010-02-08
> **Objekt said:**
> No no no...that is no good.  If I do that, I get no network connection!

However, commenting out the lines beginning with "iface" made it so I can edit settings for auto eth0 and auto eth1, for some reason.  I guess that's some progress.

You cannot use both NetworkManager and /etc/network/interfaces. They conflict with one another. Once you delete the settings in /etc/network/interfaces, log off and back on. Then you will be able to configure your network with NetworkManager.

---

### Post by Objekt on 2010-02-08
Alrighty, that's done.  NetworkManager now shows two adapters, with the same name (Marvell 88E8506 PCI-E Gigabit Ethernet Controller), each having an entry called "Auto Ethernet."  The top one (presumably eth0?) is connected once I log in.  The second I can manually select.  It attempts to connect for a while, but eventually gives up.

I'm not sure how to proceed from here.

---

### Post by dmizer on 2010-02-09
Make sure you have DNSmasq installed. Leave the second interface unconfigured. No IP address, nothing. Just apply these directions I posted earlier to the second interface: [http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](http://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)

If that still does nothing, please post the output of:
```
lshw -C network
```

---

### Post by Objekt on 2010-02-09
Yes, I have dnsmasq installed.  That tutorial doesn't work.  It was the first thing I tried, several weeks ago.

Output of lshw -C network:
```
 *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 12
       serial: 00:22:15:2f:4f:11
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.1.10 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:286 memory:fe9fc000-fe9fffff ioport:d800(size=256) memory:fe9c0000-fe9dffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 12
       serial: 00:22:15:2f:4e:b5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=10.42.43.1 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:287 memory:fe8fc000-fe8fffff ioport:c800(size=256) memory:fe8c0000-fe8dffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

(the last one is for Virtualbox 3.1.2 PUEL)

---

### Post by dmizer on 2010-02-09
> **Objekt said:**
> Yes, I have dnsmasq installed.  That tutorial doesn't work.  It was the first thing I tried, several weeks ago.

Please tell me more about your physical network. If you have a direct connection between Ubuntu and XP, are you using a crossover cable?

Also, please make sure that the XP PC is configured for DHCP, and manually set DNS servers. If you do not know what your ISP DNS servers are, you can use opendns servers instead:
208.67.222.222
208.67.220.220

Is the XP computer getting an IP address? Can you ping Ubuntu (at 10.42.43.1) from XP?

---

### Post by Objekt on 2010-02-09
Physically, I have one computer with two built-in NICs (the Marvell 88E8056 devices), eth0 and eth1, running Ubuntu 9.10.  eth0 is connected to my router, and so gets to the Internet.  eth1 is connected to the client, a netbook running Windows XP, by a regular Ethernet cable.  In Windows terminology, I am trying to bridge eth1 and eth0, and share the resulting bridge.

I have successfully done Internet connection sharing using the same hardware, but with both the desktop and netbook running Windows XP.  I just bridged the two adapters, ran Network Setup Wizard on both machines, and that was it.  So I know the hardware is OK, it's just hell getting them to play together under Ubuntu.

No, the Win XP netbook is not getting assigned an IP address.  It says the connection is no good ("limited or no connectivity"), and the "Repair" action does not work.

I do have a crossover Ethernet cable.  I have tried it as well, with the same (lack of) success under Ubuntu.  As with the non-crossover cable, I can use it to do ICS when both machines are running Windows XP.

---

### Post by dmizer on 2010-02-09
> **Objekt said:**
> No, the Win XP netbook is not getting assigned an IP address.  It says the connection is no good ("limited or no connectivity"), and the "Repair" action does not work.

"Limited or no connectivity" does not mean the XP machine is not getting an IP address. Please open a command prompt and check ipconfig to see if you are getting assigned an IP address. Also try pinging the Ubuntu box.

---

### Post by andou on 2010-02-09
Not sure if this helps, but it helped me.

[**InternetConnectionSharing**]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

and

[IMG]http://jeremy.visser.name/wordpress/wp-content/uploads/2009/03/nm-nat.png[/IMG]

Just want to reiterate that you would want to select "Shared to Other Computers" for the Adapter you're trying to share, ie: Eth1 - since Eth0 is your Internet connection for your desktop.

---

### Post by Objekt on 2010-02-09
There isn't any "eth0" and "eth1" to select.  When I right click on NetworkManager and select "Edit connections..." I get a list with exactly one entry, just called "Auto Ethernet." 

If I choose to edit the settings of that one and only connection, the box showing adapter MAC is blank.  Very odd.  Yet I can still get an Internet connection.  I don't know how that is possible, since you would think NetworkManager would have to know which MAC to use!

In short, there isn't any way to single out the eth1 adapter and set it to "shared" as is shown in most of the tutorials, including the one you linked.

---

### Post by dmizer on 2010-02-09
> **Objekt said:**
> There isn't any "eth0" and "eth1" to select.  When I right click on NetworkManager and select "Edit connections..." I get a list with exactly one entry, just called "Auto Ethernet." 

If I choose to edit the settings of that one and only connection, the box showing adapter MAC is blank.  Very odd.  Yet I can still get an Internet connection.  I don't know how that is possible, since you would think NetworkManager would have to know which MAC to use!

In short, there isn't any way to single out the eth1 adapter and set it to "shared" as is shown in most of the tutorials, including the one you linked.

Then you must still have some configuration left in /etc/network/interfaces, because the output of lshw -C network from before indicates that you have an IP address for both of your adapters.

Have you installed any other networking tools, something like wicd or firestarter, or gnome-network-admin? All of these can interfere with NetworkManager ICS.

I am absolutely positive that the current version of NetworkManager is capable of ICS. It is essential that you manage 100% of your connection through NetworkManager though.

---

### Post by Objekt on 2010-02-09
> **dmizer said:**
> Then you must still have some configuration left in /etc/network/interfaces, because the output of lshw -C network from before indicates that you have an IP address for both of your adapters.

No, there is nothing in interfaces.  Every line is commented out (#).

> **dmizer said:**
> Have you installed any other networking tools, something like wicd or firestarter, or gnome-network-admin? All of these can interfere with NetworkManager ICS.
None of those are present.  I have Gnome network admin at one point, but uninstalled it a while ago, replacing it with NetworkManager.

> **dmizer said:**
> I am absolutely positive that the current version of NetworkManager is capable of ICS. It is essential that you manage 100% of your connection through NetworkManager though.

Sure, just not on my hardware, it seems.

---

### Post by Iowan on 2010-02-09
> **Objekt said:**
> No, there is nothing in interfaces.  Every line is commented out (#). You left the two lines defining "lo"?

---

### Post by dmizer on 2010-02-09
Have you rebooted since you made the changes to /etc/network/interfaces?

---

### Post by Objekt on 2010-02-09
> **Iowan said:**
> You left the two lines defining "lo"?

No.  Commented out.

---

### Post by Iowan on 2010-02-09
Uncomment those two lines to make the file look like the post #6 example - then reboot or restart (I prefer a reboot to re-sync the networking components).

---

### Post by Objekt on 2010-02-09
Done.  Now what?  Still can't share the connection.  Yes, I rebooted.

By the way, I looked and yes, the Windows XP machine is somehow getting an IP address on its NIC.  I don't know whether it's giving itself the address, or whether the link with the Ubuntu machine is working just enough to give it one.  I do know I still can't get to the Internet from the Win XP client.  The "limited or no connectivity" effectively means "no access."  Trying the "repair" action or running Network Setup Wizard still does nothing.

---

### Post by OzzyFreakDude2 on 2010-02-11
I also have almost the identical problem that Objekt has.  The differences are as follows:

I'm trying to share the internet on my wlan0 to my LAN on eth0.  My LAN works when I manage it in the /network/interfaces file and use dhcp3-server, but when I try to use networkmanager to share the connection (even when I specifically stop dhcp3-server), the windows box can't get an IP address.  When I run ipconfig /renew, it says that the dhcp request timed out, and that "an error occurred while releasing interface loopback pseudo-interface 1 " the system cannot find the file specified".  The whole time on Ubuntu, the 'wired network connection established' indicator keeps popping up over and over, as if it kept connecting, disconnecting, and connecting again so fast that the disconnected indicator doesn't have time to show up.

also, I have tried multiple things to share the internet, such as firestarter (which I had to uninstall in order to access the internet again) and network-config 0.2.  As mentioned by dmizer, I suspect that one of these might have done something to conflict with networkmanager.  However, I don't know how to clear any changes that these programs might have made.

-for more information, i've discussed it in depth at the thread [http://ubuntuforums.org/showthread.php?t=1403862](http://ubuntuforums.org/showthread.php?t=1403862)

Any help is appreciated

---

### Post by Objekt on 2010-02-11
> **OzzyFreakDude2 said:**
> I also have almost the identical problem that Objekt has.  The differences are as follows:

I'm trying to share the internet on my wlan0 to my LAN on eth0.  My LAN works when I manage it in the /network/interfaces file and use dhcp3-server, but when I try to use networkmanager to share the connection (even when I specifically stop dhcp3-server), the windows box can't get an IP address.  When I run ipconfig /renew, it says that the dhcp request timed out, and that "an error occurred while releasing interface loopback pseudo-interface 1 " the system cannot find the file specified".  The whole time on Ubuntu, **the 'wired network connection established' indicator keeps popping up over and over, as if it kept connecting, disconnecting, and connecting again so fast that the disconnected indicator doesn't have time to show up.**

I see that too, when I try to make a connection to the Win XP client.

It never actually works, unless I manually specify IP addresses for both eth1 and the Win XP client (for example, 10.0.0.1 and 10.0.0.2, respectively).  When I do that, I can pass pings back and forth, but nothing else.

Now that I've read your initial post in the other thread, yep, we're having almost EXACTLY the same problems, and have both tried almost exactly the same stuff to get it to work, with almost exactly the same symptoms along the way.  The primary difference is that I have two physical, wired NICs on one machine, where you're trying to both connect to the Internet with and share just the one NIC (WiFi).  

Both of our goals should be attainable.  Certainly they are easy to do under Windows, as you've discovered.  But so far it just isn't happening with Ubuntu, for no obvious reason.

For me, sharing the otherwise-unused NIC is mostly a matter of "because dammit, I should be able to" rather than absolute necessity.  However, that extra NIC can come in handy if your router goes tits up.  Mine did, so for a couple of days, I was doing ICS in Windows XP so that my roommate's computer could get on the Internet.  Eventually we bought a replacement router.  There's less necessity now, but it's still incredibly frustrating that ICS Simply Does Not Work under Ubuntu 9.10.

---

### Post by Objekt on 2010-02-11
Well, isn't THAT interesting!

On a hunch, I tried the following experiment earlier this evening:

-Started up my desktop with an Ubuntu 9.10 64-bit Live CD.

-Right clicked on NetworkManager, selected "Edit Connections," edited the "eth1" connection.  Went to the IPv4 tab, set the connection to "Shared to other computers."  Essentially, I followed the dead-simple ICS tutorial you most often see recommended, here and elsewhere, for Ubuntu 9.10.

-Booted up the Win XP client, checked that the cable was connected to the Ubuntu machine's 2nd NIC.

-Set the XP machine's NIC to "Obtain an IP address automatically" and manually set the DNS servers to OpenDNS (208.67.222.222 and 208.67.220.220).*

-Performed a "Repair" operation on the XP machine's network connection.

-IT WORKED!

So I have proven that is IS possible to do ICS with my hardware + Windows XP client.  I just can't make it work anywhere but the Live CD environment, so far.

--
Addenda:

Note: dnsmasq is installed in Ubuntu 9.10 by default.  It is already present when you boot the Live CD.

*Not sure this step is required.  It may have worked with "Obtain DNS server addresses automatically" but I haven't tried it that way yet.

---

### Post by OzzyFreakDude2 on 2010-02-12
That's interesting.  That leads me to believe that something that we've done to our network settings since installing ubuntu is conflicting with it.  Now the question is what, and how do we reset them?  it'd be great if there was a way to restore all of the system settings to 'factory default'....

---

### Post by Objekt on 2010-02-12
That is exactly the path I'm on.  So far I've got my /etc/network/interfaces back to defaults, by comparing it with the one used in a Live CD session.

I think some stuff is still hosed up in my /etc/NetworkManager folder.  I'm going to use the same methodology - that is, compare it to the Live CD environment - to fix that.  It may be as simple as copying the entire /etc/NetworkManager folder from the Live CD session to a USB stick, then copying that to my hard drive when running my Ubuntu 9.10 install.

---

### Post by Iowan on 2010-02-12
Last time I booted a LiveCD on a working install, I could access the HD from the Live session. You might be able to transfer the information directly...

---

### Post by OzzyFreakDude2 on 2010-02-14
I tried installing ubuntu x64 on my netbook, and the "shared to other computers" option worked to assign an IP address to the ubuntu machine I've been having troubles with.  I didn't have internet to test the internet connection with, though.  I'm going to just completely reinstall ubuntu on my problem machine, I'll let you know how it goes

---

### Post by Saghaulor on 2010-02-23
Make sure you don't have any crazy rules created in ufw.

```
sudo ufw status
```

Also, check your iptables.

```
sudo iptables -L
```

Look for any rules that might be messing things up.

As you've noticed, it's a pretty simple operation. You just have something tweaked incorrectly.

---

### Post by Objekt on 2010-02-24
This is what I get:

```
objekt@objekt-desktop:~$ sudo ufw status
[sudo] password for objekt: 
sudo: ufw: command not found
objekt@objekt-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
objekt@objekt-desktop:~$
```

So ... what next?

---

### Post by Saghaulor on 2010-02-25
> **Objekt said:**
> This is what I get:

```
objekt@objekt-desktop:~$ sudo ufw status
[sudo] password for objekt: 
sudo: ufw: command not found
objekt@objekt-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
objekt@objekt-desktop:~$
```

So ... what next?

I'm not an expert with iptables, but from what I can tell, you don't have any rules established.

Apparently you don't have ufw installed either, which is strange, as it's default with Ubuntu.

But, the point is, this shouldn't be an issue.

Here's an idea. Load up your livecd, share out the connection, then run the iptables command again. See what it says.

Then we'll know what we need it to look like.

But just to double check, your /etc/network/interfaces is default?

---

### Post by Objekt on 2010-02-25
Now there's an idea!  I know ICS works under the Live environment, so could be there's something going on there with iptables or ufw.

I believe I removed ufw in an attempt to get ICS working.  Obviously it didn't help.

I don't have access to the machine now, but I can tell you that /etc/network/interfaces is entirely default.  I made sure of that as part of my troubleshooting, once I found that ICS worked in the Live CD environment.

---

### Post by Objekt on 2010-02-25
OK, here's the output from a live session, running those two commands, after I got ICS working:
```
ubuntu@ubuntu:~$ sudo ufw status
Status: inactive
ubuntu@ubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.43.0/24       state RELATED,ESTABLISHED 
ACCEPT     all  --  10.42.43.0/24        anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ubuntu@ubuntu:~$ 
```

The netbook running Win XP had, as you might expect, IP address 10.42.43.0.

Now that I'm running my regular 9.10 install, I get what I showed above from iptables: that is, no rules active.  Must be that's the problem.

I'm not familiar with how to set up rules in iptables, or have them automatically reestablished every time I want to do ICS.  That's the next task.

---

### Post by Saghaulor on 2010-02-26
Objekt,

Like I said, I'm no expert re: iptables, but I think what you need is the following:

> Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.43.0/24       state RELATED,ESTABLISHED 
ACCEPT     all  --  10.42.43.0/24        anywhere            

---

### Post by leptogenesis on 2010-06-10
I may be necroposting, but I just encountered the same error and I came across this thread during the hour I spent trying to fix it...hopefully this will save somebody an hour.

I encountered an issue very similar to this--I tried to do internet connection sharing and network manager kept alternating between "connection established" and "disconnected".  I looked in /var/log/syslog and found the lines:

```

Jun 10 21:39:26 my-laptop dnsmasq[23384]: unknown interface eth1
Jun 10 21:39:26 my-laptop dnsmasq[23384]: FAILED to start up

```

Turns out the problem was with dnsmasq, which network manager apparently relies on in order to do ics.  It was trying to start on the wrong interface (/etc/dnsmasq.conf contained the line "interface=eth1", but eth0 was the one that my other computer was supposed to connect to).  Changing that configuration in /etc/dnsmasq.conf fixed the problem.

---

### Post by aaaantoine on 2011-01-11
The fix that worked for me:
> do you have dnsmasq-base package installed (also if you have the (full) dnsmasq package installed try to remove that as it might confuse some parts of NM).
Source: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/389006](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/389006)

I had the same symptoms as described earlier in this thread (constant connecting and disconnecting), and removing dnsmasq (but keeping dnsmasq-base) immediately solved it.

So, Objekt, I bet the reason why the LiveCD works but your installed OS doesn't is that your installed OS has dnsmasq installed and the LiveCD does not.

---

