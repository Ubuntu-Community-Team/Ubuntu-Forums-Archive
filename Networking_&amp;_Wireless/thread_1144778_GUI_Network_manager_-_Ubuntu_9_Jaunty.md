---
title: "GUI Network manager - Ubuntu 9 Jaunty"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by yasheshb on 2009-05-01
Hello:

  I downloaded and installed the amd64 server DVD and am having problems doing network 
settings for my machine. 

  I read some articles [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)
but when i try - 

System - Administration

I only see Network Tools 
(no network manager).

Any help on how to get a GUI based network manager  ?
i also tried
apt-get install gnome-network-admin
and it gives an error message "package not found".

Thanks.

Yashesh

---

### Post by dmizer on 2009-05-01
Use the networking applet in the system tray by the clock (looks like a computer monitor).

If you don't have that, you can install network-manager-gnome

---

### Post by yasheshb on 2009-05-01
> **dmizer said:**
> Use the networking applet in the system tray by the clock (looks like a computer monitor).

If you don't have that, you can install network-manager-gnome

dmizer.

  thx. i right clicked on the networking applet by the clock 
and selected Edit Connections

  it shows the following - 1.png (Wired : Auto eth0)

then i clicked on  eth0 and Edit and it showed 2.png
and in the tab IP4 settings it shows 

Method: Automatic DHCP

I changed the Method to Manual and added my IP to Addresses and added the DNS servers
but the Apply button is greyed out.

Not sure if this is the correct way to do it. (3.png, 4.png)

so i thought well.. maybe this is not the network-manager-gnome so i tried to 
install it 
root@bfc33:~# apt-get install network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@bfc33:~# 

but looks like it's present.

i checked my FC6 box and the networking gui works pretty much like [http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-graphical-tool.html)

something wrong with my setup ?

yashesh

---

### Post by dmizer on 2009-05-01
Did you upgrade or is this a fresh install?

Please post the contents of this file: /etc/network/interfaces

---

### Post by yasheshb on 2009-05-01
this is fresh install.. and i added a few packages (mysql, php, apache etc) using Synaptic Package Manager.

root@bfc33:/etc/network# cat /etc/networks 
# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0

root@bfc33:/etc/network# cat /etc/network/interfaces 
auto lo
iface lo inet loopback

root@bfc33:/etc/network# uname -a
Linux bfc33 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

root@bfc33:/etc/network# hostname
bfc33

thx.

yashesh

---

### Post by yasheshb on 2009-05-01
hmm.. any insight ? did i mess up my installation ?

thx.

yashesh

---

### Post by tentwelveeight on 2009-05-01
> **yasheshb said:**
> hmm.. any insight ? did i mess up my installation ?

thx.

yashesh

Nah, you can always fix it. If you installed Gnome Network Manager you will find it under one of the other menus, like System->Network or something. It is a pretty straightforward manager from what I can tell. Perhaps using that tool will help you.

I too have difficulty understanding the new default network manager. I need to configure to NIC cards for an LTSP setup. I can get it to work with the old GNOME network manager just fine, but when I try to configure a static IP address for the eth1 using the new network manager I can't get it to work. I experience your same problem of aving the "apply" button greyed out until I also add a netmask. I put "255.255.255.0" as the netmask and the "apply" button comes alive and I click "apply" but I still can't boot my thin clients. I can look at "connection information" and it says that eth1 is connected to 192.168.0.1 like I want it to be, but my clients don't boot. What am I doing wrong?

---

### Post by yasheshb on 2009-05-04
i was finally able to figure out the greying out of the apply button. After i added the IP Address and Netmask, the apply button came alive :). i also had a bit of trouble adding the 2 dns servers (they need to be seperated by a comma - there's a tool tip help for it so hover on it for about 2 secs). 

after making these changes and clicking the apply button which files are changed ? i checked /etc/resolv.conf but that was
not updated...

yashesh

---

### Post by papangul on 2009-05-04
I had no luck in trying to set dns servers using NM. I had to set the "prepend domain-name-servers" parameter in /etc/dhcp3/dhclient.conf file.
Also don't forget to restart networking after changing the dhclient.conf, otherwise it would not take effect.

---

### Post by Panhead Bill on 2009-05-05
I'm having similar problems, with a possible workaround. 

Network manager seems to accept the info I enter; IP address, Subnet mask, Gateway, and DNS server. But when I click apply, the gateway changes momentarily to 0.0.0.0 and then grays out.

This wired connection fails to connect.


A workaround I stumbled onto:

If in the IPv4 tab, I just change the DHCP client ID to the address I want to be the static address, (while leaving the IPv4 method as "Automatic DHCP", it works.

The problem with this workaround is that the network manager icon is now "Red X'd" and the status info from it states that the computer is not connected (even though it really is connected).

Is this a possible bug?

---

### Post by wally42 on 2009-09-07
> **dmizer said:**
> Use the networking applet in the system tray by the clock (looks like a computer monitor).

If you don't have that, you can install network-manager-gnome


Yeah! That's all I needed to do !! now my laptop is on line!!!!

---

### Post by cdaaawg on 2010-02-04
I too was having nothing but trouble setting manual configuration for networking. I observed some very strange behaviour while futilely thrashing about trying to get a manual configuration set. Whenever I tried choosing Manual in the Method spin box, the Apply button would turn gray. Here is how I stumbled across a workaround:

Secondary click on NetworkMmanager applet icon in notification tray.
Primary click on Edit Connections
In the Network Connections dialog, primary click on the Wireless tab
Highlight your wireless ESSID and primary click on the Edit button.
This first time through, I was not challenged with a password request!
Primary click on IPv4 Settings tab
Enter an IP address in the DHCP Client ID field.
Click Apply.
Now I was challenged with a password request.
Testing the IP configuration with ifconfig, I observed that the IP address assigned to my host was not as I had set it, so I returned to the NM applet and retraced my steps. Lo and behold, as soon as I clicked the Edit button in the Wireless tab dialog, I was challenged for authentication! (Just the behaviour one would expect!) I was then able to choose Manual from the Method spin box and then set all the IP configuration parameters; address, net mask, and gateway (use the enter key after setting each parameter) as well as the DNS server addresses and the search domain, then clicking Apply. Restarting the networking daemon via /etc/init.d/networking restart did not set the DNS servers' addresses, so I went ahead and rebooted and everything worked fine from then on.

The fact that I was NOT challenged for authentication the first time through, thus disabling manual configuration and the Apply button is a bug if I ever saw one.

I hope this helps someone, although it has been many months since this thread was started. I know I have been struggling with some other networking configuration issues (like being nagged for authentication to connect to a network I have never connected to before and being unable to uncheck the Connect Automatically box), all most likely due to to this failure by the NM applet to authenticate properly.

I think Ubuntu management needs to take a hard look at their 6 month release cycle policy. Critical things like this that seem to break with each new "upgrade" will drive a lot of folks away from their distro, me included.

---

