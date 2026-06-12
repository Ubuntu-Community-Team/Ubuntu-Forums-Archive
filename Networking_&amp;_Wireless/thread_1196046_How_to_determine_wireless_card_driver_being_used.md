---
title: "How to determine wireless card driver being used?"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by rdd37 on 2009-06-24
Hi all,

I imagine there is a simple answer to this question, but I've been unable to find it in the archives, or thru google, etc.

What I need to is to determine which driver is being used for my wireless card. The card is working fine (no connectivity troubleshooting is needed) -- I am just trying to learn more about wireless networking, and as part of that endeavor trying to create a wpa_supplicant.conf file. The one parameter I'm unsure of is -D (driver).

"The available drivers to specify with the -D option are:
       hostap (default) Host AP driver (Intersil Prism2/2.5/3). 
       hermes Agere Systems Inc. driver (Hermes-I/Hermes-II).
       madwifi MADWIFI 802.11 support (Atheros, etc.).
       atmel  ATMEL AT76C5XXx (USB, PCMCIA).
       wext   Linux wireless extensions (generic).
       ndiswrapper Linux ndiswrapper.
       broadcom Broadcom wl.o driver.
       ipw    Intel ipw2100/2200 driver.
       wired  wpa_supplicant wired Ethernet driver
       bsd    BSD 802.11 support (Atheros, etc.).
       ndis   Windows NDIS driver."


Some of the system details include:
Ubuntu 8.10

**lsusb** ->
Bus 003 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]

**iwconfig wlan1** ->
~$ wlan1     IEEE 802.11bg  ESSID:"XXX"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=54 Mb/s   Tx-Power=11 dBm   
          Retry min limit: 7   RTS thr: off   Fragment thr=2352 B   
          Encryption key: <-->   Security mode: open
          Power Management: off
          Link Quality=55/100  Signal level:-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**lshw -C network**->
description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: XX:XX:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.X multicast=yes wireless=IEEE 802.11bg



Any pointers greatly appreciated!

---

### Post by rdd37 on 2009-06-24
It occurred to me that I might be able to find this information in a pre-existing wpa_supplicant.conf file on the system, assuming that my existing connection thru Network Manager creates this file. However, there is only one 'wpa_supplicant.conf' file on the system, and it appears to be some kind of sample/template/XML-ish file:
/etc/dbus-1/system.d/wpa_supplicant.conf 


So I still need to find another way to determine the driver used.

---

### Post by rdd37 on 2009-06-25
Is this question *that* boring or *that* tough..?  

edit: or... *that* stupid?  ;)

---

### Post by rdd37 on 2009-06-25
I noticed [this thread]("http://ubuntuforums.org/showthread.php?t=1196179"), which suggests that
"the drivers will either be built into the kernel or available as kernel modules which are located in /lib/modules/2.6.x.y"

I've been exploring around this directory and sub-directories, including /lib/modules/2.6.27-14-generic/kernel/drivers/net/wireless/
but there are many entries:
rwxr-xr-x 12 root root   4096 2009-05-16 14:36 .
drwxr-xr-x 28 root root   4096 2009-05-16 14:36 ..
-rw-r--r--  1 root root  43156 2009-04-15 15:27 adm8211.ko
-rw-r--r--  1 root root  16212 2009-04-15 15:27 airo_cs.ko
-rw-r--r--  1 root root  99064 2009-04-15 15:27 airo.ko
-rw-r--r--  1 root root  97560 2009-04-15 15:27 arlan.ko
drwxr-xr-x  2 root root   4096 2009-05-16 14:36 ath9k
-rw-r--r--  1 root root  18724 2009-04-15 15:27 atmel_cs.ko
....
(over 20 entries)


It's still not clear to me what driver is being used.. any ideas?

---

### Post by shel-hall on 2009-06-25
> **rdd37 said:**
> Is this question *that* boring or *that* tough..?  

edit: or... *that* stupid?
Neither, but I don't know the answer.

It's rather remarkable that iwconfig shows you all those details but doesn't show the driver in use. 

Sorry to be so little help.

-Shel

---

### Post by rdd37 on 2009-06-25
> **shel-hall said:**
> 

Sorry to be so little help.

-Shel

Quite alright, of course. 
I might make personal history with this question though -- first time ever stumping a forum full of Linux users.  ;)

---

### Post by Sub101 on 2009-06-25
Running:

```
sudo dmesg
```

should output, among a great deal of other things, the driver you are using.

Try to find the name of your card in the list.

Otherwise post the output here and I will see if I can spot it

---

### Post by rdd37 on 2009-06-25
> **Sub101 said:**
> Running:

```
sudo dmesg
```

should output, among a great deal of other things, the driver you are using.

Try to find the name of your card in the list.

Otherwise post the output here and I will see if I can spot it


