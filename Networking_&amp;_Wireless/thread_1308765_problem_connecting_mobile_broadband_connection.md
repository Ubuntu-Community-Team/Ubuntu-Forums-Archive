---
title: "problem connecting mobile broadband connection"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by awadhesh016 on 2009-10-31
hi, I am using compaq presario 1732 and use a huawei ec325 cdma modem to connect to internet. in jaunty it was working fine but in karmic its just not connecting.it detects the modem,it displays the error message half a second after I try to connect.

---

### Post by pdc on 2009-10-31
you are not alone;

you will find many threads in the last 1-2 days describing this;

what would make you re-install 9.04 ?

or crunchbang linux? or easy peasy ?

---

### Post by dj-toonz on 2009-10-31
or you could try my walkthough on how to get the heuwi modems working in Karmic

[How to get a Huawei HSDPA USB modem working in a new install of Karmic ]


Open up places, Computer & if you see a virtual CD ROM & HUAWEI SD Storage (for the microSD card if your modem Has one

right mouse click on the Virtual CD ROM (you don't need it as there the windows drivers) & select safety remove device)

then when the HUAWEI SD Storage device & the virtual CD ROM has Gone , close the computer browser box


open a terminal up

Applications , Accessory , Terminal

then copy & paste these following commands (there just to get your modem to be seen by network-manager)

sudo modprobe -r option

[enter your user password if asked for it] then can follow on with the rest without entering your user password

sudo modprobe -r usbserial

sudo modprobe usbserial vendor=0x12d1 product=0x1001

or

sudo modprobe usbserial vendor=0x12d1 product=0x1003 [If the first code doesn't work]


& don't forget to close the terminal box when finished with it


then when you goto Network-Manager & right mouse , click on edit connections, Mobile broadband, Add a connection , your modem will now be showing like it is in the screen shot

[[ UPDATE ]] Just been told, if it doesn't work the first time around, insert a MicroSD card in the modem before inserting into the machine ??? funny that,, but somebody said it worked for them that way, thought I would mention it, other wise I would be getting told off

And the screen shots to show the modem not working before I used the following commands & the modem working after.


P.S you have to do the following the first time you want to connect using the connection. After that you can disconnect & connect all you want, just make sure you don't reboot other wise you will have to repeat the above commands to get the connection working again

*** you don't need to re-enter network-manager & re-add the connection after making it the first time *** your connection you made stays in network-manager

"" If you do pull the modem out & plug it back in , just go back into places, Computer & safety remove the virtual CD & the connection will show back up in Network-Manager ""

now you can surf to your hearts content

sorry It's taken a bit to post back but just got in

Big shout out & credit goes to dmwelsch for letting me know about the MicroSD card tip & unpluging the modem & pluging it back in , that you have to either reboot the system to get the modem working or safety remove the virtual drive & HUAWEI SD Storage

---

### Post by lahirusena on 2009-11-07
im having some kind of problem with my usb huawei E220 broadband dongle,
i  only can connect via Ubuntu, if i first  connect via windows & restart without exiting from mobile partner & go to ubuntu
please help i need to direct connect without going to windows always

---

