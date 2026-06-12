---
title: "Internet stick problem"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by user_linux on 2012-05-07
I am trying to start internet on Ubuntu 10.4 from Wind's Huawei stick but when I click edit connection<mobile broadband<add but I don't see my mobile broadband highlighted. I checked terminal with lsusb and I see my USB stick there. What can I do to resolve this issue?
thx!

---

### Post by Ms. Daisy on 2012-05-08
You likely need the driver.  You can try this tutorial:

[http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/](http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/)

to see if a driver exists in the repositories that will work for it.

---

### Post by user_linux on 2012-05-08
i did it and i have all the drivers. any other ideas?
> **Ms. Daisy said:**
> You likely need the driver.  You can try this tutorial:

[http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/](http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/)

to see if a driver exists in the repositories that will work for it.

---

### Post by nothingspecial on 2012-05-08
*Thread moved to **Networking & Wireless**.*

---

### Post by burma1 on 2012-05-08
I had same problem I downloaded Sakis3g and set my network manager setting to wind mobile the is an explanation to this on line and then follow the instuctions and once you get a connection there is a drop down menu on the applet that appears you need to choose embed and it will work every time at least this was the easiest way that could find

---

### Post by user_linux on 2012-05-08
> **burma1 said:**
> I had same problem I downloaded Sakis3g and set my network manager setting to wind mobile the is an explanation to this on line and then follow the instuctions and once you get a connection there is a drop down menu on the applet that appears you need to choose embed and it will work every time at least this was the easiest way that could find
Ok, but i wasn't able to access the website its offline. However, I tried downloading rfkill but still i don't see my stick enabled. Any alternatives?

---

### Post by plant on 2012-05-09
With internet stick, you have installa wvdial.
and then edit the wvdial.config file.

You will have download wvdial.
If you have a lan connection, then you can use the
sudo apt-get install wvidal
or use synaptic to download wvdial

Then you have to edit the file: /etc/wvdial.conf
and add these: 

[Dialer username]
Phone = *99#
Username = <YOUR PHONE NUMBER>
Password = <LAST FOUR DIGITS OF THE ABOVE NUMBER>
New PPPD = yes
Modem = /dev/ttyUSB0
Baud = 115200
SetVolume = 0
[Modem 0 ]
Dial Command = ATDT
Init = ATZ
init2 = AT + CRM = 1
Flowcontrol = ( CRTSCTS )
Stupid Mod = 1
Inherits = Modem 0



after this take a terminal and type
sudo wvdial
or
sudo wvdial <user_name>

and wait sometime to connect.
keep the terminal open to browser the internet.

---

### Post by plant on 2012-05-09
It will be bit tricky to download wvdial and it dependencies from another computer.
It will be better to have a temporary lan connection to install wvidal.

---

### Post by user_linux on 2012-05-09
> **plant said:**
> It will be bit tricky to download wvdial and it dependencies from another computer.
It will be better to have a temporary lan connection to install wvidal.

isn't there any simpler way, i mean ubuntu is made to make people's life easier and this shouldn't be so hard.

---

