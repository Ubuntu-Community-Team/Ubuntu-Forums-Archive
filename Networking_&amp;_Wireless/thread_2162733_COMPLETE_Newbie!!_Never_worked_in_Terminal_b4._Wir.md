---
title: "COMPLETE Newbie!! Never worked in Terminal b4. Wireless worked initially, now NOT"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by jjwred7 on 2013-07-15
Hi Everyone.  Thank you in advance for taking the time to read my post.  I have searched as much as I possibly could to make sure I do this posting correctly.

I JUST installed Lubuntu 12.04 on an old Dell Inspiron 700M.   I truly am a COMPLETE NEWBIE and have NEVER ran dos prompts, terminal commands, NOTHING like that ever before.

I tried to look at the forum and copied and will paste as much info as I can find that might help to solve my issue.  Like I said I am a COMPLETE NEWBIE (but want to learn) and have never done anything like this before.  I am SURPRISED I ever got it running at all!!!  lol  I have my system setup to dual boot for either Windows XP or Lubuntu 12.04.    I HAD a wireless connection for the first day, then JUST when I was getting really excited about how much FASTER Lubuntu was than running all the bloat of Windows XP (evidently), SUDDENLY ALL the wireless connections disappeared.   Not only did I not get a wireless connection, there was system would no longer SEARCH for a wireless connection.

I LOVED Lubuntu 12.04 when it was working and would LOVE to get it working again because it COMPLETELY revitalized this machine!!   I am COMPLETELY LOST Now though.  I have done as many searches as I can and have NO IDEA where to go from here.  I dont really know the chipset or whatever wireless info is needed but I tried to follow the guidelines of the forum and post as much data as I Could from the commands I found on this site for wireless postings.

Again I have NO IDEA what I DID...I just typed in the terminal some of the EXACT codes you suggested here on this forum.

Btw the wireless connection DOES work in Windows, but not on Lubuntu.  I really want my Lubuntu back and would LOVE to become much more proficient at Ubuntu in general.  Baby steps I know, but I am ALREADY lost!! :-(

Below I will copy and paste the info I saved from the terminal in Lubuntu 12.04 in the instructions of this forum.  I HOPE I am posting the correct data.  

Like I said it WORKED initially and just as I began to get really excited it suddenly stopped working.   Btw the wired connection does work, but I never used wired and and it is not in a convenient area of the house.

Thank you again in advance for any help you can provide.

Here is the data I saved from terminal commands

```
lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)




00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:01.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
02:04.1 CardBus bridge [0607]: Texas Instruments PCI7420 CardBus Controller [104c:ac8e]
02:04.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller [104c:802e]
02:04.3 Mass storage controller [0180]: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller [104c:ac8f]
02:05.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)


$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:af:7d:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31840 (31.8 KB)  TX bytes:31840 (31.8 KB)


$ iwconfig
lo        no wireless extensions.


eth0      no wireless extensions.


rename3   unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


$ sudo lshw -C network
[sudo] password for jjwred7: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: rename3
       version: 04
       serial: 00:0c:f1:4f:1a:b0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:10 memory:e0206000-e0206fff
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 02
       serial: 00:0f:1f:af:7d:46
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:10 memory:e0204000-e0205fff
```

---

### Post by wildmanne39 on 2013-07-15
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by jjwred7 on 2013-07-15
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks


Thank you for the prompt replay Wild Man . I do not have ethernet at this time but I will try to run it per your instructions in the link.  If I cannot do that properly I will just wait until I can connected via ethernet in the morning.  Although I ADMIT I am IMPATIENT and want to try it NOW!!!  lol   Wish me luck on doing it right!!
Thanks again for your prompt reply!!!   I hope ONE DAY some of these things you are asking me to do actually MEAN something to me!!!  lol

---

### Post by jjwred7 on 2013-07-15
I am NOT sure if this is the right info (probably not) because I tried to do it via the link and executable without an ethernet connection.   Anyway...below is the only info I could find.  I TRIED to run the executable and it asked for my password, but I dont know if and what it did after that and where the info went!!!  lol

I am NOT sure if this info is pertaining to my computer or not or if I just copied info from your script!! lol

If not, I will just wait until I have an ethernet connection although this is killing me...lol

FILEBASE="wireless-info"
MODMATCHES="(air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt5|rt6|rt7|rtl|r818|r871|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etork)[^[:punct:] ]*"
exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCould not write target file \"$FILEBASE.txt\", aborting.\n\n"
    exit 1
fi
printf "\n*************** info trace ***************\n"
printf "\n***** uname -a *****\n\n"
uname -a
printf "\n***** lsb_release *****\n\n"
lsb_release -idrc
printf "\n***** lspci *****\n\n"
lspci -nnk | grep -iA2 net
printf "\n***** lsusb *****\n\n"
lsusb
printf "\n***** iwconfig *****\n\n"
iwconfig
printf "\n***** rfkill *****\n\n"
rfkill list all
printf "\n***** lsmod *****\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"
printf "\n***** nm-tool *****\n"
nm-tool
printf "\n***** NetworkManager.state *****\n"
cat /var/lib/NetworkManager/NetworkManager.state
printf "\n***** NetworkManager.conf *****\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi
printf "\n***** interfaces *****\n\n"
cat /etc/network/interfaces | sed -r 's/wpa-psk [[:graph:]]+/wpa-psk <WPA key removed>/'
printf "\n***** iwlist *****\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi
printf "\n***** resolv.conf *****\n\n"
grep -v '^#' /etc/resolv.conf
printf "\n***** blacklist *****\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
	BLACKLIST=$(grep '^blacklist' $CONFFILE)
	if [ -n "$BLACKLIST" ]; then
	    printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
	fi
    fi
done
printf "\n***** dmesg *****\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"
printf "\n****************** done ******************\n\n"
exec 1>&3 3>&-
exec 2>&4 4>&-
sed -r -i 's/([[:alnum:]][[:alnum:]]:){5}[[:alnum:]][[:alnum:]]/<MAC address removed>/' $FILEBASE.txt
if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm -f $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi

---

### Post by varunendra on 2013-07-15
It is the script itself. The result file (wireless-info.txt, or wireless-info.txt.tar.gz) would have been saved in the same folder from which you ran this script. Copy-paste the contents from that file (if it is a .txt one), or simply attach it to your next post here. :)

