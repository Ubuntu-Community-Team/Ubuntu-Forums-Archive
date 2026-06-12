---
title: "Ubuntu Re-boot Gets Stuck On &quot;Configuring Network Interfaces&quot;"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by umechanism on 2009-03-20
OS = 32 Bit Ubuntu 8.10
Computer = Dell Studio Desktop
Interface = Wired Ethernet,  Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

My network connection had been working fine until I decided to assign a static IP address to my desktop.  I Googled around for "command line network configuration" because I've not had good success with Gnome's Network Manager.  I found a nice article that laid out all the things I needed to do.  Namely, remove Network Manager then edit /etc/network/interfaces and add the appropriate ip address, gateway, etc.  Very straight forward.

However, rebooting my machine proved to be a mistake.  Ubuntu would get stuck at "Configuring Network Interfaces".  I could use CTL-ALT-DEL to force it on but, once booted, I had no Internet connection.  I immediately try to undo what I had done - I reinstalled Network Manager and configured my /etc/network/interfaces file back to what it was before I did all of this.

Ubuntu still gets stuck.  And, oddly, none of my remote shares on my NAS are mounted automatically as directed by my fstab file.  This used to work to but now it doesn't!  

Here is my /etc/network/interfaces file as it is today:
```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp 
auto eth0
iface eth0 inet static
address 192.168.2.109
netmask 255.255.255.0
gateway 192.168.2.1

```

Here is a list of my interfaces;  

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 3
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3450
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
03:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
michael@ubuntu-dell:~$ 


```

Please help if you can.

---

### Post by umechanism on 2009-03-20
Should I just comment out everything in my /interfaces file and use network manager to configure the connections?  

I'm going nuts!#-o

---

### Post by seb_renaud on 2009-03-21
Hi,

I am not sure if this will help, but I have a similar situation as yours:
I edited the /etc/network/interfaces ( and resolve.conf ) files, but I did not remove network-manager. I deleted all the connections lists in network-manager. The end result is that I have the network setup I want, but strangely enough, if I right-click on the network manager and untick Enable Networking, the network interface is really disabled( even if none are configured).

I am writing all this in case that you did not have the networking set to "Enabled".

I will investigate this further, and will come back here to let you know if I find anything else.

---

### Post by Detonate on 2009-03-21
Are you connecting through a router, or are you directly hooked to a DSL or cable modem?  Have you verified that the static IP address you are trying to use is one that is available?  Are you sure the gateway is correct?

---

### Post by rplantz on 2009-03-21
> **Detonate said:**
> Are you connecting through a router, or are you directly hooked to a DSL or cable modem?  Have you verified that the static IP address you are trying to use is one that is available?  Are you sure the gateway is correct?

I am having the same problem. I sorta fixed it by adding my static IP address through NetworkManager and commenting out everything in /etc/network/interfaces:
```

bob@bob-desktop:~$ cat /etc/network/interfaces
#auto eth0
#iface eth0 inet static
#address 192.168.1.47
## network 192.168.1.0
#netmask 255.255.255.0
## broadcast 192.168.1.255
#gateway 192.168.1.1

```
then using NetworkManager to give:
```

bob@bob-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        00:50:8D:71:3B:1D

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         192.168.1.47
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```
I am connected to a router, which is connected to a DSL modem. My router is still set to act as a DHCP server for other machines on my LAN.

The problem is that when I reboot this machine "Auto eth0" takes over and gives me a dynamic IP address. I have to use the NetworkManager applet to manually switch to the static IP address. Yes, I have tried unticking "Connect automatically" and "System setting" in the "Auto eth0" configuration, and ticking them in my static configuration.

It's all workable, but it bothers me that the /etc/network/interfaces file doesn't work correctly.

BTW, does anyone know which files NetworkManager uses?

---

### Post by Detonate on 2009-03-21
I'm not sure what is going on with yours, but that's the reason I remove all network managers.  I just edit my interfaces file, and resolv.conf and go with that.  I suspect the OP's problem has to do with the static IP address he chose, and his gateway IP.

---

### Post by rplantz on 2009-03-21
> **Detonate said:**
> I'm not sure what is going on with yours, but that's the reason I remove all network managers.  I just edit my interfaces file, and resolv.conf and go with that.  I suspect the OP's problem has to do with the static IP address he chose, and his gateway IP.

This would be my preference. And when I read the comments in Synaptic: "NetworkManager ... is intended only for the desktop use-case, and is not intended for usage on servers." I have set up a web server (private on my LAN) for experimentation and learning.

Perhaps the two systems -- interfaces vs. NetworkManager -- are "fighting" each other during boot.

My resolv.conf file is
```

