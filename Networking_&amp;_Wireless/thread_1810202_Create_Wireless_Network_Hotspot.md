---
title: "Create Wireless Network Hotspot"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by gonkyouka on 2011-07-22
I connected a USB Wireless Dongle (Sapido AU-4512S) on my Ubuntu 10.04 64bit. I wanted to share my wired internet connection from my pc to my friend's laptop. So, I did the following:

1. Installed ndiswrapper-utils, ndiswrapper-common and ndisgtk in Synaptic Package Manager.

2. Installed Windows 7 64bit driver of my USB Dongle through Wireless Network Drivers(ndisgtk)

3. Now it says, net8192su  -- Hardware present: Yes

4. Created a Ad-hoc connection clicking on Network Manager > create new wireless network..

5. Edited the Name, set Security to WEP 128-bit Passphrase and entered my desired password.

6. Finally clicked Create but it says "Wireless Connection disconnected"

I'm thinking about maybe the problem is with my dongle so I checked by using the command:
```
sudo iwconfig wlan0
```
which gives me information about wlan0

The next thing I did worsen the situation. I unplugged the USB dongle ang plugged it again. This time, 
```
sudo iwconfig wlan0
```
gives me no result anymore. 
```
wlan0     No such device
```

Also, the option that says "create new wireless connection" disappeared in my Network Manager Applet now.

Now I have no problem. To restore the "Create new wireless connection" in my Network Manager Applet and finally create a wifi hotspot using my wired connection from pc.

I'd be very much thankful..

If this might help:
```
gonix@kyouka:~$ lsusb
Bus 002 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0ac8:c40a Z-Star Microelectronics Corp. 
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
gonix@kyouka:~$ sudo iwconfig wlan0
wlan0     No such device

```

---

### Post by westie457 on 2011-07-22
Hi it is quite possible you have an incorrect driver. Take a look at this link. It might solve your wireless issues.

