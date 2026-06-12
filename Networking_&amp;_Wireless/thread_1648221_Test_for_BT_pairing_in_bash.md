---
title: "Test for BT pairing in bash"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by uriel1998 on 2010-12-18
This is probably something stupid, but...

I want to test whether or not my phone is connected from bash.  I'm finding *lots* of information about /dev/rfcomm0, but that's not on my system (Ubuntu 10.04).  The device pairs just fine, and I can connect with gammu just fine, and I have the device address ("00:1F:5D:37:17:FB").  

I just need something I can put in a bash script to say "Is this connected or not" akin to testing for a file's existence:

```

if [ -f /home/steven/arbitrary filename ]
  then
    notify-send --icon=blueman "We're connected"
fi

```

Is there something simple like that?

(Note:  My phone's old enough that gammu's daemon doesn't work properly with it, which is why I'm hacking it this way.)

---

### Post by papibe on 2010-12-23
-f tests for a regular file (neither a device or a directory). Try -e to check if something's just there.

I hope it helps

---

### Post by uriel1998 on 2010-12-23
The best thing I've found so far is to use hcitool - but I'm having a bit of a problem in my bash script:

[code]
isconnected=`hcitool inq ##:##:##:##:##:## | grep ##:##:##:##:##:##`
echo $isconnected
is_digit=`test  "$isconnected" > "00"`
if [ $is_digit -ne 1 ];
                then 
                #dostuff
fi
[code]

Obviously, that's the BT address of my phone.  It correctly assigns $isconnected, but I can't get it to enter the loop properly.  ::sigh::

---

