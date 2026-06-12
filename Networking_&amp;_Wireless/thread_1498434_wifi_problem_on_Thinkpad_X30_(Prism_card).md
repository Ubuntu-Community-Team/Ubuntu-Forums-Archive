---
title: "wifi problem on Thinkpad X30 (Prism card)"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by morgonhed on 2010-05-31
Hi,

I've just installed Ubuntu 10.04 on my old X30 alongside my fully working 8.04 and have strange wifi problems under 10.04 (under 8.04 it worked out of the box):

- no available networks are shown
- running "sudo iwlist scanning" results in "eth1      Interface doesn't support scanning : Device or resource busy"
- without any wireless congfiguration from my side I get this:

sudo iwconfig eth1
eth1      IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\
xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=90/70  Signal level=-8 dBm  Noise level=-147 dBm
          Rx invalid nwid:0  Rx invalid crypt:63  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

A very strange ESSID there appearing out of nowhere...

Here some more information:

lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
01:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
01:00.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
01:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:00.0 USB Controller: OPTi Inc. 82C861 (rev 10)

sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: eth1
       version: 01
       serial: 00:05:3c:06:34:3e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.8.2 latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: irq:11 memory:f8000000-f8000fff(prefetchable)


Can anyone provide me with some tips?

Many thanks!

---

