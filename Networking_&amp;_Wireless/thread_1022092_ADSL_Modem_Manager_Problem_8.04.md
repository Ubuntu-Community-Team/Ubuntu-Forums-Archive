---
title: "ADSL Modem Manager Problem 8.04"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by walk.away on 2008-12-26
Hi. I recently bought a Asus Eee 901. and have just installed Ubuntu-eee (now Easy Peasy i think) to be able to install usbadslmodemmanager to be able to go on the internet using the crappy Speedtouch Modem i have to use (v4.0).

I have managed to install v0.5.8
i insert all my online details to configuration then it "syncronizes" and says 800k/bits down and 300k/bits up but there is no connection to the internet. When i click "connect" nothing happens. 

When installing the firmware for the modem i got a message saying 
> "The Firmware needs to be copied to /lib/firmware For this to happen Root privileges are needed"
then upon clicking ok it says firmware has been installed remove then reconnect the modem.

i ran usbasdlmodemmanager in console as others have to see what results i got.
> parry@Parry-Eee:~$ usbadslmodemmanager
USB Adsl Modem Manager V0.5.8 (2008/12/26 15:43:09)
Root is /usr/share/apps/usbadslmodemmanager
sudo command will be gksudo
about to load path : /usr/share/apps/usbadslmodemmanager/data/langs.xml
xmllangs: XML file succesfully parsed
Language selected is : English
test language is working: The New Firmware has been installed
Please unplug, then re-plug in the Modem
Status Started
checking : ps -ef | grep "pyt[h]on ./USBAdslModemManager.py"
Updating Status!
----------STARTING DETECTION----------
ifconfig returns error ppp0: error fetching interface information: Device not found
DET : Stage 1 Firmware Found in dmesg at line 612
DET : Stage 2 Firmware Found in dmesg at line 613
DET : lsusb response is 4.00
DET : Modem Found in lsusb -vvv : 4.00
DET : synchronising found in dmesg at line 614
DET : ADSL Line is up found in dmesg at line 615 details: (768 kb/s down | 352 kb/s up)
ifconfig returns error ppp0: error fetching interface information: Device not found
----------GENERATED STATUS----------
noModem: False
actual_firmwareOk: True
actual_modemConnected: True
actual_syncronizing: False
self.status_lineUp: True line: 615
self.status_lineDown: False line: 0
actual_connected: True
connection_ip_detail: 
----------Tool Tip-----------
Modem Speedtouch 330 V4.00
Line status: Synchronized
(768 kb/s down | 352 kb/s up)
Changing tray to : /usr/share/apps/usbadslmodemmanager/icons/modem_synced.png
Updating Status!



I have been using this for about a day. And i have no knowledge for coding etc. But if anyone has had experience of this problem or admins could advise then it would be greatly appreciated.

---

