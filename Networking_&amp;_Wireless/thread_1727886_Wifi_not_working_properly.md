---
title: "Wifi not working properly"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by j-peg on 2011-04-13
I just installed Ubuntu 10.10 tryed 11.04 but didn't work, but in both my internet connection was a lot slower than it is on windows. I can connect to the wifi but i get 1/10 of the speed that i usually do and it keeps losing the connection.
I'm using a MSI computer with a "802.11bgn 1T1R mini Card Wireless Adapter"

thx in in advance :)

---

### Post by j-peg on 2011-04-15
Plz help i have tryed find people with the same problem and i find alot but i can't find any good explanations too solve it (could be because I'm new to ubuntu ;)).

---

### Post by uncaspi on 2011-04-15
You could try to turn off power save mode.
sudo iwconfig wlan0 power off txpower 20

In the example it is used wlan0 for the card. You may need to replace it with your card.

---

### Post by j-peg on 2011-04-16
Hmm when i typed it in it just told me that it didn't know what Txpower were

---

### Post by j-peg on 2011-04-16
also i can use the internet when i have it pluged into the ethernet but only for google nothing else works...

---

### Post by uncaspi on 2011-04-16
Ok type sudo iwconfig wlan0 power off

assuming your card is wlan0

Linux is case sensitive. Sure you typed txpower 20

---

### Post by j-peg on 2011-04-17
hmm i tryed sudo iwconfig wlan0 power off but nothing really happened my wlan is wlan0, i checked and my txpower is set to 17 but i can't seem to change it tryed typing the other thing again.
I have also tryed getting ndiswrapper and ndisgtk to work but can't get them installed so after about 12 hours i gave up trying to repair it that way... 
when i wrote the power off line it seemed that it is holding on to the internet longer but it still just gets slower and then stops working after 2 min..

---

### Post by uncaspi on 2011-04-17
To see if you have any intruders, trojans etc open a terminal and shut down all internet applications. See if there are any traffic through the the card by issue this command.

sudo /sbin/tcpdump -i wlan0

---

### Post by j-peg on 2011-04-17
Hey I'm a pretty big newb in ubuntu ;) i tryed writing the code but it just told me it couldn't find it
I don't think i have a trojan horse or something like that because the only things i have downloaded was through genuin websites (ubuntu.com and chrome) i tryed copying the iwconfig for my wlan:
jpeg@masterbate:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Pixels"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:CB:21:74:47   
          Bit Rate=1 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=12 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But when i drop the wlan and connect directly it gets worse, then i dont ewen have 2 min my connection can just only load google nothing else (could be because google take so litle)

thx for all the help so far i really apriciate it

and do you have any personal experience with ndiswrapper and ndisgtk?

---

### Post by hoppings on 2011-04-17
Hi,

I'm very sorry for posting this in the wrong place but I've spent ages trying to work out how to post a new thread on the forum, without success.

How do I set up Cisco on Ubuntu for BT Fon or OpenZone?

I run a Mac desktop at home but out and about I have a laptop running Ubuntu. 

Ability to access BT Open Zone and Fon would be great but I understand they are not secure without a VPN client.

Problem is I need hand-holding to do anything remotely 'networky'.

Having managed to get the Cisco client installed I now need to configure it before connecting. When looking at the box to input the parameters I do not have a clue. 
I go to Network - VPN Connections - Configure VPN - 
In Network Connections I go to the VPN tab and click Add.
In the Choose a VPN Connection Type box I select Cisco Compatible VPN (vpnc) from the drop-down list.

Then an Editing VPN Connection 1 box comes up.
That's where I stop and don't have a clue - what's a Gateway, Group name, etc. ???

Please can someone direct me where I can get some help with this.

Does anyone have any experience of Ubuntu to access BT OpenZone that can a advise how to fill in the parameters.?

---

### Post by uncaspi on 2011-04-17
I saw from your posting that the bit rate was set to 1Mbs.
Try this.

sudo iwconfig wlan0 rate 54M


To hoppings:

New thread is labeled at the upper left corner on the forum

---

### Post by j-peg on 2011-04-18
okay i will try that :)

---

### Post by j-peg on 2011-04-18
Nothing happened, but think it must be some setting since its both wlan and ethernet there is screwing up

---

### Post by uncaspi on 2011-04-18
Maybe your card doesen't support 54M. Try
sudo iwconfig wlan0 rate 11M

And maybe you must restart the network service before the changes takes place.

sudo /etc/init.d/networking restart

or sudo cd /etc/init.d
./networking restart

---

### Post by j-peg on 2011-04-18
nope i looked at iwconfig and it had changed but i will try with 11M instead

---

### Post by j-peg on 2011-04-18
Hey i fixed it :D after watching what you had told me to write i started too se a pattern with what things you can change in "iwconfig" so i just tryed everything, and when i set power management "sudo iwconfig wlan0 power on" and it works :) Thanks alot now i can actually use Ubuntu ^^

---

