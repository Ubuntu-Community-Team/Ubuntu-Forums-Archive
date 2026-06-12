---
title: "Accessing Signal Strength (RSSI) Indication on USB760"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by not_a_phd on 2009-12-30
Does anyone know exactly how to access the signal strength indication from a Novatel USB760 3G modem? I have it up and running on my Karmic system, but live in a low signal strength area. I wish to make a baseline assessment of signal strength at various locations in the house, and need access to this.

I saw on another post, the use of the AT+CSQ key to do this. But, I don't know how to issue this modem command to the stick while it is running. Also, I don't know where the results would end up.

Help?

---

### Post by jimd562000_1 on 2009-12-30
KNetDockApp has a nice signal strength meter. Got it parked right down here on my bar - and a traffic graph in the icon. Have found it indispensible in monitoring my wireless system.

---

### Post by not_a_phd on 2009-12-30
Yes, but I don't think that app is set up to monitor signal strength on an external modem. (or is it?) Do you have experience using it with a USB wireless modem, or just a standard wi-fi dongle? 

At this point, I will try anything, but would like some assurance that it will work.

In another post, someone showed how they used the modem command AT+CSQ during initialization with gnome-ppp. However, I am not using gnome-ppp since the USB760 is recognized by the kernel, and is managed by the network manager applet. The gnome network manager also has a very nice signal strength scale, it just seems to be completely non-functional while I am connected with the modem.

Cheers.

---

### Post by jimd562000_1 on 2009-12-30
I have used it on a usb wireless modem and a pci wireless.

---

### Post by jimd562000_1 on 2009-12-30
It would be a simple matter of just installing it from add/remove, and try it on yours.

---

### Post by not_a_phd on 2009-12-30
Thanks. I will give it a go!

---

### Post by not_a_phd on 2009-12-30
OK. I got it. Unfortunately, for whatever reason, I am not seeing the Signal Level indication in the properties tab for the USB modem.

I do see this on the WiFi device. As you indicated, this is an extremely nice tool. Just wish it worked for my modem.

Wonder if there is a setting that would allow the modem to continuously telemeter the RSSI data to the kernel?

---

### Post by jimd562000_1 on 2009-12-31
the only other settings i found are knetdockapp --help-kde through terminal

---

### Post by GeorgeVita on 2010-01-01
Hi **not_a_phd**, just some ideas to try:

Most 3g modems have at least 2 ports to communicate, one is reserved for ppp connection (real modem) and the 2nd for other control as telemetry, SMS handling and data volume counting.

In my Huawei E169:
/dev/ttyUSB0 is used for connection (AT commands) and ppp data
/dev/ttyUSB1 cannot be used for AT commands (on fully updated Ubuntu 9.04)
/dev/ttyUSB2 accepts/responds to AT commands as **AT+CSQ**

I tried the following:
- connected as usual (9.04 network manager)
- from terminal: **screen /dev/ttyUSB2**
- typed **AT** and pressed <enter> key, the modem responded **OK**
- typed **AT+CSQ** <enter>, response=+CSQ: 14,99 OK
- as I tested only Ubuntu 9.04, I do not know if modem-manager (9.10) 'holds' other ports

My connection was active (this message and test done line).

Notes:
- I am not sure if AT+CSQ is the 'typical' signal strength for 3g data or only for the standard gsm signal.
- Closing 'screen' window still holds the /dev/ttyUSBx port and it needs to 'kill' the procedure (find it with: **ps -A | grep -i screen** and then kill it with: **kill 1234** where 1234 is the process#).
- reboot needed if the modem port 'stuck'.

>>> For your modem you must first find your 'communicable' ports.


Regards,
George

---

### Post by not_a_phd on 2010-01-02
I had finally stumbled onto the screen command for pushing the AT+CSQ command onto modem. Thank your George for you multiple port tutorial, as I had only been able to get signal strength data on the /dev/ttyUSB0 port while unconnected from the network.

Ultimately I had to return the modem because the signal strength outside my residence was at -96-dbm on the evdo channel, and I didn't feel like purchasing a 15db antenna to get my signal up to marginal.

The advice that I got on this forum was key for me to be able to make this assessment (and ultimately saved me $400US).

---