**PS:**
The fact that it asked for your password means you did it right. Congratulations for running your first Linux script ! ;)

---

### Post by jjwred7 on 2013-07-15
I tried to attach the file.  I hope it worked

---

### Post by varunendra on 2013-07-15
> **jjwred7 said:**
> I tried to attach the file.  I hope it worked

Yes it did. Since Wild Man seems to have gone offline, I guess I may try a few shots.

Is your wireless access-point named "ASIANROCKSTAR"? Because that is the one that seems to have the strongest signal.

If it is, then could you try changing the channel in the router/access-point from 7 to 1 or 11? These (channel 1 and 11) often work better with linux drivers.

Another thing you can do right in your system is to run the following command in terminal (shortcut key to open terminal is Ctrl+Alt+T) :
```
sudo iwconfig rename3 power off
```
Just copy-paste (with mouse) the above code in your terminal to avoid typing mistakes. This will turn the power management off on the wireless interface.
*[COLOR="#800000"][Note : sudo will ask for your password. You won't see anything on the screen while typing the password. Just type it correctly and press "Enter"][/COLOR]*

It's a weird name by the way for an interface (rename3). Did you try any other fixes lately?

---

### Post by wildmanne39 on 2013-07-15
There are a few things we need to check on.
> Mode:Managed  Channel=0
It says your router is on channel 0 it will not work on 0.
Please try 1 or 11.

It says > Nickname:"ipw2100"
but that name does not show up in the  iwlist scan.

Let's turn power managemnt off:
```
echo -e '#!/bin/bash\n/sbin/iwconfig wlan0 power off' | sudo tee -a /etc/pm/power.d/wireless

```
This file usually only has```
 auto lo
iface lo inet loopback
```in it did you remove network manager?> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#NetworkManager#iface eth0 inet dhcp
#NetworkManager#wpa-ssid DG860AE2
#NetworkManager#wpa-psk  DG860A6E1EE2

Edit:> udevd[340]: renamed network interface eth1 to rename3Very interesting in dmesg.
Thanks

---

### Post by jjwred7 on 2013-07-15
I think this is the SAME data...but I did it a second time just to make sure...

---

### Post by wildmanne39 on 2013-07-15
Did you clone the drive ubuntu is on by any chance? Did you remove network manager and set static ip?
Thanks

---

### Post by jjwred7 on 2013-07-16
> **Wild Man said:**
> Did you clone the drive ubuntu is on by any chance? Did you remove network manager and set static ip?
Thanks

Sorry for the long delay guys.  I had a wireless signal for 5 mins...rebooted and it was gone again (after executed some of your advice and turning off wireless power manangement).    I will wait until I am at work this morning so I can have a ethernet connection to try again.


It is a little frustrating that it doesnt seem to connect wirelessly.   

As far as your questions go Wildman, I DONT even know what any of that means!!!  lol  I DONT think I removed the network manager or set anything to a static ip but maybe I did by accident somehow.  As far as Cloning anything...I have NO IDEA.  I DID do this per some forum advice though: 


[LIST]
[*]open the 'Synaptic Package Manager' and search for 'bcm'

[*]uninstall the bcmwl-kernel-source package

[*]make sure that the firmware-b43-installer and the b43-fwcutter packages are installed

[*]reboot
[/LIST]

---

### Post by praseodym on 2013-07-16
Please open the file
```

gksudo gedit /etc/network/interfaces
```
and remove anything except
```
auto lo
iface lo inet loopback
```
Save, close the editor and reboot. This device maybe only supports WEP and WPA encryption, not WPA2. Which of the networks shown is yours? Please show also
```

cat /etc/udev/rules.d/70-persistent-net.rules
iwlist chan
ifconfig -a
```
Your router firmware is up-to-date? Channel "fixed", bandwidth to 20MHz, MAC-address filter is off and the network is not "hidden"? Check you router manual for applying these settings.

---

### Post by jjwred7 on 2013-07-16
> **praseodym said:**
> Please open the file
```

gksudo gedit /etc/network/interfaces
```
and remove anything except
```
auto lo
iface lo inet loopback
```
Save, close the editor and reboot. This device maybe only supports WEP and WPA encryption, not WPA2. Which of the networks shown is yours? Please show also
```

cat /etc/udev/rules.d/70-persistent-net.rules
iwlist chan
ifconfig -a
```
Your router firmware is up-to-date? Channel "fixed", bandwidth to 20MHz, MAC-address filter is off and the network is not "hidden"? Check you router manual for applying these settings.
 

I put that code in the Terminal (not sure if that is what you meant or not) and it appeared that nothing happened.  It asked me for my administrative password but nothing appeared to happen.

I dont know what the editor is if we are not talking about the Terminal

---

### Post by praseodym on 2013-07-16
Sorry, you are using Lubuntu, so the 1st line needs to be
```

gksudo leafpad /etc/network/interfaces
```

---

### Post by jjwred7 on 2013-07-16
> **praseodym said:**
> Sorry, you are using Lubuntu, so the 1st line needs to be
```

gksudo leafpad /etc/network/interfaces
```


I did as per your instructions, saved and rebooted and still no wireless connection.
I ran the next commands and got this:

jjwred7@ubuntu:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:05.0/ssb0:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:1f:af:7d:46", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:02:01.0 (ipw2100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0c:f1:4f:1a:b0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
jjwred7@ubuntu:~$ iwlist chan
lo        no frequency information.


eth0      no frequency information.


rename3   14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Channel:0


jjwred7@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:1f:af:7d:46  
          inet addr:192.168.0.31  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:feaf:7d46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:990025 (990.0 KB)  TX bytes:183283 (183.2 KB)
          Interrupt:10 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31157 (31.1 KB)  TX bytes:31157 (31.1 KB)


rename3   Link encap:Ethernet  HWaddr 00:0c:f1:4f:1a:b0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by praseodym on 2013-07-16
Setup a new file because of the strange outputs of "ifconfig":
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
sudo service network-manager restart
```

Check:
```

cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
iwlist chan
dmesg | grep iwl
```

---

### Post by jjwred7 on 2013-07-16
> **praseodym said:**
> Setup a new file because of the strange outputs of "ifconfig":
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
sudo service network-manager restart
```

Check:
```

cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
iwconfig
sudo iwlist scan
cat /etc/resolv.conf
iwlist chan
dmesg | grep iwl
```

Do I input ALL of the sudo code stuff at ONCE (copy and paste) or do I need to do them one at a time???   Sorry, this truly is ALL new to me!!  :-)   Thank you in advance for your help.

