---
title: "rt2500 wifi card with dapper??"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by anuski on 2006-06-12
I have been trying to get my conceptronic wifi card (chipset ralink rt2500) with ubuntu dapper in my compaq evo n1100 for over a week a now with no success. I am a newby to linux, but i am getting more and more confused because i think it is showing a weird behaviour. Any help, useful links, etc will be very appreciated.

In the begining i thought the only problem was about wpa. The card was detected as eth1 right away and drivers seemed to be working properly. I could, for example, do a iwlist scan and see the net i desired to connect to. I the meanwhile i installed wifi-radar, wifi assistant and network manager to see if they would be of any help. They all showed the net without problems, but wasn´t able to connect. I was sure it was only about the wpa and struggled to make it work with no results.

Then when i changed the net's security to open, all the applications listed above and the iwlist scan will still show the net but i could still not connect. However strange this may seem, this didn´t bother me too much because the same happenned with windows xp: when it was open, i was not able to connect (although i ad had no problems with wpa).

No, what really has me stunned. When i changed it to a wep key, windows xp again had no problems connecting. But in ubuntu, now network manager won't detect my net. Wifi-radar does but the signal quality goes on and off. Similar result for the iwlist scan, sometimes it detects the net, sometimes it doesn't. Like if the signal was going on and off. But it goes smoothly with windows.

I really don't want to use windows to connect to the internet, so ir really need to get this working. Can anyone please help?

---

### Post by anuski on 2006-06-13
ok, i have made some progress i think. I was manually trying to configure and still don't have access to the web, so it is not working, but for the first time ever, when doing an iwconfig eth1 i don't get link quality 0/100. 

Now, wifi-radar is still doing the blinking stuff about my signal quality. Network manager still doesn't detect it. But now an iwlist scan will alwasy do.

This is what i get for a iwconfig eth1 and iwlist eth1 scan:
eth1      RT2500 Wireless  ESSID:"mynetsname"
          Mode:Managed  Frequency=2.467 GHz  Access Point: 00:16:38:C4:FF:58
          Bit Rate:54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:myhexkey   Security mode:open
          Link Quality=73/100  Signal level=-36 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


eth1      Scan completed :
          Cell 01 - Address: 00:16:38:C4:FF:58
                    Mode:Managed
                    ESSID:"mynetsname"
                    Encryption key:on
                    Channel:12
                    Quality:74/100  Signal level:-102 dBm  Noise level:-192 dBm

Now, it bothers me a lot that what appears as the key when i do an iwconfig eth1 is NOT what i have set as key using the iwconfig key. It adds a 0 at the beginning and 12 more at the end. Is this the problem? 

I have the feeling i am nearly there but there is something really simple i am not getting. Any suggestions?

---

### Post by anuski on 2006-06-13
It is working!!!!
Ok, not one GUI is working, but i could easily configure by hand it once i realised my key was ascii although it was very hex looking (dumb me) and i had wireless connection working! I then edited /etc/network/interfaces and now i have it on reboot. It is great! I don´t get a nice icon on my tool bar, but i give a damn. If i ever manage to make it work with wpa, i'll post how.

---

### Post by Skullster on 2006-06-15
Hi I am glad you got it to work!

I have a RT2500 minipci card in my X64 laptop.  I have done everything as you have and tried swapping between asci and hex key types (HEX is right) but it just will not connect even though all the scans say it should:-

~$ iwconfig ra0
ra0       RT2500 Wireless  ESSID:"essid"
          Mode:Managed  Frequency=2.437 GHz  Access Point: mac here
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=61/100  Signal level=-66 dBm  Noise level:-199 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


~$ iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: mac here
                    Mode:Managed
                    ESSID:"essid"
                    Encryption key:on
                    Channel:6
                    Quality:60/100  Signal level:-68 dBm  Noise level:-199 dBm

So then I tried looking at what the key it thought it had and here it is after being entered in /etc/network/interfaces as the correct HEX value

~$ sudo iwlist ra0 encr
ra0       2 key sizes : 40, 104bits
          4 keys available :
                [1]: ????-????-????-????-????-????-?? (104 bits)
                [2]: off
                [3]: off
                [4]: off
          Current Transmit Key: [1]
          Security mode:open

- this is the same key as on the router but its only says its 104 bit.  My trusty netgear router does 64 and 128! Here the keysizes are 40 and 104.

Bloomin thing wont ping anything so ifp was used and:-

~$ sudo ifup  ra0
SIOCADDRT: Network is unreachable
Failed to bring up ra0.

So now I am stuck!  Either the drivers shipped with Dapper for the RT2500 are using old encryption or I have missed something!  Back to the terminal!

If anyone could help on this I would be very happy - I really need to get on with trying XGL and Compiz :cool:

---

### Post by Skullster on 2006-06-15
Ah Ha!

Now It works!  I removed all the IP6 refs from the hosts entries!  This fixed the issue both using a static IP and a fixed IP!

YAY!

Still no nice GUI though ;-)

---

