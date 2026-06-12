---
title: "Flying Angel HSDPA USB Modem"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by nazerim on 2009-10-03
I have successfully installed and configured this USB Modem on 9.04. When plugged in it identifies itself as a CDROM with label Flying Angel - lsusb reports the device as ID 1d09:1025 .

1. To switch to HSDPA Modem mode, issue an eject command to the device, in my case:[INDENT]  [FONT=Courier New]eject /dev/sr1
[/FONT][/INDENT]2. The modem can use the option driver:[INDENT] [FONT=Courier New]modprobe -v option
echo "1d09 1026" >/sys/bus/usb-serial/drivers/option1/new_id
[/FONT][/INDENT]3. To connect to my ISP (Maxis prepaid broadband in Malaysia), the noremoteip option is required. This is not supported by NetworkManager, therefore I needed to use my own scripts. 

The HSDPA modem will be attached to the third ttyUSB device. On my configuration, with no other serial USB devices, the assigned numbers start with 0, therefore the device is /dev/ttyUSB2.

The following pppd options are needed (save to /etc/ppp/peers/maxis).
[FONT=Courier New]
[/FONT][B]/etc/ppp/peers/maxis
[/B][INDENT][FONT=Fixedsys][FONT=Courier New]/dev/ttyUSB2 
921600 
modem 
crtscts 
defaultroute 
usehostname
noipdefault
usepeerdns 
idle 0 
logfd 6
noauth
usepeerdns
noremoteip
replacedefaultroute
connect "/usr/sbin/chat -v -f /etc/chatscripts/maxis-connect"
disconnect "/usr/sbin/chat -v -f /etc/chatscripts/maxis-disconnect"[/FONT]
[/FONT][/INDENT]4. The maxis-connect scripts are given below. The SIM card has the CID configuration for Maxis prepaid broadband in CID slot 2, 

[B]/etc/chatscripts/maxis-connect
[/B][INDENT][FONT=Courier New]TIMEOUT         5[/FONT]
[FONT=Courier New] ECHO            ON[/FONT]
[FONT=Courier New] ABORT           '\nBUSY\r'[/FONT]
[FONT=Courier New] ABORT           '\nERROR\r'[/FONT]
[FONT=Courier New] ABORT           '\nNO ANSWER\r'[/FONT]
[FONT=Courier New] ABORT           '\nNO CARRIER\r'[/FONT]
[FONT=Courier New] ABORT           '\nNO DIALTONE\r'[/FONT]
[FONT=Courier New] ABORT           '\nRINGING\r\n\r\nRINGING\r'[/FONT]
[FONT=Courier New] ''              \rAT[/FONT]
[FONT=Courier New] TIMEOUT         12[/FONT]
[FONT=Courier New] OK        'ATX3'[/FONT]
[FONT=Courier New] OK        'ATE0V1'[/FONT]
[/INDENT][INDENT][FONT=Courier New] # Set the APN if needed below. If you uncomment this, comment out the last ATD[/FONT]
[FONT=Courier New] #OK              'AT+cgdcont=1,"IP","unet"'[/FONT]
[FONT=Courier New] #OK              ATD*99#[/FONT]

[FONT=Courier New] # Dial SIM card default configuration 2 (Maxis prepaid broadband)[/FONT]
[FONT=Courier New]  OK              ATD*99*1,2#[/FONT]

[/INDENT][B]/etc/chatscripts/maxis-disconnect
[/B][INDENT] [FONT=Courier New]ABORT        "BUSY"        
ABORT        "ERROR"        
ABORT        "NO DIALTONE"    
SAY        "\nSending break to the modem\n"    
""        "\K"        
""        "\K"        
""        "\K"        
""        "+++ATH"    
""        "+++ATH"    
""        "+++ATH"    
SAY        "\nPDP context detached\n"

[/FONT][/INDENT]5. To start the connection:[INDENT][FONT=Courier New]pon maxis[/FONT]
[/INDENT]6. To disconnect, remove the modem or[INDENT] [FONT=Courier New]poff
[/FONT][/INDENT]7. Using udev, the setup (eject) and connection can be automated.

Example entries in udev rules:[FONT=Courier New]
[/FONT][INDENT][FONT=Courier New] # CD-ROM (pci-0000:00:1d.7-usb-0:1:1.0-scsi-0:0:0:0)[/FONT]
[FONT=Courier New] # Replace xxxx with the actual serial number[/FONT]
[FONT=Courier New] ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="TF--UMTS_CD-ROM_xxxxxxxxxxxxxxx-0:0", RUN+="/usr/bin/eject /dev/%k", ENV{GENERATED}="1"[/FONT]

[FONT=Courier New] # Flying Angel[/FONT]
[FONT=Courier New] SYSFS{idVendor}=="1d09", SYSFS{idProduct}=="1026", RUN+="/usr/sbin/flyingangel.sh"[/FONT]

[/INDENT][FONT=Courier New] **/usr/sbin/flyingangel.sh **[/FONT][INDENT][FONT=Courier New]#!/bin/sh[/FONT]
[FONT=Courier New] /usr/sbin/flyingangel-option.sh &[/FONT]

[/INDENT][FONT=Courier New] **/usr/sbin/flyingangel-option.sh **[/FONT][INDENT][FONT=Courier New]#!/bin/sh[/FONT]

[FONT=Courier New] # Enable interface[/FONT]
[FONT=Courier New] modprobe -v option[/FONT]
[FONT=Courier New] echo "1d09 1026" >/sys/bus/usb-serial/drivers/option1/new_id[/FONT]

[FONT=Courier New] # Test until /dev/ttyUSB2 comes up to dial (may take up to a minute!)[/FONT]
[FONT=Courier New] while [ ! -e /dev/ttyUSB2 ]; do[/FONT]
[FONT=Courier New]     sleep 10[/FONT]
[FONT=Courier New] done[/FONT]

[FONT=Courier New] # Wait a while then dial[/FONT]
[FONT=Courier New] sleep 5[/FONT]
[FONT=Courier New] /usr/bin/pon maxis[/FONT]

[FONT=Courier New] # Removing the modem will disconnect[/FONT]
[/INDENT]Hope this helps

---