bob@bob-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1

```

Do my settings look reasonable?

BTW, I apologize if this seems to be hijacking the OP's thread. I was thinking that my questions would shed more light on his/her problems.

---

### Post by Detonate on 2009-03-21
This is what my interfaces file looks like.  Work's perfectly with no network manage installed to screw it up.

[B]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

#iface eth0 inet dhcp
[/B]

And my resolv.conf file:

[B]domain domain.actdsltmp
search domain.actdsltmp
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.0.1[/B]

Note that I am using the nameservers from OpenDNS, and I have the same entries in my roiuter for nameservers.

Works perfectly for me.

---

### Post by rplantz on 2009-03-21
> **Detonate said:**
> This is what my interfaces file looks like.  Work's perfectly with no network manage installed to screw it up.

And my resolv.conf file:

[B]domain domain.actdsltmp
search domain.actdsltmp
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.0.1[/B]

Note that I am using the nameservers from OpenDNS, and I have the same entries in my roiuter for nameservers.

Works perfectly for me.

Thank you very much! It works!

The only difference in my set up is that I am using my ISP for DNS. So I have:
```

bob@bob-desktop:~$ cat /etc/resolv.conf
# Where to look for names
nameserver 192.168.1.1

```

and the DNS entries in my router are 0.0.0.0

ifconfig shows that this machine has the static IP address I assigned in /etc/network/interfaces (following your example), and my other machines get their IP addresses from my router's DHCP server.

And it no longer hangs for five minutes at network configuration during reboot.

Thanks again for your help.

---

### Post by umechanism on 2009-03-21
> **Detonate said:**
> Are you connecting through a router, or are you directly hooked to a DSL or cable modem?  Have you verified that the static IP address you are trying to use is one that is available?  Are you sure the gateway is correct?

Yes, I am connecting through a router and the IP address is available.  Thanks for the reply!

Mike

---

### Post by Detonate on 2009-03-21
Have you tried using the settings I posted above, modified for your system of course, and after removing network manager?

---

### Post by rplantz on 2009-03-21
> **umechanism said:**
> Yes, I am connecting through a router and the IP address is available.  Thanks for the reply!

Mike

In addition to following Detonate's /etc/network/interfaces file and using the /etc/resolv.conf file I show above, I also used synaptic to "completely remove" network-manager, network-manager-gnome, and firestarter. I don't know if these actions had any effect on my positive results.

Bob

---

### Post by umechanism on 2009-03-21
I've tried all these suggestions but mine still gets stuck while booting up.  Is my resolve.conf file correct?

```
nameserver 205.152.37.23
nameserver 205.152.150.23
```

and my network interfaces:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#iface eth0 inet dhcp 
auto eth0
iface eth0 inet static
address 192.168.2.109
netmask 255.255.255.0
gateway 192.168.2.1

```

---

### Post by rplantz on 2009-03-21
> **umechanism said:**
> I've tried all these suggestions but mine still gets stuck while booting up.  Is my resolve.conf file correct?

```
nameserver 205.152.37.23
nameserver 205.152.150.23
```



umechanism, I assume these are DNS addresses you got from your ISP? When I tried that, the hanging did not go away. Using the IP address of my router
```

nameserver 192.168.1.1

```
works for me.

Bob

---

### Post by Detonate on 2009-03-21
What is the make and model of your router?

---

