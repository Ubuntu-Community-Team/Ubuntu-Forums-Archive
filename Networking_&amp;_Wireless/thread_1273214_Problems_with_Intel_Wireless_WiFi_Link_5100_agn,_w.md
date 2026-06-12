---
title: "Problems with Intel Wireless WiFi Link 5100 agn, with wifi &quot;n&quot; connection"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by akyra on 2009-09-23
Dear all,

I’m using Ubuntu Jaunty 64 bits and I have a problem in my laptop (Toshiba Satellite A500-141 with Intel Corporation Wireless WiFi Link 5100 agn) with the wifi “n” connection.

When starts my laptop the Network Manager shows established connection but if I do a ping command to 192.168.1.2 (it's the router) the answer delay until 46 seconds. After this firts ping the answer time reduce until 2ms. Also, disconnections happen regulary (but network manager shows the connection established) but the ping delay until 40 seconds one more time.

If I connect with wifi "b" or cable, works fine and Vista wifi “n” connection works fine too.

I try to install the intel driver, but after copy the driver "cp iwlwifi-5000-2.ucode /lib/firmware" what is the next step? Actually I have iwlwifi-5000-1.ucode installed.

The lspci command return:
jordi@jordi-laptop:~$ lspci -nn | grep Network
14:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]

and this is the ping results:
jordi@jordi-laptop:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
From 192.168.2.3 icmp_seq=28 Destination Host Unreachable
From 192.168.2.3 icmp_seq=29 Destination Host Unreachable
From 192.168.2.3 icmp_seq=30 Destination Host Unreachable
From 192.168.2.3 icmp_seq=31 Destination Host Unreachable
From 192.168.2.3 icmp_seq=32 Destination Host Unreachable
From 192.168.2.3 icmp_seq=33 Destination Host Unreachable
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=46189 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=45188 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=44188 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=43188 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=42189 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=41187 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=40188 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=39188 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=38188 ms
64 bytes from 192.168.2.1: icmp_seq=10 ttl=64 time=37189 ms
64 bytes from 192.168.2.1: icmp_seq=11 ttl=64 time=36188 ms
64 bytes from 192.168.2.1: icmp_seq=12 ttl=64 time=35188 ms
64 bytes from 192.168.2.1: icmp_seq=13 ttl=64 time=34189 ms
64 bytes from 192.168.2.1: icmp_seq=14 ttl=64 time=33188 ms
64 bytes from 192.168.2.1: icmp_seq=15 ttl=64 time=32188 ms
64 bytes from 192.168.2.1: icmp_seq=48 ttl=64 time=2.44 ms
64 bytes from 192.168.2.1: icmp_seq=49 ttl=64 time=2.47 ms
64 bytes from 192.168.2.1: icmp_seq=50 ttl=64 time=2.79 ms 


Thak you very much in advanced, and sorry my english.

---

### Post by akyra on 2009-09-25
Hi all,
I try to install the new intel firmware "iwlwifi-5000-2.ucode", but I don't know how.
I've done: "sudo cp iwlwifi-5000-ucode-8.24.2.12 (2)/iwlwifi-5000-2.ucode /lib/firmware", but, what is the next step?
This is console result:
jordi@jordi-ubuntu:~$ uname -r
2.6.28-15-generic
jordi@jordi-ubuntu:~$ dmesg | grep iwl
[ 11.269247] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[ 11.269250] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 11.269335] iwlagn 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 11.269343] iwlagn 0000:14:00.0: setting latency timer to 64
[ 11.269375] iwlagn 0000:14:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[ 11.291255] iwlagn 0000:14:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 11.291325] iwlagn 0000:14:00.0: irq 2296 for MSI/MSI-X
[ 11.294866] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 23.622760] iwlagn 0000:14:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[ 23.710974] iwlagn 0000:14:00.0: loaded firmware version 5.4.1.16
[ 23.866506] Registered led device: iwl-phy0::radio
[ 23.866524] Registered led device: iwl-phy0::assoc
[ 23.866538] Registered led device: iwl-phy0::RX
[ 23.866551] Registered led device: iwl-phy0::TX
[ 54.361843] iwlagn 0000:14:00.0: index 0 not used in uCode key table.
[ 293.541276] iwlagn 0000:14:00.0: iwl_tx_agg_start on ra = ffff88013e5ae740 tid = 0
[ 293.541332] iwlagn 0000:14:00.0: HW queue is empty
[14096.921265] iwlagn 0000:14:00.0: iwl_tx_agg_start on ra = ffff88012c079740 tid = 0
[14096.921325] iwlagn 0000:14:00.0: HW queue is empty

