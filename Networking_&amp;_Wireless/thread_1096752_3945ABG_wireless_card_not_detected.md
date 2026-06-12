---
title: "3945ABG wireless card not detected"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by diver boy on 2009-03-15
I am new to ubuntu, and Linux as well.  I have a Lenovo T60 laptop.  Hed to replace the hard drive and decided to give ubuntu studio a try.  I had been runnig Windows XP Professional and have a wireless network at home that I connect to.

During the installation when it came time to configure the network I had two choices:

irda0 - unknown interface
eht0 - Intel 82573L Gigabit Ethernet Controller

Whichever I selected, DHCP could not configure,  so I did a manual configuration of the etth.

When I completed the install, there is no indiction of any network connectivity.

I tried running hte hardware test under system administration.  There it deteces the following:

Intel Corporation 8257L Gigabit Ethernet Controller
Intel Corporation PRO Wireless 3495ABG (Golan)
Network Connection (rev 02)

I am lost.  What can I do to get connectivity?

---

### Post by chili555 on 2009-03-15
First, make sure the little slide switch on the front of your T60 is over on the 'On' position, so you can see the green background. Then open up a terminal (Applications -> Accessories -> Terminal, if you are running Gnome) and type:```
sudo modprobe iwl3945
ifconfig
```Does a new interface, wlan0 probably, appear? Now when you click on the NetworkManager icon, do you see a wireless interface? Can you select it, see your network and connect?

---

### Post by diver boy on 2009-03-15
The sudo modprobe iwl3945 does not bring back any data at all
the ifconfig shows eth0 and local loopback, no wireless.

sudo lshw -C netwok
shows etho and the *-network DISABLED
       deciption: wirless iterface
       product: PRO/Wieless 3945G [Golan} Nework Connection
       vendor: Inel Corporation
       physical id: 0
       bus info: pci@0000:03:00:0
       logical name: wmaster0
        version: 02
       
and some additional details.

I do not have Network Manager on my system.

---

### Post by chili555 on 2009-03-15
> *-network DISABLEDThis strongly suggests the wireless switch is in the 'Off' position. Is it?

If I switch my switch to 'Off' and back to 'On', I have trouble getting re-connected. You might just reboot with the switch in the 'On' position and see if your wireless springs to life.> I do not have Network Manager on my system.Excellent! May we please see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by diver boy on 2009-03-15
Thanks for the quick replies.

Yes, the network switch is on.  I fliped it off and on, and rebooted, same thing.

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

Then it lists the IP address i manually entered in during the install.

---

### Post by chili555 on 2009-03-15
Please do:```
sudo gedit /etc/network/interfaces
```and add the following:```
auto wlan0
iface wlan0 inet dhcp
```Check your work, save and close. Then do:```
sudo /etc/init.d/networking restart
```Any interesting messages?

May I please see:```
dmesg | grep iwl
```Thanks.

---

### Post by diver boy on 2009-03-15
I mad ethe requested changes.  restarted the networking, and got the following messages:
Internet Systems Consortium DHCP Client V3.1.1

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LDP/wlan0/00:18:de:b8:cf:c8
Sending on LDP/wlan0/00:18:de:b8:cf:c8
sending on Socket/fallback
DHCPDISCOVER on wlan0 tp 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 tp 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 tp 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 tp 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 tp 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 tp 255.255.255.255 port 67 interval 18
No DHCPOFFERRS received
No working leases in presistent database - sleeping




dmseg | grep iwl

[   13.204558] iwl3945 Inter(R) PRO/Wireless 3945ABG/BG Metwork Connection driver for Linux 1.2.26ks
[   13.304658] iwl3945 Copyright (c) 2003-2008 Intel Corporation
[   13.514540] iwl3945 0000:03:00:0 PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.514556] iwl3945 0000:03:00:0 setting latency timer to 64
[   13.514577] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   13.579638] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.580296] phy0: selected rate control algorithm 'iwl-3945-rs"
[   13.778274] iwl3945 0000:03:00:0: PCI INT A disabled
[ 7063.575534] iwl3945 0000:03:00:0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 7063.575714] iwl3945 0000:03:00:0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[ 7063.576026] firmware: requesting iwlwifi -3945-1.ucode
[ 7063.691717] Registered led device: iwl-phy0:radio
[ 7063.692623] Registered led device: iwl-phy0:assoc

---

### Post by chili555 on 2009-03-15
Ah ha! Now we're getting somewhere! Your dmesg looks fine, and the computer now sees a wlan0. I feel like we're getting close. Please let us see:```
sudo iwconfig wlan0
sudo iwlist wlan0 scan
```Thanks.

---

### Post by diver boy on 2009-03-15
iwconfig

