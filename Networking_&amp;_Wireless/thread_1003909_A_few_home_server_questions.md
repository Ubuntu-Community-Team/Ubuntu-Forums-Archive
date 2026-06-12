---
title: "A few home server questions"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by z.s.tar.gz on 2008-12-06
3 questions:

1. I have a better modem/router to replace my modem. However, every time I connect it, I can't connect to the internet or anything. Any ideas?

2. I have a dhcp line with 4 computers on it, one being a server. I would like to have 3 comps dhcp and one static. Can that be done?
If so, how?

3. Do you think I should use 8.04 or 8.10 server edition? I haven't tried 8.10 yet.

---

### Post by nickdbliss on 2008-12-06
> **z.s.tar.gz said:**
> 3 questions:

1. I have a better modem/router to replace my modem. However, every time I connect it, I can't connect to the internet or anything. Any ideas?

2. I have a dhcp line with 4 computers on it, one being a server. I would like to have 3 comps dhcp and one static. Can that be done?
If so, how?

3. Do you think I should use 8.04 or 8.10 server edition? I haven't tried 8.10 yet.

1. Does its DHCP server works? It might not be assigning IP addresses right. Which connection do u use? DSL or Cable?
2. Yes you can do it. There is an option called Static DHCP. i use it for my laptop. But i am not sure if it is provided by ur router. i use Dlink DI-524 router.
3. I tried 8.04 not sure about 8.10. But like they say, whatever works for you just stick to it.

---

### Post by superprash2003 on 2008-12-07
1)You need to configure your new router if you are using DSL . just connecting wont help
2)Yes you can insert static ip.. you havent mentioned if the pc for which you need static ip is a ubuntu or a windows machine!!
3)8.04 is LTS so better support..

---

### Post by LeadFingers on 2008-12-07
If you're using a cable modem you need to call your ISP and give them the MAC address of your new modem. usually found on the bottom of the modem. until you do that it won't work.

---

### Post by Iowan on 2008-12-08
1. No experience, so no comment.
2. If you have access to DHCP server, it's not difficult. (Access is really only necessary to learn lease range - or to set up static lease).
3. I'd opt for the _L_ong _T_erm _S_upport... 8.04

---

