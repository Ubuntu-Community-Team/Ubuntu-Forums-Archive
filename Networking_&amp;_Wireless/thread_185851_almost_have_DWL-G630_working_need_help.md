---
title: "almost have DWL-G630 working need help"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by onesojourner on 2006-06-01
I posted this in the dapper forum but its over running right now and it just keeps getting lost.

I have an old dell inspiron 7000 (PII 266) that I installed dapperRC on. I did have breezy but the 4 gig hdd filled up and would not allow the computer to boot... (is that fixed in dapper?) anyways I had wireless working on it sort of. I tried and tried and finally manually configured it during the breezy install and it would work but only on my wireless network. I could never get it to connect to anything else. Its not that big of a deal since the tank of a laptop is mainly stuck under the couch so some one can grab it and check email or such. the card is a d-link DWL-G630. it is detectect and I activated it. in network settings I clicked properties and it would not list the network so I manually typed it in
network name: hartmanhouse
key typer: hexadecimal
wep key: **********
DHCP

I double checked and everything is right. in connection properties wlan1 status is disconnected but signal strength is high 80-90%. whats going on? why will this stupid thing not get on the network?

I ran lspci and found the card

0000:06:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless interface

**Summary card detected, Wlan1 shows a signal of about 90% but states it disconnected, card shows up in network settings, card is activated, Manually typed in netwrk ssid and wep key. **

any thoughts? I thought maybe I would try this network manager that everyone is talking about but how would I do that with no internet connection? I wish they would stick that stuff on the cd. thanks for any help you guys can give.

**Update**

would network manager solve this?

