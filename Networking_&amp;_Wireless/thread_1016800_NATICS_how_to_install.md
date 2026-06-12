---
title: "NAT/ICS how to install?"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by StGeorge on 2008-12-20
I have tried to ask this question with no decent answers for the last two years.

I have Ubuntu 8.10 desktop edition installed on this computer.
I wish this OS to be a gateway for other computers on my network.
I also have 98se on this computer.
When this computer is booted into windows 98se it is configured with ICS and Network Neighbourhood.(No problems for other computers to access internet and shared files and folders on the network through this computer).

What I wish to do is this:

I would like to use Ubuntu as my default OS.

I have never been able to because configuring it to act as a gateway for other computers, (we have XP and 98se on other computers), has been a nightmare.

I have read numerous links posted in forum replies but none of them work.

This computer uses a 5 port ethernet  switch from this computer and the modem to allow internet access for the other computers.

My connection settings show:
Auto eth0
IPv4 (automatic (DHCP)

Auto eth1
IPv4 (automatic (DHCP)

Has anyone any ideas how to do this?

---

### Post by mpokrywka on 2008-12-20
I assume that your network layout looks like this (GATEWAY=your computer with Ubuntu) and your GATEWAY has internet access working:

INTERNET <---> modem <---> eth0|GATEWAY|eth1 <---> switch and rest of computers

For this to work you need to configure your GATEWAY to give IP addresses for other computers in network. So you need to set static IP address on eth1 (internal), for example:
192.168.0.1 netmask 255.255.255.0

Next install "dnsmasq" and edit its configuration (/etc/dnsmasq.conf):
```
find line with "#interface=" and change it to "interface=eth1"
and
find line with "#dhcp-range=..." and change it to "dhcp-range=192.168.0.50,192.168.0.150,12h"

```
This means: on eth1 listen for requests and send addresses (dhcp) from given range.
After editing you probably need to restart dnsmasq **sudo /etc/init.d/dnsmasq restart**

For connection sharing you need your GATEWAY to perform NAT - add this rules to /etc/rc.local (before "exit 0"):
```
iptables -t nat -F
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```
This means that any packets exiting GATEWAY on eth0 will have source address translated to match eth0's address.
Run this script to activate rules: **sudo /etc/rc.local**

Last step: make sure that packets will be forwarded between eth0 and eth1.
Edit /etc/sysctl.conf and uncomment "net.ipv4.ip_forward=1" line.
To apply setting invoke **sudo sysctl -e -p**

That's all

---

### Post by StGeorge on 2008-12-21
Well that is the simplest solution I have yet been given in two years.
My problem now is that I tried various suggestions prior to reading your post and I now have NO internet connection at all.
I think I may have to re-install the OS as I cannot manually configure the internet connection through Network Tools or any other graphical tool supplied with Ubuntu.
I will not try it through Terminal as that is what got me into this mess I am now in. It is too time consuming.
I booted the live CD and took screenshots of the Network connections as the live CD had no problem connecting to the internet.
I can see where the errors are but as already stated I cannot manually configure anything with the graphical interfaces.
Probably another two years before I try again.
Will get back though if I succeed.

My Internet settings on this desktop are:
DNS Servers 194.168.4.100
IP Address 192.168.0.1
Subnet Mask 255.255.255.0

---

### Post by mpokrywka on 2008-12-21
I think reinstall is the fastest solution. You probably do not have many useful data on your Ubuntu system (and networking is not working), so popping live CD and install fresh will get you working system in half hour or so. Then follow four steps mentioned above and you should be done.

To minimize probability of IP addresses conflict you should use different IPs for your "internal" network. So in step 1 configure static IP for eth1:
address 10.0.0.1 netmask 255.0.0.0
and in step 2 use
dhcp-range=10.0.0.50,10.0.0.150,12h

There is one thing I am not sure - I have not installed fresh Ubuntu Hardy and Intrepid, but on upgrades I noticed that nowadays there is some firewall named "ufw" installed. This firewall will almost certainly conflict with step 3. My advice is to disable this firewall (**sudo ufw disable**), and if you are really concerned about "threats from internet" add one line to /etc/rc.local:
```

iptables -A input -i eth0 -m state --state NEW,INVALID -j DROP

```
This setting drops all connections attempt from internet (I assume eth0 provides you internet). Connections started from your machine will work without problem (similar to Windows XP firewall).

---

### Post by Iowan on 2008-12-21
I presume you've seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing"), but in case you  haven't...

---

### Post by mpokrywka on 2008-12-21
> **Iowan said:**
> I presume you've seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing"), but in case you  haven't...
There are few problems with above "help":
[LIST=1]
[*]That "$sudo" is misleading for novices. Because if one types exactly "$sudo id" in terminal it will not work as expected. This should be changed - dollar sign removed.
[*]There is no persistence in "gateway set up". This "$sudo ifconfig eth1 192.168.0.1" config will will vanish after reboot, so better advice would be to set static IP through GUI - I use kubuntu so I can't tell how Gnome menus are called. Manual configuration should probably not be done through network manager - network connection should be working before dnsmasq is started. Same about "configure NAT" and "Enable routing". I, at least, have told which files modify to make setting survive reboot.
[*]I do not like "Configure nat" config. When there is masquerade rule without outgoing interface specified, when user will want to configure port forwarding, real originating IP will be translated to "internal" IP.
[*]**dnsmasq** should be default choice for ICS because it is nearly hassle free for clients.
[/LIST]

---

### Post by StGeorge on 2008-12-21
Given Up for now.
Back into windows and will stay for a while.
Two days now of re installing, rebooting several computers and trying various advise (none of it works).
Cannot alter IP address. There is no graphical interface that makes this easy.
Cannot find any code for getting anything to work.
installed dnsmask. Even with commands nothing happens.
Often get told by Terminal that permission is denied even though I have auto login as administrator and there are no other users on this computer.
Thanks for trying though.
Will probably install Sabayon 3.5.1 over Ubuntu.
Told by a Geek that this is the real linux OS.
Never had a networking experience like this in 15 years.

---

### Post by mastermindg on 2008-12-21
Not sure what you're doing wrong St. George, but by following the directions of mpokrywka as well as disabling the firewall (ufw) my Gateway is working successfully between my Ubuntu Hardy server and my Wii :P

Just to clarify: 

You would need two separate devices (switch,router,etc) to do what you are wanting to do. So, if you are attempting to do this with one device it will fail.

---

### Post by mpokrywka on 2008-12-21
> Cannot alter IP address. There is no graphical interface that makes this easy.
You encouraged me to check, if this is really the case.
I got access to friends notebook with Ubuntu Hardy and I can tell you how exactly set static IP using GUI.
(excuse me my translation - I worked on non english ubuntu, so names may not be exactly accurate)

Step 0:
There is one problem: if you have many network cards you have to choose right one. Fortunately there is GUI tool to check this.
```
Menu System->Administration->Network tools
```
There is this list box "Network devices", pick one after another to see which one has IP address. Remeber name in parenthesis, for example (eth0)
This device which has IP address is your internet device.

Step 1:
Configuring static IP:
```
Menu System->Administration->Network
Click "Unblock"(Unlock?)

```
Now you should be paying attention to what I write.
```
Select wired connection and click "Properties",
look at window title, like "eth1 Properties"
and **MAKE SURE** this is **NOT** your internet device
(like eth0 that we found in step 0). 
(If you selected your internet device
then close this window and select another)
Uncheck "Roaming",
set configuration to "Static IP",
fill IP address and netmask,
leave Gateway blank.
Click OK to confirm.

```
done.

I understand you are tired of this ubuntu crap, but when you have more patience and try again,
stop at any step that tells you about permission problems. There should not be any.
I probably assumed that you know how to edit "protected system configuration files" (/etc/...). This can be done using:
Alt+F2 (there will be window "Run program")
and type:
**gksu gedit /etc/name_of_file_to_edit**

---

### Post by StGeorge on 2008-12-21
Ok guys since you have put so much effort into this I will try again tomorrow and post back.
I do appreciate your efforts.
It has driven me a little mad though.

---

### Post by StGeorge on 2008-12-21
OK I have:
Menu System->Administration->Network tools

I do not have:
Menu System->Administration->Network

I Have:
Menu System->Preferences->Network Configuration

I do not have anything that:
Click "Unblock"(Unlock?)

There are no:
"eth1 Properties"

There is no:
Uncheck "Roaming",

When I do edit IPv4 in eth1 it does not save and it does not ask me for a password.

Had enough again.
Thanks anyway.

---

### Post by mpokrywka on 2008-12-21
One question, what version of ubuntu is this? Intrepid?

---

### Post by StGeorge on 2008-12-22
Yes it is intrepid.
Ubuntu 8.10.
I appreciate your persistence in trying to help me with this mpokrywka.
After reading your reasons for using **dnsmask**:
> # I do not like "Configure nat" config. When there is masquerade rule without outgoing interface specified, when user will want to configure port forwarding, real originating IP will be translated to "internal" IP.
# dnsmasq should be default choice for ICS because it is nearly hassle free for clients.
I couldn't agree more as I was intending to put dual boot systems on three other computers. 2 clients with XP and another client with 98se. They will also have Linux as a second OS eventually.
There is also the possibility that I will put another two types of Linux and XP onto this computer, (the host). Configuring this computer to accept other computers on my network when it is in XP or 98se is no problem. In the past I have had no problem getting client computers with Linux to find this computer the host, when it booted into windows 98se.
The problem has always been getting Ubuntu to act as a gateway for client computers.
I now wonder if I should not simply install the server edition, but I am concerned that Ubuntu is not really up to this type of networking. I am not and have never been a command line computer user.
My first experience with computers started with Windows 95.
I have never needed the command line.

One thing of note is you asked if:

> I probably assumed that you know how to edit "protected system configuration files" (/etc/...). This can be done using:
Alt+F2 (there will be window "Run program")
and type:
gksu gedit /etc/name_of_file_to_edit

The answer is that in 2 years I have never been shown the above.
It is the most useful piece of information I have received in all this time.

---

### Post by dmizer on 2008-12-22
> **mpokrywka said:**
> There are few problems with above "help":
[LIST]
[*]That "$sudo" is misleading for novices. Because if one types exactly "$sudo id" in terminal it will not work as expected. This should be changed - dollar sign removed.[/list]
Thanks for pointing that out. I've updated the Wiki to remove the "$" from the commands.
> **mpokrywka said:**
> [LIST][*]There is no persistence in "gateway set up". This "$sudo ifconfig eth1 192.168.0.1" config will will vanish after reboot, so better advice would be to set static IP through GUI - I use kubuntu so I can't tell how Gnome menus are called. Manual configuration should probably not be done through network manager - network connection should be working before dnsmasq is started. Same about "configure NAT" and "Enable routing". I, at least, have told which files modify to make setting survive reboot.[/list]
If I recall correctly, that used to be persistent. If that is no longer the case, I will look for a different option.

It was a conscious decision to refrain from using GUI directions because of what you mentioned here:
> I use kubuntu so I can't tell how Gnome menus are called.
If I give GUI directions for Gnome (default Ubuntu install), people using Kubuntu or Xubuntu will not be able to follow the howto. As a long time user of Xubuntu and having run into a multitude of howto's which hinge on one small GUI edit (which has no Xubuntu equivalent), I've decided that the best way to write a howto is with CLI directions despite the general distaste for them.

> **mpokrywka said:**
> [LIST][*]I do not like "Configure nat" config. When there is masquerade rule without outgoing interface specified, when user will want to configure port forwarding, real originating IP will be translated to "internal" IP.[/list]
I am aware of this and have a better solution somewhere in my directory, but I'll need to dig it up.

> **mpokrywka said:**
> [LIST][*]**dnsmasq** should be default choice for ICS because it is nearly hassle free for clients.[/LIST]
The only reason I do not have it as default is because it requires correctly configuring the /etc/dnsmasq.conf with the correct interface and IP range. Since this information is difficult for people to get entered correctly, and OpenDNS servers can easily be entered via the GUI, I decided that dnsmasq is better suited as an advanced configuration.

Thank you for your input.

---

### Post by mpokrywka on 2008-12-22
> **dmizer said:**
> It was a conscious decision to refrain from using GUI directions...

Yeah, you are right, now I am wiser.
Bad thing is, even under the same flavour, GUIs constantly change,
and, as I noticed, they are sometimes broken (Itrepid static IP fiasco).
I strongly suggest that you should press fellow ubuntu developers
to fix it in Intrepid (not in some future release,
ship it as security update that anybody will install).
As a moderator you should tell them, how much pain
is working around that stupid bug.

---

### Post by dmizer on 2008-12-23
> **mpokrywka said:**
> I strongly suggest that you should press fellow ubuntu developers
to fix it in Intrepid (not in some future release,
ship it as security update that anybody will install).
As a moderator you should tell them, how much pain
is working around that stupid bug.

This can be resolved by installing the network admin like so:
```
sudo aptitude install gnome-network-admin
```

This will give you the same System > Administration > Network tool that existed in Hardy and all previous releases. I assume that installing "kde-network-admin" will have the same/similar effect in Kubuntu.

I really have zero pull with the developers.

---

