---
title: "HOWTO: Install/Connect to a HP  wireless printer"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by mpnordland on 2010-09-17
I, having encountered this problem, and also having solved it, decided to write a HOWTO to help others.[INDENT]1. install hplip-toolbox with:[/INDENT][INDENT][INDENT]```
sudo apt-get install hplip-gui
```[/INDENT]2.  launch that either from System>Preferences>HPLIP Toolbox or[INDENT]```
hplip-gui
```[/INDENT][INDENT]from the Terminal
[/INDENT]3. A window stating that there are no devices installed should appear,  
        click Setup Device. If it doesn't show up, then click Devices>Setup Device...

4. In the setup device window there are several options to choose from[INDENT]select the "Wireless/108.11" option
[/INDENT][INDENT]connect the printer by usb when prompted
[/INDENT][INDENT]your printer should be detected
select it and click next
choose your wireless network from the list of detected networks
enter the security information for your network (e.g. password, WEP key)

[/INDENT]5. Your printer will now be configured[INDENT]Once it is finished it will display the network settings of the printer, write down the printers ip address if you want to connect to it with other computers
[/INDENT][/INDENT]And Thats IT!

---

### Post by pjh421 on 2010-09-19
Thank you.  I will bookmark this page!

Paul

---

### Post by OooBuntuRox on 2010-09-20
[SIZE=2]Thanks for the post. I stumbled through several attempts today without success. 
[B]
From a Dell laptop 15n, Ubuntu 10.04-32 bit:[/B]
I installed HPLIP and went through the steps of the gui
was told to disconnect the usb cable
was told that my printer was connected
[B]
From the HP-c4795 wifi printer:[/B]
had the blue wifi confirmation light on the printer
All settings seemed good on the printer configuration test page (I think, but I am a Noob with wifi printers)

But after I click finish in the HPLIP GUI, the printer isn't displayed/ can't be found.

I can print if a usb cable is connected but can't print by wifi.

**Router:** I set up WPA, turned SSID broadcast on and all filters off after the first failed attempt.
[B]
Am I missing something?[/B]

I will try following your instructions again from scratch. And when I do, I will be sure to use a hardwire connection to install the packages. Maybe the HPLIP install I tried didn't go in right?
[/SIZE]   

 [SIZE=2]**QUESTION: **Should the device URL have USB in it after setup?   HP:/USB/Photosmart_C4700_Series?Serial=**************[/SIZE]


 [SIZE=2]Thanks, OooBuntuRox[/SIZE] :guitar:

[SIZE=3]**UPDATE: **Well, I tried step one and this is what I got for results:
[/SIZE][SIZE=3][B]:~$ sudo apt-get install hplip-toolbox
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hplip-toolbox
 :~$ 
[/B]
Doesn't seem to have done anything... Do I have to edit where it looks for the packages or something?

Thanks, OooBuntuRox[B] :guitar:


[/B][/SIZE]

---

### Post by mpnordland on 2010-09-30
sorry for taking too long, to respond, i just figured out that hplip-toolbox is a non-existant package the actual name is hplip-gui, sorry for the typo, I hope this helps. if not, say so and I'll try to help

---

### Post by OooBuntuRox on 2010-10-01
> **mpnordland said:**
> sorry for taking too long, to respond, i just figured out that hplip-toolbox is a non-existant package the actual name is hplip-gui, sorry for the typo, I hope this helps. if not, say so and I'll try to help

[SIZE=2]
Thanks. When I have more time, I'll give it another try. Perhaps when I upgrade to 10.10[/SIZE] :)

[SIZE=3]OooBuntuRox,[/SIZE] :guitar:

---

### Post by nesnahnhoj on 2012-11-22
after struggling for hours with hplip and various toolboxes telling me that they cannot connect me wirelesssly I gave up and went back to the Ubuntu system settings.
I finally chose to add a network printer having unplugged the usb connection to my photosmart. Hey presto it found my printer and connected me by wireless.
Scanning works too.
Don't mess about with HP tools. Let the Ubuntu system do it.

---

### Post by wildmanne39 on 2012-11-22
Old thread closed.

---

