---
title: "HP G60-114EA Wireless does not work!"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by danielgroves on 2009-03-05
Hi,

I have an HP G60-114EA notebook, but Ubuntu 8.10 cannot detect my wireless card.  When I click the networking icon I only get wired as an option.  According to winodws I have the following wireless card:
Atheros AR5007 802.11b/g WiFi Adapter

Is thier a way to fix this? 

Thanks
Dan

---

### Post by locosmurf on 2009-05-04
Hello DanielGroves,

Have you tried seeing if your system recognizes the device? Running Gnome, go to System -> Administration -> System Testing

Go through the tests and see if your wireless card is detected. If so, try setting up the wireless drivers using System -> Administration -> Hardware Drivers

That's the user friendly way to do things. the CLI is faster, but some people are afraid of it ^_^

---

### Post by ebug on 2009-05-05
You dont have to ticker with ndiwrapper or madwifi. The driver is already built in intrepid and jaunty.

Mine worked by quick press of the wifi button (about 1 to 2 seconds). You should press the button while the color is still orange. Do it light and release a second quick. The button should stay orange when you release your finger. Then a second later it will turn to blue. Look at the wifi icon on the panel. There are two dots. The first dot (which I assume your wireless card) will turn green and then the second dot (I assume the wiless router connection) will light up to green. Then you got your connection. It may ask for the security code if there is one. 

Note: If you press the button and it turns blue while your finger is on the button, the connection will not bite. 

This instructions looks silly but this is how I activate hp wifi button without doing all those ndiswrapper, madwifi circus.

May problem is everytime I switch on my laptop, I have to do this quick press again. 

I missed the manual slide button of hp dv series. Don't have to do the above ritual.

Anybody knows how to make the hp wifi button automatically turn on to blue light and connect?

---

### Post by locosmurf on 2009-05-05
My WiFi and Touchpad buttons do not work at all on this laptop (running Jaunty). Also, my Wireless worked ootb. It's interesting that so many different problems with the wifi button is present with one model of laptop. Sometimes, it works flawlessly, others, you have to press it in a certian way, and still others do not work at all.

---

### Post by booshire on 2009-06-12
The issue I ran into when installing Jaunty was that the previous version, Ubuntu 8.04 or 10, did not have to ath9k drivers OOtB. I had compiled them in myself. I upgraded the system through aptitude and I could not get the wireless to work at all with the new kernel. Blacklisting, removing, recompiling... it went on all night. Finally I made a quick backup and did a fresh install with the default kernel and everything was fine. Maybe I should have blacklisted and disabled the driver BEFORE I did the upgrade.

---

