---
title: "Bluetooth and Bitpim"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by ashkev on 2009-06-25
I am on 9.04 using bitpim 1.0.6

Hello, I have been trying to get my Samsung Propel to work with Bluetooth and Bitpim.  I have the phone connected to the laptop with Blueman, but I can't seem to connect with PIM.  

I have the COM port set to /dev/rfcomm0.  At first, I couldn't connect to this port because of a permission problem.  I reset the permission, but the directory appears to be empty....

I tried following [this ]("http://ubuntuforums.org/showthread.php?t=885765&highlight=bitpim+bluetooth") tutorial, but when I get to this part: 
Now run
Code:

```
rfcomm connect 0 ##:##:##:##:##:## ??
```

where ?? is the channel number.

I get this:
```
kevin@kevin-laptop:~$ rfcomm connect 0 00:24:91:12:CC:9E 7
Can't connect RFCOMM socket: Connection refused
kevin@kevin-laptop:~$ 

```

As I said, the phone and the laptop are connected.  I can browse files on the phone from the laptop and vise versa, but the command line pairing seems to fail.

Any ideas?

Thanks,

Kevin

---

### Post by mjbauer95 on 2009-07-29
Did hcitool auth work for you? It looks like there is some kind of permission problem. I've also got problems when connecting to my phone via bluetooth.

---

