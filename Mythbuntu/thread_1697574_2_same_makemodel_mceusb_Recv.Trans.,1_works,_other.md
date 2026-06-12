---
title: "2 same make/model mceusb Recv./Trans.,1 works, other only Recv’s"
date: 2011-03-01
forum: Mythbuntu
---

### Post by Akriss on 2011-03-01
I have two mce-usb IR receiver / transmitters (AVS Gear GP-IR02BK). One is working great for both receiving and transmitting in Mythbuntu 10.10. The other only receives. 

The only difference I see in the two is: 
When doing:

On working one.
```
~$ cat /proc/bus/input/devices
I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (1784:0008)"
P: Phys=usb-0000:00:06.0-3/input0
S: Sysfs=/devices/virtual/rc/rc0/input6
U: Uniq=
H: Handlers=kbd event6
B: EV=100003
B: KEY=fff 0 108fc326 217604100000000 0 118000 418000100001 9e968000000000 10000000
```
And ```
~$ lsusb
Bus 004 Device 003: ID 1784:0008 TopSeed Technology Corp. eHome Infrared Transceiver

```

The other that is not working for transmitting (recv’s fine). That is swapped for the working one on same computer then rebooted returns: 
```
~$ cat /proc/bus/input/devices
I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="Media Center Ed. eHome Infrared Remote Transceiver (1784:0011)"
P: Phys=usb-0000:00:04.0-5/input0
S: Sysfs=/devices/virtual/rc/rc0/input3
U: Uniq=
H: Handlers=kbd event3
B: EV=100003
B: KEY=fff 0 108fc326 217604100000000 0 118000 418000100001 9e968000000000 10000000
```
And ```
~$ lsusb
Bus 004 Device 003: ID 1784:0011 TopSeed Technology Corp.

```

I first thought the mceusb devise was faulty so I RMA it for a new one. However, the replacement is the same, and seeing that it does receive fine I do not think it's a faulty devise.

Have I encountered a (known) bug with the default LIRC install?
If so Can I Compile LIRC from the latest available from their web site (lirc-0.8.7.tar.bz2) to fix it?

Or perhaps I'm encountering something similar to this post?:
[http://ubuntuforums.org/showthread.php?t=656859](http://ubuntuforums.org/showthread.php?t=656859) .

Or can I just be that unlucky to have received two bad devises one after the other?

[COLOR="Red"]Soleved[/COLOR]
I got smart and posted on LIRC mail list and with the help from Jarod (A Lirc Dev) fixed it.

---

### Post by gsanse on 2011-03-30
Can you share the fix please, having the same problem

---

### Post by Akriss on 2011-03-31
OK,
First Jarod Wilson had me install the source code of the "V4L-DVB Device Drivers" from [_How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers_]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers").

And before actually compiling and installing I went into the V4L-DVB Device Driver directory and found the file named "mceusb.c" with in that file I found a line that refereed to my devise (1784:0011). and it had a line that looked like  "driver_info = MCE_GEN2_TX_INV" 

I changed that line to "driver_info = MCE_GEN3" . then compiled and installed. 

Now I did all that after two-three days (and 20 or so RedBulls) of reading and trying to understand  what the heck I was doing.  

And now that I am in a not so "focused" stated I can only paraphrase what I did. Because honestly I am still not sure. 

Here is another post that spawned a few days after talking with Jarod. It has more info in it then my post. [_here at "gossamer-threads"_]("http://www.gossamer-threads.com/lists/mythtv/users/475912") it may prove more helpful.

---