### Post by rplantz on 2009-03-21
> **Detonate said:**
> What is the make and model of your router?

Don't know if this is directed at me, but mine is a TrendNet TEW-452BRP. I got it on sale about a year ago for almost nothing.

BTW, despite the low cost of this router, tech support at TrendNet has been excellent. When I was first trying to set a static IP address, I asked them. They were very helpful. Their tech even sent me a link, [http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/) , to help me. That got me to the point of the hanging problem, and your remarks helped me solve that. I have no financial stake in TrendNet. I mention my experience with them because most of us are quick to complain about bad service, and I think it's just as important to acknowledge good service.

---

### Post by umechanism on 2009-03-21
> **rplantz said:**
> umechanism, I assume these are DNS addresses you got from your ISP? When I tried that, the hanging did not go away. Using the IP address of my router
```

nameserver 192.168.1.1

```
works for me.

Bob

Bob,

I obtained those DNS addresses by going to my Window's Vista laptop and typing "ipconfig" which works that same as "ifconfig" in Linux.  It listed those DNS servers so that is what I put in my config file.

I did not know that you can use the IP address of your router to obtain DNS addresses.  Perhaps I'll try the same.  Mine is a Linsys WRT54G.

---

### Post by umechanism on 2009-03-21
> **Detonate said:**
> What is the make and model of your router?

Linksys WRT54G.

---

### Post by Detonate on 2009-03-21
I think the OP has his gateway wrong.  That's why I was wondering what his router is, if I had that info I could google it and come up with the correct settings.

---

### Post by Detonate on 2009-03-21
Well I don't even have to look that one up.  Your Gateway should be 192.168.1.1

