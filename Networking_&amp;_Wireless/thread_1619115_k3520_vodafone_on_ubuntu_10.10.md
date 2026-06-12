---
title: "k3520 vodafone on ubuntu 10.10"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by munshi on 2010-11-11
hello all,
i am a complete newbie when it comes to ubuntu. i have a toshiba laptop with ubuntu 10.10 64-bit installed with all software upadtes.

i own a k3520 usb stick from vodafone and i cannot seem to connect to the internet using the stick from ubuntu.

i have searched the software center and downloaded 2 of the results but when i try to install the driver i get an error message that i cannot seem to by pass. the stick is seen by the ubuntu but always fails to connect. any help will be much appreciated.

---

### Post by alexfish on 2010-11-11
Hi

which software have you installed

also need some info

open up the terminal from Applications, enter the following command

Code:

[COLOR=Blue]usb-devices[/COLOR]

locate the lines indicating the device and post [COLOR=Blue]only those lines[/COLOR]

the devices should also be listed in the DIR /usb_modeswitch.d 

post the results of

Code:

[COLOR=Blue]cat /etc/usb_modeswitch.d/19d2:2000[/COLOR]

alexfish

---

### Post by munshi on 2010-11-11
thanks for the prompt reply,
i have installed option globetrotter and vodafone datacard control tool and sms server tools for GSM modems.
i am failing to install vodafone 3G devices internet connection assistant.

the terminal shows the following

<code>T:  Bus=06 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1001 Rev=00.00
S:  Manufacturer=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
S:  Product=HUAWEI Mobile
S:  SerialNumber=ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ
C:  #Ifs= 4 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
</code>

on checking the DIR /usb_modeswitch.d
<code>bash: /usb_modeswitch.d: No such file or directory</code>

on typing cat /etc/usb_modeswitch.d/19d2:2000

<code>
#######################################################
# ZTE devices

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProductList="0001,0002,0015,0016,0017,0031,0037,0052,0055,0063,0064,0108,0128"

MessageContent="5553424312345678000000000000061e000000000000000000000000000000"
MessageContent2="5553424312345679000000000000061b000000020000000000000000000000"
MessageContent3="55534243123456702000000080000c85010101180101010101000000000000"

NeedResponse=1

CheckSuccess=20
</code>


thanks again for your prompt reply and your help

---

### Post by alexfish on 2010-11-11
Hi

looking at the info the device has configured, but does not list as the 3520

according to information in the device_reference data base the 3520 is ZTE

########################################################
# ZTE K3520-Z
#
# Contributor: Paul McDermott

;DefaultVendor=  0x19d2
;DefaultProduct= 0x2000

are you sure it says 3520 on the device

will the device configure with the network manager, if not need to see if modem-manager is installed

Code:

[COLOR=Blue]which modem-manager[/COLOR]

also post the results of

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*


[COLOR=Black]If the modem-manager is not installed then no path to MM will show , if so you will have to install

if modem-manager is installed , will have to look further

alexfish
[/COLOR][/COLOR]

---

### Post by munshi on 2010-11-12
thanks again for your help. and yes i am sure i have the huawei k3520 vodafone mobile connect usb stick. and the results for the commands you asked for are


which modem-manager

/usr/sbin/modem-manager


and the results for ls -al /dev/serial/by-id/usb*

lrwxrwxrwx 1 root root 13 2010-11-12 09:04 /dev/serial/by-id/usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-11-12 09:04 /dev/serial/by-id/usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-11-12 09:04 /dev/serial/by-id/usb-ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ_HUAWEI_Mobile_ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ-if02-port0 -> ../../ttyUSB2


just a small note the network manager does see a vodafone default 1 connection but is unable to connect.

---

### Post by alexfish on 2010-11-12
Hi

Are you sure the correct details have been entered in the Network Manager
PIN CODE or and PUK code
APN, username and password if required , phone number : check with service provider

is it a requirement the device to be first registered in windows,if so does it work in windows

