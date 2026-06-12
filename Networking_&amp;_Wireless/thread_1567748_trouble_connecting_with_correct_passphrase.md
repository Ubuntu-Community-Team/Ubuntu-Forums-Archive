---
title: "trouble connecting with correct passphrase"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by MahBumble on 2010-09-04
Hi all,

I'm having trouble connecting to a wireless network! Have spent the last couple of weeks using the resources here to get ndiswrapper working and to get the wireless recognised. Now I've stumbled onto a less well-covered problem, and was hoping someone may be able to help. 

First off I wrote a post with all the answers to the  'HOWTO post a Wireless issue (ticket)' points, however I think I've ID'd the problem, and didn't want to start a thread with a very large post of terminal output (unsure which sections are relevant and which aren't).

Ndiswrapper seems to be functioning fine - I can see the wireless networks in the area and try to connect to mine, however when I type the wirless password it tries to connect, then after a 60ish second delay, asks me for the password again. I've got the correct password, and have tried the command

```

tholiver@spoff:~$ iwconfig wlan0 key 'my passphrase'

```however, I get out:
```

Error for wireless request "Set Encode" (8B2A) :
    invalid argument "my passphrase".

```This is the output of iwconfig:

```

tholiver@spoff:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"considerably faster than thou"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Thanks
MahB

---

