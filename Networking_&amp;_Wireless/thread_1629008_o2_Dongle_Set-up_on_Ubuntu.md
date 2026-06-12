---
title: "o2 Dongle Set-up on Ubuntu"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by JVV on 2010-11-23
Hello, 

I'm a very recent convert to Ubuntu after my windows computer crashed.  Yesterday I bought a T-Mobile dongle (UK) but cannot get it to work. 

HUAWEI Model: E1752Cu

Thanks in advance!

Jay, London UK

---

### Post by alexfish on 2010-11-23
Hi

you say it does not work

does the network manager recognise the device / but can't connect

recognised but can't connect:
depending on pay plan if agreement 
has the account been set up
or if top up card / ensure the card is topped up

if the device is not recognised (do you have usb_modeswitch installed)
some early versions of usb_modeswitch can reset the device (not recognised)
more so if Virtual Software is installed, Try solve by disabling usb_modeswitch
{** just added link at foot of post Look there First**}

still not connecting (depending on version of ubuntu is it 32 or 64 bit)

can have a look here , read in detail esp post #1

[How To : Mobile Broadband Connections [ Ubuntu  10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

also have a look at Sakis3g

Can also post the results of , from the terminal

Code:

[COLOR=Blue]lsusb[/COLOR]


alexfish

Added link: can also have a look here

Solved E1752:
[http://ubuntuforums.org/showthread.php?t=1553529](http://ubuntuforums.org/showthread.php?t=1553529)

---

### Post by JVV on 2010-11-23
Hi alexfish, 

Thank you for your reply. 

I'm using Ubuntu 10.04 LTS. I have just installed usb-modeswitch from the package manager and then tried to go through Network Connections and Mobile Broadband set-up. No luck unfortunately, I'm working through the post links you sent me. 

I've posted the terminal results from lsusb below:

dell@dell-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12d1:140c Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
dell@dell-laptop:~$

---

### Post by alexfish on 2010-11-23
Hi

according to the info the device has switched

unswitchd12d1:1446 
switched [COLOR=Blue]12d1:140c
[/COLOR]
will the device configure in network manager

if not post the results of

Code:
[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]


Code:
[COLOR=Blue]usb-devices[/COLOR]

locate the lines indicating the modem and post only those lines

if there are lines indicating [COLOR=Blue]Driver = none[/COLOR]
try

Code:
[COLOR=Blue]sudo modprobe option

[COLOR=Black]then repeat the command "usb-devices"[/COLOR]
[/COLOR]
If got lines indicating Driver = option

and won't configure with NM then will have to look further

alexfish

---

### Post by JVV on 2010-11-24
Hi alexfish, 

After installing the usb-modeswitch, I went through System>>Network Connection>>Mobile Broadband and set up the modem. It appears in the drop-down "V" at the top of the screen and when I click on the Mobile Broadband it connects and I get a steady blue light on the modem. Unfortunately, when I use my browser (Firefox) it says "work offline" even though the connect is live. 

I copied from the Terminal the codes you requested:
dell@dell-laptop:~$ ls -al /dev/serial/by-id/usb*

lrwxrwxrwx 1 root root 13 2010-11-24 23:29 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-11-24 23:29 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-11-24 23:29 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-11-24 23:29 /dev/serial/by-id/usb-HUAWEI_Technology_HUAWEI_Mobile-if03-port0 -> ../../ttyUSB3


and
dell@dell-laptop:~$ usb-devices

.....
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
.........

I could not see Driver=none within the terminal window

---

### Post by alexfish on 2010-11-24
Hi 
Every thing Device wise seems OK

as regards the connection
It is unusual for fire fox to work in Offline mode with the Network  Manager
check the details in the Network Manager 

see if it shows the Primary and Secondary servers , if not then
device is  not connecting to the network / sometimes you will get a time out before
the servers respond , or if the network is busy

post the results of last two line of each command

Codes:
[COLOR=Blue]grep IP /var/log/messages[/COLOR]
[COLOR=Blue]grep DNS /var/log/messages[/COLOR]

Or to find DNS servers NS1 and NS2 from the resolv.conf

Code:
[COLOR=Blue]cat /etc/resolv.conf[/COLOR]

if nothing shows for the [COLOR=Blue]IP[/COLOR] then their is no connection

if you have[COLOR=Blue] IP[/COLOR] address but no [COLOR=Blue]DNS[/COLOR]  then there is no connection to the Servers NS1 or NS2

to try and fix this

Code:
[COLOR=Blue]sudo gedit /etc/ppp/options[/COLOR]

Then look for the lines :

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
# ipcp-max-failure <n>

edit to look like :

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
[COLOR=Blue]ipcp-max-failure 30[/COLOR]

and add this line

[COLOR=Blue]replacedefaultroute[/COLOR]

if problems persist , can also change [COLOR=Blue]#-chap[/COLOR] look for the line and change:  and also add [COLOR=Blue]ktune[/COLOR] , ktune sets IP forwarding

[COLOR=Blue]-chap[/COLOR]

add line

[COLOR=Blue]ktune[/COLOR]

save the file and exit

If you have DNS server NS1 and NS2 and Firefox is still in Offline mode, fix by selecting from the menu
then uncheck the Work Offline box

for a permanent fix

After opening Firefox, try opening page "about:config"... Filter for "toolkit.networkmanager.disable"
Change the line to ....." toolkit.networkmanager.disable;true "

See screenshots in Attachments

alexfish

---

### Post by JVV on 2010-11-28
Hi Alexfish, 

Thank you for the detailed reply. I have followed all of your suggestions, including changing the code within gedit, and modifying Firefox but to no avail!

Firefox will not connect and Google Chrome gives me the following error messages:

[COLOR=#000000][FONT=Times New Roman][FONT=Helvetica]Error 102 (net::ERR_CONNECTION_REFUSED): Unknown error.

[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Helvetica]Error 105 (net::ERR_NAME_NOT_RESOLVED): The server could not be found.[/FONT][/FONT][/COLOR] 


The device definitely connects, i get a message from the Network manager saying Broadband Mobile connection established. 

I have put the terminal results you asked for below:

dell@dell-laptop:~$ grep IP /var/log/messages
.........
Nov 28 21:50:55 dell-laptop pppd[2925]: local  IP address 10.54.159.14
Nov 28 21:50:55 dell-laptop pppd[2925]: remote IP address 10.64.64.64


dell@dell-laptop:~$ grep DNS /var/log/messages
......
Nov 28 21:50:55 dell-laptop pppd[2925]: primary   DNS address 82.132.254.2
Nov 28 21:50:55 dell-laptop pppd[2925]: secondary DNS address 82.132.254.3


dell@dell-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 82.132.254.2
nameserver 82.132.254.3

---

### Post by alexfish on 2010-11-29
Hi

82.132.254.2
82.132.254.3

82.132.254.2
IP:
82.132.254.2
server location:
United Kingdom
ISP:
Telefonica O2 UK

can you double check the info in Network Manager(ref T-mobile} APN
what does it show and also the dialup number
or have you changed IPv4 settings

is your location UK if not can give location

---

### Post by JVV on 2010-11-29
sorry I made a mistake with my subject heading for this thread. I bought an O2 dongle not T-mobile one, however when I spoke with O2 they said all dongles (T-Mobile, Vod etc) were made by the same company, so a linux fix would be the same

---

### Post by alexfish on 2010-11-29
something wrong somewhere with the settings

O2 UK setting show as

Plan "Contract"
APN ="mobile.o2.co.uk"
username = "o2web"
password = "password"
DNS = 193.113.200.200
DNS = 193.113.200.201
    
Plan "Contract (faster)"
APN ="mobile.o2.co.uk">
username = "faster"
password = "password"
DNS193.113.200.200
DNS193.113.200.201

Plan Prepaid
APN = "payandgo.o2.co.uk"
username = "payandgo"
password = "payandgo"
 
Check the settings or
try changing the IPv4 setting to Automatic (PPP) address only

and enter 
[COLOR=Blue]193.113.200.200 , 193.113.200.201[/COLOR]
in the DNS servers: entry box

No DNS listed "Prepaid" can ask o2 or can try same as Contract if changing IPv4 settings

---

### Post by Tankgirl on 2010-12-01
I hope you don't mind a noob jumping in on this thread, especially as I'm actually a 'whispers (fedora) user'.

The reason I've joined is to ask for some help from you knowledgeable peeps.

The hubby and I have just moved into our new house, no phone line and therefor internet for a couple of weeks, so we thought we'd get mobile broadband.
We've gone with o2 and seem to be having the same problems as JVV. We've gone through the info on this thread and on  [B]How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]
[/B] without any luck.

We plug the dongle in, the modem is detected (steady blue light etc), network manager sets it up. We can do a DNS lookup that works fine, but if we ping say [www.bbc.co.uk](www.bbc.co.uk) we get server fail notification. A general ping shows 100% packet loss. If we use openDNS the DNS lookup doesn't work at all, so we are using o2.
 
Basically everything shows as it should work, but we just can't get it to connect to web servers.

---

### Post by alexfish on 2010-12-01
> **Tankgirl said:**
> I hope you don't mind a noob jumping in on this thread, especially as I'm actually a 'whispers (fedora) user'.

The reason I've joined is to ask for some help from you knowledgeable peeps.

The hubby and I have just moved into our new house, no phone line and therefor internet for a couple of weeks, so we thought we'd get mobile broadband.
We've gone with o2 and seem to be having the same problems as JVV. We've gone through the info on this thread and on  [B]How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]
[/B] without any luck.

We plug the dongle in, the modem is detected (steady blue light etc), network manager sets it up. We can do a DNS lookup that works fine, but if we ping say [www.bbc.co.uk]("http://www.bbc.co.uk") we get server fail notification. A general ping shows 100% packet loss. If we use openDNS the DNS lookup doesn't work at all, so we are using o2.
 
Basically everything shows as it should work, but we just can't get it to connect to web servers.

Been thinking 

from the previous posts the device was connecting to unlisted servers , as far as
the details in serviceproviders database show.

also was on post sometime back , where the device had to be registered in windows
The grey matter did not click at first.

So the question is. Have the devices been registered using windows and the supplied software. 

the user name and passwords may not be correct . I did a google for these { but may be in the SMS text messages of the device}

and when done the device connected / showing the listed DNS servers

Can you also post the Addresses of the DNS servers

alexfish

Added: think this is one of the settings

O2 has one special setting for mobile broadband:

APN: m-bb.o2.co.uk
user:  o2bb
password: password

part of an old thread   #[**5**]("http://ubuntuforums.org/showpost.php?p=8509066&postcount=5")
think the details have something to do with hot spots and connecting like a wifi if you have o2 broadband (phone line connection)

---

### Post by JVV on 2010-12-02
Hi alexfish & Tankgirl, 

After nearly a week of trying to get this dongle to work it was surprisingly easy. 

1. Follow alexfish's instructions including modifying Firefox

2. Go to your local O2 store, ask them to put it into their laptop, for some reason it works there and then put into your laptop and bingo it works!

I have no idea why this worked. The O2 guy assured me all he did was plug it into his windows O2 laptop and he didn't register the sim/dongle etc.

alexfish thanks for all your help.

---

### Post by pythonsyntax on 2010-12-04
I was thinking about getting this how ast is this is it like same as the other one slow?

---

### Post by Tankgirl on 2010-12-06
Hi, sorry for the delay in reply. Thanks for your help and advice.

We tried alexfish's advice, still couldn't get it to work, but gave us an idea of what the problem might be. 
So we gave customer support a call to ask if they could register the dongle over the phone as we do not have access to a secure windoze OS.
While he said O2 don't support linux (I didn't expect them to-but he still offered a couple of ideas we could try), he told us we needed to register on the O2 mobile broadband website before we can use it. This explains why we could only access the O2 DNS.


What we did-
- Open browser and go to [https://mobilebroadbandandaccess.o2.co.uk](https://mobilebroadbandandaccess.o2.co.uk) (this page should be listed in the setup/help booklet about topup etc).
- fill out phone number and other information requested where asked.
- Disconnect and reconnect dongle

And it worked. Feel a bit silly for not seeing the logic behind only being able to use O2 DNS and accessing their site to register though.

As for speed, we get a little better than dial-up! not great, but it's only a stop-gap for us until we get our broadband connected.
We also tried Orange, whose coverage wasn't marginal, but not full speed (so they said), we got it working 1st time, but got at best 1/10th of dial-up speed and it kept on dropping out completely!

---

