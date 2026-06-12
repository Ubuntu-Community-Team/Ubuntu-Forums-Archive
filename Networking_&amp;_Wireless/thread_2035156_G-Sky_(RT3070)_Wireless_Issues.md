---
title: "G-Sky (RT3070) Wireless Issues"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by ctownstud00 on 2012-07-30
I have been searching and reading for days, now. I have gained some ground on this thing (thanks Chili555), but I haven't solved everything, yet. Please help!!

I am using a G-Sky USB Wireless N Card, with the RT3070 chipset inside. I am running Ubuntu 10.04 Netbook Edition, but I run in Gnome, not the Netbook mode.

First, when I plugged in the USB wireless card, it was recognized, but no APs would show up. I did some research and found out that I should blacklist rt2800usb and that rt2870sta was built in to the kernel. This got things rolling, as it recognized APs and could connect to UNENCRYPTED networks (which, obviously brings us to the next issue).

Then, I attempted to get encrypted networks going, and so I did some more research and, at this point, I downloaded the latest Ralink driver for the RT3070. I edited os/linux/config.mk to say "Yes" for WPA support, and tried to compile the driver with $make and $make install, but I received errors right away, without the appearance of much happening. [COLOR=Orange][EDIT: I may have done something else that I read somewhere in one of the numerous tutorials and forum threats that I read, but if I did, I do not recall what it was!][/COLOR] I rebooted and was able to connect to encrypted networks--I was feeling good about this, and I thought I had solved everything, but then, I noticed that the connection bit rate was lower than anticipated for a Wireless N network (only 54MBps).

Now, I have been attempting to solve this issue with various methods, and I feel that the driver is not compiling itself correctly, and that I am relying on the included "staging" driver. When checking the version on terminal, it tells me that it is older than I expected, so this reaffirmed my suspicion.

```
~$ modinfo rt2870sta | grep -i version
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32-41-generic SMP mod_unload modversions 586 

```and

```
~$ dmesg | grep -i rt2
[   15.318717] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.377559] usbcore: registered new interface driver rt2870

```Here is what the error looks like when I try to run $make and $make install:
```

:~/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO$ make
make -C tools
make[1]: Entering directory `/home/xxx/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: gcc: Command not found
make[1]: *** [all] Error 127
make[1]: Leaving directory `/home/xxx/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/tools'
make: *** [build_tools] Error 2
```and

```
~/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO$ sudo make install
[sudo] password for xxx: 
make -C /home/xxx/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/xxx/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/xxx/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/
install: cannot stat `rt5370sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/xxx/Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO/os/linux'
make: *** [install] Error 2
```I noticed in the README_STA_usb file included with the latest driver files, the following:

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

Since it was returning errors about gcc when I was running $make and $make install, I thought that, perhaps I had to specify the location of gcc (I have no idea what gcc is, I am NOT familiar with debian stuff very much, I am an old Windows user); however, I am unsure WHERE in the os/linux/config.mk file to specify this, so I am, again, stumped.

To sum things up, I have the card working, connecting to encrypted networks, but not at Wireless N speeds. PLEASE PLEASE PLEASE help, my brain is FRIED!!!

Thanks kindly,
Sean

---

### Post by chili555 on 2012-07-30
> make[1]: gcc: Command not foundThat usually means that all the build tools are not installed. Please do:```
sudo apt-get install build-essential linux-headers-generic
```> make[1]: *** [all] [COLOR="Red"]Error[/COLOR] 127When you see this at *make*, there is no useful purpose in proceeding to *make install*, it will be an error, too. 

After you have installed build-essential and headers, please do:```
cd Downloads/2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO
sudo su
make
make install
modprobe -r rt2870sta
modprobe rt2870sta
exit
```Many a forum post has been written and answered about getting N speeds out of rt2870sta. It seems to depend on your astrological sign and the phase of the moon. You may or you may not and I have no explanation why.

---

### Post by ctownstud00 on 2012-07-31
Chili, you were correct, I had apparently not installed build-essentials, and, even though I forgot to write about it in my initial posting, I do remember downloading something (what I thought was build-essentials) before trying to install the driver. Also, I already had the latest headers.

I was able to run the $make and $make install after installing build-essentials; however, I still am only noticing G speeds. =( Also, I'm noticing that the version still reads 2.0.1.0, instead of 2.5.0.3, as I believe it should.

```
$ modinfo rt2870sta | grep -i version
version:        2.0.1.0
srcversion:     169A56F8E0E6AA9C2B2FD02
vermagic:       2.6.32-41-generic SMP mod_unload modversions 586 

