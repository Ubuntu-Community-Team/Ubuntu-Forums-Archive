---
title: "Wireless Doesn't work on 9.04 at all"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by wolfteeth on 2009-04-29
Wireless Doesn't work on 9.04 at all

I upgraded my Ubuntu8.10 to 9.04 yesterday and everything is fine but network manager doens't work at all. 
iwconfig, lspci etc are well managed and my laptop is HP NC2400 with Intel PRO 3945ABG

I performed full reinstall to 9.04 again, same problem that network manager doesn't work.

the symptoms is:
problem is even I input the SSID and WPA2 manually, it doens't work, and seems it never work, means, the ICON of network manager never has any changes.. dont like 8.04/8.10, the icon will refresh to get wifi, but 9.04 not...

found lot's of posts here for this problem. but still raise again..

[Resolution Updates on the [below posts]("http://ubuntuforums.org/showpost.php?p=7216418&postcount=15") but may not suite for you]

---

### Post by Bogdon6 on 2009-04-29
I had a similar problem. Here's what worked for me: 

1. Click on System | Administration | Hardware Drivers
2. In the Hardware Drivers dialog box, there's an deactivated item:
Alternate Atheros "MadWifi" driver.
3. Click on Alternate Atheros "MadWifi" driver, the click on "Activate" in the lower left hand corner. Then click close.  
4. Reboot. 

Now wireless works, at least for me.

---

### Post by Cerberus2k7 on 2009-04-29
> **Bogdon6 said:**
> I had a similar problem. Here's what worked for me: 

1. Click on System | Administration | Hardware Drivers
2. In the Hardware Drivers dialog box, there's an deactivated item:
Alternate Atheros "MadWifi" driver.
3. Click on Alternate Atheros "MadWifi" driver, the click on "Activate" in the lower left hand corner. Then click close.  
4. Reboot. 

Now wireless works, at least for me.

I checked in mine.  It's completely empty and says "No preprietary drivers are in use on this system." :confused:

---

### Post by t0mppa on 2009-04-29
The madwifi driver is only offered as a secondary driver for 9.04, ath5k should work better for Jaunty, when you have an Atheros card. Intel cards have their own drivers, which require a different set up.

---

### Post by sneakyB on 2009-04-29
> **Cerberus2k7 said:**
> I checked in mine.  It's completely empty and says "No preprietary drivers are in use on this system." :confused:

Also having problems with the wifi driver, as many of you. if I click on activate, I get the message " this driver was just disabled, but is still in use". still, no wifi working... tried rebooting, read forums on how to get it work for hours, but still no go... 
anyone advice?

thanks

---

### Post by tad1073 on 2009-04-29
Wireless for 9.04 w/atheros driver on 64 bit seems to be completely borked.

I have posted in multiple threads about the same issue and no one seems to know how to fix the problem.