### Post by chili555 on 2010-06-01
Let's see how many drivers are loaded. Please post:```
lsmod | grep -e orinoco -e hostap
```Thanks.

---

### Post by morgonhed on 2010-06-01
Here the modules:

lsmod | grep -e orinoco -e hostap
hostap_pci             44488  0 
hostap                 99846  1 hostap_pci
lib80211                5046  2 hostap_pci,hostap
orinoco_pci             2655  0 
orinoco                62841  1 orinoco_pci
cfg80211              126485  1 orinoco

Any ideas?

Many thanks!

---

### Post by chili555 on 2010-06-01
That's too many conflicting drivers. Let's ban some. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add two lines at the end:```
blacklist hostap
blacklist hostap_pci
```Proofread carefully, save and close gedit. Reboot. Is your wireless working better now?

---

### Post by morgonhed on 2010-06-01
Many thanks for your suggestion - however:

Blacklisting the hostap-driver did not change anything (as far as the wifi problem is concerned). 

I then tried to blacklist (only) the orinocco-driver after which my system would not boot any more (boy am I glad I kept my 8.04 installation...).

Any other ideas?

This is really a bit disappointing to me as this laptop has seen many distros over the years and wifi never was a problem before...

---

### Post by chili555 on 2010-06-01
Would you please blacklist the two hostap drivers, reboot and then let us see:```
dmesg | grep -e orin -e eth1
```Thanks.

---

### Post by morgonhed on 2010-06-01
Ok, here the output:

dmesg | grep -e orin -e eth1
[   28.103446] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[   28.302105] orinoco_pci 0.15 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[   28.351007] orinoco_pci 0000:01:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   29.289313] orinoco_pci 0000:01:02.0: Hardware identity 8013:0000:0001:0000
[   29.289458] orinoco_pci 0000:01:02.0: Station identity  001f:0002:0001:0008
[   29.289466] orinoco_pci 0000:01:02.0: Firmware determined as Intersil 1.8.2
[   29.289472] orinoco_pci 0000:01:02.0: Ad-hoc demo mode supported
[   29.289477] orinoco_pci 0000:01:02.0: IEEE standard IBSS ad-hoc mode supported
[   29.289482] orinoco_pci 0000:01:02.0: WEP supported, 104-bit key
[   30.265982] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   30.285147] eth1: New link status: Disconnected (0002)
[   31.073297] eth1: New link status: Connected (0001)
[   31.073749] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   31.114426] eth1: New link status: Disconnected (0002)
[   41.112051] eth1: no IPv6 routers present

---

### Post by chili555 on 2010-06-01
It actually looks pretty solid. Are you trying to connect with Network Manager? Does it see networks and try to connect? What does this tell us?```
iwconfig
sudo iwlist eth1 scan
```Thanks.

---

### Post by morgonhed on 2010-06-01
I do not try to connect to any network at the moment but I expect to see some (other people's private) networks.

The network manager only shows "Wireless Networks" and below that "disconnected".

I don't use the network manager as a) I don't understand it and b) I had issues with my UMTS-card with it (only got it to work with wvdial but that's another issue).

However there is clearly something wrong as this output seems wrong to me:

sudo iwconfig eth1
eth1      IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=88/70  Signal level=-8 dBm  Noise level=-146 dBm
          Rx invalid nwid:0  Rx invalid crypt:11  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Also I cannot scan for networks:

sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
irda0     Interface doesn't support scanning.
eth1      Interface doesn't support scanning : Device or resource busy
ppp0      Interface doesn't support scanning.

sudo iwlist eth1 scan
eth1      Interface doesn't support scanning : Device or resource busy


There must be some driver problem but I cannot see anything wrong (your observation about the previous driver conflict was a good point however).

---

### Post by chili555 on 2010-06-01
> this output seems wrong to meIt seems wrong to me, too. This part is consistent with actually being connected:> Link Quality=88/70 This part is just plain wacky:> ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F |\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A" Let's blacklist the orinoco suite and load hostap and see if it improves. Amend blacklist.conf as outlined above and change from this:```
blacklist hostap
blacklist hostap_pci
```To this:```
blacklist orinoco
blacklist orinoco_pci
```Reboot and then let's see:```
iwconfig
dmesg | grep -e host -e eth1
```Thanks.

---

### Post by morgonhed on 2010-06-01
As I already wrote above I tried to blacklist not hostap but orinocoo before and as a result my system did not boot any more (just hanging after grub).

I then had to boot my 8.04 version, mount the 10.04 filesystem and revert the blacklisting after which it worked again...

But if that is the only thing you can recommend I can try that again (just to be absolutely sure) - but I have to wait for a compilation to finish ...

---

### Post by chili555 on 2010-06-01
> if that is the only thing you can recommendUnfortunately, it is. Be sure to blacklist *both *orinoco *and* orinoco_pci.

---

### Post by morgonhed on 2010-06-01
Ok, tried blacklisting both hostap and orinocco, system boots ok but (quite logical if you think about it) now I don't have any wireless interface anymore.

What now? Switch to Suse?

---

### Post by morgonhed on 2010-06-01
Just verified again that when blacklisting orinocco but not hostap the system does not boot any more...

What a shame really, 10.04 is such a nice distro otherwise...

---

### Post by chili555 on 2010-06-01
Can you confirm that you blacklisted *both* orinoco *and* orinoco_pci?

Do you believe that Suse has different drivers built by different people than Ubuntu? Have you tried a live CD?

---

### Post by morgonhed on 2010-06-01
Summing up what I have tried so far:

- no blacklisting: wifi does not work properly

- blacklisting hostap and hostap_pci: same problem

- blacklisting orinoco and orinoco_pci: system does not boot

- blacklisting hostap, hostap_pci, orinoco and orinoco_pci: no wireless devices

And I am only kidding with SuSE. I really like Ubuntu, but I had a bit more issues moving from 8.04 to 10.04 than I had expected (the wifi is the last remaining). 

After all this is a LTS release (so it should be well tested) and I do not have any exotic hardware (that worked without problems in earlier versions) - so I am simply a tiny little bit disappointed that it is not as smooth as I think it could (and should) be.

But many thanks for all your support!

---

### Post by morgonhed on 2010-06-02
My 8.04 system uses only the hostap driver (and not orinoco), so I guess I should blacklist orinoco - but then my system does not boot any longer.

Has anyone an idea how I can investige the boot problem further?

Here is what happens:

I select the entry in grub, than the monitor goes black, then the monitor gets a little greenish and no further progress is made - it just hangs like that...

Many thanks!

---

### Post by chili555 on 2010-06-02
Select the entry in Grub and press 'e' for edit. Use the arrow keys to get down to the second line, which should be very long. Press 'e' again. Back out the words 'quiet splash.' Press Enter and press 'b' for boot.

You will then be able to see the boot process unfold. Be ready with a pencil and paper to write down the last few entries before it locks up.

You might also see some clues in /var/log/syslog. They are time-stamped, so make note of the time of day you attempted to boot.```
sudo less /var/log/syslog
```You can use the arrow keys to scroll back and forth.

---

### Post by chili555 on 2010-06-02
I just noticed this: [https://bugs.launchpad.net/ubuntu/+source/hostap-utils/+bug/573472](https://bugs.launchpad.net/ubuntu/+source/hostap-utils/+bug/573472)

If you check in System > Administration > Synaptic, do you have hostap-utils installed? Can you please remove it?

---

### Post by morgonhed on 2010-06-02
A few more observations (at the moment I have to use wifi, so I cannot use 10.04 but I will try your other suggestions shortly):

"sudo iwconfig eth1" shows garbage for the essid.
An explicit "sudo iwconfig eth1 <some essid>" seems to set the essid correctly (another iwconfig et least displays it) but only if the essid contains no blanks. Trying to configure an essid with blanks results in garbage again.

Also I tried to manually unload and load the drivers.

Starting with only orinoco-drivers loaded I can to

sudo modprobe -rf orinoco_pci
sudo modprobe -rf orinoco

But when I then do an 

sudo modprobe hostap

the system freezes.

So it looks to me as if the kernel has a problem loading the hostap-driver which could also be the boot-problem....

But it is strange that I seem to be able to load the hostap driver when the orinoco driver is also loaded - really makes no sense...

---

### Post by morgonhed on 2010-06-02
hostap_utils is not installed (it is a clean install from cd).

Here the messages displayed during booting with only hostap blacklisted:

Begin: Running /scripts/init-bottom ...
Done

BUG: soft lockup - CPU#0 stuck for 61s!

The line starting with BUG is then repeated indefinitely (or so it seems - I have turned off the laptop after some minutes).

---

### Post by morgonhed on 2010-06-02
[http://ubuntuforums.org/showthread.php?p=8645980](http://ubuntuforums.org/showthread.php?p=8645980) looks a lot like my problem.

Seems to me that something was broken in 9.04 and has not been fixed up to now...

Dammit - compiling a new kernel on my hardware takes forever...

---

### Post by morgonhed on 2010-06-04
This is extremely annoying...

I have now compiled a 2.6.34 kernel straight from kernel.org without any Ubuntu patches and it shows the same behaviour.

I am out of ideas now - anyone with another suggestion?

---

### Post by morgonhed on 2010-06-04
Finally managed to solve my wifi problem.

The culprit turned out to be the network manager that already gave me problems with my UMTS-card.

"sudo apt-get remove network-manager" and everything works...

I must say I am disappointed by Ubuntu's QA.

---

### Post by jarbain on 2010-06-07
Morganhed, sorry to bother you but I am having the exact same problem trying to get my wireless working on a Thinkpad T30.  In your final configuration:

1. You removed the network-manager application.
2. Did you end up using the hostap driver or the orinoco driver? I'm guessing it was the hostap driver.
3. Did you end up blacking listing the orinoco and orinoco_pci drivers?

FYI - I tried installing a number of different distros (openSuSE 11.2, PCLinuxOS 2010 KDE, LinuxMint 9) on my T30 and all suffered from the same wireless issues.  Every single install loads the orinoci driver which does not to work with the Intersil Prism 2.5 chipset.  No WPA is available.  Interesting thing is, I also tried installing Ubuntu 8.04 Desktop and could not get the wireless working.  

Thanks for your help.

---

### Post by morgonhed on 2010-06-08
Just removing the network-manager and rebooting solved all wireless problems, no further tweaking is nessecary.

In the end I did not blacklist anything, so both hostap and orinoco are loaded, but that does not seem to be a problem.

Without the network-manager you connect to a hotspot by setting the essid with iwconfig and starting a dhcp-client for eth1.

And finally afaik the card in the X30 (and I think that also applies to the T30) does not support WPA (that is a hardware limitation - it can only do WEP).

After all this laptop is almost 8 years old!

hth

---

### Post by chili555 on 2010-06-08
> And finally afaik the card in the X30 (and I think that also applies to the T30) does not support WPA (that is a hardware limitation - it can only do WEP).If I remember correctly, most of the Prism 2.5 series cards (including mine) do not support WPA; a few, depending on their firmware, do.

You can find out with:```
sudo iwlist eth1 auth
```

---

### Post by jarbain on 2010-06-08
I checked and the firmware on my Intersil Prism Chipset is 1.4.9.  

I had assumed it would be able to support WPA, previously I was running Windows XP and the WPA Authentication was working fine under XP with my router.  I really wanted to move away from XP to Linux.  I'm guessing the driver under Windows supported WPA.

I removed Network Manager and tried to configure the card using iwconfig, but was not able to set the WPA authentication.  I'm guessing the 1.4.9 firmware just doesn't support WPA.

Appreciate all the help, but without the wireless I think it's time to just retire the T30.  Thanks again.

---

### Post by morgonhed on 2010-06-09
Some PRISM-cards actually can be flashed with a new firmware to make it support WPA (I tried that with my laptop a couple of years ago unfortunately could not get it to work then but I did not try too hard as I don't really need it.)

And if WPA worked with Windows then your firmware already supports it and it should work under Linux as well - I would not give up on it just yet.

I have used many Linux distos over the years on my laptop and found the Thinkpad-hardware generally to be well supported - anything that works under Windows should (eventually) also work under Linux (if you are persistent enough).

But Ubuntu is really a bit sloppy sometimes (at least that is my impression). This network-manager that (before I got rid of it) gave me nothing but troubles (with both wifi and UMTS) evidently is not really ready for production...

---

### Post by jarbain on 2010-06-11
Thought I would post a followup and hopefully this will help others having problems with the Intersil Prism 2 chipset and getting wifi to work.

As a last effort, I decided to flash my Prism 2 chipset with updated firmware.  My current firmware was primary: v1.1.0 and secondary v.1.49.  Based on the version of my chipset, I was able to flash primary: v1.1.1 and secondary v1.7.4.  On most websites, the version 1.7.4 will support WPA.

The following two websites were very useful on determining the version of my chipset as well as the instructions for flashing new firmware and downloading updated firmware.  I recommend reading these two websites in detail before attempting to flash firmware.  The websites were:

[http://junsun.net/linux/intersil-prism/](http://junsun.net/linux/intersil-prism/)
[http://www.aircrack-ng.org/doku.php?id=prism2_flashing](http://www.aircrack-ng.org/doku.php?id=prism2_flashing)
[http://wiki.debian.org/hostap](http://wiki.debian.org/hostap)

The junsun website was the most complete and also includes the firmware downloads.  I will try and remember the steps I took.  The instructions for running prism2_srec are from the junsun site, I have listed them here as reference, but please read the website.

1.  I installed ubuntu 8.04 LTS on my laptop.
2.  After install, used Synaptic to install: hostap-utils package.  This package contains: prism2_srec which is used to flash the new firmware.
3.  Run hostap_diag wlan0  to determine the version of your chipset.
4.  Examime the output to determine the appropriate primary and secondary versions you can use.  This is detailed on the junsun website. Per the website - if you use the wrong versions, you can kill the chipset.
5. Download the correct firmware.
6. Verify a test run by:  prism2_srec -v wlan0 <primary> <secondary>
7. If no warnings, flash the chipset with:
prism2_srec -f -v wlan0 <primary> <secondary>

I was able to successfully flash the chipset.  Actually using the NetworkManager in Ubuntu 8.04, I was able to configure by Wifi connection and connect to my router using WPA.  Before the flashing the chipset, I was not successful at all.

Interesting note: After I flashed the chipset, I booted Ubuntu 10.04 LiveCD and tried to use NetworkManager to configure the connection using WPA.  With the LiveCD, it would not connect to the access point.  I did not try to configure it with iwconfig directly.  

I have to agree with morgonhed that Network Manager seems to be very buggy.

I am staying with Ubuntu 8.04 and my wifi is working.  Thanks for the help on this forum.  Hopefully this will help another person.  

Regards.

---

### Post by fernandofat on 2010-07-31
jarbain, I'm having the same problem with a Thinkpad X30 and Ubuntu 10.04. Can't connect to my network using WPA.

I will try the steps you recomended and post the result here.

BTW, I tested with many other Linux distros such as Fedora, Slackware, Slax and Backtrack (that I can remember) and no success. With Windows XP everything works fine.

---

### Post by tlinsenm on 2010-10-08
Thanks, jarbain, for the details! Have to second fernandofat, after firmware upgrade, I can connect to my WPA-encrypted wifi network on Windows XP without a problem, but not on Lucid. Will try Hardy over the weekend.

To avoid the risk of frying your chipset (Jun Sun cautions about that in his Howto, [http://junsun.net/linux/intersil-prism/](http://junsun.net/linux/intersil-prism/)), if you still have Windows XP installed, you can use the IBM firmware update, available here: [http://www-307.ibm.com/pc/support/site.wss/migr-43800.html#Wireless](http://www-307.ibm.com/pc/support/site.wss/migr-43800.html#Wireless) The Prism is listed as "High rate wireless LAN Mini PCI", with Firmware Update of 25 Feb 2003 and v1.04.09.02. This will upgrade to firmware version 1.7.4, enough for WPA to work.

---

### Post by tlinsenm on 2010-10-10
> **tlinsenm said:**
>  Will try Hardy over the weekend.

Well, that didn't work out for me either... Can't get a connection, and I tried both Network Manager with hostap and Wicd with hostap and wext... However, I've by now found out that WPA works out of the box on Puppy 4.3.1 (see [http://www.puppylinux.com/download/release-4.3.htm](http://www.puppylinux.com/download/release-4.3.htm)), so I'll stick with that for the time being...

---

