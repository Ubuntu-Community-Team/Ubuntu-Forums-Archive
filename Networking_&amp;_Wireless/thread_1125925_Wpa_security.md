---
title: "Wpa security"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by Trafficflow on 2009-04-14
Can anybody give me a link for how to configure WPA2? Thats all I need.

---

### Post by t0mppa on 2009-04-14
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9002706]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9002706")

First hit from Google with keywords WPA & 2. :)

Really, there isn't much of a setup to do. Hardest part is probably finding out how to access your routers configuration and that depends on the model of your router, usually it's done by putting the router's IP address on the browser, hitting go and signing in though.

If you want a router specific line by line guidance through the configuration part, then you'll have to know what kind of a router you have.

On the Ubuntu end, it's really simple, just pick WPA2 from the dropdown, when it asks for authentication and type in the password you put on the routers configuration.

---

### Post by Trafficflow on 2009-04-15
I know how to configure WPA-2 in my router that is easy, The whole problem is there is no WPA to pick from in the dropdown.You have to install some type of supplicant and install. That what I need

---

### Post by wkulecz on 2009-04-15
While not Ubuntu specific, I'm finding issues with the maximum Pass Phrase length among different hardware and had to go re-enter everything once already when a new device wouldn't accept the current pass phrase key :(

Is there a spec that gives the maximum length of the pass phrase a device must accept?  

Unfortunately not all Linux wireless drivers support enhanced security modes at present, which is probably why your device lacks the WPA or WPA2 selection.

I thought the supplicant was to do PPPoE to a DSL modem without a router in between.  I'd welcome clarification.

--wally.

---

### Post by Trafficflow on 2009-04-15
Is previous statement correct? I found a few threads that sound like there is a configuration. Which is correct?

---

### Post by wkulecz on 2009-04-16
As I understand it, the various security options are supported or not in the wireless driver.  Its possible there is a package that impliments a "universal" wireless security layer the driver could use, but for what wireless I've got to work on Linux, the security options available depended on the driver installed, and no extra packages appear to get downloaded.

I gave up on this stuff when I upgraded to draft-N.  I got a Linksys WGA600N "gamming adaptor", programmed it on XP and then moved it to my wife's Ubuntu box where it connects to the wired ethernet port.  Ubuntu thinks is on a wired DHCP network.  The WGA box's firmware handles all the wireless security and connection stuff.  About as pain free as it gets, and if you have issues you get the full manufacturer's support since you are setting up the WGA on windows.

--wally.

---

### Post by t0mppa on 2009-04-17
Oh sorry, assumed it was something relatively simple by the length of the problem description.

And yes, I do remember reading posts about some Wireless drivers only supporting WEP. Never paid that much attention to it, since in a way, I guess I was lucky by having an Atheros chip that had native drivers for it, which do support WPA.

---

### Post by wkulecz on 2009-04-17
This is the device I'm talking about:

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175239647577&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4757724212B05](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175239647577&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4757724212B05)

Maybe someday the WiFi drivers for Linux will be there and just work, but untill that day comes I'll avoid the pain and use these wired to wireless converters.  

The only place this won't work is if you need full mobility WiFi running only on battery power as this box needs its own AC adaptor.  For me this mode has never been anything more than a toy even on XP as battery life is too short for most all my needs and adding a WiFi connection shortens it further.

--wally.

---

