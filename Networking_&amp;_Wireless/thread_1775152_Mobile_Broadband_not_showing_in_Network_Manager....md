---
title: "Mobile Broadband not showing in Network Manager...Help needed!!!"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by vikaskumargdra on 2011-06-04
Hi all!
I have u usb 3G stick and I configured a mobile broadband connection to connect to the internet.I filled all details and saved the connection.Now I clicked on the network manager icon in top right corner, but there was no connection with the name I just created.Again I checked in edit connections dialog box and found the connection there.Now how do I connect to this newly created connection while there is no option in network manager???
Please help'
Thanks in advance.

---

### Post by binkles on 2011-06-04
Same problem here but i'm running xubuntu 10.10.

---

### Post by svenskmand on 2011-06-04
I have the exact same problem with a Telia dongle. It worked flawless in 10.10, but not 11.04 :S

Help very much appreciated :D

---

### Post by vikaskumargdra on 2011-06-04
I have found the reason and a possible solution too.The reason behind is that Ubuntu is unable to recognize your modem and thats why it cant load it.You have noticed it when creating new mobile broadband connection that the option to select device is grayed out, thats cuz ubuntu havent drivers for your modem.Ok now the solution.The solution is for my usb stick which is Micromax mmx350g.Try it with yours:


I tried my best for not being a die-hard & ardent fan (which I am not certainly) of linux and found a layman's quick-fix solution for this. Sakis-3g is cute little tool that anyone can use on linux. Here are a few steps for installing Sakis-3g.

    Download Sakis-3g from Sakis-3g website directly (thanks to google for providing its kind helping hand).
    I extracted it to my home folder.
    Enter “$ sudo chmod +x sakis3g”
    Enter “$ sudo .//sakis3g helper balloons &”

Then I connected my Micromax usb modem to my laptop and waited patiently for a miracle to happen. Well nothing strange happened but this brought up a linux trademark holding usb removable disk on the upper panel of my desktop (which I wasnt very happy to see it untill i got really connected). Now sakis3g was working as it popped up message detecting my modem. On clicking the icon it brought up a menu driven tool. Hastily I clicked on “Connect with 3G”
Voila!!! And I did it. Pretty easy stuff.

Though I can get connected to internet with good speeds, but still I am too lazy to type that command (which is not always so user-friendly) each and every time I want to access www. I had to get a permanent fix on this problem. With some help from google, I managed figure out some driver fixes that could fix this issue permanently (i.e. Due to my little liking to linux/unix).
Well, I have worked out few easy steps to get connected to internet (its pretty hard to survive without it). 'Copy-paste' can make things (like shell commands) look bit less creepy.

    I made sure if I have got usb-modeswitch & wvdial packages installed on my system in the 'synaptic pakage manager' from System > Administration drop down menu in the menu bar.

    Still I checked if there was any latest update available for the above listed packages by typing below mentioned commands in my not-so-friendly gnome terminal.
    Enter “$ sudo apt-get install usb-modeswitch”
    Enter “$ sudo apt-get install wvdial”
    Enter “$ watch lsusb”
    And the output showed some crap that resembled something like this
    Bus 002 Device 006: ID 1c9e:f000
    After few seconds it showed
    Bus 002 Device 007: ID 1c9e:9605
    Where, 1c9e is the vendor id and f000 & 9605 are the product ids of the usb modem before and after switching. That is f000 is the default product id & 9605 is the target product id.
    After confirming the outputs, I made some tweaks in usb-modeswitch configuration files as below
    Enter “$ sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules”
    The file opened in gedit. There I had to enter some text below the line that said
    LABEL="modeswitch_rules_begin"
    It looks something like this :-
    LABEL="modeswitch_rules_begin"
    #Micromax MMX352G USB 3G MODEM
    ATTRS{idVendor}=="1c9e", ATTRS{idProduct}=="9605", RUN+="usb_modeswitch '%b/%k'"
    Had to save and then exit the editor.
    Then I copied the default configuration file to a new configuration file that would help our modem to switch and act like a true modem.
    Enter “$ sudo cp /etc/usb_modeswitch.d/1c9e\:9200 /etc/usb_modeswitch.d/1c9e\:9605”
    Editing one more usb_modeswitch configuration file brought me one step closer to the edge.

    Enter “$ sudo gedit /etc/usb_modeswitch.d/1c9e\:9605”
    Here's the ouput of the file.





    ########################################################
    # Micromax MMX 352G USB 3G Modem
    DefaultVendor= 0x1c9e
    DefaultProduct=0x9605
    TargetVendor= 0x1c9e
    TargetProduct= 0x9605
    CheckSuccess=20
    MessageContent="55534243123456780000000000000606f50402527000000000000000000000"

    Now finally we have to work out with usbserial module (that is what drivers are referred to in UNIX)

    Enter “$ sudo gedit /etc/modules”
    Add the below mentioned line at the end of the file.
    #MICROMAX 352G 3G USB MODEM
    usbserial vendor=0x1c9e product=0x9605
    Rebooted the machine curiously.


