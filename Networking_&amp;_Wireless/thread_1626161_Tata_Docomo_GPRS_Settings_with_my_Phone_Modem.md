---
title: "Tata Docomo GPRS Settings with my Phone Modem?"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by khushalb on 2010-11-19
Guys I need to setup my Sony Ericson C510 phone modem in Ubuntu linux the latest one that I have installed. When I connect my Phone using USB connection it doesnt show me the Dialog box where it says create new "Mobile Broadband Connection".
I am not sure how can I configure my Tata Docomo GPRS Connection to use it with Ubuntu.
 
Here's one blog i came across which says:-
 
It’s wonderful to see people browsing in their mobile phones at work places and while they travel. Many Telecom companies provide cheap GPRS / EDGE based internet connectivity which can also be connected to a computer. Here, I will explain how to connect TATA Docomo Internet service in your Ubuntu machine.
 
**Step 1 : **Connect your phone and create a new ‘Mobile Broadband’ connection from the appeared wizard. You can Select ‘Airtel’ in ‘Service Provider’ which we will change to suit Docomo Internet.
 
**Step 2** : Change the ‘Name’ in ‘Summary’ page to “Docomo Internet”
 
**Step 3** : Go to System –> Preferences –> Network Connections, Under the “Mobile Broadband” tab, select “Docomo Internet” and click on “Edit”.
 
**Step 4** : Change APN to ‘ TATA.DOCOMO.INTERNET ‘ without quotes. Also, Under “IPv4&#8243; tab, select “Method” as “Automatic (PPP) addresses only”. We will give Open DNS as DNS servers, ie, in the “DNS Servers” box, give ’208.67.222.222, 208.67.220.220&#8242; wihout quotes.
 
Done! Now click on the antenna icon in system tray, select “Docomo Internet” from the list – You are connected! Best of Luck
 
But when I connect to the internet with my SE C510 phone I dont get that option create a new ‘Mobile Broadband’ connection like it says in that article above. Anyone can help me out please?

---

### Post by Jahid65 on 2010-11-20
Which version are you using? 10.04(lucid) or 10.10(maverick ? you may need to install usb-modswitch-data & usb-modswitch first. [http://packages.ubuntu.com/lucid/usb-modeswitch](http://packages.ubuntu.com/lucid/usb-modeswitch) After installing those reboot your pc & plug-in your phone & do the rest.

---

### Post by khushalb on 2010-11-22
I am using 10.04 lucid and thanks man for the reply i will try and install the package you recommended and see if it works.

---

### Post by pdc on 2010-11-22
Josh; who oversees usb_modeswitch would recommend you install the latest version 1.1.4 from the debian repositories

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

you need the programme and its data package;

I think ..... that by installing the programme first, it brings in the data package as a dependency for you (ie is done automatically ..)

you need to choose the version of usb_modeswitch that matches your processor ie i386 or 64bit or whatever ..........

---

