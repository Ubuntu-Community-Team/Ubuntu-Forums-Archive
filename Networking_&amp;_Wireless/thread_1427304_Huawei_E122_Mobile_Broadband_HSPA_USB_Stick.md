---
title: "Huawei E122 Mobile Broadband HSPA USB Stick"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by jd87 on 2010-03-11
Ubuntu version = 9.10 (netbook remix)
Kernel = 2.6.31-19-generic i686
Hardware = Asus EEE PC 701sd

I'm trying to use a Huawei E122 USB stick to connect to the internet on UK mobile network "3". I've tried all kinds of ways to get it to work but with no joy. 

Starting off in network manager adding a new Mobile Broadband connection, the device is automatically recognised as "HUA WEI Huawei Mobile". I then choose the right country and network and this sets the APN as "3internet", the number to dial as *99# and the username and password blank. I then try to connect. Nothing happens for a few seconds, then I just get a network manager message saying "GSM Network - Disconnected - You are now offline". I've tried changing the dial number to *99***1# which is the number used in Windows, and I've tried entering various things for username/password but nothing makes a difference.

The next thing I tried was connecting using wvdial in the terminal. I ran "sudo apt-get install wvdial". Then I ran wvdialconf, which generates the following /etc/wvdial.conf file:

> [Dialer Defaults]
Init2 = AT0Q V1 E1 S0=0 &C1 &D2
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Username = <Your login name>
Init1 = ATZ
; Password <Your Password>
Modem = /dev/ttyUSB0
Baud = 9600

I edited wvdial.conf to look like this:

> [Dialer Defaults]
Init2 = AT0Q V1 E1 S0=0 &C1 &D2
Modem Type = Analog Modem
Phone = *99#
ISDN = 0
Username = three
Init1 = ATZ
Password = three
Modem = /dev/ttyUSB0
Baud = 9600

Next I ran sudo wvdial. This was the output:

> --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Modem Initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 7200000
--> Carrier detected. Waiting for prompt.
--> Don't know what to do! Starting pppd and hoping for the best.
--> Starting pppd at Thu Mar 11 16:15:41 2010
--> Pid of pppd: 2570


This goes on with a few lines of pppd: p[08]9 ? and includes "Authentication (CHAP) successful" but then I get this:

> --> Disconnecting at Thu Mar 11 16:15:42 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

It then Auto Reconnects over and over.

I have tried adding the line "Init3 = AT+CGDCONT=1,"IP","3internet"" to wvdial.conf and I have tried things like "Stupid Mode = 1" as well as changing the dial number, username, password etc. Whatever I do I still get the same output from wvdial.

I have also tried connecting using various versions of Vodafone Mobile Connect (with ozerocdoff and usb-modeswitch installed) but it seems to give a similar result; the device is recognised and it gets so far in connecting but then it just fails.

Everything I've tried is just based on stuff I have found on forums. I'm actually a complete ubuntu newbie and now completely out of things to try. Any ideas other than taking it back to the shop? Thanks.

[EDIT] Sorry forgot to mention - I also installed the program "3connect" through wine. It's the windows dialer program that comes on the stick, installation seemed to go fine, but again it can't connect. I should mention that I can connect using this same stick absolutely fine in windows xp.

---

### Post by jd87 on 2010-03-19
It's so nice to see the ubuntu community is so helpful and welcoming to it's users. Sigh.

---

### Post by alexfish on 2010-03-19
hi

I am not sure if the user and password are correct in the NM

have a look here