That is all. Configuration of devices was complete.

Now, after the machine rebooted, I plugged in the usb modem and waited for around half a minute.

    Back to GUI by clicking on the Network Manager Applet on the top panel, a list of available connections came through a drop down menu.
    Among these I clicked on New Mobile Broadband (GSM) Connection.
    The New Broadband Connection Wizard popped up. Clicked on the “Forward” button.
    I had to select India (Wonderful place where I live). Clicked on “Forward” (Pretty easy).
    Selected “BSNL/Cellone” from the list of service providers. Again a click happened.
    Selected “BSNL/CellOne Old East Zone Prepaid (Jharkhand, Bihar, Kolkata, West Bengal, Orissa, Assam, North East, Adman Nicobar)” from the list of plans that were available and clicked on “Forward” & then “Apply”.
    Connection Configuration window will appear where I selected “Connect Automatically” under Connection Name. Entered “*99#” in front of number and entered “bsnlnet” in front of APN. Finally “Save”.


Finally, done with all clicking which quite effortless. Nothing seemed to appear for some time, but then automatically the Network Manager Applet selected my configured connection. That is all I had to do. Time to have the sweet fruit of my tireless effort.

See if this helps!
Have a nice day

---

### Post by AcerLaura on 2011-06-04
I was quite happy with Ubuntu 10 & being a trusting soul I 'upgraded' to 11.04 (after all Ubuntu is now promoted as being so much more user friendly).
Result? B'all - No internet! My 3G dongle is no longer recognised.
So back to Win7. I've had enough!
Ubuntu? It's still for geeks & looks like it always will be.
What a shame.

(I note many of the 'experts' that tell you the easy bit 'how to set up a network connection' have just changed their titles from Ubuntu 10 to 11 assuming that plugging in a modem to a usb port will work as before)

---

### Post by svenskmand on 2011-06-05
Ok I got it to work I followed [this bug-report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/usb-modeswitch-data/+bug/776959").

You just have to plug in the dongle, then run this command
```

sudo modprobe usbserial vendor=0x12d1 product=0x1506

```
then wait about 5-10 seconds until the mobile broadband profile show up in the network connections manager in the top right corner. I can now select it and use the 3G internet :)

Only downside is that you have to do this every time you plug in the dongle. Hopefully the ubuntu team will fix this soon, so this is not necessary anymore :D

My dongle is a Huawei E367.

---

### Post by vikaskumargdra on 2011-06-05
> **AcerLaura said:**
> I was quite happy with Ubuntu 10 & being a trusting soul I 'upgraded' to 11.04 (after all Ubuntu is now promoted as being so much more user friendly).
Result? B'all - No internet! My 3G dongle is no longer recognised.
So back to Win7. I've had enough!
Ubuntu? It's still for geeks & looks like it always will be.
What a shame.

(I note many of the 'experts' that tell you the easy bit 'how to set up a network connection' have just changed their titles from Ubuntu 10 to 11 assuming that plugging in a modem to a usb port will work as before)

yeas Ubuntu 10.10 was better than the new one.So I am thinking of downgrading....lol
This is really a bad thing for ubuntu that the previous version id better than the current one.11.04 also have some booting problems and driver related isssues.Hope all this fixes in Ubuntu 11.10
Ubuntu team pls do something about this.

---

### Post by gaigoleb2 on 2011-06-17
just follow the below mentioned link

[http://hashprompt.blogspot.com](http://hashprompt.blogspot.com)

---

### Post by Matbro on 2011-06-28
Hi 

Had the same problem on my laptop with 11.04 and E367 Huawei modem

I solved it this way:

Wrote a simple script called "huawei":

[I]#!/bin/sh 

# Script to enable Huawei E367 HDSPA modem i Ubuntu Natty 11.04 
# modem detected as Vendor = 1201 Product = 1506 running DMESG after boot. 

modprobe -r usb_storage 
modprobe -r usbserial 
wait 5 
modprobe usbserial vendor=0x12d1 product=0x1506 [/I]

To install your own script, copy it to /etc/init.d, and make it executable.

[I]sudo cp huawei /etc/init.d
sudo chmod +x /etc/init.d/huawei[/I]

To make the script run with the*start*argument at the end of the start sequence, and run with the*stop*argument at the beginning of the shutdown sequence:

*sudo update-rc.d huawei defaults 98 02*

98 and 02 are the start and stop sequence numbers respectively. Both are numbers between 00 and 99 and specify how early or late a service is started or killed. If a service is started late, it should be killed early and vice-versa. A good rule of thumb is to make the stop sequence number equal to 100 minus the start sequence number.

Cold boot, plug the modem after boot will work  :)
reboot with the modem inserted will work !      :)

