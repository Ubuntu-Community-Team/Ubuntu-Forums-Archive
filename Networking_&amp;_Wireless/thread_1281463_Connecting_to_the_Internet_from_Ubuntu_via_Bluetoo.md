---
title: "Connecting to the Internet from Ubuntu via Bluetooth through Blackberry"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by krish.nagarajan on 2009-10-03
This article is mainly from the perspective of an eeePC (or any laptop) though it should work on any machine with Ubuntu and Bluetooth. <BR> <BR>

 **Step 1: Pair the Blackberry and the PC via Bluetooth - use the PIN 0000. **

You will need to set the Bluetooth **Discoverable** options on the Blackberry to **Yes**. Also set the Blackberry to not ask again (trusted). 

 Further steps are on the PC / laptop. 

 **Step 2: Run hcitool as follows :** 

 [FONT=Courier New]hcitool scan 
[/FONT] 
Sample output:

 [FONT=Courier New]Scanning ...
    00:25:57:04:E0:BC    BlackBerry 9000 
[/FONT] 
**Note down the MAC address in the output above. **
 [B]
Step 3: Search for DUN channel over Bluetooth.
Run the following command[/B]

 [FONT=Courier New]sdptool search 00:25:57:04:E0:BC 
[/FONT] 
**Sample output:**
  [FONT=Courier New]Browsing 00:25:57:04:E0:BC ... 
[/FONT] 
[FONT=Courier New]Service Name: Dialup Networking

Service RecHandle: 0x10000

Service Class ID List:

  "Dialup Networking" (0x1103)

  "Generic Networking" (0x1201)

Protocol Descriptor List:

  "L2CAP" (0x0100)

  "RFCOMM" (0x0003)

    Channel: 1

Profile Descriptor List:

  "Dialup Networking" (0x1103)

    Version: 0x0100

Service Name: Headset

Service RecHandle: 0x10001

Service Class ID List:

  "Headset Audio Gateway" (0x1112)

  "Generic Audio" (0x1203)

Protocol Descriptor List:

  "L2CAP" (0x0100)

  "RFCOMM" (0x0003)

    Channel: 2

Language Base Attr List:

  code_ISO639: 0x656e

  encoding:    0x6a

  base_offset: 0x100

Service Name: Hands-free

Service RecHandle: 0x10002

Service Class ID List:

  "Handsfree Audio Gateway" (0x111f)

  "Generic Audio" (0x1203)

Protocol Descriptor List:

  "L2CAP" (0x0100)

  "RFCOMM" (0x0003)

    Channel: 3

Language Base Attr List:

  code_ISO639: 0x656e

  encoding:    0x6a

  base_offset: 0x100

Profile Descriptor List:

  "Handsfree" (0x111e)

    Version: 0x0105

Service Name: BlackBerry Desktop Service P:0x211211F9 R:0x07 V:0x20104

Service RecHandle: 0x10003

Service Class ID List:

  UUID 128: 426c6163-6b42-6572-7279-44736b746f70

  "Serial Port" (0x1101)

Protocol Descriptor List:

  "L2CAP" (0x0100)

  "RFCOMM" (0x0003)

    Channel: 4

Language Base Attr List:

  code_ISO639: 0x656e

  encoding:    0x6a

  base_offset: 0x100

Service Name: BlackBerry Bypass Service P:0x211211F9 R:0x07 V:0x20003

Service RecHandle: 0x10004

Service Class ID List:

  UUID 128: 426c6163-6b42-6572-7279-427970617373

  "Serial Port" (0x1101)

Protocol Descriptor List:

  "L2CAP" (0x0100)

  "RFCOMM" (0x0003)

    Channel: 5

Language Base Attr List:

  code_ISO639: 0x656e

  encoding:    0x6a

  base_offset: 0x100

Service Name: Advanced Audio

Service Provider: BlackBerry

Service RecHandle: 0x10005

Service Class ID List:

  "Audio Source" (0x110a)

Protocol Descriptor List:

  "L2CAP" (0x0100)

    PSM: 25

  "AVDTP" (0x0019)

    uint16: 0x100

Profile Descriptor List:

  "Advanced Audio" (0x110d)

    Version: 0x0100

Service Name: A/V Remote Control TG

Service Provider: BlackBerry

Service RecHandle: 0x10006

Service Class ID List:

  "AV Remote Target" (0x110c)

Protocol Descriptor List:

  "L2CAP" (0x0100)

    PSM: 23

  "AVCTP" (0x0017)

    uint16: 0x100

Profile Descriptor List:

  "AV Remote" (0x110e)

    Version: 0x0100

Service Name: SIM Access

Service RecHandle: 0x10007

Service Class ID List:

  "SIM Access" (0x112d)

  "Generic Telephony" (0x1204)

Protocol Descriptor List:

  "L2CAP" (0x0100)

  "RFCOMM" (0x0003)

    Channel: 6

Profile Descriptor List:

  "SIM Access" (0x112d)

    Version: 0x0101

Service Name: Phonebook Access PSE

Service RecHandle: 0x10008

