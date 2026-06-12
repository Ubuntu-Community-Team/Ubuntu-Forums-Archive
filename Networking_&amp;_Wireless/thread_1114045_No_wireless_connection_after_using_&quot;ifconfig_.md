---
title: "No wireless connection after using &quot;ifconfig wlan0 down&quot;"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by ashour on 2009-04-02
Hi

i got ralink rt61
and to user aircrack i had to bring my interface down using 
"sudo ifconfig wlan0 down" and wireless connection goes of however i just restarted and everthing always got back to normal
now i redone the process but still it can't even connect to the wireless connection.

i tried "sudo ifconfig wlan0 up"
but it didn't work.

---

### Post by coutts99 on 2009-04-02
Maybe -

sudo dhclient wlan0

??

---

### Post by superprash2003 on 2009-04-02
post output of ifconfig from the terminal..also type **sudo /etc/init.d/networking restart**

---

### Post by chili555 on 2009-04-02
> **ashour said:**
> Hi

i got ralink rt61
and to user aircrack i had to bring my interface down using 
"sudo ifconfig wlan0 down" and wireless connection goes of however i just restarted and everthing always got back to normal
now i redone the process but still it can't even connect to the wireless connection.

i tried "sudo ifconfig wlan0 up"
but it didn't work.When you did aircrack, did you have to put your card in 'monitor' mode? I suggest the following sequence:```
sudo ifdown wlan0
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0
```Now does your internet connectivity return?

---

### Post by ashour on 2009-04-02
the first 2 replies got the internet back but after using aircrack i can't get it back again

sudo ifdown wlan0 tells me:
Ignoring unknown interface wlan0=wlan0.

---

### Post by ashour on 2009-04-03
any help?

---

### Post by chili555 on 2009-04-03
> the first 2 replies got the internet backI am sorry; I don't understand this. Do you mean that you applied the first two replies to your forum post or the first two commands I suggested?

May I assume that when you were using aircrack you had to put your card in *monitor* mode? I think that's why you cannot access the internet, because the card needs to be in *managed *mode. On most cards, the solution is to take the interface, wlan0, down, change the mode to managed and bring it back up.

Even though you got an error, did you proceed with the other steps?

---

### Post by ashour on 2009-04-05
> **chili555 said:**
> I am sorry; I don't understand this. Do you mean that you applied the first two replies to your forum post or the first two commands I suggested?

May I assume that when you were using aircrack you had to put your card in *monitor* mode? I think that's why you cannot access the internet, because the card needs to be in *managed *mode. On most cards, the solution is to take the interface, wlan0, down, change the mode to managed and bring it back up.

Even though you got an error, did you proceed with the other steps?
i mean that the commands suggested got the internet just back after using
sudo ifconfig wlan0 down

but not after using aircrack.

---

### Post by ashour on 2009-04-07
i even now restart and i can't get internet at all on kubuntu
Guys any help i really need to fix that.

---

