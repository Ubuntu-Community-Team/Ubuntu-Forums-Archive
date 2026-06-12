---
title: "How to make Smart Bro ZTE MF627 work on Ubuntu 9.10"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by lod2 on 2010-03-02
**Smartbro on Ubuntu 9.10**

Device Needed:
-Smartbro USB modem model: ZTE MF627

Instructions:

1. Plug in the usb device. Once it appears on your desktop, right click the smartbro icon and select _eject_
2. The light will go out. Wait for a while until it goes back again. At this point, the usb is now switched from card reader to a modem.
3. Right click network manager and select _Edit Connections_
4. Select the _Mobile Broadband_ tab and click the _Add_ button
5. A window would appear and by default, the _ZTE Incorporated ..._ is selected. Click_ Forward_
6. Select _Philippines_ as the provider's country and click _Forward_. A list of providers will be displayed. Choose _Smart_ and click [U]Forward
[/U]7. On the billing plan, click the drop down menu (the one which says _Default_) and select _My Plan is Not Listed_. A blank text box will appear.
    Type _smartbro_ as your access point name and click _Forward_ then click _Apply_

A new window will appear. There are many textboxes here but you only need to modify a few. 

8. Select the _PPP Settings_ Tab and click the _Configure Methods_ button
9. Uncheck all methods except PAP. Click _Ok_. Optionally you may also click _Connect Automatically_ then finally click _Apply_.
10. After clicking apply, your modem will attempt to connect. You will notice that the green light from your modem will start to blink and a 
   message saying _Established Connection_ or something similar will appear. Open your browser and test if you are now able to browse the web. If 
   not, give wait for about 30 sec and retry opening your browser again. If it still fails, remove your usb and repeat steps 1 & 2. Afterward, Left Click the Network Manger then click the _smartbro_ (or something similar) to re establish connection.

NOTES: On certain occasions, I have established conections but when I try to browse, the browser seems to be offline despite the _connection established_ message from the network manager as well as the modem's blinking light indicating that I am connected. When this happens, what I do is I disconnect the connection (without unplugging the modem), then reconnect. After a few reconnection (usually 2 or 3 times), I would be able to browse by then. As for the credit charges imposed by Smart Philippines, I have observed that no credit was taken during those times that I have established connection but wasn't able to browse :)

**More Tips:**

-When finished surfing, _left click_  the _network manager icon_ and click _disconnect_.
-When reconnecting, repeat step 1 & 2. And if you have checked _Connect Automatically_ from step 8, your modem will automatically connect the   moment it switches into modem mode.

---

### Post by includeRamon on 2010-04-08
thank you so much , this is a very big help for me, i have been trying to connect my smartbro ZTE MF627, thank you so much, if may ask how dd you figure it out this solution? i used a smart bro prepaid before, it worked fine by just setting apn to SMARTBRO..

---

### Post by carlexpc on 2010-04-12
Do you have any idea if the Mobile Internet providers in the Philippines change their respective APNs from time to time?

---

### Post by kstella on 2010-04-24
I'm using wicd instead of network-manager. Is there any way to get Smart Bro to work with wicd, or do I need to switch back?

---

### Post by alexfish on 2010-04-24
Hi lod2  
 

 from your post:
 

 NOTES: On certain occasions, I have established conections but when I try to browse, the browser seems to be offline despite the _connection established_ message from the network manager as well as the modem's blinking light indicating that I am connected. When this happens, what I do is I disconnect the connection (without unplugging the modem), then reconnect. After a few reconnection (usually 2 or 3 times), I would be able to browse by then. As for the credit charges imposed by Smart Philippines, I have observed that no credit was taken during those times that I have established connection but wasn't able to browse  
 

 

 

Here I have change the IPCP configure-NAKs returned before starting , remove the # and set the number to 30 ( or any thing above the default value till there is a constant connection )

Code:

sudo gedit /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
ipcp-max-failure 30


 tip start at 30 and work down
 
 use  NM IPv4 settings to Automatic (PPP) instead of Setting the NM to IPv4 settings to Automatic (PPP) address only and having to enter the numerical addresses in the DNS servers text box.

Also

Code:
sudo gedit /etc/ppp/options
Add this line and save:

replacedefaultroute

if this is done then replace the # in front of the