[http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/](http://polishlinux.org/linux/ubuntu/three-uk-3g-modem-in-ubuntu-linux/)

---

### Post by pdc on 2010-03-19
Hi jd87;

sorry to hear of your troubles: if you didn't get help initially, it is because there are only two very knowledgable folks who can help with mobile broadband: GeorgeVita and alexfish; and that's about it; so no answer means: they ain't on-line !

You are to be commended for all the work and googling you have done: you have learnt a lot in a very short space of time

I was able to get a ZTE modem working using wvdial; using a script GeorgeVita suggested: looks slightly different to yours; and uses ttyUSB2 rather than USB0 and I am cannot remember which search identifies which to use: but ttyUSB2 works for me!

my wvdial.conf file is below and I have added what seems to be the UK 3 APN setting

from this

[http://androidcommunity.com/forums/f41/g1-3-three-apn-settings-7744/](http://androidcommunity.com/forums/f41/g1-3-three-apn-settings-7744/)

> [Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","three.co.uk"
Phone = *99#
Stupid Mode = 1

I can only offer this for trial; I have been very pleased with wvdial; 

Ubuntu 9.10 has not been a happy story with mobile broadband: if you tell us what

> uname -r

says; the latest updates of 9.10 seem to be okay; you need to update to the 2.6.31.19 kernel I think .........

control-c cancels the connection, once you establish it

....... looking at alex's post to the polishlinux thread, 

> *Found a modem on /dev/ttyUSB1*.          was what the wvdial configure found ....... so you can only try ttyUSB1 if ttyUSB2 or ttyUSB0 do not help

---

### Post by GB_Joe on 2010-03-24
Hum.

Having just had a really bad experience with a Vodafone PAYG dongle on one friend's lappie (which ended up with me having to switch them to Win XP) I'm now researching the situation for another friend.

I went in to the 3 shop and they let me try their dongle, which was an E122. I got exactly the same results that I'm seeing in this post and everywhere else I've Googled.

It looks to me like this modem is basically not going to work with Ubuntu at this stage. I'm running the beta of Lucid on my own laptop, so I guess I may give that a go, but I'm not sure I want to turn my friend into a beta tester!

3 also say they can provide a ZTE MF627, and it looks like there me be more chance of getting this running. I don't know if that'll end up giving a slower connection though...

Anyhow, according to alexfish's link, 3 give you 3 days to return it, so perhaps I'll give that a go.

---

### Post by snip3r8 on 2010-03-26
i got my wvdial working with e220 ,it dials and i can connect (thats how im writing this now). but its not showing the connection in my notification area.

when i "ifconfig i get :
```

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:41.13.215.166  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:178 (178.0 B)  TX bytes:205 (205.0 B)

```

my wvdial.conf is :
```

[Dialer Defaults]
New PPPD = yes
Dial Command = ATDT
Dial Attempts = 1
Modem = /dev/ttyUSB0
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Username = vodafone
Password = vodafone
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0

[Dialer hspa]
Phone = *99***16#
Stupid Mode = 1
Init3 = AT+CGDCONT=1,"IP","internet"


[Dialer myPIN]
Init4 = AT+CPIN=1234


```

by the way ,1234 is not my real pin code

---

### Post by lunatico on 2010-07-10
Ok, for what it's worth, I have the Huawei E122 (Three Network Ireland) and I have used it on 3 different computers with Ubuntu (9.10, 10.04 and UNR10.04) and it works perfectly on all of them. All I had to do was:
```
sudo apt-get install usb-modeswitch libusb-dev

```
And then reboot. After login just plug-in the dongle and you'll see it on NM, click and follow the wizard.
Sometimes it requires to goes for it to connect, as in, the first time it connects and disconnects straight away, unplug and plug again and attempt a second time to connect and all is good, this only happens sometimes, I can live with it.

---

### Post by merlin_ie on 2010-07-30
> **lunatico said:**
> Ok, for what it's worth, I have the Huawei E122 (Three Network Ireland) and I have used it on 3 different computers with Ubuntu (9.10, 10.04 and UNR10.04) and it works perfectly on all of them. All I had to do was:
```
sudo apt-get install usb-modeswitch libusb-dev

```
And then reboot. After login just plug-in the dongle and you'll see it on NM, click and follow the wizard.
Sometimes it requires to goes for it to connect, as in, the first time it connects and disconnects straight away, unplug and plug again and attempt a second time to connect and all is good, this only happens sometimes, I can live with it.

gotta get you a guinness for that absolute legend of a post. just saved my head hittin the wall lol. cheers mate :D

---

### Post by biometricstu on 2010-08-17
> **lunatico said:**
> Ok, for what it's worth, I have the Huawei E122 (Three Network Ireland) and I have used it on 3 different computers with Ubuntu (9.10, 10.04 and UNR10.04) and it works perfectly on all of them. All I had to do was:
```
sudo apt-get install usb-modeswitch libusb-dev

```
And then reboot. After login just plug-in the dongle and you'll see it on NM, click and follow the wizard.
Sometimes it requires to goes for it to connect, as in, the first time it connects and disconnects straight away, unplug and plug again and attempt a second time to connect and all is good, this only happens sometimes, I can live with it.

You are a total star!!  I just dumped Windoze 7 from my sons Dell Netbook (it was unusable) and having shown him how amazing Ubuntu Netbook Remix is he was then a bit dissapointed that his 3 mobile wouldn't work.  Thanks to your genius, he is now an ubuntu convert.  Once again a BIG thanks

---

### Post by lunatico on 2010-08-17
> **biometricstu said:**
> he is now an ubuntu convert.  Once again a BIG thanks

YES! Keep the converts coming!

---

### Post by Blojic on 2010-08-20
> **lunatico said:**
> Ok, for what it's worth, I have the Huawei E122 (Three Network Ireland) and I have used it on 3 different computers with Ubuntu (9.10, 10.04 and UNR10.04) and it works perfectly on all of them. All I had to do was:
```
sudo apt-get install usb-modeswitch libusb-dev

```
And then reboot. After login just plug-in the dongle and you'll see it on NM, click and follow the wizard.
Sometimes it requires to goes for it to connect, as in, the first time it connects and disconnects straight away, unplug and plug again and attempt a second time to connect and all is good, this only happens sometimes, I can live with it.

+ another one. Love you man.

Lucid / E122 on Three UK / needed another internet connection to install packages. As lunatico said; now and again you need to unplug/plug (hot) the dongle but, other than that, it worked a dream.

---

### Post by staby on 2010-08-23
> sudo apt-get install usb-modeswitch libusb-dev
Thank You

---

### Post by stefcep on 2010-08-25
Anyone had any luck in getting this to work with 9.04?

I'm happy with 9.04, all my harware EXCEPT for the E122 modem works ( I'm using the E220 but upgraded to the E122 with the new 3 deal), so I want to stay on 9.04, and not change my OS for the sake of getting a modem to work, if I can.

---

### Post by jarviser on 2010-08-29
Just to add to the discussion,. as someone from outside USA it's always best NOT to select from drop-down lists of countries and ISPs in the mobile broadband network connection panels. If possible, look up the APN for your ISP in Google, or better still if you can get the dongle set up on a windoze PC, look at the APN in the setup. This is particularly the case with newer PAYG packages which have APNs very different from the USA contract APNs in the Network Connection in Ubuntu.

Then after selecting device then country,  use the "I can't find my provider..." selection and simply name the connection, type in the correct APN and that is usually all that is required. Check the dial sequence is correct but it's usually *99#

Neither my UK Orange contract nor UK Vodafone PAYS will accept the default settings

---

### Post by adamadamadam on 2010-08-31
[QUOTE```
sudo apt-get install usb-modeswitch libusb-dev

```And then reboot. After login just plug-in the dongle and you'll see it on NM, click and follow the wizard.[/QUOTE]

  Total noob questions (using 10.04LTS)
1. Does that code go into 'terminal'? and
2. What is NM?
Cheers

---

### Post by jarviser on 2010-08-31
NM is Network Manager (There is usually also an icon in the panel)

If you highlight the command and Ctrl-C to copy, go into Terminal and Ctrl+Shift+V to paste in. As it starts with sudo it will need your logon password

---

### Post by adamadamadam on 2010-08-31
Thanks, but still no love happening :(
Ive entered the code and password- progress happens (building dependency tree etc)
and rebooted. Then nothing comes up automatically in network manager and adding manually doesn't seem to do much, but i am rather unskilled.

When I open the 3 Mobile icon that is displayed on the desktop after plugging in the USB, i run the autorun.exe and get an archive manager message saying 

"an error occured-something about an end-of-central-directory signature not found. Either this file is not a zipfile, or it constitutes one disk of a multi-part archive"....yadda yadda yadda

---

### Post by jarviser on 2010-08-31
Ignore the files on the dongle - they are for windows.

If the dongle is on the list of Ubuntu recognized dongles, you only have to click on the NM icon, select the one that says "connect to new Mobile Broadband connection" or similar words, then follow the instructions using the "I cannot find my supplier" create a new connection and enter the CORRECT APN for your supplier. The correct APN is usually available on Google, but check a few as they change. Alternatively load the thing on Windopws and look at the APN in the profile - it will be there somewhere

see [here]("http://www.jarviser.co.uk/jarviser/3gdell5510lucidlynx.html")  also

---

### Post by adamadamadam on 2010-08-31
ahh, there seems to be the problem. my dongle is NOT recognised (as far as I can tell) and when i click on the NM icon, there is no "connect to new mobile broadband connection" option.

---

### Post by jarviser on 2010-08-31
Try right click on icon and Edit Connections. In the Mobile broadband tab do an Add, and it should offer you the option to use the dongle  in the list of devices on the first page. If it's not there it's not being recognized. If it is, proceed as per my article, but be prepared to try the manual (Can't find my supplier...") method rather than selecting from the drop-downs of ISPs.

---

### Post by lunatico on 2010-08-31
> **adamadamadam said:**
> ahh, there seems to be the problem. my dongle is NOT recognised (as far as I can tell) and when i click on the NM icon, there is no "connect to new mobile broadband connection" option.

Are you sure you have a Huawei E122 dongle there?

---

### Post by jarviser on 2010-08-31
Alternatively, this week I had a similar problem where it would not recognize any dongles. This was straight after I experimented with the Betavine Vodafone connection package which screwed the NM. In fact I watched the connection disappear half way through installing the package. Turns out there is an alpha version for 10.04 in Betavine which is still not perfect! Not going there again.
 In the end I reinstalled Ubuntu - OK now.

---

### Post by alexfish on 2010-08-31
> **jarviser said:**
> Alternatively, this week I had a similar problem where it would not recognize any dongles. This was straight after I experimented with the Betavine Vodafone connection package which screwed the NM. In fact I watched the connection disappear half way through installing the package. Turns out there is an alpha version for 10.04 in Betavine which is still not perfect! Not going there again.
 In the end I reinstalled Ubuntu - OK now.

[COLOR=#980101]****[/COLOR] [VMC software from Betavine{ vodafone mobile  connect re:Betavine Connection Manager}]("http://ubuntuforums.org/showthread.php?t=1548553")

---

### Post by jarviser on 2010-08-31
> **alexfish said:**
> [COLOR=#980101]****[/COLOR] [VMC software from Betavine{ vodafone mobile  connect re:Betavine Connection Manager}]("http://ubuntuforums.org/showthread.php?t=1548553")

D'OH!  And I thought I had done a search for Betavine too!

---

### Post by adamadamadam on 2010-09-08
yep, its definitely the E122 model, says it right on the modem. 
Tried the right click on NM, checked the Mobile Broadband tab and it's not recognised there :( 
As I've mentioned earlier, the files contained on the dongle are recognised, so there isn't a problem with the USB connection. 
Is there anything else i can try??

---

### Post by lunatico on 2010-09-08
> **adamadamadam said:**
> Is there anything else i can try??

uhm... and you're absolutely sure that you ran
sudo apt-get install usb-modeswitch libusb-dev
and that the packages where in fact installed without errors?
you can try running the command again and check the output, it'll say if they're already installed or if it fails to install...
other than that I'm not sure...

---

### Post by jonnybgreen on 2010-10-24
> **adamadamadam said:**
> yep, its definitely the E122 model, says it right on the modem. 
Tried the right click on NM, checked the Mobile Broadband tab and it's not recognised there :( 
As I've mentioned earlier, the files contained on the dongle are recognised, so there isn't a problem with the USB connection. 
Is there anything else i can try??
This is a bit longwinded but here goes. I have dual boot Vista and Ubuntu 10.04. Before Lunatico put up his post-thankyou brother-I was having to first boot up Windows with the E122 dongle attached or attached after bootup and connect to the internet then disconnect and restart in Ubuntu. Then the dongle would be recognised by NM and I could connect but only once! So if you disconnected you'd have to restart in Windows and go through it again. I tried a few fixes but it just confused everything-I am certainly not an expert-and in the end I reinstalled and went with above. Ok now assuming you can connect you can then put in Lunatico's command which should Stop you going to Windows to 'initialise' the dongle. I still have problems-I switch my pc off at the plug at night and when I'm not using it,I think its more eco,so when I switch on I have to connect the dongle after bootup in Ubuntu and when the light on the dongle flashes blue-are you getting green followed by blue lights?-right click NM and click enable Mobile Broadband then click NM and click in my case Three Ireland Default 1-NM gave it this name-and it connects. When I want to disconnect I right click NM and unclick enable Mobile Broadband because if you click NM and click disconnect you cant reconnect without physically disconnecting the dongle from the pc.Phew...hope this makes sense and you can connect ok. There's a few othe rblips but if you can connect you're 90% there. I use Ubuntu 99% of the time but it has been useful having Windows sometimes....you can download packages on Windows then when you're in Ubuntu copy&paste the package into Ubuntu right click on the package and you have the option to install....you can also read the forums. Hope it works out. Going to have anothe rlook at what jarviser says now.

---

### Post by jaqian on 2010-11-01
> **lunatico said:**
> Ok, for what it's worth, I have the Huawei E122 (Three Network Ireland) and I have used it on 3 different computers with Ubuntu (9.10, 10.04 and UNR10.04) and it works perfectly on all of them. All I had to do was:
```
sudo apt-get install usb-modeswitch libusb-dev

```
And then reboot. After login just plug-in the dongle and you'll see it on NM, click and follow the wizard.
Sometimes it requires to goes for it to connect, as in, the first time it connects and disconnects straight away, unplug and plug again and attempt a second time to connect and all is good, this only happens sometimes, I can live with it.

Brilliant! I can now switch a friend from winXP to LinuxMint, saves me a lot of headaches :)

---

### Post by jaqian on 2010-11-04
> **lunatico said:**
> Ok, for what it's worth, I have the Huawei E122 (Three Network Ireland) and I have used it on 3 different computers with Ubuntu (9.10, 10.04 and UNR10.04) and it works perfectly on all of them. All I had to do was:
```
sudo apt-get install usb-modeswitch libusb-dev

```
And then reboot. 

Thanks for this it works great on my desktop and my friends (both Mint9). I have an old Dell Dimension 4000 that I stuck u-lite (ubuntu lite) on and tried the above command but doesn't seem to work.

U-lite seems to be based on Hardy Heron, do I need to point the computer to different repositories to download usb-modeswitch? 

Thanks.

---

### Post by lunatico on 2010-11-04
> **jaqian said:**
> Thanks for this it works great on my desktop and my friends (both Mint9). I have an old Dell Dimension 4000 that I stuck u-lite (ubuntu lite) on and tried the above command but doesn't seem to work.

U-lite seems to be based on Hardy Heron, do I need to point the computer to different repositories to download usb-modeswitch? 

Thanks.

Uhm as far as I remember with Hardy I went the Vodafone software way not the NM way...
[https://forge.betavine.net/projects/vodafonemobilec/](https://forge.betavine.net/projects/vodafonemobilec/)

---

### Post by jaqian on 2010-11-05
Thanks for that just couldn't get it working so jacked it in and am now using Mint9 with Fluxbox... the modem works great. Thanks :)

---

### Post by Eirspeed on 2010-11-17
d

---

### Post by jaqian on 2010-11-18
> **Eirspeed said:**
> What I've been doing (strictly for project uses, of course) is running the modem on my mac, then connecting the modem via virtual machine software to a VM running ubuntu. Seems to work for me.

By the way, glad to see a fellow Irish Ubuntu fan, its actually a rural mobile broadband project for the young scientist.

I wouldn't have enough ram (512) to run a virtual machine but interesting idea. Whats the project? It wouldn't be trying to get broadband service outside of Dublin would it? ;)

Yeah like Debian/Ubuntu, find it the easiest to use.

---

### Post by Eirspeed on 2010-11-21
d

---

### Post by Eirspeed on 2010-11-21
d

---

### Post by Xalabam on 2010-11-23
> **lunatico said:**
> Ok, for what it's worth, I have the Huawei E122 (Three Network Ireland) and I have used it on 3 different computers with Ubuntu (9.10, 10.04 and UNR10.04) and it works perfectly on all of them. All I had to do was:
```
sudo apt-get install usb-modeswitch libusb-dev

```
And then reboot. After login just plug-in the dongle and you'll see it on NM, click and follow the wizard.
Sometimes it requires to goes for it to connect, as in, the first time it connects and disconnects straight away, unplug and plug again and attempt a second time to connect and all is good, this only happens sometimes, I can live with it.


man, THX A LOT.

---

### Post by lunatico on 2010-11-24
Hey Guys,

Now I'm the one who needs help. Basically at work I had to stop using network-manager because of a bad bug so I'm using WICD now.

Unfortunately it only supports wired and wireless connections so I have to find another way of connecting with my usb donggle.

Does anyone have a working wvdial.conf script for Three Ireland?

Thanks!

---

### Post by Eirspeed on 2010-11-25
d

---

### Post by lunatico on 2010-11-26
> **Eirspeed said:**
> Three sucks anyways, unless you're a farmer in rural Connemara? :D (whom I to talk I live in Kildare)


Ah! Not a farmer in Connemara... more of an IT geek around Glway City and Oranmore.... I don't dislike Three that much... I used to have a Vodafone dongle and then switched to Three and this work better for me in terms of coverage and price vrs. download allowance.

Anyway.... network manager is fine, it's almost perfect and I would love to keep using it. I am still using it at home but on my work computer I stopped using it because of this bug:
[http://ubuntuforums.org/showthread.php?t=1607284](http://ubuntuforums.org/showthread.php?t=1607284)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992)

So for wired and wireless I'm using WICD now, I'm forced to.

---

### Post by Eirspeed on 2010-11-26
d

---

### Post by oliphaunt on 2011-03-31
> **lunatico said:**
> Ok, for what it's worth, I have the Huawei E122 (Three Network Ireland) and I have used it on 3 different computers with Ubuntu (9.10, 10.04 and UNR10.04) and it works perfectly on all of them. All I had to do was:
```
sudo apt-get install usb-modeswitch libusb-dev

```
And then reboot. After login just plug-in the dongle and you'll see it on NM, click and follow the wizard.

I just registered here to thank you!  It works great here with T-Mobile in the Netherlands too.

---

### Post by lunatico on 2012-08-02
Modem doesn't seem to be working on Linux Mint 13, therefore I suspect it's not working on Ubuntu 12.04. Has anyone tried on 12.04?

---

