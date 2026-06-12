---
title: "Configuring Huawei Wireless USB Broadband Modem"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by LequidMetal on 2009-04-17
Hi,

      I would like to know how to connect to the Internet using a  Huawei USB Broadband Modem .I have to use a Broadband client software to connect to the Internet in windows.So i just called the Customer support and they told me that they have a windows and Mac client  but not a linux client . So i am  guessing that it may have some kinda native support in linux . ? Need some help configuring it to connect to the internet

[COLOR="Red"]Info [/COLOR]
[ATTACH]110085[/ATTACH]
Huawei USB Modem (3.1Mbps) 
Model - EC 168C
ISP - Reliance Communications
Operating system -Kubuntu 8.10


[COLOR="Red"]lsusb dump[/COLOR]
```

Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 12d1:1412 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by w0lv3n on 2009-04-17
im still only learning, but what does it say when you punch this is in:
```
ls /dev/ttyU*
```
Has it mounted the device?

---

### Post by LequidMetal on 2009-04-17
No idea .... this is what i got 

```

/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2  /dev/ttyUSB3

```

Edit :
FYI : i am on Gnome currently .....

---

### Post by w0lv3n on 2009-04-17
hrmm, well i spose you could try and do what I did...

in terminal:
```
sudo modprobe usbserial vendor=0x12d1 product=0x1412
```

It probably wont change a thing now that I think about it, as its already registered under tty*.

Who is the internet with? Do you need a Username/Password?

I'd recommend trying to use wvdial or a gui like gnomePPP.

```
sudo gedit /etc/wvdial.conf
```

Edit this file to something like this:
```
[Dialer Defaults]
Modem = /dev/ttyUSB2

Modem Type = Analog Modem

ISDN = 0

Baud = 460800

Dial Attempts = 1

Username = user@bigpond.com

Password = password

Init1 = ATZ

Init2 = AT&F &D2 &C1

Init3 = ATS7=60 S30=0 S0=0

Init4 = AT+CGDCONT=1,"IP","telstra.bigpond"

Phone = *99***1#

Stupid Mode = 1
```

Only parts you should need to change would be username, password and APN. If you dont need username and password, put something like 'wap' in both.
If your not sure wat your APN is, do a google for "APN yourISP" (where yourISP is obviously... your.. isp...)

Once you have done that, 
try running "wvdial" in terminal
hopefully it will connect for you. If it does, its a workaround for now at least!

hope some of this helps, im only new at this but i doubt any of this ^ could break it :P

---

### Post by LequidMetal on 2009-04-17
yup i need a username and password ..... 


I was trying something similar ...... Heres what i got executing wvdial after making the required modification

sudo wvdial
```


--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Apr 17 20:59:02 2009
--> Pid of pppd: 5948
--> Using interface ppp0
--> local  IP address 115.xxx.xxx.xxx
--> remote IP address 220.xxx.xxx.xxx
--> primary   DNS address 202.xxx.xx.xxx
--> secondary DNS address 202.xxx.xx.x


```

Am i connected ??? Currently i am using a different connection(wired) to log into this forum

how do i know when the connection is working ??

---

### Post by LequidMetal on 2009-04-17
^ ok 

It seems to have been connected but for some reason refuses to load webpages 


I tried disconnecting the device (unplugging the modem) with wvdial running this is what i got

```


 Connect time 9.9 minutes.
--> Disconnecting at Fri Apr 17 21:09:07 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Disconnecting at Fri Apr 17 21:09:07 2009


