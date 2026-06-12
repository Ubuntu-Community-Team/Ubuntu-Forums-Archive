---
title: "connected to internet but i can surf da web or download apps????"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by youngunix on 2009-10-09
I've been working on installing Ubuntu on my laptop, finally i backed up everything and installed it....neway, it says that i'm connected to the internet but i can't surf the web or download nething???

---

### Post by CharlesA on 2009-10-09
Post what ifconfig returns please.

---

### Post by youngunix on 2009-10-09
i actually can't do that, since there's no internet on Ubuntu to post the ipcofig...i'm on vista now!!!

---

### Post by Shibblet on 2009-10-09
You may want to change the title to "Can't".  I read it and said, "Isn't that what he wants to do?"

---

### Post by youngunix on 2009-10-09
ma bad!! i tried to change it, but it changed only the one in the thread, how do i change all of'em???

---

### Post by youngunix on 2009-10-09
why is ubuntu acting up, connected to internet yet can't surf or download???

---

### Post by Iowan on 2009-10-10
Can you ping websites by IP address? Check contents of */etc/resolv.conf* to verify correct DNS servers.

---

### Post by callan79 on 2009-10-10
> **youngunix said:**
> why is ubuntu acting up, connected to internet yet can't surf or download???


Probably a little more info would be helpful - what type of internet connection do you have? If it's ADSL, are you doing PPPoE on your computer or on a router? What type?

Do you have an IP Address (right click network manager and choose connection information)

At terminal, can you ping to an IP address? Can you ping to a website?

For example try a ping to my site

```

ping 202.6.141.219
ping flog.cruzn.net.au

```

See what happens ...

Cheers
Callan

---