wlan0    IEEE 802/11abg ESSID:""
Mode:Managed  Frequency:2.412 Ghz  Access Point:Not Associated
Tx-power-15dBm
Retry min limit:7 RTS thr:off Fragment the=2352 B
Encryption Key: off
Power Management:off
Link Quality:0 Signal level:0 Noise Level:0 TX invalid iwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx exxeccsive restirw:0 Invalid Misc:0 Missed beacon:0

scan

Wlan0 scan completed
cell 01 address :00:0c:41:CB:13:66
ESSID "linksys-g"
Channel 6
Frequenct 2.437 GHz (Channel 6)
Encryption Key off
But rates 1,2,5,11,18,24,36,54,6,9,12,48 Mb/s
Extra:tsf=0000034cc9e7e188
Extra Last beacon 1956 MS ago
Cell 2 address 00:cc:41:0c:05:47
ESSID: Linksys-a"
Mode: Master
Channel:52
Frequency 5.26GHz (Channel 52)
Quality=65/100  Signal level:-69dBm  Noice level =-95dBm
Encrytion key:off
Bit rtaes 6.9.12.18.24.36.48.54 Mb/s
extra:tsf=0000034ccb319036
Extra: Last beacon: 964 MS ago

Thanks for the gelp.  Also, I just installed this yesterday,  How do I find the root password.  I set one for me as the user, but did not set one for root.

---

### Post by chili555 on 2009-03-15
Looks great! Now please try this:```
sudo iwconfig wlan0 essid linksys-g
sudo iwconfig wlan0 ap 00:0C:41:CB:13:66
sudo dhclient wlan0
```I assume you are trying to connect to *linksys-g.* If not, substitute both the essid and ap details. Did you get an IP address, that is, did you connect?> How do I find the root password. I set one for me as the user, but did not set one for root.They are one and the same.

---

### Post by diver boy on 2009-03-15
I entered the suggested commands.  1st time I received permission denied
second time I receive d the same message about

wmaster0: unknown hardware address type 801

Through the

No working leases in persistent database - sleeping.


Also, when I try to login as root, authentication fails with my normal password.  I am not opposed to redoing the install if you feel that might be needed

---

### Post by chili555 on 2009-03-15
I'm not quite sure I understand. If you logged in as a normal user, when you logged in as the computer was booting, then any command preceded with 'sudo' should work perfectly, after giving your password. If you want to log in, while booting, as root, you probably can't.

You can log in to a terminal as root like this:```
sudo su
```After giving your password, you will be logged in, on the terminal, with root privileges.