```

cant figure out whats wrong ..... the modem seems to have connected but wont load any web pages

---

### Post by w0lv3n on 2009-04-17
Ok, well at least we have gotten somewhere.

Now I would look into downloading gnomePPP or similar for your os, and configure it accordingly.

We know that the modem is identified and works, so now we just have to get the right way to connect it i suppose!

I will try and dig up the info I once used to connect a similar huawei modem.

---

### Post by w0lv3n on 2009-04-17
also just thinking about it, this may sound silly but when you are 'connected' make sure "work offline" is not selected!

here is a url for GnomePPP as I guess you cant download it from linux.
[http://www.gnomefiles.org/app.php?soft_id=41](http://www.gnomefiles.org/app.php?soft_id=41)

Still searching for the configuration required but Im quite sure its straight forward. Give it a crack and have a play!

---

### Post by Chokkan on 2009-04-18
Checking the work offline box is a good idea. Also make sure your user is in the dialout group.

---

### Post by LequidMetal on 2009-04-18
I am currently using a wired Internet connection inside Linux itself ! 

Ofcourse i do log out before testing my wireless modem 

all of my posts here were made from Linux 

and where is this 'work offline' mode option and dial out group ??

ps using Kubuntu so gonna to try out kppp

---

### Post by tofiluk on 2009-04-18
hi! i also happen to be using huawei.

do you think you just missed some configuration?

in my case, i have to edit the connection by changing the APN from minternet to fbband

---

### Post by LequidMetal on 2009-04-18
its possible .... where do i do that ?

should i try unplugging my wired Internet and then running my USB modem  ?

---

### Post by w0lv3n on 2009-04-18
the APN is editable in the 'wvdial.conf' file that i posted earlier. In my example the APN is 'telstra.bigpond' you will haev to search for the appropriate APN for your provider.

Forgot you were running kubuntu!

I would try starting linux perhaps without the wired connection. It shouldnt make a difference, but that way you can be sure I spose.

The "work offline" option is in the file menu of Firefox, down the bottom just above 'quit'

See how you go!

---

### Post by LequidMetal on 2009-04-18
i am posting from linux so that (work offline) obviously is not selected

btw i have a separate dialler software provided by my isp for my wired Internet ......

---

### Post by tofiluk on 2009-04-18
> **w0lv3n said:**
> the APN is editable in the 'wvdial.conf' file that i posted earlier. In my example the APN is 'telstra.bigpond' you will haev to search for the appropriate APN for your provider.

Forgot you were running kubuntu!

I would try starting linux perhaps without the wired connection. It shouldnt make a difference, but that way you can be sure I spose.

The "work offline" option is in the file menu of Firefox, down the bottom just above 'quit'

See how you go!

yes, the provider gives you the APN. :D actually, i had easier time configuring my huawei in ubuntu than with windows.

---

### Post by LequidMetal on 2009-04-18
```


Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = #777
New PPPD = yes
Modem = /dev/ttyUSB0
Username = name 
Password = password
CBaud = 460800

```

i was using this blog as a guide 

this blogger used the same modem and isp

[http://animeshmeher.wordpress.com/](http://animeshmeher.wordpress.com/)

it doesnt work for me though

---

### Post by LequidMetal on 2009-04-18
I tried Genome-ppp

I went to the modem tab and clicked "Detect" after setting the type as USB 


it returned dev/tty/USB2  and

Type was automatically changed from USB to analog modem 


i dont think gppp is correctly detecting my modem .... what do i do now ??

---

### Post by skintythe1andonly on 2009-04-18
I have had these working with kubuntu a while ago (hardy testing) using the vodafone drivers for them but they are supposed to sork with all huawei as long as you have the right settings 

[https://forge.betavine.net/projects/vodafonemobilec/]("https://forge.betavine.net/projects/vodafonemobilec/")

---

### Post by LequidMetal on 2009-04-18
ok managed to get it connected :popcorn: [i had to change that usbtty thingy to USB2]

i am finally posting from my wireless connection ........ yay ! 

but my problem has nt been solved yet ......:(

i can connect only by using the commandline 

```

sudo wvdial 

