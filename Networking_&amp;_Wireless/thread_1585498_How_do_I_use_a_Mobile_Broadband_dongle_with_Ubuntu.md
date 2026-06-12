---
title: "How do I use a Mobile Broadband dongle with Ubuntu?"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by CrownedInWood on 2010-09-30
Hello, all!
 
I'm an Ubuntu newbie, but I already love it as it saved my laptop. I live in the UK, and I bought a mobile broadband dongle from 3 network. Naturally it's only compatible with Windows and Mac OS. How do I get it to work with Ubuntu?
 
Please bear in mind that I am completely new to Ubuntu, so please make and instructions as basic as possible.
 
Thank you for your help!
 
~CrownedInWood

---

### Post by alexfish on 2010-09-30
Hi

welcome to the forum

there is a "how to" in "Tutorials & Tips" and , suggest read all of first post in detail , also explore the links
as a little knowledge about these devices helps

[How To : Mobile Broadband Connections [ Ubuntu  10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

if you have a problem getting connected, please post back here

regards

alexfish

ADDED there is a reference to 3 in post #30

---

### Post by emoguitarist06 on 2010-09-30
My experience with Ubuntu and Internet Sticks is just plug-n-play with no software download/installation needed

That was AT&T & Sprint in the USA

---

### Post by CrownedInWood on 2010-10-03
I thank you for the reply, but as to the link you sent me, I can't make head nor tail of it. It includes a section on "code," but I have no idea how or where to enter this code, or even if I need to.

I've been trying to use the "New Mobile Broadband Connection" Assistant, but though I've run it twice, and set up two connections-- and though I now have two such connections listed under the "Mobile Broadband Connections" section of my Networks Connection list-- it seems that neither of them has allowed me to actually connect to the internet. The only information missing in these two profiles, under "Advanced" are "Network" and "PIN." If I fill in these two information boxes correctly, will I be able to connect to the internet using the dongle?

---

### Post by CrownedInWood on 2010-10-03
Oh-- it should also be noted that when I first start the Network Connection Wizard (in "Network Connections" -> "Add"), where it says "Create a connection for this mobile broadband device" the pull-down box that follows is greyed out and cannot be pulled down. I'm not sure if that's relevant or not . . .

---

### Post by Megaptera on 2010-10-03
My 3 dongle in UK. Plug in, wait for symbol on desktop, click on wireless icon top right panel click new connection and follow GUI 4 or 5 stages and done in two minutes. Worked with Huwaei in 9.04, 9.10, 10.04 & 10.10.

---

### Post by alexfish on 2010-10-03
> **CrownedInWood said:**
> Oh-- it should also be noted that when I first start the Network Connection Wizard (in "Network Connections" -> "Add"), where it says "Create a connection for this mobile broadband device" the pull-down box that follows is greyed out and cannot be pulled down. I'm not sure if that's relevant or not . . .

Hi

if the Network Manager does not recognise the device , it is necessary to use ( in Linux terms is what we call) the terminal 
to retrieve data or send commands. this can be selected from the menus . click on Applications , Accessories ,select terminal
this will open up a terminal window

so lets find out if the device has been recognised in linux , open up the terminal 

Boot up the computer without the device , connect the device , wait for approx 30 seconds .

Note if any [COLOR=Blue]device[/COLOR] or [COLOR=Blue]file[/COLOR] etc appears on the desktop

enter these codes (highlighted in blue) in the terminal window ( can also use copy and paste )

code:

[COLOR=Blue]usb-devices[/COLOR]
try to determine which parts are relevant to the device, and post  only those parts

code:
[COLOR=Blue]
ls -al /dev/serial/by-id/*[/COLOR]

post the results of the outputs in the terminal ( this info will determine if the device has been detected ) or if further actions are required .

regards

alexfish

---

### Post by desnaike on 2010-10-03
Did you start all this by installing usb-modeswitch-data from package manager

---

### Post by CrownedInWood on 2010-10-03
@#6: I've tried that, and it claims to have set up a good connection, but when I boot up Firefox it tells me there's no connection. So I think that all I've done is establish a wireless network based on my computer, not one that connects my computer to the internet.

---

### Post by CrownedInWood on 2010-10-03
@#7: Usually when I plug in the device an icon appears on my desktop in fairly short order. This time it didn't, but when I go to "Places," it's listed there.

I opened the Terminal and inputted usb-devices, as you advised. It spat back a great deal of information; I assume each grouping of code has to do with a single device. According to the manufacturer info, this must be the correct one:

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  3 Spd=480 MxCh = 0
D= Ver=2.00 Cls=oo(>ifc) Sub=00 Prot=00 MxPS=64 #Cfgs = 1
P: Vendor=19d2 ProdID=0103 Rev=00.00
S: Manufacturer=ZTE,Incorporated
S: SerialNumber=P673A3H3GD010000
C: #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I= If#= 0 Alt= 0 #Eps= 2 Cls=08(stor.) Sub =06 Prot=50 Driver=ysb-storage

I tried entering the second bit of code you recommended, but got back the output "Is: command not found

---

### Post by CrownedInWood on 2010-10-03
@#8: Since I have no idea what you're talking about, I can safely say that I did not.

---

### Post by spiky001 on 2010-10-03
Hi did you say that you had set dongle up in network manager "create new mobile connection"?

---

### Post by alexfish on 2010-10-03
the "Is"  

is none capital "L"  = l

can you try again

code:
[COLOR=Blue]
ls -al /dev/serial/by-id/*[/COLOR]

can you have a look through the listing of usb-devices see if can find similar lines as below

T:  Bus=01 Lev=01 Prnt=01 Port=08 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0031 Rev=00.00 <<====Your device id's will be different
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE CDMA Technologies MSM
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

alexfish

---

### Post by Megaptera on 2010-10-04
> **Megaptera said:**
> My 3 dongle in UK. Plug in, wait for symbol on desktop, click on wireless icon top right panel click new connection and follow GUI 4 or 5 stages and done in two minutes. Worked with Huwaei in 9.04, 9.10, 10.04 & 10.10.

I'm not clear, have you tried this?

Thanks for clarifying.

---

### Post by CrownedInWood on 2010-10-04
@#12: Yes, I tried to set up a new connection using the network manager many times, but even after doing so, was not able to connect. The new connection never appeared as a valid option for my computer to connect to, even though I filled in all relevant fields-- correctly, to the best of my knowledge.

It asked for "number," so I entered the number of the SIM card, "username" which 3 network told me was once again the number of the SIM card, "password" which was sent to me by 3 network, "APN" which was 3network, and then "network" and "PIN" -- I don't know what either of these values should be, nor did 3 network when I asked. Even after going through the setup wizard they remained blank. According to 3 network they're not necessary, though of course I don't know . . .

---

### Post by CrownedInWood on 2010-10-04
@#13: I tried entering the code you supplied into the terminal exactly (by copy-paste). And then I tried taking out the spaces, and some of the other characters as well. I tried just about every permutation I could think of, but every time I got "no such file or id" or "invalid option."

---

### Post by CrownedInWood on 2010-10-04
@#14: If what you are referring to is the option of "setting up a new network connection" under "Network Connection Settings," then yes, I have gone through that process, multiple times, with no success.

---

### Post by alexfish on 2010-10-04
> **CrownedInWood said:**
> @#14: If what you are referring to is the option of "setting up a new network connection" under "Network Connection Settings," then yes, I have gone through that process, multiple times, with no success.

Hi

will post soon on what to do next/ looking up info

alexfish

---

### Post by alexfish on 2010-10-04
> **CrownedInWood said:**
> @#13: I tried entering the code you supplied into the terminal exactly (by copy-paste). And then I tried taking out the spaces, and some of the other characters as well. I tried just about every permutation I could think of, but every time I got "no such file or id" or "invalid option."

Hi

With the forgoing you will have to be patient as I may post further actions to do if this fails
but from what I am reading This device may be difficult to configure (I can only but try to help)



Your posted listings indicate exactly what can happen with this device(it is in a switched state 
but has failed to configure the ports)

I can only advise the following options at present

Edited ----------- (Wrong info ) Removed----------------


[COLOR=Blue]uninstall the usb_modeswitch 
[/COLOR]
boot up the computer without the device
connect the device , then if a device or file etc appears on the desktop leave it alone

from the terminal enter this code

Code:
[COLOR=Blue]lsusb
[/COLOR]

Code:
[COLOR=Blue]dmesg | grep -e "modem" -e "tty" [/COLOR]




see what happens and post the results

alexfish

---

### Post by CrownedInWood on 2010-10-07
@#19: Thanks much for your reply, and sorry for the delay in getting back to you-- I've been sick these last few days.
 
I followed the steps you outlined. When I put in the code lsusb when the device was in, among other outputs I also got the following:
 
Bus 001 Device 003: ID 19d2:0103 ONDA Communication S.p.A.
Bus 001 Device 001: ID 1d6b:002 Linux Foundation 2.0 root hub
 
When I took the device out, and then re-entered lsusb, the outputs were the same but there was no line listed at 19d2.
 
When I entered the dmesg code, I received the following output:
 
[    0.000000] console [tty0] enabled.
 
What should I do next?

---

### Post by alexfish on 2010-10-07
hi

can you try this

from the terminal

code:
[COLOR=Blue]sudo gedit /etc/udev/rules.d/zte_eject.rules
[/COLOR] 
add the following line

[COLOR=Blue]SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="0103", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"[/COLOR]

save and exit

reboot 

what does the "lsusb" command show

---

### Post by running_wild on 2010-10-07
I have a vodafone K3805-Z and after trying several ways to make it work i fond this script [sakis3g](http://www.sakis3g.org/"target=_blank) and voila it now works.

---

### Post by baxibax on 2010-10-08
I purchased a dongle on the 3 network yesterday and am having the same problems I need help I really dont know what I'm doing

---

### Post by halj32 on 2010-10-08
try installing usb-modeswitch + usb-modeswitch-data
then you should see the dongle in your network manager
then you just have to enter (if in UK)
go to edit connections, mobile broadband, new connection,
give your network a name ie; 3G
Number; *99#
APN: 3internet
done
enjoy

---

### Post by baxibax on 2010-10-08
I have been having all the same probs as crownedinwood.  The pull down box is also greyed out etc everything is the same.
 
Please please help in the most simpliest of instruction as im having trouble with the links already posted.
 
Can someone post a step by step guide as to how I can run my 3 dongle on the OS. Baring in mind that all of crownedinwood problems seem to be mirrored with me.

---

### Post by CrownedInWood on 2010-10-08
@22: Can you be more specific? You said you "found" the script and it worked . . . where did you find it and what did you do with it?

---

### Post by CrownedInWood on 2010-10-08
@24: How do you install usb-modeswitch data?  Please bear in mind that I cannot download software from the internet directly onto my laptop, as my laptop won't connect to the internet using the dongle.

---

### Post by CrownedInWood on 2010-10-08
@#19: I started my computer without the device. Then I plugged in the device. No information related to the device appeared on my desktop. Then I entered the two lines of code you suggested into the terminal, and got the following result:
 
[     0.000000] console [tty0] enabled
[     0.449894] tty tty30: hash matches
 
 
Anyway, I don't know if I uninstalled the usb_modeswitch or not . . . if I need to do this, would you tell me how?

---

### Post by CrownedInWood on 2010-10-08
@#21, alexfish:
 
THANK YOU SO MUCH!
 
I don't know why and I don't know how, but somehow whatever you advised me to do in posts #19 and #21 did the trick. When I followed your instructions, then rebooted my computer with the dongle in, I was connected to the internet! I'm able to load web pages and everything without any trouble, and once again my computer is running quickly and well.
 
Thank you so, so much for your patience and efforts on my behalf! I hope that your solution works for some of the other people who have happened upon this thread.

---

### Post by alexfish on 2010-10-08
Just pleased your connected

thanks

and thanks to all who input to Ubuntu

alexfish

---

### Post by running_wild on 2010-10-10
> **CrownedInWood said:**
> @22: Can you be more specific? You said you "found" the script and it worked . . . where did you find it and what did you do with it?

Sorry wrong link [http://www.sakis3g.org/#downloading](http://www.sakis3g.org/#downloading) try this.
And just run the script in the console ./sakis3g

I see that you solved your problem, this is no longer need.

---

