---
title: "internet connection with broadband from the terminal"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by 10ghost on 2010-07-17
Hi All,
I am trying to connect to the internet from command line.
i issued the command nm-tool the output is
Device: ttyUSB0
Type:Mobile Broadband (GSM)
Driver:option1
state:disconnected
Default:no

capabilities:



I also issued the command sudo iwlist ttyUSB0 scan
it gives this as output
ttyUSB0 does not support scanning

I also issued the command
sudo iwconfig ttyUSB0 essid "MTN DEFAULT"
iT GIVES THE OUTPUT
Error for wireless request "Set ESSID" (8B1A)
SET failed on device ttyUSB): no such device



How can one find out the essid value of a broandband network?
How can i connect to the internet from command line for a broadband network?

---

### Post by alexfish on 2010-07-17
For GSM connections have a look here

   [How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

[example: 3G modem connected using only one terminal  command (pppd)]("http://ubuntuforums.org/showpost.php?p=7790046&postcount=54").

---