Let's try another thing:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwconfig wlan0 essid linksys-g
sudo iwconfig wlan0 ap 00:0C:41:CB:13:66
sudo dhclient wlan0
```Did you connect?

I am running low on ammunition.

---

### Post by diver boy on 2009-03-15
I think we are getting closer.  The confusion onver root, was just me looking to avoid the sudo on all of the commands.  get it now.

I followed your instructions.

When I ran rhw dhclient wlan0  I came up with the same message as before

wmaster0: unknown hardware address type 801

 through the 
No DHCPOFFERS received
No working leases in persistnet database - sleeping

However when I go to the netowrk tools I see more than before.  When I first started all I would see under Network device was the Loopback Interface (lo)

Now is see:

Loopback Interface (lo)
Ethernet Interface (eth0)
Unknown Interface (wmaster0)
Wireless Interface (wlan0)
Wireless Interface (wlan:avahi)

The Wireless Interface (wlan:avahi) Interface statistics show
Transmitted bytes

---

### Post by diver boy on 2009-03-15
Sorry, did not finish

Transmitted bytes 5.3KB
Transmitted packets: 30
Tansmission errors: 0
Received bytes 3.1 KB
Received packets 28
Reception errors: 0
Collisions: 0

So it look as though there is the begining of communication, but without Network Manager, I do not know how to find the wireless network to connect to.

---

### Post by chili555 on 2009-03-15
The wlan0:avahi interface is a dummy entry when no connection is yet found. The transmitted and received bytes are simply you trying to find a connection via dhclient.> I do not know how to find the wireless network to connect to.That's the purpose of scanning. Is *linksys-g* your network?

Open System -> Administration -> Synaptic and see if *linux-backports-modules-intrepid-generic* is installed. If not, please do. Then please repeat the commands to connect:```
sudo iwconfig wlan0 essid linksys-g
sudo iwconfig wlan0 ap 00:0C:41:CB:13:66
sudo dhclient wlan0
```

---

### Post by diver boy on 2009-03-15
OK, I checked and I do not have the linux-backports.....file.

Where can I find this file?  I can copy it to a jump drive and the hopefully load it on to my system.

---

### Post by chili555 on 2009-03-15
You can get it here: [http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-intrepid-generic)

Note that it depends on *linux-backports-modules-2.6.27-11-generic*, so get that, too. I assume your running kernel is 2.6.27-11. Find out with:```
uname -r
```If not, post back and we'll get it sorted out.

Note that when you drag-n-drop these off of the USB drive, they may not be executable as a program. Right click and, under Properties -> Permissions, be sure to check off 'Allow executing file as a program'. Then you should be able to right-click the files and install with Gdebi package manager.

---

### Post by diver boy on 2009-03-15
I do have linux-backports-modules-2.6.27 installed.

---

### Post by diver boy on 2009-03-15
OK, I downloaded the linux-backports-modules-intrepid-generic package.  When I open it to install there is an error: Dependency is not satisfiable: linux-backposrts-moduels-2.6.27.1-generic.

Inching closer.

---

### Post by chili555 on 2009-03-15
> Dependency is not satisfiable: linux-backposrts-moduels-2.6.27.1-generic.Are you sure it's not 2.6.27-**11** that it wants and that you downloaded? Install the other one first and then *generic.*

---

### Post by diver boy on 2009-03-15
That was my typo.  the Dependency is linux-backports-modules-2.6.27.11-generic

I have linux-backports-modules-intrepid-generic-2.6.27.11 installed.  Not sure of the significance of the generic before the version or after it.

---

### Post by chili555 on 2009-03-15
> Not sure of the significance of the generic before the version or after it.It means it works with studio, servers, desktop, etc. Please be sure you have installed *both* packages. The one without the numbers is a dummy package that makes sure that as updates come along, you get the latest version of *backports* to match any new kernel you get.

Can you now connect?

---

### Post by diver boy on 2009-03-15
I have linus-backports-modules-2.6.27.7-generic, linux-backports-modules-intrepis 2.6.27.11 and linux-backports-modules-intrepid-generic 2.6.27.11 installed.  I still get the Error: Denepenecy is not satisfiable: linux-backports-modules-2.6.27.11-generic

I have been searching for this package, but have not yet found on ehtat I can load.

I found linux-backports-modules-2.6.27.11 generic_2/6/27/11/12, and it gives me the same error.

---

### Post by diver boy on 2009-03-16
I have searched and cannot find the linux-backposrt-modules-2.6.27.11-generic package.

Any suggestions on where I might be able to find it?  Once I have it I will install the 2.6.27.11.14 package and give it a try.

---

### Post by chili555 on 2009-03-16
> **diver boy said:**
> I have searched and cannot find the linux-backposrt-modules-2.6.27.11-generic package.

Any suggestions on where I might be able to find it?  Once I have it I will install the 2.6.27.11.14 package and give it a try.Right here: [http://packages.ubuntu.com/intrepid/i386/linux-backports-modules-2.6.27-11-generic/download](http://packages.ubuntu.com/intrepid/i386/linux-backports-modules-2.6.27-11-generic/download)

---

### Post by diver boy on 2009-03-16
chili555, thanks for the continued assistance.

I now have all the requested packages installed.

Sorry to say that I am still getting the same messages

wmaster0: unknown hardware address type 801

through

No working leases in persistent database - sleeping

---

### Post by chili555 on 2009-03-16
> Wlan0 scan completed
cell 01 address :00:0c:41:CB:13:66
ESSID "linksys-g"
Channel 6
Frequenct 2.437 GHz (Channel 6)
Encryption Key off
But rates 1,2,5,11,18,24,36,54,6,9,12,48 Mb/s
Extra:tsf=0000034cc9e7e188
Extra Last beacon 1956 MS agoI don't see any signal strength. Would you please run:```
sudo iwlist wlan0 scan
```And let us see the signal strength, please.

Again, is *linksys-g* your network or is it your university or internet cafe or neighbor? Is it possible that the router or access point uses MAC filtering? Have you connected to it with other computers?

Have you, each time, used the complete list of commands?```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwconfig wlan0 essid linksys-g
sudo iwconfig wlan0 ap 00:0C:41:CB:13:66
sudo dhclient wlan0
```

---

### Post by diver boy on 2009-03-16
I appoligize, I left out the line with the signal quality.

Quality = 62/100  Signal level : -70db  Noise level =-127 db

Reran the commands again, and it is finally working.

Thank you so much for all of the help

---

### Post by diver boy on 2009-03-16
DO I need to enter these commands every time I restart my system?

I just rebooted and needed to enter the five commands before I could connect

---

### Post by chili555 on 2009-03-16
I sorta knew you'd be back!

You can make the first two commands permanent with this command:```
echo 'options iwl3945 disable_hw_scan=1' | sudo tee -a /etc/modprobe.d/options
```The next three can be set in */etc/network/interfaces*. Amend it so it reads like this:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys-g
wireless-ap 00:0C:41:CB:13:66
```Check your work, save and close your text editor. Now reboot and it should connect automagically!

---

### Post by diver boy on 2009-03-16
Thanks again.  It has been years since I played around with unix.  Spent to long in the windows word.

I am now up an functional.

---