[http://ubuntuforums.org/archive/index.php/t-1501914.html](http://ubuntuforums.org/archive/index.php/t-1501914.html)

---

### Post by gonkyouka on 2011-07-22
> **westie457 said:**
> Hi it is quite possible you have an incorrect driver. Take a look at this link. It might solve your wireless issues.

[http://ubuntuforums.org/archive/index.php/t-1501914.html](http://ubuntuforums.org/archive/index.php/t-1501914.html)
Thank you so much for such a quick reply. I'll sort this one out later.. I'm about to go to bed.

Edit:
```
~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91864 r8192 d22824 u1048576
[    0.000000] pcpu-alloc: s91864 r8192 d22824 u1048576 alloc=1*2097152
[    0.335819] pci 0000:00:08.0: reg 1c 32bit mmio: [0xfbefa400-0xfbefa40f]
[   18.661871] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   75.026532] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192su'
[   75.027153] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192su; check system log for messages from 'loadndisdriver'

```

```
~$ sudo modprobe r8192s_usb
[sudo] password for gonix: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
gonix@kyouka:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

At this point, Wireless Networks appears in my Network Manager applet with 'device not ready' grayed out.

Then..
```
~$ dmesg | grep -i firmware
[    1.107999] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.108000] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[43907.427003] rtl819xU: --->FirmwareDownload92S()
[43907.427013] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[43907.570924] rtl819xU:request firmware fail!
[43907.571299] rtl819xU:Firmware Download Fail!!a
[43907.578503] rtl819xU: --->FirmwareDownload92S()
[43907.578511] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[43907.580835] rtl819xU:request firmware fail!
[43907.581202] rtl819xU:Firmware Download Fail!!a
[43908.215628] rtl819xU: --->FirmwareDownload92S()
[43908.215638] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[43908.217977] rtl819xU:request firmware fail!
[43908.218345] rtl819xU:Firmware Download Fail!!a
[43908.228879] rtl819xU: --->FirmwareDownload92S()
[43908.228890] usb 1-2: firmware: requesting RTL8192SU/rtl8192sfw.bin
[43908.231505] rtl819xU:request firmware fail!
[43908.231882] rtl819xU:Firmware Download Fail!!a

```

My Wireless Netword Drivers says:
```
net8192su 
Hardware present: Yes
```

Can anyone point me to the right direction please? I'm totally helpless..

---

### Post by gonkyouka on 2011-07-23
bump

---

### Post by zkhan on 2012-01-08
You will want to use a mesh type wireless network where wireless nodes are interconnected to one another and find the best route to the gateway automatically. You can start with open-mesh.com... they are a free service that allows you to monitor the entire network from any web browser. 

Here's a bit about our software offering incase you have the need to meter / monitor access by device or username...

WiFiRUSH captive portal solution (integrated WiFi-CPA) makes creating a Wireless ISP / HotSpot easy, especially when Ubiquiti or Open-MESH access points are used. Our solution is robust, feature rich, and based on WiFi-CPA, Coovachilli (updated Chillispot), Orange-Mesh integration for robin-node monitoring similar to Open-mesh. 

The control panel options allow the operator to manage an open wireless system for authenticated guest access and an encrypted carrier for private traffic simultaneously on the same device. All the features and settings are controlled centrally with an easy web based control panel. 
Wifirush
If you are interested in trying it out, visit Wifi Rush:Support and request for an invite for a demo account. 
Here is a list of features within our captive portal solution: 
•	Local Content, Advertising 
•	100% customizable Walled Garden, Redirect pages 
•	Multiple Locations 
•	Accept PayPal, Credit Cards 
•	Voucher Access System 
•	Bandwidth Control 
•	MAC Authentication 
•	Firmware / x86 Client 
•	Usage Tracking and Reporting 
•	Express & Advanced HotSpot Modes 
•	100% HotSpot Branding 
•	Local Captive Portal (LAN Interface) 
•	Import User Accounts (.CSV) 
•	Multiple Payment Gateways 
•	Traffic Logging 
•	meshDashboard 
•	mesh Firmware Manager 
•	Multi-Administration Support 
•	Enhanced MAC Authentication 
•	MikroTik Support 
•	HotSpots/AccessPoints
•	Unlimitied HotSpot Profiles 
•	Unlimited Nodes (Gateways)

•	Generate and Print Voucher Codes
WiFi-CPA™ provides the ability to generate and print voucher codes or user accounts based on a variety of parameters. It provides the ability to define valid usage duration, price, expiry date, maximum allowed usage in a session, minimum duration between logins, time interval during which usage is disallowed and more. The codes can be exported in .CSV or .TXT file format and printed on standard A 4 paper or Avery label sheets using any standard printer.
•	User Management
The user management feature of WiFi-CPA™ allows the HotSpot operator to create and manage user accounts. Import .csv file to User Accounts in batches.
•	Usage Monitoring
The HotSpot software allows the HotSpot operator to monitor the usage rate across multiple wireless HotSpot locations. In addition to the ability to view the usage statistics for various time horizons (daily, weekly, monthly, yearly). It also provides detailed graphical charts illustrating the usage.
•	Sales Tracking
The ability to track daily, weekly, monthly and yearly sales for a single wireless HotSpot location or across multiple locations is a key feature of the HotSpot solution . This functionality allows the wireless HotSpot operators to obtain a clear view of the actual performance of the various HotSpot locations in near real time.
It also provides statistical and graphical illustration of the historical sales in various intervals of time.
•	AccessPoint/Node Status
The Control Panel continuously monitors all the wireless HotSpot locations and displays the status of each of these locations (online, off-line, in use). It also sends email or pager alerts (SMS) to the wireless HotSpot operator if any of the locations are down. This critical functionality ensures that the wireless HotSpot network runs without any disruptions. Remotely enable and disable entire HotSpot networks or individual HotSpots.
•	Add New Locations
One of the unique features of WiFi-CPA™ is that it allows the wireless HotSpot operator to instantly add additional new locations to the wireless network. This allows the WISP or the HotSpot operator to expand his wireless network in a rapid manner.
•	Multiple Currency Support
This feature of the control panel allows operators in different countries to specify the usage fee in their local currency.

•	Export/Import data in PDF & Excel
The control panel allows the operators to export user and usage data in PDF and Excel formats.
Import user account in .csv formats.
•	Add Time
The control panel allows the operators to add time to existing Time Codes and User Accounts. In addition, the users can add time by using the online "Manage Account" from the login page..
•	Bandwidth Management
This feature of the control panel allows the operator of the HotSpot to specify usage fees based on various bandwidth plans. The bandwidth plans include rate plans, cumulative data plans (daily and monthly) and plans that are a combination of rate & cumulative.
•	Multiple Payment Gateways
WiFi-CPA™ allows Wireless HotSpot operators to accept payments directly to their PayPal, Google Checkout or merchant account.
•	Free Usage Scenario
This feature is suited for HotSpot operators who provide a free service. Create Packages with zero cost, or use "Express" Login to create a click-and-go login process.
•	Device Authentication
This feature allows devices such as IP phones, etc. to access your HotSpot network using their MAC address.
•	Location based Advertisements
This optional feature allows the operator to display local ads in the login page. For example, a hotel could display the ads of the restaurants nearby thereby generate

---

