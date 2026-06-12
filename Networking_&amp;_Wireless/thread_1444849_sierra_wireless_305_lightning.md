---
title: "sierra wireless 305 lightning"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by yllek on 2010-04-01
i have a sierra wireless usb 305 lightning. it says it is compatible with ubuntu but when i configure it it will try to connect to the internet and then give me a message that it has disconnected. it will not connect at all. i have a dell inspiron b130 laptop. what am i doing wrong. please help. im trying ubuntu 9.10

---

### Post by Wiebelhaus on 2010-04-01
Yep , I had the same issue on a Customers Machine.

> **Note: Ubuntu 9.10 distribution is not supported with Sierra Wireless modems. Ubuntu 9.04 distribution is still supported with all Sierra Wireless modems listed in this KB article.
We expect the issue to be fixed in Ubuntu 10.4.

[Source]("http://sierrawireless.custhelp.com/app/answers/detail/a_id/641/~/can-i-use-a-sierra-wireless-modem-on-linux-machines-(direct-ip-modems)%3F")

---

### Post by thesenu on 2010-04-02
i use sierra 885..

---

### Post by yllek on 2010-04-02
i have the 305 i dont need to get another usb card i need help installing the one i have

---

### Post by alexfish on 2010-04-03
Hi

I don't know this modem. however it may help to find out the type of modem and also see if any drivers are loading when it is plugged in, 

Boot up the computer without the modem , give the system time to settle, then plug the modem in , then from the terminal enter these commands an post the results

Code:

lsusb

this should tell you which type of modem it is

Code:

dmesg | grep -e "modem" -e "tty" 

this will show which lines the modem is using


from a seperate terminal

Code;

tail -f /var/log/syslog

this will show what is happening when the modem is plugged in

with this info it may be possible to get it working

also check with your ISP any details of phone number , user name , password, any the servers they normally connect to , get the named server and possible two of the numerical addresses for the server, and if it uses pap or chap

thanks in advance

alexfish

---

### Post by sc0g on 2010-06-07
-----------------------------------
UPDATE 06/15/2010, 15:37