Service Class ID List:

  "Phonebook Access - PSE" (0x112f)

Protocol Descriptor List:

  "L2CAP" (0x0100)

  "RFCOMM" (0x0003)

    Channel: 7

  "OBEX" (0x0008)

Language Base Attr List:

  code_ISO639: 0x656e

  encoding:    0x6a

  base_offset: 0x100

Profile Descriptor List:

  "Phonebook Access" (0x1130)

    Version: 0x0100
[/FONT]                                                                                                                         

[FONT=Courier New]
[/FONT] **Note down the channel associated with Dialup Networking - it is Channel 1 in the this example **

[FONT=Courier New]Service Name: Dialup Networking

[/FONT] [FONT=Courier New]Service RecHandle: 0x10000

[/FONT] [FONT=Courier New]Service Class ID List:

[/FONT] [FONT=Courier New]  "Dialup Networking" (0x1103)

[/FONT] [FONT=Courier New]  "Generic Networking" (0x1201)

[/FONT] [FONT=Courier New]Protocol Descriptor List:

[/FONT] [FONT=Courier New]  "L2CAP" (0x0100)

[/FONT] [FONT=Courier New]  "RFCOMM" (0x0003)

[/FONT] [FONT=Courier New]    Channel: 1
[/FONT]

**Step 4: Edit /etc/bluetooth/rfcomm.conf and add / uncomment / edit following lines**
 
[FONT=Courier New]#
# RFCOMM configuration file.
#

rfcomm0 {
#    # Automatically bind the device at startup
    bind yes;
#
#    # Bluetooth address of the device
    device 00:25:57:04:E0:BC;
#
#    # RFCOMM channel for the connection
    channel    1;
#
#    # Description of the connection
    comment "Krish's Blackberry  Bold 9000";
} 

[/FONT] **Update the device and channel with the MAC address and channel noted in steps 2 and 3 respectively.**


 [B]Step 5: Create /dev/rfcomm0. 
Run[/B]
  
[FONT=Courier New]sudo rfcomm bind 0 00:25:57:04:E0:BC 1 [/FONT][B] [FONT=Courier New]
[/FONT]
Replace the MAC address with the BB MAC address and 1 with the Channel noted down in Step3 [/B]
 [B]

Step 6:  Create pppd config files as follows:[/B]

 **/etc/ppp/peers/blackberry containing**
 
[FONT=Courier New]nodetach
/dev/rfcomm0
115200
connect "/usr/sbin/chat -f /etc/ppp/peers/blackberry-connect"
defaultroute
lcp-echo-failure 0
crtscts
usepeerdns
user ""
password "" [/FONT][B][FONT=Courier New]
[/FONT]
Note: If your mobile provider requires a User/Password enter this in this file.[/B]
 [B]
/etc/ppp/peers/blackberry-connect containing[/B]
 
[FONT=Courier New]ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED ABORT ERROR
SAY "Initializing\n"
'' ATZ
OK-AT-OK ATDT*99#
CONNECT \d\c
[/FONT][B]
Note: If the dialup sequence for your provider is not *99# update the respective line here. [/B]
 [B] Note2: You might need to omit the line  CONNECT \d\c

[/B]** Step 7: Set permissions on /etc/ppp/peers/blackberry***
 
[FONT=Courier New]chown root:root /etc/ppp/peers/blackberry 

chmod 755  /etc/ppp/peers/blackberry /etc/ppp/peers/blackberry-connect [/FONT][B][FONT=Courier New]
[/FONT]
Step 8: Assign your user to the required groups (user krish in the example below)[/B]
 
[FONT=Courier New]sudo adduser krish dialout 
sudo adduser krish dip 
[/FONT]
**Note: you will need to logout and login for this to take effect.**
 [B]

Step 9: Create simple dialup script[/B]
 [FONT=Courier New]#!/bin/bash
pon blackberry & 
[/FONT]
Execute this script to connect via blackberry.
 [B]

Step 10: Disconnecting[/B]
 [FONT=Courier New]poff
[/FONT]

---

### Post by damory on 2009-11-26
Thank-you so much for this post!  I have spent hours trying to get to the bottom of why I could not get this to work and your instructions worked perfectly.  Am posting using my Bold now!! Thanks again.

---

### Post by robertmorodan on 2010-12-17
i get 

 sdptool search 00:1C:CC:5D:E0:35
Unknown service 00:1C:CC:5D:E0:35

why?

---

### Post by Randy Winchester on 2011-02-15
> **robertmorodan said:**
> i get 

 sdptool search 00:1C:CC:5D:E0:35
Unknown service 00:1C:CC:5D:E0:35

why?

The sdptool search command didn't work for me either.  Try sdptool browse.  00:1C:CC:5D:E0:35 is the address of your BlackBerry.

Try this:

$ sdptool browse 00:1C:CC:5D:E0:35

If you get 
"Failed to connect to SDP server on 00:1C:CC:5D:E0:35: Connection refused"

Check your BlackBerry Bluetooth set up device app and make sure you have a Bluetooth connection to your PC and try it again.

Cheers,
Randy

---

