---
title: "*-network DISABLED"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by llanitedave on 2010-05-22
I upgraded to 10.0.4 a week ago on my Dell Vostro 1720 laptop.  It's been working flawlessly -- until now.

I used Amarok last night to play some music from Magnatunes.  That was the last activity before going to bed.  I hadn't used Amarok since before the upgrade.

This morning, I found that my internet would not connect.  The connection icon on KDE showed an unplugged socket.  With a mouse hover the message read "Unmanaged".  Right clicking displayed "Network Management disabled".

I opened up Network Connection in System Settings, and it showed my wireless connection, and all the data in it was as before, but it would not connect.  

I ran "sudo lshw -C network" in my terminal, and this is what it showed:

```
dave@Dave-Dell-Linux:~$ sudo lshw -C network
[sudo] password for dave: 
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:f3:57:88
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:4000(size=256) memory:fe004000-fe004fff(prefetchable) memory:fe000000-fe003fff(prefetchable) memory:fe020000-fe03ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 00
       serial: 00:24:d6:4e:d8:ce
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:f6000000-f6001fff
dave@Dave-Dell-Linux:~$ 

```

So -- can anybody help me figure out why my network is disabled and what I can do to reactivate it?

BTW, I'm dual booting with Windows 7 and it works fine there.

---

### Post by purelinuxuser on 2010-05-22
Please post the output of
```
lspci
```
```
iwconfig
```
```
dmesg | grep -i iwlagn
```
so we can gain some information to help you.

---

### Post by llanitedave on 2010-05-22
```
dave@Dave-Dell-Linux:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)           
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)          
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)                
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)                   
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)                   
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)                   
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)                   
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GS] (rev a1)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)
dave@Dave-Dell-Linux:~$ 
```

```
dave@Dave-Dell-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

dave@Dave-Dell-Linux:~$ 
```

```
dave@Dave-Dell-Linux:~$ dmesg | grep -i iwlagn
[   19.212443] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   19.212446] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   19.212516] iwlagn 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   19.212525] iwlagn 0000:0e:00.0: setting latency timer to 64
[   19.212650] iwlagn 0000:0e:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   19.471453] iwlagn 0000:0e:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   19.471538] iwlagn 0000:0e:00.0: irq 33 for MSI/MSI-X
dave@Dave-Dell-Linux:~$ 
```

Thanks for looking at this.  Unfortunately I'm totally clueless about what I'm seeing here, and I need all the help I can get!

---

### Post by purelinuxuser on 2010-05-22
[SIZE=1][I]Everything looks fine to me- driver's loaded, no missing firmware, no weird messages in dmesg.

A common mistake that even experienced Ubuntu users make is accidentally toggling the WiFi killswitch and disabling their wireless.  Look around your laptop for a WiFi switch (if you still have your manual, you can probably find it in there).  If you don't have a physical one, try pressing your WiFi enable/disable button (Fn+F8 ).  Hopefully your wireless will be re-enabled... if it doesn't come on immediately, try restarting the computer.  Hope this helps!
[/I]
[SIZE=2]**Edit: I just NOW realized that all network interfaces were disabled, not just your wireless!  Sorry, my bad! :P**[/SIZE]
[/SIZE]

---

### Post by llanitedave on 2010-05-22
I looked around a little more, and located the /etc/network/interfaces file.

At the time, it only had the following lines:

[b]auto lo
iface lo inet loopback[/b]

I edited it, one section at a time.  When I added:

[b]auto eth0
iface eth0 inet dhcp[/b]

After restarting the network and running **sudo lshw -C network**,
the eth0 portion of the network was no longer diabled, the wireles (wlan0) still was.

I modified the file again to add 
[b]auto wlan0
oface wlan0 inet dhcp[/b]

And did it all again.  NOW I have eth0 disabled again, but not wlan0!  

I obviously still don't know what I'm doing.  Now I can finally see the wireless network, but I still can't connect to it.  The icon in my KDE panel shows bars, but the network identifier displays a key icon to the left of it, and when I click there nothing happens.

---

### Post by purelinuxuser on 2010-05-22
> **llanitedave said:**
> I looked around a little more, and located the /etc/network/interfaces file.

Err... not really the kind of file you want to be messing with if you plan on configuring your networking with Network Manager.  I have a few ideas for getting things back online:

