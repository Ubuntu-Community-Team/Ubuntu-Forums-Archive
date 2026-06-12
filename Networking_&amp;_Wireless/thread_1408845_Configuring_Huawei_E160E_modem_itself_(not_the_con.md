---
title: "Configuring Huawei E160E modem itself (not the connection)"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by JiVi on 2010-02-16
Hi all, I wasn't able to find anything else than posts regarding connection problems, so decided to write a new one.

I have a Huawei E160E, and I'm experiencing problems with Optus network in Australia. The modem always works when using GPRS but in some places it fails after authentication when using 3G connections. (More info here: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/1297363.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1297363.html))

So this means, that depending on my location I have to configure the modem to use only GPRS or also UMTS/HSDPA. This is easily done with Virgin's own software, but it's not available for Linux (surprising ... not). So is there a way to configure the modem with Ubuntu? Terminal hacks are ok, it doesn't have to be a polished GUI app (though there's nothing wrong with a good GUI app either).

edit: to clarify, the purpose is to change settings inside the modem, not within Ubuntu

Thanks,

 - J

---

### Post by GeorgeVita on 2010-02-17
Hi **JiVi**,
from my 'old' post: [http://ubuntuforums.org/showpost.php?p=7771722&postcount=3](http://ubuntuforums.org/showpost.php?p=7771722&postcount=3)

When you know the modem com port (ex. /dev/ttyUSB0) send the command manually from terminal BEFORE connection to network:
```
echo 'AT^SYSCFG=14,2,3FFFFFFF,2,4' > /dev/ttyUSB0
``` ```
echo 'AT^SYSCFG=13,1,3FFFFFFF,2,4' > /dev/ttyUSB0
``` First example is '3G only' and second 'GPRS only'.

Although above could work for you, ASK your provider why this problem appears!

Regards,
George

---

### Post by JiVi on 2010-02-17
> **GeorgeVita said:**
> Hi **JiVi**,
from my 'old' post: [http://ubuntuforums.org/showpost.php?p=7771722&postcount=3](http://ubuntuforums.org/showpost.php?p=7771722&postcount=3)


Hi George,

Thanks for the tip, but unfortunately it didn't work. At least not yet. I'll try to google around with that command to see if I can find any additional info. It might be helpful, if you could provide me with the original source of that command.

And I've been in contact with Virgin Mobile's support, and I just asked them to contact Optus and check whether the network problem (check the link in my original post) could be fixed. Let's see what they can do.

Cheers,
 -J

---

### Post by JiVi on 2010-02-18
> **JiVi said:**
> Hi George,

Thanks for the tip, but unfortunately it didn't work. At least not yet. I'll try to google around with that command to see if I can find any additional info. It might be helpful, if you could provide me with the original source of that command.

And I've been in contact with Virgin Mobile's support, and I just asked them to contact Optus and check whether the network problem (check the link in my original post) could be fixed. Let's see what they can do.

Cheers,
 -J

Never mind, I already found quite a lot of info myself. And I got the command working with minicom, I think there was a problem with baudrates with that plain terminal command.

Now if Optus just got the 3G working...

Cheers,
-J

---

### Post by GeorgeVita on 2010-02-18
Hi **JiVi**,
so AT commands are OK but didNOT worked for your modem with the echo command. Possibly the port was not initialized before or the 'auto baudrate' function of the modem missed some characters.

As manufacturers do not supply info, these commands found somewhere at forum.huawei.com (I do not remember exactly).

Regards,
George

---

