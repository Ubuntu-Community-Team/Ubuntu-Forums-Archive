---
title: "Problem with D-Link DWL-520e and ndiswrapper"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by fsleeman on 2009-09-10
I am working from a fresh install of Ubuntu 9.04 and have installed ndisgtk (with ndiswrapper common + utils) and have loaded this driver: [http://www.findmysoft.com/drivers/download-D-Link-DWL-520E-1-0-network-card-driver.html](http://www.findmysoft.com/drivers/download-D-Link-DWL-520E-1-0-network-card-driver.html)


When I install the driver using ndisgtk, I get a message "Unable to see if hardware is present" although the icon on the right has the text "Hardware present: yes". When I click on "Configure Network" I get this message "Could not find a network configuration tool". I have googled this and found many questions and no answers.

iwconfig gives:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

lshw -C Network gives: 
...
*-network DISABLED
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wifi0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=0.0.0 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11-DS

Any suggestions on what to do? I have read many message board posting and help guides without success. I also have a TRENDnet TEW-423PI card but I haven't gotten that one to work either.

---

### Post by fsleeman on 2009-09-10
Also should note I tried the firmware trick here: [https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1](https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1) which also didn't work.

I did see this in /var/log/dsmeg:
[    9.767432] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netprism'
[    9.767940] ndiswrapper (load_wrap_driver:108): couldn't load driver netprism; check system log for messages from 'loadndisdriver'

I am running the 64bit Ubuntu version, should I revert back to the 32 bit version? I have read some people have had issues with the 64bit of the OS.

---

### Post by fsleeman on 2009-09-11
I have reverted back to 32-bit Ubuntu in hopes it will help. I was able to get the card to show up as UNCLAIMED which I assume is a step in the right direction. The Network Manager how shows "Wireless Networks" greyed out with text about the wireless not being managed. ndisgtk still cannot find a network configurator and listed the hardware as present.

---

