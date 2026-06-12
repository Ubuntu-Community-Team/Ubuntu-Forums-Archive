---
title: "Wifi Problem"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by topdog2009 on 2009-11-25
I have an HP laptop with a dual boot into Windows Vista and Ubuntu. I am unable to get high speed where I live so therefore attempt to connect at a local establishment which has high speed wireless available.

Windows Vista automatically recognizes the wireless network and signs in. Ubuntu does not find the wireless network.

Any ideas how a newbie to the linux system can connect to the wireless network?

---

### Post by pdc124 on 2009-11-25
sudo iwconfig
to list your wireless card

then 

sudo iwlist ethx scan 
to list the networks it can see , and a bit about them (eg encryption).

---

### Post by topdog2009 on 2009-11-26
Thanks, I will give that a try on my next visit.

---

### Post by topdog2009 on 2009-11-27
sudo iwconfig reported the following:-

lo  no wireless extensions
 
eth0 no wireless extensions

wmaster0 no wireless extensions

wlan0 IEEE  8.02 11 abgn  ESSID ""
Mode: Managed
Frequency: 2.412 GHz
Access Point : Not Associated
Tx - Power = 20 dBm
Retry min limit : 7
RTS thr: off
Fragment thr = 2352 B
Encryption Key : off
Power Management : off
Link Quality : 0
Rx Invalid crypt  : 0
Rx invalid frad : 0
Tx excessive retries : 0
Invalid Misc : 0
Missed beacon : 0

AND

sudo iwlist ethx scan   Reported: 

Interface does not support scanning

NOTE- I was not in a WIFi area when I did this.

Brian

---

### Post by pdc124 on 2009-11-27
try
 sudo iwlist wlan0 scan

which should list the wireless networks the card can see

---

### Post by topdog2009 on 2009-11-27
That produces:

wlan0 no scan results

---

### Post by pdc124 on 2009-11-27
are you in range of the wireless network you want to connect to ? 

what does the GUI  show  for wireless networks ?

---

### Post by topdog2009 on 2009-11-27
Not during the running of the scripts that you recommended. I have to make a trip (about 30 minutes) to get to the closest Wifi source.

I may be able to check this weekend. I can try again and run the scripts and getg back. Appreciate your assistance.

Brian

---

### Post by topdog2009 on 2009-11-28
Currently in a HoJo and get the following on sudo iwlist wlan0 scan

Cell 01 - Address 00:90:4C:91:00:01 ESSID: "Hojo block"
Mode: Master
Channel: 11
Frequency 2.462 GHz (channel 11)
Quality = 9/100 Signal leve; : -112dBm Noise level = 118 dBm
Encription key: off
IE: Unknown 000A486F6A6F20626C6F636B
IE: Unknown 010882848B962430486C
IE : Unknown 03010B
IE : Unknown 2A0100
IE : Unknown 2F0100
IE : Unknown 32040c121860
IE : Unknown DD06001018020004
:
Bit Rates 1:2:5.5:11:18:24:36:54:6:9:12:48
Extra: tsf 000002608d952fA8
Extra: Last Beacon : 2216 ms ago

Brian

---

### Post by RedSingularity on 2009-11-28
Still no internet though?  Try pinging a website such as google......

ping -c 5 [www.google.com](www.google.com)

if that doesnt work try this..........

ping -c 5 66.249.80.104

---

### Post by topdog2009 on 2009-11-28
Pinging Google received the message "unknown host"

Pinging the number received the message "network is unreachable"

Brian

---

### Post by RedSingularity on 2009-11-28
Did you ever install any drivers for this card?  

Post the output of lspci

---

### Post by topdog2009 on 2009-11-28
All I have installed is Ubuntu from the CD. I cannot connect using either wifi OR a Bell USB stick, therefore I have innumerable upgrades to do hence the need to be able to get connected.

lspci reports (amongst other things)
02:00.0 Network Controller: Atheros Communications Inc. AR928 Wireless Network Adapter (PCI-Express) (rev01)

