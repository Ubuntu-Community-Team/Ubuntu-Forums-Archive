---
title: "broadcom bcm4306 rev 3 not working in ubuntu server 10.04"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by db654 on 2010-05-22
good evening ladies and gents,

I am in the process of setting up a home server and have hit a bit of a brick wall. During the installation I was notified that 'no network interfaces detected' but I carried on with the installation. The installation went fine and booted up into the o/s.  There is no ethernet port on the motherboard, however I am using a wireless bcm4306 rev 3 broadcom pci card.

Now that I am logged in, how would I go about getting my wireless card working? I have followed a guide where I installed the b43-fwcutter package, downloaded the firmware and extracted the firmware to /lib/firmware and restarted pc but I'm still not getting any action from the wifi card.



Here is the output of some commands:
**lspci | grep Broadcom\ Corporation**
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

**iwconfig wlan0**
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

**lshw -C network**
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:17 memory:dfff8000-dfff9fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:1c:31:a8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

**lsmod | grep b4**
b43                   157827  0 
mac80211              204922  1 b43
cfg80211              126517  2 b43,mac80211
led_class               2864  1 b43
ssb                    37336  1 b43


Any help/info/suggestions on getting this working will be gratefully appreciated!

Cheers

---

### Post by db654 on 2010-05-23
*bump*

---

### Post by db654 on 2010-05-25
It appears as though I have got the card working! I'll post the steps just in case they help some one else ( I will post thorough steps just in case there is someone just starting out with ubuntu). As mentioned in my original post, I didn't have any internet access at all on my server pc- there is no onboard LAN and the wireless card in question was not working. 

So on my main pc which is connected to the internet, I cracked open a terminal and downloaded the b43-fwcutter .deb package for lucid ([http://packages.ubuntu.com/lucid/i386/b43-fwcutter/download](http://packages.ubuntu.com/lucid/i386/b43-fwcutter/download)) and saved it to my desktop for now (package filename: b43-fwcutter_012-1build1_i386.deb)

The next step was to obtain the correct firmware using info from the following site ([http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new))

The firmware required is broadcom-wl-4.150.10.5 (I am using kernel 2.6.32-21-generic-pa) so make sure in your terminal you are in the desktop area (for simplicity) and type:
[B]wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
[/B] which will download the tarball to your desktop.

Now I plugged in a USB stick to my main pc, cd'd to the desktop and placed the b43-fwcutter deb and the firmware tarball onto it. I then unplugged the usb stick and mounted it on my server pc (automount doesn't happen on the server o/s) and typed:
**sudo mount -t vfat /dev/XXX] /mnt/external**

[note I created a mount point in /mnt/ called external:
**sudo mkdir /mnt/external** ]

you can find out which device your usb is by typing:
**sudo fdisk -l**      and place the appropriate string in the /dev/XXX expression above

so with the usb mounted, I then copied the 'b43-fwcutter_012-1build1_i386.deb' and 'broadcom-wl-4.150.10.5.tar.bz2' to my home area. Now change directory to your home area where you just copied the files to.

I then installed the .deb package by executing:
**sudo dpkg -i b43-fwcutter_012-1build1_i386.deb**

and then unpacked the .tar.bz2 by executing:
**sudo tar xjf broadcom-wl-4.150.10.5.tar.bz2**

after the unpacking finished, I then executed:
**sudo b43-fwcutter -w /lib/firmware ./broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o**
 and you should see some output in the terminal.

I then executed:
**sudo ifconfig wlan0 up**

and then when I exeucted 
**sudo iwlist wlan0 scan**

I could see my SSID and the houses surrounding, success!

So now running **dmesg | grep b4** , I get the following:
[    2.274942] b43-pci-bridge 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.534412] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   10.856761] Registered led device: b43-phy0::tx
[   10.856819] Registered led device: b43-phy0::rx
[   10.856882] Registered led device: b43-phy0::radio
[  823.524060] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[  823.543799] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[  823.557412] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[  823.571045] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[  823.700058] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

Now that I have the card running, I just need to figure out how to configure it to connect to my router!

Hope this helps someone!

---

### Post by db654 on 2010-05-25
update:
to configure the wifi card to connect to my router, I simply installed a wpa_supplicant .deb package on the server pc and then edited the appropriate wpa_suppicant.conf and /etc/network/interfaces file.

works like a charm!

---

### Post by Yum_Salad on 2010-05-27
I tried this but just got a bunch of errors showing in the grep command at the end :(

---

### Post by apoth on 2010-06-06
Works for me... for 30 seconds, then it goes down and spends a minute reconnecting!

---

### Post by audryla on 2010-06-15
Thanks!!!
Works like a charm and not only on server:p
First time, when get bcm4306 rev 3 working without pain...
off course do not forget wpa_suppicant.conf and /etc/network/interfaces files. Some info here:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Wireless](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Wireless)
[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)
[wpa_supplicant file sample]("http://hostap.epitest.fi/gitweb/gitweb.cgi?p=hostap.git;a=blob_plain;f=wpa_supplicant/wpa_supplicant.conf")
One important thing on desktop: remove network-manager
```
sudo apt-get remove network-manager
```
This will avoid something like this:
> **apoth said:**
> Works for me... for 30 seconds, then it goes down and spends a minute reconnecting!

BR
audryla

---