[LIST=1]
[*]First things first, right click on the Network Manager applet and be sure "Enable networking" is checked.  Network Manager automatically disables all devices if this option is unchecked.
.
[*]If that didn't work, try running ```
sudo ifconfig wlan0 up
sudo ifconfig eth0 up
``` in a terminal.  If you get errors/problems then post the output of those commands.
.
[*]If all else fails, run "sudo service network-manager start" and post the output.
[/LIST]

---

### Post by llanitedave on 2010-05-23
1.  Interestingly enough, I may not even have the Network Manager applet on my panel in KDE.  I have two icons, one for "Wireless Connections" and one for Eth0.  When I try to open the full Network Manager Application from my applications menu, it doesn't respond.

2.  The two ifconfig commands gave me no output at all.  
3.  Starting the network-manager gave me the report that it's already running.

I ran "sudo service network-manager stop", and the network manager icon appeared on the panel where the unplugged socket icon had been.  However, I was still unable to start the Network Manager Application or get any response from the applet.

I ran start on network-manager again, and the response was "network-manager start/running, process 3067"

If it helps, below is a screen shot of the relevent portion of my panel.  It shows it's picking up the signal to my network.  But still, it's not doing anything WITH that signal!

[IMG]http://www.birdandflower.com/misc/networkPanel.png[/IMG]

---

### Post by purelinuxuser on 2010-05-23
*Edit: Revert the changes you made in /etc/interfaces before you perform these steps.*

Hmm... try running
```
killall nm-applet
nm-applet &
```to restart the Network Manager applet (that's for Gnome, but it should work in KDE too... I think :)).

After that, run the two ifconfig commands again.  HOPEFULLY that will fix things.  Otherwise, see if you can configure the wireless manually... not very ideal, but it will show us if the problem is with Network Manager or something else... :confused: You can find instructions on this here: [http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/](http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/) .  Be sure to run iwconfig at the end and post the output.

---

### Post by llanitedave on 2010-05-23
Thanks for sticking with me on this.  You've been a real hope through this mess.  I'll continue in the morning and implement your suggestions.

---

### Post by llanitedave on 2010-05-23
Well, I ran "killall nm-applet", and got a "no process found" response.

I input "nm-applet &" and got a suggestion that I should install it using apt-get install.

I think that's a hint that my network manager is either missing or corrupted.  My next step, I think, is to try to reinstall it, although I'll have to do that from a saved file since there's no install disk (and no internet on this machine!)

I also tried the crunchbag.org link and tried to follow the instructions given, but I got errors on the password step -- even though I used the caveats they provided about text passwords.  So for now, I'm still stuck.  'll keep trying to get the network manaer application or applet installed.

---

### Post by purelinuxuser on 2010-05-23
Hmm... I'm almost stumped!  Uhm, I guess you COULD try to reinstall nm-applet, but it's for GNOME and may not work at all on KDE.

You can find Ubuntu packages here: [packages.ubuntu.com]("http://ubuntuforums.org/packages.ubuntu.com")

---

### Post by llanitedave on 2010-05-23
I don't know if I'd call it "fixed" or even "solved", but 'm back on line.  I downloaded the .tar for Wicd (from another machine) and installed it.  It picked up the network, took my password, and I'm up and running!

---

### Post by purelinuxuser on 2010-05-23
> **llanitedave said:**
> I don't know if I'd call it "fixed" or even "solved", but 'm back on line.  I downloaded the .tar for Wicd (from another machine) and installed it.  It picked up the network, took my password, and I'm up and running!

Yeah, looks like Network Manager was the problem.  I'd mark the thread [SOLVED], and if you need more help, you can always mark it unsolved. :)

---

### Post by Marafarrico on 2010-09-10
I had the same problem with 10.04. I installed "Wicd Network Manager" from "Ubuntu Software Center" and I chosen to used wired connection whenever it is detected and after rebooting wired connections work now.

---

### Post by andriansah on 2011-03-20
Thank you for this thread. My problem is fix now

---

### Post by trauervoll on 2011-09-24
Hi folks!
I'm having the same problem. Here [http://pastebin.com/RbHxiEC8](http://pastebin.com/RbHxiEC8) are the relevant commands outputs. The workarounds didn't work to me =(

Any help? Thank's!

---

### Post by trauervoll on 2011-09-24
Hey, i just solved it:

I ran the command :~$ rfkill list all and could see that my wirelles was blocked than i ran :~$ rfkill unblock all and now everything is OK ;)

seeyah!

---