I have to finish a presentation I have to do in Windows UGH! so have to sign off for the evening. Thanks for the assistance - i will endeavour to pick this up tomorrow.

Brian

---

### Post by RedSingularity on 2009-11-28
Before doing the below check in System>Admin>Hardware Drivers to see if your card can be activated there.  And make sure your card is switched "on" either with a switch or a key combination.  Many times users have not turned the card on.  If none of this works continue below......

Download madwifi located [here]("http://sourceforge.net/projects/madwifi/").  To install..........

1)  Extract the folder to the desktop.
2)  In a terminal do cd ~/Desktop/madwifi-0.9.4
3)  Then type ./configure (it may give you errors)
4)  If no errors type make 
5)  Then type sudo make install
6)  Reboot

---

### Post by topdog2009 on 2009-11-30
Thanks, I will give that a try but I will not be near a wifi source for at least a week. I will be back <vbg>

On another note but somewhat similar - I currently have my machine as a dual boot Windows & Ubuntu. Can I also use Ubuntu in a virtual machine and, is that is possible, can I use the Windows connection to access the web throught Ubuntu. Hope that makes sense.

Brian

---

### Post by topdog2009 on 2009-11-30
System>Admin>Hardware Drivers - found no drivers!

Downloaded madwifi

cd ~/Desktop/madwifi-0.9.4 produced No such file or directory.

Because of my lack of knowledge of the language, I finally got there by
 cd\Desktop
cd\madwifi-0.9.4

/config produced 'No such file or directory.

A listing of the madwifi directory produced this list of files:

ath
ath_hal
BuildCaps.inc
contrib
COPYRIGHT
docs
hal
include
INSTALL
kernalversion.c
makefile
makefile.inc
net80211
patches
README
regression tools
release.h
scripts
THANKS

Because the configure did not produce anything positive I did not run make. Is it safe to do so?

Brian

---

### Post by Albertkinng on 2009-11-30
hello, I have a netbook, this netbook can connect in wifi at work but it can't at home. It asks for the wep number and it doesn't matter how many times I put the number it try to scan but it's asking again and again for the wep number, it's the same I use for all my computers in my house, but this ubuntu netbook  don't want to connect to my wifi antenna in my house, everywhere it connects fine even in the airport.... but no in my house... help me please!

---

### Post by RedSingularity on 2009-11-30
> **topdog2009 said:**
> System>Admin>Hardware Drivers - found no drivers!

Downloaded madwifi

cd ~/Desktop/madwifi-0.9.4 produced No such file or directory.

Because of my lack of knowledge of the language, I finally got there by
 cd\Desktop
cd\madwifi-0.9.4

/config produced 'No such file or directory.

A listing of the madwifi directory produced this list of files:

ath
ath_hal
BuildCaps.inc
contrib
COPYRIGHT
docs
hal
include
INSTALL
kernalversion.c
makefile
makefile.inc
net80211
patches
README
regression tools
release.h
scripts
THANKS

Because the configure did not produce anything positive I did not run make. Is it safe to do so?

Brian

Make sure you have typed ./configure and if there is still no file found go ahead and do the make command followed by sudo make install.

---

### Post by RedSingularity on 2009-11-30
> **Albertkinng said:**
> hello, I have a netbook, this netbook can connect in wifi at work but it can't at home. It asks for the wep number and it doesn't matter how many times I put the number it try to scan but it's asking again and again for the wep number, it's the same I use for all my computers in my house, but this ubuntu netbook  don't want to connect to my wifi antenna in my house, everywhere it connects fine even in the airport.... but no in my house... help me please!


I suggest you start a new thread.....you will receive more help that way.  :) Anyway, Have you chosen the proper encryption standard for your network?

---

### Post by topdog2009 on 2009-12-01
./configure produced nothing

make produced:

cd:1:can't cd to /lib/modules/2.6.28-15-generic/build
makefile.inc;66 ***/lib/modules/2.6.28-15-generic/build is missing,please set KERNELPATH. Stop.

