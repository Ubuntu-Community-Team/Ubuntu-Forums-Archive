---
title: "How to Connect to Internet through GPRS Phone via Bluetooth"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by karumudi7 on 2010-02-23
How to connect to my Mobile Phone which have GPRS. 
I want to connect Via BLUETOOTH. Becoz I dont have any Data Cables.
Plz give me the instructions to connect to my Phone via Bluetooth to access Internet.

Plz give OFFLINE installation instruction becoz no internet connection for that PC.

---

### Post by karumudi7 on 2010-02-24
No one? :(

---

### Post by karumudi7 on 2010-02-24
Plz reply guys!

---

### Post by karumudi7 on 2010-02-25
Hey Linux Geeks where r u?

---

### Post by harisund on 2010-02-26
You do realize posting like this isn't going to get anyone's help right? 

Instead of what you are doing, why don't you be a little more specific?

---

### Post by PaulReaver on 2010-02-26
you need to know your carrier information.

for example for t-mobile-uk
Username    = User
password    = mms
phone number=*99#

---

### Post by PaulReaver on 2010-02-26
open a terminal

add your username to the dip group
in a terminal

sudo useradd -G dip YourUserName

then in a terminal 

sdptool browse


scroll the terminal up and look for "Browsing" followed by and number in this format   XX:XX:XX:XX:XX:XX

this is your bluetooth address. write it down.



look in the same terminal for "Service Name: Dial-up networking" 
four or five lines under this there will be a "channel:" entry write this number down. this is your dial up networking bluetooth channel.

in a terminal type

sudo rfcomm bind rfcomm0 {your bluetooth address} {your bluetooth channel}


this connects the phone to rfcomm0

then in a terminal

sudo pppconfig

select create a connection
leave this as "provider"
then select ( ) Dynamic  Use dynamic DNS
then select  PAP      Peer Authentication Protocol
enter the mobile network username
enter the mobile network password
leave the modem port speed at default
leave the next one at  (*) Tone 
enter the mobile network phone number
select to choose modem port yourself and enter /dev/rfcomm0
then select "Finished Write files and return to main menu."
select ok
then  "Quit   Exit this utility"




thats your phone set up as a dial up modem.
just press alt and F2 and type pon to connect to the internet
and poff to disconnect

Simples   :)

---

### Post by alcarola on 2011-01-11
In Lucid Lynx you don't need to follow the above steps to access the Internet over GPS via Bluetooth. Nowadays its only a matter of a few clicks in the right places

I first configured a bluetooth connection to my ancient GSM phone Nokia 6021 in Blueman applet and then I configured mobile broadband in NetworkManager Applet. Then I could use these two applets to connect to the internet.

---

