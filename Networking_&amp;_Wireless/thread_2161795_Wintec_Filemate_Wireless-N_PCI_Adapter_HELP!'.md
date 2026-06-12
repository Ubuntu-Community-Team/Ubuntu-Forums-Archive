---
title: "Wintec Filemate Wireless-N PCI Adapter HELP!'"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by jammerxd on 2013-07-12
Hello,
I recently purchased and installed the Wintec Filemate Wireless-N PCI Adapter and to my dismay it refused to work with ubuntu. I went to the manufactuerer's website and downloaded the official driver for ubuntu linux. The only trouble is, IT DOESN'T WORK! I followed the instructions in the included readme:

INFO ABOUT MY SETUP:
OS: Ubuntu Server 13.04
PCI Card Model: 3FMPCIMWN-R

--------------------------RAW TEXT FROM README:------------------------------
Runing the scripts accomplish all operations including building up modules 
from the source code, installing driver to the kernel and starting up the nic.
    1. Build up the drivers from the source code
      make


    2. Install the driver to the kernel
          make install
          reboot


    3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
      ifconfig wlan0 up 
      Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name, 
                since it may change wlan0 to wlan1,etc.
And I still get an error 2 when I try to even run the first command("sudo make"). Obviously I am running server edition of Ubuntu and want to keep it that way. This is the following output of the first instruction:

------------END RAW TEXT---------------------

------------BEGIN OUTPUT---------------------

jammerxd@JAMMERD:~/linux_driver2$ make
make[1]: Entering directory `/usr/src/linux-headers-3.8.0-19-generic'
  CC [M]  /home/jammerxd/linux_driver2/ieee80211/ieee80211_rx.o
In file included from /home/jammerxd/linux_driver2/ieee80211/ieee80211_rx.c:45:0:
/home/jammerxd/linux_driver2/ieee80211/ieee80211.h:2279:24: error: field 'ps_task' has inclomplete type
/home/jammerxd/linux_driver2/ieee80211/ieee80211_rx.c: In function 'ieee80211_rx_mgt_rsl':
/home/jammerxd/linux_driver2/ieee80211/ieee80211_rx.c:3012:17: error: implicit declaration of function 'tasklet_schedule' [-Werr
or=implicit-function-declaration]
cc1: some warnings being treated as errors
make[2]: *** [/home/jammerxd/linux_driver2/ieee80211/ieee80211_rx.o] Error 1
make[1]: *** [_module_/home/jammerxd/linux_driver2/ieee80211] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-3.8.0-190generic'
make: *** [all] Error 2


-----------END OUTPUT------------------
Can anyone help me and tell me why this is happening? These files were downloaded directly from the manufacturer website!

---

### Post by kurt18947 on 2013-07-12
How about posting the output of this command?

```
lspci
```?

The output will look similar to this:

```
Bus 002 Device 002: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

