---
title: "Wireless connectio help"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by noelc on 2010-10-09
Hi I purchased a netgear G5$ Wireless USB stick today. There is wirless network availble as I,m useing it to send this message (Lap top useing windows).

I tried many things but cant seem to wirelss connection on my linux desktop. The help pages arent much help either can some one point me in the right direction?

Thx

---

### Post by mvklingeren on 2010-10-09
Can you take a look 'ksystemlog', its in your KDE menu. Then open the 'Kernel' log (there's a 'kernel' button in the toolbar)

What do these last lines say, maybe you can copy paste it in a .txt file and post it to this forum from your desktop?

Also, if you open a shell with 'konsole' (also in your KDE menu) and then type:

ifconfig

can you copy paste / tell us what is shown there -> anything behind wlan0?
do you have a wlan0?

(ideally, pastebin a copy of your dmesg/kernel log)

---

### Post by noelc on 2010-10-09
Sorry Im not that educated with Linux and did not understand your post?

---

### Post by techdude3177 on 2010-10-09
Open up the command line and type in ifconfig and paste us the output please.
If you dont know how to open up the command line press Ctrl+Alt+T

---

### Post by noelc on 2010-10-09
Sorry Im not that educated with Linux and did not understand your post?

---

### Post by noelc on 2010-10-09
> **techdude3177 said:**
> Open up the command line and type in ifconfig and paste us the output please.
If you dont know how to open up the command line press Ctrl+Alt+T

Hi I ran ifconfig in a terminal and theres a lot of output. I cant copy and paste as I,m useing two different computers. Is the something in particular with the output I should post here or is all of it necessary?

---

### Post by techdude3177 on 2010-10-09
Alright on second thought. Run this command in the command line "iwconfig" and let us know if you have any interfaces with the following with "IEEE 802.11g"

---

### Post by noelc on 2010-10-09
Ok here is what is outot

lo no wireless extensions

etho no wireless extensions

wlan0 IEEE 802.11bg ESSID:off/any
Mode:Managed Acess Point: Not associated Tx-power=off
Retry long limit:7  RTS thr:off Fragment thr:off
Power management off

Thats it

---

### Post by techdude3177 on 2010-10-09
Try running "sudo iwlist wlan0 scan". This should tell you if there are any wireless network avaible.

I take it you have Network Manager running? 
Have you tired putting in your essid and password key into network manager manually?

---

### Post by noelc on 2010-10-09
> **techdude3177 said:**
> Try running "sudo iwlist wlan0 scan". This should tell you if there are any wireless network avaible.

I take it you have Network Manager running? 
Have you tired putting in your essid and password key into network manager manually?

OK type in script into teminal with the following output

interface does not support scanning

Also I dont think I,m running network manager nor am I amble to set it up manually

---

### Post by techdude3177 on 2010-10-09
Did you install the drivers for the device that you are currently using?

Also lets see this commands output: ps aux | grep -i Network
You should see NetworkManager as one of the outputs. Meaning your running networkmanager its that little icon up in the corner with the wifi symbol.

---

### Post by noelc on 2010-10-10
I think i need to load the Wireless USB driver? Not sure how to do that as its a windows based CD. I tried loading ndisgtk
 as I think this may help but I get a error message "ant find package.

Help

Thanks

---

### Post by techdude3177 on 2010-10-10
Here check out this [Tech Document]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), it should be more then enough to help you solve your issue. Post if you need anything else.

---

### Post by noelc on 2010-10-10
Thanks but I might call it quits. I know the device is not being recognised and suspect because the driver is not loaded.

Thanks away

---