/Mats

---

### Post by RoSy1978 on 2011-06-30
Hi Mats,
I have same problem, you know I am also newbie in Ubuntu ;). I tried to solve it as you did,wrote this script, loaded in terminal and received following message.

dar@ubuntu:~$ sudo cp /home/dar/Dokumenty/huawei /etc/init.d
dar@ubuntu:~$ sudo chmod +x /etc/init.d/huawei
dar@ubuntu:~$ sudo update-rc.d huawei defaults 98 02
update-rc.d: warning: /etc/init.d/huawei missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/huawei ...
   /etc/rc0.d/K02huawei -> ../init.d/huawei
   /etc/rc1.d/K02huawei -> ../init.d/huawei
   /etc/rc6.d/K02huawei -> ../init.d/huawei
   /etc/rc2.d/S98huawei -> ../init.d/huawei
   /etc/rc3.d/S98huawei -> ../init.d/huawei
   /etc/rc4.d/S98huawei -> ../init.d/huawei
   /etc/rc5.d/S98huawei -> ../init.d/huawei

Any ideas what to do please?
i would appreciate any help. Thank you

---

### Post by RoSy1978 on 2011-06-30
yes, it works. great.
thank you Mats

---

### Post by wdschei on 2011-07-17
@[Matbro]("http://ubuntuforums.org/member.php?u=1283333") Thanks man. I have not done Nix scripting in a while. This worked like a charm.

Now my daughter won't have to use a terminal window. You would have thought it was going to kill her when I showed her what needed to be done after she reconnected the modem.

---

### Post by JuanWPL on 2011-07-23
I have a satellite internet provider,, Hughes,, and I can't make it work with ubuntu why?

---

### Post by Anssi-J on 2011-08-15
Oh man, thank you Matbro, you're a genius.

I had wrestled with my Huawei Mobile stick
some time to get it work, but with no luck, 
until I found your advice: that little huawei 
script of yours worked immediately!

Alltså stort tack,
mvh Anssi
Åbo
Finland

---

### Post by anttud on 2011-10-31
I have tried everything what I have found from forum and google. Not sure if i'm doing something wrong but nothing works for me. I'm running on ubuntu 10.04. 
I think the problem is that ubuntu regonizes modem as CD and I just can't get it fixed. I can't find it from network manager, though the blue light is blinking. 
```
root@john-laptop:~$ lsusb
Bus 002 Device 004: ID 12d1:14ac Huawei Technologies Co., Ltd. 

```
have also tried
```
sudo modprobe usbserial vendor=0x12d1 product=0x1506
```
and
```
sudo modprobe usbserial vendor=0x12d1 product=0x14ac
```
I can't install Oneirics modeswitch.
Error: Dependency is not satisfiable: libpipeline1 (>= 1.0.0)
This is what i get.
And i have no idea what to try next?

---

### Post by rajpuv on 2012-09-22
> **vikaskumargdra said:**
> I have found the reason and a possible solution too.The reason behind is that Ubuntu is unable to recognize your modem and thats why it cant load it.You have noticed it when creating new mobile broadband connection that the option to select device is grayed out, thats cuz ubuntu havent drivers for your modem.Ok now the solution.The solution is for my usb stick which is Micromax mmx350g.Try it with yours:


I tried my best for not being a die-hard & ardent fan (which I am not certainly) of linux and found a layman's quick-fix solution for this. Sakis-3g is cute little tool that anyone can use on linux. Here are a few steps for installing Sakis-3g.

    Download Sakis-3g from Sakis-3g website directly (thanks to google for providing its kind helping hand).
    I extracted it to my home folder.
    Enter “$ sudo chmod +x sakis3g”
    Enter “$ sudo .//sakis3g helper balloons &”

Then I connected my Micromax usb modem to my laptop and waited patiently for a miracle to happen. Well nothing strange happened but this brought up a linux trademark holding usb removable disk on the upper panel of my desktop (which I wasnt very happy to see it untill i got really connected). Now sakis3g was working as it popped up message detecting my modem. On clicking the icon it brought up a menu driven tool. Hastily I clicked on “Connect with 3G”
Voila!!! And I did it. Pretty easy stuff.