and the static IP address you want to use should be 192.168.1.(some number in the routers capabilities by outside the ones reserved for DHCP  and don't use 192.168.1.0 or 192.168.1.1 or 192.168.1.256 as these are reserved for the router.  To access the settings in your router enter 192.168.1.1 in the location bar of your browser.  If this is the first time you have looked at this it will ask for a user name and password.  Leave the user name blank and enter "admin" (without the quotes) in the password field.  Once in there, you will be able to see stuff such as where the dhcp numbers start, and the dns entries.

---

### Post by Detonate on 2009-03-21
I originally wrote this for Kubuntu users, but the same instructions will work in gnome or xfce, just change the commands as necessary.

Recently there seems to have been a lot of posters with problems  getting their internet connection working with a wired connection.  Many of these problems seem to be related to the network manager not working correctly.  This could be Knetworkmanager, in Kubuntu 8.04 and earlier, and network-manager-kde in 8.10.

It's nice to have a GUI to help with setup of things, but sometimes they just don't seem to work.  In fact, sometimes they actually break a working system.  So I'm going to explain, step-by-step how to get things working for your network and internet without using the GUI.

First thing you should do is remove any network managers you have installed.  The reason we remove them is because, once you get your network up and running, those programs will try change things in the files we are going to edit, and possibly break things again.  Open a terminal and, depending on your version of Kubuntu, issue one of these commands.

For 8.10

```
sudo apt-get remove network-manager-kde
```

```
sudo apt-get remove network-manager
```

For 8.04 and earlier

```
sudo apt-get remove network-manager-kde
```

```
sudo apt-get remove knetworkmanager
```

```
sudo apt-get remove network-manager
```

And remove any other networking managers you may have installed.

Now we need to make sure that your system is actually recognizing your ethernet hardware.
Issue the command ```
ifconfig
``` in a terminal, and you will quickly see what interfaces are currently active.  Hopefully you will see at least eth0 and lo listed.  If not, you need to get eth0 working, and that is beyond the scope of this howto.  Search the forum for information on getting your network card up and running, then come back here.

Next you will need to edit two files.  The /etc/network/interfaces file and the /etc/resolv.conf file.  Be sure and back up both files before editing them.

Open the interfaces file by issuing the command kdesudo kate /etc/network/interfaces in a terminal.  When kate opens you should see something like this.
[b]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp
[/b]If your file doesn't look like this, edit it.  Then save the file.  You should now be able to connect to a dhcp server, which is your router or cable/dsl modem if you are not using a router.  This setup will get you running with DHCP.  If you want to use a static IP on your network, you would change the line
**iface eth0 inet dhcp**
to read
**iface eth0 inet static**

and then enter the following lines below that.
[b]address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.0.1[/b]

Modify these lines for your system.  The address must be one that will be recognized by your router and outside the DHCP address your router assigns, if DHCP is enabled in you router.

The gateway also must be the gateway of your router.

[color=red]The following info is only for using a static IP. If you are using dhcp you should not have to edit the resolv.conf file.
[/color]

But before you get connected, we need to tell your computer  where to find the domain name server. (DNS)

That is the function of the /etc/resolv.conf file.

So let's open up that file with kate (or any text editor) by issuing the command kdesudo kate /etc/resolv.conf in a terminal.

This is what mine looks like.

[b]nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.0.1[/b]

You can have up to three nameservers listed in resolv.conf.   These are the places where information is stored that resolves urls into IP addresses.  The first two listed above are for OpenDNS which is the DNS server I have been using for a long time.  The last one is for my router where information is kept to allow you to access other computers on your network.

In your file, you want to put the nameserver (DNS) that matches the one listed in your router or modem.  You will need to access the setup page from a browser to find out exactly what that is.  You can find out how to do this by consulting you router or modem documentation.

Here's a shot of the page in my router's setup that shows us the info we need.

  [[IMG]http://img145.imageshack.us/img145/4396/router2cm4.th.png[/img]](http://img145.imageshack.us/my.php?image=router2cm4.png)

Edit your file to include those DNS's listed in your router's or modems setup, preceded by the word "nameserver" before each.  Save the file (you did make a backup earlier didn't you)?

Now we are ready to see if it works.  Issue the following command in a terminal.

```
sudo /etc/init.d/networking restart
```

See:
man interfaces
man resolv.conf

Note:  I used the command kdesudo but in you have KDE 3.5.* you will use kdesu instead.  And when I said "router" that could also refer to your modem if you are connected directly without a router.  And of course you can substitute any text editior for "kate".

Please feel free to point out any mistakes or other helpful hints.

---

### Post by umechanism on 2009-03-21
> **Detonate said:**
> Well I don't even have to look that one up.  Your Gateway should be 192.168.1.1

and the static IP address you want to use should be 192.168.1.(some number in the routers capabilities by outside the ones reserved for DHCP  and don't use 192.168.1.0 or 192.168.1.1 or 192.168.1.256 as these are reserved for the router.  To access the settings in your router enter 192.168.1.1 in the location bar of your browser.  If this is the first time you have looked at this it will ask for a user name and password.  Leave the user name blank and enter "admin" (without the quotes) in the password field.  Once in there, you will be able to see stuff such as where the dhcp numbers start, and the dns entries.

Thanks for the help.  I checked my router settings and the router's IP address is 192.168.2.1.  I've attached an image showing my setup.

Does this look correct?

Also, if my settings were not configured correctly, how then am I able to get online to type this message?  I'm using ubuntu now.  I just had to hit CTRL-ALT-DEL to force the boot to finish.  I'm not totally convinced that my network settings are incorrect.

---

### Post by Detonate on 2009-03-21
I find it strange that your router settings are different ffrom mine, but go ahead and try those settings and see if you can connect.

---

### Post by umechanism on 2009-03-21
I am connected.  That's just it.  My problem isn't that I can not connect (I'm connected now as I type via ubuntu).  My problem is that Ubuntu gets stuck on "Configuring Network Interfaces" during bootup and I have to hit "CTRL-ALT-Del" to force it to finish.  Once it is fully booted, and the desktop is visible, I can connect but none of my remote shares are mounted by fstab (they were before I made these network changes).  I then have to mount them all manually.

---

### Post by Detonate on 2009-03-21
Let me see the contents of your fstab.
(Going to bed soon, so don't expect a reply tonight)

---

### Post by umechanism on 2009-03-21
> **Detonate said:**
> Let me see the contents of your fstab.
(Going to bed soon, so don't expect a reply tonight)

Here is my fstab
```
#Volume 1 Mounting 320 Gig
#//192.168.2.102/shares/Volume1/FileShare /mnt/hpmediavault/Volume1/FileShare cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0
//192.168.2.102/FileShare /mnt/hpmediavault/Volume1/FileShare cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0

//192.168.2.102/Backup /mnt/hpmediavault/Volume1/Backup cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0
//192.168.2.102/CinemaNow /mnt/hpmediavault/Volume1/CinemaNow cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0
//192.168.2.102/MediaShare /mnt/hpmediavault/Volume1/MediaShare cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0


#Volume 2 Mounting 1TB 
//192.168.2.102/Images /mnt/hpmediavault/Volume2/Images cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0

```

Thanks for the help.

---

### Post by capscrew on 2009-03-21
@ umechanism,

I see one quick problem in your jpg.  You are assigning a static address that is part of the dhcp pool.  The pool (100 -149) should be used **ONLY** for dhcp clients.  Modify your /etc/network/interfaces file in this manner:

```
address 192.168.2.175 
```

Any number outside of the pool will.  I arbitrarily picked 175.

---

### Post by Detonate on 2009-03-22
I think capscrew is right.  You probably developed those fstab entries by checking the IP of your Windows computer, and using that IP.  Problem is that was a dynamic IP.  At some time later that computer was rebooted and the IP changed.  So you need to also set your windows computer with a static IP and us that IP in your fstab entires.  I have not used samba in a very long time so I can't comment on the rest of those entries.

To check a couple of things,

In a terminal, issue:

sudo mount -a

and see if that produces any error messages that might be helpful.

Also see if you can ping 192.168.2.102

---

### Post by Detonate on 2009-03-22
Also open up your router interface in your browser again and go to Setup and in Basic Setup you should see a page like this.

[[IMG]http://img140.imageshack.us/img140/7389/routerj.th.png[/IMG]](http://img140.imageshack.us/my.php?image=routerj.png)

Then you can see what addresses you are using for your DHCP.  In mine in the picture you can see that I allow 50 DHCP users starting at 192.168.1.100.  That means I cannot use addresses from 192.168.1.100 through 192.168.1.149 for my static IP addresses.

---

### Post by umechanism on 2009-03-22
> **capscrew said:**
> @ umechanism,

I see one quick problem in your jpg.  You are assigning a static address that is part of the dhcp pool.  The pool (100 -149) should be used **ONLY** for dhcp clients.  Modify your /etc/network/interfaces file in this manner:

```
address 192.168.2.175 
```

Any number outside of the pool will.  I arbitrarily picked 175.

I reconfigured my IP address to 192.168.2.175 but Ubuntu still got stuck during boot time.  This is driving me crazy....
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#iface eth0 inet dhcp 
auto eth0
iface eth0 inet static
address 192.168.2.175
netmask 255.255.255.0
gateway 192.168.2.1

```

---

### Post by umechanism on 2009-03-22
> **Detonate said:**
> Also open up your router interface in your browser again and go to Setup and in Basic Setup you should see a page like this.

[[IMG]http://img140.imageshack.us/img140/7389/routerj.th.png[/IMG]](http://img140.imageshack.us/my.php?image=routerj.png)

Then you can see what addresses you are using for your DHCP.  In mine in the picture you can see that I allow 50 DHCP users starting at 192.168.1.100.  That means I cannot use addresses from 192.168.1.100 through 192.168.1.149 for my static IP addresses.

Detonate,

I have attached an image of my basic setup for my router.  One difference is that you have specified a Static DNS1 and a Static DNS2 where as I have not.  Should I have specified this?  I'm using this router connected to a DSL modem.  

If I should specify these entries, do I use the ones I get when I type "ipconfig" in my Windows laptop?

Thanks for the help.

---

### Post by Detonate on 2009-03-22
You must configure the other computer with a IP that matches the IP you are trying to use to mount your remote shares.  You must use an IP outside of the DHCP range.  Is the Windows computer set up to use a static IP?  What is It?

---

### Post by umechanism on 2009-03-22
> **Detonate said:**
> You must configure the other computer with a IP that matches the IP you are trying to use to mount your remote shares.  You must use an IP outside of the DHCP range.  Is the Windows computer set up to use a static IP?  What is It?

There are three machines on my network.  
[LIST=1]
[*]Windows Laptop - IP 192.168.2.100
[*]HP Media Vault (NAS) - IP 192.168.2.102
[*]Dell Desktop (Ubuntu) - IP 192.168.2.175 (recently changed)
[/LIST]

The HP Media Vault is the remote share that I am trying to mount in my fstab config file.

---

### Post by Detonate on 2009-03-22
OK, I don't know how to configure that.  You say it was working before?  When you set up the shares in the HP Media Vault were you required to enter the specific machines or users that are allowed to access those shares?  Did you run sudo mount -a in a terminal to see what errors are produced?  Can you ping 192.168.2.102?

---

### Post by umechanism on 2009-03-22
Here is the ping:
```
PING 192.168.2.102 (192.168.2.102) 56(84) bytes of data.
64 bytes from 192.168.2.102: icmp_seq=1 ttl=64 time=2.24 ms
64 bytes from 192.168.2.102: icmp_seq=2 ttl=64 time=0.185 ms
64 bytes from 192.168.2.102: icmp_seq=3 ttl=64 time=0.175 ms
64 bytes from 192.168.2.102: icmp_seq=4 ttl=64 time=0.178 ms
64 bytes from 192.168.2.102: icmp_seq=5 ttl=64 time=0.183 ms
64 bytes from 192.168.2.102: icmp_seq=6 ttl=64 time=0.150 ms

```

As far as configuring the Media Vault - it consists of a couple of hard drives.  You just create folders on the hard drives and save files in the appropriate folder.  So, the "Backup" folder will have my backup files in it, "FileShare" has unprotected files like mp3's, documents, etc...that I share on the network...and so on and so forth.  They're just folders on a remote hard drive accessed like any Network Attached Storage device.

Typing "sudo mount -a" yields no errors but it does require me to enter my password for each folder that I am mounting which is unusual.
```
michael@ubuntu-dell:~$ sudo mount -a
[sudo] password for michael: 
Password: 
Password: 
Password: 
Password: 
Password: 
michael@ubuntu-dell:~$ 


```
Previously, typing my password one time was sufficient to mount all folders at the same time.  Curious.

---

### Post by umechanism on 2009-03-22
Success!

Well, sort of.  I went into the fstab config file and commented out all the remote shares.  I saved, rebooted, and my machine booted without a hitch.  So...I've got something wrong with my fstab config file that I'll need to work through -----again.  I just got that dang thing working the other day and it is funny that it all "went bad" after I made the changes to my /etc/network/interfaces file.

No matter...I'll take my questions over to the HP Media Vault's forum and bug those fellers.  Thank you for all of your help!

---

### Post by Detonate on 2009-03-23
I don't think the problem has anything to do with your interfaces file changes.  It's a permissions problem.  But I don't understand it, because you run fstab as sudo, they should mount without asking for your password.  Good luck!!

---

### Post by umechanism on 2009-04-04
> **Detonate said:**
> I don't think the problem has anything to do with your interfaces file changes.  It's a permissions problem.  But I don't understand it, because you run fstab as sudo, they should mount without asking for your password.  Good luck!!

You were correct.  It was a permissions problem.  The remote share had no password set on it but Samba/Linux needed one to make it work so I inserted a username/password field in my fstab and all is working great.  No more getting stuck.  Here is an example of the fstab now:
```
/192.168.2.176/Backup /mnt/hpmediavault/Volume1/Backup cifs username=michael,password=igofast,_netdev,uid=michael,gid=users 0 0
```

It is working like a charm now.  I hope this helps someone.

---

