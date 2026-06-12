---
title: "Interesting problem"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by regdabs on 2009-09-30
I got my wireless working yesterday (yea) and it worked fine all afternoon.  Today I tried to get online again.  I am in the family room, have 4 bars on the signal strength meter (80%) and when I tried to open any site I get the message "address cannot be found". Can't get on anything.  If I carry the computer into the room where the router is the meter goes to 5 bars (100%) and everything works fine.  If I go back to the family room and turn off Ubuntu and open Vista (4 bars again_) everything works fine again.  Any one have this problem and do you have any comments, suggestion.  Surely the one bar on the signal meter would not make that much difference.  I have run with less than 4 bars before and everything woked.

---

### Post by diafanos on 2009-09-30
I had a similar problem. I think it's a known bug or at least a known issue with a specific type of wifi adapters. 

Running the folowing command may solve the problem
```

sudo iwconfig ath0 rate 5.5M

```

Replace *ath0* with the name of your wireless adapter.

Run 
```

iwconfig

```

to find out its name, if you don't know it.

---

### Post by regdabs on 2009-09-30
Here is what I get when I run iwconfig:


carl@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:231  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

carl@ubuntu:~$ 

What is this telling me?

---

### Post by regdabs on 2009-09-30
This is what I get when I run iwconfig




carl@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:231  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

carl@ubuntu:~$

---

### Post by diafanos on 2009-10-01
then probably your wireless interface is named "eth1"
Try running the command:

```

sudo iwconfig eth1 rate 5.5M

```

---

