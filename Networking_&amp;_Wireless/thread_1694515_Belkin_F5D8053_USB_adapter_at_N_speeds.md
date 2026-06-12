---
title: "Belkin F5D8053 USB adapter at N speeds?"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by jw1949 on 2011-02-24
Thanks to the forum (yes you Chilli), my adapter is connecting but using Driver - usb and reporting a speed of 54Mbps.  I want to achieve N speeds to stream video to an ASUS media player in another room.  I am an older guy and a Linux newbie but trying to learn!


jack@jack-desktop:~$ **_lsusb_**
Bus 004 Device 003: ID 0b05:1715 ASUSTek Computer, Inc. 2045 Bluetooth 2.0 Device with trace filter
Bus 004 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 050d:815c Belkin Components F5D8053 N Wireless USB Adapter v3000 [Ralink RT2870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2011-02-24
Getting N speeds is tricky. Reading here, it seems that some are successful and some not: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/377745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/377745)

I'd suggest you make sure rt2800usb and it's rt2x00 henchmen are blacklisted. Also, do:```
sudo gedit /etc/Wireless/RT2870STA/RT2870STA.dat
```Make sure the WirelessMode= value is present and is WirelessMode=5 or 9.

Beyond that, I have no more suggestions.

---

### Post by jw1949 on 2011-02-24
When I go into gedit for rt2870sta.dat, it is empty ?

---

