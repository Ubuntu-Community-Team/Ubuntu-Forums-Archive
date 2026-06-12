---
title: "Ar5001 unable to connect"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by Dhezballah on 2011-05-12
[SIZE=2]Hi,

The problem is wireless connections show up in the connections list but when I try to connect it will just keep trying to connect and will never actually complete. During the connecting process it will constantly ask for my WPA2 key. Wired connection does work but that is only a temporary fix to this problem. The phy0 wlan hard block is stuck to yes also, so that could be the problem.
other info:
Running Ubuntu 11.04 dual boot with windows vista 32 bit
Wireless card is Atheros ar5001 on Toshiba satellite laptop

Thanks[/SIZE]

---

### Post by Dhezballah on 2011-05-13
No one has any ideas?

---

### Post by Dhezballah on 2011-05-13
Update
Hard block is now off still no connection
Wireless stuck at the connecting/authenticating phase still.

---

### Post by Dhezballah on 2011-05-13
Hmm just went across to the vista side and wireless is not working there either but I checked hardware and it said it is a ar5007 not an ar5001.
Hopefully someone can help me out.

---

### Post by np426 on 2011-05-21
Hey .. had the same problem for like two days and i went to this site 
[http://forum.ubuntu-fr.org/viewtopic.php?id=463091](http://forum.ubuntu-fr.org/viewtopic.php?id=463091)

some one named 00_00 or something figured it out really simple just have to put in 6 lines of code .. try it out .. and best of luck

---

### Post by shokalabutcha on 2011-06-14
I am using AR5001, too, and I had a similar problem. Whenever I did "rfkill unblock all", my wireless would go from 
Soft blocked: Yes
Hard blocked: No

to 

Soft blocked: No
Hard blocked: Yes

In the end, I created the following script as a (barely acceptable) solution:

sudo rmmod -f ath5k
sudo rfkill unblock all
sudo odprobe ath5k

I hope this script helps someone. If anybody knows how to make this permenant, that will be much appreciated.

I am using a Natty Narwhal, (Ubuntu 11.04) running on Fujitsu Siemens Amilo PA3515 with an Atheros AR5001 wireless module.

Hope this helps,
Shoka

---

