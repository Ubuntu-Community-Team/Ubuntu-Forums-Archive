---
title: "LiveCD has wifi but not installation..."
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by thunderloki on 2011-07-13
Hi all,

I can't get wifi in my Desktop 64 installation, but I can in LiveCDs and in Windows.  I have an AirLink101 wireless-n card using the Ralink RT2860 driver (which apparently is not installed in Ubuntu Desktop, but IS installed in Server.  attempted modprobe rt2860sta resulted in no such luck, citing a missing server directory.)

[http://ubuntuforums.org/showthread.php?t=1795305&page=4](http://ubuntuforums.org/showthread.php?t=1795305&page=4) details my struggles to get this card operating in Server.  I thought I might have more luck with Desktop, but to no avail.

The real question is: WHY would this card work in LiveCD but NOT in Desktop or Server installations??  This just doesn't make sense to me.  Any help would be appreciated.  I really, REALLY want to get this system up and running and have been battling it for days now.  Thanks in advance for any thoughts or suggestions.

---

### Post by thunderloki on 2011-07-15
bump?  been wrestling with this problem for over a week...

---

### Post by varunendra on 2011-07-16
> **thunderloki said:**
> ....
The real question is: WHY would this card work in LiveCD but NOT in Desktop or Server installations??
While in Live session, please run and post outputs of these:
```
sudo lshw -C network
```
```
rfkill list all
```
and,
```
iwconfig
```

then reboot into installed version and run the same commands and post their outputs. This, as you might have already guessed, is to see the driver/configuration difference in both modes.

---

### Post by Nepenthes73 on 2011-07-16
I've had the same problem when I upgraded from 10.04 to 10.10 and to 11.04. Eventually I just went back to 10.04, and have been having no network problems since then...until today.

I just installed the latest kernel (and other upgrades) from 'Update Manager' and low and behold, network connections aren't working. Currently I'm working off the CD.

---

### Post by thunderloki on 2011-07-16
sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:24:8c:19:54:eb
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:69 memory:fbdfc000-fbdfffff ioport:d800(size=256) memory:fbdc0000-fbddffff
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 12
       serial: 00:24:8c:19:54:ea
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:70 memory:fbafc000-fbafffff ioport:a800(size=256) memory:fbac0000-fbadffff
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:09:01.0
       logical name: wlan0
       version: 00
       serial: 00:21:2f:38:3a:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.1.71 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbef0000-fbefffff

``` (The RaLink is the one in question.)

rfkill list all:
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Eyes Only"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Eyes Only (correct hex tho)   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:35   Missed beacon:0
```

lsmod | grep rt
```

parport_pc             36959  0 
parport                46458  3 parport_pc,ppdev,lp
rt2860sta             543010  0 
rt2800pci              18535  0 
rt2800lib              45181  1 rt2800pci
crc_ccitt              12667  2 rt2860sta,rt2800lib
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
scsi_transport_sas     40545  2 mvsas,libsas
```

---

### Post by thunderloki on 2011-07-16
lshw -C network: ```
 RT2760 Wireless blah blah... driver=rt2860 wireless=Ralink STA logical name: wlan0
```
rfkill list all: no results
iwconfig: ```
Ralink STA ESSID:"" Nickname:"RT2860STA" Correct Access Point, Correct channel, Bit Rate=1 Mb/s ... no signal, etc. 
```

Hope that helps -- I can give you more info from the second output if necessary, not too clear on how to copy it into a .txt on a USB and transfer it over.  But that should be the relevant info.  Oh yeah, and:

I blacklisted rt2800pci and rt2x00pci, and removed them from lsmod.  So lsmod only returns rt2860sta.  Hope this helps you help me!  hehe.  Thanks again!

---

### Post by nm_geo on 2011-07-16
thunderloki

Did you reboot after the blacklist addition?  You did have a driver conflict going on for sure. Like the one below...

[http://ubuntuforums.org/showthread.php?t=1749179&page=2](http://ubuntuforums.org/showthread.php?t=1749179&page=2)

---

### Post by varunendra on 2011-07-17
Well, you didn't make it clear which of your outputs belong to which mode. So assuming they are in the same sequence as I asked (live (working) mode first and regular non-working mode second post), then you have blocked the wrong drivers.

From your first post (assuming it was from live, working mode):-
> **thunderloki said:**
> sudo lshw -C network
```
....
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: Ralink corp.
....
....
       configuration: broadcast=yes [COLOR=DarkRed]**driver=rt2800pci **[/COLOR]driverversion=2.6.38-8-generic 
```....
....


And your second post (assuming it is from installed, non-working mode):-
> **thunderloki said:**
> lshw -C network: ```
 RT2760 Wireless blah blah... [COLOR=Red]**driver=rt2860**[/COLOR] wireless=Ralink STA logical name: wlan0
```.  ....Oh yeah, and:

**I blacklisted rt2800pci and rt2x00pci, and removed them from lsmod.  So lsmod only returns rt2860sta**.  Hope this helps you help me!  [COLOR=Purple]**hehe**[/COLOR].  Thanks again!
well....[COLOR=Purple]***hehe,* **[/COLOR] but if I'm guessing right then you need to blacklist rt2860, not rt2800pci.

Please confirm /clarify the situation.

---

### Post by thunderloki on 2011-07-17
@nm_geo, thanks for the suggestion.  Chili recommended I blacklist the rt2800pci drivers in my original discussion, which I linked for reference in my topic here.  I did reboot.  I rebooted many times and tried many different configurations, including reinstalling Ubuntu OS multiple times in different Server and Desktop modes, which is why I posted here: none of the installations work; only the LiveCD and Windows work.

@varunendra, I was thinking the same myself, [COLOR="DarkOrange"]_**hehe**_[/COLOR].  To verify your assumptions, yes, the first pasted code was using the correctly-associated LiveCD wireless.  Thanks for the pointer.  How would I go about "un"blacklisting and/or modprobing the correct drivers?  I'm not too sure which drivers might be necessary, although I would guess (from my original linked post) that I need to basically do the exact *opposite* of: ```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt2800pci
rmmod -f rt2x00pci
```I'm just not sure quite how to go about doing that.  I guess modprobe is the opposite of rmmod?  And what about the -f?  Many thanks again for your help; this problem has really been driving me nuts.

---

### Post by thunderloki on 2011-07-17
My first thought was that perhaps since he suggested I lsusb | grep -i rt, the rt2860 drivers are more oriented toward the USB wireless devices, and maybe the rt2800*pci* drivers are...well.. more suited to PCI devices.

---

### Post by varunendra on 2011-07-17
To be honest, I've absolutely no idea which driver is suitable for what. My suggestion was based on your own experience (live mode (= rt2800) = working, and native mode (= rt2860) = not working).

As for un-blacklisting the drivers, I use a very basic (quite trivial) method. Just open the blacklist.conf file in super-user mode:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```and add a hash (#) mark in the beginning of any line which you want to disable (ineffective). So in your case, after opening that file with above command, look for the line that says **blacklist rt2800pci** (it would most probably be in the last) and add the '#' mark in its beginning. So now it should look like this:
```
# blacklist rt2800pci
```Do the same with any other driver (means corresponding 'blacklist' line) that you wish to 'un-block'.

Please note that you can also simply delete the line to unblock the corresponding driver after reboot. The commenting out of a line (putting '#' in its beginning) is recommended so that you don't need to remember it if you want to block it again.

Obviously, you can similarly add a line (or un-comment, if it already exists) to block a driver. The sequence of lines doesn't matter. In your particular case, the rt2860 driver can be blocked by adding this line in the same file:
```
blacklist rt2860
``` (the command does the same thing in the background)

After doing this, you can either use the command:
```
sudo modprobe rt2800pci
```or just reboot your computer.

Let us know how it goes.


**EDIT:**
If you prefer the last modprobe command instead of a reboot, then you have to first remove the previously loaded driver rt2860:
```
sudo rmmod rt2860
```

---

### Post by chili555 on 2011-07-17
> blacklist rt2860> sudo rmmod rt2860In both cases, it's rt2860[COLOR="Red"]sta[/COLOR]. The suggested changes require the correct name of the module or they won't work.

If rt2800pci works and rt2860sta doesn't, I'll fall off my chair; it will be a first.

---

### Post by thunderloki on 2011-07-17
@Chili, I noticed via lshw -C network, that the RT2760 device (after blacklist of 2860sta) using driver rt2800pci shows ```
driverversion=2.6.38-8-server
```whereas the LiveCD boot uses 2.6.38-8 *generic*.  Perhaps this is the deciding factor?  Then again, why would the desktop install NOT work if the generic is the only difference?  I tried modprobing rt2860sta under Desktop, and it wasn't available (apparently it is a server module?)

My final resort will probably be [this procedure]("http://ubuntuforums.org/showthread.php?t=966185"), which at present is somewhat beyond me.  I am of course capable of learning but I am just thinking it might be useful to exhaust my options here.  I have no idea why neither driver will work if they are not conflicting.  I can't write it off to a bad card, a bad router, a bad signal, and apparently I can't even write it off to Linux difficulty, or even Version 11 difficulty, because it _***DOES*_** work in Live Ubuntu 11.04.

---

### Post by thunderloki on 2011-07-17
Upon ifup wlan0, I get the following errors:
```
phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
phy0 -> rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy, aborting.
phy0 -> rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5).
SIOCSIFFLAGS: Input/output error
```repeated three times.  After that, ssh stops and starts.

This is in native server 64 install, after blacklisting rt2860sta, unblacklisting rt2800pci, and modprobe rt2800pci.

[EDIT]
iwconfig, at this point, gives the correct ESSID (because I put it in /etc/network/interfaces) but shows Access Point: Not-Associated.

---

### Post by thunderloki on 2011-07-17
Perhaps it would be wise to compile rt2800pci for server instead of generic?  Is that even an option?  :???:

---

### Post by thunderloki on 2011-07-17
By the way, Chili, lshw -C network shows that the RT2760 device uses *driver=rt2860*, not *rt2860sta*; however, lsmod shows rt2860sta.  I don't know if this is any help...  also, strangely enough, the LiveCD apparently uses rt2800pci successfully.  Maybe a different version of it.

---

### Post by thunderloki on 2011-07-17
Another proposed solution to this problem is to use the new Ubuntu Linux kernel from Oneiric, which supposedly has better Ralink driver support.  I am so lost and confused at this point that I'm just Googling whatever combination of "RT2860", "Ubuntu", and whatever other random keywords you might choose from this discussion.  Any guidance would be greatly appreciated.

---

### Post by chili555 on 2011-07-17
> **thunderloki said:**
> @Chili, I noticed via lshw -C network, that the RT2760 device (after blacklist of 2860sta) using driver rt2800pci shows ```
driverversion=2.6.38-8-server
```whereas the LiveCD boot uses 2.6.38-8 *generic*.  Perhaps this is the deciding factor?  Then again, why would the desktop install NOT work if the generic is the only difference?  I tried modprobing rt2860sta under Desktop, and it wasn't available (apparently it is a server module?)

My final resort will probably be [this procedure]("http://ubuntuforums.org/showthread.php?t=966185"), which at present is somewhat beyond me.  I am of course capable of learning but I am just thinking it might be useful to exhaust my options here.  I have no idea why neither driver will work if they are not conflicting.  I can't write it off to a bad card, a bad router, a bad signal, and apparently I can't even write it off to Linux difficulty, or even Version 11 difficulty, because it _***DOES*_** work in Live Ubuntu 11.04.Let's see what kernel you have installed:```
uname -r
```Let's see what versions exist on your system:```
sudo updatedb
locate rt2860sta

```Frankly, unless someone has removed it, rt2860sta is included in recent kernels by default. Most devices cause a conflict by also loading rt2800pci. When the wireless doesn't work very well because of the underlying conflict, many compile a new driver from source. Since it doesn't fix the underlying driver conflict, it *still* doesn't work very well! Let's see if we can unravel your situation.

---

### Post by chili555 on 2011-07-17
> **thunderloki said:**
> Another proposed solution to this problem is to use the new Ubuntu Linux kernel from Oneiric, which supposedly has better Ralink driver support.  I am so lost and confused at this point that I'm just Googling whatever combination of "RT2860", "Ubuntu", and whatever other random keywords you might choose from this discussion.  Any guidance would be greatly appreciated.Read my lips: "No new kernels!"

---

### Post by thunderloki on 2011-07-17
uname -r returns 2.6.38-8 server; updatedb gives no results.  You are probably right about the re-compile -- I was thinking maybe there's a way I could compile this item for server?  According to the LiveCD the 2800pci *generic* driver worked, and it apparently had both rt2860sta and 2800pci listed in lsmod.

locate rt2860sta returns /lib/modules/2.6.38-8-server/kernel/drivers/staging/rt2860/rt2860sta.ko .

I noticed that in one of your more detailed posts you mentioned the source of the driver conflict: modinfo rt2800pci and rt2860sta both return the same pci string (or something of that sort) -- would it be valuable to try these commands in Live mode and see whether there is still a conflict?

---

### Post by chili555 on 2011-07-17
Everything looks fine so far. So, can you do:```
sudo modprobe rt2860sta
```Can you blacklist rt2800pci and doesn't it work?

---

### Post by thunderloki on 2011-07-17
I'm really starting to think that it's just an issue somehow relating to the server version kernel, or perhaps the AMD64 (kernel?  OS?  other drivers?  software?  I have no idea.)

I'm posting this from the LiveCD.  I can post my massive output from the Live version now.

Installing Desktop, then using tasksel for the LAMP packages and whatnot, is definitely a viable option for me if other options are exhausted.  I just would really prefer to have a clean, minimal AMD64 server setup going on this thing.

Now for the (potentially valuable) info from Live.

root@ubuntu:/home/ubuntu# modinfo rt2800pci | grep 0781
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
root@ubuntu:/home/ubuntu# modinfo rt2860sta | grep 0781
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*

still the same conflict; rt2860sta IS listed in lsmod.  lshw -C network shows driver=rt2800pci 2.6.38-8-generic for the Ralink; network is associated correctly.

blacklist doesn't have rt2860sta OR rt2800pci in it.

now for more detail:

=============iwconfig```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MG6O6" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1F:90:AA:FC:B2  
          Bit Rate=48 Mb/s   Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:35   Missed beacon:0
```

=============ifconfig```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:19:54:eb 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

eth1      Link encap:Ethernet  HWaddr 00:24:8c:19:54:ea 
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
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22368 (22.3 KB)  TX bytes:22368 (22.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:2f:38:3a:ea 
          inet addr:192.168.1.71  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:2fff:fe38:3aea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3428 (3.4 KB)  TX bytes:10114 (10.1 KB)
```

=============cat /etc/network/interfaces```
ubuntu@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

=============lshw -C network```
root@ubuntu:/home/ubuntu# lshw -C network
  *-network              
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:24:8c:19:54:eb
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:69 memory:fbdfc000-fbdfffff ioport:d800(size=256) memory:fbdc0000-fbddffff
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 12
       serial: 00:24:8c:19:54:ea
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:70 memory:fbafc000-fbafffff ioport:a800(size=256) memory:fbac0000-fbadffff
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:09:01.0
       logical name: wlan0
       version: 00
       serial: 00:21:2f:38:3a:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 ip=192.168.1.71 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbef0000-fbefffff
```

=============rfkill list all```
root@ubuntu:/home/ubuntu# rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

=============lspci```
root@ubuntu:/home/ubuntu# lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
05:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
06:00.0 RAID bus controller: Marvell Technology Group Ltd. 88SE6440 SAS/SATA PCIe controller (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
09:01.0 Network controller: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus
09:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
```

=============lsmod```
root@ubuntu:/home/ubuntu# lsmod
Module                  Size  Used by
parport_pc             36959  0
dm_crypt               22993  0
ppdev                  17113  0
lp                     17825  0
parport                46458  3 parport_pc,ppdev,lp
binfmt_misc            17565  1
snd_hda_codec_hdmi     28103  1
snd_hda_codec_analog    98042  1
snd_hda_intel          33211  2
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
rt2860sta             543010  0
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30486  1 snd_seq_midi
arc4                   12529  2
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              18535  0
rt2800lib              45181  1 rt2800pci
crc_ccitt              12667  2 rt2860sta,rt2800lib
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2x00pci              14322  1 rt2800pci
rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
asus_atk0110           17976  0
i7core_edac            27903  0
edac_core              53845  1 i7core_edac
squashfs               36692  1
aufs                  181143  4158
nls_utf8               12557  1
isofs                  40283  1
dm_raid45              77827  0
xor                    12890  1 dm_raid45
btrfs                 550402  0
zlib_deflate           27074  1 btrfs
libcrc32c              12644  1 btrfs
pata_marvell           12905  0
firewire_sbp2          22897  0
usbhid                 46956  0
hid                    91020  1 usbhid
radeon                982197  3
ahci                   25951  3
mvsas                  56615  0
ttm                    76664  1 radeon
libsas                 59768  1 mvsas
drm_kms_helper         42136  1 radeon
libahci                26642  1 ahci
drm                   227495  5 radeon,ttm,drm_kms_helper
firewire_ohci          40370  0
firewire_core          62646  2 firewire_sbp2,firewire_ohci
sky2                   58509  0
crc_itu_t              12707  1 firewire_core
scsi_transport_sas     40545  2 mvsas,libsas
i2c_algo_bit           13400  1 radeon
floppy                 74120  0
```

=============blacklists
```
root@ubuntu:/home/ubuntu# cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

=============uname-r, etc
```
root@ubuntu:/home/ubuntu# uname -r
2.6.38-8-generic

root@ubuntu:/home/ubuntu# updatedb

root@ubuntu:/home/ubuntu# locate rt2860sta
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/rofs/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
```

=============modinfo rt2800pci and rt2860sta
```
root@ubuntu:/home/ubuntu# modinfo rt2800pci
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     9EAFA237203AC68B2B4EC40
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00pci,eeprom_93cx6
vermagic:       2.6.38-8-generic SMP mod_unload modversions
parm:           nohwcrypt:Disable hardware encryption. (bool)

root@ubuntu:/home/ubuntu# modinfo rt2860sta
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
srcversion:     C22EE7282F9A519D7E9A764
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.38-8-generic SMP mod_unload modversions
parm:           mac:rt28xx: wireless mac addr (charp)
```

```
root@ubuntu:/home/ubuntu# modinfo rt2800pci | grep 0781
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
root@ubuntu:/home/ubuntu# modinfo rt2860sta | grep 0781
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
```

---

### Post by chili555 on 2011-07-17
Yes, the conflict still exists. Until rt2860sta leaves staging and goes mainstream, it always will.

In your installed version, not live, can you blacklist rt2800pci, modprobe rt2860sta, reboot and does it work?

I have no explanation as to why it seems to work live and not installed. Unless you intend to run live forever, it's not worth the intellectual exercise to me.

---

### Post by thunderloki on 2011-07-17
That is correct.  If I modprobe rt2860sta and edit /etc/modprobe.d/blacklist.conf to add rt2800pci, and rmmod -f rt2800pci, reboot, ifdown and ifup wlan0, /etc/init.d/networking restart, edit /etc/network/interfaces correctly, etc, etc, etc....  it still refuses to associate correctly.

Even when I hardcode the access point MAC address, wireless channel, so on and so forth, into /etc/network/interfaces, it still leaves me hanging at "Encryption: off".  I have read some other forum entries about similar problems.  I do have my home network set to WEP and I know it works on the Live installation.  If you think it would be helpful, I can copy the same results to a USB from my Server installation and post them here.  I think we've seen most of those by now, though...

I can post the Server-con-blacklisted info, as well as the default Server configuration info.  I really just feel like if I can set things up to imitate the LiveCD setup I'll be golden...

---

### Post by chili555 on 2011-07-17
> Even when I hardcode the access point MAC address, wireless channel, so on and so forth, into /etc/network/interfaces, it still leaves me hanging at "Encryption: off". May I assume you are referring now to your server setup, with no Network Manager or Wicd running? May I see your /etc/network/interfaces?

Please be sure rt2800pci is blacklisted.

---

### Post by thunderloki on 2011-07-17
Correct.

```
cat etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.1
wireless-channel 6
wireless-essid MG606
wireless-key #A##-AAAA-A#
```

lsmod shows only rt2860sta.  sudo lshw -C network results in```
 a whole bunch of stuff

Product: RT2760 Wireless 802.11n 1T/2R Cardbus
vendor: Ralink corp.
physical id: 1
bus info: pci@0000:09:01.0
logical name: wlan0
version: 00
serial: 00:21:2f:38:3a:ea
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2860 ip=192.168.1.199 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
resources: irq:17 memory:fbef0000-fbefffff
```
Please excuse any typoes.

iwconfig:
```

lo - no wireless extensions.
eth0 - no wireless extensions.
eth1 - no wireless extensions.
wlan0:
Ralnk STA ESSID:"" Nickname:"RT2860STA"
Mode:Auto Frequency=2.437 GHz Access Point: Not-Associated
Bit Rate: 1Mb/s
RTS thr:off Fragment thr:off
Link Quality=10/100 Signal level:0dBm Noise level:-97dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

iwlist scan gives: ```
lo, eth0, eth1 don't support scanning...

wlan0 scan completed: Cell 01 - Address: ##:#A:##:AA:AA:A#
Protocol:802.11g
ESSID:"MG606"
Mode:Managed
Channel:6
Quality:44/100 Signal level:-72 dBm Noise level:-97 dBm
Encryption key:on
Bit Rates:118 Mb/s
Cell 02 -- irrelevant
```

---

### Post by thunderloki on 2011-07-17
The only real reason I was concerned about why Live works and native doesn't is that perhaps the solution to making Native work lies in the reason that Live does work.

---

### Post by thunderloki on 2011-07-17
It just seems odd to me that the driver conflict is not causing problems in Live even though rt2800pci and rt2860sta are both listed in lsmod, neither is blacklisted....  ya know.  It makes me think that the driver conflict may not be the issue at stake?

---

### Post by thunderloki on 2011-07-17
> **chili555 said:**
> Yes, the conflict still exists. Until rt2860sta leaves staging and goes mainstream, it always will.

This specifically is what I'm trying to get at.  What I was trying to say was that, yes, the conflict still exists in Live -- and the wireless works flawlessly.  Therefore, it must be a different problem causing this device to function differently than we would expect...

---

### Post by varunendra on 2011-07-18
> **chili555 said:**
> In both cases, it's rt2860[COLOR=Red]sta[/COLOR]. The suggested changes require the correct name of the module or they won't work.

If rt2800pci works and rt2860sta doesn't, I'll fall off my chair; it will be a first.
Sorry, I missed the "sta" part in his statement, only followed what appeared in his output code:
> **thunderloki said:**
> ```
 RT2760 Wireless blah blah... **driver=rt2860** wireless=Ralink STA logical name: wlan0
```
...
...
I blacklisted rt2800pci and rt2x00pci, and removed them from lsmod.  So lsmod only returns **rt2860sta**....

Besides, I already declared "I have no idea of what is suitable for what".. :D


@thunderloki,

Since we are comparing scenarios with the live session, hope you understand that we should currently stay with the desktop installation only, not the 'server' installation.
> **thunderloki said:**
> ...
This is in native server 64 install, after blacklisting rt2860sta, unblacklisting rt2800pci, and modprobe rt2800pci....

So, not meaning to contradict chilli, but did you try the same thing on desktop installation? What happened if you did? And if you did not, then should we assume that you are only concerned about your server installation and the desktop installation was just an experiment?

Making these things clear would help us being more precise.

And once again, "I have no idea of what is suitable for what".. :)

---

### Post by chili555 on 2011-07-18
> cat etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them.  For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.1
wireless-channel 6
wireless-essid MG606
wireless-key #A##-AAAA-A#I suggest you try the WEP key without dashes. Also, if there are any letters in the key, try both upper- and lower-case. I doubt you need the channel; the access point and your wireless device will negotiate that between them. After you make changes, the system will re-read the file when you do:```
sudo ifdown wlan0 && sudo ifup wlan0
```Then check:```
iwconfig
```Thanks.

---

### Post by thunderloki on 2011-07-18
@Chili, Both of those changes (upper-to-lowercase, and removing dashes) give the same results.  In fact, the un-hyphenated /etc/network/interfaces key still shows a hyphenated key in iwconfig.

@Varun, don't worry about the driver names, that was a bit confusing to me as well.  I think that lshw -C network has the driver return its name, instead of the name of the module.

As to server vs desktop -- I was actually right in the middle of reinstalling Server over Desktop when I made this post, but the problem seems to be basically the same.  I will try comparing the native Desktop settings with the Live Desktop settings.  I did try the blacklist rt2800pci fix, but modprobe rt2860sta resulted in module not found, because according to the terminal, it was from the Server kernel, or something...

Perhaps a locate rt2860sta in Desktop mode will give me what I'm looking for.  Or perhaps recompiling their drivers for 64-bit mode would be a good solution.

---

### Post by chili555 on 2011-07-18
So have you tried both installed and live?```
sudo updatedb
locate rt2860sta
```

---

### Post by thunderloki on 2011-07-18
Yes I have -- I'm on Live right now.  updatedb gives no results, locate rt2860sta gives:

```
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/rofs/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
```

---

### Post by chili555 on 2011-07-18
So the module *does* exist in Live. How about the installed version?

---

### Post by thunderloki on 2011-07-19
Sure does -- /lib/modules/2.6.38-8-server/kernel/drivers/staging/rt2860/rt2860sta.ko .

---

### Post by chili555 on 2011-07-19
> **thunderloki said:**
> Sure does -- /lib/modules/2.6.38-8-server/kernel/drivers/staging/rt2860/rt2860sta.ko .So, since you reinstalled, are you now able to blacklist rt2800pci and use rt2860sta? But it simply won't connect to a WEP encrypted network?

Please do:```
sudo ifdown wlan0 && sudo ifup wlan0
sudo cat /var/log/syslog | grep -e wlan -e rt2 | tail -n20
```Let's see if syslog has some clues. If this is sparse, also look in syslog.1.

---

### Post by thunderloki on 2011-07-20
cat syslog basically gives 3 messages which are repeated several times:

lifemote dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval (various)
lifemote kernel: [ 5550.023650 ] wlan0: no IPV6 routers present (on that note, I have tried under a previous installation of Server to disable ipv6 as a fix, to no avail)
lifemote dhclient: same... over and over...
lifemote ntpdate[ pid ] name server cannot be used: temporary failure in name resolution
...
lifemote dhclient: can't create /var/lib/dhcp3/dhclient.wlan0.leases: No such file or directory
(repeats once)
lifemote kernel: [ 5630.519628 ] <==== rt28xx_init, Status=0

---

