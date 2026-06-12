---
title: "networkmanager chooses wrong network"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by duncombe on 2010-11-21
I have a problem with NetworkManager making the wrong choice of network to connect to when coming out of sleep or booting. 

I want to have my laptop (lucid) preferentially use the wired network eth0 when it boots or comes out of hibernate or sleep. No matter what I tried it connects to the wired network and then also tries to connect to wireless as well, even when I have had wireless unabled when going to sleep. 

Attempting to fix this by turning off auto connect on the wireless essids has introduced a secondary problem. Now when it wakes up, the network it tries to connect to is not mine, call it C*, but my neighbors, call it N*, to which I have never been connected and do not have permission or passwords to connect to. Even when I am using wireless and was connected to my own network before sleep, when it comes back it tries to connect to the N* network, instead of C*. 

So I'd like to know how to have NetworkManager connect to eth0 and only if there is no network on eth0 to attempt to start wireless. And I'd like to tell it to ignore other networks than C* especially if C* is up and working, and under no circumstances to attempt to connect to N*, even if there is no other network to be found.

Reading the documentation of NM it seems to me that this all should be taken care of automatically, but in my setup it is not working the way it should! 

Any help appreciated,
Thanks
    Chris

---

### Post by magnatron on 2010-11-21
If you right click the network manager you should be able to edit connections, under the wireless tab you'll find the one it keeps trying to connect to, to stop it just delete that one from the list.

---

### Post by Hippytaff on 2010-11-21
have you tried
```

{name of wireless} down

```
ie on mine it would be
```

eth1 down

```
:-)

---

### Post by duncombe on 2010-11-21
I did try that, next time I sleep and come back NetworkManager has put it back in the list and is trying to connect to it again.

---

### Post by duncombe on 2010-11-21
But that will surely disable the interface. I want to ignore an invalid essid on the interface, and connect to a valid one.

---

### Post by magnatron on 2010-11-21
If you delete the invalid one from the list it will stop trying to connect to it. It wont delete the interface only the invalid one that it keeps trying to connect to. When you left click you should still see a list of networks to connect to in the wireless list. I take it we're talking about disabling the wireless, not the wired network.

Hippytaff is correct and to find out what your wireless interface is on the command line it's usually a good idea to get familiar with iwconfig which will bring up a list of devices that are wireless enabled in my case it shows up as wlan0 in the terminal, example:

inspiron:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"XXXXXXXXX"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00: DE :AD:BE:EF   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr Off   Fragment thr Off
          Power Management Off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

to switch it off manually from the command line I would type: iwconfig wlan0 down

the command iwconfig wlan0 up or ifconfig wlan0 down (up) should do the same thing only the command up will turn it back on again!

---

### Post by duncombe on 2010-11-21
okay, I know about iwconfig and iwlist.

Deleting the offending essid from the NM wireless list does seem to work (although I am sure I did try before and had the problem as described, but now it seems to be working and the N* network is ignored), so lets say that part of the problem is solved. To return to getting the wired/wireless thing working, you are saying I should iwconfig wlan0 down. Then I will surely have no wireless connection. What happens when I take the laptop upstairs away from the wire, and I want wireless on? Do I have to manually bring up the wireless interface, despite that the documentation says that NM takes care of this automatically?

---

### Post by Hippytaff on 2010-11-21
if it doesn't work automatically then
```

wlan0 up

```

---

### Post by magnatron on 2010-11-21
Sorry my bad, I presumed that what you where saying was that you kept having the neighbors wireless auto connect to your NM when you took your PC out of sleep (hibernation etc) what normally causes that is if you've accidentally clicked his Wifi instead of your own, its then obviously presented you with a password prompt and then you click cancel and the normal problem is as you've described it then seeks to auto connect on startup every-time to a network you dont want to connect to.  So what I was saying was RIGHT click goto Edit Connections to DELETE the erroneous WiFi in the auto connection list of the NM.  Not disable your Wireless interface, once you've edited the auto connection out of the NM that should be the end of that interface pop-in up in your NM but if it isnt, then all I can say is who's been using your PC. lol

---

### Post by duncombe on 2010-11-21
Magnatron: 

Yes, if I think careful what I was doing when I had the neighbour network problem, I may well have clicked inadvertently on the offending network and caused it to join the list again...

Now to get the wireless network not to be connected to when the wire is connected?

Thanks for your help!

---