replace the # in front of the " ipcp-max-failure 30 " do not use both methods and see which works best   
 

 regards  
 

 alexfish

---

### Post by prvteprts on 2010-05-19
When I try to connect the first time, the light will turn blue, but then it will disconnect after a few seconds (GSM Network Disconnected).

I have tried turning off the wifi hardware and restarting as mentioned in this article: [http://knightlust.blogspot.com/2009/06/smartbro-zte-mf627-on-ubuntu-jaunty.html](http://knightlust.blogspot.com/2009/06/smartbro-zte-mf627-on-ubuntu-jaunty.html) , but the same thing happens.

Any ideas on this?

---

### Post by alexfish on 2010-05-20
Hi

can you try this from the terminal and find and change  lcp-echo values  to 0

Code:

sudo gedit /etc/ppp/options

lcp-echo-failure 0
lcp-echo-interval 0

save and exit

does this help

---

### Post by prvteprts on 2010-05-31
> **prvteprts said:**
> When I try to connect the first time, the light will turn blue, but then it will disconnect after a few seconds (GSM Network Disconnected).

I have tried turning off the wifi hardware and restarting as mentioned in this article: [http://knightlust.blogspot.com/2009/06/smartbro-zte-mf627-on-ubuntu-jaunty.html](http://knightlust.blogspot.com/2009/06/smartbro-zte-mf627-on-ubuntu-jaunty.html) , but the same thing happens.

Any ideas on this?

I figured out the problem... it turns out the SIM card I used did not have enough credit lol. I loaded it up, and it connected fine. Now, even though it's out of credit, it still connects but the browser always redirects to m.smart.com.ph .

---

### Post by lod2 on 2010-06-10
if you are using 10.04, check the thread below

[http://ubuntuforums.org/showthread.php?t=1506375&highlight=zte+mf627](http://ubuntuforums.org/showthread.php?t=1506375&highlight=zte+mf627)

---

### Post by Arnold Martin on 2010-09-01
> **lod2 said:**
> if you are using 10.04, check the thread below

[http://ubuntuforums.org/showthread.php?t=1506375&highlight=zte+mf627](http://ubuntuforums.org/showthread.php?t=1506375&highlight=zte+mf627)

I would bet and curse, but this works for me, and I am in an hsdpa network.

My wvdial.conf IS THIS, just change your login name and password, and maybe the phone no. if you are not using the SmartBro plus the modem no., ex /dev/ttyUSB0.


 [Dialer Defaults]
 Phone = *99#
 Username = your login name
 Password = your login password
 Stupid Mode = 1
 Dial Command = ATDT


 [Dialer hsdpa]
 Modem = /dev/ttyUSB2
 Baud = 115200
 Init2 = ATZ
 Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
 ISDN = 0
 Modem Type = Analog Modem


 Then when you dial, run as a superuser the wvdial hsdpa. But first of  all these, do install wvdial and usb-modeswitch using the same modem,  note that you will be in GPRS network but wvdial and usb-modeswitch is  just a tiny program that installing it will not take that long. Now take  the modem into a windows system and switch it back to "3G only" in the  Network settings so the light will turn from blue to green, then plug it  to your linux and run the command, wvdial hsdpa. Wait a little and then  rock on!:popcorn:

---

### Post by David_Melb on 2010-09-01
MF633BP+ modem and Telstra 3G
I would like to thank you for your assistance.  I was un-mounting the driving instead of ejecting and once I had done this  the usb changed from 0x19d2 0x2000 to 0x19d2 0x0031 (use LSUSB to verify the switch.)
Used Terminal Window to verify status of USB with the command >>lusb

I then created the new connection under edit for and noticed that it immediately displayed the ZTE modem.
Selected Country - Australia
Selected Telstra
Then 3G

added User Name  User@bigpond
added password XXXXX
Changed APN to telstra.bigpond

Selected connect automatically and all okay.

Modem went from Blue on to flashing blue.

NB Modem was registered at a telstra shop.  Unable to register it with ubuntu.

Thanks david_melb:D

---

### Post by tech-hero on 2010-12-06
Hi guys, im new to ubuntu. i've managed to make my Sun Wireless Broadband MF627 work for my 10.04. though sun's fair usage policy sucks, it's still a lot much better than nothing. 
 
I have a question, do you guys have an idea how to lock my MF627's data connection to UMTS? i really find it very annoying when my data connection switches from UMTS to GPRS though i really think i have UMTS signal on my room. When i'm using my Windows 7, i can set the settings to use "UMTS only" through the built in software in MF627 (the connection speed is noticeably fast and the LED indicator is BLUE). any idea how can do the same with UBUNTU using the built in network manager?

---

### Post by alexfish on 2010-12-07
Hi

can have a look at post #8

[How To : Mobile Broadband Connections [ Ubuntu  10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

alexfish

---

### Post by tech-hero on 2010-12-07
Hi. were you able to test that one?
 
i read it but i don't fully understand. been using ubuntu for just 3wks. i still have a lot to learn.
 
regarding the INIT command,[FONT=Courier New]AT+ZSNT=2,0,0 3G Only , where do i have to input that? wvdialconf? i don't know. how can i make it permanent?[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]i've had an experiment yesterday. i've used network manager to connect to my SUN wireless broadband and got a green signal(GPRS). after i got connected, i ran gnome-ppp detect my modem, set the speed to 46something and change the setup for INIT and typed in AT+ZSNT=2,0,0. to my surprise, my green signal changed into blue which made me formulate a theory that i have to activate that initialization command to get a 3g signal lock connection.[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]i wonder where i could put that initialization command so that i won't be doing this all the time. are there any setup or config file that can be used for initializing modem connections in network manager? i love how connection manager automatically detect things, but i think, it lacks an option to configure your connection settings :)[/FONT]
[FONT=Courier New][/FONT] 
[FONT=Courier New]thanks for the answer bro. until i find a way to make this thing permanent, i think i will just use my newly discovered way to lock my wireless connection in 3g. :)[/FONT]

---

### Post by alexfish on 2010-12-08
Hi

you could make a simple script 

if you read through the thread , even at first post on how to send

AT commands from the terminal

if making a script file use the same commands

, you could then place the script file on the desk top

how to make a script file

[http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)

**you could also use chat : **edit the tty* to suit the device

Example to get the signal strength

Code:

[COLOR=Blue]chat -s -v '' AT OK AT+CSQ OK > /dev/ttyUSB1 <  /dev/ttyUSB1[/COLOR]

Response:

alexfish@alexfish-desktop:~$ chat -s -v '' AT OK AT+CSQ OK >  /dev/ttyUSB1 < /dev/ttyUSB1
send (AT^M)
expect (OK)
^M
NO CARRIER^M
^M
+CMTI: "SM",11^M
^M
OK
 -- got it

send (AT+CSQ^M)
expect (OK)
^M
^M
+CMTI: "SM",12^M
^M
+CSQ: 14,99^M
^M
OK
 -- got it

in your case you could try


[COLOR=Blue]chat -s -v ''AT OK AT+ZSNT=2,0,0 OK > /dev/ttyUSB1  < /dev/ttyUSB1[/COLOR]

Don't for get to Edit the tty port to suit the modem {but in most case  for ZTE devices  port [COLOR=Blue]ttyUSB1 , will be OK [COLOR=Black], If no other devices are connected} even if connected to  the web[/COLOR][/COLOR]

Note: the only exception would Ubuntu 10.10 , if using Network Manager , the modem-manager will be holding onto the control port , 
so if you want to experiment , don't use network manager

regards

alexfish

---

### Post by tech-hero on 2010-12-09
i've spent my whole evening trying to work on this one. anyway,
 
what do i expect sir after i type
 
[COLOR=#0000ff]chat -s -v ''AT OK AT+ZSNT=2,0,0 OK > /dev/ttyUSB1 < /dev/ttyUSB1[/COLOR]
[COLOR=#0000ff][/COLOR] 

it just prints out AT then something like "alarm" and "failed" i really don't know how to make this work. i knew that the option is to lock the connection to UMTS only.
 
 
anyway, i also figured out that the default NETWORK MANAGER only works if modem is detected in /dev/ttyUSB1 ... if it is not there, if it is ttyUSB3, it doesn't connect but it got detected. how could i ever fix this? in order to bring it back to ttyUSB1, i have to restart my system.
 
any idea? i find this thing so challenging. let's keep it on. thanks for your response sir.

---

### Post by tech-hero on 2010-12-19
i finally made it work. i used modem-cmd to chat with my modem. so now i could set it easily even it is used by network manager ... so happy about this!

---

