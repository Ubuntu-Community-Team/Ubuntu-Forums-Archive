---
title: "ip link - not showing eth0 or wlan0, only shows lo"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by Soulhuntor on 2013-02-17
Hello,

I just installed Ubuntu 12.04.2 and I am unable to get my internet to work.  When running $ ip link - it only shows lo

$ lspci | grep Ethernet
shows
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Can anyone help me get my internet working?

Thanks for any help.

---

### Post by TimeCrank on 2013-02-17
**Check that the device is on**

                                                                                             
[LIST=1]
[*]                       Many wireless network devices can be turned on  or off. Check to see if there is a hardware switch, some devices can be  switched off from Windows and may need to be turned back on from  Windows.
[*]                       If it is turned on then see [the section called &#8220;Check for device recognition&#8221;]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-device").
[/LIST]
                 
                                                                                                              **Check for device recognition**

                     
                   
                 
                                    
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: sudo lshw -C network
[/LIST]
                 
                 You should see an output, along with the words "CLAIMED, UNCLAIMED, ENABLED or DISABLED"
                                    
[LIST=1]
[*]                       Claimed - this indicates a driver is loaded but not functioning, see [the section called &#8220;Using Windows Wireless Drivers&#8221;]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper")
[*]                       Unclaimed - there is no driver loaded, see [the section called &#8220;Using Windows Wireless Drivers&#8221;]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper").
[*]                       Enabled - there is a driver loaded, see [the section called &#8220;Check for a connection to the router&#8221;]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-connection").
[*]                       Disabled - see [the section called &#8220;Check that the device is on&#8221;]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled").
[/LIST]
                 
               
                                                                                               **Using Windows Wireless Drivers**

                     
                   
                 
                 Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.
                                    
[LIST=1]
[*]                       Obtain the Windows Driver for your system and locate the file that ends with .inf.
[*]                       [Install the **ndisgtk** package]("apt:ndisgtk").
[*]                       Open **ndisgtk** (System &#8594; Administration &#8594; Windows Wireless Drivers).
[*]                       Select *Install new driver*.
[*]                       Choose the location of your Windows .inf file and click **Install**.
[*]                       Click **OK**.
[/LIST]
                 
               
                                                                                               **Check for a connection to the router**

                     
                   
                 
                                    
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: iwconfig.
[*]                       If the ESSID for our router is shown there may be a problem with ACPI support. Boot the kernel with the pci=noacpi option.
[/LIST]
                 
               
                                                                                               **Check IP assignment**

                     
                   
                 
                                    
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: ifconfig.
[*]                       If there is an IP address shown see [the section called &#8220;Check DNS&#8221;]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-dns").
[*]                       From the **Terminal** enter the command: sudo dhclient if_name where if_name is the connection listed earlier.
[*]                       If you receive a message that says bound to xxx.xxx.xxx.xxx then see [the section called &#8220;Check DNS&#8221;]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-dns")
[*]                       If not then reboot the system.
[/LIST]
                 
               
                                                                                               **Check DNS**

                     
                   
                 
                                    
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: ping -c3 85.190.27.2.
[*]                       Now type the command: ping [www.ubuntu.com](www.ubuntu.com). If you get a response from both then see [the section called &#8220;IPv6 Not Supported&#8221;]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ipv6").
[*]                       Type the command: cat /etc/resolv.conf.  If there is no nameserver listed then contact your ISP and find out  your primary and secondary domain name servers. Once you have this  information see [the section called &#8220;Wireless&#8221;]("https://help.ubuntu.com/10.04/internet/C/connecting-wireless.html").
[/LIST]
                 
               
                                                                                               **IPv6 Not Supported**

                     
                   
                 
                                    
[LIST=1]
[*]                       IPv6 is supported by default in Ubuntu and can sometimes cause problems.
[*]                       To disable it, open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
[*]                       Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
[*]                       Reboot Ubuntu.
[/LIST]

---

### Post by Soulhuntor on 2013-02-17
The wireless hardware switch is on, but that shouldn't matter for a wired connection right?

For lshw -C network
My wireless network controller doesn't say claimed, unclaimed, enabled or disabled.
For Ethernet it says UNCLAIMED

iwconfig
says
lo no wireless extensions

ifconfig
shows inet addr:127.0.0.1 for lo
pinging 127.0.0.1 works
pinging [www.ubuntu.com](www.ubuntu.com) says unknown host



> **TimeCrank said:**
> **Check that the device is on**

                                                                                             
[LIST=1]
[*]                       Many wireless network devices can be turned on  or off. Check to see if there is a hardware switch, some devices can be  switched off from Windows and may need to be turned back on from  Windows.
[*]                       If it is turned on then see [the section called “Check for device recognition”]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-device").
[/LIST]
                 
                                                                                                              **Check for device recognition**

                     
                   
                 
                                    
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: sudo lshw -C network
[/LIST]
                 
                 You should see an output, along with the words "CLAIMED, UNCLAIMED, ENABLED or DISABLED"
                                    
[LIST=1]
[*]                       Claimed - this indicates a driver is loaded but not functioning, see [the section called “Using Windows Wireless Drivers”]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper")
[*]                       Unclaimed - there is no driver loaded, see [the section called “Using Windows Wireless Drivers”]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper").
[*]                       Enabled - there is a driver loaded, see [the section called “Check for a connection to the router”]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-connection").
[*]                       Disabled - see [the section called “Check that the device is on”]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-disabled").
[/LIST]
                 
               
                                                                                               **Using Windows Wireless Drivers**

                     
                   
                 
                 Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.
                                    
[LIST=1]
[*]                       Obtain the Windows Driver for your system and locate the file that ends with .inf.
[*]                       [Install the **ndisgtk** package]("apt:ndisgtk").
[*]                       Open **ndisgtk** (System &#8594; Administration &#8594; Windows Wireless Drivers).
[*]                       Select *Install new driver*.
[*]                       Choose the location of your Windows .inf file and click **Install**.
[*]                       Click **OK**.
[/LIST]
                 
               
                                                                                               **Check for a connection to the router**

                     
                   
                 
                                    
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: iwconfig.
[*]                       If the ESSID for our router is shown there may be a problem with ACPI support. Boot the kernel with the pci=noacpi option.
[/LIST]
                 
               
                                                                                               **Check IP assignment**

                     
                   
                 
                                    
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: ifconfig.
[*]                       If there is an IP address shown see [the section called “Check DNS”]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-dns").
[*]                       From the **Terminal** enter the command: sudo dhclient if_name where if_name is the connection listed earlier.
[*]                       If you receive a message that says bound to xxx.xxx.xxx.xxx then see [the section called “Check DNS”]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-dns")
[*]                       If not then reboot the system.
[/LIST]
                 
               
                                                                                               **Check DNS**

                     
                   
                 
                                    
[LIST=1]
[*]                       Open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: ping -c3 85.190.27.2.
[*]                       Now type the command: ping [www.ubuntu.com](www.ubuntu.com). If you get a response from both then see [the section called “IPv6 Not Supported”]("https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ipv6").
[*]                       Type the command: cat /etc/resolv.conf.  If there is no nameserver listed then contact your ISP and find out  your primary and secondary domain name servers. Once you have this  information see [the section called “Wireless”]("https://help.ubuntu.com/10.04/internet/C/connecting-wireless.html").
[/LIST]
                 
               
                                                                                               **IPv6 Not Supported**

                     
                   
                 
                                    
[LIST=1]
[*]                       IPv6 is supported by default in Ubuntu and can sometimes cause problems.
[*]                       To disable it, open a **Terminal** (Applications &#8594; Accessories &#8594; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
[*]                       Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
[*]                       Reboot Ubuntu.
[/LIST]

---

### Post by sanderj on 2013-02-17
> **Soulhuntor said:**
> Hello,

I just installed Ubuntu 12.04.2 and I am unable to get my internet to work.  When running $ ip link - it only shows lo

$ lspci | grep Ethernet
shows
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Can anyone help me get my internet working?

Thanks for any help.

What's the output of:

```
lspci -nnk | grep -iA2 net

```

---

### Post by Soulhuntor on 2013-02-17
> **sanderj said:**
> What's the output of:

```
lspci -nnk | grep -iA2 net

```

lspci -nnk | grep -iA2 net

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
     Subsystem: Dell Device [1028:0228]
     Kernel modules: b44

0c:00.0 Network controller [0280]: broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
     Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
     Kernel driver in use: wl

---

### Post by sanderj on 2013-02-17
So both have drivers activated? Strange.

Is this a plain install of Ubuntu 12.04? Out of the box?

Can you try if the Wifi works?

And:  Start Software sources (via "Dash" in the upper left corner), and then click on the Additional Drivers tab. Does it show anything?

---

### Post by Soulhuntor on 2013-02-17
> **sanderj said:**
> So both have drivers activated? Strange.

Is this a plain install of Ubuntu 12.04? Out of the box?

Can you try if the Wifi works?

And:  Start Software sources (via "Dash" in the upper left corner), and then click on the Additional Drivers tab. Does it show anything?

Yes it is a plain install of Ubuntu 12.04.2

Wifi does not work either

Running Additional Drivers comes up with a window saying "Downloading package indexes failed, please check your network status. Most drivers will not be available." if I close that, the additional drivers window comes up, but nothing is there to enable.

---

### Post by sanderj on 2013-02-17
Can you use/borrow a USB (wifi) network dongle so that Ubuntu can download the addtional drivers?

---

### Post by Soulhuntor on 2013-02-17
> Can you use/borrow a USB (wifi) network dongle so that Ubuntu can download the addtional drivers?

Yeah, but wouldn't I possibly need to download some drivers for that?

I'm reinstalling Ubuntu now. I can get a wired connection working with the installer.  So I am going to download updates with the install and hopefully that fixes any problems.

Edit: Reinstalling with updates did not help.  Also with the first install, Ubuntu took ~30 seconds to boot, now it's taking ~90 seconds

---

### Post by Hadaka on 2013-02-17
Hi, it looks like your ethernet and wireless are conflicting
please do..

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
sudo modprobe b44
```

let us know if that works for you
thanks

---

### Post by Soulhuntor on 2013-02-17
> **Hadaka said:**
> Hi, it looks like your ethernet and wireless are conflicting
please do..

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
sudo modprobe b44
```

let us know if that works for you
thanks


Is it normal for the first command to take longer than 20 minutes?

It has been here for the last 20-30 minutes:
update-initramfs: generating /boot/initrd.img-3.5.0-23-generic

---

### Post by Hadaka on 2013-02-17
Hi, no thats not normal, it should just do it. You may have to boot
and try again. and before enter code:

sudo apt-get install linux-headers-generic

---

### Post by varunendra on 2013-02-18
> **Hadaka said:**
> it looks like your ethernet and wireless are conflicting
You mean b43 and wl are conflcting? Possibly.

*@ Soulhuntor,*
You can manually download linux-firmware-nonfree from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)

Once downloaded, you can install it by double-clicking on it.

After installing, make sure the sta driver is removed properly-
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```

Then do-
```
sudo modprobe -v b43
```
to bring your wireless up.

If it doesn't work or gives any errors, post back with errors.
Also, follow the 'Wireless Script' link in my signature and post back its results too.

Once the wireless is up, we can focus on ethernet.

---

### Post by varunendra on 2013-02-19
@ Soulhuntor,
Please try what I suggested above, this post is just for a heads up.

@ Hadaka,
I hope you wouldn't mind me sharing your PM here, as it is an important fact and would be beneficial for all if put here -

Hadaka's PM-
>  **b44,b43,wl info**
Hi, yes conflict,per the master chili55...b44 and b43 both
require the ssb module, however the wl/sta driver blacklists
the ssb module and throws b44 and b43 which both need it
into useless mode, i was unaware of this untill a couple
days ago when chili555 informed me about it..anyway
thought ide pass that info along.

First of all, a big Thanks for the heads up.

Secondly, I must admit that I had seen such cases before and was aware of this fact, somehow slipped my mind while posting earlier *(..and master chili555 would be very angry with me for overlooking that :()*.

However, the case where I first saw it was a conflict between b43 and b44 over ssb - who gets it first :)

If that happened here too, I *think* we may have to create a script to ensure b43 is loaded first and b44 later - after a gap of a few seconds. Although what I remember was a case with 10.04 (or maybe earlier), so hope it might have been sorted out in newer releases.

As for the blacklisting, I hope the custom blacklist file would automatically be removed while 'purging' wl driver (tested here). If not, we can do it manually.

Would be interesting to see what Soulhuntor comes up with to share with us.
Thanks again.

---

### Post by phungus on 2013-03-03
[SIZE=2]Newbie here. I am[FONT=arial] having the exact same problem as SoulHuntor. The PCI-ID is the same for both the ethernet and the WLAN cards. I also have the same output when I input "[COLOR=#000000]lshw -C network", "[/COLOR][COLOR=#000000]iwconfig", and "[/COLOR][COLOR=#000000]ifconfig". I then installed linux-firmware-nonfree. When I ran "[/COLOR][/FONT][/SIZE][COLOR=#000000][FONT=Ubuntu Mono][SIZE=2][FONT=arial]sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source", it output "E: Unable to locate package [package name]" for each of the packages I tried to purge. And when I run "sudo modprobe -v b43", the command is running for a very long time.

What should I try next? Thanks for the help![/FONT][/SIZE]
[/FONT][/COLOR]

---

### Post by praseodym on 2013-03-03
Load the LAN driver via```

sudo modprobe b44
sudo service network-manager restart
sudo apt-get install linux-firmware-nonfree
```
Both should work now. Maybe the LAN driver needs to be forced to load at boot-up. Once:
```

echo b44 | sudo tee -a /etc/modules
```

---

### Post by phungus on 2013-03-03
Thanks for the help! I ended up reinstalling the whole OS with an ethernet connection (first try was offline) and the ethernet driver was installed with the new installation. The wireless driver were installed easily with the two following commands that I got from [http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working](http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working).

Hope this helps SoulHuntor.

[LIST]
[*]
sudo apt-get remove bcmwl-kernel-source
[*]make sure that the firmware-b43-installer and the b43-fwcutter packages are installed


sudo apt-get install firmware-b43-installer b43-fwcutter
[/LIST]

---

