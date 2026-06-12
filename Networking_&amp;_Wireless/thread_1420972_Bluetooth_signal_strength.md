---
title: "Bluetooth signal strength"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by mark bower on 2010-03-03
For wifi we have NetWork Mgr, Wavemon, iwconfig etc to continuously observe signal strength.  What software or command line code shows bluetooth strength?  I have connection between the dongle and BT200 on the HP printer.  I want to look at signal strength between the devices in order to move the dongle on extension to a stronger signal strength location.

I have tried two methods without success - 1st ends wtih msg "not connected", 2nd says "host is down".

_1st Method_
rfcomm connect 0 BDaddr = no rtn msg             [note;  BDaddr is address of BT200]
hcitool rssi BDaddr = "not connected"

_2nd Method_
hciconfig= "UP Running PSCAN"
hcitool scan = get BDaddr and name
sdptool records BDaddr = "failed to connect, host is down"
sdptool search SP = provides info on the BT200
sudo rfcomm bind /dev/rfcomm0= binds the dongle to rfcomm0, no rtn msg
sudo cat /dev/rfcomm0 = "host is down"

However, ls /dev/rfcomm0 indicates in colored /dev/rfcomm0 test that the connection is bound.  Suggestions?

---

### Post by mark bower on 2010-03-03
bump #1

---

### Post by mark bower on 2010-03-03
o.k. Solution is at hand.  I needed modified syntax which uses channel "1".  In fact, "spdtool search SP" shows the BT200 to be on channel 1.  The correct code lines are,  

sudo rfcomm connect 1 HDaddr    [note: where my Hdaddr = 00:08:f4:223:28:71]
hcitool rssi HDaddr 1

The output for the latter command line is:  "RSSI return value: -17'.  This represents a weak signal, bluetooth thru 2 walls, one with metal mesh for shower tile.  When I run the files at on the computer that is 4' from the BT200, the readings go to "0" or "-1".  This is expected since the dongle is very close to the BT200.

Doesn't look like there is a lot of interest in knowing BTooth strength, but in following post I will present what works and I can duplicate.

mark

---

### Post by mark bower on 2010-03-04
To see Bluetooth signal strength do the following:

Open a terminal
Enter "hcitool scan"    [see BDaddr and channel for remote BT device]
Enter "sudo rfcomm connect 1 BDaddr   [where device operates on ch 1]
[note:  use the up arrow to repeat cmd above until connection is made, sometimes as many as 5 times in my case.  should get msg "connected /dev/rfcomm1 to BDaddr on channel 1", and line "Press Ctrl-C to hangup"]
Open a new terminal
Enter "hcitool rssi BDaddr" 
[note:  should get line "RSSI return value: -19", where -19 is signal strength]

To see the output 20 times without reentered in second terminal, make a script file from the code lines below and place on desktop.  I named mine "BTsignal".sh.  Then after connection is made in the 1st terminal, click on the desktop file.  After each completion, you can click on file again.  The file is kludggy, and should be made to run continuously with a key press to exit.  I haven't script programmed, so do not know how to do it at this time.

#!/bin/bash
#file:  BTsignal.sh
clear
for i in `seq 1 20`;
do
   hcitool rssi 00:08:f4:23:28:71 1
   sleep 2  
   clear    
done    

I did discover that my normal BT function(set-up via system>bluetooth preferences) was disturned, and I could not print to the HP printer.  I just shutdown and rebooted and normal operation was restored.

Bottom line, I can now work on improving the BT signal strength by playing with aerials, reflectors, location etc - and not working blindly.

mark

---

