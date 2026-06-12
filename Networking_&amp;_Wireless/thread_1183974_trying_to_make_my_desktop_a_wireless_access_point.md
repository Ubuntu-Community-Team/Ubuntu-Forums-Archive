---
title: "trying to make my desktop a wireless access point"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by xxkilo on 2009-06-10
I'm very new to Ubuntu and a couple of days ago installed 8.04. I was surprised at how fast I was able to solve the problem of getting connected to the internet. However a more complicated problem followed.

I can't get my wireless card to work... I have 2 cards: my ethernet card which connects directly with a cable and a wireless card which in windows worked quite well as a wireless access point for my laptop.

I thought I had found the perfect "how to doc": 
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

I followed the instructions and everything seemed fine until the part where I need to restart my network: 
sudo /etc/init.d/networking restart

[FONT=Verdana]this is the error I got:[/FONT]

[COLOR=Red] * Reconfiguring network interfaces...                                           * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
SIOCDELRT: No such process
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
dsl-provider: ERROR while getting interface flags: No such device
Plugin rp-pppoe.so loaded.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
[/COLOR]
I'm not sure what I should do...

I ran lspci and got:
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

iwconfig gave me:
wlan0     IEEE 802.11g  ESSID:"'Kilo Wireless Connection'"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Anyone have any ideas? Thanks.

---

### Post by xxkilo on 2009-06-10
well... I got the error to go away by doing some playing around in 
sudo gedit /etc/network/interfaces

firestarter started but now if I have firestarter using eth0, my internet connection drops. I have to set it to use ppp0.

The next part of the instructions say that the wireless network should appear on the client computer but it doesn't.. my laptop uses Vista.. could this be the problem.. It worked with my desktop in XP.

I'll keep playing around until I get somewhere or someone konws the solution...hope someone has a simple answer.

---

### Post by superprash2003 on 2009-06-11
your trying to setup ICS right??
 so why not do it via firestarter and then setup your ubuntu machine in adhoc mode so that it can behave like a WAP , although it could connect to only 1 machine at a time..
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

---

### Post by xxkilo on 2009-06-19
thanks superprash.. I actually saw that article before. Sorry I haven't replied or had a chance to try it. I've been so busy with work lately. I think I'll try the adhoc connection tonight. But Ideally I'd like to have more than one computer connected as I have 2 laptops in the house.

---

### Post by xxkilo on 2009-06-19
so I tried to set up the wireless network again...

Yes I am trying to set up ICS... but I think you might need to be a bit more clear with me. You said do "it" with firestarter.. what's "it"?
Then I tried to look at the ad hoc document but it's pretty confusing to me.. It doesn't seem like a step by step walk through but more an explanation of different setups. I'm not sure if I need to install network manager, fix wireless in ad-hoc GUI or use wireless extensons CLI tools.

---