```

both genome-ppp and kppp refuse to work 

when i queried my modem using my kppp my computer hung up

gppp seems to be detecting the modem ..... but refuses to connect to the internet
[COLOR="Red"]
Please help me setup a kppp account [/COLOR]

---

### Post by amitabhishek on 2009-04-18
[http://www.thinkdigit.com/forum/showthread.php?p=1093545&posted=1#post1093545](http://www.thinkdigit.com/forum/showthread.php?p=1093545&posted=1#post1093545)

---

### Post by w0lv3n on 2009-04-18
Well congrats on getting connected at least!

When gPPP or kPPP detects the modem, it will likely set it as an analog modem. This is the same for wvdial. Also, tty/usb2 is the most common port for the modem.

I think if you try and give either of the PPP clients a crack using the autodetect settings you might get it working.
Just make sure your APN and username and password are correct. Also, see if you can track down the correct phone number for your ISP, usually it would be ```
*99#
```
another one to try:
```
*99***1#
```

hopefully you can make this work.

Otherwise you could just make a launcher for the wvdial command and then just double click?

---

### Post by Chokkan on 2009-04-19
Command line is the way I connect as I just gave up trying to do it through GnomePPP. Would be nice to get it working though.

---

### Post by LequidMetal on 2009-04-19
> **w0lv3n said:**
> Well congrats on getting connected at least!

When gPPP or kPPP detects the modem, it will likely set it as an analog modem. This is the same for wvdial. Also, tty/usb2 is the most common port for the modem.

I think if you try and give either of the PPP clients a crack using the autodetect settings you might get it working.
Just make sure your APN and username and password are correct. Also, see if you can track down the correct phone number for your ISP, usually it would be ```
*99#
```
another one to try:
```
*99***1#
```

hopefully you can make this work.

Otherwise you could just make a launcher for the wvdial command and then just double click?

Yeah i could .... but Genome-ppp seems to have some extra features does nt it ? ....

could this be that number ?? 
```

#777

```

and where do i enter it ?

---

### Post by w0lv3n on 2009-04-19
it could be that number.
open up wvdial.conf again and post it up here. As you have been able to connect with that file, it contains all the info we need. **Be sure to delete your username and password from it though!**

In GnomePPP you can change the number on the main dialog i think. Im in vista at, but tomorrow morning I will look at it again.

What ever settings you can change in GnomePPP or kPPP - and that are in your wvdial.conf, then change them to the onesvalues of the wvdial.conf.

sorry if that sounds confusing lol.

good luck, talk to you again soon.

---

### Post by LequidMetal on 2009-04-20
sorry had some work ...... could nt log into linux yesterday ....

Heres my wvdial.conf

```

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = #777
New PPPD = yes
Modem = /dev/ttyUSB2
Username = name 
Password = password
CBaud = 460800

```

---

### Post by w0lv3n on 2009-04-20
Who is your isp?

Try running one of the other phone numbers I listed (the 99 ones) and see any of those work. Im just a bit curious as to the layout of the #777 number as it starts with a # as oppose to ending with one.

Maybe you could even try *777# instead?
If its the way Im thinking it is, a hash is 'end' command so if it tries to dial #777 it thinks there is only # , thus no number.

Will look into it for you!

---

### Post by skintythe1andonly on 2009-04-21
[http://ubuntuforums.org/showthread.php?t=633981]("http://ubuntuforums.org/showthread.php?t=633981")

This is a good place to start also if you are going through the wvdial.conf route

---

### Post by LequidMetal on 2009-04-21
> **LequidMetal said:**
> sorry had some work ...... could nt log into linux yesterday ....

Heres my wvdial.conf

```

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = #777
New PPPD = yes
Modem = /dev/ttyUSB2
Username = name 
Password = password
CBaud = 460800

