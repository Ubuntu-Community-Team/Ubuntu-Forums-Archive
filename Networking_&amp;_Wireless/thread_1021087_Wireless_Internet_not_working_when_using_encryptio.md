---
title: "Wireless Internet not working when using encryption"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by teqnilogik on 2008-12-24
Hi all,

I installed Ubuntu 8.10 today on my Toshiba Satellite A205-S5804 laptop.  It has a Realtek RTL8187b wireless adapter.  The 2.6.27 kernel added support for my card.  After installation of Ubuntu I was able to connect to my wireless network and connect to the Internet.  But something happened and now I am able to connect to my wireless network, I get a good DHCP IP address from my router, but I cannot ping any web site or even my router's IP (192.168.1.1).  I use WPA2 Personal encryption on my wireless network.  After some experimenting, I disabled the wireless security on my network and reconnected to the wireless network in Ubuntu and after that I was able to ping my router and ping out to the Internet.  So something is happening in Ubuntu where it allows me to connect to the wireless network but after that I am not able to ping out to anything.  I also tried using WEP encryption and I encountered the same problem.  My router's DHCP table sees my laptop connecting to it when encryption is enabled.  Does anyone have any suggestions to get Ubuntu pinging out using encryption on a wireless network?

EDIT: After further testing, disabling the wireless security doesn't allow me to connect to the Internet.  It worked once but now even with wireless encryption disabled I am unable to connect to the Internet.  I have noticed with wireless encryption disabled that I will occasionally get a ping reply from my router but for the most part pinging out fails.  So right now it appears that I am able to make connection to my wireless network with encryption and without encryption but I am unable to ping out to anything.  Also, if I connect up an ethernet cable to my laptop the Internet works fine.

---

### Post by teqnilogik on 2008-12-26
I have resolved this problem after searching Google and various forums.  The solution was to use the Windows 98 driver with ndiswrapper.

Below are the steps I followed to get it working:

**Step 1:** Install ndiswrapper-common and ndiswrapper-utils-1.9

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

**Step 2:** Download the RTL8187B Windows 98 driver [here](http://www.wireless-driver.com/download/realtek/Realtek-RTL8187B-Wireless-80211g-54Mbps-USB-20-Network-Adapter-Driver.htm).  Download the "Window Driver (support Win98/WinME/Win2K/WinXP/Vista)" file.  Save the file to your desktop.

**Step 3:** Extract the Win98 folder from the zip archive to your desktop.

**Step 4: **Modify the net8187b.inf file in the Win98 folder by opening it up in a text editor (just double-clicking the file should open it up in a text editor).  You will see the following lines:

```
;;****************************************************************************

;; IDs for 98SE/ME/2K/XP

;;****************************************************************************

[Realtek]

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200

%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
```

Add the following line underneath the last line above:

```
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
```

Save the file.

**Step 5:** Install the driver with ndiswrapper.

```
cd /home/username/Desktop/Win98
sudo ndiswrapper -i net8187b.inf

```

**Step 6:** Load ndiswrapper module.

```
sudo modprobe ndiswrapper
```

**Step 7:** Verify the driver is installed and working.

```
ndiswrapper -l
```

If everything worked, the following should display on your screen:

```
net8187b : driver installed
	device (0BDA:8197) present (alternate driver: rtl8187)
```

**Step 8:** Make ndiswrapper startup with Ubuntu

```
sudo ndiswrapper -m
sudo ndiswrapper -ma && sudo ndiswrapper -mi
```

**Step 9:** This step only applies to people running Ubuntu 8.10.  Blacklist the rtl8187 module to stop it from loading with Ubuntu.  This is the driver that came with Ubuntu that didn't allow my wireless to work properly.  You want to prevent this from loading so it doesn't interfere with the ndiswrapper driver.

```
sudo gedit /etc/modprobe.d/blacklist
```

Add the following line to the end of this file:

```
blacklist rtl8187
```

Save the file.

**Step 10:** Reboot Ubuntu

**Step 11:** Connect and configure your wireless network using Ubuntu's Network Manager.  From my testing WPA2 Personal and WEP work.  Though, it took my wireless adapter a couple tries to get connected to my wireless network but after that the connection ran smooth.

I hope this guide helps people having similar problems!

---

### Post by blackstripes on 2009-01-21
I also have a Toshiba a205-s5804.  I've installed 8.10 and wireless, to my surprise, was working out of the box.  However, I was getting issues of the signal randomly dropping and then coming back.  

I followed your guide step by step and I seem to be in a worse position.  Wireless still seems to work, but I am not able to use any type of encryption or for some reason my route won't assign the laptop an IP address.  So, my question is how do I undo what I did in this guide?  I can know how to unblacklist the original driver, but I am not sure how to uninstall ndiswrapper and the win98 driver.  Can you or anyone else help?

---

### Post by teqnilogik on 2009-01-30
Sorry it didn't work out.  That's odd you had these issues since I was able to use encryption with my wireless network and generally didn't experience any issues after using the Win 98 driver with ndiswrapper.  

You should be able to uninstall the driver you install using ndiswrapper by running the following command:

```
sudo ndiswrapper –e net8187b.inf
```

---