Though I can get connected to internet with good speeds, but still I am too lazy to type that command (which is not always so user-friendly) each and every time I want to access www. I had to get a permanent fix on this problem. With some help from google, I managed figure out some driver fixes that could fix this issue permanently (i.e. Due to my little liking to linux/unix).
Well, I have worked out few easy steps to get connected to internet (its pretty hard to survive without it). 'Copy-paste' can make things (like shell commands) look bit less creepy.

    I made sure if I have got usb-modeswitch & wvdial packages installed on my system in the 'synaptic pakage manager' from System > Administration drop down menu in the menu bar.

    Still I checked if there was any latest update available for the above listed packages by typing below mentioned commands in my not-so-friendly gnome terminal.
    Enter “$ sudo apt-get install usb-modeswitch”
    Enter “$ sudo apt-get install wvdial”
    Enter “$ watch lsusb”
    And the output showed some crap that resembled something like this
    Bus 002 Device 006: ID 1c9e:f000
    After few seconds it showed
    Bus 002 Device 007: ID 1c9e:9605
    Where, 1c9e is the vendor id and f000 & 9605 are the product ids of the usb modem before and after switching. That is f000 is the default product id & 9605 is the target product id.
    After confirming the outputs, I made some tweaks in usb-modeswitch configuration files as below
    Enter “$ sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules”
    The file opened in gedit. There I had to enter some text below the line that said
    LABEL="modeswitch_rules_begin"
    It looks something like this :-
    LABEL="modeswitch_rules_begin"
    #Micromax MMX352G USB 3G MODEM
    ATTRS{idVendor}=="1c9e", ATTRS{idProduct}=="9605", RUN+="usb_modeswitch '%b/%k'"
    Had to save and then exit the editor.
    Then I copied the default configuration file to a new configuration file that would help our modem to switch and act like a true modem.
    Enter “$ sudo cp /etc/usb_modeswitch.d/1c9e\:9200 /etc/usb_modeswitch.d/1c9e\:9605”
    Editing one more usb_modeswitch configuration file brought me one step closer to the edge.

    Enter “$ sudo gedit /etc/usb_modeswitch.d/1c9e\:9605”
    Here's the ouput of the file.





    ########################################################
    # Micromax MMX 352G USB 3G Modem
    DefaultVendor= 0x1c9e
    DefaultProduct=0x9605
    TargetVendor= 0x1c9e
    TargetProduct= 0x9605
    CheckSuccess=20
    MessageContent="55534243123456780000000000000606f50402527000000000000000000000"

    Now finally we have to work out with usbserial module (that is what drivers are referred to in UNIX)

    Enter “$ sudo gedit /etc/modules”
    Add the below mentioned line at the end of the file.
    #MICROMAX 352G 3G USB MODEM
    usbserial vendor=0x1c9e product=0x9605
    Rebooted the machine curiously.


That is all. Configuration of devices was complete.

Now, after the machine rebooted, I plugged in the usb modem and waited for around half a minute.

    Back to GUI by clicking on the Network Manager Applet on the top panel, a list of available connections came through a drop down menu.
    Among these I clicked on New Mobile Broadband (GSM) Connection.
    The New Broadband Connection Wizard popped up. Clicked on the “Forward” button.
    I had to select India (Wonderful place where I live). Clicked on “Forward” (Pretty easy).
    Selected “BSNL/Cellone” from the list of service providers. Again a click happened.
    Selected “BSNL/CellOne Old East Zone Prepaid (Jharkhand, Bihar, Kolkata, West Bengal, Orissa, Assam, North East, Adman Nicobar)” from the list of plans that were available and clicked on “Forward” & then “Apply”.
    Connection Configuration window will appear where I selected “Connect Automatically” under Connection Name. Entered “*99#” in front of number and entered “bsnlnet” in front of APN. Finally “Save”.


Finally, done with all clicking which quite effortless. Nothing seemed to appear for some time, but then automatically the Network Manager Applet selected my configured connection. That is all I had to do. Time to have the sweet fruit of my tireless effort.

See if this helps!
Have a nice day

Thanks it worked for me after following the steps that you have put. The only catch for TATA DOCOMO 3G dongle is that after restart you have to edit the connections to change the APN to "tatadocomo3g".

---

### Post by RoosterHam on 2013-03-21
I have a slightly related problem. I have a Huawei E367 HSPA+ usb modem. I have used it on Fedora, Ubuntu and Lubuntu, all of which automatically detected it, and allowed me to connect immediately after plugging it in ( after initial account/connection configuration ). 

I installed the KDE desktop on the Lubuntu laptop that this had been working. Since then, when logged into a KDE session, plugging the usb modem in does not add an interface to the modem manager. The connection comes up in "Wireless Broadband" tab of "manage connections," as do all the wlan and particular ethernet profiles I have set on when it was a standard Lubuntu system. But editing my wwan connection pops up a message saying "No agents were available for this request".

lsmod, lsusb, and tail -f /var/log/syslog all tell me that everything is detected and configured exactly the same as always (by which I mean lsusb has always seen an E398 but the E367 still worked that way), the way that works from LXDE. Is this a problem with the KDE ModemManager?

---

### Post by lisati on 2013-03-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Thread closed.

---

