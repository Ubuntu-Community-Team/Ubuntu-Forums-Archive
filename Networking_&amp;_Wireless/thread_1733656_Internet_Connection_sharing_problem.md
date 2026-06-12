---
title: "Internet Connection sharing problem"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by MrVga on 2011-04-19
Hello there,
I'm currently using an Intel atom with wifi and got internet access and i want to share it through the lan port to a router but i got a problem
as a first stage I try to share it to my laptop but in vain
I have dhcp the wifi settings and the lan settings "shared to other computers" and i turn off the firewall.
the wifi ip is 192.168.10.1 gateway 192.168.10.254 and also the dns
the lan ip is 10.42.43.1
at my laptop (windows 7)i have ip auto and get ip 10.42.43.10 and gateway 10.42.43.1 and the dns the same
I can ping one another but i don't have internet access at my laptop (can't ping anything outside my local network)
What do you think is the problem?
thanks in advance

---

### Post by Fire_Chief on 2011-04-19
I think you want to set the "share to other computers" setting on the wifi connection instead of the LAN connection.

Have a look at this article for more details.
[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

Cheers!

---

### Post by MrVga on 2011-04-19
> **Fire_Chief said:**
> I think you want to set the "share to other computers" setting on the wifi connection instead of the LAN connection.

Have a look at this article for more details.
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Cheers!
thank you for your answer
unfortunately this is not a solution
if you put "share to other computers" to the wifi I loose my internet connection
(i have this as a reference)somehow the wifi doesn't link with the lan port and i can't get the gateway properly at the laptop i guess:confused:

---

### Post by MrVga on 2011-04-19
problem solved
a dhcp or a static ip at the wifi and a manual at the lan ex. 192.168.0.1 without gateway
and i used firestarter and i checked the internet share from it's settings
and then putted manual ip to my laptop 192.168.0.10 with gateway 192.168.0.1 and dns the internet dns(the dns that uses the wifi)
and everything works fine:popcorn:

---

### Post by worldhello on 2011-04-20
Interesting:  sounds like you might have the answer to my question   [http://ubuntuforums.org/showthread.php?t=1733059](http://ubuntuforums.org/showthread.php?t=1733059)   
   Could you elaborate the details for newbies like me, please? THANKS!  > **MrVga said:**
> problem solved
a dhcp or a static ip at the wifi and a manual at the lan ex. 192.168.0.1 without gateway
and i used firestarter and i checked the internet share from it's settings
and then putted manual ip to my laptop 192.168.0.10 with gateway 192.168.0.1 and dns the internet dns(the dns that uses the wifi)
and everything works fine:popcorn:

---