Thank you very much in advanced

---

### Post by chili555 on 2009-09-25
This is a problem that I don't understand, but it may be related to the firmware:```
iwlagn 0000:14:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
```We don't see that any 'n' channels listed as tunable. 

The card wants iwlwifi-5000-1.ucode, but can't find it and so it loads 5.4.1.16 instead. Perhaps the 5.4.1.16 firmware doesn't provide 'n' capabilities. Please check with:```
ls -al /lib/firmware | grep 5000
```Do you have iwlwifi-5000-1.ucode there? Is it readable by all, like this?> -rw-r--r--  1 root root 345008 2009-04-02 17:46 iwlwifi-5000-1.ucodePlease post back and we'll try to get you going.

---

### Post by akyra on 2009-09-25
Hi Chilli

This is the console results:
> jordi@jordi-ubuntu:~$ ls -al /lib/firmware | grep 5000
-rw-r--r--  1 root root 345008 2009-04-02 23:46 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root 353240 2009-04-23 21:28 iwlwifi-5000-2.ucode
jordi@jordi-ubuntu:~$ 


Actually I'm connected to my route (belkin N1 Vision) and teorically the network is b,g,n, and I'm connected in channel 11.

Thank you very much.

---

### Post by chili555 on 2009-09-25
> I try to install the intel driverCan you provide us a link to the driver you tried to install? Did something go wrong with the install? It looks like the stock, inbuilt driver is being loaded and it's requesting iwlwifi-5000-1.ucode instead of iwlwifi-5000-[COLOR="Red"]2[/COLOR].ucode. May we assume you tried the Intel driver to try to solve your slow pings?

Have you installed linux-backports-jaunty-generic? It evidently contains a newer iwlagn driver, as well as microcode. It is available through Synaptic.> teorically the network is b,g,nWhat does iwconfig say your bit rate is? 54Mb/s? That's certainly not 'n'.

---

### Post by akyra on 2009-09-25
Hi,

> Can you provide us a link to the driver you tried to install?
This is the download link: [http://www.intellinuxwireless.org/?n=Downloads]("http://www.intellinuxwireless.org/?n=Downloads") and you can find the "  iwlwifi-5000-ucode-8.24.2.12.tgz" firmware.

> Did something go wrong with the install?
I follow the instructions, well, I only done "sudo cp iwlwifi-5000-ucode-8.24.2.12 (2)/iwlwifi-5000-2.ucode /lib/firmware", but I think that is not enough, but I dont know wich is the next step (compile the firmware??)


> Have you installed linux-backports-jaunty-generic?
I've installed "linux-backports-modules-jaunty-generic" (I think that is ok).

> May we assume you tried the Intel driver to try to solve your slow pings?
Yes, I tried, and also I try to solve the periodic disconnections.

> What does iwconfig say your bit rate is? 54Mb/s? That's certainly not 'n'.
Really doesn't is wifi "n".
In this link you can find a router configuration:
[http://www.badongo.com/pic/7223176]("http://www.badongo.com/pic/7223176")

Thank you very much.

---

### Post by chili555 on 2009-09-25
> I follow the instructions, well, I only done "sudo cp iwlwifi-5000-ucode-8.24.2.12 (2)/iwlwifi-5000-2.ucode /lib/firmware", but I think that is not enough, but I dont know wich is the next step (compile the firmware??)That would simply copy the entire folder, containing the firmware, the README and the license to /lib/firmware. The driver cannot find it if it's inside a folder. However, you do have the -2.ucode in there, probably from the installation of *backports*.> Really doesn't is wifi "n".I don't really understand this, I guess something got lost between Spain and South Carolina, USA. When you open a terminal and run:```
iwconfig wlan0
```What is the bit rate? Can you please post the output of iwconfig?> you can find a router configurationIt looks like you have the router set correctly to connect at 'n' speeds if the wireless card negotiates it; the question is, is it or not? Why not? iwconfig will help us.

---

### Post by akyra on 2009-09-26
Hi chili555,

> That would simply copy the entire folder, containing the firmware, the README and the license to /lib/firmware.
I've only copied the "iwlwifi-5000-2.ucode" firmware file, I haven't copied the license, neither all the folder. It's necessary?

jordi@jordi-ubuntu:~$ ls /lib/firmware/iw*
/lib/firmware/iwlwifi-3945-1.ucode  /lib/firmware/iwlwifi-4965-2.ucode
/lib/firmware/iwlwifi-3945-2.ucode  /lib/firmware/iwlwifi-5000-1.ucode
/lib/firmware/iwlwifi-4965-1.ucode  /lib/firmware/iwlwifi-5000-2.ucode

> I don't really understand this, I guess something got lost between Spain and South Carolina, USA
Sure! It was in the atlantic ocean. :)


> What is the bit rate? Can you please post the output of iwconfig?

jordi@jordi-ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Jordi_Belkin_N1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:C6:1C:F8   
          Bit Rate=60 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=70/70  Signal level=-14 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

This are the instructions to install the new firmware (from intel), but I don't understand.

> 2. INSTALLATION

The iwlagn driver will look for the file iwlwifi-5000-2.ucode using the
kernel's firmware_loader infrastructure.  In order to function
correctly, you need to have this support enabled in your kernel.  When
you configure the kernel, you can find this option in the following
location:

        Device Drivers ->
                Generic Driver Options ->
                        Hotplug firmware loading support


You can determine if your kernel currently has firmware loader support
by looking for the CONFIG_FW_LOADER definition on your kernel's
.config.

In addition to having the firmware_loader support in your kernel, you
must also have a working hotplug and udev infrastructure configured.
The steps for installing and configuring hotplug and udev are very
distribution specific.

Once you have the firmware loader in place (or if you aren't sure and
you just want to try things to see if it works), you need to install
the microcode file into the appropriate location.

Where that appropriate location is depends (again) on your system
distribution.  You can typically find this location by looking in the
hotplug configuration file for your distro:

	% grep \"^FIRMWARE_DIR\" /etc/hotplug/firmware.agent

This should give you output like:

	FIRMWARE_DIR=/lib/firmware

If it lists more than one directory, you only need to put the
microcode in one of them.  In the above example, installation is
simply:

	% cp iwlwifi-5000-2.ucode /lib/firmware

You can now load the driver (see the INSTALL and README.iwlwifi provided with
the iwlwifi package for information on building and using that driver.)


Thank you for your patience.

---

### Post by chili555 on 2009-09-27
> I haven't copied the license, neither all the folder. It's necessary?No. Your /lib/firmware file looks just perfect.> Bit Rate=60 Mb/sYour bit rate is in the 'n' range, but still low. Your signal strength is as high as it can get, so we would expect that the bit rate would be higher still.

After I studied the instructions you linked us to, it appears to me that this firmware will be asked for by the driver that can be downloaded on the same page. However, I do not think it is appropriate for you because it is version 1.2.25 and the version installed in Jaunty is 1.3.27. I can't imagine that reverting to an older version will fix anything.

As well, the instructions say the driver is only for kernels 2.6.18 to 2.6.23. My kernel, and, I suspect yours, is 2.6.28-15. You can find out with:```
uname -r
```There is doubt that the older driver would even build and install correctly if it's built for an older kernel. Why is there not a newer version on Intel's site, you ask? I suspect it's because they believe the driver and firmware associated with the current kernel is the best.

I am convinced that we must look elsewhere, aside from the driver and ucode, to try to solve your pings and disconnects. When you ping and it takes a long time, please do:```
sudo cat /var/log/messages | grep iwl
```Let's see what the system tells us.

As far as this:> 2. INSTALLATION

The iwlagn driver will look for the file iwlwifi-5000-2.ucode using the
kernel's firmware_loader infrastructure. In order to function
correctly, you need to have this support enabled in your kernel. Etc.You can ignore all this. We know that the driver is loading the firmware.

---

### Post by akyra on 2009-09-27
Hi,

> uname -r
jordi@jordi-ubuntu:~$ uname -r
2.6.28-15-generic

> After I studied the instructions you linked us to, it appears to me that this firmware will be asked for by the driver that can be downloaded on the same page. However, I do not think it is appropriate for you because it is version 1.2.25 and the version installed in Jaunty is 1.3.27. I can't imagine that reverting to an older version will fix anything.
Yes, I agree with the driver, but I don't understand why de firmare loaded is "lbm-iwlwifi-5000-1.ucode" (I put in the second message):
[ 23.622760] iwlagn 0000:14:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[ 23.710974] iwlagn 0000:14:00.0: loaded firmware version 5.4.1.16
> 
Why is there not a newer version on Intel's site, you ask?
I dont find new drivers version on Intel's site. All the information that I've found, are in [http://www.intellinuxwireless.org/?n=Downloads]("http://www.intellinuxwireless.org/?n=Downloads") 
I understand that the new drivers are inclusive with the kernel. Is it correct?

This are the results (sudo cat /var/log/messages | grep iwl):
> jordi@jordi-ubuntu:~$ sudo cat /var/log/messages | grep iwl
Sep 27 16:53:25 jordi-ubuntu kernel: [   11.788445] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Sep 27 16:53:25 jordi-ubuntu kernel: [   11.788449] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Sep 27 16:53:25 jordi-ubuntu kernel: [   11.788541] iwlagn 0000:14:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Sep 27 16:53:25 jordi-ubuntu kernel: [   11.788601] iwlagn 0000:14:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Sep 27 16:53:25 jordi-ubuntu kernel: [   11.810277] iwlagn 0000:14:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Sep 27 16:53:33 jordi-ubuntu kernel: [   23.637777] iwlagn 0000:14:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
Sep 27 16:53:33 jordi-ubuntu kernel: [   23.696622] iwlagn 0000:14:00.0: loaded firmware version 5.4.1.16
Sep 27 16:53:33 jordi-ubuntu kernel: [   23.851485] Registered led device: iwl-phy0::radio
Sep 27 16:53:33 jordi-ubuntu kernel: [   23.851504] Registered led device: iwl-phy0::assoc
Sep 27 16:53:33 jordi-ubuntu kernel: [   23.851518] Registered led device: iwl-phy0::RX
Sep 27 16:53:33 jordi-ubuntu kernel: [   23.851532] Registered led device: iwl-phy0::TX
Sep 27 17:11:28 jordi-ubuntu kernel: [ 1100.754535] iwlagn 0000:14:00.0: iwl_tx_agg_start on ra = ffff88012ac91340 tid = 0
Sep 27 17:14:10 jordi-ubuntu kernel: [ 1262.435826] iwlagn 0000:14:00.0: iwl_tx_agg_start on ra = ffff880131475b40 tid = 0


And this is the result from /var/log/messages:
> Sep 27 17:14:10 jordi-ubuntu kernel: [ 1262.435826] iwlagn 0000:14:00.0: iwl_tx_agg_start on ra = ffff880131475b40 tid = 0
Sep 27 17:15:27 jordi-ubuntu kernel: [ 1339.727804] iwlagn 0000:14:00.0: iwl_tx_agg_start on ra = ffff88011540d340 tid = 0

Thank you very much.

---

### Post by chili555 on 2009-09-28
> I don't understand why de firmare loaded is "lbm-iwlwifi-5000-1.ucode"Because the built-in driver, version 1.3.27, asks for 5000.1. The obsolete driver on Intel's site would ask for 5000-2.> I understand that the new drivers are inclusive with the kernel. Is it correct?Correct.

I can't see anything wrong with the /var/log/messages. I can't see anything to try to fix. This is my favorite kind of problem; there is nothing wrong, evidently, but it doesn't work properly.

802.11n is notoriously hard to get going with Linux, especially with some wireless cards. The only thing I have left to suggest is to set your router to use 802.11a, b and g, but not 'n', and to see if you have the slow pings and disconnects at 'g' speeds. Perhaps 'n' support will improve with future versions of Ubuntu.

---

### Post by akyra on 2009-09-28
But, the "lbm-iwlwifi-5000-2.ucode" is newer than "lbm-iwlwifi-5000-1.ucode"? If this is thus, is posible to make a new kernel with the new firmware version? Or the "lbm-iwlwifi-5000-1.ucode" is the newer version?

It¡s a litle complicated for my.

On my router only is possible select wifi "a, b, g,n" or wifi "Deactivated", I can't select "a, b, b" only

Thank you

---

### Post by chili555 on 2009-09-28
> But, the "lbm-iwlwifi-5000-2.ucode" is newer than "lbm-iwlwifi-5000-1.ucode"? I don't know for sure, however, my guess is that the -2.ucode, which is on Intel's site, and associated with kernel versions 2.6.18 to 2.6.23 is older than the -1.ucode that came with the *backports* package matching kernel 2.6.28-15. 

There is a trick you can try temporarily; rename -2.ucode to -1.ucode and rename -1.ucode to -1.ucode.bak, like this:```
cd /lib/firmware
sudo mv iwlwifi-5000-1.ucode iwlwifi-5000-1.ucode.bak
sudo mv iwlwifi-5000-2.ucode iwlwifi-5000-1.ucode
```If it makes no difference in your ability to connect and stay connected, you can reverse the process. In order for the change to take effect, do:```
sudo rmmod -f iwlagn
sudo modprobe iwlagn
```> On my router only is possible select wifi "a, b, g,n"You can force the card to 'g' speeds:```
sudo iwconfig wlan0 rate 54M
```Please let us know.

---

### Post by akyra on 2009-09-29
Hi

> There is a trick you can try temporarily; rename -2.ucode to -1.ucode and rename -1.ucode to -1.ucode.bak, like this:
No difference

> sudo iwconfig wlan0 rate 54M
No difference

> jordi@jordi-ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Jordi_Belkin_N1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:C6:1C:F8   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jordi@jordi-ubuntu:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=43103 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=42103 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=41103 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=40103 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=39103 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=38103 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=37103 ms
64 bytes from 192.168.2.1: icmp_seq=8 ttl=64 time=36103 ms
64 bytes from 192.168.2.1: icmp_seq=9 ttl=64 time=35103 ms
64 bytes from 192.168.2.1: icmp_seq=10 ttl=64 time=34103 ms
64 bytes from 192.168.2.1: icmp_seq=11 ttl=64 time=33102 ms
64 bytes from 192.168.2.1: icmp_seq=12 ttl=64 time=32102 ms
64 bytes from 192.168.2.1: icmp_seq=13 ttl=64 time=31093 ms
64 bytes from 192.168.2.1: icmp_seq=14 ttl=64 time=30084 ms
64 bytes from 192.168.2.1: icmp_seq=15 ttl=64 time=29076 ms
64 bytes from 192.168.2.1: icmp_seq=45 ttl=64 time=7.92 ms
64 bytes from 192.168.2.1: icmp_seq=46 ttl=64 time=7.42 ms
64 bytes from 192.168.2.1: icmp_seq=47 ttl=64 time=5.45 ms
64 bytes from 192.168.2.1: icmp_seq=48 ttl=64 time=86.9 ms
64 bytes from 192.168.2.1: icmp_seq=49 ttl=64 time=22.5 ms
64 bytes from 192.168.2.1: icmp_seq=50 ttl=64 time=1.35 ms


I think is very rare, but can I do anythhing else?

Thank you very much.

---

### Post by akyra on 2009-09-29
Hi Chili555

Two weeks ago, I spoke to Belkin support, and today they send me an e-mail with a link to download a new firmware for the router.
This afternoon I've installed the new firmware and..., surprise, the ping answer was inmediatly!!!!, but the speed was the same 60Mb/s just 20inch from the router.

Now I'm about 10m from the router and the speed is reduced until 36Mb/s. Do you know why? It's possible to increase the connection speed?

> jordi@jordi-ubuntu:~$ ping 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=7.91 ms
64 bytes from 192.168.2.1: icmp_seq=2 ttl=64 time=4.97 ms
64 bytes from 192.168.2.1: icmp_seq=3 ttl=64 time=11.5 ms
64 bytes from 192.168.2.1: icmp_seq=4 ttl=64 time=11.9 ms
64 bytes from 192.168.2.1: icmp_seq=5 ttl=64 time=2.37 ms
64 bytes from 192.168.2.1: icmp_seq=6 ttl=64 time=8.36 ms
64 bytes from 192.168.2.1: icmp_seq=7 ttl=64 time=38.6 ms
^C
--- 192.168.2.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6008ms
rtt min/avg/max/mdev = 2.379/12.249/38.632/11.218 ms
jordi@jordi-ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Jordi_Belkin_N1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:C6:1C:F8   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thank you very much

---

### Post by akyra on 2009-09-29
I've tested the conexion with Windows Vista and the speeds is 5,5Mbs
I think that is very slow.

I'll ask to Belkin.

---

### Post by PatrickVogeli on 2009-09-29
[http://ubuntuforums.org/showthread.php?t=1266806&page=2](http://ubuntuforums.org/showthread.php?t=1266806&page=2)

---

### Post by chili555 on 2009-09-29
> Do you know why?No.>  It's possible to increase the connection speed?Not that I know of on the computer end. Your transmit power is already at the maximum, as far as I know, 15 dBm. You might look around in the router's configuration to see if there is a power setting that you can adjust. You might also try different channels in the router to see if that helps.

---

### Post by akyra on 2009-09-30
Hi all

Yesterday I had connected a wifi printer to the router, and it's possible that the speed was decreased.

Now I'm connected, and the speed is 60Mbps (the same speed that windows vista), and I don't know why, but I'm in contact with Belkin to ask them.

Note.- Can someone put "SOLVED".

Thank you very much.

---

### Post by retskrad on 2011-01-20
I have this problem to, anybody knows an answer?

---

