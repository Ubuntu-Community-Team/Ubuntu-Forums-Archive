---
title: "Intel 4965 wireless stopped working?!"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by unclben on 2009-08-28
I have a ThinkPad X61s with a built-in Intel 4965 wireless chip. I have been using it for months, with both Intrepid and Jaunty. I just spent a week in a hotel where I used wired ethernet only. Now I'm back home and wireless won't work! Wired still works fine. I have tried reboots. I have tried restarting networking via init.d. I have tried "ifconfig wlan0 down" followed by an "up" command. No errors pop up, but I still can't get wireless.

If I left-click on the nm-applet, it says "wireless is disabled" under the "Wireless Networks" heading. If I right-click the applet, the "Enable Wireless" checkbox is grayed out, regardless of whether or not the "Enable Networking" box is checked.

I ran lsmod and and looked for wireless stuff. I found the following entries that seemed relevant:
iwlagn 100228 0
iwlcore 93184 1 iwlagn

I tried doing "iwlist scan" and wlan0 reported "No scan results".

I have to stay I am stumped and frustrated. Can anybody here provide any insights, solutions, or additional troubleshooting to perform?

TIA

-Ben

---

### Post by Metaljaz on 2009-08-28
Under System>Administration>Hardware Drivers is there a proprietary driver that should be used that is not enabled?
Also check to make sure that you wireless is turn on on your laptop. I have a different laptop but i can turn
my wireless off and on with the keyboard command F2. Make sure its not turned off.

---

### Post by SweetieDarling on 2009-08-29
Confirmed - Jaunty has been running fine with my 4965AGN until I caught up on a backlog of updates today, and I haven't had wireless since. 

#dmesg | grep iwl
[   11.709031] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   11.709035] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   11.709414] iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.709498] iwlagn 0000:0c:00.0: setting latency timer to 64
[   11.709704] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   11.712935] iwlagn: EEPROM not found, EEPROM_GP=0x90000000
[   11.712938] iwlagn: EEPROM not found, EEPROM_GP=0x90000000
[   11.712940] iwlagn: Unable to init EEPROM
[   11.712964] iwlagn 0000:0c:00.0: PCI INT A disabled
[   11.714230] iwlagn: probe of 0000:0c:00.0 failed with error -2

Any suggestions?

---

### Post by unclben on 2009-08-29
> **Metaljaz said:**
> Under System>Administration>Hardware Drivers is there a proprietary driver that should be used that is not enabled?
Also check to make sure that you wireless is turn on on your laptop. I have a different laptop but i can turn
my wireless off and on with the keyboard command F2. Make sure its not turned off.No proprietary drivers, but wow am I an idiot. Your second suggestion was almost correct. My ThinkPad has a hardware toggle switch on the front of the casing. I never use it, so I always forget that it exists; your comment jogged my memory. It must have gotten bumped while I was traveling, because it was in the 'wireless off' position. Problem solved! Thanks, Metaljaz!

---

### Post by SweetieDarling on 2009-08-29
I have Fn+F2 to enable/disable wifi and bluetooth (no hardware switch), bluetooth is working fine so I know the radio is on.  Anyone know how to solve the "EEPROM not found" error?  Google has nothing...

---

### Post by Metaljaz on 2009-08-29
What did you do different to your system that caused it to stop working? (Upgrade, updates) 
Please post your version of Ubuntu and type the below command in the terminal window:

lspci

then look under network controller and post the results here. Should look something like this:

0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

---

