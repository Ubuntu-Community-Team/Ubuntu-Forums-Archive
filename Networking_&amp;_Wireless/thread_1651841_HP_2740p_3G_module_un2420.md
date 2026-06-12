---
title: "HP 2740p 3G module un2420"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by mzaharinov on 2010-12-23
Hello
I have a problem with 3G module un2420.
Once loaded system lsusb does not show Qualcomm module.
What is a problem?
My system is Ubuntu 10.10 with Kernel 2.6.35-24.
Help please.

---

### Post by ottosykora on 2010-12-24
if you still have windows installed, then try to switch it on there, then just reboot (not switch off) and see again.

you also need to install gobi-loader from repository

---

### Post by mzaharinov on 2010-12-24
Hi 
i back to windows and switch on connection.
but in ubuntu not work gobi_loader 0.7-1 is a version .
i run gobi_loader not work still on _ 
not load firmware in Gobi module.
what is a this problem.
I'am from Bulgaria my GSM provider is Globul.

P.S.
And in Network Manager not found Mobile connection Add button.

---

### Post by mzaharinov on 2010-12-24
Gobi loader after reset from windows load firmware and still wait. 
I kill gobi_loader and run again and not work.
Copy firmware from Windows folder .
/lib/udev/gobi_loader -2000 /dev/ttyUSB0 /lib/firmware/gobi

in lsusb :

Bus 001 Device 004: ID 03f0:241d Helett-Packard Gobi 2000 Wireless Modem (QDL mode)

Update Ubuntu to 11.04 and not work.

How to add connection in Network Manager.
and 3G Radio On/Off where is search on /sys/*.


And GPS modul in Gobi 2000 how to find not list in /dev/ttyUSBx.

Thanks for Help.
m.

---

### Post by ottosykora on 2010-12-25
I am not sure if I can help, since I am still fighting with the module myself.

OK , you have in your usb list now, thats fine.

The question is also if you have the right firmware for the provider. In the packages there are often about 10 different files with same name. I read somewhere to take the one from folder 6, this should be the default one, but who knows.

then someone created such script:

#!/bin/sh
rfkill unblock wwan
sleep 5
stop network-manager
killall modem-manager
sleep 3
/lib/udev/gobi_loader /dev/ttyUSB0 /lib/firmware/gobi
start network-manager
sleep 0.5
exit 0

So, I run windows frst, to switch the device on. Then reboot to ubuntu, run the script and then reboot again.
Then the device might ask you for the PIN and from there on it should appear in the network manager , you can select then the provider etc and set the connection up.

Still it is some kind of try, not allways I manage to make it work , sometimes I have to reboot few times.

---

### Post by mzaharinov on 2010-12-26
OKi i found a problem or Bug in gobi loader .

Boot Windows load a firmware to Gobi 2000 modul.
After restart windows and run ubuntu not shutdown Laptop restart only Gobi Mobile Broadband work perfect.
After shutdown laptop and run again on boot a system stay in gobi_loader and not run system. I kill gobi-loader system boot and no found Mobile Broadband modem.
in lsusb modem is a QDS mode and on /dev/ttyUSB0 only found.
After Restart to Windows and back to Ubuntu on lsusb no QDS Mode onli Wireless found and on /dev/ttyUSB found 0,1 
0 is a QDS mode and ttyUSB1 is a GSM Modem and MObile connection is work. in /dev/ttyUSB not found USB2 this is a GPS modul.

Need to fix gobi_loader to load firmware and qcserial kernel modul to found ttyUSB2 for GPS.
Or need to fix qcserial to fix Load Firmware and GPS .

?

Thanks again.

P.S.
And this script not need to work GSM connection.
After this step modem work perfect.

---

### Post by mzaharinov on 2010-12-26
Hi again
I Found problem and fast solution in this moment while fix bug in gobi_loader or qcserial.

Fix: 

Goto windows and Uninstall Gobi Driver 
After this go to intall directori of Gobi Driver and Edit "MultiInstaller.ini" and Change line:

[GPS-Disable]
Dev1=GPS=0 
to
Dev1=GPS=1

Save fail and run Launcher.exe install driver and restart system.
Windows now install Driver for GSM Modem and GPS modul.

Now restart system not shutdown and go to Ubuntu:
Th&#1077;re found in /dev 
ttyUSB0 (Diagnostic Monitoring port)
ttyUSB1 (GSM Modem)
ttyUSB2 (GPS Module)

go to Network Manager and add Mobile Connection.

This method works only as a restart from Windows to Ubuntu.
If you run the system directly into the Ubuntu environment gobi_loadera block and do not want the system to boot. You can go with Ctrl + alt + F1 to log as root and kill gobi_loader. To boot Ubuntu.

Should be fine qcserial or gobi_loader to load firmware in the module.
For the moment, I invented as a solution.

To run GPS you need :
Go to Terminal and write this :

echo -n "\$GPS_START" > /dev/ttyUSB2        -   To Start GPS
echo -n "\$GPS_STOP" > /dev/ttyUSB2        -   To Stop GPS


This metod is work Fine in Ubuntu 11.04 Alpha 1 and System is HP 2740p with un2420 Gobi2000 Module.

Any help to fix the problem with loading the firmware without loading Windows please write here I can test at any time.
I will be grateful in advance.

---

### Post by ottosykora on 2010-12-26
whoou!

OK, to switch on the GPS, I did not attempt so far also under windows. I operate it there under XP, just by the use of the connection manager or what they call it from HP. This did work out of the box there, so I di dnot investigate further about the gps, but will try some day.

I also see, that you did not find a way to power on the device properly from linux, as most other people did confirm.

The excat reason however, why I have to kill the network manager and modem manger in order to load the firmware.

---

### Post by mzaharinov on 2010-12-26
Hi again


After kill the network manager and modem manger qcserial is reset da Gobi modul and not functional to firmware update.
Need qcserial and gobi_loader to upload firmware complet to modul.

Ubuntu team need to fix this.

For GPS on WindowsXP change in Multiinstaller and run your gps.

---

### Post by ottosykora on 2010-12-30
hmmm, strange, I also di dnot understand all first, but on my HP mini, I reall need to kill both first, then restart again. OK, the qcserial is then still running, but the rest not? And so during this time I am bale to upload the firmware?

From my side it looks like this is so, but it seems all somehow strange.

---

