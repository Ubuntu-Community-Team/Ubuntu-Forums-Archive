---
title: "3g broadband sharing with 9.10 desktop &amp; networkmanager"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by bradyh on 2010-01-18
Hi so I just managed to share a 3g verizon um175 card's connection over the ethernet very easily.

the hardware is a pretty old pentium 4 with 256mb RAM and only usb 1.1 but it works ok
software is a standard install of ubuntu 9.10 (karmic koala) plus firestarter

in the console
"sudo apt-get install firestarter"

This guide is a bit rough an assumes a basic understanding of ip addresses...gateways dns servers etc.

this solution does not provide dhcp ....but hey I don't want that anyway (5 gigs a month isn't that much:) 

alright I'm assuming your 3g wireless card already works on windows or os x....if not install their software and activate your card...verify it works etc...

now plug the card into the ubuntu box and set it up with networkmanager right click the connection and select new cdma modem (or similar) and input your details as neccesary

once connected unplug any ethernet...turn off any wifi and verify you have internet access.

then right click the network manager icon and select "Edit Connections"  or go to "system" "preferences" "network connections"

select "wired" pick eth0 click enter 
then click ipv4 settings tab

change from dhcp to manual and enter the following details

address = 192.168.13.1
netmask = 255.255.255.0
leave gateway blank

alright now start firestarter

go to "applications" "internet" "firestarter"

use the wizard and select ppp0 as your internet device

select connection sharing and
then use eth0 as your sharing device

dhcp will be greyed out....thats ok

plug your ethernet card back into your router or switch

start firestarter firewall...

now configure another computer to use this gateway..

I used an osx machine running leopard but anything should work with the right config.

set your ip address to be 192.168.13.101
netmask 255.255.255.0
router (or default gateway) 192.168.13.1

IMPORTANT you need to enter DNS servers...I use openDNS I recommend registering for their free service (google openDNS) and using these servers

208.67.222.222
208.67.220.220

Thats it! 
save everything and you should have a working internet connection that is shareable!  obviously everyone needs their own ip address and setup is a little cumbersome but hey it works!

if you want dhcp you can probably get this to work using ubuntu server, wvdial, and the great help by googling ubuntu easyrouter.

but hey this works for me....and I like having network manager deal with the usb modem.

Hopefully there aren't too many typos in this hope it works for you!!

Cheers, 
Brady

---

### Post by woodmaster on 2010-01-18
was wondering if this was possible...I'll have to give it a go

---

### Post by Tche² on 2010-02-13
Excellent tips. It works perfectly for me with Vodafone 3G Modem Huawei 220.
Thank you.

---

### Post by Sylslay on 2010-02-13
Thanx for post, I was looking for that since yesterday.
\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/\\:D/,
I will try with wlan0 connection on old liksys B router, and see if it working aswell.

Not tested yet, and whan I leave getway blank, I can't go forword and press "next" not highlihted. But I will edit config file /etc/interfaces with vi.
thx,testing tomoorow.

Not working in juanty 9.04, or I did not tray hard enugh!

Primo: Whan set eth0, need wrote any gateway for lan card, if I wan't leave blank "next" bottom is gray and can't go foward.

2. Setup firestarter is easy , no problem.

3. Setup 3g card is done be network menager, I use Huaweii e220 from Meteor.

3. But when set eth0 and  I switch off DHCP, I set 
ip: 192.168.101
mask: 255.255.255.0
gateway (router one) 192.168.1.1

4. Do I need switch of DHCP in router aswell?

5. Any time I connect both 3g and lan to router, my browser stop connecting, 
if I tray ping I have mesg: 

PING 212.77.100.101 (212.77.100.101) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=1 Destination Net Unreachable
From 192.168.1.1 icmp_seq=2 Destination Net Unreachable
From 192.168.1.1 icmp_seq=3 Destination Net Unreachable

6. If I switch off DHCP at ruter and write this setings

address = 192.168.13.1
netmask = 255.255.255.0
leave gateway blank,

just can't login to router at all.
without gate.

---

### Post by Sylslay on 2010-02-18
**GUAYS, ARE YOU USE CROSSOVER OR STRAIGHT LAN CABLE? **

It works for me too. --SOMESTEAGE!!!
Did fresh install ubuntu 9.10 and setup step by step.
Switched off DHCP on router and then set static ip for eth0 and used firestarter.

THX.
PS . When put some ip addres as gateway than coudn't put (change for empty), or live blank ip..
So delete old Auto eth0 and created new wired connection with network menager.

Next day I though!!

Now just need secend PC to run last test.
Or tray test it in VirtualBOX.

Next day I figure out that!!

Try test in VirtualBox.

FIRST I DID , EVERYTHING AS ABOVE.
SECOND. 
SET VIRTUALBOX WITH NEW UBUNTU 9.10 BOX, AND IN network seetnig I mark INSTEAD NAT, used 
bridge with wlan0 , my wifi card from Host.