```

Also, I am having an issue with the names of my wireless connections.

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"xxx"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.422 GHz  Access Point: xxx   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-55 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1_rename  IEEE 802.11bg  ESSID:"xxx"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

I would like the wlan0 to be named ra0 and I would like the wlan1_rename to be named wlan0.

Also, I would like to disable the wlan0 connection by default, unless I specify it to be on in the terminal, with, for example, $ifconfig wlan0 up. I know it's not the original issue, but is this possible?

---

### Post by chili555 on 2012-07-31
Wow! This is a bit complicated.> Also, I would like to disable the wlan0 connection by default, unless I specify it to be on in the terminal, with, for example, $ifconfig wlan0 up. I know it's not the original issue, but is this possible? Do you have two wireless devices? Did you forget to tell old Chili a thing or two? >  Also, I'm noticing that the version still reads 2.0.1.0, instead of 2.5.0.3, as I believe it should.Do you think this file builds a driver rt2870sta? I don't:> 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPOI think it builds a driver rt5370sta. Please check what's loaded:```
lsmod | grep -e rt2 -e rt3 -e rt5
```Hmmmm:> install -m 644 -c [COLOR="Red"]rt5370sta[/COLOR].ko /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/

---

### Post by ctownstud00 on 2012-07-31
Chili, yes, I have two wireless devices. One is internal in my netbook and the other is the USB plug-in device. The internal device, I plan to use as a soft wireless AP, which will repeat whatever network I connect to with the USB device. (I know that's not the original problem, that is just my overall goal here, so, perhaps we should forget about making the internal device stay off at boot.)

$lsmod command returns the following:
```
# lsmod | grep -e rt2 -e rt3 -e rt5
rt2870sta             461811  1 

```

And, yes, I thought I was building a RT2870sta driver! Also worth mentioning; I am seeing some errors on boot, mentioning something about failures loading the rt2870sta driver due to something already having claimed it or something like that.. I'm unsure how to check the boot screen logs to copy it for you, and it appears rather quickly, so it's difficult to read...

Thanks for your help thus far, I was hoping I could grab your attention on this one,
Sean

---

### Post by chili555 on 2012-07-31
> something about failures loading the rt2870sta driver due to something already having claimed it or something like that.. I'm unsure how to check the boot screen logs to copy it for you,You can scroll through dmesg:```
dmesg | less
```Use the arrow keys until you see the offending messages. I suspect it will be near the end. 

I wonder if rt2870sta is loading automatically. Please show me:```
cat /etc/modules
cat /etc/udev/rules.d/network_drivers.rules
cat /etc/modprobe.d/network_drivers.conf
```Also, tell me if there are any interesting messages if you do:```
sudo modprobe -r rt2870sta
sudo modprobe rt5370sta
```Thanks.

---

### Post by ctownstud00 on 2012-07-31
Chili, thanks again for your continued assistance.

Here are a couple of lines I'm seeing in red at the Ubuntu startup screen (before the login screen appears):

```
[   15.657264] acer-wmi: Unable to detect available WMID devices
[   15.915023] Error: Driver 'rt2870' is already registered, aborting...
[   15.915193] usbcore: error -16 registering interface         driver rt2870

```

Here are the results of the $cat commands:

```
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
$ cat /etc/udev/rules.d/network_drivers.rules
cat: /etc/udev/rules.d/network_drivers.rules: No such file or directory
$ cat /etc/modprobe.d/network_drivers.conf
cat: /etc/modprobe.d/network_drivers.conf: No such file or directory

```

The wireless card is being used for Internet access right now, so when I try to $modprobe -r rt2870sta, it returns with a fatal error, that the module is in use. I used $ifconfig wlan0 down to turn off the module, then the $modprobe -r rt2870sta was able to work, it appears.

```
$ sudo modprobe -r rt2870sta
FATAL: Module rt2870sta is in use.
$ sudo ifconfig wlan0 down
$ sudo modprobe -r rt2870sta
$ sudo modprobe rt5370sta