---

### Post by praseodym on 2013-07-16
Each of the lines seperately, one after another

---

### Post by jjwred7 on 2013-07-17
> **praseodym said:**
> Each of the lines seperately, one after another

Hi Praseodym. I input the codes per your instructions and now I am MAGICALLY writing to you on a WIRELESS connection!!  :-)  I even REBOOTED and it came back!!  lol

I TRIED to copy the code results you wanted me to run, but for some reason it will not let me attach the results (say invalid file format).   I am going to take this laptop out to a NEW wireless connection today just to see if it can find it!!!

SO far I am SO HAPPY!!!  Thank you for your help everyone!!!   I have NO idea what I am doing (obviously) but it sure has sped up what was a USELESS computer (essentially).  If  can keep it working for a week I think I will actually install Ubuntu on (Not Lubuntu necessarily) on a computer with some greater processing power!

Thanks again and I HOPE it continues working!!!  lol

I did say the results from the codes you asked me to run afterward, I dont know why I cannot attach them in a proper file format this time.

---

### Post by praseodym on 2013-07-17
For Ubuntu you need at least 1 GB RAM (2 GB recommended!). Alternatively, with less RAM you can try Xubuntu 12.04 long-term support (LTS) or Lubuntu 13.04 (no LTS!)

---

### Post by jjwred7 on 2013-07-17
WooHoo....I am NOW at the Public Library replying on their wireless connection whilst on Lubuntu 12.04!!!  :-)   Thank you SO MUCH to ALL who helped!!!  I hope this works when I get home tonight on my network.   I have NO IDEA WHAT you guys did or what any of those codes I put into Terminal meant, but I hope ONE day maybe I will have SOME idea!!

Thank you again to ALL!!!!

---

