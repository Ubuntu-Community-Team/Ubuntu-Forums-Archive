---
title: "Wireless connection falling at 11 Mb/s"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by kounabi on 2009-12-07
Hey!

As you see in my title I try to connect to my wireless network. Everything looks fine but in Network manager says that the rate is 11Mb/s....Even if I try to fix with the command:

```
iwconfig wlan0 rate 54M fixed
```It changes at 54Mb/s but only for a couple of seconds.
This results to transferring files at around 500KB/s which sucks....

For any information please ask

---

### Post by teward on 2009-12-07
Why are you trying to reset the transfer rate?

Just a note:  The advertised transfer rates you get are never the actual speeds you get.  The 11 Mb/s is based on your distance from the router, signal strength, noise level, etc, etc, etc.  And Mb means mega-bit, which is 1,000,000 bits.  This is NOT the same as a megabyte, which is approx. 8,000,000 bits.

I'm on a Wireless N network, with a supposed transfer rate of 54 Mb/s, and I get approx. 32 Mb/s, yet on a good day I can get 1.5 MB (megabyte) per second transfer rates because the network I use is connected to a super-bandwidth internet connection.  (I'm at a University, so go figure)

---

### Post by kounabi on 2009-12-07
thanks for the information but I already know the difference between bits and bytes...

I know that the connection rate is not accurate but file transfer between computers of the same network at 500KB/s is unacceptable...

So this is what I'm trying to fix!!

I don't care what it says about the rate in network manager if file transfer rates are good enough...

---

### Post by kounabi on 2009-12-07
ok here 's some more information...

when I start a file transfer with the connection rate being at 54Mbps the transfer rate is at 1.1MBps.Then the connection rate suddenly decreases to 11Mbps and the file transfer rate is limited to 500KBps
The connection rate keeps playing between 54 and 11 Mbps and so does the transfer rate....

Can someone explain why this happens?

---

### Post by kounabi on 2009-12-07
Ok i think I found a solution by using the following command
```
iwconfig wlan0 sens SOMETHING
```
But when i run this command I get the following error
```
Error for wireless request "Set Sensitivity" (8B08) :
    SET failed on device wlan0 ; Operation not supported.
```
Why is that happening?

Anyone please.....

---