I found this tutorial for the USBConnect Lightning (USB 305) device: [http://sierrawireless.custhelp.com/app/answers/detail/a_id/641/kw/modem%20command%20lightning](http://sierrawireless.custhelp.com/app/answers/detail/a_id/641/kw/modem%20command%20lightning). I downloaded their patch for the 2.6.32 kernel and used their instructions. 

After building this module and rebooting, the Kubuntu Network Manager recognizes the device and it is ready to use. Have not tried KPPP since I was able to get it working using network manager.

Obviously, the downside to using this method is that you must rebuild the module every time you install/update your kernel.
-----------------------------------



**Does anyone have any idea what the proper Dial Command is for this device?**


I am using this modem as well, Sierra Wireless USB 305 (USBConnect Lightning). I've tried using KPPP and WVDIAL, but the dial command *ATDT*99#* throws *ERROR - INVALID DIAL COMMAND* every time.    :(

I'm running Ubuntu 10.4, Linux 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

lsusb:
```
Bus 002 Device 008: ID 1199:68a3 Sierra Wireless, Inc.
```

dmesg:
```
[431557.818224] sierra 2-1:1.4: GSM modem (1-port) converter detected
[431557.818317] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[431557.818388] sierra 2-1:1.3: GSM modem (1-port) converter detected
[431557.818437] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[431557.818478] sierra 2-1:1.1: GSM modem (1-port) converter detected
[431557.818525] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[431557.818567] sierra 2-1:1.7: GSM modem (1-port) converter detected
[431557.818630] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
```

My WVDIAL configuration:
```
[Dialer Defaults]
Modem = /dev/ttyUSB0
ISDN = off
Modem Type = USB Modem
Baud = 460800
Init1 = ATX3
Init2 = at+cgdcont=1,"IP","ISP.CINGULAR"
Phone = *99#
Dial Prefix = 
Dial Attempts = 1
Dial Command = ATDT
Ask Password = off
Username = ISP@CINGULARGPRS.COM
Password = CINGULAR1
Auto Reconnect = off
Abort on Busy = off
Carrier Check = on
Check Def Route = on
Abort on No Dialtone = on
Stupid Mode = on
Idle Seconds = 0
Auto DNS = on
```

My output when running WVDIAL:
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: at+cgdcont=1,"IP","ISP.CINGULAR"
at+cgdcont=1,"IP","ISP.CINGULAR"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
ERROR
--> Invalid dial command.
--> Disconnecting at Mon Jun  7 13:50:30 2010
```


Any help would be greatly appreciated!!

---

### Post by mattmcshane on 2010-10-13
Just to let you know there are some information that is incorrect.

First is AT&T does not have a user name and password, both MUST be blank.

Second is the dial number it should be *99***1#

Third is:

Init1 = ATX3 ** not sure about this.
Init2 = [at+cgdcont=1,"IP",]   ["ISP.CINGULAR"] 
            [ALL CAPS]            [all small]

can also sub "Broadband" for "isp.cingular" (both are provisioned APN's)

Fourth is: Im not entirely sure if this setting makes a difference, but at least with AT&T there is NEVER a dial tone, and if it aborts on no dial tone it will never connect, at least that is how I read it.

---

### Post by rvndrk3233 on 2010-10-17
This works with 10.04 live cd. Select the wifi button.

2) add new GSM connection. The guy lied to you. If it stars with *99, its GSM.

3) choose your card/att or whatever.
4) make sure you match your isp. att uses isp.cingular.

It works out of the box on Lucid and 9.10. TRUST ME. I have att. I love my 3G(outside of IB that is...)

No, you do not need login info, but someone already listed what you should be using IF you need it.

gnome-ppp and pppd need that info. The files look ok to me, its been awhile and dont have myusual config scipts with me. Was not expecting to need them.

Maverick is borked somehow. The driver kicks over, but doesn't connect.
I think there is a more serious problem with Ubuntu maverick. I tried to copy the same settings off the cd but with 777(all view and execute) permissions and got the same place.

The problem appears to be when pppd is called. if invoked directly with 'sudo pppd call gsm'
I get the following:

IP Header compression failed. Dropping NCR. Normal termination of line.
(or similar. add the debug option to /etc/ppp/peers/gsm to get where i got.)

 Yes, I know about root. Its the only way to get pppd to shut up and launch without chmod-ding the file to 777.

I've used kricket and nTelos and Verizon as well. Kricket and ntelos need the bit-flopper app to get them into modem mode. I forget what the verizon card was. I know one of these three didnt work with Ubuntu and the other two were one-shot bit-flippers.

The ATT card works. Double check you are not near brick or cement, they block off cell signal. If you can dump the parameters from the modem, they should be < -112db, which is the signal cutoff level. Below 100 is best. Worst come to worst, get an external antenna or a small usb extension cable.I've tried everything in IB and still got shafted due to TWO down towers. I get good signal everywhere else.

modem speed should read some crazy amount. You are paying for a card that can handle usb2.0 speeds, but rarely goes over usb1.0 speeds.(1.2mb/sec)

I use 760800 or similar. Valid speeds are 115200*(x). 8 is a good number.

Also:

set up dns at opendns.org or 4.2.2.2. seems the ISPs have issues with DNS queries as of late, COX being the worst.ATT, if the signal is weak will not give you this setting, but will give you an IP. If you set it by hand it works fine.(well...it USED to.)


hope this helps. This is a WONDERFUL card. I activated it on windows 7, so you might have to borrow a friends notebook to set it up, but I dont recall that ever being an issue. Now of course ATT is terrible at servie so go get the sierra FW update and dialer software if you use windows. No dropouts once connected. Connecting sometimes takes a few tries or pulling of the USB cable and waiting for the device to reset itself. Its annoying, but worth it.

---

### Post by jsgroby on 2010-10-20
Has anyone here been able to get this device working on 10.10?  I have everything set up as outlined in the above posts.  /dev/ttyUSB0 /dev/ttyUSB1 /dev/ttyUSB2 and /dev/ttyUSB3 all show up.

I can query the modem directly via minicom at /dev/ttyUSB0 but I get the same ERROR message as above when dialing.

Interesting note, the USB0-3 devices do NOT show up in ifconfig at all.

Any thoughts or ideas?

Thanks
jsg

---

### Post by alexfish on 2010-10-20
Hi

there have been resent post with these errors ( But don't know if this is relevant)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
from wvdial

**Remember if your Sim Card requires a PIN code to add in the conf file " Init1 = AT+CPIN= < your pin code > **

**Things to spot with wvdial **

**May indicate PIN code required **(use correct pin code)

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
OK
--> Modem initialized.
--> [B]Configuration does not specify a valid phone number.
[/B]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**May indicate Sim is locked , due to sending wrong code , puck code may be required**(best solution, place sim card in mobile phone , unblock sim , disable pin or puk code security)

[I]--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
**ERROR**
--> **Invalid dial command.**[/I]
-->** Disconnecting at Wed Oct 13 13:13:24 2010**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

One way to check is to use the command

[COLOR=Blue]AT+CPIN?[/COLOR]

if pin code required 

AT+CPIN=<YOURPINCODE>

without the < >

---

### Post by jsgroby on 2010-10-20
> **alexfish said:**
> Hi

there have been resent post with these errors ( But don't know if this is relevant)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
from wvdial

**Remember if your Sim Card requires a PIN code to add in the conf file " Init1 = AT+CPIN= < your pin code > **

**Things to spot with wvdial **

**May indicate PIN code required **(use correct pin code)

--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
Init3 = AT+CGDCONT=1,"IP","internet.wind","",0,0
OK
--> Modem initialized.
--> [B]Configuration does not specify a valid phone number.
[/B]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**May indicate Sim is locked , due to sending wrong code , puck code may be required**(best solution, place sim card in mobile phone , unblock sim , disable pin or puk code security)

[I]--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
**ERROR**
--> **Invalid dial command.**[/I]
-->** Disconnecting at Wed Oct 13 13:13:24 2010**
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

One way to check is to use the command

[COLOR=Blue]AT+CPIN?[/COLOR]

if pin code required 

AT+CPIN=<YOURPINCODE>

without the < >


I just tried the AT+CPIN? command and the output from my modem is:

+CPIN: READY

so if I understand your post correctly my ERROR in wvdial at this time is not related to a CPIN issue.

---

### Post by alexfish on 2010-10-20
+CPIN: READY

No pin required or correct pin code entered , but  worth checking 

have you tried what is suggested  here 

[https://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC81c2xvT1k2aw%3D%3D#GSM/UMTS_AT_Commands](https://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC81c2xvT1k2aw%3D%3D#GSM/UMTS_AT_Commands)

alexfish

---

### Post by jsgroby on 2010-10-20
> **alexfish said:**
> +CPIN: READY

No pin required or correct pin code entered , but  worth checking 

have you tried what is suggested  here 

[https://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC81c2xvT1k2aw%3D%3D#GSM/UMTS_AT_Commands]("https://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC81c2xvT1k2aw%3D%3D#GSM/UMTS_AT_Commands")

alexfish

Here are the results:

at+csq
+CSQ: 99,99

The ati5 command, no matter what port I enter it on, gives the following:

Manufacturer: Sierra Wireless, Inc.
Model: USB 305
Revision: I2_0_0_11ap CARMD-EN000104 2010/03/12 15:12:01
IMEI: XXXXXXXX
ERROR

IMEI blocked out for security reasons.


at!gstatus?
ERROR

at+cfun=1
+CME ERROR: operation not allowed


My device is not listed in the devices in that article but I went ahead and tried multiple ports for AT commands and they all give the results above.

---

### Post by jsgroby on 2010-10-20
I do want to add that this modem works fine when connected to an OS X or Windows machine using the software provided by Sierra.

---

### Post by alexfish on 2010-10-20
> **jsgroby said:**
> I do want to add that this modem works fine when connected to an OS X or Windows machine using the software provided by Sierra.

sounds like a good idea

Worth a try see what happens

---

### Post by jsgroby on 2010-10-21
> **alexfish said:**
> sounds like a good idea

Worth a try see what happens

The modem DOES work fine with both Windows 7 and OS X 10.6

So I know it is NOT a hardware problem now and it seems to be an Ubuntu/configuration  issue.

---

### Post by jsgroby on 2010-10-22
Have tried Sakis3G as well and that also will not connect.  I am beginning to think that something got broken with regards to broadband modems in 10.10.

Sakis3G fails at registering network.  The Error message is Modem unable to register a network.

---

### Post by alexfish on 2010-10-22
some of sierra AT command may differ from the standard (look at the ones like reset etc )

Perhaps contact Sierra

also look 

                                 Sierra wireless At commands reference , this will auto download
 

 [http://www.sierrawireless.com/resour...rence-v2.4.pdf](http://www.sierrawireless.com/resour...rence-v2.4.pdf)


beyond that have you tried this device in earlier versions of Ubuntu


also is the device wcdma or 3g


ask your service provider to confirm dial up details IE dial Number , APN if required,


user name and password


also check details of the Connection when in windows


Can post details of these commands from the terminal


Code:


[COLOR=Blue]ls -al /dev/serial/by-id/usb*

[COLOR=Black]Code:

[COLOR=Blue]usb-devices[/COLOR]

locate the lines which relate to the device and post only those lines


[/COLOR][/COLOR]alexfish
[COLOR=Blue][COLOR=Black]
added : Note from post

 [/COLOR][/COLOR]at!gstatus?
ERROR

Try Typing Capital letters : IE  

AT!GSTATUS?

---

### Post by jsgroby on 2010-10-25
> **alexfish said:**
> some of sierra AT command may differ from the standard (look at the ones like reset etc )

Perhaps contact Sierra

also look 

                                 Sierra wireless At commands reference , this will auto download
 

 [http://www.sierrawireless.com/resour...rence-v2.4.pdf](http://www.sierrawireless.com/resour...rence-v2.4.pdf)


beyond that have you tried this device in earlier versions of Ubuntu


also is the device wcdma or 3g


ask your service provider to confirm dial up details IE dial Number , APN if required,


user name and password


also check details of the Connection when in windows


Can post details of these commands from the terminal


Code:


[COLOR=Blue]ls -al /dev/serial/by-id/usb*

[COLOR=Black]Code:

[COLOR=Blue]usb-devices[/COLOR]

locate the lines which relate to the device and post only those lines


[/COLOR][/COLOR]alexfish
[COLOR=Blue][COLOR=Black]
added : Note from post

 [/COLOR][/COLOR]at!gstatus?
ERROR

Try Typing Capital letters : IE  

AT!GSTATUS?

This device has not been tried in earlier versions of Ubuntu, but as I mentioned above, it DOES work in Windows 7 and OS X (10.6).

Here are the results of the commands you requested:

jsgroby@arbiter:~$ ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2010-10-25 12:14 /dev/serial/by-id/usb-Sierra_Wireless_Inc._USB_305_352683031024505-if00-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-10-25 12:14  /dev/serial/by-id/usb-Sierra_Wireless_Inc._USB_305_352683031024505-if01-port0  -> ../../ttyUSB3
lrwxrwxrwx 1 root root 13 2010-10-25 12:14  /dev/serial/by-id/usb-Sierra_Wireless_Inc._USB_305_352683031024505-if03-port0  -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-10-25 12:14  /dev/serial/by-id/usb-Sierra_Wireless_Inc._USB_305_352683031024505-if04-port0  -> ../../ttyUSB0

and

jsgroby@arbiter:~$ usb-devices
T:  Bus=01 Lev=00 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=68a3 Rev=00.06
S:  Manufacturer=Sierra Wireless Inc.
S:  Product=USB 305
S:  SerialNumber=xxxxxxxxxxxxxxx
C:  #IFs=5 Cfg#=1 Atr=80 MxPwr=500mA
I:  If#=0 Alt=1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#=1 Alt=1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#=3 Alt=1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#=4 Alt=0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#=7 Alt=0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra_net

Does this shine any light on anything?  As I mentioned earlier, I never see any interfaces show up in ifconfig command.

Thanks
Jeff

p.s.  It is indeed a 3g device.  And doing AT!GSTATUS? gives same results as at!gstatus?  both return ERROR

---

### Post by jsgroby on 2010-11-03
This is resolved for me.  What I did was remove desktop Ubuntu from my ThinkPad X61 and installed Netbook version of 10.10.  Once installed, without doing anything additional, I plugged in the Sierra USB 305 and went to Network Connections.  Clicked on Mobile Broadband and set up a new AT&T connection using Data Connect as my plan.  Once I did this and set it to automatically connect it connected and I have been running fine since.

However, I would like to add that AT&T's DNS servers suck...big time...

Thanks for everyone's help in trying to troubleshoot this issue previously.

jsg

---

### Post by alexfish on 2010-11-07
hi

strange one , looking through the listing the configurations look odd

although may be just the way the drivers are configuring 

could you possibly post results of same commands from the Netbook version

for comparison

reason is why should it be working an a variation of 10.10 

thanks in advance

alexfish

---

### Post by alexfish on 2010-11-11
Looks like site has been updated

  Link page for Sierra wireless


  [Can I use a Sierra Wireless Modem on Linux Machines (direct IP modems)?]("http://sierrawireless.custhelp.com/app/answers/detail/a_id/641/session/L3NpZC9iV2xDKkxlaw%3D%3D")
 

 There are ppp files listed somewhere on the site ; downloading and reading through
 the file , there are details of how to connect with GSM and CDMA

---

### Post by triwave on 2010-11-16
> **jsgroby said:**
> This is resolved for me.  What I did was remove desktop Ubuntu from my ThinkPad X61 and installed Netbook version of 10.10.  Once installed, without doing anything additional, I plugged in the Sierra USB 305 and went to Network Connections.  Clicked on Mobile Broadband and set up a new AT&T connection using Data Connect as my plan.  Once I did this and set it to automatically connect it connected and I have been running fine since.


I just wanted to add that it works out of the box for me in Ubuntu 10.04 Netbook (on an HP Mini210).

**HOWEVER** it's didn't work right away. It was recognized, but I couldn't get it to connect. 

I tried a different USB port and it connected right away :confused:

Happy it works just fine in one of my USB ports ... not sure why that would be, but if your scratching your head and it's not working just try plugging it into another USB port - maybe you'll get lucky :) 

... posted using my 305 on ubuntu 10.04 ...

---

### Post by BarefootSoul83 on 2010-12-06
having a hard time with this Sierra Wireless card.

I have several people on Ubuntu that I give support to,

most of them got their internet through Altel, which just switched in our area to AT&T.

I cant get this thing to work for the life of me.... anyone have any breakthroughs yet?

---

### Post by BarefootSoul83 on 2010-12-09
ok, check this out...

I brought my neighbors PC over and after much tinkering, got the card to work...

took the pc to his house, with the data card still in the same usb port it was plugged into (and all the same settings)...and nothing...

THIS MAKES NO SENSE!

---

### Post by jhardin1 on 2010-12-23
> **BarefootSoul83 said:**
> ok, check this out...

I brought my neighbors PC over and after much tinkering, got the card to work...

took the pc to his house, with the data card still in the same usb port it was plugged into (and all the same settings)...and nothing...

THIS MAKES NO SENSE!

I've been having the same problem with a client's computer.  I read the earlier post about switching USB ports and it connected right away.  Very strange.

---

### Post by Beamsbox on 2011-01-20
Issue #1:
I was able to get this to work on 10.10 after I installed the sierra driver mentioned in an earlier post. Then I installed using this: "**sudo apt-get install ubuntu-restricted-extras", and I can't connect. I'm thinking the configuration changed somewhere, as I can see the network, it just tries to connect, then kicks me off. I'm not even sure how to uninstall the update to see if things would return to normal.**
 
**Issue #2:**
**I have another HD, same computer (EEEPC-1000HE) that I've installed eeebuntu 3.0.1 NBR on and this one I can't seem to get the card to work at all. The driver won't even compile, giving me the following:**
 
**Compiling sierra.c sierra_net.c**
**make: *** /lib/modules/2.6.28-11-generic/build: No such file or directory. Stop.**
**make: *** [default] Error 2**
 
**I'm not sure why the compiler wouldn't work, as it worked fine with the 10.10 distro.**
 
**I'm a total noob to linux, but would appreciate learning. I've meant to for some time now, just haven't...**
 
**Thanks prior for any help offered.**

---

### Post by IceDoE on 2011-02-04
None of the methods so far have helped, and I've tried using this on multiple machines. 

Looking at Seirra's site though, they're rather kernel specific and only have up to kernel 2.6.34, while Ubuntu 10.10 uses 2.6.35. Since this problem only started happening recently, maybe that's where the problem lies?

To note: everything worked perfect out of the box a few months ago, now it works on nothing. I've even gone through getting new SIM cards from AT&T and such. However, I've also heard a rumour that AT&T, at least for their DSL service in some places, has started blocking or forcing slowdown with Linux systems as of a couple months ago. I'm hoping that's not the problem here.

---

### Post by narzizz on 2011-02-17
Hi all,
This is my very first post and i hope i can help okay try to do this in it works for me on my Ubuntu 10.04 i386 and 10.10 amd64,

first we need usb-modeswitch package because usb305 lightning have feature called ZeroCD.

```
sudo apt-get install usb-modeswitch
```next we need known information about our sierra 305
```
lsusb
```find this line
```
Bus 001 Device 006: ID 1199:68a3 Sierra Wireless, Inc.
```based on that information we have vendor id and device id
next we add some udev.rules
```
sudo nano /etc/udev/rules.d/70-sierra-305
```then add this line
```
ATTRS{idVendor}=="1199", ATTRS{idProduct}=="68a3", RUN+="usb_modeswitch '%b/%k'"
```finally try connecting to the internet using network manager and it should be worked, because it works on mine

hope this help and sorry for my english bad:guitar:
also i try to write a blog [here ]("http://narzizz.wordpress.com/2011/02/17/solving-usb-sierra-wireless-error-on-ubuntu/")

---