Sub101 - thank you for the suggestion & offer. 


dmesg does indeed seem to include the driver name: 
--------------------------------
[15.488786] usbcore: registered new interface driver rt73usb
[15.728167] udev: renamed network interface wlan0 to wlan1
--------------------------------

**rt73usb**

I'm still confused as to where this driver name fits with the available driver options for wpa_supplicant.conf:
       hostap (default) Host AP driver (Intersil Prism2/2.5/3).  
       hermes Agere Systems Inc. driver (Hermes-I/Hermes-II).
       madwifi MADWIFI 802.11 support (Atheros, etc.).
       atmel  ATMEL AT76C5XXx (USB, PCMCIA).
       wext   Linux wireless extensions (generic).
       ndiswrapper Linux ndiswrapper.
       broadcom Broadcom wl.o driver.
       ipw    Intel ipw2100/2200 driver.
       wired  wpa_supplicant wired Ethernet driver
       bsd    BSD 802.11 support (Atheros, etc.).
       ndis   Windows NDIS driver.


However it turns out (I think), that rt73usb is not compatible with wpa_supplicant (according to this old (2007) post):
[rt73usb does not support wpa_supplicant, it seems]("http://ubuntuforums.org/archive/index.php/t-520695.html")
...so, I'm guessing that's why I don't see rt73usb (or similar) listed in the wpa_supplicant.conf driver options. 
So, I won't be creating a wpa_supplicant.conf file. Unless I'm mistaken here. ;)

thanks again for the pointer..

---

### Post by sadinsudin on 2009-07-04
hi guys ..
i;m using using ubuntu 8.04
i can't detect my machine wireless adapter 
i'm using the presario v3000 ( to be exact v3415au)
with broadcom wireless..

i already tried to configure the wireless through reading the releven thread but yet
it failed

to begin with, i entered the command and the output as below

1
iwconfig wlan1
wlan1     No such device

2
iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

pls help..

---

### Post by tehardis on 2009-11-08
You can install Device Manager. This will tell you the wireless card driver as well as other info about your computer. On you Ubuntu computer:

1. Choose system => Administration => Synaptic Package Manager.

2. Click the search button on the toolbar, and type [COLOR=Red]gnome-device-manager [COLOR=Black]in the Search field. Click the search button.

3. Click the program's entry in the list of results. Select to mark it for installation (don't worry if a dialog box appears telling you additional software needs to be installed).

4. Click Apply on the toolbar.

[/COLOR][/COLOR][COLOR=Red][COLOR=Black][COLOR=Red][COLOR=Black]If your computer is not online, you'll need to use a computer that is online (perhaps another computer, or Windows XP if you dual-boot you will need to copy the software, and then copy it across to your Ubuntu computer for installation. To download the software, visit the following two [/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Red][COLOR=Black]addresses in your browser. You will prompted to download a file after typing in each address:

 [COLOR=Red]http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-device-manager/gnome-device-manager_0.2-2_i386.deb

[/COLOR][/COLOR][/COLOR][COLOR=Red][COLOR=Black][COLOR=Red]http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gnome-device-manager/libgnome-[/COLOR][/COLOR][/COLOR][COLOR=Red][COLOR=Black][COLOR=Red]device-manager_0.2-2_i386.deb[COLOR=Black]

After the files are downloaded, copy them to the desktop of your Ubuntu machine, using a floppy disc disk or maybe a USB memory stick. Then open a command prompt window on the Ubuntu computer by clicking Applications => Accessories => Terminal. In the terminal window, type the following, hitting Enter after each line:

[COLOR=Red]cd ~/Desktop
sudo dpkg -i lib[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Red][COLOR=Black][COLOR=Red]gnome-[/COLOR][/COLOR][/COLOR][COLOR=Red][COLOR=Black][COLOR=Red]device-manager_0.2-2_i386.deb
sudo dpkg -i [/COLOR][/COLOR][/COLOR][COLOR=Red][COLOR=Black][COLOR=Red]gnome-device-manager_0.2-2_i386.deb[COLOR=Black]

After you have installed the Device Manager, you can open it by clicking Applications => System Tools => Device Manager. You will need to click View => Device Properties to ensure the Device Manager adds the Properties tab. Your wireless driver should be listed under the properties tab. Just remember that just because a piece of hardware is listed within Ubuntu's Device Manager doesn't mean it is configured to wotk with Ubuntu. 

I got this information from the book "Beginning Ubuntu Linux" fourth edition written by Keir Thomas and Andy Channelle. The instructions begin on page 120.

I hope this helps. 
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by hero1900 on 2011-11-01
lspci -k

---

### Post by nothingspecial on 2011-11-01
Halloween has been an gone.

Please do not raise old threads from the dead.

Closed.

---

