---
title: "How to turn on another computer on the network"
date: 2012-11-03
forum: Networking &amp; Wireless
---

### Post by honeybear on 2012-11-03
Hello people, i have something in mind that i want to share with you and hopefully get some new opinions..

I would like to check if nmap -sP tells that the ip of the pc is there or not.

WIth crontab, at a specific time, ask the server to send a command to turn on this another linux station.

Would you know how ?

thanks

---

### Post by honeybear on 2012-11-03
I have found this solution.

with updating the grub
[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)


is there a solution with bash and not updating the grub??

---

### Post by honeybear on 2012-11-03
[HTML]```
wakeonlan  x:xx:xx:x:x:x
Sending magic packet to 255.255.255.255:x with x:x:x:x:x:x
```[/HTML]


it works. does i need to install wakeonlan on the machine that needs to be awaken?

---

### Post by jonnyboysmithy on 2012-11-03
Not sure. Some bioses have a wake up on lan option. That should work to make it boot. To come out of suspend I think the machine will need to have the correct software. I might be wrong though. just my 2 cents..

---

### Post by honeybear on 2012-11-03
> **jonnyboysmithy said:**
> Not sure. Some bioses have a wake up on lan option. That should work to make it boot. To come out of suspend I think the machine will need to have the correct software. I might be wrong though. just my 2 cents..

ethtool eth0 tells you if you bios have the wol

my has not :( too bad

---

