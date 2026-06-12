---
title: "Ralink 3070 Alfa Driver Install"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by kid1000002000 on 2010-02-14
Hi all.

Having trouble getting my Alfa 802.11 b/g/n Wireless Card set up in Ubuntu 9.10.  It is a 2W card, Model No. AWUS036NH.  When I connect it to the computer, the card will register in Network Manager but lists as "Disconnected."  

I have followed the following steps, but to no avail from the thread [URL="http://ubuntuforums.org/showthread.php?t=1387475"]http://ubuntuforums.org/showthread.php?t=1387475.
[/URL][INDENT]1.  Copy driver for network card to Desktop
2.  Open a terminal
3.  sudo -i
4.  cd /home/ubuntu/Desktop/rt3070alfa
5.  tar -xf 036NH_2009_1110_Linux.tar.bz2
6.  cd 2009_1110_RT3070_Linux_STA_v2.1.2.0
7.  gedit os/linux/config.mk
8.  Change "HAS_WPA_SUPPLICANT=n" and "HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n" to y
9.  make && make install (make install gave errors until I changed two file names from RT2870.dat > RT3070.dat and rt2870STACARD.dat to RT3070STACARD.dat)
10. sudo gedit /etc/modprobe.d/blacklist.conf and add:
a.  blacklist rt2x00usb
b.  blacklist rt2x00lib
c.  blacklist rt2800usb
11. reboot
[/INDENT]Further searching across various other forums, trying other's posts, has yielded no success, hence asking for help directly.

