---
title: "Network manager problem"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by enl on 2010-01-22
Hi guys,I'm using ubuntu karmic and I'm not able to connect to the internet with my reliance netconnect data card using network manager. Other distros like fedora, opensuse n sabayon connected easily with nm. 
Ubuntu detects the data card flawlessly but just doesnt connect. This problem has been persistent even in previous ubuntu versions, n I used to use wvdial. But downloading wvdial on some other comp with every dependency is really cumbersome. I'd really appreciate any help to get nm working.

---

### Post by MoRoBoShi on 2010-01-22
It's a wireless card or a wired one?

post an lspci -n to identify which Network Card it is.

---

### Post by enl on 2010-01-22
Its a huawei wireless cdma card.. 
i'm onnline through another comp right now, will post the output of the command asap.

---

### Post by claracc on 2010-01-22
Try to install wicd. It is in the repositories, when you install it, automatically it is uninstalled network manager and network manager gnome, which have known bugs with some wifi cards un karmic koala.

I hope it can help

---

### Post by GeorgeVita on 2010-01-22
Hi **enl**, it would be better to manage it with network manager as this is the 'standard' for Ubuntu. Ubuntu 9.10 had a serious bug at initial kernel affecting a lot of mobile broadband devices, so try to update it using other internet connection (wifi or ethernet) if possible.

In any case, please provide more info about your modem and recent kernel:

- Boot without modem, **wait** for the system to load
- open a terminal window and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- attach modem, **wait** 30 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**
- from terminal: **uname -a**

Post all output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') till 'uname -a'. Also give us the model/manufacturer for your modem (look at the sticker label on it).

To get **wvdial** read: [http://ubuntuforums.org/showpost.php?p=8707586&postcount=17](http://ubuntuforums.org/showpost.php?p=8707586&postcount=17)

Regards,
George

---

### Post by pradeepthundiyil on 2010-02-11
hi,

I am dual booting ubuntu 9.1 with vista. I have the same prob too.. I am not able to connect to internet using Reliance NetConnect (Huawei EC325) USB modem. i tried all the ways.  This is the error message while giving wvdial command..


TDT777#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT777#
--> Waiting for carrier.
ATDT777#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT777#
--> Waiting for carrier.
ATDT777#
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT777#
--> Waiting for carrier.

Please help.....!

---

### Post by pradeepthundiyil on 2010-02-12
hi all,

To all those who have problem with net connection using mobile braodband.. (usb modem).. I also had problem with that.. Now I 'm posting this from Ubuntu. 

Step 1. Download Gnome-ppp
Step 2. Install in ubuntu
Step 3. Click settings.
Step 4. Click detect modem
step 5. give username and password..
Step 6 Click connect.

Good luck...!

---

