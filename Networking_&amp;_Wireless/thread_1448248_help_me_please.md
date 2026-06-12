---
title: "help me please"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by setyo wirawan on 2010-04-06
how to connect modem a&at in ubuntu 9.10.. tx

---

### Post by rogerpittman on 2010-04-06
Are you using one of the USB dongles like the AT&T USB Mercury?

---

### Post by Iowan on 2010-04-06
> **setyo wirawan said:**
> how to connect modem a&at in ubuntu 9.10.. txDial-up, DSL, cable? (Guess I'm not familiar with a&at)

---

### Post by setyo wirawan on 2010-04-07
i use A&AT mobile device with usb.. can you tell how to configure in ubuntu 9.10

---

### Post by dineshs on 2010-04-07
pl post the output of```
lsusb
```
Also you can try configuring via network manager
right click on network manager icon then edit connections
click mobile broadband -add and proceed

---

### Post by thabelo on 2010-04-07
sudo apt-get install cutecom

Its like minicom but it has a graphical interface

Hope that helps

---

### Post by thabelo on 2010-04-07
I forgot to ask... what kind of modem are you using and Operating System are you using.

---

### Post by setyo wirawan on 2010-04-07
i using a&at modem sierra 855 compas,, and i using windows 7.. 
now,, i using vpn,. can you tell me how to configure it

---

### Post by metalf8801 on 2010-04-07
> **setyo wirawan said:**
> i using a&at modem sierra 855 compas,, and i using windows 7.. 
now,, i using vpn,. can you tell me how to configure it

Wait so your not using Ubuntu or a Ubuntu remix?

---

### Post by thabelo on 2010-04-08
I see the sierra 855 compas  USB dongle, is that it. And if it is it must have come with the Software and it should be found as a serial connection in your windows machine.

I am not very familiar with windows but I took a look at it and i think if you can go to 

control panel -> Administrative tools -> computer management -> ports com [expand]
you should see your dongle.

Get that working and open a hyper terminal and connect to the com port that your modem is connected on.

Get that working for now.... And we can take it from there...

---

### Post by setyo wirawan on 2010-04-10
oh,, sorry. i use ubuntu and windows 7 in 1 notebook..

---

### Post by alexfish on 2010-04-10
Hi setyo wirawan
 

  as requested by others we need some information, so can you respond to the questions asked then forum members may be able to help
 

 
[LIST=1]
[*]describe , how does the modem 	connect to the computer , I am presuming it is this one
 	[http://www.techradar.com/reviews/pc-mac/networking-and-wi-fi/modem-routers/sierra-wireless-compass-885-481261/review](http://www.techradar.com/reviews/pc-mac/networking-and-wi-fi/modem-routers/sierra-wireless-compass-885-481261/review)
[*]Did the modem self configure with 	windows 7, if not did it come with a disk to configure with windows 	7. sometimes it is necessary to configure the modem in XP or Vista 	then get the firmware upgraded , check with your service provider  	
[/LIST]
 

   For Ubuntu first boot up the computer, then hopefully the system will recognise the device
 

  open up the terminal and enter this command
 

 Code:
 

 tail -f /var/log/syslog
 

 **tail** is a command which outputs the last 10 lines of a file, with the -f option it continues to monitor the file and keeps outputing any further additions appended to the file in real time.
 

 Now connect the modem , are thee any changes in the terminal
 

 From a separate terminal
 

 Code:
 

 dmesg | grep -e "modem" -e "tty"  
 

 this  will just give you the lines including **modem**. You could also search for lines with tty or modem by
 

  also assuming it is a usb device  
 

 Code:
 

 lsusb
 

 this will show the id's of the device
 

  this information will tell us if the modem has configured with Ubuntu or requires further software to get it to work.
 

 Also note when using the lsusb command , when you connect the modem use the command  
 

 then if a file , cd or device shows up on the desktop just right click on the device and eject or safely remove the device, then type the lsusb command again, if the device id's change then Ubuntu has detected  the modem , check with the Network Manager, you may see make new connection, then follow the wizard ,
 

   Post all the results if possible
 

 thanks in advance
 

 alexfish

---

