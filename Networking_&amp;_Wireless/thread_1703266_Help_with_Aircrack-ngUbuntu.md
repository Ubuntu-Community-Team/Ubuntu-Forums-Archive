---
title: "Help with Aircrack-ng/Ubuntu"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by steaksauce on 2011-03-09
Okay, so I'm using air-crack to crack into my network for fun. (It's WPA, **NOT** wep)

I've acquired a network handshake (I think, do I run ```
sudo airodump-ng --channel 11 --bssid 00:00:00:00:00:00 -w data mon0
``` and capture only_** four **_packets for WPA keys?)

After that, I need to run the command ```
**aircrack-ng -w wordlist capture_file**
```(where wordlist is  your dictionary file, and capture_file is a .cap file with a valid WPA  handshake)

My wordlist is in /home/steaksauce/Documents/Dictionaries/ and the particular file I want to use as a dictionary is lenth10.txt -- I downloaded a dictionary, and added my own passkey to it so I could have my fun

So I type in ```
aircrack-ng -w /home/steaksauce/Documents/Dictionaries/lenth10.txt data.cap
```The first part being the path of my dictionary, the data.cap being the data packets I captured in the command beforehand. After I type that in I get ```
fopen(dictionary) failed: No such file or directory
fopen(dictionary) failed: No such file or directory
Opening data.cap
open failed: No such file or directory
Read 0 packets.

No networks found, exiting.


Quitting aircrack-ng...

```It cannot find my dictionary file or my cap file. Can I get some help with this?
Thanks in advance :)

---

### Post by steaksauce on 2011-03-09
> **steaksauce said:**
> Okay, so I'm using air-crack to crack into my network for fun. (It's WPA, **NOT** wep)

I've acquired a network handshake (I think, do I run ```
sudo airodump-ng --channel 11 --bssid 00:00:00:00:00:00 -w data mon0
``` and capture only_** four **_packets for WPA keys?)

After that, I need to run the command ```
**aircrack-ng -w wordlist capture_file**
```(where wordlist is  your dictionary file, and capture_file is a .cap file with a valid WPA  handshake)

My wordlist is in /home/steaksauce/Documents/Dictionaries/ and the particular file I want to use as a dictionary is lenth10.txt -- I downloaded a dictionary, and added my own passkey to it so I could have my fun

So I type in ```
aircrack-ng -w /home/steaksauce/Documents/Dictionaries/lenth10.txt data.cap
```The first part being the path of my dictionary, the data.cap being the data packets I captured in the command beforehand. After I type that in I get ```
fopen(dictionary) failed: No such file or directory
fopen(dictionary) failed: No such file or directory
Opening data.cap
open failed: No such file or directory
Read 0 packets.

No networks found, exiting.


Quitting aircrack-ng...

```It cannot find my dictionary file or my cap file. Can I get some help with this?
Thanks in advance :)

I done some research and fixed the no networks problem, however, I cannot acquire my own network handshake. I'm using atheros5001 (I think) and I have a broadcom4312. For the aircrack-ng suite I'm using the atheros. I tried getting a handshake by commecting and disconnecting (a few times): my broadcom card to the network, my fiances computer to the network, and another spare and still no luck. Anyone have any ideas?

---

### Post by wojox on 2011-03-09
Did you download the air-crack from their site? It's a newer more up to date version.

I use atheros on my netbook. No problem. 

I also have bcm4312 on my laptop. For that you have to go to the aircrack site and look around their forums. This is all from memory so bear with me here. For the 4312 to work you need to download the b43 driver and patch it. The instructions are on the air-crack site somewhere. 

Hope this helps some.

---

### Post by steaksauce on 2011-03-10
I'm not interested in the 4312 working with it, I can handle that.

I got in in my terminal
```
sudo apt-get install aircrack-ng
```

i just can't get my card to acquire a handshake, even after 3 other computers connecting, disconnecting, reconnecting, etc during the capture of 40k packets.

---

### Post by wojox on 2011-03-11
> **steaksauce said:**
> I'm not interested in the 4312 working with it, I can handle that.

I got in in my terminal
```
sudo apt-get install aircrack-ng
```

i just can't get my card to acquire a handshake, even after 3 other computers connecting, disconnecting, reconnecting, etc during the capture of 40k packets.

What's the version number?

---

### Post by symioun on 2011-03-24
sir,
i m trying to install aircrack-ng but it shows 
king@king-Virtual-Machine:~$ sudo apt-get install aircrack-ng
[sudo] password for king: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aircrack-ng

---