### Post by chili555 on 2011-02-24
Let's add two lines:```
Default
WirelessMode=5
```Proofread, save and close gedit. Now check:```
cat /etc/Wireless/RT2870STA/RT2870STA.dat
```You should see our two lines. Now do:```
sudo rmmod -f rt2870sta
sudo modprobe rt2870sta
```Any improvement?

---

### Post by jw1949 on 2011-02-24
No, no difference.  Does the upper case lower case make any difference ?

---

### Post by chili555 on 2011-02-24
> Does the upper case lower case make any difference ?Well, absolutely! In this and every other file in Linux and Ubuntu, case matters. This:> /etc/Wireless/RT2870STA/RT2870STA.datis definitely not the same as this:> /etc/Wireless/RT2870STA/rt2870sta.datNor this:> /etc/Wireless/rt2870sta/RT2870STA.datOne will not work in place of the other and Ubuntu is not going to second-guess; it's either correct or incorrect. Do you want to go back and check your work?

---

### Post by jw1949 on 2011-02-25
Understood!  Apologies for delay - we have a time difference and the boss assigned me to other duties this am.

1.  On the upper/lower case question, I have now checked my work and it is OK - I can see our 2 lines.  I had to create a Wireless directory in /etc and an RT2870STA directory below that before I could save the .dat file to the right place.   However, I'm not sure why I did not have these directories in the first place !

2. The network applet still says the driver is usb and the speed is 54Mb/s.

3. I ought to have said earlier that I also have a PCI Wireless card on this desktop - called an Atheros AR5008.  Both devices are set to NOT connect automatically so I choose which after a reboot.

4.  I perhaps also should have said that I am connecting to a Belkin N router - F5D8633uk4.  This is providing home network coverage and is linked by LAN cable to a Netgear DG834GT router which is providing DHCP and the connection to the internet.  

5.  This adapter F5D8053 - and the adapter in the ASUS media player are the only N rated devices in my network (other than my wife's iPad?) so the Belikin is set to accept G and N connections with no security at present.  I plan to add security when I have everything working; or should that be IF?

Jack

---

### Post by chili555 on 2011-02-25
> I plan to add security when I have everything working; or should that be IF?As far at I can tell, you have everything working; just not at N speeds. I suggest security at once. Incidentally, either Network Manager or wpa_supplicant or the driver has trouble with mixed WPA *AND* WPA2 mode. I suggest WPA2 only.

I wish I knew what else to suggest to get N speeds. I'm fresh out of ideas.

---

### Post by jw1949 on 2011-02-28
BELKIN F5D8053

I placed a query with Belkin support as follows:

Question Reference #110226-000837
Family: 	Network Adapters
Technology: 	N
Model: 	F5D8053uk
Version: 	v3000
Category Level 1: 	Software and Drivers
Category Level 2: 	Driver
Date Created: 	25/02/2011 05.04 PM
Last Updated: 	25/02/2011 09.25 PM
Status: 	Waiting
Operating System: 	Linux

Adapter connects OK but shows speed at 54Mb/s - should be higher - 300Mb/s?

I am connected to F5D8633uk4 router and need N speeds to stream video from this desktop to an ASUS media player.

and received the following response:

Dear Belkin Customer,

Thank you for contacting Belkin Technical Support.

I understand your concern and I will be happy to assist you with the same.

Please try changing the secrutiy mode on the router to WPA2 PSK with AES Encription technique and check if the issue persist.

Follow the steps to reset the WiFi password:

- Open a browser on the computer that is connected to the router 
- In the address bar type in 192.168.2.1 and hit "Enter".
- Click on "Channel and SSID" under "Wireless".
- Leave the password blank and click Submit". 
- Change the SSID to a new name. For example Home_Network(no space between words).
- Change wireless channel to 1 or 6 or 11.
- Apply changes.
- Click on "Wi-Fi Protected Setup" under "Wireless".
- Under the heading "Wi-Fi Protected Setup", click on the drop down and choose "Disable".
- Apply the changes.
- Click on "Security" under the heading "Wireless".
- Choose WPA/WPA2 from the drop down right next to Security Mode.
- Choose Authentication as WPA2 PSK and Encryption technique as AES only.
- Enter your password across Preshared PSK.
- Click on "Apply Changes".

Make a note of the SSID and the Preshared PSK. SSID would be the network name and Preshared PSK would be the wireless password. You will have to reconnect all the wireless devices to the network using the new password.

Follow the steps accordingly:

Please follow the steps on wireless XP:

- Click "Start" on the bottom left hand side of your computer screen and go to “Control Panel".
- Click "Network and Internet Connections" and then choose "Network Connections".
- We would find "Wireless Network Connection" icon.
- Right click on the icon and choose "Properties". In the “Wireless Network Connection Properties" window, we should find 3 tabs on the top. "General",
"Wireless Networks" and "Advanced".
- Click "Wireless Networks". We would find "Available Networks" and "Preferred Networks". Under "Preferred Networks", highlight all the available networks one by one and click on "Remove". "Preferred Networks" should be completely blank. Click "OK".
- We would be back on the "Network Connections" window. Right click on the "Wireless Network Connection" and choose "View Available Wireless Networks".
- We would find a list of networks. Choose your network and try connecting.

Please follow the steps on wireless Windows Vista:

- Click "Start" on the bottom left hand side of your computer screen and choose "Control Panel".
- Click on "Network and Internet" and then "Network and Sharing Center".
- In the "Network and Sharing Center" window, click "Manage wireless networks" on the top left hand side.
- Remove all the networks under "Preferred Network". Close all the windows.
- On the desktop or the main screen of the computer, click "Start" and choose "Connect To".
- A window would come up showing all the available networks. Highlight your network and click "Connect".

Please follow the steps on wireless Windows 7:

- Click "Start" and then "Control Panel"
- In the "Control Panel" window, click "View network status and tasks" under "Network and Internet"
- Towards the left, we would find "Manage Wireless Networks"
- Select the preferred network and click “remove” on the top of the window
- After removing the preferred networks, please ensure that we are on the "Network and Sharing Center" window
- Click "Connect to a network" under "Change your network settings"
- It would show all available networks. Highlight your network and connect to it.

If the issue persist, get back to us with the following information:

1. Please confirm if the model number is F5D8053 v3000.
2. Are you getting better speed on other computers?
3. Please confirm if the model number of the router is F5D8633. What is the version number of the router?

---

### Post by jw1949 on 2011-02-28
I have now responded to Belkin as follows:

 I have implemented security as you suggested but as stated in my original post, I am not using Windows but have Linux Ubuntu 10.10 installed.  The system is connected OK, but the speed is still reported as 54Mbps.

1. the model number is ver3004uk
2. I have not tested on another computer.
3. the router is ver1000uk.

Can you please advise the next steps ?

---