if you are convinced all details are correct the will need further

Need to find if the device is communicating,and info from the device

START
Open up a first terminal , enter these codes

Codes:

[COLOR=Blue]sudo killall modem-manager[/COLOR]

[COLOR=Blue]tr -s "\n" < /dev/ttyUSB0[/COLOR]

this will monitor the replies of the device,[COLOR=Purple]leave this terminal open[/COLOR]

Open up a second terminal, enter the following codes, note any responses from the first terminal

Codes:
[COLOR=Blue]echo -e "AT\r" > /dev/ttyUSB0[/COLOR]

[COLOR=Blue]echo -e "ATZ\r" > /dev/ttyUSB0[/COLOR]

if there is no response IE "OK"then I would assume there could be a fault with the device, unplug the device and reconnect
close the first terminal and go to START and try again

to find if pin or puk code required

[COLOR=Blue]echo -e "AT+CPIN?\r" > /dev/ttyUSB0[/COLOR]

if 
+CPIN: READY ME......is not pending for any password
+CPIN: SIM PIN ...is Sim code required
+CPIN: SIM PUK PUK1 ..is Puk code required/the device is locked / place the sim in mobile phone to unlock with puck code

To enter Pin code

Code:
[COLOR=Blue]echo -e "AT+CPIN=<yourpincode>\r" > /dev/ttyUSB0[/COLOR]


example:
echo -e "AT+CPIN=1234\r" > /dev/ttyUSB0

to find if APN's are listed

Codes:
[COLOR=Blue]echo -e "ATZ\r" > /dev/ttyUSB0[/COLOR]

[COLOR=Blue]echo -e "AT+CGDCONT?\r" > /dev/ttyUSB0[/COLOR]

Find ISP or Operator
CODE:
[COLOR=Blue]echo -e "AT+COPS?\r" > /dev/ttyUSB0[/COLOR]

to find operators in area, after the code is entered it will take a while to search

Code:
[COLOR=Blue]echo -e "AT+COPS=?\r" > /dev/ttyUSB0[/COLOR]

Finally signal strength

[COLOR=Blue]echo -e "AT+CSQ\r" > /dev/ttyUSB0[/COLOR]

Post all the results  possible

---

### Post by munshi on 2010-11-12
thanks alexfish for all the help, but in windows i do not even enter a username, password, pin, puk etc,etc. and the device works perfectly well with both windows and mac devices.
entering these codes i found out the following

[COLOR="Blue"]echo -e "AT\r" > /dev/ttyUSB0

echo -e "ATZ\r" > /dev/ttyUSB0[/COLOR]

**ok** for both codes.

for
[COLOR="Blue"]
echo -e "AT+CPIN?\r" > /dev/ttyUSB0[/COLOR]

**+CPIN: READY**


to find if APN's are listed

Codes:[COLOR="Blue"]
echo -e "ATZ\r" > /dev/ttyUSB0

echo -e "AT+CGDCONT?\r" > /dev/ttyUSB0[/COLOR]

i got the following

[B]AT+CGDCONT?
+CGDCONT: 1,"IP","internet.vodafone.net","0.0.0.0",0,0
+CGDCONT: 2,"IP","internet.vodafone.net","0.0.0.0",0,1
+CGDCONT: 3,"IP","00000","0.0.0.0",0,1
+CGDCONT: 4,"IP","internet.vodafone.net","0.0.0.0",0,0

OK[/B]


on applying [COLOR="Blue"]echo -e "AT+COPS?\r" > /dev/ttyUSB0[/COLOR]

[B]AT+COPS?
+COPS: 0,2,"60202",2

OK[/B]


for networks available after [COLOR="Blue"]echo -e "AT+COPS=?\r" > /dev/ttyUSB0[/COLOR]

OK
[B]AT+COPS=?
+COPS: (1,"vodafone EG","voda EG","60202",0),(2,"vodafone EG","voda EG","60202",2),(3,"EGY MobiNiL","MobiNiL","60201",0),(3,"etisalat","etisalat","60203",0),(3,"etisalat","etisalat","60203",2),,(0,1,2,3,4),(0,1,2)

