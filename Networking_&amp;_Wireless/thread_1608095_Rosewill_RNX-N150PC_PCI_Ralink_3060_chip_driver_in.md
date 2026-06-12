---
title: "Rosewill RNX-N150PC PCI Ralink 3060 chip driver instructions"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by MooPi on 2010-10-28
This is the procedure I used to install the driver for my new Rosewill Rosewill RNX-N150PC PCI 2.2 Wireless Adapter. It uses the Ralink 3060 chip. I'm using Lucid 10.04 and WICD as my network manager.(I have tested this driver and method on both 10.10 & currently 11.04 with success) I downloaded the drivers from Ralinks site
[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D")

Make sure you have installed gcc build-essential ```
sudo apt-get install gcc build-essential
```
I then followed the instuctions in the README file.
Navigate to downloaded_driver_folder/os/linux and open config.mk in a text editor.
Find and set so that it indicates ( y ) at the end of this text string```
[COLOR="blue"]HAS_WPA_SUPPLICANT=y[/COLOR]
```

and also set ```
[COLOR="blue"]HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y[/COLOR]
```
 
 Next, open a terminal in the driver folder and type ```
sudo make
```
 then ```
sudo make install
```
 
 
 Now you'll need to load the driver
 ```
sudo modprobe rt3562sta
```
 ```
sudo ifconfig ra0 inet up
```
 
 
 After I successfully connected I added the driver to /etc/modules so it it would load at startup. This is a copy of mine
 
```
 # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rt3562sta.ko
```

Edit complete save file and reboot to test. I hope this helps anyone using Raklink 3060/3062/3562 chipset. Mine connects with a strong consistent signal.

Looks as if an addition is necessary to complete the driver install. The need to blacklist a default driver to enable the new driver. 
From terminal
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Add this to the end of that file
```
blacklist rt2800pci
```

---

### Post by Shualdon on 2010-10-28
I used this driver in 10.04 and it worked fine.
But now I use 10.10, and although the driver is running - both Wicd and Network Manager can't find any networks.

---

### Post by MooPi on 2010-10-28
> **Shualdon said:**
> I used this driver in 10.04 and it worked fine.
But now I use 10.10, and although the driver is running - both Wicd and Network Manager can't find any networks.

I haven't tested under 10.10 yet. What have you done so far to get the device working ?

---

### Post by Shualdon on 2010-10-28
> **MooPi said:**
> I haven't tested under 10.10 yet. What have you done so far to get the device working ?

I use my brother's USB wireless adapter which has a built-in support...

---

### Post by MooPi on 2010-10-28
No what have you done to get your Ralink device working ?
How about we try some terminal commands to see what comes up.
```
lspci -v | less
```
```
iwconfig
```
If you show a network in the last command run this.
```
iwlist scanning
```
Post any results back here please

---

### Post by Shualdon on 2010-10-28
I have Edimax EW-7711In (PCI).
It shows up in ifconfig, but that's it.

lspci -v (only the related part)
```
05:02.0 Network controller: RaLink Device 3060
        Subsystem: Edimax Computer Co. Device 7711
        Flags: bus master, slow devsel, latency 32, IRQ 18
        Memory at fbcf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt3562sta, rt2800pci

```

iwconfig (wlan2 is the Ralink, wlan1 is the USB)
```
lo        no wireless extensions.

eth1      no wireless extensions.

wlan2     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"confidential"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:B0:72:9A:BD   
          Bit Rate=54 Mb/s   Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scanning
```
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan2     No scan results

vboxnet0  Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:22:B0:72:9A:BD
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"confidential"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ea5a89e570
                    Extra: Last beacon: 19568ms ago
                    IE: Unknown: 00096162617262616E656C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

---

### Post by MooPi on 2010-10-28
Looks as if you just have to tell your computer to use the device. In terminal  ```
ifdown wlan1
``` ```
ifup wlan2
```
Then open wicd and under preference change your wireless adapter to wlan2

---

### Post by Shualdon on 2010-10-28
> **MooPi said:**
> Looks as if you just have to tell your computer to use the device. In terminal  ```
ifdown wlan1
``` ```
ifup wlan2
```
Then open wicd and under preference change your wireless adapter to wlan2

```
Ignoring unknown interface wlan1=wlan1.

```
and the same result with wlan2.

---

### Post by MooPi on 2010-10-28
Sorry you need su privelges
```
sudo ifdown wlan1
```
```
sudo ifup wlan2
```

---

### Post by Shualdon on 2010-10-28
```
omri@omri-desktop:~$ sudo ifdown wlan1
ifdown: interface wlan1 not configured
omri@omri-desktop:~$ sudo ifup wlan2
Ignoring unknown interface wlan2=wlan2.

```

---

### Post by MooPi on 2010-10-28
How about ```
sudo ifconfig wlan1 down
``````
sudo  ifconfig wlan2 up
```

---

### Post by Shualdon on 2010-10-28
well... this is weird.
after the "wlan1 down" command - the network disconnects.
but after a few seconds all goes back to normal. somehow wlan1 is waking up automatically....

---

### Post by MooPi on 2010-10-28
It is probably set to automatically reconnect. You may have to remove the device to test the wlan2 .

---

### Post by Shualdon on 2010-10-28
Ok...
I disconnected wlan1 and did "sudo ifconfig wlan2 up" again.
but no luck here. no response. nothing changed. :\

---

### Post by MooPi on 2010-10-28
I noticed that your card has two modules loading for it .
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Add this line at the end of the file
```
blacklist rt2800pci
```
You'll need to reboot then ```
iwconfig
```

---

### Post by Shualdon on 2010-10-28
ahh!
It's alive! ALIVE!

I had "blacklist rt2800**usb**", but after adding the "pci" one and rebooted - It's all seems to go back to normal!

Thank you very very much :)

---

### Post by hanasaki on 2010-12-10
[LIST]
[*]Is there support in the standard bundled Ubuntu 10.10 kernels?
[LIST]
[*]If not, what is a good lower priced PCI 802.11g,n (preferably low / high profile like this) that works "out of the box"?
[*]If not, can you sum up what had to be done to get it to work on 10.10?
[/LIST]
 
[*]Any feedback on the overall performance or what may be better for the about the same cost?
[/LIST]
Thanks,

---

### Post by bagwanram on 2011-01-01
Hello!
I am trying to get my Rosewill RNX N150pcx installed in 10.04lts. I got to the 5th step: Now you'll need to load the driver
 
Code:
sudo modprobe rt3562sta.ko

these commands just result in: FATAL Module rt3562sta.ko not found

lspci shows a network controller at 02:09.0 RaLink Device 3060 etc...

the funny thing is when I opened Hardware Drivers rt3562sta.ko was there. it says the driver is activated but not currently in use. So I deactivated it. then reactivated it. It worked! I connected to my wireless router.

BUT... after reboot no such luck. the driver still says its active but not in use. but if i disable/reable, it just asks for reboot and I am back to where i started.(no connection)
And I did add the lines to /etc/modules and saved it....

One Note, Make Install required sudo privledges. but i did not use it on the Make Command.....

Thanks for the help!

Jazz

---

### Post by bagwanram on 2011-01-01
I used 'sudo make' started the whole processover with a fresh driver folder and it made it work!
 yeah!

---

### Post by cbutzon on 2011-01-27
I followed the instructions to install the driver for my wireless adapter, but it appears that it doesn't "see" any available networks (despite being 10 feet from a working access point). Here's some info that MooPi suggested would be helpful:

lspci -v | less:

```
05:00.0 Network controller: RaLink Device 3060
        Subsystem: RaLink Device 3060
        Flags: bus master, slow devsel, latency 32, IRQ 20
        Memory at fdcf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt3562sta, rt2800pci
```iwconfig: 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```iwlist scanning
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```Can someone please give me some guidance? Thanks in advance.

EDIT: I also tried the "connect to a hidden wireless network" option and entered the WAP's name and WPA2 security key -- still no luck. For what it's worth, it connects just fine in Windows on the same machine.

---

### Post by eurik on 2011-02-21
```
make -C /home/ged/Plocha/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux -f Makefile.6 install
mkdir: adresá&#345; &#8222;/etc/Wireless&#8220; nelze vytvo&#345;it: Soubor ji&#382; existuje (file already exists)
make[1]: Entering directory `/home/ged/Plocha/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/ged/Plocha/2008_1225_RT3070_Linux_STA_v2.0.1.0/RT3070STA.dat /etc/Wireless/RT3070STA/.
cp: nelze získat informace o &#8222;/home/ged/Plocha/2008_1225_RT3070_Linux_STA_v2.0.1.0/RT3070STA.dat&#8220;: Adresá&#345; nebo soubor neexistuje (no such file or directory)
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ged/Plocha/2008_1225_RT3070_Linux_STA_v2.0.1.0/os/linux'
make: *** [install] Error 2

```Hi, I have the Edimax EW-7711 and no luck bringing it to live.

I tried to follow this (on Ubuntu 10.10) and while running the make install of the driver, I got the error message above. Any suggestions please? I'm stuck.

(running both make and make install as root)

edit: [http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D)

I installed the new one that you postet in another thread, and the make, make install went allright,

but when I try running the driver, it says not found - how do I find the proper name  of the driver?

---

### Post by eurik on 2011-02-23
Found the module /lib/modules/2.6.35_25_generic/kernel/drivers/net/wireless/rt3562sta.ko but still getting the same error message - not found?!

---

### Post by rrinker on 2011-02-25
Been a while since I've been on here, but I just built a new system with an Atom D510 to use on my model railroad, and Ubuntu seemed like a natural. Since I have no way to do wired ethernet in the location where this machine will be, I picked up the Rosewill RNX-N250 card with the RT3062 chip. Basically after reading this and other threads which indicated that I would indeed be able to get it to work with 10.10. 
 Machine build and install went fine, today I tried to follow the steps in this thread line by line - and got errors. Particularly, the sudo modprobe rt3562sta.ko reported that the file did not exist. However, I proceeded onward and added the blacklist entry for the RT2800PCI and rebooted - AND IT WORKED. I am wirelessly connecting just fine.
 I really can't explain, or even figure out how it would ever work when an important step clearly fails, but it does. So take heart if the process results in an error, it may not be as critical as it appears. In the README file included with the downloaded driver files mentions using insmod, and I tried that, but that told me the module was already there. That's why I decided to move on and add the blacklist and give it a try. I'm sure there's some really dumb reason it worked anyway, but I am by no means a Linux expert. My first taste was way back at 0.89a but I haven't been a regular user that entire time.

                   --Randy

---

### Post by chili555 on 2011-02-25
> sudo modprobe rt3562sta.ko That's incorrect; it should be:```
sudo modprobe rt3562sta
```The file extension .ko is not required.

---

### Post by rrinker on 2011-02-25
> **chili555 said:**
> That's incorrect; it should be:```
sudo modprobe rt3562sta
```The file extension .ko is not required.

 Pretty sure I tried that too, same error, file does not exist.

Of course, dare I speak too soon, I applied all the latest updates once I got the box online, and when I restarted - no wireless. I repeated the make and make install steps, rebooted, and was back in business.

                   --Randy

---

### Post by holbrooka on 2011-03-07
> **cbutzon said:**
> I followed the instructions to install the driver for my wireless adapter, but it appears that it doesn't "see" any available networks (despite being 10 feet from a working access point). Here's some info that MooPi suggested would be helpful:

lspci -v | less:

```
05:00.0 Network controller: RaLink Device 3060
        Subsystem: RaLink Device 3060
        Flags: bus master, slow devsel, latency 32, IRQ 20
        Memory at fdcf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt3562sta, rt2800pci
```iwconfig: 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```iwlist scanning
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```Can someone please give me some guidance? Thanks in advance.

EDIT: I also tried the "connect to a hidden wireless network" option and entered the WAP's name and WPA2 security key -- still no luck. For what it's worth, it connects just fine in Windows on the same machine.
cbutzon,
Did you have any luck getting it all working?  I was having a similar issue.  Everything working fine under 9.04, upgraded to 9.10, working great, upgraded to 10.04 and suddenly it was like my card working at all, not finding any wireless networks.

In some setting or other I had noticed I had a "wlan0", but I had always used my "ra0" for my wireless interface in WICD.  I tried a few things first (purgeing  WICD and re-installing, no change), then I simply changed the wireless interface in the WICD preferences box and it started up right away.

Hope you are up and running.

---

### Post by AdRock952 on 2011-03-08
Hello

Just installed Ubuntu 10.10 and I have an Edimax EW-7711ln wireless card.

I need to get it installed and drivered so I can get online but the problem is that I don't have a network card or even a network connection on the mobo becuase it's quite old so i can't even get online with it to download any drivers.

I have a folder (don't know which version) with all the files inside.

I was following the instructions on the first post on how to install the drivers and i've checked to see if GCC is installed and it is.

Now i don't know what to do here where it says set

> HAS_WPA_SUPPLICANT=y

When i open the file in the text editor, it's just an blank empty file.  Do i need to add these lines or should there be code there already?

Where can I get a driver that will work if this one is wrong or just help installing?

---

### Post by interzoneuk on 2011-03-08
AdRock952 the file should contain data already.

I have just used the DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz driver to make my add-on NWP210 work.

The file that you need to change 'HAS_WPA_SUPPLICANT=y' is in

... say I extracted the driver in 

/home/morgan/src/drivers/wlan_addon_NWP210/

I would 

cd  /home/morgan/src/drivers/wlan_addon_NWP210/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217

then edit (nano / vi / text editor) 

/home/morgan/src/drivers/wlan_addon_NWP210/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk

initially it will have 

--------------------------------
# Support ATE function
HAS_ATE=n

# Support QA ATE function
HAS_QA_SUPPORT=n

# Support XLINK mode
HAS_XLINK=n


# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n

# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

#Support Net interface block while Tx-Sw queue full
HAS_BLOCK_NET_IF=n

#Support DFS function
HAS_DFS_SUPPORT=n

#Support Carrier-Sense function
HAS_CS_SUPPORT=n


# Support for Multiple Cards
HAS_MC_SUPPORT=n

#Support for PCI-MSI
HAS_MSI_SUPPORT=n


#Support for IEEE802.11e DLS
HAS_QOS_DLS_SUPPORT=n

#Support for EXT_CHANNEL
HAS_EXT_BUILD_CHANNEL_LIST=n


#Support for Net-SNMP
HAS_SNMP_SUPPORT=n

#Support features of 802.11n Draft3
HAS_DOT11N_DRAFT3_SUPPORT=y

#Support features of Single SKU. 
HAS_SINGLE_SKU_SUPPORT=n

#Support features of 802.11n
HAS_DOT11_N_SUPPORT=y

... lots more
--------------------------------

try downloading the file again

Also extract with tar xfvz DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz

- Does anyone know how to stop the ralink driver spamming dmesg?

you then need to sudo make then sudo make install btw

---

### Post by AdRock952 on 2011-03-08
Thanks for your reply

I downloaded it again and was now able to edit those lines.

I ran the make and make install commands using sudo and i noticed that there were some warnings while compiling.  Is that anything to worry about?  It seemed to compile without any errors i think.

The problem I have now is what folder do i need to be in when i run

> sudo modprobe rt3562staDoes it create the file in the /os/linux folder?

I think i found the file there and I run that command inside of that folder but i don't know if has done anything becuase it goes back to command line with no message.

EDIT:

I think i got the driver created but i need to start it.

I went into the driver folder, used the modprobe command and got this output

> FATAL Module rt3562sta.ko not foundHere is my output like other users have shown

lspci -v (only the related part)
> 00:08.0 Network controller: RaLink Device 3060
        Subsystem: Edimax Computer Co. Device 7711
        Flags: bus master, slow devsel, latency 32, IRQ 18
        Memory at fbcf0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt3562sta, rt2800pciiwconfig
> lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:0ff   Fragment thr:off
          Power Management:offiwlist scanning
> lo        Interface doesn't support scanning.

wlan0     No scan results

---

### Post by chili555 on 2011-03-08
> The problem I have now is what folder do i need to be in when i run

Quote:
sudo modprobe rt3562sta
Does it create the file in the /os/linux folder?You can run the command anywhere. Once you have the module installed globally in your system, the inner workings of the command 'modprobe' take care of that for you. If there is an error, you will be notified.

No real harm with warnings.

---

### Post by AdRock952 on 2011-03-08
I've run that

> sudo modprobe rt3562staand it's got back to command line.

How do i know if it's installed and how do i start the wireless?

Just run this command

> sudo ifconfig ra0 inet upand the error message is
> 
ra0: ERROR while getting interface flags: No such device

---

### Post by chili555 on 2011-03-08
> I've run that

Quote:
sudo modprobe rt3562sta
and it's got back to command line.
That means, roughly, "command accepted and no errors to report, sir!"> How do i know if it's installed and how do i start the wireless?Do you have a wireless interface, ra0 or otherwise, when you run:```
iwconfig
```What interesting kernel messages are there?```
dmesg | grep -e rt2 -e rt3
```Ordinarily, you should be able to click the Network Manager icon, see networks and click yours to connect.

---

### Post by AdRock952 on 2011-03-08
I went back and looked at some of the earlier posts and now i've got it working

What is needed is a really well explained tutorial beuase apart from on here I've found nothing about installing wireless network drivers.

---

### Post by MooPi on 2011-03-17
I just updated to the latest kernel running under 10.04 ( 2.6.32-29-generic ) and discovered that my wireless was not working. Reboot to an earlier kernel and wireless worked. So I deduced that I needed to reinstall the driver for the latest kernel. Followed my own instructions to install again and everything is back and running again.
As chili555 says below( make clean ) an important step to correctly complete the re-installation.

---

### Post by chili555 on 2011-03-17
> So I deduced that I needed to reinstall the driver for the latest kernel. Quite correct. Whenever a new kernel or, in Ubuntu-speak, linux-image is installed, you'll need to reinstall. Navigate to the RT3060 folder and do:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt3562sta
exit
```

---

### Post by valem on 2011-03-19
Hi guys, I am fairly new to Linux and Ubintu, but reading this thread (and this forum) has helped me install and use my wireless adapter. Thank you!

That is until last night following some ubuntu updates.
I was using my computer and I noticed the update manager. So I clicked the checkmark to proceed with the updates.

A couple of hours later I was done working, and before I shut down I noticed that the updates required a reboot. So I decided to reboot and then shut down.
After the reboot I noticed that I had no internet connection, and I actually realized that the wireless adapter "disappeared". Even the lights on the card are not flashing anymore. At least the first time I installed the card the lights were flashing. Now it's dead. So I had to move the PC to wire it up (ethernet still works)

I have no idea what to do. I tried to reinstall the drivers from scratch, but I realized that that is not the problem, the card is missing.

iwconfig does not even show it anymore!

Is there any way to find out what the latest update includes? Anyway to uninstall the updates?

I found this command "lshw -c network" and this is what it returns:

root@vale-desktop:/home/vale/Downloads/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0# lshw -c network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: c
       bus info: pci@0000:00:0c.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:ef000000-ef00ffff
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 00
       serial: 00:09:5b:0a:29:60
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:12 ioport:d000(size=256) memory:ef010000-ef010fff memory:80000000-8000ffff

Any thoughts hints or suggestion ?
tia
vale

---

### Post by chili555 on 2011-03-19
> Any thoughts hints or suggestion ?Did you undertake the steps outlined in the post just above yours? Any errors to report?

---

### Post by valem on 2011-03-19
The main error is that the system does not seem to see the that there is a wireless adapter.
I want to point out that I succeeded in installing the drivers and I had been using the wireless card for over two weeks.
The wireless adapter disappeared after some Ubuntu updates last night that required to reboot.

---

### Post by chili555 on 2011-03-19
> **valem said:**
> The main error is that the system does not seem to see the that there is a wireless adapter.
I want to point out that I succeeded in installing the drivers and I had been using the wireless card for over two weeks.
The wireless adapter disappeared after some Ubuntu updates last night that required to reboot.> Whenever a new kernel or, in Ubuntu-speak, linux-image is installed, you'll need to reinstall. Navigate to the RT3060 folder and do:

```
sudo su
make clean
make
make install
modprobe rt3562sta
exit
```

Did you do as I suggested? Were there errors?

---

### Post by valem on 2011-03-19
Thanks for the help, it works now.
It was due to the new Kernel! I had no idea I needed to re-install every-time the kernel is updated.
Thanks!

---

### Post by interzoneuk on 2011-03-23
valem - just to let you know in later kernels there is no need to add the driver after an update.

I am also running Arch linux (amd64) with the latest kernel (from testing) 2.6.38 - the in kernel drivers work well (better IMO) so no need to compile anything.

Hopefully in Natty it will just work out the box.

Cheers

---

### Post by lbriner on 2011-04-26
There was another step mentioned afterwards where you need to blacklist the built-in RT2800 driver so that the kernel will load the driver you just built. Add "blacklist rt2800pci" without the quotes to the end of /etc/modprobe.d/blacklist.conf and then reboot.

---

### Post by catlover2 on 2011-04-30
Hello, 

You helped me over here at one point: [http://ubuntuforums.org/showthread.php?t=1713808](http://ubuntuforums.org/showthread.php?t=1713808)
This still works in Natty, just upgraded today.

I only did this part:

> I then followed the instuctions in the README file.
Navigate to downloaded_driver_folder/os/linux and open config.mk in a text editor.
Find set     
     ```
HAS_WPA_SUPPLICANT=y 
```and also set      
     ```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y 
``` Open a terminal in the driver folder and type
     ```
sudo make 
``` then
     ```
sudo make install 
``` Now you'll need to load the driver
      
     ```
sudo modprobe rt3562sta 
```      and before with Maverick, you had me do this:
> Your going to need to blacklist some modules that are interfering . Open  /etc/modprobe.d/blacklist.conf  with your choice of text editor. For  example sake I'll select gedit
     
     ```
sudo gedit /etc/modprobe.d/blacklist.conf 
```At the end of the file add these lines
     
     # blacklist for rt3562sta blacklist rt2800pci blacklist rt2800lib blacklist rt2800usb blacklist rt2x00pci blacklist rt2x00lib blacklist rt2x00usb 
And apparently that blacklisting was not modified during the upgrade.

Thanks tor the great tutorial!

Catlover

---

### Post by chili555 on 2011-04-30
If you rebuild for a newer kernel, which Natty has, you need to do:

Code:
[COLOR="Red"]sudo make clean
[/COLOR]
sudo make

then
Code:

sudo make install

Now you'll need to load the driver

Code:

sudo modprobe rt3562sta

---

### Post by EriktheAwful on 2011-05-04
Thanks, chili! I updated to 11.04 yesterday and have been trying to get my wireless back up and running. I followed these instructions and it works fine now.
[quote=chili555]```

sudo su
[COLOR=Red]make clean
[/COLOR]make
make install
modprobe rt3562sta
exit
```[/quote]

The hardest part was realizing "Navigate to the RT3060 folder" meant finding the download folder in Terminal.

---

### Post by chili555 on 2011-05-04
Good work! Happy it's working now.

---

### Post by ratcheer on 2011-06-14
This is a great thread! I used it to get my Ralink 3060 in my new PC working. I had also had to do a similar thing to get my wired ethernet NIC to work. I wonder why Ubuntu consistently picks up the wrong drivers for certain hardware items?

One more question, please. Now that I have both wired and wireless working, should I turn off one or the other? If both are connected, which connection will Ubuntu actually use?

Thanks so much for this thread.

Tim

---

### Post by chili555 on 2011-06-14
> **ratcheer said:**
> This is a great thread! I used it to get my Ralink 3060 in my new PC working. I had also had to do a similar thing to get my wired ethernet NIC to work. I wonder why Ubuntu consistently picks up the wrong drivers for certain hardware items?

One more question, please. Now that I have both wired and wireless working, should I turn off one or the other? If both are connected, which connection will Ubuntu actually use?

Thanks so much for this thread.

TimPlease see: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for them;If you have easy access to wired ethernet, I'd use it exclusively. It's faster and far more secure.

---

### Post by ratcheer on 2011-06-14
> **chili555 said:**
> Please see: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)If you have easy access to wired ethernet, I'd use it exclusively. It's faster and far more secure.

That was my hunch, as well. I have unchecked "Enable Wireless" in the network indicator and everything is working as expected.

Thank you,
Tim

---

### Post by Tengo_Hambre on 2011-07-13
Hi all, 

i'm a complete linux noob, and i'm trying to get my PCI wireless card working (Azio AWD102N).  After following the instructions in the thread at [COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1745435](http://ubuntuforums.org/showthread.php?t=1745435)[/COLOR], i ran into the same problems with the original driver, and after following the thread, i am now trying to install the RT3562 driver from [COLOR=Blue][http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)[/COLOR].  i follow essentially the same steps in the tutorial at [COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)[/COLOR], except the initial cd command i use is cd DPO* to get me into the right directory.  anyway, when the time comes to execute sudo make and sudo make install, i am getting an error and cannot get any further in the steps.  here's what it gives me

```

make -C tools
make[1]: Entering directory `/home/brock/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/brock/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 2/tools'
/home/brock/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 2/tools/bin2h
make: /home/brock/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217: Command not found
make: *** [build_tools] Error 127
```any ideas on how to get this to work?  Thanks a bunch!

---

### Post by ratcheer on 2011-07-13
Tengo_Hambre, make sure you have packages build-essential and the linux-headers for your current kernel installed.

Tim

---

### Post by chili555 on 2011-07-13
> **ratcheer said:**
> Tengo_Hambre, make sure you have packages build-essential and the linux-headers for your current kernel installed.

Timratcheer is absolutely correct. However, if he wanted to be absolutely, perfectly, beautifully correct, he'd suggest build-essential and linux-headers-*generic*.

---

### Post by Tengo_Hambre on 2011-07-13
> **chili555 said:**
> ratcheer is absolutely correct. However, if he wanted to be absolutely, perfectly, beautifully correct, he'd suggest build-essential and linux-headers-*generic*.

sorry if you saw my preemptive first post.  i checked and i have build essential installed.  i tried to install linux headers generic, but the software center says "dependency is not satisfiable: linux-headers-2.6.38.10-generic"

---

### Post by chili555 on 2011-07-13
> "dependency is not satisfiable: linux-headers-2.6.38.10-generic"Uh oh! I just got linux-headers-2.6.38.10-generic from Update Manager today and I wondered about it. My running kernel is 2.6.38.8-generic. I wonder if the newer kernel itself was held up for some reason. I'm sure it will sort itself out soon.

ratcheer is in charge here, but if I may suggest, I'd install linux-headers-`uname -r` for now and make a note to install -generic in a few days. What generic does is keep the headers updated automagically as a later kernel or linux-image is offered by Update Manager.

OK, back to you, ratcheer.

---

### Post by Tengo_Hambre on 2011-07-13
> **chili555 said:**
>  My running kernel is 2.6.38.8-generic. 

i tried downloading and installing this one instead--it is already installed.  so i have both of the packages mentioned installed.  any other ideas?  i also tried installing the driver from azio's site, it seems to have issues as well, though it gets farther than the 3562 driver:
```

brock@brock-Z68X-UD3-B3:~$ cd 2009*
brock@brock-Z68X-UD3-B3:~/2009_0521_RT2860_Linux_STA_V2.1.2.0$ sudo make
[sudo] password for brock: 
make -C tools
make[1]: Entering directory `/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/tools'
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.o
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSTaskAttach&#8217;:
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:1231:8: warning: unused variable &#8216;pid_number&#8217;
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSNetDevAttach&#8217;:
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:1570:10: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:1571:10: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:1572:10: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:1573:10: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:1579:11: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.c:1613:9: error: &#8216;struct net_device&#8217; has no member named &#8216;validate_addr&#8217;
make[2]: *** [/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/../../os/linux/rt_linux.o] Error 1
make[1]: *** [_module_/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2
brock@brock-Z68X-UD3-B3:~/2009_0521_RT2860_Linux_STA_V2.1.2.0$ sudo make installmake -C /home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2860sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2860sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/brock/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux'
make: *** [install] Error 2
brock@brock-Z68X-UD3-B3:~/2009_0521_RT2860_Linux_STA_V2.1.2.0$
```

edit: if it might be easier to go back to trying the rt2860 driver, i tried it again today and it seems to run into a hangup with the "sudo ifconfig wlan0 down" command...

```
wlan0: ERROR while getting interface flages: No such device
```

---

### Post by Luponiano on 2011-07-29
Hello, I have followed the instructions in this thread and I have the card working but it behaves strangely. And by strangely I mean it connects to my access point and keeps connected but the data is as if were sended intermittently. So, for instance, firefox navigation stops for about 8 seconds and the page suddenly appears. This happens also with transmission, which works for about 10 seconds, then it stops sending and receiving, and suddenly it starts again transmitting. And most strange, when accessing the router config page this kind of lag also happens. If I plug the old usb wireless it works smoothly without interruptions.

Any clue? May the card be broken?
```

iwconfig:
ra0       Ralink STA  ESSID:"Pumpol"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 5C:4C:A9:98:A4:51   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=67/100  Signal level:-62 dBm  Noise level:-74 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chili555 on 2011-07-29
The signal strength is a concern. Are you far away from the access point? Also, may we see: ```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by Luponiano on 2011-08-02
Sure, this is the result:

```
lsmod | grep -e rt2 -e rt3
rt3562sta             874110  1
```

I have repeated the process and still the same "lag" problem. The usb stick does not seem to suffer from this behaviour.

Thank you!

---

### Post by Luponiano on 2011-08-02
The network card box says it is a WGLPC150, not a Rosewill, but is identified with "lspci" with:

```
03:00.0 Network controller: Ralink corp. Device 3060
```


Typing "iwconfig" this is what I get:

```

ra0       Ralink STA  ESSID:"Pumpol"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 5C:4C:A9:98:A4:51   
          Bit Rate=150 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-62 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chili555 on 2011-08-02
> **Luponiano said:**
> The network card box says it is a WGLPC150, not a Rosewill, but is identified with "lspci" with:

```
03:00.0 Network controller: Ralink corp. Device 3060
```


Typing "iwconfig" this is what I get:

```

ra0       Ralink STA  ESSID:"Pumpol"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 5C:4C:A9:98:A4:51   
          Bit Rate=150 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-62 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Lots of people sell wireless devices with Ralink chipsets. This iwconfig looks spectacular! N speeds and quality 100/100! Does it still lag? Are there any clues here?```
sudo cat /var/log/syslog | grep etwork | tail -n25
```Is there some other process on your computer that's hogging CPU or GPU cycles? Open a terminal and run:```
top
```What is the top-most process under %CPU that's running as you surf in Firefox?

---

### Post by Luponiano on 2011-08-02
Hello, I repeated the iwconfig several times, this could be the average of all of them:
```

ra0       Ralink STA  ESSID:"Pumpol"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 5C:4C:A9:98:A4:51   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=78/100  Signal level:-61 dBm  Noise level:-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Network syslogs as I typed your command are:
```

Aug  2 13:54:51 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug  2 13:54:51 TorreTuent kernel: [14922.454022] ===>Set_NetworkType_Proc::(INFRA)
Aug  2 13:54:51 TorreTuent kernel: [14922.454025] Set_NetworkType_Proc::(NetworkType=1)
Aug  2 13:54:51 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  associating -> associated
Aug  2 13:54:51 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  associated -> 4-way handshake
Aug  2 13:54:51 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 13:54:51 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  group handshake -> completed
Aug  2 13:56:29 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  completed -> disconnected
Aug  2 13:56:29 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug  2 13:56:31 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug  2 13:56:31 TorreTuent kernel: [15022.491063] ===>Set_NetworkType_Proc::(INFRA)
Aug  2 13:56:31 TorreTuent kernel: [15022.491066] Set_NetworkType_Proc::(NetworkType=1)
Aug  2 13:56:31 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  associating -> associated
Aug  2 13:56:31 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  associated -> 4-way handshake
Aug  2 13:56:31 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 13:56:31 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  group handshake -> completed
Aug  2 13:58:34 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  completed -> disconnected
Aug  2 13:58:34 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  disconnected -> scanning
Aug  2 13:58:36 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  scanning -> associating
Aug  2 13:58:36 TorreTuent kernel: [15146.697930] ===>Set_NetworkType_Proc::(INFRA)
Aug  2 13:58:36 TorreTuent kernel: [15146.697933] Set_NetworkType_Proc::(NetworkType=1)
Aug  2 13:58:36 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  associating -> associated
Aug  2 13:58:36 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  associated -> 4-way handshake
Aug  2 13:58:36 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  4-way handshake -> group handshake
Aug  2 13:58:36 TorreTuent NetworkManager[932]: <info> (ra0): supplicant connection state:  group handshake -> completed

```

The computer is a quadcore Q6600 @ 2.40Ghz with 4GB RAM. When the network stops none of the cpus is higher in use than 10%.

This is top result:
```

 1155 root      20   0  482m 311m 261m S    2  7.7   9:08.55 Xorg                                                    
 3136 lupo      20   0  147m  28m  16m S    2  0.7   7:26.71 chrome                                                  
 2289 lupo      20   0  148m  21m  16m S    1  0.5   2:56.15 clock-applet                                            
 3265 lupo      20   0  185m  45m  26m S    1  1.1   4:36.70 spotify                                                 
 2562 lupo      20   0  145m  30m  14m S    1  0.7   2:36.03 transmission-gt                                         
 3068 lupo      20   0  175m  54m  19m S    1  1.4   1:18.15 chrome                                                  
 6978 lupo      20   0 97712  22m  17m S    1  0.6   0:46.69 gnome-system-mo                                         
 7038 lupo      20   0  549m 245m  32m S    1  6.1   0:23.54 firefox-bin  

```

The snapshot was taken while a network cut was being produced.

I agree this is strange and is driving me nuts, everything seems to be ok but it keeps dropping down the connections.

This computer is running with Transmission, NX Client, Spotify, Firefox, Chrome and Chromium at the same time. When I plug the usb stick (which has less quality signal) works without interruptions, its only when I activate the Ralink when connections are dropped. Exactly, when one of this cut downs occurs, Spotify stops sounding, transmission stops sending and receiving, cannot navigate (¡¡even in the lan!! this is strange!) and have to wait until suddenly everything starts working again.

Thx!

---

### Post by chili555 on 2011-08-02
> supplicant connection state:  completed -> disconnectedIf you Google this phrase, you will see that it's a well-documented complaint. Apparently, it's a result of Network Manager re-scanning for available networks. Ordinarily, that's perfectly fine for a laptop that strolls down to the coffee shop or university and needs to look around for available networks. It's not so good for a desktop that is churning away on Transmission, NX Client, Spotify, Firefox, Chrome and Chromium at the same time. I wonder if it would help to instruct NM that we want one ESSID only by specifying the ESSID, address, etc. Please see attached.

If you decide to set a static IP, be sure it's outside the DHCP range used by the router. Post back with your results.

Actually, on a stay-at-home desktop machine, I'd ditch NM altogether.

---

### Post by Luponiano on 2011-08-03
Hello, I tried a fixed ip outside the dhcp range but still intermitent connections. 

I googled a little and found some people used wicd instead of NetworkManager. So I did unistall NM (Seems to conflict with wicd)
```
sudo apt-get purge network-manager network-manager-gnome
```

And installed Wicd via Software Center.
I have been connected without interruptions, so its clear is a NM problem. 

I saw another possible solution in this post:
```
http://ubuntuforums.org/showthread.php?p=10839430&posted=1#post10839430
```

Which suggest to update the kernel. I have not tried it because I do not know which consecuences it can have, Do you think I should try? Is it safe?

---

### Post by chili555 on 2011-08-03
> Which suggest to update the kernel. I have not tried it because I do not know which consecuences it can have, Do you think I should try? Is it safe?I think it's probably safe. The reason 2.6.39 hasn't been pushed out to Update Manager is unknown to me. It may have a glitch or two that's being worked on, but that glitch may or may not affect you. Frankly, if Wicd is working for you as expected, I wouldn't do anything more.

As our systems do more for us, there are more layers of complexity, the driver, wpa_supplicant, Network Manager and many more below that. Since no software is perfect, occasionally, systems that ought to work perfectly, don't.

---

### Post by Luponiano on 2011-08-03
You are pretty right. Complexity makes hard to be free of bugs.

I will let my configuration stand as it is now so it is working.

When the new kernel becames available officialy I will test if NM works without problems. Until then, I will enjoy my stable connection and ubuntu again.

Thank you for your help!

---

### Post by dlcurry on 2011-08-09
I have a 64-bit 11.04 box, followed the instructions on 6/13/11 to get the wifi working (N115, but still worked).  Been a while since I've turned the system on, so I, like a good little geek, ran update manager.  Now, no wifi.  I mean, the system doesn't even show I have a driver anymore.   Since that horrid moment, I've enabled proposed pkgs, double checked the .dat file, scanned the msg board threads (again!) and rebooted MANY times, all with no joy.  Anyone else had this happen?  Fixes???  Failing that, any idea what in the update (56 days' worth (ahem)) broke my system, and how to un-do?  FYSA- $ lspci -nn 02:06.0 Network controller [0280]: Ralink corp. Device [1814:3060]  $ iwconfig lo        no wireless extensions.  eth0      no wireless extensions.  TIA, Dave

---

### Post by ratcheer on 2011-08-09
dlcurry, if the updates included a revised Linux kernel and you had installed a different driver, you will have to reinstall your driver.
 
Tim

---

### Post by EriktheAwful on 2011-08-27
> you will have to reinstall your driver.
I've been screwing up my wireless about once a month. Each time I've had to string Cat5 across the floor, navigate to this board, and re-follow chili's instructions. Last time I dumped the driver files in an easy-to-navigate to folder so I can find them quickly in terminal. This time I made a text file titled "Repairing Wireless" that has a list of the commands.

Sooner or later I'll learn to stop tinkering and leave it alone.

---

### Post by chili555 on 2011-08-27
Did you know you can print my instructions to a .pdf file and keep them in the same folder? Please see attached.

---

### Post by mechanizedmedic on 2011-08-30
> **EriktheAwful said:**
> 
Sooner or later I'll learn to stop tinkering and leave it alone.


I know I won't stop tinkering so I try to make the consequences less time consuming. I pasted together this script to make the initial install a one command deal. It includes the commands for restoring after a kernel upgrade in the opening comments.

```
#!/bin/sh
## This script is intended to be run on a clean Ubuntu install after initial updates
#
## To fix wireless connectivity after a kernel update run the commands below
#
## cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
## sudo su
## make clean
## make
## make install
## modprobe rt3562sta
## exit
##


# Script must run as root
script_name="ralink3062.sh"

if [ $(id -u) -ne 0 ]; then
        echo "You need to run this script as root."
        echo "Use 'sudo ./$script_name' then enter your password when prompted."
        exit 1
fi

#check for internet connection, abort if not connected or continue.
wget -q --tries=10 --timeout=5 http://www.google.com -O /tmp/index.google &> /dev/null

if [ ! -s /tmp/index.google ];

then 	echo "internet connection not detected... ABORTING...";
	exit 1

else 	echo "internet connetion detected"
	rm /tmp/index.google

#modify modprobe blacklist
sed '$a\
blacklist rt2800pci\n
blacklist rt2800lib\n
blacklist rt2x00pci\n
blacklist rt2x00lib\n' /etc/modprobe.d/blacklist.conf

#install dependancies
apt-get install build-essential linux-headers-generic

#download and extract archive
wget -r http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D -O DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz
tar zxf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz

#edit make file
#DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk

sed -i 's/HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/g' DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk
sed -i 's/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/g' DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk

#compile
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
make
make install
echo rt3562sta >> /etc/modules

fi

echo " "
echo "INSTALLATION COMPLETE... DISCONNECT ETHERNET CABLE AND RESTART YOUR COMPUTER" 
```

---

### Post by Midnitte on 2011-08-30
> **MooPi said:**
> This is the procedure I used to install the driver for my new Rosewill Rosewill RNX-N150PC PCI 2.2 Wireless Adapter. It uses the Ralink 3060 chip. I'm using Lucid 10.04 and WICD as my network manager.(I have tested this driver and method on both 10.10 & currently 11.04 with success) I downloaded the drivers from Ralinks site
[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D")

Make sure you have installed gcc build-essential ```
sudo apt-get install gcc build-essential
```
I then followed the instuctions in the README file.
Navigate to downloaded_driver_folder/os/linux and open config.mk in a text editor.
Find and set so that it indicates ( y ) at the end of this text string```
[COLOR="blue"]HAS_WPA_SUPPLICANT=y[/COLOR]
```

and also set ```
[COLOR="blue"]HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y[/COLOR]
```
 
 Next, open a terminal in the driver folder and type ```
sudo make
```
 then ```
sudo make install
```
 
 
 Now you'll need to load the driver
 ```
sudo modprobe rt3562sta
```
 ```
sudo ifconfig ra0 inet up
```
 
 
 After I successfully connected I added the driver to /etc/modules so it it would load at startup. This is a copy of mine
 
```
 # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rt3562sta.ko
```

Edit complete save file and reboot to test. I hope this helps anyone using Raklink 3060/3062/3562 chipset. Mine connects with a strong consistent signal.

Looks as if an addition is necessary to complete the driver install. The need to blacklist a default driver to enable the new driver. 
From terminal
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Add this to the end of that file
```
blacklist rt2800pci
```

Tried doing this in 11.04, unfortauntly when i get to "sudo ifconfig ra0 inet up" it reports "SIOCSIFFLAGS: Operation not permitted"

Any help for this?

*also, under lspci is shows up as "01:00.0 Unclassified device (0080): Ralink corp. Device 3060

apparently "sudo service networking restart should fix this but it doesnt, and ra0 doesnt show up under ifconfig, but it does show up under iwconfig.

---

### Post by Midnitte on 2011-08-31
bump? D:

---

### Post by mechanizedmedic on 2011-09-03
> **Midnitte said:**
> Tried doing this in 11.04, unfortauntly when i get to "sudo ifconfig ra0 inet up" it reports "SIOCSIFFLAGS: Operation not permitted"

Any help for this?

*also, under lspci is shows up as "01:00.0 Unclassified device (0080): Ralink corp. Device 3060

apparently "sudo service networking restart should fix this but it doesnt, and ra0 doesnt show up under ifconfig, but it does show up under iwconfig.

post output of these commands and we'll see where you're at.

```
lsmod
sudo lshw -C network
iwconfig

```

---

### Post by Midnitte on 2011-09-04
```
midnitte@Midnitte-HTPC:~$ lsmod
Module                  Size  Used by
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  208 
aes_generic            38279  1 aes_x86_64
dm_crypt               22993  1 
vesafb                 13761  1 
snd_hda_codec_realtek   336771  1 
binfmt_misc            17565  1 
nvidia               8107272  34 
snd_hda_intel          33176  0 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
l2cap                  53570  16 rfcomm,bnep
snd_seq_midi_event     14899  1 snd_seq_midi
ppdev                  17113  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18600  2 
snd                    67382  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
parport_pc             36959  1 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
[COLOR="MediumTurquoise"]rt3562sta             986681  0 [/COLOR]
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
floppy                 74120  0 
ahci                   25951  2 
crc_itu_t              12707  1 firewire_core
r8169                  48022  0 
pata_amd               14130  0 
libahci                26642  1 ahci

midnitte@Midnitte-HTPC:~$ sudo lshw -C network
  *-generic DISABLED      
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: ra0
       version: 00
       serial: 00:1a:ff:ff:ff:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:efb00000-efb0ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:01:2e:24:06:5b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.137.74 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:de00(size=256) memory:efdff000-efdfffff memory:efc00000-efc1ffff
midnitte@Midnitte-HTPC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```  sorry for the delay =p

---

### Post by mechanizedmedic on 2011-09-04
> **Midnitte said:**
> ```
midnitte@Midnitte-HTPC:~$ sudo lshw -C network
  **[COLOR="Red"]*-generic DISABLED[/COLOR]**      
       description: Wireless interface
.......

```  
sorry for the delay =p

looks like your card is disabled, friend. i know you tried something similar BUT it's worth it to do the simple "up" command first. so...

```
sudo ifup ra0
sudo lshw -C network
```

if you get an error OR if the second command still shows your card "DISABLED" post the output of these two beauties.

```
rfkill list
dmesg | tail 

```

---

### Post by Midnitte on 2011-09-05
```
midnitte@Midnitte-HTPC:~$ sudo ifup ra0
[sudo] password for midnitte: 
Ignoring unknown interface ra0=ra0.
midnitte@Midnitte-HTPC:~$ sudo lshw -C network
  *-generic DISABLED      
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: ra0
       version: 00
       serial: 00:1a:ff:ff:ff:ff
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.1.1 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:efb00000-efb0ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:01:2e:24:06:5b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.137.63 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:de00(size=256) memory:efdff000-efdfffff memory:efc00000-efc1ffff
midnitte@Midnitte-HTPC:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
midnitte@Midnitte-HTPC:~$ dmesg | tail
[   20.225090] fb0: VESA VGA frame buffer device
[   20.500845] Intel AES-NI instructions are not detected.
[   20.551695] padlock_aes: VIA PadLock not detected.
[   20.599553] padlock_sha: VIA PadLock Hash Engine not detected.
[   21.765717] Adding 913404k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:913404k 
[   25.228234] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   29.270009] eth0: no IPv6 routers present
[   54.066012] ecryptfs_parse_options: eCryptfs: unrecognized option [ecryptfs_check_dev_ruid]
[  755.790649] r8169 0000:04:00.0: eth0: link down
[  758.033665] r8169 0000:04:00.0: eth0: link up
``` Any chance the Bluetooth might be a problem?

---

### Post by mechanizedmedic on 2011-09-05
> **Midnitte said:**
> Any chance the Bluetooth might be a problem?

i don't have any experience with bluetooth so i can't say either way.

i was a little hasty before and forgot to start at the beginning. make sure your ethernet cable is disconnected from the computer when you're trying to connect with wireless. wired connections "bump" wireless ones. if you've had the computer wired up this whole time that *could* be your problem. if so, unplug and restart.

also, i made the mistake #-o of not having you try to disable eth0 before enabling ra0. let's have a proper go with that.

```
sudo ifconfig eth0 down
sudo ifconfig ra0 up
dhclient
sudo ifconfig

```

if no luck, post back with these.

```
modinfo rt3562sta
cat /etc/network/interfaces
```

oh, and have a happy labor day!

---

### Post by Midnitte on 2011-09-09
no dice:
```
 midnitte@Midnitte-HTPC:~$ modinfo rt3562sta
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/rt3562sta.ko
version:        2.4.1.1
srcversion:     4D386FD1EDC7B95F07E2F57
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
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
depends:        
vermagic:       2.6.38-11-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
midnitte@Midnitte-HTPC:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

thanks for the fast response, sorry its been taking me so long, was at school =p

---

### Post by mechanizedmedic on 2011-09-10
> **Midnitte said:**
> 
thanks for the fast response, sorry its been taking me so long, was at school =p

well, i'm out of ideas. i've googled the crap out of this and can't seem to find anything close with a relevant solution.

if i were you [famous last words] i'd try putting the card into another PC to rule out the card as the issue. you can also put the card in another pci slot just to double check. i've had to return plenty of defective hardware over the years so you never know... 

if the card works with another pc you should start a new thread to address your problem specifically. to speed things up post the output of these in your thread or link to your posts in this one.

```
sudo lshw -C network
sudo lsmod
sudo ifconfig
rfkill list
dmesg | tail
```

take luck!

---

### Post by wildmanne39 on 2011-09-10
Hi, have a look at this link it may fix your problem.
[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)
Thank you

---

### Post by Midnitte on 2011-09-10
> **wildmanne39 said:**
> Hi, have a look at this link it may fix your problem.
[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)
Thank you

Sorry, thanks for the link but no dice, still getting operation not permitted.

Under lspci -v the devices is listed as "Unclassified device [0080]: Ralink corp. Device 3060", could this be part of the problem? (since it isnt being recognized as a network controller?)

---

### Post by ratcheer on 2011-09-11
> **Midnitte said:**
> Sorry, thanks for the link but no dice, still getting operation not permitted.

Under lspci -v the devices is listed as "Unclassified device [0080]: Ralink corp. Device 3060", could this be part of the problem? (since it isnt being recognized as a network controller?)

Yes, that would seem to be a problem. Try searching "Unclassified device [0080]" on Google.

Tim

---

### Post by wildmanne39 on 2011-09-11
Hi, where are you getting that message from?

The driver compiled completely correct?

Is that the complete error message or does it say something about the rfkill?

Please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nn | grep -e 0280 -e 0200 
```
```
rfkill list all
```
```
dmesg | egrep 'rt3|firm'
```
```
lsmod | grep rt3
```
Thank you

---

### Post by ratcheer on 2011-09-11
Have you downloaded and installed the latest ***firmware*** from Ralink? Maybe that would help Linux detect it properly.

Tim

---

### Post by Midnitte on 2011-09-11
> **wildmanne39 said:**
> Hi, where are you getting that message from?

The driver compiled completely correct?

Is that the complete error message or does it say something about the rfkill?

Please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nn | grep -e 0280 -e 0200 
```
```
rfkill list all
```
```
dmesg | egrep 'rt3|firm'
```
```
lsmod | grep rt3
```
Thank you

```
ubuntu 11.04 :p
04:00.0 Ethernet controller [0200]: Ralink semiconductor co. , ltd. rtl8111/81688 pci express gigabit ethernet controller [10sec:8168] (rev 01)
0: hci0: Bluetooth
   soft blocked: no
   hard blocked: no
[   14.101346] rt3562sta: module license 'unspecified' taints kernel.
rt3562sta                986681   0
```
I didnt try messing with the firmware becuase i wasnt sure what to do with it, I also tried switching the pci slot but no change in lspci -v

installing new firmware now
```
[14.981064] rt3562sta....
```

---

### Post by wildmanne39 on 2011-09-11
Hi, have a look at this link post 6.
[http://ubuntuforums.org/showthread.php?t=1490123](http://ubuntuforums.org/showthread.php?t=1490123)
Thank you

---

### Post by Midnitte on 2011-09-11
> **wildmanne39 said:**
> Hi, have a look at this link post 6.
[http://ubuntuforums.org/showthread.php?t=1490123](http://ubuntuforums.org/showthread.php?t=1490123)
Thank you

Ah no dice, perhaps I should just start over and see if that works, or as you said try another computer or even in windows.

---

### Post by wildmanne39 on 2011-09-12
Hi, did you run all the commands in post 83 because there was not much information posted?

I never said to reinstall or go back to windows.

Was this card working before you installed ubuntu?
Thank you

---

### Post by Midnitte on 2011-09-12
> **Midnitte said:**
> ```
ubuntu 11.04 :p
04:00.0 Ethernet controller [0200]: Ralink semiconductor co. , ltd. rtl8111/81688 pci express gigabit ethernet controller [10sec:8168] (rev 01)
0: hci0: Bluetooth
   soft blocked: no
   hard blocked: no
[   14.101346] rt3562sta: module license 'unspecified' taints kernel.
rt3562sta                986681   0
```
I didnt try messing with the firmware becuase i wasnt sure what to do with it, I also tried switching the pci slot but no change in lspci -v

installing new firmware now
```
[14.981064] rt3562sta....
```

I just didnt type all the info (like for cat /etc/lsb-release; uname -a), I haven't tried it in windows or another computer yet, but was going to give it a try (once i find some install CDs =p)
(also, wont be back to my pc till thursday =p)

---

### Post by Despotism on 2011-09-24
> **Midnitte said:**
> Issues

Midnitte - I had issues with the 3062 chipset with the "Zonet ZEW1690 Wireless Adapter" card.

To make things worse, I have only been using Ubuntu and Linux for about two weeks, but I got this working for Ubuntu 11.04 and with the Minimal CD, using xfce4 as my desktop.

Post #1 by MooPi on this thread are the exact instructions I followed.. However there was a small different in the prep-work.

I downloaded - [This]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D") - AND - [This]("http://www.ralinktech.com/license_us.php?n=2&p=1&t=U0wyRnpjMlYwY3k4eU1ERXdMekF6THpNeEwyUnZkMjVzYjJGa01UWTBNamsyTVRBNE1pNTZhWEE5UFQxU1ZESTROakJmUm1seWJYZGhjbVZmVmpJMkM%3D")

The firmware file, unziped.

$ sudo cp rt2860.bin /lib/firmware/rt2860.bin

Follow Post#1 to the letter.

Lastly because I did it with Minimal CD and xfce Desktop.
I installed Network-Manager

$ sudo aptitude install network-manager-gnome

(yeah I wanted the graphical interface and I like gnomes manager more - Reminds me more like Windows 8-[)

Rebooted, connected Wireless first time.

I will say that with the minimal cd and Xfce there is not much loaded so I did load up some stuff. Nautilus, the extra columns for mp3, a Metadata editor, xfce tools (kinda all the normal stuff you would use) XBMC, Nvidia Drivers, and RapidRAID 640 Controller drivers, there was a couple of extras like Firefox etc, but it's pretty bear install. It's possible sometime I installed helps but that is what I did for my card to work.

Edit:-
The instructional I followed was actually not the post in this thread, I had stumbled across this first.
[http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/]("http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/")
But the instructions are somewhat the same, apart form the Firmware file, as well the NetworkManager needing to be installed for it to work.

---

### Post by uconnjl on 2011-11-05
> **Despotism said:**
> Midnitte - I had issues with the 3062 chipset with the "Zonet ZEW1690 Wireless Adapter" card.

To make things worse, I have only been using Ubuntu and Linux for about two weeks, but I got this working for Ubuntu 11.04 and with the Minimal CD, using xfce4 as my desktop.

Post #1 by MooPi on this thread are the exact instructions I followed.. However there was a small different in the prep-work.

I downloaded - [This]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D") - AND - [This]("http://www.ralinktech.com/license_us.php?n=2&p=1&t=U0wyRnpjMlYwY3k4eU1ERXdMekF6THpNeEwyUnZkMjVzYjJGa01UWTBNamsyTVRBNE1pNTZhWEE5UFQxU1ZESTROakJmUm1seWJYZGhjbVZmVmpJMkM%3D")

The firmware file, unziped.

$ sudo cp rt2860.bin /lib/firmware/rt2860.bin

Follow Post#1 to the letter.

Lastly because I did it with Minimal CD and xfce Desktop.
I installed Network-Manager

$ sudo aptitude install network-manager-gnome

(yeah I wanted the graphical interface and I like gnomes manager more - Reminds me more like Windows 8-[)

Rebooted, connected Wireless first time.

I will say that with the minimal cd and Xfce there is not much loaded so I did load up some stuff. Nautilus, the extra columns for mp3, a Metadata editor, xfce tools (kinda all the normal stuff you would use) XBMC, Nvidia Drivers, and RapidRAID 640 Controller drivers, there was a couple of extras like Firefox etc, but it's pretty bear install. It's possible sometime I installed helps but that is what I did for my card to work.

Edit:-
The instructional I followed was actually not the post in this thread, I had stumbled across this first.
[http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/]("http://www.hyperborea.org/journal/2010/08/wifi-ralink-3062/")
But the instructions are somewhat the same, apart form the Firmware file, as well the NetworkManager needing to be installed for it to work.

Works on 11.10 too!!

---

### Post by timothysrooney on 2011-11-13
I have tried all of what has been suggested in the above posts. I am not having luck getting my Rosewill RNX-N150PC wireless working. Can someone tell me what I've done wrong? What can I do to fix this problem? Here's the output I get from my attempts. Can someone help? Thanks! 

Finally, if you need me to provide more information, also let me know what you need to see, and I can provide those details as well. Thanks!

[COLOR="Red"]tsr@TimothySRooney:~$ cd Downloads/Ralink/ 
tsr@TimothySRooney:~/Downloads/Ralink$ ls[/COLOR] 
2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0          DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217      rnx-n150pc_linux_2.6.3x.zip 
2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0.tar.bz2  DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz 
[COLOR="Red"]tsr@TimothySRooney:~/Downloads/Ralink$ cd 2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/ [/COLOR]
[COLOR="red"]tsr@TimothySRooney:~/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0$ ls [/COLOR]
chips   include           LICENSE ralink-firmware.txt  os          RT2860STACard.dat  sta                       tools 
common  iwpriv_usage.txt  Makefile                     README_STA  RT2860STA.dat      sta_ate_iwpriv_usage.txt 
[COLOR="red"]tsr@TimothySRooney:~/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0$ make [/COLOR]
make -C tools 
make[1]: Entering directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools' 
gcc -g bin2h.c -o bin2h 
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools' 
/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools/bin2h 
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux/Makefile 
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux modules 
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build' 
make[1]: *** No rule to make target `modules'.  Stop. 
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build' 
make: *** [LINUX] Error 2 
[COLOR="red"]tsr@TimothySRooney:~/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0$ make install [/COLOR]
make -C /home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux -f Makefile.6 install 
mkdir: cannot create directory `/etc/Wireless': File exists 
make[1]: Entering directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux' 
rm -rf /etc/Wireless/RT2860STA 
rm: cannot remove `/etc/Wireless/RT2860STA/RT2860STA.dat': Permission denied 
make[1]: *** [install] Error 1 
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux' 
make: *** [install] Error 2 
[COLOR="red"]tsr@TimothySRooney:~/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0$ sudo make [/COLOR]
[sudo] password for tsr: 
make -C tools 
make[1]: Entering directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools' 
gcc -g bin2h.c -o bin2h 
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools' 
/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools/bin2h 
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux/Makefile 
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux modules 
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build' 
make[1]: *** No rule to make target `modules'.  Stop. 
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build' 
make: *** [LINUX] Error 2 
[COLOR="red"]tsr@TimothySRooney:~/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0$ sudo make install [/COLOR]
make -C /home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux -f Makefile.6 install 
mkdir: cannot create directory `/etc/Wireless': File exists 
make[1]: Entering directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux' 
rm -rf /etc/Wireless/RT2860STA 
mkdir /etc/Wireless/RT2860STA 
cp /home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/RT2860STA.dat /etc/Wireless/RT2860STA/. 
install -d /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/ 
install -m 644 -c rt3562sta.ko /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/ 
install: cannot stat `rt3562sta.ko': No such file or directory 
make[1]: *** [install] Error 1 
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux' 
make: *** [install] Error 2 
tsr@TimothySRooney:~/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0$

More information? 

For my Makefile, I have this stuff

T28xx_MODE=STA
TARGET=LINUX
CHIPSET=3562

PLATFORM=PC

ifeq ($(PLATFORM),PC)
LINUX_SRC=/lib/modules/$(shell uname -r)/build
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
CROSS_COMPILE=
endif

Did I need to change something in the above? Something in the Makefile.4 or the Makefile.6?

Next, I noticed some of the hints were to just copy the bin file. Where is that? I cannot seem to find that? Is this something made when the make is done correctly instead of the errors I get? Again, if I don't provide enough information, tell me what other details will help in solving this problem. Thanks!!!

So I downloaded the rt2860.bin from the website (links provided by the above post, thanks!) I got the file, copied it to my desktop (PC that's having the problems), and found that the directory where I needed to copy the file (/lib/firmware/) already had a copy of that file. So if the rt2860.bin is already in place, the above post doesn't help me either. What next? Where can I go from here?

So I'm just going to keep adding stuff! Maybe somebody can help me with all the details here!

[COLOR="red"]tsr@TimothySRooney:~$ cat /etc/lsb-release; uname -a [/COLOR]
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.10 
DISTRIB_CODENAME=oneiric 
DISTRIB_DESCRIPTION="Ubuntu 11.10" 
Linux TimothySRooney 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 athlon i386 GNU/Linux 
[COLOR="red"]tsr@TimothySRooney:~$ lspci -nn | grep -e 0280 -e 0200 [/COLOR]
01:07.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060] 
[COLOR="red"]tsr@TimothySRooney:~$ rfkill list all [/COLOR]
[COLOR="red"]tsr@TimothySRooney:~$ dmesg | egrep 'rt3|firm' [/COLOR]
[   10.789000] rt3562sta: disagrees about version of symbol module_layout 
[   10.789026] rt3562sta: disagrees about version of symbol module_layout 
[   10.790371] rt3562sta: disagrees about version of symbol module_layout 
[   10.791605] rt3562sta: disagrees about version of symbol module_layout 
[   10.792832] rt3562sta: disagrees about version of symbol module_layout 
[   10.794052] rt3562sta: disagrees about version of symbol module_layout 
[   10.795261] rt3562sta: disagrees about version of symbol module_layout 
[   10.796491] rt3562sta: disagrees about version of symbol module_layout 
[   10.798266] rt3562sta: disagrees about version of symbol module_layout 
[   10.799492] rt3562sta: disagrees about version of symbol module_layout 
[COLOR="red"]tsr@TimothySRooney:~$ lsmod | grep rt3 [/COLOR]
tsr@TimothySRooney:~$

Okay, here's more stuff as responses from earlier posts that asked other people for more information.

[COLOR="Red"]tsr@TimothySRooney:~$ lsmod [/COLOR]
Module                  Size  Used by 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_via      61329  1 
binfmt_misc            17292  1 
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi 
joydev                 17393  0 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
psmouse                63474  0 
serio_raw              12990  0 
radeon                961723  3 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
ttm                    65224  1 radeon 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
drm_kms_helper         32889  1 radeon 
asus_atk0110           17742  0 
drm                   196322  5 radeon,ttm,drm_kms_helper 
parport_pc             32114  1 
i2c_algo_bit           13199  1 radeon 
snd_timer              28932  2 snd_seq,snd_pcm 
k10temp                12990  0 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_via,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer 
soundcore              12600  1 snd 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp 
usbhid                 41905  0 
hid                    77367  1 usbhid 
usb_storage            44173  0 
uas                    17699  0 
pata_amd               13753  0 
sata_nv                23379  2 
forcedeth              58103  0 
[COLOR="red"]tsr@TimothySRooney:~$ sudo lshw -C network [/COLOR]
[sudo] password for tsr: 
  *-network UNCLAIMED     
       description: Network controller 
       product: RT3060 Wireless 802.11n 1T/1R 
       vendor: Ralink corp. 
       physical id: 7 
       bus info: pci@0000:01:07.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list 
       configuration: latency=64 maxlatency=4 mingnt=2 
       resources: memory:dfef0000-dfefffff 
[COLOR="red"]tsr@TimothySRooney:~$ iwconfig [/COLOR]
lo        no wireless extensions. 

eth0      no wireless extensions. 

tsr@TimothySRooney:~$

---

### Post by chili555 on 2011-11-14
> make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2 When 'make' errors out, you might as well stop; all further steps will be errors as well. If trhe module builds at all, it won't work.

First, it doesn't look like the necessary build tools and linux headers are installed. Second, I doubt a package built in January 2010 is going to compile correctly against a 3.0 kernel. Finally, the module rt2800pci is designed to drive your device. Did you try it?```
sudo modprobe rt2800pci
iwconfig
sudo iwlist wlan0 scan
```

---

### Post by ratcheer on 2011-11-14
@chili555, rt2800pci does not work well or at all with this hardware. I have to use the driver from Ralink to get it to work on my system. There are several threads where I have helped people get their Ralink wlan going by installing a driver that works.

Yes, I know rt2800pci is *supposed* to work, but it doesn't.

Tim

---

### Post by timothysrooney on 2011-11-14
Thank you for a response! I typed what you suggested. (I also appreciate the explanation for what to expect so that I know what I was trying wouldn't work!) What did I get? Here's what the PC is telling me. 

[COLOR="Red"]tsr@TimothySRooney:~$ sudo modprobe rt2800pci [/COLOR]
[COLOR="red"][sudo] password for tsr: 
tsr@TimothySRooney:~$ iwconfig 
[/COLOR]lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID : off/any  
          Mode:Managed  Access Point : Not-Associated   Tx-Power=20 dBm   
          Retry  long limit : 7   RTS thr : off   Fragment thr : off 
          Power Management : off 
          
[COLOR="red"]tsr@TimothySRooney : ~ $ sudo iwlist wlan0 scan [/COLOR]
wlan0     No scan results 

tsr@TimothySRooney : ~ $

Note, I added some spaces in there because the characters were being turned into smiley faces. Just ignore inserted spaces where there should be none. It's just to stop smiley faces from appearing.

Finally, I did all the above steps. I rebooted. (Wireless mouse stopped responding with the USB drive switching. I hoped the reboot would get wireless network functioning after I'd executed your suggested commands. No luck there so my wireless network still doesn't function. But maybe the output will help me find some other solution? That someone can suggest? Please!!!)

---

### Post by chili555 on 2011-11-14
> **ratcheer said:**
> @chili555, rt2800pci does not work well or at all with this hardware. I have to use the driver from Ralink to get it to work on my system. There are several threads where I have helped people get their Ralink wlan going by installing a driver that works.

Yes, I know rt2800pci is *supposed* to work, but it doesn't.

TimI understood that it and the firmware was improved in 11.10. Have you tried it?

---

### Post by chili555 on 2011-11-14
> **timothysrooney said:**
> Thank you for a response! I typed what you suggested. (I also appreciate the explanation for what to expect so that I know what I was trying wouldn't work!) What did I get? Here's what the PC is telling me. 

[COLOR="Red"]tsr@TimothySRooney:~$ sudo modprobe rt2800pci [/COLOR]
[COLOR="red"][sudo] password for tsr: 
tsr@TimothySRooney:~$ iwconfig 
[/COLOR]lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID : off/any  
          Mode:Managed  Access Point : Not-Associated   Tx-Power=20 dBm   
          Retry  long limit : 7   RTS thr : off   Fragment thr : off 
          Power Management : off 
          
[COLOR="red"]tsr@TimothySRooney : ~ $ sudo iwlist wlan0 scan [/COLOR]
wlan0     No scan results 

tsr@TimothySRooney : ~ $

Note, I added some spaces in there because the characters were being turned into smiley faces. Just ignore inserted spaces where there should be none. It's just to stop smiley faces from appearing.

Finally, I did all the above steps. I rebooted. (Wireless mouse stopped responding with the USB drive switching. I hoped the reboot would get wireless network functioning after I'd executed your suggested commands. No luck there so my wireless network still doesn't function. But maybe the output will help me find some other solution? That someone can suggest? Please!!!)Please do:```
sudo modprobe rt2800pci
dmesg | grep rt2
```Please post the result.

---

### Post by timothysrooney on 2011-11-14
> **chili555 said:**
> I understood that it and the firmware was improved in 11.10. Have you tried it?

Have I tried it? I'm not sure! How can I try it? What must I do to try the improved firmware? Also, Here's some of the contents of my /etc/modprobe.d/blacklist.conf

blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib

Not that this matters (maybe it does), but it should show that I've tried to follow the instructions for other suggested solutions!

---

### Post by timothysrooney on 2011-11-14
> **chili555 said:**
> Please do:```
sudo modprobe rt2800pci
dmesg | grep rt2
```Please post the result.

Here are those results...

[COLOR="Red"]tsr@TimothySRooney:~$ sudo modprobe rt2800pci [/COLOR]
[COLOR="red"][sudo] password for tsr: 
tsr@TimothySRooney:~$ dmesg | grep rt2 
[/COLOR][ 1865.451731] rt2800pci 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17 
[ 1865.489412] Registered led device: rt2800pci-phy0::radio 
[ 1865.489424] Registered led device: rt2800pci-phy0::assoc 
[ 1865.489435] Registered led device: rt2800pci-phy0::quality 
tsr@TimothySRooney:~$

Looking at other posts earlier in the discussion, I'll also provide these results, just in case that will help.

[COLOR="Red"]sudo modprobe rt3562sta[/COLOR]
FATAL: Error inserting rt3562sta (/lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/rt3562sta.ko): Invalid module format

---

### Post by chili555 on 2011-11-14
> Have I tried it? I'm not sure! How can I try it?My comment was directed at ratcheer, not you.

Now let's see:```
dmesg | grep wlan
ls -al /lib/firmware/rt2860.bin
md5sum /lib/firmware/rt2860.bin
```We hope we see:> $ md5sum /lib/firmware/rt2860.bin
[COLOR="Red"]75a1da3caa0b1c95e81dfba207f834c6[/COLOR]  /lib/firmware/rt2860.binThanks.

---

### Post by timothysrooney on 2011-11-14
I'm getting closer! I can see the wireless network now. I'm trying to connect, but it's taking a while... 

Our wireless network sometimes does not cooperate. Maybe if I reset that?

---

### Post by timothysrooney on 2011-11-14
> **chili555 said:**
> My comment was directed at ratcheer, not you.

Now let's see:```
dmesg | grep wlan
ls -al /lib/firmware/rt2860.bin
md5sum /lib/firmware/rt2860.bin
```We hope we see:Thanks.

Here are several replies, all combined right here.

Your comment to ratcheer? Got it! Sorry I misunderstood. 

Next, 

[COLOR="Red"]tsr@TimothySRooney:~$ dmesg | grep wlan 
tsr@TimothySRooney:~$ ls -al /lib/firmware/rt2860.bin 
[/COLOR]-rw-r--r-- 1 root root 8192 2011-08-23 08:23 /lib/firmware/rt2860.bin 
[COLOR="red"]tsr@TimothySRooney:~$ md5sum /lib/firmware/rt2860.bin [/COLOR] 
75a1da3caa0b1c95e81dfba207f834c6  /lib/firmware/rt2860.bin 
tsr@TimothySRooney:~$ 

Finally, when I rebooted the PC, all the wireless stuff that had been enabled by one of my previous above steps has stopped! When I click the network windshield (I'm not sure the name of it, but it's in the Desktop bar--again, I'm probably using the wrong word, sorry, but it's essential the start menu bar), I now only have wired network. The wireless option that existed (and let me attempt to connect to my home wireless network) is now gone. Also, of course the Wired Network option is disabled. If I had a Wired Network available, I would be using that. Now there's nothing for Wireless Network.

---

### Post by chili555 on 2011-11-14
> Finally, when I rebooted the PC, all the wireless stuff that had been enabled by one of my previous above steps has stopped! Well, of course. We are attempting to use rt2800pci by manually loading it:```
sudo modprobe rt2800pci
```However, this module and its dependencies are blacklisted so they won't load on boot unless you do so manually. Please amend /etc/modprobe.d/blacklist.conf to remove these items:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Now reboot and you'll probably be all set.> I'm getting closer! I can see the wireless network now. I'm trying to connect, but it's taking a while... We are indeed getting close!

---

### Post by timothysrooney on 2011-11-14
So I went back and did the steps suggested in the instructions to me. That did get my Wireless Network to appear, and it even has the name of the wireless network. I'm getting very close!!

I try to connect. It doesn't find anything. I choose the Connect to Hidden Wireless Network, and Rooney does appear. But I don't think it should be a hidden wireless network. Next, I keep getting asked for the Password. I type that in, and it just keeps trying to connect. And then repeatedly asks me for the password. 

I'm so close!!! Just work, you pesky computer!!!

---

### Post by chili555 on 2011-11-14
What does this tell us?```
sudo iwlist wlan0 scan
iwconfig
```Thanks.

---

### Post by timothysrooney on 2011-11-14
> **chili555 said:**
> What does this tell us?```
sudo iwlist wlan0 scan
iwconfig
```Thanks.

Why won't this cooperate!?!?!! Here's what I get.

[COLOR="Red"]tsr@TimothySRooney:~$ sudo iwlist wlan0 scan [/COLOR]
[COLOR="red"][sudo] password for tsr: [/COLOR]
wlan0     No scan results 

[COLOR="red"]tsr@TimothySRooney:~$ iwconfig [/COLOR]
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID : off/any  
          Mode:Managed  Access Point : Not-Associated   Tx-Power=20 dBm   
          Retry  long limit : 7   RTS thr : off   Fragment thr : off 
          Power Management : off 
          
tsr@TimothySRooney : ~ $

And how can I turn off those smiley faces? (Note I've added spaces to turn the smiley faces back to normal characters.)

Also, some previous stuff you wanted me to type has changed. It now looks like this.

tsr@TimothySRooney:~$ sudo modprobe rt2800pci 
[sudo] password for tsr: 
tsr@TimothySRooney:~$ dmesg | grep rt2 
[   10.985677] rt2800pci 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18 
[   11.029721] Registered led device: rt2800pci-phy0::radio 
[   11.029734] Registered led device: rt2800pci-phy0::assoc 
[   11.029755] Registered led device: rt2800pci-phy0::quality 
[   11.388119] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware 
tsr@TimothySRooney:~$

I'm off to class. I'll be back around dinner time. Thus, I can't respond for a while. Any advice or suggestion while I am away is still great. Thanks!

---

### Post by ratcheer on 2011-11-14
> **chili555 said:**
> I understood that it and the firmware was improved in 11.10. Have you tried it?

Yes, and rt2800pci still would not work for me. Nor will r8169 work for my ethernet card. However, on Arch Linux with kernel 3.1.4, r8169 now works. I still have to use rt3562sta for my wireless card, though.

I will try to disappear from this thread. But I will keep an eye on it to see if he can get rt2800pci to work. I would really enjoy it if I could stop messing with these outside drivers.

Thanks,
Tim

---

### Post by chili555 on 2011-11-14
UNCLE!

Isn't that what we say when we've lost the battle and give up? I had high hopes for the revised and updated rt2x00 suite of drivers under kernel 3.0, but I have seen many problems and no successes. So, Uncle. Let's put the blacklists back in place and compile the driver from source. You have in your system:> tsr@TimothySRooney:~/Downloads/Ralink$ ls
2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0 [COLOR="Red"]DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217[/COLOR] rnx-n150pc_linux_2.6.3x.zip
2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0.tar.bz2 DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgzYou will need to install build tools and linux headers. With an ethernet connection, please do:```
sudo apt-get build-essential linux-headers-generic
```Next you need to use the newer version I've highlighted. Open DPO_RT.../os/linux/config.mk with a text editor. Change line 12 to read HAS_WPA_SUPPLICANT=y and change line 15 to read HAS_NATIVE_WPA_SUPPLICANT=y. Proofread, save and close the text editor. Now open a terminal and do:```
cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
sudo su
make
make install
modprobe rt3562sta
exit
```Now is it working?

---

### Post by timothysrooney on 2011-11-14
Chili555, thank you so much for another solution. I have a very busy evening ahead of me. I won't be able to move my PC around to get to the Ethernet connection until tomorrow evening. Because of this, don't expect more information until then. Thanks, though, for providing this solution. I hope it works! I'll keep you updated as I go through the process tomorrow. 

Thanks!!!

---

### Post by timothysrooney on 2011-11-15
So this is what I get...

[COLOR="Red"]tsr@TimothySRooney:~$ sudo apt-get build-essential linux-headers-generic
[sudo] password for tsr: [/COLOR]
E: Invalid operation build-essential
[COLOR="red"]tsr@TimothySRooney:~$ cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
tsr@TimothySRooney:~/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo su
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
[/COLOR]make -C tools
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2
[COLOR="red"]root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make install[/COLOR]
make -C /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `rt3562sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
make: *** [install] Error 2
[COLOR="Red"]root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# modprobe rt3562sta
[/COLOR]FATAL: Error inserting rt3562sta (/lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/rt3562sta.ko): Invalid module format
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217#

---

### Post by timothysrooney on 2011-11-15
But maybe if I try this instead...

sudo apt-get build-dep linux-headers-generic

---

### Post by timothysrooney on 2011-11-15
Nope! I get the same stuff again! Why did my wireless card work in the old Ubuntu? Hmmm... 

[COLOR="Red"]tsr@TimothySRooney:~$ sudo apt-get build-dep linux-headers-generic
[sudo] password for tsr: [/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux-meta' as source package instead of 'linux-headers-generic'
The following NEW packages will be installed:
  gawk libsigsegv2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 454 kB of archives.
After this operation, 1,376 kB of additional disk space will be used.
[COLOR="red"]Do you want to continue [Y/n]? Y[/COLOR]
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main libsigsegv2 i386 2.9-4ubuntu2 [14.4 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main gawk i386 1:3.1.8+dfsg-0.1build1 [439 kB]
Fetched 454 kB in 3s (129 kB/s)
Selecting previously deselected package libsigsegv2.
(Reading database ... 167291 files and directories currently installed.)
Unpacking libsigsegv2 (from .../libsigsegv2_2.9-4ubuntu2_i386.deb) ...
Setting up libsigsegv2 (2.9-4ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package gawk.
(Reading database ... 167299 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.8+dfsg-0.1build1_i386.deb) ...
Processing triggers for man-db ...
Setting up gawk (1:3.1.8+dfsg-0.1build1) ...
tsr@TimothySRooney:~$ ^C
[COLOR="red"]tsr@TimothySRooney:~$ sudo apt-get build-dep linux-headers-generic[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'linux-meta' as source package instead of 'linux-headers-generic'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[COLOR="red"]tsr@TimothySRooney:~$ cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
tsr@TimothySRooney:~/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo su
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make[/COLOR]
make -C tools
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2
[COLOR="red"]root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make install[/COLOR]
make -C /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/
install -m 644 -c rt3562sta.ko /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/
install: cannot stat `rt3562sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
make: *** [install] Error 2
[COLOR="red"]root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# modprobe rt3562sta
[/COLOR]FATAL: Error inserting rt3562sta (/lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/rt3562sta.ko): Invalid module format

---

### Post by chili555 on 2011-11-16
Sorry for the error. It is supposed to be:```
sudo apt-get **install** build-essential linux-headers-generic-**pae**
```Then proceed as previously.

Once again, when you see this:> make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2Please do exactly what it suggests: Stop. All further steps will be errors as well.

---

### Post by timothysrooney on 2011-11-16
Thanks, Chili! I figured I was done and out of solutions! Again, I've got to work today so I won't get to this until later this evening. I hope your new suggestion will work for me. Also, I'm sorry for continuing to try to retype the steps after I get an error. I am just holding out hope that something will work, despite the initial "make" not working. I'll keep this in mind tonight when I try things out. Thanks very much! I'll keep you updated when I have results to post.

---

### Post by chili555 on 2011-11-16
I will be looking forward to your (good) report.

---

### Post by timothysrooney on 2011-11-16
SSDD!! That's too bad, though. Any other ideas? If not, where can I find a list of compatible WiFi cards that'll work with Ubuntu 11.10 right off the shelf? Any advice if you have no other solutions? (UNless I did something wrong in my attempt here...)

[COLOR="Red"]tsr@TimothySRooney:~$ sudo apt-get install build-essential linux-headers-generic-pae
[sudo] password for tsr: 
[/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following NEW packages will be installed:
  linux-headers-3.0.0-12-generic-pae linux-headers-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 834 kB of archives.
After this operation, 10.9 MB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main linux-headers-3.0.0-12-generic-pae i386 3.0.0-12.20 [832 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main linux-headers-generic-pae i386 3.0.0.12.14 [2,364 B]
Fetched 834 kB in 5s (148 kB/s)                 
Selecting previously deselected package linux-headers-3.0.0-12-generic-pae.
(Reading database ... 167388 files and directories currently installed.)
Unpacking linux-headers-3.0.0-12-generic-pae (from .../linux-headers-3.0.0-12-generic-pae_3.0.0-12.20_i386.deb) ...
Selecting previously deselected package linux-headers-generic-pae.
Unpacking linux-headers-generic-pae (from .../linux-headers-generic-pae_3.0.0.12.14_i386.deb) ...
Setting up linux-headers-3.0.0-12-generic-pae (3.0.0-12.20) ...
Examining /etc/kernel/header_postinst.d.
Setting up linux-headers-generic-pae (3.0.0.12.14) ...
[COLOR="red"]tsr@TimothySRooney:~$ cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
tsr@TimothySRooney:~/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo su
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
[/COLOR]make -C tools
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217#

---

### Post by chili555 on 2011-11-16
Would you please try:```
cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt3562sta
exit
```As before, stop means stop. 

FWIW, I think this step, done *without* the proper headers, has tripped us up.> cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile

---

### Post by timothysrooney on 2011-11-16
Thanks for the quick response, Chili. Bad news, though... I think. Maybe you can make out what the problem is? Regardless, here's the output. 

[COLOR="Red"]tsr@TimothySRooney:~$ cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
tsr@TimothySRooney:~/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo su
[sudo] password for tsr: 
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make clean[/COLOR]
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{o,cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf os/linux/Makefile
[COLOR="red"]root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make[/COLOR]
make -C tools
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217#

---

### Post by chili555 on 2011-11-17
I actually awoke at oh-dark-thirty agonizing about your problem. I then installed a pae kernel on my machine to test. Here is your 'make':> make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: *Entering directory* '/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `**/lib/modules/3.0.0-12-generic-pae/build**'
make: *** [LINUX] Error 2And here is mine:> make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: *Entering directory* '**/usr/src/linux-headers-3.0.0-12-generic-pae**This makes me suspect that the correct headers are still not present in your system. Please try:```
sudo su
apt-get install --reinstall linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~. Now do:```
cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
make clean
make
make install
modprobe rt3562sta
exit
```The module builds and loads with warnings but no errors on my shiny new pae kernel.

---

### Post by ratcheer on 2011-11-17
Why is make going into `/lib/modules/3.0.0-12-**generic-pae**/build'? That doesn't sound right, to me.

Tim

---

### Post by chili555 on 2011-11-17
> **ratcheer said:**
> Why is make going into `/lib/modules/3.0.0-12-**generic-pae**/build'? That doesn't sound right, to me.

TimExactly! I think it should go into ..headers-pae.

---

### Post by timothysrooney on 2011-11-17
Here's what I've got... (And thanks, guys, for your very attentive efforts! It's great to have support/efforts to fix this problem! Kudos to you both.)



[COLOR="Red"]tsr@TimothySRooney:~$ sudo apt-get install build-essential linux-headers-generic-pae 
[/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic-pae is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[COLOR="red"]tsr@TimothySRooney:~$ sudo su
root@TimothySRooney:/home/tsr# apt-get install --reinstall linux-headers-`uname -r`
[/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/832 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 175489 files and directories currently installed.)
Preparing to replace linux-headers-3.0.0-12-generic-pae 3.0.0-12.20 (using .../linux-headers-3.0.0-12-generic-pae_3.0.0-12.20_i386.deb) ...
Unpacking replacement linux-headers-3.0.0-12-generic-pae ...
Setting up linux-headers-3.0.0-12-generic-pae (3.0.0-12.20) ...
Examining /etc/kernel/header_postinst.d.
[COLOR="Red"]root@TimothySRooney:/home/tsr# cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make clean
[/COLOR]cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{o,cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf os/linux/Makefile
[COLOR="Red"]root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make[/COLOR]
make -C tools
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217#

---

### Post by chili555 on 2011-11-17
Fascinating...and confounding. Please run:```
sudo dpkg -s build-essential | grep Status
```If it comes back as:> Status: install ok installedThen proceed with:```
cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
sudo su
make uninstall
make clean
make
make install
modprobe rt3562sta
exit
```If build-essential is not correctly installed, please do:```
sudo apt-get install --reinstall build-essential
```This just gets curiouser.

---

### Post by timothysrooney on 2011-11-17
Why does it hate me? I'm so nice to my computer! It shouldn't be difficult like this! At any rate, here's an answer to your commands/suggestions. It's not what I want to see... I don't think, at least! Maybe it'll help you? Regardless, here it is. 

[COLOR="Red"]tsr@TimothySRooney:~$ sudo dpkg -s build-essential | grep Status
[sudo] password for tsr: 
[/COLOR]
Status: install ok installed
[COLOR="Red"]tsr@TimothySRooney:~$ cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
tsr@TimothySRooney:~/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo su
root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make uninstall[/COLOR]
make -C /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux -f Makefile.6 uninstall
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/wireless/rt3562sta.ko
/sbin/depmod -a 3.0.0-12-generic-pae
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
[COLOR="red"]root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make clean[/COLOR]
cp -f os/linux/Makefile.6 os/linux/Makefile
make -C os/linux clean
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -f ../../common/*.o
rm -f ../../common/.*.{o,cmd,flags,d}
rm -f ../../os/linux/*.{o,ko,mod.{o,c}}
rm -f ../../os/linux/.*.{cmd,flags,d}
rm -fr ../../os/linux/.tmp_versions
rm -f ../../os/linux/Module.symvers
rm -f ../../os/linux/Module.markers
rm -f ../../os/linux/modules.order
rm -f ../../chips/*.o
rm -f ../../chips/.*.{cmd,flags,d}
rm -f ../../sta/*.o
rm -f ../../sta/.*.{cmd,flags,d}
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux'
rm -rf os/linux/Makefile
[COLOR="red"]root@TimothySRooney:/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
[/COLOR]make -C tools
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2

---

### Post by timothysrooney on 2011-11-18
Here's another question. This is just so I can try to understand what is going on with this whole process. Take a look at this output, please. 

[COLOR=Red]tsr@TimothySRooney:~/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0$ make[/COLOR] 
make -C tools
make[1]: Entering directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools'
/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0/os/linux modules
[COLOR=Lime]make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
[/COLOR]make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2
[COLOR=Red]tsr@TimothySRooney:~/Downloads/Ralink/2010_0115_RT3562_RT3062_Linux_STA_V2.3.0.0$ ls /lib/modules/3.0.0-12-generic/build
[/COLOR]arch    Documentation  fs       ipc      kernel    mm              samples   sound   ubuntu
block   drivers        include  Kbuild   lib       Module.symvers  scripts   source  usr
crypto  firmware       init     Kconfig  Makefile  net             security  tools   virt

My question is that the stuff in green indicates there's no rule to make the target module. So I went to the directory specified, and that is the last line I typed. The contents of the directory are listed above. Where is the rule to make the target module? Does that mean the directory listed there should have a make? There is certainly a Makefile. What does that Makefile contain? 

Taking a look at the Makefile, it's much too long to post here, but I can see roughly what is in that Makefile. What seems to be the problem? Do I have to type make in this directory to make the stuff specified by the Makefile? Or has that already been done? And any response/reply to my question is appreciated. And if it's too long, complicated, or dull to merit a response, that's also fine. I was just curious to learn more of what is happening with this error. Thanks!

---

### Post by ratcheer on 2011-11-18
I have another question. I apologize if I have already asked it before.

Why is your Ralink driver so old? The one I am using is version 2.4.1.1 dated 17-Dec-2010. Yours seems to be 2.3.0.0 dated 15-Jan-2010. I recommend downloading the latest driver directly from Ralink.

Also, please post the output of "uname -a".

Tim

---

### Post by timothysrooney on 2011-11-18
> **ratcheer said:**
> I have another question. I apologize if I have already asked it before.

Why is your Ralink driver so old? The one I am using is version 2.4.1.1 dated 17-Dec-2010. Yours seems to be 2.3.0.0 dated 15-Jan-2010. I recommend downloading the latest driver directly from Ralink.

Also, please post the output of "uname -a".

Tim


Thanks for the question, ratcheer. To respond to your first question, I have that output as the first line below. To respond to your second question, I've tried that newer driver. I just have been working with the older driver in my posts because that's what Chili has been typing in his replies. Regardless of which one I use, though, I'm getting the same results. 

Here's the output to show that... I think! Maybe if I did some of the steps in the newer directory, it would work. I think I have already tried, that, though, with the same negative results. 

[COLOR=Red]tsr@TimothySRooney:~$ uname -a[/COLOR]
Linux TimothySRooney 3.0.0-12-generic-pae #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 i686 athlon i386 GNU/Linux
[COLOR=Red]tsr@TimothySRooney:~$ cd Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
tsr@TimothySRooney:~/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ ls
[/COLOR]chips   include           Makefile  README_STA_pci     RT2860STA.dat  sta_ate_iwpriv_usage.txt
common  iwpriv_usage.txt  os        RT2860STACard.dat  sta            tools
[COLOR=Red]tsr@TimothySRooney:~/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217$ sudo make
[/COLOR][sudo] password for tsr: 
make -C tools
make[1]: Entering directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/tsr/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make[1]: Entering directory `/lib/modules/3.0.0-12-generic-pae/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.0.0-12-generic-pae/build'
make: *** [LINUX] Error 2
tsr@TimothySRooney:~/Downloads/Ralink/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217

---

### Post by ratcheer on 2011-11-18
Ok, I am lost on this one. Sorry.

Tim

---

### Post by chili555 on 2011-11-19
> My question is that the stuff in green indicates there's no rule to make the target module. So I went to the directory specified, and that is the last line I typed. The contents of the directory are listed above. Where is the rule to make the target module? Does that mean the directory listed there should have a make? There is certainly a Makefile. What does that Makefile contain? That's the whole point! Why is the Makefile going to /lib/modules/3.0.0-12-generic-pae/build? It ought to be going to linux-headers, as in my build:> root@LAPTOP60:/home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
make -C tools
make[1]: Entering directory `/home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.0.0-12-generic-pae/build SUBDIRS=/home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
[COLOR="Red"]make[1]: Entering directory `/usr/src/**linux-headers-3.0.0-12-generic-pae**'[/COLOR]
  CC [M]  /home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_md5.o
  CC [M]  /home/chili/Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/../../common/crypt_sha2.o
<snip>I can't imagine what is wrong if you have the build tools and linux headers installed. We have attempted to verify that. Grasping at straws, please open Synaptic Package Manager and be sure that both are installed. Please see attached. Please verify the little green box indicating that build-essential, linux-headers-generic-pae and linux-headers-3.0.0-12-generic-pae are definately installed. If not, install them.

In agreement with my esteemed colleague ratcheer, I'd remove the older versions 2.3.0.0 of the driver altogether.

I am running very low on ideas/talent/mojo.

---

### Post by timothysrooney on 2011-11-20
Chili, thanks for all your work, advice, and suggestions. I have finally resolved the issue. Unfortunately, it's not in a manner that will help too many other people. That's okay for me, but it won't be beneficial to the rest of the users looking for solutions here. That's too bad. But if you are looking for a quick fix to this problem, I can at least give you my solution.

After lots of time and effort (I know I invested > 10 hours in this, and I don't know how much Chili or Ratcheer also helped, but I sincerely appreciate all you guys did), I recognized it was time to cry "Uncle!" I went to Best Buy, found the NetGear N150 Wireless USB Adapter, found the installation tips on...

Okay, I found the link earlier. 

This doesn't help at all! I know I found the link on this forum somewhere... I don't know what link or site it was, though. At any rate, I foudn the driver for the Netgear USB, installed that driver, added the Netgear N150 to an open USB on my PC, and sure enough, everything works! It's not helping anybody with the Rosewill RNX-N150PC, but at least my problem is solved. Thanks for everyone's help and attention. Recommendation? Stop at Best Buy, get the USB adapter for $35, and take wireless with you wherever you need it!

---

### Post by alchemist77 on 2011-11-23
I did the upgrade to kernel 3.0.0-13 generic in 11.10, Reran the instructions from the first post using my downloaded file extracted to the RaLink Folder. (I have had to do this a number of times)used the make and make install restarted from a cold boot and it works like a champ. Just wishing I did not have to do this every time I upgrade.......

---

### Post by mechanizedmedic on 2011-11-28
> **alchemist77 said:**
> I did the upgrade to kernel 3.0.0-13 generic in 11.10, Reran the instructions from the first post using my downloaded file extracted to the RaLink Folder. (I have had to do this a number of times)used the make and make install restarted from a cold boot and it works like a champ. Just wishing I did not have to do this every time I upgrade.......

i use the following two scripts for just what you're talking about. the first is for after a new installation or distro upgrade and the second is for after kernel upgrades. :popcorn:

```
#!/bin/sh
## This script is intended to be run on a clean Ubuntu install after initial updates
## Script must run as root
script_name="ralink3062.sh"

if [ $(id -u) -ne 0 ]; then
        echo "You need to run this script as root."
        echo "Use 'sudo ./$script_name' then enter your password when prompted."
        exit 1
fi

#check for internet connection, abort if not connected or continue.
wget -q --tries=10 --timeout=5 http://www.google.com -O /tmp/index.google &> /dev/null

if [ ! -s /tmp/index.google ];

then 	echo "internet connection not detected... ABORTING...";
	exit 1

else 	echo "internet connetion detected"
	rm /tmp/index.google

#modify modprobe blacklist
sed '$a\
blacklist rt2800pci\n
blacklist rt2800lib\n
blacklist rt2x00pci\n
blacklist rt2x00lib\n' /etc/modprobe.d/blacklist.conf

#install dependancies
apt-get install build-essential linux-headers-generic

#download and extract archive
wget -r http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09USXlNek15TlRReE9TNTBaM285UFQxRVVFOWZVbFF6TlRZeVh6TTFPVEpmTXpBMk1sOU1hVzUxZUZOVVFWOVdNaTQwTGpFdU1WOHlNREV3TVRJeE53PT1D -O DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz
tar zxf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217.tgz

#edit make file
#DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk

sed -i 's/HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/g' DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk
sed -i 's/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/g' DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/config.mk

#compile
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
make
make install
echo rt3562sta >> /etc/modules

fi

echo " "
echo "INSTALLATION COMPLETE... DISCONNECT ETHERNET CABLE AND RESTART YOUR COMPUTER"
```


```
#!/bin/sh
## this script is intended to fix wireless connectivity after a kernel update for the rt3562sta driver
script_name="ralink3062_update.sh"

cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/
sudo su
make clean
make
make install
modprobe rt3562sta
exit
```

---

### Post by john1923 on 2012-01-21
Thank you.

You are a lifesaver. 

To help others find your post, my card was a Edimax EW-7711ln PCI card.

---

### Post by wsilk on 2012-03-11
The steps in the original post worked for me as well.  I've got a Zonet ZEW1642S PCI card and it now connects!

---

### Post by valem on 2012-06-10
Likewise, I have been successfully installing the drivers everytime after an upgrade for the past two years, however last night I upgraded to 3.2.0-24-generic #39-Ubuntu SMP and now I am unable to get my wireless working.
At the last step, after modprobe rt3562sta I get the following:

FATAL: Error inserting rt3562sta (/lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/rt3562sta.ko): Invalid module format

Any idea?
Thanks!

---

### Post by chili555 on 2012-06-10
> Any idea?Yes; I have the idea that you compiled this oldtimer:> DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_[COLOR="Red"]2010[/COLOR]1217...against your shiny new 3.2.0-24 kernel and it errored out because we no longer use wooden spoke wheels on our sleek BMWs. Let's see if there isn't a better way. Please post:```
lspci -nn | grep 0280
```

---

### Post by ratcheer on 2012-06-10
@chili555, that same "old-timer" driver is still working for me on 12.04 3.2.0-24-generic, Sabayon on linux 3.3, Arch Linux on 3.3.8, and Siduction on 3.4.1.

Tim

---

### Post by valem on 2012-06-12
@chili555 this is what I get

vale@vale-desktop:~$ lspci -nn | grep 0280
00:0c.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]

I didn't know there was a newer driver ... I'm going to look for it.
Only way I can get my wireless controller to work right now is to boot to the previous version.

Thanks!

---

### Post by chili555 on 2012-06-12
In Ubuntu 12.04, this device is driven by the module rt2800pci. Does it not work for you? Let's look at some diagnostics:```
sudo modprobe rt2800pci
dmesg | grep rt2
iwconfig
```Thanks.

---

### Post by valem on 2012-06-13
Thanks chili555! It came alive and connected right after modprobe rt2800pci ...
Excuse my ignorance, but can you please explain what the difference is between modprobe rt3562sta and rt2800pci and also, how do you know? How would have I been able to find the answer?
Thanks again!!

---

### Post by chili555 on 2012-06-13
> please explain what the difference is between modprobe rt3562sta and rt2800pci rt3562sta is the compiled from source code driver that wouldn't compile for you. We might have been able to work out the method, but why? The native driver rt2800pci works for you with no compiling.> how do you know? How would have I been able to find the answer?Become a driver monkey by studying such things for 10-12 hours a day for ten or so years. No-one expects anyone to do that; that's why there is a forum where you can tap into the OCD sickos who love this stuff and then retreat before you get the rash.

The native driver may be blacklisted, the usual process when you compile a driver. Please check:```
sudo gedit /etc/modprobe.d/blacklist.conf
```If there are any 'blacklist rt2800pci' or similar lines in there, remove them. Proofread, save and close gedit. Now let's get rt2800pci to load on boot automatically:```
sudo gedit /etc/modules
```Add one thing at the end:```
rt2800pci
```Proofread, save and close gedit. Reboot.

Now does your wireless work as expected automatically? If so, use thread tools at the top to mark Solved, so the searchers can learn and then retreat before you get the rash.

Seriously, if you need further assistance, post back.

---

### Post by ratcheer on 2012-06-13
> **valem said:**
> Thanks chili555! It came alive and connected right after modprobe rt2800pci ...
Excuse my ignorance, but can you please explain what the difference is between modprobe rt3562sta and rt2800pci and also, how do you know? How would have I been able to find the answer?
Thanks again!!

It is simple, the two commands load two different drivers. rt2800pci is the driver included with the standard Ubuntu system, whereas rt3562sta is the proprietary driver from the chipset maker, Ralink.

I can currently use either driver on my system (also an RT3062 chipset). rt3562sta performs better, but rt2800pci seems to have more features. For example, I get an IPv6 address with rt2800pci, but not with rt3562sta.

Tim

---

### Post by valem on 2012-06-13
I enjoyed your answer thanks!!
Yes, rt2800pci was blacklisted!
In modules, I added[FONT=monospace] [/FONT]rt2800pci, and after reboot it works, but should I remove rt3562sta.ko from modules?
So after future updates I won't have to go through all the steps again to get my wireless working?

---

### Post by valem on 2012-06-13
I see, that makes sense! Thanks Tim.

---

### Post by chili555 on 2012-06-14
> **valem said:**
> I enjoyed your answer thanks!!
Yes, rt2800pci was blacklisted!
In modules, I added[FONT=monospace] [/FONT]rt2800pci, and after reboot it works, but should I remove rt3562sta.ko from modules?
So after future updates I won't have to go through all the steps again to get my wireless working?Not necessary because it didn't get built properly:> At the last step, after modprobe rt3562sta I get the following:

FATAL: Error inserting rt3562sta (/lib/modules/3.2.0-24-generic/kernel/drivers/net/wireless/rt3562sta.ko): Invalid module format
If you wanted to be OCD super-sanitary, you could go into the build directory in a terminal and do:```
sudo su
make uninstall
exit
```

---