links to this post with no good solution
[http://www.ubuntuforums.org/showthread.php?t=184126](http://www.ubuntuforums.org/showthread.php?t=184126)
[http://www.ubuntuforums.org/showthread.php?t=183649](http://www.ubuntuforums.org/showthread.php?t=183649)

---

### Post by onesojourner on 2006-06-02
bump? any one?

---

### Post by ignavia on 2006-06-02
I can't really offer any help. My G630 worked beautifully. I plugged it in post install, while the PC was running. Ubuntu recognized it as ath0 and let me set up the networking right away.

Since mine's ath0 and yours is wlan1, I'm guessing we have different cards. I think mine's a version C2, and apparently Atheros chipset based on the interface name.

---

### Post by SSamiK on 2006-06-02
It's not the same card as I had problems with, but it's the same chipset, and similar errors, so maby the same fix would sort your problems out as well. 

Have you tried the solutions in these threads?

[http://ubuntuforums.org/showthread.php?t=145836]("http://ubuntuforums.org/showthread.php?t=145836") Post #3
[http://ubuntuforums.org/showthread.php?t=183031]("http://ubuntuforums.org/showthread.php?t=183031") 

Don't know if it will help, but maby worth a try...

---

### Post by stimpsonjcat on 2006-06-02
are you connected to a router? can you ping it? in a terminal, type
```
ping -c 10 xxx.xxx.xxx.xxx
```
replace the x's with your router's IP address, probably 192.168.1.1
if that doesn't work, check your network settings. are you sure you're using DHCP? sometimes it helps to disable (not just deactivate) the ethernet interface in System>>Admin>>Networking>>Properties. for troubleshooting it might also help to disable WEP encryption and not hide your SSID.
if it works, try
```
ping -c 10 66.102.9.147
``` (google.com)
if that doesn't work there's probably something wrong with the connection between your router and your ISP. are there any other computers on your network? can you access the internet from there?
If it works, try
```
ping -c 10 www.google.com
```
if that doesn't work, there may be a problem with your DNS server settings, though those should be configured automatically if you're using DHCP.

---

### Post by judgekaster on 2006-06-02
i had the same problems with a similar DLink acx111 based wireless card.  Though it presents itself in "iwconfig", the command "iwlist wlan0 scan" will alway return with a failure to get accesspoint information. 

my solution was to replace the firmware the came with Dapper with the one found in the acx111.sourceforge.com site, i.e.

[http://acx100.erley.org/acx_fw/acx111_netgear_wg311v2/fw1/]("http://acx100.erley.org/acx_fw/acx111_netgear_wg311v2/fw1/")

to do this:

1) open a terminal and issue the following commands

sudo -s
< supply password >
rmmod acx
cd /lib/firmware/`uname -r`
mv acx acx-bak

2. open another terminal and issue the following command

tail -f /var/log/messages

3. back to first terminal

modprobe acx

4. check terminal 2 and look for the line that indicates an error where the firmware file is missing, something like /lib/firmware/2.6.13/acx/2.3.1.31/tiacx111c16 missing; make a note of this path

5. back to terminal 1

copy the firmware file downloaded above to the location pointed to in #4; then

modprobe acx111

6. check your network again

6.

---

### Post by guwrt on 2006-06-02
Hello

I have try your solution and my cardbus doesn't light anymore. The link light turned off. The file that you download on sourceforge, do I have to rename it before copying?

In the second terminal, I didn't see any error. So I cannot determine the path.

I am working with a Dell C600. Everything was ok under Breezer but under Dapper , It doesn't work at all.

Thanks for your support

---

### Post by judgekaster on 2006-06-03
yes, you will have to rename it... would you kindly post the output of

tail -n 20 /var/log/messages

after 

modprobe acx111

---

### Post by tdyer on 2006-06-03
hi all

i also almost have my dwl-g630-rb working

it uses the tnet1130 driver so i believe that makes it the TI acx100 or something.

i was in the process of following the steps i found for the sourceforge drivers. found here: [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

when i realized i was almost late for work and rushed off in a hurry.

this morning i woke up and after booting up i noticed that my card magically worked with no encryption and with wep.

no although i should just bless my lucky stars that it works...i would like WPA.

following the steps here: [http://www.ubuntuforums.org/showthread.php?t=179643](http://www.ubuntuforums.org/showthread.php?t=179643)

and my card does not work. ](*,) 

any ideas what so ever?

---

### Post by guwrt on 2006-06-03
Hello judgekaster,

Just before going throuhgt, Is it necessary to rename ack to acx to acx-bak?

If I rename the file obtained with the link, which name I use?

Can I just replace Tiacx111c16 file with the downloaded file?

Thanks again

Guwrt

---

### Post by tdyer on 2006-06-03
ok...

i somehow killed my install. kept crashing on boot.

format and relaod,

network manager now sees my wireless card, but it doesnt see any networks

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by guwrt on 2006-06-03
I am at the same point. I tried different thing and still not want to talk with my access point.

Not easy Dapper

Guwrt

---

### Post by judgekaster on 2006-06-04
[QUOTE=guwrt]Hello judgekaster,

Just before going throuhgt, Is it necessary to rename ack to acx to acx-bak?

If I rename the file obtained with the link, which name I use?

Can I just replace Tiacx111c16 file with the downloaded file?

Thanks again

Guwrt[/QUOTE]

hello guwrt,

1) renaming acx to acx-bak is just to make sure that acx111 module won't see the firmware file and thus generate an error when it is loaded

2) do post the output of tail -n25 /var/log/messages and tail -n25 /var/log/syslog when you do a 'modprobe acx111' after renaming the acx directory to acx-bak

---

### Post by Tux+ on 2006-06-04
I'm using a DLink G520+ that uses the acx111 driver. I can't seem to get it to see any network's either! I usally pick up couple of networks on breezy but nothing on dapper. I copied my /etc/networking/interfaces file to dapper and still no luck. I followed judgekaster's steps but that seems to kill the light on the card so i restored the acx-bak and its backup again.

It's really bugging as i want to upgrade my breezy to dapper but wanted to make sure the wireless worked first and good job i did this.

Is it normal to say "Send On        Socket/Fallback" when i do /etc/init.d/networking restart
?

----Edit----
Got it to work now. It was the new driver not working for my card and used the version before it (1.2.1.34). I added the

options acx firmware_ver=1.2.1.34

to /etc/modprobe.d/options and after a reboot it worked.
the page can be found [here]("http://ubuntuforums.org/showthread.php?t=183031")

---

### Post by guwrt on 2006-06-04
Hello judgecaster,

Here is the results for your request,

dell01@dell01-laptop:~$ tail -n25 /var/log/messages
Jun  4 20:18:46 localhost kernel: [4342093.968000] acx: firmware image 'acx/default/tiacx111c16' was not provided. Check your hotplug scripts
Jun  4 20:18:46 localhost kernel: [4342093.978000] acx: firmware image 'acx/default/tiacx111' was not provided. Check your hotplug scripts
Jun  4 20:18:46 localhost kernel: [4342093.978000] acx: reset_dev() FAILED
Jun  4 20:18:46 localhost kernel: [4342093.978000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Jun  4 20:18:46 localhost kernel: [4342093.989000] acx_pci: probe of 0000:06:00.0 failed with error -5
Jun  4 20:19:31 localhost kernel: [4342138.722000] pccard: card ejected from slot 1
Jun  4 20:19:35 localhost kernel: [4342142.870000] pccard: CardBus card inserted into slot 1
Jun  4 20:19:35 localhost kernel: [4342142.871000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
Jun  4 20:19:35 localhost kernel: [4342142.871000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun  4 20:19:35 localhost kernel: [4342142.871000] acx: found ACX111-based wireless network card at 0000:06:00.0, irq:11, phymem1:0x26020000, phymem2:0x26000000, mem1:0xd8a00000, mem1_size:8192, mem2:0xd8c80000, mem2_size:131072
Jun  4 20:19:36 localhost kernel: [4342143.582000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
Jun  4 20:19:36 localhost kernel: [4342143.582000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-23-386
Jun  4 20:19:37 localhost kernel: [4342144.457000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  4 20:20:55 localhost kernel: [4342222.711000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Jun  4 20:20:55 localhost kernel: [4342222.723000] usbcore: deregistering driver acx_usb
Jun  4 20:25:04 localhost kernel: [4342471.549000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Jun  4 20:25:04 localhost kernel: [4342471.549000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Jun  4 20:25:04 localhost kernel: [4342471.561000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun  4 20:25:04 localhost kernel: [4342471.562000] acx: found ACX111-based wireless network card at 0000:06:00.0, irq:11, phymem1:0x26020000, phymem2:0x26000000, mem1:0xd8a10000, mem1_size:8192, mem2:0xd8c80000, mem2_size:131072
Jun  4 20:25:04 localhost kernel: [4342471.582000] acx: firmware image 'acx/default/tiacx111c16' was not provided. Check your hotplug scripts
Jun  4 20:25:04 localhost kernel: [4342471.593000] acx: firmware image 'acx/default/tiacx111' was not provided. Check your hotplug scripts
Jun  4 20:25:04 localhost kernel: [4342471.597000] acx: reset_dev() FAILED
Jun  4 20:25:04 localhost kernel: [4342471.597000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Jun  4 20:25:04 localhost kernel: [4342471.609000] acx_pci: probe of 0000:06:00.0 failed with error -5
Jun  4 20:25:04 localhost kernel: [4342471.610000] usbcore: registered new driver acx_usb
dell01@dell01-laptop:~$ 

dell01@dell01-laptop:~$ tail -n25 /var/log/syslog
Jun  4 20:20:42 localhost dhclient: No working leases in persistent database - sleeping.
Jun  4 20:20:42 localhost ntpdate[6100]: can't find host ntp.ubuntu.com
Jun  4 20:20:42 localhost ntpdate[6100]: no servers can be used, exiting
Jun  4 20:20:55 localhost dhclient: receive_packet failed on wlan0: Network is down
Jun  4 20:20:55 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.3
Jun  4 20:20:55 localhost dhclient: Copyright 2004-2005 Internet Systems Consortium.
Jun  4 20:20:55 localhost dhclient: All rights reserved.
Jun  4 20:20:55 localhost dhclient: For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
Jun  4 20:20:55 localhost dhclient:
Jun  4 20:20:55 localhost kernel: [4342222.711000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Jun  4 20:20:55 localhost kernel: [4342222.723000] usbcore: deregistering driver acx_usb
Jun  4 20:20:55 localhost dhclient: Bind socket to interface: No such device
Jun  4 20:25:04 localhost kernel: [4342471.549000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Jun  4 20:25:04 localhost kernel: [4342471.549000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
Jun  4 20:25:04 localhost kernel: [4342471.561000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jun  4 20:25:04 localhost kernel: [4342471.562000] acx: found ACX111-based wireless network card at 0000:06:00.0, irq:11, phymem1:0x26020000, phymem2:0x26000000, mem1:0xd8a10000, mem1_size:8192, mem2:0xd8c80000, mem2_size:131072
Jun  4 20:25:04 localhost firmware_helper[6157]: main: error loading '/lib/firmware/acx/default/tiacx111c16' for device '/class/firmware/0000:06:00.0' with driver 'acx_pci'
Jun  4 20:25:04 localhost kernel: [4342471.582000] acx: firmware image 'acx/default/tiacx111c16' was not provided. Check your hotplug scripts
Jun  4 20:25:04 localhost firmware_helper[6160]: main: error loading '/lib/firmware/acx/default/tiacx111' for device '/class/firmware/0000:06:00.0' with driver 'acx_pci'
Jun  4 20:25:04 localhost kernel: [4342471.593000] acx: firmware image 'acx/default/tiacx111' was not provided. Check your hotplug scripts
Jun  4 20:25:04 localhost kernel: [4342471.597000] acx: reset_dev() FAILED
Jun  4 20:25:04 localhost kernel: [4342471.597000] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Jun  4 20:25:04 localhost kernel: [4342471.609000] acx_pci: probe of 0000:06:00.0 failed with error -5
Jun  4 20:25:04 localhost kernel: [4342471.610000] usbcore: registered new driver acx_usb
Jun  4 20:35:10 localhost -- MARK --
dell01@dell01-laptop:~$  


That's it for the message

Thanks for support

Guwrt

---

### Post by tdyer on 2006-06-04
i am having mixed successes. my networkmanager detects my card now, and detects wireless networks...not sure if that will last after a reboot
it seems to start working after i do the rmmod acx step...yeah

here is the tail of my log file after trying modprobe acx.
root@tristan-laptop:~# tail -n 20 /var/log/messages
Jun  4 23:41:32 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for s ub-path wlan0.dbus.get.domain_name
Jun  4 23:41:32 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for s ub-path wlan0.dbus.get.nis_domain
Jun  4 23:41:32 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for s ub-path wlan0.dbus.get.nis_servers
Jun  4 23:41:32 localhost kernel: [4296395.595000] eth0: Media Link On 100mbps full-duplex
Jun  4 23:41:49 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for su b-path eth0.dbus.get.host_name
Jun  4 23:41:49 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for su b-path eth0.dbus.get.domain_name
Jun  4 23:41:49 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for su b-path eth0.dbus.get.nis_domain
Jun  4 23:41:49 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for su b-path eth0.dbus.get.nis_servers
Jun  4 23:43:05 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for s ub-path wlan0.dbus.get.host_name
Jun  4 23:43:05 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for s ub-path wlan0.dbus.get.domain_name
Jun  4 23:43:05 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for s ub-path wlan0.dbus.get.nis_domain
Jun  4 23:43:05 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for s ub-path wlan0.dbus.get.nis_servers
Jun  4 23:44:24 localhost gconfd (root-6451): SIGHUP received, reloading all databases
Jun  4 23:44:24 localhost gconfd (root-6451): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to  a read-only configuration source at position 0
Jun  4 23:44:24 localhost gconfd (root-6451): Resolved address "xml:readwrite:/root/.gconf" to a writable confi guration source at position 1
Jun  4 23:44:24 localhost gconfd (root-6451): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun  4 23:44:24 localhost gconfd (root-6451): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to  a read-only configuration source at position 3
Jun  4 23:44:24 localhost gconfd (root-6451): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read -only configuration source at position 4
Jun  4 23:44:24 localhost gconfd (root-6451): GConf server is not in use, shutting down.
Jun  4 23:44:24 localhost gconfd (root-6451): Exiting


now for the funky stuff...if i try either wep or wpa encryption it tells me that my card does not support encryption...wpa-supplicant is installed.

any ideas?

thanks in advance

---

### Post by funkydan2 on 2006-06-05
My understanding is that WPA is still not supported using the version of the acx module in Dapper.  If you visit the [acx sourceforge site](http://acx100.sf.net) you'll read that there is some work on getting wpa support in the ACXSM branch of the code, but that it's not reliable yet.

I think the problem with the acx driver in dapper is that an unreliable version of the acxsm code has been included (hence the 2.3.1.31 firmware, which is for the acxsm code).

So I don't think there will be WPA support for acx wireless cards with Dapper, but there is a chance that it may be ready for Edgy.

---

### Post by judgekaster on 2006-06-05
Hello Gwurt,

The pertinent lines of your log are the following:

```

Jun  4 20:25:04 localhost kernel: [4342471.582000] acx: firmware image 'acx/default/tiacx111c16' was not provided. Check your hotplug scripts
Jun  4 20:25:04 localhost kernel: [4342471.593000] acx: firmware image 'acx/default/tiacx111' was not provided. Check your hotplug scripts

```

If your will check the /lib/firmware/`uname -r`/acx/default directory, you will see that the tiacx111c16 is a link to the firmware image in the directory 2.3.1.31:

```

$ ls -la /lib/firmware/`uname -r`/acx/default

```
results in
```

total 0
drwxr-xr-x  2 root root 296 2006-05-31 08:10 .
drwxr-xr-x 13 root root 344 2006-05-31 08:10 ..
lrwxrwxrwx  1 root root  19 2006-05-31 08:10 tiacx100 -> ../1.9.8.b/tiacx100
lrwxrwxrwx  1 root root  22 2006-05-31 08:10 tiacx100r0D -> ../1.9.8.b/tiacx100r0D
lrwxrwxrwx  1 root root  22 2006-05-31 08:10 tiacx100r11 -> ../1.9.8.b/tiacx100r11
lrwxrwxrwx  1 root root  22 2006-05-31 08:10 tiacx100r15 -> ../1.9.8.b/tiacx100r15
lrwxrwxrwx  1 root root  20 2006-05-31 08:10 tiacx100usb -> ../1.0.9/tiacx100usb
lrwxrwxrwx  1 root root  23 2006-05-31 08:10 tiacx111c16 -> ../2.3.1.31/tiacx111c16
lrwxrwxrwx  1 root root  23 2006-05-31 08:10 tiacx111c17 -> ../2.3.1.31/tiacx111c17
lrwxrwxrwx  1 root root  23 2006-05-31 08:10 tiacx111c19 -> ../2.3.1.31/tiacx111c19

```
So, let us copy the firmware image to that location. I suggest that you open a terminal and issue the following commands:

```

$ sudo -s 
<Enter password>
$ rmmod acx111
$ cd /lib/firmware/`uname -r`
$ mv acx acx-bak
$ mkdir acx
$ cd acx
$ mkdir default
$ mkdir 2.3.1.31
$ cd 2.3.1.31
$ wget http://acx100.erley.org/acx_fw/acx111_netgear_wg311v2/fw1/FwRad16.bin_1.2.1.34
$ mv FwRad16.bin_1.2.1.34 tiacx111c16
$ cd ../default
$ ln -s ../2.3.1.31/tiacx111c16 tiacx111c16
$ modprobe acx111
$ exit

```

Now you can check your log messages if you get the same message as before. If the message is gone, that means the firmware was used by the acx111 module. Now, check if your wireless card is working..

```

$ sudo iwconfig
$ sudo iwlist wlan0 scan

```

If you get a reading of the access points near you, you can then use the "Networking" tool provided in Ubuntu.

That's it.

---

### Post by guwrt on 2006-06-07
Hello judgecaster,

You was almost on it. You're great. Thanks.

I write this text to explain how I get my card running again with Dapper. I must specify that my card is a version B1.

First of all, I took back my installation CD for this cardbus that's was used for Windows. I made a copy of two files(fwrad16.bin and fwrad17.bin) in my home directory. I had renamed those 2 files to become tiacx111c16 and tiacx111c17.

Those 2 files were copied in the directory /lib/firmware/2.6.15-23-386/acx/1.2.1.34.

These 2 files replaced those that were already there. Finally, there is now 5 files present in the directory /lib/firmware/2.6.15-23-386/acx/1.2.1.34.

tiacx111
tiacx111c16
tiacx111c17
tiacx111r16
tiacx111r17

After, I have created a link for each of these files in /lib/firmware/2.6.15-23-386/acx/default.

I have made a reboot of my computer.

I have open the wifi manager assistant to establish the communication between my card and my acces point with no encryption. The act led started to blink finally.

Final step, I have include my wep key and the link was still ok. I was able to go on the net. Eureka!!!!

Thanks again judgecaster

Guwrt

---

