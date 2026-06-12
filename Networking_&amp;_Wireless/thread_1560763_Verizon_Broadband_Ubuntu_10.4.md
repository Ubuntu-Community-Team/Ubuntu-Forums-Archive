---
title: "Verizon Broadband Ubuntu 10.4"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by cliffwatts on 2010-08-25
I'm confused about connecting to the internet using verizon mobile broadband. When I click on the network icon in 10.4 and choose mobile broadband and and add the verizon option and insert my usb 760 modem nothing happens. How do I get this to work?

---

### Post by alexfish on 2010-08-25
hi

from the terminal try this command to see which ports are been used by the device

Code:

dmesg | grep -e "modem" -e "tty"

If nothing shows post the details of 

CODE:

lsusb

then try wvdial or gnomeppp 

to set up wvdial

code:

wvdialconf

then read the location of the conf file usally /etc/wvdial.conf

to edit the file 

CODE:

sudo gedit /etc/wvdial.conf

FOR INFO>>>>>>>>>>

CDMA:
To connect via 1xRTT and use your provider as an ISP, use the following values:
Number #777
Username <number>@<provider>
Password <pwd>

In all cases, replace <number> with your raw phone number: (555) 123-1234 would be '5551231234'

<provider> and <pwd> vary based on your provider.
Provider <provider> <pwd>
Verizon vzw3g.com vzw
Alltel alltel.com allltel

If you are using Sprint, Username is your Vision login and Password is your Vision password. The number to dial remains #777.
Why to avoid 1xRTT


EV-DO

EV-DO is the current choice of CDMA providers for data services, and offers significant speed boosts over 1xRTT.
Details

To connect via EV-DO and use your provider as an ISP, use the following values:
Number #777
Username <number>@<provider>
Password <pwd>

In all cases, replace <number> with your raw phone number: (555) 123-1234 would be '5551231234'

<provider> and <pwd> vary based on your provider.
Provider <provider> <pwd>
Verizon vzw3g.com vzw
Alltel alltel.com allltel

regards

alexfish

---

### Post by cliffwatts on 2010-08-26
Thanks 

I an now trying to figure out how to install wvdial or gnome-ppp from my repositories that are on dvd's.  Soon as I get this done I will let you know if I was successful.

---