I realise what is happening but not sure why. I thought that I had installed Ubuntu by just following the install instructions. Obviously I need to learn a lot more about the language.
I can find the missing file in the correct directory.

Brian

---

### Post by RedSingularity on 2009-12-01
I have just researched it and i see that ubuntu 9.04 already has the driver installed.  Is there a key combination to press on the computer itself to enable the card?  On mine it was Fn+F6 or F7.

---

### Post by elmoisk00l on 2009-12-01
I am experiencing nearly the same problem, I had gotten a virus on my school issued netbook (Windows) and decided instead of having them re-image it for me I would just put Ubuntu on it fully. (Had had it dual-booting) So I used a Live USB and reformatted over the entire drive. Now, I cannot use the Fn+F6 combination to turn on the WiFi card. (LSPCI output: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)) It had worked when I had it dual booting... Any suggestions on how to get the Wireless card to come on? I am currently using an Ethernet cable to post this. 
It had worked in the past so I know that it is compatible, to a degree.
 Various Stats:
Dell Latitude 2100 Netbook
Dell 1510 wireless card
2 GB ram
16 GB SSD

As soon as I get WiFi working I will be a very happy person :)

---

### Post by topdog2009 on 2009-12-01
Unless there are bells and whistles when the card is enabled I cannot tell if the Fn and F6 or 7 works. The Fn F7 combination lowers the brightness of the screen; the F6 key has a padlock pictured on it but it does not appear to lock anything.

I will now have to wait until I get to attempt to use a wifi .

Thanks for you assistance, I will let you know what happens.

Brian

---

### Post by RedSingularity on 2009-12-01
> **topdog2009 said:**
> Unless there are bells and whistles when the card is enabled I cannot tell if the Fn and F6 or 7 works. The Fn F7 combination lowers the brightness of the screen; the F6 key has a padlock pictured on it but it does not appear to lock anything.

I will now have to wait until I get to attempt to use a wifi .

Thanks for you assistance, I will let you know what happens.

Brian


It may not be those keys on your laptop/netbook.  Look at the different symbols and make your best guess.  It may help if you have a light for the WLAN.  It will turn on when you press the key combo.

---

### Post by topdog2009 on 2009-12-02
Hooray..

Well Hoo anyway. Hopefully when I am in a wifi area the ray part will come. The magic light of wifi came on.

Keep your fingers crossed, I will let you know if it is successful. Thanks again.

:D

Brian

---

### Post by topdog2009 on 2009-12-18
I guess instead of Hoo Ray it will be Boo Hoo.

I am currently on line in a wifi environment using windows.

Despite all the assistance I have received I still cannot get Ubuntu to recognise the wifi system on my machine.

Guess I have played enough with Ubuntu. I might try one other system to see if I have any more success.

Thanks for all those who offered advise.

Brian

---

### Post by The3irikr on 2009-12-21
hey i have the same thing... all those tests i basically got the same result. 
the last post about the ping, i did in the terminal 
ping -c 5 66.249.80.104
and got
network is unreachable..
:confused:

---

### Post by RedSingularity on 2009-12-21
Post your output of 

lspci | grep Network

---

### Post by The3irikr on 2009-12-21
ok i got

02.06.0 Network controller: Broadcom Corporation BCM 4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by RedSingularity on 2009-12-21
Now post the output of lsmod.

---

### Post by The3irikr on 2009-12-21
it says the output is
2780  1 video

---

### Post by RedSingularity on 2009-12-21
In a terminal do 

sudo apt-get install b43-fwcutter

then reboot and see if you can connect to a network.

If you cannot look in System>Admin>Hardware drivers.

---

### Post by The3irikr on 2009-12-21
i'll try..
check this out.. it's a problem i have...
[http://ubuntuforums.org/showthread.php?t=1360890](http://ubuntuforums.org/showthread.php?t=1360890)

---