So I was able to login on VM to my router box for gatway 192.168.1.1.
Able to change any setings and so on.
BUT COULD'T COONNECT TO INTERNET, FIRSTARTER WAS ON, INTERNET WAS ON HOST, BUT NO ON VIRTUALBOX WITH UBUNTU.

[COLOR="Red"]NO JOY!!![/COLOR]

Plese anyone point me to  and [COLOR="Blue"]SAY[/COLOR], what I have done wrong?

Next day I will delete this post.....

---

### Post by Sylslay on 2010-03-05
[COLOR="Teal"]JOY[SIZE="3"][/SIZE][/COLOR]:p

laptop 1: ppp0,
ISP: Meteor, all setings mark for  auto with share with other users.
DNS from Meteor is 
212.129.64.220
212.129.64.221

Firestarter set as above, 
dhcp is off, 
ppp0 => eth0
(red picture with thunder in tray, but is blue play in panel of firestarter, ITS ON.)


Lan seting: I call it split eth0 insted auto eth0

ip: 192.168.13.1
mask: 255:255:255:0
gatway: 0:0:0:0

dns: from opendns:
208.67.222.222
208.67.220.220

ROUTER: Linksys befw11s4srouter 10/100MB lan, wifi 11mB

Basic setup:
DHCP IS OFF,
Obtain IP automatic is off:

Static is used:
IP: 192.168.13.10
MASK: 255:255:255:0
gatway.192.168.13.1

dns: from meteor

212.129.64.220
212.129.64.221


TAB: Advance settngs.
static 192:168:13.1
mask 255:255:255:0
connect to: 192.168.13.1

After saved setting, can't any more log to router, but internet is working on both laptops



laptop 2: wifi

ip:	192.168.13.5
mask: 255.255.255.0
gatway 192.168.13.1
DNS:Meteor:
212:129.64.220
212.129.64.221

laptop2: Lan

192.168.13.2
maska: 255.255.255.0
gatway 192.168.13.1
DNS:Meteor:
212:129.64.220
212.129.64.221

Scenario 2: (You can test without second laptop that internet coming form router)
Option with Vitual Box, tested.

Insted "Nat" I bridge wlan0-laptop1 to => "virtualbox"-eth0-inside
and run karmic.iso as VM,

seting are like:
laptop1 with Virtualbox host - wlan0 at laptop1 and eth0-inside Virtualbox :
laptop1 ip: any from local link beetwin wifi-card and router, network manager set  as local link, 
for eth0-inside 192.168.13.20
mask: 255.255.255.0
gatway 192.168.13.1
DNS: from opendns:
208.67.222.222
208.67.220.220

conclusion:
all computres are part of one domain 192.168.13.x
1st laptop with ppp0 got lan ip 192.13.1 and is call gateway.
I mess with 2 DNS, aslong as it working I don't care.
I knew that I can bridge vboxlan with ppp0 and get internet much easer, Scenario 2 purpose only for testing that connection is realy shared.

PS. For me subject is close. I used crossover lan cable.
Works for Two WinXP machine aswell, instead Firestarter, need mark share internet connection on 1st laptop 3G Broband

---

### Post by aircftech on 2010-04-11
Works great after I put in all the dns info and disabled my router dhcp.

Thanks Brady!

---

### Post by BKaren on 2010-04-18
> **bradyh said:**
> Hi so I just managed to share a 3g verizon um175 card's connection over the ethernet very easily.
 
So the first computer has to be powered up all the time for this to work correct? 
 
That would not work for us, the only computer that is even always here is the old desktop in the basement that the grandkids use when they visit. It is only turned on when they are here, and the 3G coverage down there is marginal. 
 
We use an [MBR1000 router ]("http://mbr1000.com")located on the top floor, and all the computers including Linux, Macs and PCs play well together using it. 
 
When the house was built it was assumed that the internet would come into the basement where the phone line does, so the house was prewired with Cat5 to most rooms. When it was time to move in we discovered that wired internet was not available here, only satellite or cellular. The room the router is located in luckily was wired, so we use that link the reverse of the way it was intended. 
 
The laptops for the most part are of course wifi. 
 
Later

---

### Post by Sylslay on 2010-05-09
Yes, need power up 2 machine (or more) all the time, so Two peaple can use anu CHAT cliant at the same time. But not sure aboue 2 Skype on one LAN. Never Check.

---

### Post by mezo9090 on 2010-09-13
worked like charm, thanks, i was looking for this for a very long time.

---

### Post by masque7 on 2010-10-01
Works good for me between 2 Ubuntu boxes. Any ideas on alternatives to Firestarter (e.g. for command line systems)? Is Firestarter really necessary?

EDIT: any ideas why sharing the 3g connection like this this breaks the LAN/filesharing?

---