OK[/B]

for signal quality after posting [COLOR="Blue"]echo -e "AT+CSQ\r" > /dev/ttyUSB0[/COLOR]


[B]AT+CSQ
+CSQ: 10,99[/B]

OK


i hope this answers all the questions you had..and the same device on the same computer in the same area works fine with windows. with goood signal quality and strength

---

### Post by alexfish on 2010-11-12
Hi

the only thing which may not be  OK is the signal strength

"10" is boarder line between working and not working (may get errors) , 15 is good , connect the device on usb-cable and try move
to get better signal quality

not sure why network manager re modem-manager not connecting


try these from the terminals 

open the first terminal

Codes:

Codes:

[COLOR=Blue]sudo killall modem-manager[/COLOR]

[COLOR=Blue]tr -s "\n" < /dev/ttyUSB0[/COLOR]

Open up a second terminal, enter the following codes, note any responses from the first terminal

Codes:

[COLOR=Blue]echo -e "ATZ\r" > /dev/ttyUSB0
[/COLOR]
[COLOR=Blue]echo -e "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0\r" > /dev/ttyUSB0[/COLOR]

[COLOR=Blue]echo -e "AT+CREG?\r" > /dev/ttyUSB0[/COLOR]

wait a few seconds, if the device has an led see if it changes

then 

now is to try  <cid> dial commands 

listed according to the locations on the device

+CGDCONT: 1,"IP","internet.vodafone.net","0.0.0.0",0,0 <== [COLOR=Blue]ATDT*99***1#[/COLOR]
+CGDCONT: 2,"IP","internet.vodafone.net","0.0.0.0",0,1 <==[COLOR=Blue] ATDT*99***2#[/COLOR]
+CGDCONT: 3,"IP","00000","0.0.0.0",0,1
+CGDCONT: 4,"IP","internet.vodafone.net","0.0.0.0",0,0 <==[COLOR=Blue] ATDT*99***4#[/COLOR]

the dial code for the first one

Code:

[COLOR=Blue]echo -e "ATDT*99***1#\r" > /dev/ttyUSB0[/COLOR]

repeat the command a few times until hopefully a CONNECT message , you may have to try 

echo -e "ATDT*99***2#\r" > /dev/ttyUSB0

echo -e "ATDT*99***4#\r" > /dev/ttyUSB0

if you get the CONNECT message or CONNECT <number>

enter this code

Code:

[COLOR=Blue]sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns ktune[/COLOR]

enter your sudo (system )password

see what happens

---

### Post by munshi on 2010-11-12
i moved to a different room in my house where reception is better. and got the following results


in the first terminal after the first code

[B]AT+GCAP
+GCAP: +CGSM,+DS,+ES

OK
AT+GCAP
+GCAP: +CGSM,+DS,+ES

OK
AT+GCAP
+GCAP: +CGSM,+DS,+ES

OK[/B]

in the second terminal after coding the following

[COLOR="Blue"]echo -e "ATZ\r" > /dev/ttyUSB0[/COLOR]

**OK**

[COLOR="Blue"]echo -e "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0\r" > /dev/ttyUSB0


ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0[/COLOR][/COLOR]

**OK**


[COLOR="Blue"]echo -e "AT+CREG?\r" > /dev/ttyUSB0[/COLOR]

[B]AT+CREG?
+CREG: 0,1

OK[/B]


ON APPLYING [COLOR="Blue"]echo -e "ATDT*99***1#\r" > /dev/ttyUSB0[/COLOR]

[B]OK
ATDT*99***1#
CONNECT[/B]


AND I GET THAT FROM THE FIRST ONE

 [COLOR="Blue"]sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns ktune[/COLOR]

[B]Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
PAP authentication succeeded
Modem hangup
Connection terminated.[/B]