```

I think theres some confusion ..... let me clarify 

I **[COLOR="Red"]can connect to the internet using the wvdial[/COLOR]** commandline 
so obviously the above config works .....
But i [COLOR="Red"]**am not able to connect**[/COLOR] to the same using **[COLOR="Red"]Genome-ppp [/COLOR]**
where i get the invalid Phone number error .

My ISP - Reliance Communications (CDMA / 3G /India)

---

### Post by LequidMetal on 2009-04-22
Heres a screenshot of my Gnomeppp Modems tab .
Please tell me where i am going wrong :)

[CENTER][B][COLOR="Red"]click on the image to maximise it and open it in a new window/tab[/COLOR] 
[/B]

[attach]110577[/attach]

[attach]110578[/attach][/center]

---

### Post by w0lv3n on 2009-04-22
Firstly, just make sure you hit "detect" and leave it with wat it comes up with (even if it says "analog modem")

Any chance you could post a screenshot of what is in the "init strings" button?

I now recall that I had to put some extra commands in when I got mine to work... will look it up

---

### Post by w0lv3n on 2009-04-22
Ok, after looking over what we have gone through so far, I think I may of found the problem. So lets give it a crack.

Originally you posted
> Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = #777
New PPPD = yes
Modem = /dev/ttyUSB2
Username = name 
Password = password
CBaud = 460800
As your wvial.conf

I noticed now that there is not init string for setting your APN.

So firstly, lets try and add that to the wvdial.conf gnomePPP uses this conf aswell as options in its GUI im quite sure.

```
sudo gedit etc/wvdial.conf
```

Now make it look like this:
> Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
**Init3 = AT+CGDCONT=1,"IP","*APN*"**
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = #777
New PPPD = yes
Modem = /dev/ttyUSB2
Username = name 
Password = password
CBaud = 460800

***APN*** is where your WPN must be entered. Mine is *telstra.bigpond* so yours should be something similar. Search "youisphere APN" in google and you should have no trouble finding it. (I would do this, but I cant seem to find where your posted your ISP if you did?)

Now that thats done, save the file.

Now open gnomePPP
goto Setup > Modem tab > click Init Strings
check what is in here, there should be at least 2 strings.
Check to see if there is a line similar to " AT+CGDCONT=1,"IP","3netaccess" " .
If not, enter it into the next blank line. If it is, check that the APN is correct.

Save all changes.

Try connecting, let me know how you get on.
Good luck
-W

---

### Post by LequidMetal on 2009-04-23
sorry could nt find the correct APN for my connection

I did try an APN but i got a "Command not found" error . So obviously its the wrong one

**My ISP - Reliance Communications** 


APNs that i came across for this isp are listed as follows
rcomwap - for GSM WAP settings
rcommms - for GSM MMS settings
rcomnet - Reliance Netconnect (200kbps)  Wireless Broadband ( Not the one i use)
   


I use 
Reliance NetConnect Broadband+ (3.1mbps) Wireless Broadband (The one i use) 
could nt find the correct APN

---

### Post by LequidMetal on 2009-04-23
[CENTER]My InitString  screenshot 
 (Taken from Gnome)

[ATTACH]110704[/ATTACH][/CENTER]

---

### Post by LequidMetal on 2009-04-23
> **w0lv3n said:**
> 
So firstly, lets try and add that to the wvdial.conf gnomePPP uses this conf aswell as options in its GUI im quite sure.


From my understanding Gnome-ppp is a frontend GUI for wvdial..... if that is so , i simply cannot understand how i can connect with wvdial but not with Gnome-ppp ..... Maybe Gnome-ppp uses a new configuration rather than any existing one ?

---

### Post by w0lv3n on 2009-04-23
Yes gPPP is a frontend for wvdial as far as I know aswell, but i added the extra part about putting the init string into gPPP aswell simply because I wanted to be sure it was there.

I dont understand how you can be connecting to the net atm either, without an APN defined in wvdial.conf.... im no pro and it has stumped me!

rcomwap is your APN, so add this line - through gppp should be fine.
Init3 =```
AT+CGDCONT=1,"IP","APN"
```

good luck!

---

### Post by LequidMetal on 2009-04-24
Nope thats not my APN 

using that particular APN i get this error in wvdial
```

--> Sending: AT+CGDCONT=1,"IP","rcomwap"
AT+CGDCONT=1,"IP","rcomwap"
COMMAND NOT SUPPORT
--> [COLOR="Red"]Re-Sending[/COLOR]: AT+CGDCONT=1,"IP","rcomwap"
AT+CGDCONT=1,"IP","rcomwap"
COMMAND NOT SUPPORT
--> Modem not responding.

```

Gnome-ppp

```

--> Sending: Init3 = AT+CGDCONT=1,"IP","rcomwap"
--> Sending: ATQ0
ATQ0
OK
--> [COLOR="Red"]Re-Sending[/COLOR]: Init3 = AT+CGDCONT=1,"IP","rcomwap"
--> Modem not responding.


```

My conclusions :
1) My connection does nt seem to need an APN
2) It may not even have an APN :lolflag:
3) If it does its impossible to find it . :(

---

### Post by LequidMetal on 2009-04-24
Exciting Update 

I was able to simulate the error i get in Gppp , in the terminal !
I got this error when in my haste i entered 
```