I have also filled bug reports at launchpad and [http://bugzilla.gnome.org/enter_bug.cgi?product=NetworkManager](http://bugzilla.gnome.org/enter_bug.cgi?product=NetworkManager)

---

### Post by MarcusA on 2009-04-29
I had to reinstall to get my wireless working again.. :p

---

### Post by tad1073 on 2009-04-29
> **MarcusA said:**
> I had to reinstall to get my wireless working again.. :p

re-installing doesn't work for me.

until there is some kind of conformation that the problem has been resolved, no ubuntu for me

---

### Post by Cerberus2k7 on 2009-04-29
Surprisingly, I got mine to "work" by uninstalling ndiswrapper, and then manually reinstalling it.  But in the process it killed my eth0 connection.  Then I got that back.  Kinda finicky lol.

I followed this: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

---

### Post by blitzer on 2009-04-29
Really weird, Wireless worked great after upgrade but quit after first update.

After the update the window opened up asking to confirm my already set up wireless - network name and password ?

Now I use direct connect AGAIN !  All of these upgrades and still problems with wireless whats up ?

Just getting frustrated  :confused:

---

### Post by Mind5torm on 2009-04-29
Hello...here is your solution...i had the same problem to 8.10 and after upgrading to 9.04.
The thing is that Network Manager comes to an "unmanaged" state by default into system services . So u have to go and change this from its settings via terminal...there is a file called nm-settings.conf as far i remember that u change its value from false to true or otherwise. Then try to give parametres for ur wirelles via terminal . 
i did all this and now i connect and network manager works fine and scans ok and the icon uses its litle graphic when connecting...Forgive me for not remembering the path of the files...its smt like /usr/share/local/networkmanager or /usr/bin/docs/networkmanager.
I read all this from network managers preinstalled documentation with man from terminal...
Hope u r ok...

---

### Post by wolfteeth on 2009-04-29
Are you talking about the file under /etc/NetworkManager/nm-system-settings.conf?

the line: 
[ifupdown]
managed=false

I tried to change to ture, but still same, the icon never changed...the graphic same...:confused:

> **Mind5torm said:**
> Hello...here is your solution...i had the same problem to 8.10 and after upgrading to 9.04.
The thing is that Network Manager comes to an "unmanaged" state by default into system services . So u have to go and change this from its settings via terminal...there is a file called nm-settings.conf as far i remember that u change its value from false to true or otherwise. Then try to give parametres for ur wirelles via terminal . 
i did all this and now i connect and network manager works fine and scans ok and the icon uses its litle graphic when connecting...Forgive me for not remembering the path of the files...its smt like /usr/share/local/networkmanager or /usr/bin/docs/networkmanager.
I read all this from network managers preinstalled documentation with man from terminal...
Hope u r ok...

---

### Post by Mind5torm on 2009-04-30
Yes exactly the one is this and the other one is a file inside /etc/Network/interfaces...i ve changed manually login as root and set up my wifi connection as the default. After rebooting it showed me the netwrok manager like it should be. Nm-system-settings.conf is at /etc/networkmanager/ if u want to change it back...The thing is that now that its working ok , it doesnt autoconnect although i have it to auto for this connection...i need to run ifdown every time i boot....weird thing...hope i ve helped u...ubuntu 9.04 also "sugested" me a driver after updating and i installed it...previously i was working with my windows wirelles driver. Hope i ve helped u...

---

### Post by wolfteeth on 2009-05-04
No, it doesn't work for me and not fully understand what you are saying about the other one file, do you mean /etc/network/interfaces? to input wireless connection on interfaces file?

> **Mind5torm said:**
> Yes exactly the one is this and the other one is a file inside /etc/Network/interfaces...i ve changed manually login as root and set up my wifi connection as the default. After rebooting it showed me the netwrok manager like it should be. Nm-system-settings.conf is at /etc/networkmanager/ if u want to change it back...The thing is that now that its working ok , it doesnt autoconnect although i have it to auto for this connection...i need to run ifdown every time i boot....weird thing...hope i ve helped u...ubuntu 9.04 also "sugested" me a driver after updating and i installed it...previously i was working with my windows wirelles driver. Hope i ve helped u...

---

### Post by wolfteeth on 2009-05-05
I finally get the network manager works...

I tried to remove network manager and install wicd, found it doesn't work at all.

I have to remove wicd and reinstall network manager again.

and then, click the Network manager icon and select "Connect to Hidden wireless Network"

Input&Select the SSID, WPA2

It asks to select cer or make it in insecure, I agreed

It then asks to store a new password key, input "xxxxxx", where, xxxxxx is a password key you expected

after doing so, the network manager Icon refresh and recycling...

it works now.....

---

### Post by xyverz on 2009-05-08
I lost count of how many times I installed WICD and Network-Manager.  It never worked for me.

What has worked for me was re-enabling the SSID broadcast.  Not the best method, but I can get rid of my WEP SSID now.

So for me: hidden SSID + WPA2 + Ubuntu 9.04 == teh suck.  visible SSID + WPA2 + Ubuntu 9.04 == WIN!

It might be worth noting that I'm running a MBP 4,1 version.  Everything else BUT the wireless worked perfectly, right out of the box.

---

### Post by Mars73 on 2009-05-24
> **xyverz said:**
> 
What has worked for me was re-enabling the SSID broadcast.  Not the best method, but I can get rid of my WEP SSID now.

So for me: hidden SSID + WPA2 + Ubuntu 9.04 == teh suck.  visible SSID + WPA2 + Ubuntu 9.04 == WIN!


Looks exactly the same here.
I've tried almost a hundred things, thinking there was something wrong with the driver (have a Belkin usb wireless g), nm, wicd, kernel, Samba etc etc.
One of the things I use Ubuntu for is to stream movies to my Xbox downstairs and with 9.04 it always disconnected after a while.
Turning on ssid broadcast seems to be the answer, although I had it always on disabled with previous Ubuntu versions. Guess it won't hurt that much as it's not really protecting. Be sure to use WPA(2).
As a positive side effect I got full speed with ssid enabled and with ssid disabled I got 1/3th of the speed.

---

### Post by ToshiLaptopUser on 2009-05-27
First, let me say hello. I am new to gnome and [ubuntu]. I am a Toshiba Satallite, L305D-S5874, AMD Mobile Athlon X2. I have installed the hardware driver from the administration option. I have the "madwifi" driver set to active. I under network tools option, this is unknown interface. Here is the problem, Wireless connection does not work :(. I am currently an engineering student at community college and am trying this out over the pre-installed Windows Vista 32bit. I really hate Windows Vista. Someone please help me?!?! I forgot to mention that my wireless card is a AR5004EG AR242x 802.11abg Wireless PCI Express Adapter. Thanks!!

---

### Post by ToshiLaptopUser on 2009-05-31
Well, I'm not sure how, but I resolved my own issue by uninstalling Ubuntu, then restarted with a clean install. So far my wireless connection has been flawless.:p

---

