---
title: "WPA not a choice"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by boots963 on 2010-01-17
I am new to ubuntu and would like to use it but it is making it very difficult for me to decide if there are any pros to the OS
...Anyway
  I am trying to connect to my home network which is wpa\psk
when i click on the networking item in the tool bar at the top it shows my network and when i click on it to join the network it asks my for my security and it only lists wep 40/128-bit key or wep 128 bit phrase or leap?? or dynamic wep(802.1x)

there is no choice for wpa. but when i set up a new network or attempt to edit the network listed under wireless i can see wpa but the system does not connect i have tried looking around for info all with instructions on "enabling" wpa by using wpasupplicant which is there but nothing happens in fact when i try the code sudo gedit /etc/network/interfaces i get command not found which in all the techniques i have tried require this line...help getting frustrated...any help would be wonderful i guess this maybe to advanced for me..who knows!!!???  thanks in advance

---

### Post by Dark_Stang on 2010-01-17
Are you sure your network is WPA? Ubuntu is pretty good about knowing what type of encryption the network is.

---

### Post by JackRock on 2010-01-17
Have you also successfully connected to this network with this machine (Even if it's with another OS) before?  The NIC may not be WPA compatible.

---

### Post by boots963 on 2010-01-17
Thank you for the response!

  Yes network is Wpa type: wpa any with  wpa shared key

---

### Post by boots963 on 2010-01-17
well the machine did not have a functional os when i got it so no but i will attempt to change my security on my network temporarily and post back!

---

### Post by boots963 on 2010-01-17
ok with the network set to open the machine connects without issues so i guess that part is eliminated!

---

### Post by boots963 on 2010-01-17
are there any options to force wpa as a choice in the network configuration? Also if i manually setup a network how do i start the connection?

---

### Post by boots963 on 2010-01-18
could this issue have anything to do with after entering 
sudo gedit/etc/network/interfaces in terminal it responds with command not found

i found this while trying to manually setup the wireless connection?

---

### Post by tjohnson_nb on 2010-01-18
> **boots963 said:**
> could this issue have anything to do with after entering 
sudo gedit/etc/network/interfaces in terminal it responds with command not found

i found this while trying to manually setup the wireless connection?
I thin you need a space after 'gedit' :)

---

### Post by gradinaruvasile on 2010-01-18
Open a terminal and type in it:

sudo iwlist scan

And post here the results.

---

### Post by bkratz on 2010-01-18
Just for the future

When using a graphical program (such as gedit) you really should be using gksudo rather than sudo. Here is an explanation of why (although you probably won't actually see the difference).

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by boots963 on 2010-01-18
ok here is post from iwlist scan

lo                     interface does not support scanning

eth0                  interface does not support scanning

eth1                  scan complete :
                      cell 01 - address: 00:12:0e:16:eb:61
                                essid:"HOME"
                                mode:master
                                channel: 11
                               frequency:2.462 ghz (channel 11)
                               signal level:43 dBm noise :13dBm
                               encryption key : on
                               bit rates:1 Mb/s;2 Mb/2;5.5 Mb/s
                               11 mB/s;22Mb/s
                               extra:bcn_int=200
                               extra:capab=0x0471
                               extra: last beaconL 76ms ago

---

### Post by gradinaruvasile on 2010-01-18
Hm. Are you sure its not WEP?

Here is the output of my scan (WPA2):

```
wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:21:B9:5B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"Wlanumeu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008aeb3ea183
                    Extra: Last beacon: 112ms ago
                    IE: Unknown: 0008576C616E756D6575
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

See there are things about authentication suites and stuff your scan doesnt mention.

What hardware you have? Type 

```
lspci | grep Network
```

in a terminal and post the results here.

---

### Post by Fire_Chief on 2010-01-18
Considering the AP scan is responding with data rates from only the A/B wireless bands it is not surprising that the encryption would be WEP. I'd definitely say the wireless card or the AP are not WPA capable.

---

### Post by boots963 on 2010-01-18
ok here is post from iwlist scan

lo                     interface does not support scanning

eth0                  interface does not support scanning

eth1                  scan complete :
                      cell 01 - address: 00:12:0e:16:eb:61
                                essid:"HOME"
                                mode:master
                                channel: 11
                               frequency:2.462 ghz (channel 11)
                               signal level:43 dBm noise :13dBm
                               encryption key : on
                               bit rates:1 Mb/s;2 Mb/2;5.5 Mb/s
                               11 mB/s;22Mb/s
                               extra:bcn_int=200
                               extra:capab=0x0471
                               extra: last beaconL 76ms ago

---

### Post by boots963 on 2010-01-18
lspci | grep Network

does not give response goes back to prompt

---