The card uses the Ralink 3070 chipset (at least, that's what I can tell from running lsusb and seeing 3070 listed there), and while I have drivers that came on a cd, I am using the updated version obtained fom railink's website.  Neither version has offered me success.  Being new to Ubuntu, however, does anybody have an idea to get this to work?  I know this is possible, as  I have gotten it to work before on another setup. I have tried multiple times to run this setup now with no success, and I really don't want to have to run vista just to use a wireless card.

Thanks for the help.

---

### Post by kid1000002000 on 2010-02-16
bump...

---

### Post by kid1000002000 on 2010-02-28
bump

---

### Post by chili555 on 2010-02-28
> **kid1000002000 said:**
> bump- with a bonus.  Willing to paypal $5 to whoever can solve it, and more than that if it becomes intensive.In my opinion, this is in conflict with the spirit of free and open source software. We work very hard but just for the fun of it. It will be fun for me to help solve your issue, but please put that Paypal button away.

You were not too clear on what went wrong, so let's take some vital signs first. Please open a terminal and do:```
dmesg | grep -e rt2 -e rt3
iwconfig
```Post the result and we'll proceed.

---

### Post by kid1000002000 on 2010-02-28
consider it done.
Here is the output from what you requested while the device is plugged in.  As you can probably tell, I have tried several times with the install.  Any changed made to posted code will always include "EDITED".
[INDENT]$ dmesg | grep -e rt2 -e rt3
[   26.672452] usbcore: registered new interface driver rt2870
[  456.598177] Registered led device: rt2800usb-phy1::radio
[  456.598229] Registered led device: rt2800usb-phy1::assoc
[  456.598280] Registered led device: rt2800usb-phy1::quality
[  456.599771] usbcore: registered new interface driver rt2800usb
[  456.628431] rt3070sta: module license 'unspecified' taints kernel.
[  456.628904] rt3070sta: Unknown symbol usb_alloc_urb
[  456.629290] rt3070sta: Unknown symbol usb_free_urb
[  456.630267] rt3070sta: Unknown symbol usb_register_driver
[  456.631064] rt3070sta: Unknown symbol usb_put_dev
[  456.631378] rt3070sta: Unknown symbol usb_get_dev
[  456.631973] rt3070sta: Unknown symbol usb_submit_urb
[  456.633350] rt3070sta: Unknown symbol usb_control_msg
[  456.634315] rt3070sta: Unknown symbol usb_deregister
[  456.635671] rt3070sta: Unknown symbol usb_kill_urb
[  456.635974] rt3070sta: Unknown symbol usb_buffer_free
[  456.637171] rt3070sta: Unknown symbol usb_buffer_alloc
[  456.694369] rt2800usb 1-3:1.0: firmware: requesting rt2870.bin

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"EDITED"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: EDITED
          Bit Rate=54 Mb/s   Tx-Power=10 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan4     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=6 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


[/INDENT]

---

### Post by chili555 on 2010-02-28
Do you have two wireless devices? wlan0 and wlan4? Is it going to be hard to separate one from the other? If you have an interface created, it seems you are almost there. What happens if you unplug the "not-3070" device and try to connect?

---

### Post by kid1000002000 on 2010-02-28
I am using a laptop, have an internal wireless card named wlan0, and external usb device (the one giving all the trouble) that is currently named wlan4.  There are dead spots at the campus where I am at, thus requiring me to use a stronger card.

Wifi can be disabled by a switch on the front of the computer, but this disables all wifi capability, including external devices.

I am able to access the internet via the internal, wlan0 card, but get nothing from the external card.  Not sure how to disable the internal device- but I also am not sure this is the issue, as I have had both working previously together (at least, before I had to do a fresh install after a crash).  I do know that in my previous install, the usb card was listed as ra0 instead of wlan4.

Using the readme from ralink's linux install directions, I have been able to follow all instructions except the last part:[INDENT]6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt3070sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

[/INDENT]I get the following error after changing the file name from 2870sta.o to 3070sta.o:[INDENT]insmod: can't read 'rt2870sta.ko': No such file or directory
[/INDENT]Perhaps this has something to do with it?  I am clueless.  I have attached the readme instructions that follow fairly closely with those posted in the original post.

---

### Post by chili555 on 2010-02-28
How do you tell your computer to connect with wlan4 instead of wlan0? More pointedly, how do you get Network Manager to cooperate? I rather imagine that if you take down wlan0, sudo ifconfig wlan0 down, for example, that NM brings it right back up. This may turn out to be an interesting challenge.

Please check PM.

---

### Post by chili555 on 2010-02-28
> # $/sbin/insmod rt2870sta.oWow! How old is this antique?

May I see:```
lsusb?
```Let's start from square one.

> Registered led device: rt2800usb-phy1::radioYour computer thinks rt2800usb is the right driver.

---

### Post by kid1000002000 on 2010-02-28
I can click on the NetworkManager icon in my panel and see both cards listed, with the networks each scanned for listed seperately beneath their names.  Connections can be enabled or disabled at will by clicking on an ssid or by clicking "disconnect".

$ lsusb
Bus 001 Device 004: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2010-02-28
Both the rt3070sta driver that you compiled and rt2800usb claim the device. Hence the duplication in *dmesg*:> [ 456.599771] usbcore: registered new interface driver rt2800usb
[ 456.628431] rt3070sta: module license 'unspecified' taints kernel.Let's start by blacklisting rt2800usb. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist rt2800usb
```Proofread carefully, save and close gedit. Now reboot and see if the behavior improves.

I am a bit worried about all the 'Unknown symbol usb_' warnings; however, let's take one step at a time.

---

### Post by CharlesA on 2010-02-28
This might help: [http://ubuntuforums.org/showthread.php?t=1387475](http://ubuntuforums.org/showthread.php?t=1387475)

Check post three and on.

---

### Post by kid1000002000 on 2010-02-28
Successfully blacklisted rt2800usb and rebooted.  Now, when I reboot, the card does not show up at all in NetworkManager.
CharlesA, thanks for the suggestion.  Your link has helped lead us to where we are at now.

---

### Post by kid1000002000 on 2010-03-01
Problem solved.  Thank you, chili555, for the solution.

Had trouble compiling the source code, causing a bad    	 	 	 	rt3070sta.ko to be compiled.  Reinstalling build-essentials and its dependencies fixed the problem, allowing for a correct install of the driver.  Afterwords, blacklisting like I had originally tried to do in the first post at the END of the file and restarting then caused the driver to work properly.

---

### Post by CharlesA on 2010-03-02
D'oh! That'll show me why I need to click on links in the OP.

---

### Post by chili555 on 2010-03-02
Just to clarify a bit, the built-in rt3070sta driver module works fine. There is no need to build from a tar.bz2 or similar. However, the built-in rt2800usb *and* rt2870sta *and* rt3070sta all claim his device with the PCI.IDS of [COLOR="Blue"]148f:3070[/COLOR]. Yours may be found in *lsusb*. 

The drivers all conflict and the device won't work correctly. kid1000002000 decided that the best option was to install a newer, better rt3070sta. However, it, too, conflicts with rt2800usb and rt2870sta, so even if the module built correctly, it still won't work!

The solution is to blacklist rt2800usb, rt2x00lib, rt2x00usb and rt2870sta. He also needed to explicitly load, in */etc/modules*, rt3070sta. The changes to the *blacklist* and *modules* file seem to work better with the device removed.

His device sprang to life at N speeds!

---

### Post by giovmendoza on 2010-07-05
I blacklisted only rt2800usb, and it worked for me!
Thanks a lot...

---

### Post by Subharo on 2011-05-18
The same fix worked for me.  I have an Asus USB-N13, which also uses the Ralink 3070 chip.  By merely blacklisting rt2800usb in /etc/modprobe.d/blacklist.conf and rebooting, that was my "fix" as well.  Thanks, chili555!   :smile:

---

### Post by ndangerfield on 2012-09-30
#11 Chilli 555

Adding that one line to the blacklist file worked. Had been trying to solve this for days.

Many thanks (running Ubuntu 10.0.4)

---

### Post by kid1000002000 on 2012-09-30
Even 2 years later, I'm really glad [chili555]("http://ubuntuforums.org/member.php?u=35909") helped out with this one. Can't believe how much I've learned since then. Gotta say, Thx again.

---

### Post by chili555 on 2012-09-30
Thank you very much for your kind words. I love to help you all get past the wireless hurdle.

---