I hope that makes some sense. and a solution to be applied.

---

### Post by alexfish on 2010-11-12
Hi

can you try again with

sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns ktune lcp-echo-interval 0 lcp-echo-failure 0 ipcp-max-failure 30

or

sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns ktune lcp-echo-interval 0 lcp-echo-failure 0 noip novj

also can post the values in ppp options

Code:
egrep -v '#|^ *$' /etc/ppp/options

---

### Post by munshi on 2010-11-12
on commanding [COLOR="Blue"]sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns ktune lcp-echo-interval 0 lcp-echo-failure 0 ipcp-max-failure 30
[/COLOR]

[B]Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup[/B]

on commanding

[COLOR="Blue"]sudo pppd ttyUSB0 115200 nodetach defaultroute noipdefault noauth lock usepeerdns ktune lcp-echo-interval 0 lcp-echo-failure 0 noip novj
[/COLOR]

[B]Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0

LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
[/B]
on commanding [COLOR="Blue"]egrep -v '#|^ *$' /etc/ppp/options[/COLOR]

[B]LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
amr@ubuntu:~$
amr@ubuntu:~$ egrep -v '#|^ *$' /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx


[/B]

---

### Post by alexfish on 2010-11-12
hi

the field has narrowed a bit , but can you have a look here

[COLOR=#000000][LCP: timeout sending Config-Requests]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml#lcp_timeout")

look at 

[/COLOR][COLOR=#000000]your system may have *iptables* or *ipchains* rules that prevent GRE transmission

but read the article "LCP:timeout , from top 

I could also suggest trying to disable all other eth and wireless connections , try again, then look at the article 

alexfish
[/COLOR]

---

### Post by munshi on 2010-11-12
i do not mean to be stupid, but i am totally lost with your last post. and reading the article left me even more puzzled. i did not know where is the tunnel, and did not understand what steps to take next.

again sorry for being such a noob, and i hope you can make it a bit more simpler to my simple mind.

---

### Post by alexfish on 2010-11-12
Hi munchi 

In most cases vodafone dongles normaly configure and connect with ubuntu
and many more Linux distro without problems.

as Ubuntu 10.10 is a new release it may be a while till
Oops (bugs)to some , get ironed out

Where I sit , the information available  is from the what the device returns from
the commands sent to the device, This is one of the advantages of Linux and its
accessibility, something which has been devoid of in other operating systems, that
applies to a lot more than a 3g dongles

don't feel like a noob or feel stupid, everyone using Linux feels that way
at sometime or another. this is the way I feel now , because I don't
have a fix to the problem,other than there a problem with the servers
or a problem with the 64bit set up, the later I suspect

If you are new to Ubuntu , hopefully for a out of box experience try 32 bit version,
see what you think

but make it a priority to try the 3g dongle with the live cd for both 64 bit and 32 bit

Added link: worth reading + the links (also worth reading links to usb_modeswitch and the history behind these devices , still an on going state for novices and the experienced)

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

regards

alexfish

---

### Post by munshi on 2010-11-13
thanks alexfish for these comforting words. i decided to try to boot up from the live CD(32-bit) and it worked perfectly. so i decided to try the live 64-bit CD and it worked perfectly too. so i decided to remove and reinstall ubuntu. and it is working perfectly with the USB stick. maybe there was something wrong with the way i installed ubuntu last time or something. but now everything is running smoothly.

---

### Post by alexfish on 2010-11-13
Hi

good news

could you mark your thread as solved, use thread tools at top of page

thanks in advance , enjoy

alexfish

Added , for future reference if you need to debug the pppd (ppp daemon) then add the debug to the line like so

 [COLOR=Blue]sudo pppd ttyUSB0 115200 debug nodetach defaultroute  noipdefault noauth lock usepeerdns ktune lcp-echo-interval 0  lcp-echo-failure 0 ipcp-max-failure 30[/COLOR]

but it is not advisable to post this info on forums, as it can reveal passwords etc etc

---