```

I reconnected to the wireless network I was on, and it connected OK; however, when I tried to access the Internet via a web browser, it just sat there, trying to load. Therefore, I attempted to revert back to the rt2870sta module for the time being, but something funny happened. Check it out:

```
$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1_rename  IEEE 802.11bg  Mode:Master  Frequency:2.422 GHz  Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr=2347 B   Fragment thr=2346 B  
          Power Management:off
         
mon.wlan1_renam  IEEE 802.11bg  Mode:Monitor  Frequency:2.422 GHz  Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr=2347 B   Fragment thr=2346 B  
          Power Management:off
         
ra0       Ralink STA  ESSID:"Coshocton_County"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:15:F9:39:2D:C0  
          Bit Rate=54 Mb/s  
          RTS thr:off   Fragment thr:off
          Link Quality=90/100  Signal level:-53 dBm  Noise level:-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

It named the Ralink properly (I wanted it to be ra0), but now the "Nickname" shows differently. Before (when using the rt2870sta module), it read "RT3070STA."

I managed to load the rt2870sta module instead of the rt5370sta module and restarted. The computer restarted EXTREMELY slowly, hanging between each step of booting, and gave me some errors about USB devices. My USB wireless mouse wouldn't work (at the login screen), so I unplugged it and restarted the machine again. Still VERY slow to boot, but without the errors this time (still errors for WMID devices, though). Hopefully this reply will provide some useful clues / information for helping remedy my issue(s)!!!

---

### Post by chili555 on 2012-07-31
Let's blacklist rt2870sta and see if we improve things:```
sudo su
echo "blacklist rt2870sta" >> /etc/modprobe.d/blacklist.conf
exit
```Please reboot and let me see:```
lsusb
```Thanks.

---

### Post by ctownstud00 on 2012-07-31
Blacklisted rt2870sta. Rebooted.

```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Internet access working at N speeds. Correctly named ra0.

```
ra0       Ralink STA  ESSID:"collinandadamrule"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.422 GHz  Access Point: E0:46:9A:4C:CE:C2   
          Bit Rate=135 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-57 dBm  Noise level:-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

What's going on, here?? =)

---

### Post by chili555 on 2012-08-01
What's going on here?? I think it's solved.

The rt5370sta module was built upon the rt2870sta code, modified extensively, of course. Somewhere deep in the C code is the meaningless 'Nickname:"RT2870STA".' I don't think it's significant in any way.

Enjoy!

---

### Post by ctownstud00 on 2012-08-01
Thanks, Chili, now, jump over to my other thread about creating a soft wireless AP and help!! hahaha =)

---

### Post by ctownstud00 on 2012-08-24
I upgraded to the newest kernel / headers or whatever in Ubuntu Netbook Edition 10.04, and my Ralink card is not being recognized. It shows under $lsusb, but it doesn't show up with $iwconfig or $ifconfig. I don't want to mess up the soft wireless AP I set up, so I was hoping that someone could direct me as to the best way to get that functioning again. I booted in the penultimate kernel that I had been working in during this thread and it worked OK, but I want it to be working in the most up-to-date kernel as well. Can anyone guide me, please?

---

### Post by chili555 on 2012-08-24
When you get a newer kernel, you need to recompile for the later one; something like:```
cd Desktop/RT5370file  [COLOR="Red"]<--or wherever you extracted the files[/COLOR]
sudo su
make cleean
make
make install 
modprobe rt5370sta
exit
```

---

### Post by ctownstud00 on 2012-08-25
> **chili555 said:**
> When you get a newer kernel, you need to recompile for the later one; something like:```
cd Desktop/RT5370file  [COLOR=Red]<--or wherever you extracted the files[/COLOR]
sudo su
make cleean
make
make install 
modprobe rt5370sta
exit
```

So, in lamen's terms, just re-install the driver on the new kernel? I'll give this a try. Thanks, Chili, you're a coffee cup full of help! =)

---

### Post by chili555 on 2012-08-25
> So, in lamen's terms, just re-install the driver on the new kernel? In layman's terms, exactly. And remember to do so for each and every newer kernel. Thanks for your kind words.

---

