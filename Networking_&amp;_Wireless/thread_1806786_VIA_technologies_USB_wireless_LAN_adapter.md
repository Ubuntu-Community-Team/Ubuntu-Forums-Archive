---
title: "VIA technologies USB wireless LAN adapter"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by NewNerd99 on 2011-07-18
Hi,
   Currently booting off a disc and I'm unable to connect to our home network.

Do I need to update drivers for this particular card?

The netbook I'm using is a 'Kogan' with an Atom N270 1.6Ghz processor.

Cheers
Chris

---

### Post by chili555 on 2011-07-18
Please open a terminal and run and post:```
lsusb
```Once we identify the card details, we'll be in a better position to proceed.

---

### Post by NewNerd99 on 2011-07-18
Thanks Chilli,

ubuntu@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera
Bus 001 Device 004: ID 160a:3184 VIA Technologies, Inc. VIA VNT-6656 [WiFi 802.11b/g USB Dongle]
Bus 001 Device 003: ID 05dc:a731 Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ubuntu@ubuntu:~$

---

### Post by chili555 on 2011-07-18
> ID 160a:3184 VIA Technologies, Inc. VIA VNT-6656 [WiFi 802.11b/g USB Dongle]This is supposed to work with the module vt6656_stage. Let's load it:```
sudo modprobe vt6656_stage
```And let's see if a wireless interface has been created:```
iwconfig
```Can you click the Network Manager icon and connect, he asks optimistically? If not, let's check for messages:```
dmesg | grep vt66
```

---

### Post by Strike0 on 2011-08-18
Can you click the Network Manager icon and connect, he asks optimistically? If not, let's check for messages:```
dmesg | grep vt66
```[/QUOTE]

Hi, 
seemingly I have exactly the same problem with the vt6656 card. I'm not quoting the output here since I am currently on another PC (but will provide the dmesg later). The vt6656_stage loads fine, the wlans are visible etc. I am running 10.10 on the netbook and with that wlan connections work out of the box and very reliably. 
However, neither with Natty nor the current Oneiric alpha the connection works. The wlan router logs show connection attempts and then the fails. I suspect this has to do with the encryption in either the stage driver or network-manager. I have tried all combinations of WPA/WP2 TKIP/AES though (after reading other posts). 

Any suggestions what I can try else to get the Oneiric wlan connections work with this card?

---

### Post by chili555 on 2011-08-18
> Any suggestions what I can try else to get the Oneiric wlan connections work with this card?You can add to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/807029](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/807029)

We can probably learn a lot from the syslog:```
sudo cat /var/log/syslog | grep -e vt66 -e etwork | tail -n25
```Or, we could try ndiswrapper.

---

### Post by Strike0 on 2011-08-18
> **chili555 said:**
> You can add to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/807029](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/807029)

We can probably learn a lot from the syslog:```
sudo cat /var/log/syslog | grep -e vt66 -e etwork | tail -n25
```Or, we could try ndiswrapper.

Thanks for the quick reply. Enclosed the output from the syslog. At first I stumbled over the errors at the end about "failure to change MAC address to 00:00:..." but in the network manager, the eth1 mac address is shown for the device. Do you get any further hints out the output? 

Also thanks for the bug-reference. In contrast to that case the card actually works with a vanilla maverick install right away here. Not sure what else I can add there, but I will look into it again further. In 10.04 I had to compile the VIA driver, which worked as well though. What would I have to blacklist, if I try that? vt6656_stage ?

---

### Post by chili555 on 2011-08-18
> the card actually works with a vanilla maverick install right away here.That suggests that it's not a Network Manager or vt6656_stage issue, but an Oneiric issue; perhaps in the kernel or networking parts. I'd find a bug tracker for Oneiric and report it there. [https://bugs.launchpad.net/ubuntu/oneiric](https://bugs.launchpad.net/ubuntu/oneiric)> What would I have to blacklist, if I try that? vt6656_stage ? What driver did the compile build? vt6656_what? If 'stage', then it will over-write the current driver so that no blacklisting is needed. If it builds some other, for example vt6656_chili, then blacklist _stage. You will find out in the 'sudo make install' step. It will say something like:> install -m 644 -c [COLOR="Red"]some_driver.ko[/COLOR] /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/

---

### Post by Strike0 on 2011-08-18
> **chili555 said:**
> That suggests that it's not a Network Manager or vt6656_stage issue, but an Oneiric issue; perhaps in the kernel or networking parts. I'd find a bug tracker for Oneiric and report it there. [https://bugs.launchpad.net/ubuntu/oneiric](https://bugs.launchpad.net/ubuntu/oneiric)What driver did the compile build? vt6656_what? If 'stage', then it will over-write the current driver so that no blacklisting is needed. If it builds some other, for example vt6656_chili, then blacklist _stage. 

Ok, I will see with the bug report (its not a widely spread device I would assume, but a netbook without working wifi is a bit far handicaped). 
I cannot remember now the name of the driver back then (with 10.04), but it was not stage. I will try that again once and see if it makes a change. I won't manage that right away though but will surely feedback the next hurdle here asap. Thanks for the quick response.

---

### Post by Strike0 on 2011-08-20
> **Strike0 said:**
> Ok, I will see with the bug report (its not a widely spread device I would assume, but a netbook without working wifi is a bit far handicaped). 
I cannot remember now the name of the driver back then (with 10.04), but it was not stage. I will try that again once and see if it makes a change. I won't manage that right away though but will surely feedback the next hurdle here asap. Thanks for the quick response.

Update: 
Now I had a couple of tries with my basic knowledge to compile it and always failed with 
Makefile:127: *** Linux kernel source not configured - missing config.h.
I followed all the steps I found, but did not succeed through the make again. I guess I will try again once. However, you mentioned ndiswrapper, so I have some hope still I may be able to run Oneiric with that nagging card. This error btw was the reason I did stick to Maverick on the machine.

---

### Post by chili555 on 2011-08-20
> Makefile:127: *** Linux kernel source not configured - missing config.h.Do you have linux-headers installed? You can check in Synaptic Package Manager.

---

### Post by Strike0 on 2011-08-21
> **chili555 said:**
> Do you have linux-headers installed? You can check in Synaptic Package Manager.

Yes, I installed all header files I could see for the kernel. 
But going back to the network manager log I noticed another thing: I said that the MAC address is shown correctly. That is the case, but only in the main network-manager screen. For the individual connection the cards address is shown as 00:00:00... I tried to override that in the /etc/network-manager/ files for the wifi AP (and setting the close variable as well), but it does not seem to make a difference on startup. Though, also when overriding it in a session, there is no connection established. So I guess that does not matter.

---

### Post by chili555 on 2011-08-21
Please give me a link to the driver you downloaded. Thanks.

---

### Post by Strike0 on 2011-08-25
> **chili555 said:**
> Please give me a link to the driver you downloaded. Thanks.

You find it here, this one comes up while searching for linux/legacy/debian: 
[http://www.viaarena.com/Driver/VT6656_linux_src_v1.20.03_x86.rar](http://www.viaarena.com/Driver/VT6656_linux_src_v1.20.03_x86.rar)

It only lists Ubuntu up to 9.10, but that should not be related to the headers error I keep getting or is it? Cheers.

---

### Post by praseodym on 2011-08-25
Obviously this driver doesnt compile from Kernel 2.6.38 and on. You may try the Windows driver attached using Ndiswrapper.

---

### Post by chili555 on 2011-08-25
> It only lists Ubuntu up to 9.10, but that should not be related to the headers error I keep getting or is it?No but yes.

If you have the correct headers installed, it should get beyond the point you stopped. However, it then errors out with:> /home/chili/Desktop/Forum/strike0/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2086:18: error: ‘struct net_device’ has no member named ‘mc_count’
/home/chili/Desktop/Forum/strike0/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2098:34: error: ‘struct net_device’ has no member named ‘mc_list’
/home/chili/Desktop/Forum/strike0/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2098:63: error: ‘struct net_device’ has no member named ‘mc_count’
/home/chili/Desktop/Forum/strike0/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2099:35: error: dereferencing pointer to incomplete type
/home/chili/Desktop/Forum/strike0/VT6656_linux_src_v1.20.03_x86/driver/main_usb.c:2100:52: error: dereferencing pointer to incomplete type
make[3]: *** [/home/chili/Desktop/Forum/strike0/VT6656_linux_src_v1.20.03_x86/driver/main_usb.o] Error 1
Theses are directly due to changes in the kernel, gcc and other build tools since 2009, when this oldie was written and today.

I am afraid that ndiswrapper is your next best choice.

---

### Post by Strike0 on 2011-08-26
> **chili555 said:**
> 
I am afraid that ndiswrapper is your next best choice.

Hi and thanks to both of you, 
I now tried the ndiswrapper with both .inf files in the driver package provided above (VT6656v1 and v2.inf), blacklisted the VT6656_stage, but unfortunately I still keep getting the same problem. 
Scanning works instantly, but the WPA handshake just won't finish successfully as you can see from the messages. 

Interestingly the router shows a successful association each time before it breaks up again. I tried different combinations of AES/TKIP WPA/WPA2 again. 

Any more suggestions by any chance? 
If the card would not work with 10.10 I would have bought an external dongle ages ago.

---

### Post by praseodym on 2011-08-26
You can give Wicd a try instead of the NM:


```
wget [http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz](http://www.elektronenblitz63.de/download/wicd-1.6.x_addon0144.tar.gz)
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon0144.tar.gz
cd wicd-1.6.x_addon0144
sudo ./install_wicd_addon
sudo service network-manager stop
sudo service wicd restart
```

Choose **wlan0** as interface and **wext** ([COLOR="Red"]not[/COLOR] ndiswrapper!) as driver. If it works deactivate the NM in "Autostart"

---

### Post by Strike0 on 2011-08-27
> **praseodym said:**
> You can give Wicd a try instead of the NM. 


I tried that. However, with the wicd from the alpha repositories (which was probably just wrong) and that did not work immediately either. Since I had other issues still with the 11.10 install, I ditched it then fully. It goes on though: I then installed archlinux to give it a try and to cut that short - I had exactly the same problem and error with the default VT6656_stage and WPA handshake. Just the error looked a bit more specific, the iwconfig always showed an error 0 "wrong PSK secret" for WPA. So now again it looks it is not an Ubuntu specific issue with that card does it? 
 
Then I setup a wep key and with that it works now - finally. I guess I will invest a few Euros in a wireless usb-stick at some stage. And Ubuntu stays on the main box of course. 
Whatever makes Maverick work out of the box on WPA with it would be interesting still. I will try to add information to the launchpad bug chili quoted earlier here once I sign up there. 

You two probably know all of it, but on the way I read some good overview on wireless chipsets and manual bash commands here: 
[https://wiki.archlinux.org/index.php/Wireless_Setup#Manual_setup](https://wiki.archlinux.org/index.php/Wireless_Setup#Manual_setup)

Thanks again, I will add here for news with that device.

---

### Post by Strike0 on 2011-09-12
One further sympton I had with the VT6656_stage I want to add quickly: 
I always had problems with suspend of the netbook with that usb-card. It would suspend fine, but on wake-up erratically crash (in more than 50% of resumes).  Last sympton under gnome3 was a blank screen with flickering cursor and no input (terminal) possible. 

After blacklisting the driver, that never happened again yet. The netbook resumes like bliss. I assume unloading the module before suspend would also work, but have not tried that as my problems to use the card render it useless anyway.

---

