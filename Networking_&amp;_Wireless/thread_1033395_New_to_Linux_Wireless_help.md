---
title: "New to Linux: Wireless help"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by ShawnMichael on 2009-01-07
Hi.  I am new to Linux and Im having issues with the network.  I am on my Dell Inspiron B130 laptop using Intel(R)Pentium(R)M. Dell Wireless 1370 Wlan Mini-Pci Card. And for whatever reason, or whatever I do, it wont let me use the network on Ubuntu.  Can anyone give me step by step to get it working?  Remember I am a first time Linux user, and I would like to use Linux.  Any help would be appreciated!

---

### Post by superprash2003 on 2009-01-07
post output of the following commands from terminal
1)iwconfig
2)iwlist scanning
3)ifconfig

---

### Post by eatberrys on 2009-01-07
Is it in the restricted drivers?

---

### Post by ShawnMichael on 2009-01-07
Iwconfig:
lo - no wireless
eth0 no
wmaster0 No
Wlan0 IEEE 802 11BG ESSID 11BG
Mode: Managed Frequency: 2.412 GHz accesspoint: Not associated
Tx-Power=27 dBm
Retry Min Limit: 7 RTS thr: off Fragment thr=2352 B
Power Management: off
Link Quality: 0 Singal Level: 0 Noise Level: 0
Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc: 0 Missed beacon:0

Pan: 0 no wireless extensions

iwlist scanning:
lo Interface doesnt support scanning 
eth0 ""
wmaster0""
wlan0 no scan result
pan0 Interface doesnt support scanning

ifconfig:
Eth0: link encap: ethernet HWADR 00:14:22:8a:2b:F4
Upbroadcast Multicast MTU: 1500 Metric:1
Rx packets:0 Errors:0 Dropped:0 Overruns:0 Frame:0
Tx packets:0 Errors:0 Dropped:0 Overruns:0 Frame:0
Collisions:0 Tx queuelen:1000
Rxbytes:0 (0.0 B) TX Bytes:0 (0.0 B)

L0  Link encap: local loopback
inet addr: 127.0.0.1 Mask 255.0.0.0
inet 6 addr: ::1/128 Scope: Host
Up Loopback Running MTU: 16436 Metric:1
Rx 246 errors:0 dropped:0 overruns:0 frame:0
Tx 246 errors:0 dropped:0 overruns:0 carrier:0
Collisions:0 tx queuelen:0
Rx bytes: 15408 (15.4 KB) Tx Bytes: 15408 (15.4 KB)

---

### Post by Bucky Ball on 2009-01-07
Be aware that Dell make nothing. They put components in boxes. Your Dell Wireless 1370 Wlan Mini-Pci Card is more likely an intel or Broadcom card with a different frock on, in which case, as a previous poster said:

System->Administration->Hardware Drivers

What do you see there? If you see the Broadcom B43 Driver, switch it on, follow your nose and you should be up soon. You can find the make of the card by pasting in a terminal:

```
lspci
```... and down the bottom somewhere you should find the card. It should look something like this:

```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

``` ... or another manufacturer. Let us know what it is and it will make it easier to fix your problem. :)

---

### Post by ShawnMichael on 2009-01-07
There is nothing in the hardware driver. Its blank

shawnmichael@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
shawnmichael@ubuntu:~$ sudo lshw -C network

---

### Post by Ayuthia on 2009-01-07
If you have a working internet connection in Ubuntu, you can install b43-fwcutter.  It is the same thing as the one in Hardware Drivers.  There is a bug in Hardware Drivers that causes it to not always find the Broadcom cards.  You should be able to install b43-fwcutter using Synaptic or you can do it in the Terminal:
```
sudo aptitude install b43-fwcutter
```
It should ask if you want to have it fetch the firmware for you.  Just say yes to it if you have a working internet connection.

Hope that helps.

---

### Post by ShawnMichael on 2009-01-07
Is there a way I can downnload that on my usb flash drive and then just go to ubuntu and upload it there??? If thats possible.. let me know.  Cuz the I have no internet on Ubuntu.

---

### Post by Ayuthia on 2009-01-07
Here is a link with some instructions on how to do it without an internet connection in Ubuntu:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by ShawnMichael on 2009-01-07
K i done that, but where do I put the codes?

---

### Post by Bucky Ball on 2009-01-07
```
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```Like I said, a Broadcom card in a Dell dress. B43 is what you want and sounds and looks like you are getting there. You may be able to add your USB stick under software sources:

System->Administration->Software Sources

... then once it is added to the sources you will be able to load b43 through Synaptic Package Manager. Try this in a terminal first:

```
sudo apt-get updates
```

... close the terminal then wait for a second and see if you have downloads waiting. Also, go to Synaptics and search for:

ubuntu-restricted-extras

Install that, close, wait and see if you get a message along the lines of 'Restricted Drivers Available'.

---

### Post by Unparallelogram on 2009-01-07
I'm using a Dell laptop with a similar card. There's a few different drivers that you can use for the Broadcom 43xx chipset that your wireless card has. The one that's currently recommended from what I've heard is called wl. You can install it by that name from the restricted drivers package, or under the restricted drivers dialogue as the Broadcom STA driver. You may also need to blacklist the b43 and ssb drivers with modprobe that may otherwise compete for serving the card and cause you to misload a driver.

1. Update your system through wired internet.

2. Install wl from restricted driver dialogue. Go to System -> Hardware Drivers and activate Broadcom STA.

3. Go edit the modprobe blacklist (You may or may not need this step, but it won't hurt since you're using wl.)
> sudo gedit /etc/modprobe.d/blacklist
and add the lines to the end
> blacklist b43
blacklist ssb

Edit: 4. Reboot

---

### Post by Bucky Ball on 2009-01-08
No. If you can use the b43, do it. Any other method should be a second choice if it doesn't work. This driver is specifically designed for the problematic Broadcom cards and has superseded other methods therefore should be the first port of call if your card is supported. Check whether it is by doing a search for 'b43 supported wireless cards' or something along those lines.

Try this:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Yes, 4318 is supported. Go that way - with b43. You will save yourself a lot of headaches, trust me.

---

### Post by ShawnMichael on 2009-01-08
I tried using the ethernet cord and it works just fine.  But I want to be on wireless, which I use most of the time when I roam anywhere.  Just a heads up

---

### Post by ShawnMichael on 2009-01-08
I finally got wireless to work.  Thanks to you Ayuthia and Bucky Ball.  Now I have issues with Firefox in which it wont open.  Also the automatic updates, had come to halt right in the middle so I was forced to shut it down and restart, but the automatic updates wont let me finish the updates.  Any tips?  Thanks.  Much much much appreciated!!!!!!  I may start to love Linux in spite of it all!  LOL

---

### Post by kickwin on 2009-06-29
I wish I had seen this discussion before I spent about two days on a failed attempt to make wireless work with ndiswrapper. B43 driver works in my case and so far I had no problem with it. But I see this in Hardware Drivers dialog box - "A different version of this driver is in use". Here is a screenshot of it. Let me know if you guys know what this is about. Thanks!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=119331&d=1246267736[/IMG]

---

### Post by Ayuthia on 2009-06-29
> **kickwin said:**
> I wish I had seen this discussion before I spent about two days on a failed attempt to make wireless work with ndiswrapper. B43 driver works in my case and so far I had no problem with it. But I see this in Hardware Drivers dialog box - "A different version of this driver is in use". Here is a screenshot of it. Let me know if you guys know what this is about. Thanks!

Can you post the results of:
```
dmesg|grep b43
```
My guess is that the firmware that is installed is the older version.  I think that the current firmware version is 4.150.10.5.

---

### Post by kickwin on 2009-06-29
Here is it.

dmesg|grep b43
> 
[    3.098235] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.041425] b43-phy0: Broadcom 4318 WLAN found
[   22.076404] input: b43-phy0 as /devices/virtual/input/input9
[   22.128064] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   22.272483] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   22.310785] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   22.399865] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   22.528273] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.569936] Registered led device: b43-phy0::tx
[   22.569957] Registered led device: b43-phy0::rx
[   22.569982] Registered led device: b43-phy0::radio
[   22.592320] b43-phy0: Radio turned on by software


---

### Post by Ayuthia on 2009-06-29
That is interesting.  The information there is correct.  How did you install the firmware (b43-fwcutter or other means)?

---

### Post by kickwin on 2009-06-29
> **Ayuthia said:**
> That is interesting.  The information there is correct.  How did you install the firmware (b43-fwcutter or other means)?

I think I installed using the b43-fwcutter. In the image I had uploaded in my previous post, you can also see that. 

Not to confuse anyone reading my posts, I want to repeat that my wireless works seamlessly but I am just curious about the message I see in my Hardware Drivers dialog box.

---

### Post by Ayuthia on 2009-06-29
I have no clue.  Obviously everything looks fine.  My guess is that it is a bug.

Can you post your lshw -C network?  I just want to see what driver it is using.  It most likely is the b43, but I am just surprised about the message.

---