wvdial

```

rather than 

```

sudo wvdial

```

I ll post the error codes here

---

### Post by LequidMetal on 2009-04-24
Error i get when i normally execute[COLOR="Red"]** gnomeppp**[/COLOR]

```

--> Carrier detected.  Starting PPP immediately.
-->[COLOR="Red"] Unable to run /usr/sbin/pppd.[/COLOR]
--> [COLOR="Red"]Check permissions[/COLOR], or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}!} }8}"}&} } } } }#}$@#}%}&{7}?[06]}'}"}(}" } ~~[7f]}#@!}!}"} }8}"}&} } } } }#}$@#}%}&{7}?[06]}'}"}(}"C[12]~
^HRSSILVL:99

```


Error i get when i execute wvdial [COLOR="Red"]without a sudo[/COLOR] in the [COLOR="Red"]**terminal**[/COLOR]

```

--> Carrier detected.  Starting PPP immediately.
--> [COLOR="Red"]Unable to run /usr/sbin/pppd.[/COLOR]
--> [COLOR="Red"]Check permissions[/COLOR], or specify a "PPPD Path" option in wvdial.conf.
~[7f]}#@!}!}%} }8}"}&} } } } }#}$@#}%}&[14]q@[14]}'}"}(}"J[13]~~[7f]}#@!}!}&} }8}"}&} } } } }#}$@#}%}&[14]q@[14]}'}"}(}" }!~~[7f]}#@!}!}'} }8}"

```

---

### Post by LequidMetal on 2009-04-24
super user privileges ! That is what stands before me and a successful connection 

Now , how do i execute Genome with super user privileges ?? :confused:

PS : i am the only user account in my Ubuntu installation

---

### Post by LequidMetal on 2009-04-24
Unexciting update

i tried running 
```

gksudo GNOME PPP

```

Did nt work ..... i get exactly the same error 

It seems Genomeppp runs wvdial without a sudo :(

---

### Post by urjoon on 2009-05-05
Hey guys,

i just bought a Reliance Netconnect HUawei EC 168C rotable USB Stick.

No need for any configuration or drivers on Ubuntu 9.04 Jaunty Jackalope.

Just plug it in.

"Preferences>Network Connections> Mobile Broadband" should detect "Auto Mobile Broadband CDMS connection"

select the connection to add phone number "#777" and you username/ password, both of which should be your 10 digit phone number.

that is all. choose the connection from notification area and enjoy.

in case it does not work. just try the following command on the terminal.

"sudo wvdialconf /etc/wvdial.conf" which will
detect the modem and install it for internet connection.

the process is much simpler than configuring the modem on windows.

---

### Post by smydtt on 2009-07-24
[FONT="Comic Sans MS"]I recently bought a reliance netconnect using Huawei EC1260 modem. The method described above works with this model as well, (at least it worked with me both on my desktop and laptop, on Ubuntu 9.04) so I would presume that it should work with any modem from Huawei for reliance netconnect. I just have the following additional points to note:

1. If on inserting the USB modem, Ubuntu automatically does not detect it, then one has two options:
 a) Configure the wvdial.conf file using the method given above, i.e. install wvdial from synaptic, then run sudo wvdialconf /etc/wvdial.conf, and then run sudo wvdial everytime you need to connect to internet.
b) alternately, after configuring the wvdial file, you can go to Preferences >> Network Connections, click on mobile broadband. If it has not already detected your connection, go to add connections, and choose from a list of connections. Since Reliance Netconnect is not included in this list, you can choose a similar connection like Tata Indicom Plug2surf, and then edit the connection by changing the phone no. to #777 and username and password to your 10-digit reliance netconnect no. Now this connection should automatically be detected everytime you insert the modem, so one does not have to go to terminal and type "sudo wvdial" everytime.

2. The other issue I faced was a corruption in the wvdial.conf file in some of the repositories. I had downloaded this from the main server, and it seems that there was some error in this file, where some junk characters had inadvertently crept into the file. If you are unable to configure your wvdial, it could possibly be because of a similar error. In this case, open this file using a text editor, and look for obvious errors, alternately, remove this file, change your repository and download wvdial again.[/FONT]

---

