---
title: "Siemens sx763 wlan problem"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by usernamenotfound on 2012-10-28
Greetings from Croatia.
I've installed Ubuntu 12.10 a couple days ago.
I can connect to my router, but I can't browse the interwebz. 
When I had windows, I've connected via pppoe broadband connection, but that option is not possible in ubuntu, I guess.

So, if there is a solution, I would be grateful because I need my laptop for school.

Bye, Matej

---

### Post by chili555 on 2012-10-28
> When I had windows, I've connected via pppoe broadband connection, but that option is not possible in ubuntu, I guess.I believe it is. In my own case, I find it preferable to set up the username/password authentication in the router, however, it can be configured in Network Manager. Right-click the icon and select Edit Connections. Click DSL > Add and set your details there. Please see attached.

---

### Post by chili555 on 2012-10-28
Here is an example PPPoE setup page from my router in case you'd prefer it, as I recommend.

---

### Post by usernamenotfound on 2012-10-28
> **chili555 said:**
> I believe it is. In my own case, I find it preferable to set up the username/password authentication in the router, however, it can be configured in Network Manager. Right-click the icon and select Edit Connections. Click DSL > Add and set your details there. Please see attached.

Should I reboot afterwards?

---

### Post by chili555 on 2012-10-28
You can probably simply ask NM to disconnect and reconnect, but if that doesn't do it, then reboot. Please see attached.

---

### Post by usernamenotfound on 2012-10-28
> **chili555 said:**
> You can probably simply ask NM to disconnect and reconnect, but if that doesn't do it, then reboot. Please see attached.

I've added the DSL, disconnected, now is reconnecting, and I'll add my user and pass in my router.
I hope that'll work :)

---

### Post by usernamenotfound on 2012-10-28
> **usernamenotfound said:**
> I've added the DSL, disconnected, now is reconnecting, and I'll add my user and pass in my router.
I hope that'll work :)

OK, so I've added the dsl on my laptop. entered username and password. reconnected wireless. rebooted my router.

didn't work.

---

### Post by chili555 on 2012-10-28
Be certain you have the username/password in either the computer or the router but not both. As I said, in my case, the router is preferable and works perfectly.

---

### Post by usernamenotfound on 2012-10-28
> **chili555 said:**
> Be certain you have the username/password in either the computer or the router but not both. As I said, in my case, the router is preferable and works perfectly.

So, when I add my username/password in my router, should I delete the dsl on NM?

---

### Post by chili555 on 2012-10-28
> **usernamenotfound said:**
> So, when I add my username/password in my router, should I delete the dsl on NM?Correct.

---

### Post by usernamenotfound on 2012-10-28
> **chili555 said:**
> Correct.

I've contacted my internet provider so they can patch those silly settings, the router has gone wild!

---

### Post by usernamenotfound on 2012-10-29
> **chili555 said:**
> Correct.

OK, so I've factory reseted my router, deleted dsl connection, tried 'sudo pppoeconf' and there was the message: pppoe is already used in your modem (I believe this computer is the one) so now I'm running command 'sudo pppoeconf wlan1' so we shall see.

---

