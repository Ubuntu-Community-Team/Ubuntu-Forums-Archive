---
title: "Wireless noise ?"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by akernan on 2011-04-10
I've noticed a significant difference in wireless noise level between Natty and Mint 10, which is based on Ubuntu.  My Natty is using kernel 2.6.38 and Mint 10 is using kernel 2.6.35.  Natty has a signal level about -55 and Mint 10 shows -90.  Both are on the same system, the only thing that is different is the drives.  Why the difference?

---

### Post by akernan on 2011-04-11
Any ideas?

---

### Post by 5149.5 on 2011-04-11
I am pretty sure that the signal levels aren't really being reported correctly. The -90dBm level probably wouldn't work at all. I have no idea where the inaccuracy is coming from. I don't know if the signal level is recoded in any of the system logs. Where are you seeing those levels?

---

### Post by akernan on 2011-04-11
> **5149.5 said:**
> I am pretty sure that the signal levels aren't really being reported correctly. The -90dBm level probably wouldn't work at all. I have no idea where the inaccuracy is coming from. I don't know if the signal level is recoded in any of the system logs. Where are you seeing those levels?

They levels are in /proc/net/wireless.  I have problem with the -90dbm level.  Here is the /proc/net/wireless on Mint 10 ..

```
tony@tony-Inspiron-1564:~$ cat /proc/net/wireless 
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
  eth1: 0000    5.  -54.  -90.       0      0      0     58      0        0

```

---

### Post by 5149.5 on 2011-04-11
I just booted Win 7 and my Natty signal level is really close to the Win 7 level for whatever that is worth. I thought your -90 level was a signal level. Your -54 signal with -90 noise level isn't too bad.

---

### Post by akernan on 2011-04-11
> **5149.5 said:**
> I just booted Win 7 and my Natty signal level is really close to the Win 7 level for whatever that is worth. I thought your -90 level was a signal level. Your -54 signal with -90 noise level isn't too bad.

Sorry, my first post was confusing.

My question is why the difference for noise level?  Nothing is changed except booting to a different OS.

Here is /proc/net/wireless for Mint 10...

```
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
  eth1: 0000    5.  -56.  -90.       0      0      0    135      0        0

```

Here is /proc/net/wireless for Natty...

```
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
  eth1: 0000    4.  -58.  -57.       0      0      0      0      0        0

```

---

### Post by 5149.5 on 2011-04-12
Check the channels/frequencies used by the two OSs. If they are using different channels  then the noise might be coming from a neighbors wlan.

---

### Post by akernan on 2011-04-12
> **5149.5 said:**
> Check the channels/frequencies used by the two OSs. If they are using different channels  then the noise might be coming from a neighbors wlan.

Both use channel 7 & freq 2.442 GHz.  I've run iwlist on both and it shows noise about -90dbm, but /proc/net/wireless on Natty shows noise about -57dbm.  Why the big difference between iwlist and /proc/net/wireless on Natty?

```
tony@tony-Inspiron-1564:~$ cat /proc/net/wireless 
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
  eth1: 0000    5.  -54.  -57.       0      0      0      0      0        0
tony@tony-Inspiron-1564:~$ 
tony@tony-Inspiron-1564:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:18:39:89:20:E0
                    ESSID:"home-net"
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:5/5  Signal level:-55 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

```

---

### Post by 5149.5 on 2011-04-12
> **akernan said:**
> Both use channel 7 & freq 2.442 GHz.  I've run iwlist on both and it shows noise about -90dbm, but /proc/net/wireless on Natty shows noise about -57dbm.  Why the big difference between iwlist and /proc/net/wireless on Natty?


I'm not sure. My first guess would be that the information in /proc/net/wireless was written at some point in the past. I would be more concerned about the iwlist levels where the noise almost equals the signal level. 

When i scanned my local wlan environment I noticed that most of the APs were stacked up around channel 6. I set my AP for channel 12 because it had the least traffic on it.

---

### Post by akernan on 2011-04-12
I'm too worried about it, everything seems to be working good now.  Thanks for the replies.

---