```
This will tell us which chipset is used in your device.  Did you happen to install your device and start your machine to see if your device was recognized?  For devices/chipsets that have been around for a while this is sometimes all that is required.   There are wireless wizards on this forum. I am not one but knowing the chipset in question is a good first step.

---

### Post by jammerxd on 2013-07-12
That commande lists all the pci devices installed on my system. The one we are interested in(the wintec pci card) is as follows:

02:0b.0 Network Controller: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN

This means that my chipset is the Realtek 8190.

---

### Post by kurt18947 on 2013-07-12
> **jammerxd said:**
> That commande lists all the pci devices installed on my system. The one we are interested in(the wintec pci card) is as follows:

02:0b.0 Network Controller: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN

This means that my chipset is the Realtek 8190.

That's it.  Here's what one of my favorite reference sites says about that chip set.  It doesn't show the WinTec but does show a Trendnet TEW-6432PI using the same chipset.  It looks like the open source Linux driver for this chipset is [B][COLOR=brown]r8190_pci

[/COLOR][/B][http://wikidevi.com/wiki/TRENDnet_TEW-641PC](http://wikidevi.com/wiki/TRENDnet_TEW-641PC)

Does that module show up in the command "lsmod"?  A concern I would have with drivers included on a CD is compatibility with newer linux distros.  For instance, the RealTek driver for a favorite USB wifi adapter worked great until 12.10.  RealTek has not updated their driver for this device to work  on 13.04 or 13.10.  I did a cursory search in the wireless forum and don't find any reference to that chipset after about 2010.  What I did find was using NDISwrapper which I am not at all knowledgeable about.  Perhaps someone more conversant with NDISwrapper will pick up.  It might be interesting to run the command "iwconfig" just to see if there's a wireless card found.  Do bear in mind that Ubuntu will not usually use a wireless network connection if there's a wired connection so if you have an ethernet cable plugged in, you would probably need to unplug and probably reboot to see if there's any wireless activity.

edit:  Hmmm, I did "modinfo" for r8190_pci and got nothing back.  I wonder if that module is not included by default?  I would probably do some poking with backports and see if I could load the appropriate software that way.

---

### Post by jammerxd on 2013-07-12
"lsmod" does not list any modules involving r8190_pci. Also, iwconfig does not show any wireless cards installed! Please tell me how to get this card working!

---

### Post by wildmanne39 on 2013-07-12
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by jammerxd on 2013-07-12
Just to clarify: I am using Ubuntu Server which means NO GUI OR Desktop Environment! I will post the results in a moment.

---

### Post by jammerxd on 2013-07-12
Here are the results

---

### Post by jammerxd on 2013-07-12
Here are the result cont'd.

---

### Post by jammerxd on 2013-07-12
Here are the results cont'd.

---

### Post by jammerxd on 2013-07-12
Here is the last result

---

### Post by wildmanne39 on 2013-07-12
I have been researching the driver you need and it does not exist for linux.

The only way you might get this device to work is with ndiswrapper but I have not seen any threads solved using it either.

I do know that in almost all cases you have to use the winxp driver to get it to work with ndiswrapper.

I do not have access to winxp drivers so I am afraid I can not help you with ndiswrapper.

Here is a link with directions:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jammerxd on 2013-07-12
I have the winxp driver, it came on the setup disc! I will try it and report back!

---

### Post by jammerxd on 2013-07-12
Yesssssssss!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! I can confirm that i got my card working in ubuntu linux!
Again this is the wintec filemate pci wireless n adapter! I pulled the winxp drivers from the cd and used ndiswrapper and it worked!

---

### Post by wildmanne39 on 2013-07-12
That is great!!! Do you use 32bit driver or 64 bit driver?

Can you attach the driver files here for everyone's benefit?
Thanks

---

### Post by jammerxd on 2013-07-13
I personally used the x86 drivers as that is the version of linux I am running. 
Okay, for the drivers, you need to download either the x86(32bit) or x64(64bit) version of the drivers(as indicated by the name of the zip file). For reference, I followed these steps taken from another topic in this forum to install the driver itself: 

[COLOR=#000000]I have used this tutorial here:[/COLOR]
[https://help.ubuntu.com/community/Wi...eisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")


[COLOR=#000000]The commands, used on Ubuntu 9.10 were:[/COLOR]

**[B][B]Step 1:- Install NDISWrapper and Blacklist Native Driver**[/B]
echo -e 'blacklist rtl8190\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/rtl8190; cd ~/rtl8190
[B][B][B]
Step 2: Copy [/B][/B]"rtl8190p.sys" and "net8190.inf" to ~/rtl8190

[B]Step 3: Configure NDISWrapper (and WPA Supplicant)
sudo ndiswrapper -i net8190.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

CONFIRMED WORKING IN UBUNTU 13.04![/B][/B][/B]

---

### Post by jammerxd on 2013-07-13
Now the only trouble is that I cannot connect to any wifi networks at all. Just to prove it, I installed a desktop environment(LXDE) and tried to connect via the gui. The network was open and had no password and linux failed to connect. I have no idea why, I would get stuck at obtaining an ip address and then it would stop trying to get one. I even tried setting a static ip address but it still wouldn't connect. I also tried using terminal, the gui(network-manager), and wicd to connect, no good. I also tried connecting to the network with our normal password(WPA2) and that did not work as wicd and everyone else gave me the bad password error. I also tried the security down to WPA only and nada! Nothing seems to be working. Also, running the command: dmesg | grep -e ndis -e wlan
 
Brings all these errors out: 

```
[  771.610439] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.625882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.642743] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.655064] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.669991] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.686114] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.702858] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.722685] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.738112] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.754539] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.776100] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.787266] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.806419] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.822428] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.842108] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.854572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.878658] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.890655] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.902792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.922690] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.942394] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.954455] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.971505] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  771.986808] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.002423] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.014500] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.026764] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.046702] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.063387] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.074734] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.086740] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.102431] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.118521] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.164623] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.175383] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.189750] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.205705] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.222720] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.237932] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.250612] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.266641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.290408] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.302502] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.325916] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.345869] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.358515] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.381947] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.398610] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.410742] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.422842] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.437862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.454443] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.470061] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.482734] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.502686] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.522713] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.542660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.554449] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.569886] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.606768] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.618724] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.638678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.658578] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.682679] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.704674] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.732303] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.747078] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.758335] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.773920] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.805651] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.817989] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.838637] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.850442] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.882654] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.905852] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.929675] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.946664] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.970584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.982501] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  772.997854] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.013943] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.029557] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.040482] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.054749] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.069735] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.094119] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.106574] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.123811] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.138727] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.161903] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.178026] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.190432] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.210392] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.234416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.246741] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.271675] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.283521] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.294747] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.306806] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.327783] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.345975] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.357981] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.374322] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.397727] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.421898] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.442432] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.454765] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.469548] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.482704] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.502693] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.514778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.529730] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.542554] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.554748] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.571271] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.585643] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.597995] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.618421] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.643125] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.657964] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.687730] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.702978] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.714321] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.726389] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.743234] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.754434] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.774854] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.790707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.802788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.822696] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.840397] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.862625] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.877805] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.891023] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.910919] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.930962] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.958890] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.973816] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  773.986981] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.010740] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.022707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.034640] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.050267] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.075417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.090669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.102917] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.118828] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.140355] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.154999] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.166882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.202646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.214808] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.242862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.254426] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.266989] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.294277] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.306700] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.326848] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.354991] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.372915] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.386981] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.418629] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.450930] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.483164] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.523010] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.543547] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.555218] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.579804] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.594948] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.607019] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.626909] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.649820] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.662579] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.678899] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.695708] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.728630] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.742079] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.754728] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.782881] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.793966] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.806569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.822846] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.842833] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.865646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.882483] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.914512] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.934402] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.946402] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.958402] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.973727] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  774.998685] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.010771] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.033910] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.074643] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.094073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.118441] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.138678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.149973] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.162556] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.182585] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.194427] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.213945] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.226742] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.250024] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.273773] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.298468] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.314726] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.337310] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.349944] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.362565] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.380398] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.391624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.405945] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.418557] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.443083] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.458735] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.473934] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.489937] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.502512] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.517800] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.530460] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.553645] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.569984] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.594710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.614451] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.626797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.646617] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.671092] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.686417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.710788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.734458] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.750490] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.762744] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.786556] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.798802] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.818686] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.837388] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.848106] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.861865] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.873675] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.890502] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.914757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.934692] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.954395] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  775.970323] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.002577] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.018704] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.030792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.042370] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.071507] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.125312] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.145016] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.169452] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.197115] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.214440] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.234752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.261788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.289624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.318506] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.336861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.376583] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.411577] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.429877] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.442432] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.465622] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.490337] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.514559] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.526711] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.549907] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.562329] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.598742] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.610464] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.634440] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.654777] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.677887] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.719936] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.734007] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.746883] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.758582] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.778585] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.794461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.806746] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.826473] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.845971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.858678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.878678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.895758] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.909837] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.922781] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.945640] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.958367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.973926] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  776.994566] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.006646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.021788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.034573] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.049908] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.062378] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.077846] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.098369] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.110748] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.133683] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.146032] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.158474] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.182779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.198228] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.210002] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.222568] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.246767] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.266680] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.278439] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.298102] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.310591] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.326682] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.354707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.377921] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.388956] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.413742] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.426755] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.442537] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.454797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.470770] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.482804] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.502783] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.522719] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.542474] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.554801] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.566803] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.581919] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.598523] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.613937] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.626795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.649885] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.666518] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.681886] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.702708] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.725588] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.738455] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.753764] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.766733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.778799] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.803186] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.814710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.826756] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.847671] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.858882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.882608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.900168] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.910664] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.930412] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.942464] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.962518] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  777.985893] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.002520] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.025608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.050446] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.062460] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.082424] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.095095] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.110503] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.122539] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.134742] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.149802] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.162427] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.182792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.194636] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.214102] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.226588] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.241883] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.265878] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.282542] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.301705] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.314795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.342490] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.365627] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.394728] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.410518] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.437639] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.449624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.462254] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.474464] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.486692] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.506868] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.518667] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.541656] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.554375] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.566420] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.578419] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.590754] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.606784] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.630793] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.642461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.657882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.670759] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.701404] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.738410] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.750498] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.762755] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.777935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.798437] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.810733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.826607] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.846600] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.858728] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.878688] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.890769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.913891] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.930133] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.953887] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.966724] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.978374] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  778.997841] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.010506] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.034765] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.054676] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.077862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.098676] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.114689] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.129246] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.142484] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.158471] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.170929] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.189417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.202942] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.218217] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.238823] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.254757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.270929] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.283219] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.294781] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.309994] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.326539] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.346111] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.358818] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.370784] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.386212] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.419445] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.438505] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.450091] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.466101] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.478564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.490990] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.510737] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.531092] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.541803] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.558416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.570726] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.590788] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.602902] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.618324] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.634299] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.650095] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.662794] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.674849] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.699216] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.710782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.722923] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.742748] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.754822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.770085] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.803612] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.818851] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.836070] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.854779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.875963] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.891976] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.923792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.942660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.955408] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.966739] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.979129] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  779.996643] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.011558] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.028139] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.051435] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.062871] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.075180] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.092214] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.103821] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.123924] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.142849] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.155325] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.179227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.198971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.211294] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.232690] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.246984] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.258932] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.282862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.307050] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.326678] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.350620] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.368903] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.388217] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.399760] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.410880] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.431496] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.446695] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.467360] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.478649] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.496479] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.517797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.531130] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.555036] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.569934] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.587176] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.598911] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.618831] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.638641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.650690] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.662041] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.682906] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.708561] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.731524] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.746577] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.758426] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.789474] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.802759] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.822957] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.845051] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.858504] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.886686] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.902425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.914927] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.937774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.955848] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.974687] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  780.986632] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.006573] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.023849] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.038093] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.050767] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.073893] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.086342] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.098760] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.110784] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.122787] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.141324] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.154730] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.174456] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.195117] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.210465] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.233935] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.254787] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.266562] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.294519] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.306774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.318574] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.350526] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.365773] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.378771] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.398685] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.418436] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.430729] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.448510] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.459142] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.473732] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.489820] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.505908] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.526754] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.550579] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.566056] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.582791] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.609558] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.630784] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.654642] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.674514] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.688111] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.706035] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.718554] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.741632] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.758826] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.770633] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.793889] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.806716] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.822489] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.859142] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.875062] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.894402] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.909052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.922618] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.934733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.946790] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.961613] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.974696] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.986769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  781.998781] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.013953] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.037917] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.051053] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.069729] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.090774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.110600] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.134546] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.147367] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.170007] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.183875] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.197882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.226583] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.239051] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.250377] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.290310] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.305764] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.322453] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.338336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.370860] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.390531] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.407797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.419494] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.436186] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.450757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.466037] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.481915] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.494525] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.517874] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.530668] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.554603] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.570727] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.585949] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.609656] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.621960] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.634552] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.650469] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.672523] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.709417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.735052] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.747663] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.768214] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.782593] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.794758] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.817823] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.830260] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.850568] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.882578] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.902759] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.923214] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.934425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.960640] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.976578] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  782.990715] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.005659] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.018619] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.038675] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.050567] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.065737] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.078702] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.101913] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.122660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.142684] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.162575] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.185817] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.203452] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.222515] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.239682] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.251755] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.271739] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.285895] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.301882] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.318936] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.330715] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.348522] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.364978] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.378614] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.410372] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.422757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.445688] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.460110] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.478794] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.500698] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.515683] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.536916] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.561762] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.586983] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.602312] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.622513] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.634502] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.651362] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.666744] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.682167] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.702812] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.746774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.769573] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.785929] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.798561] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.821674] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.832139] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.850401] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.870800] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.885942] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.902782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.918491] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.930913] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.946174] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.962191] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.978266] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  783.994336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.014815] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.027081] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.041675] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.053931] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.069355] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.085605] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.100914] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.115319] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.130643] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.146056] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.163084] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.182775] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.198792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.214783] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.230433] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.243111] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.261769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.278084] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.290913] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.309816] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.330792] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.350579] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.362667] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.378797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.390861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.402905] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.418157] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.442314] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.454779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.474793] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.494712] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.510770] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.530716] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.550417] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.562503] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.577963] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.598467] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.609995] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.626566] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.641682] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.661907] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.676325] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.698004] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.747380] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.775691] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.794302] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.840088] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.869400] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.895133] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.920074] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.943378] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.972564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  784.998861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.018569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.035973] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.052373] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.065239] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.086817] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.102624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.118785] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.130893] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.146842] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.164390] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.182255] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.198389] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.218225] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.245126] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.262782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.284793] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.309222] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.326789] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.338841] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.358117] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.374795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.394471] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.410856] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.426624] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.438591] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.454560] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.467043] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.486797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.502527] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.515250] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.526963] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.543461] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.555183] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.570448] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.603070] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.614458] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.626753] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.646605] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.678794] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.702314] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.726481] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.742037] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.762669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.779322] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.806569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.836102] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.860535] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.875874] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.900121] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.918722] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.934764] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.950665] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.966733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.986959] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  785.998958] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.030877] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.054646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.078877] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.093522] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.114647] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.126959] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.146654] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.158615] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.178542] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.194858] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.214991] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.245321] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.274703] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.294783] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.314871] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.326797] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.349843] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.383568] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.398900] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.411025] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.422794] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.438295] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.458681] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.470923] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.491039] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.506352] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.534677] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.546923] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.574949] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.594718] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.611277] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.630831] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.646684] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.662474] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.678923] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.707688] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.738634] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.754040] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.766576] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.790357] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.810751] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.826409] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.850877] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.865798] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.888861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.902470] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.925927] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.958481] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.973930] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  786.991721] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.010769] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.022199] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.044584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.058761] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.075573] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.087662] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.106604] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.118880] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.133822] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.146409] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.158355] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.182470] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.196987] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.210555] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.226378] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.237899] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.254944] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.274018] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.294805] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.306603] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.322111] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.334130] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.355189] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.366342] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.391996] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.405976] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.422823] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.434763] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.454463] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.473251] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.494147] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.506469] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.518770] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.538729] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.558422] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.574779] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.593961] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.606469] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.620608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.631185] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.645845] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.661730] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.677861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.704193] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.718707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.734760] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.751695] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.762787] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.774774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.789895] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.803918] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.814971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.826396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.838744] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.857695] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.870727] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.882453] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.902500] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.926889] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.941902] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.969683] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  787.981662] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.010587] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.030036] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.046575] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.062580] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.086563] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.101630] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.117881] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.133551] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.146775] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.166673] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.178778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.202430] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.214451] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.229850] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.246505] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.258768] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.290046] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.310416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.326891] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.338753] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.365931] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.378501] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.390786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.405808] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.430765] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.450743] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.464620] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.475413] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.486744] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.506787] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.526697] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.538710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.553835] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.574396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.586739] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.614563] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.635125] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.654516] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.666513] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.691956] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.726714] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.746576] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.766466] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.778620] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.798743] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.822714] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.837817] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.858915] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.886795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.902753] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.934475] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.952086] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.966785] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  788.983814] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.002447] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.017608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.042582] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.054740] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.077874] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.098426] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.118425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.137830] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.158529] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.174554] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.195061] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.214674] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.242607] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.259583] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.274063] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.294757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.309876] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.330488] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.348158] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.376943] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.412419] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.431419] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.460835] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.485035] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.504228] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  789.537752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  962.777685] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  962.797329] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  962.904096] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
```


Any ideas what might be wrong?

---

### Post by wildmanne39 on 2013-07-13
Please post the output of:
```
sudo cat /var/log/syslog | grep -e rtl -e ndis -e firmware -e wlan -e wpa -e etork | tail -n45
```
```
iwconfig
rfkill list all
lsmod
```
You said you went to the manufacturer's website and download the linux driver for your device, please give link?
Please use code tags.

---

### Post by jammerxd on 2013-07-13
Okay, here is the system log: 
```
Jul 13 12:39:43 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 (xid=0xaa2a1e0)Jul 13 12:39:55 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0xaa2a1e0)
Jul 13 12:40:05 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0xaa2a1e0)
Jul 13 12:40:23 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0xaa2a1e0)
Jul 13 12:40:36 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0xaa2a1e0)
Jul 13 12:40:49 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0xaa2a1e0)
Jul 13 12:41:07 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0xaa2a1e0)
Jul 13 12:41:28 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 (xid=0xaa2a1e0)
Jul 13 12:41:46 JAMMERXD dhclient: Listening on LPF/wlan0/00:08:54:a2:d9:49
Jul 13 12:41:46 JAMMERXD dhclient: Sending on   LPF/wlan0/00:08:54:a2:d9:49
Jul 13 12:41:46 JAMMERXD dhclient: receive_packet failed on wlan0: Network is down
Jul 13 12:41:46 JAMMERXD kernel: [  231.339823] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 13 12:41:49 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17 (xid=0xaa2a1e0)
Jul 13 12:41:56 JAMMERXD dhclient: receive_packet failed on wlan0: Network is down
Jul 13 12:41:56 JAMMERXD dhclient: Listening on LPF/wlan0/00:08:54:a2:d9:49
Jul 13 12:41:56 JAMMERXD dhclient: Sending on   LPF/wlan0/00:08:54:a2:d9:49
Jul 13 12:41:56 JAMMERXD kernel: [  241.797701] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 13 12:42:06 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0xaa2a1e0)
Jul 13 12:42:24 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0xaa2a1e0)
Jul 13 12:42:31 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14 (xid=0xaa2a1e0)
Jul 13 12:42:34 JAMMERXD dhclient: Listening on LPF/wlan0/00:08:54:a2:d9:49
Jul 13 12:42:34 JAMMERXD dhclient: Sending on   LPF/wlan0/00:08:54:a2:d9:49
Jul 13 12:42:34 JAMMERXD dhclient: receive_packet failed on wlan0: Network is down
Jul 13 12:42:34 JAMMERXD kernel: [  279.363420] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 13 12:42:34 JAMMERXD dhclient: receive_packet failed on wlan0: Network is down
Jul 13 12:42:45 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19 (xid=0xaa2a1e0)
Jul 13 12:42:45 JAMMERXD dhclient: dhclient.c:1996: Failed to send 300 byte long packet over wlan0 interface.
Jul 13 12:43:04 JAMMERXD dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0xaa2a1e0)
Jul 13 12:43:04 JAMMERXD dhclient: dhclient.c:1996: Failed to send 300 byte long packet over wlan0 interface.
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-3-ethernet
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-3-ethernet, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]:    SCPlugin-Ifupdown: adding wlan0 to iface_connections
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]:    SCPlugin-Ifupdown: adding iface wlan0 to well_known_interfaces
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0b.0/net/wlan0, iface: wlan0)
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]: <info> (wlan0): using WEXT for WiFi device control
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]: <error> [1373737392.268316] [nm-device-wifi.c:2841] update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 0)
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]: <info> (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 3)
Jul 13 12:43:12 JAMMERXD NetworkManager[2637]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 13 12:43:57 JAMMERXD dhclient: Listening on LPF/wlan0/00:08:54:a2:d9:49
Jul 13 12:43:57 JAMMERXD dhclient: Sending on   LPF/wlan0/00:08:54:a2:d9:49
Jul 13 12:43:57 JAMMERXD kernel: [  362.165858] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 13 12:43:57 JAMMERXD dhclient: receive_packet failed on wlan0: Network is down
Jul 13 12:43:57 JAMMERXD kernel: [  362.182757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready



```

---

### Post by jammerxd on 2013-07-13
iwconfig```
wlan0     IEEE 802.11g  ESSID:off/any            Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:65 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.



```

```
rfkill list all 
``` did not do anything.
lsmod:
```
Module                  Size  Used bynls_iso8859_1          12617  1 
nls_utf8               12493  1 
isofs                  39211  1 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
nouveau               834513  2 
mxm_wmi                12893  1 nouveau
wmi                    18590  2 mxm_wmi,nouveau
video                  18894  1 nouveau
ttm                    71289  1 nouveau
drm_kms_helper         47545  1 nouveau
drm                   228750  4 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13197  1 nouveau
hid_generic            12484  0 
usbhid                 41805  0 
snd_intel8x0           33096  2 
hid                    82666  2 hid_generic,usbhid
ppdev                  12817  0 
snd_ac97_codec        105692  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
parport_pc             27504  1 
lpc_ich                16925  0 
snd                    56485  11 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
mac_hid                13037  0 
shpchp                 32129  0 
microcode              18286  0 
serio_raw              13031  0 
ndiswrapper           192638  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
soundcore              12600  1 snd
usb_storage            47684  1 
firewire_ohci          35292  0 
firewire_core          61718  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
8139too                23071  0 
8139cp                 26557  0 
floppy                 55441  0 
```

---

### Post by jammerxd on 2013-07-13
Here is the manufacturer page: [http://www.wintecind.com/support_center/support/PCI_wireless.html](http://www.wintecind.com/support_center/support/PCI_wireless.html)

NOTE: The dedicated linux driver does NOT work on linux 13.04! It ONLY works on 8.04 or lower. I have tried to get it working, but it gives me an error(error in the source code) every time I try ```
make
``` and then ```
make install
``` as per the readme. Weather or not I use sudo in it does not make a difference.

---

### Post by wildmanne39 on 2013-07-13
Please post the results of:
```
dmesg | grep ndis 
sudo iwlist wlan0 scan 
sudo iwlist wlan0 auth
```
Thanks

---

### Post by jammerxd on 2013-07-13
I think I am going to start from scratch to be honest. I am going to reinstall ubuntu server 13.04 and then I am going to install lxde(desktop, lightweight) and then I will install the windows xp driver for my wireless card.

---

### Post by wildmanne39 on 2013-07-13
Okay good luck!

It looks like that card has been around for a long time so it is not likely to get any better support in the future.

---

### Post by kurt18947 on 2013-07-13
I did some poking around about this card.  Someone - I didn't bookmark the page - emailed Realtek.  RealTek sent back a linux driver that worked with the RTL-8190 chip.  That might be worth a try.  I don't remember much about the post but I think it was a couple years old.

---

### Post by jammerxd on 2013-07-13
Do you hve the file? Can you email it to me?

---

### Post by kurt18947 on 2013-07-15
> **jammerxd said:**
> Do you hve the file? Can you email it to me?

I do not.  You can email RealTek with your request though.

---

