---
title: "setting up linksys WRT54gl router"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by NewbuntuUser777 on 2009-04-30
New to linux and never networked any two computers before so this is probably stupid.

I just got a router and I want to setup a network between an ubuntu desktop (still on 8.10) and an ubuntu LAMP server (I want to learn LAMP).

I still have an old Vista partition on the ubuntu desktop machine.  Should I run the linksys CD on that and hope that the settings will carry over to the ubuntu partition?

I'm concerned with securing the router since it's wireless even though I'm not using the wireless right now.

Oh, and I'm also a little bit concerned about having the LAMP server connected to the internet.  For now I just want to be able to access it from the other machine for learning purposes.

Any advice on where to start?

Thanks!
Dan

---

### Post by chili555 on 2009-05-01
> New to linux and never networked any two computers beforeNo worries. We were all new once.> I still have an old Vista partition on the ubuntu desktop machine. Should I run the linksys CD on that and hope that the settings will carry over to the ubuntu partition?When you run the CD, it just allows you fast and easy access to the administration pages of the router. As far as I know, there is nothing that is done to your Windows setup that needs to be replicated on Ubuntu. It simply allow you to set up wireless encryption, WPA, hopefully, determine how many DHCP addresses the router hands out, change the name of the router from 'linksys' to something else to make it easier to identify as yours in a crowded wireless environment, such as 'chilisHome.' This can all be done without the CD from Ubuntu. I was messing around with my ancient WRT54G just yesterday using Ubuntu only.> I'm concerned with securing the router since it's wireless even though I'm not using the wireless right now.Until you do use wireless, there is no need to set up encryption. There is an option to disable wireless!> I'm also a little bit concerned about having the LAMP server connected to the internet.It will not be visible from the internet unless you take several steps to do so. It's actually not particularly easy to do so, even if you are trying! One thing that makes it very difficult is that your internet service provider usually allows you to connect by DHCP, that is, an ever changing IP address, such as 68.137.88.9. Next week, it might be 68.137.90.27. *IF* someone guesses that number, unless the router is set up to pass incoming traffic to an internal address, 192.168.1.108, for example, there is no way to get through.

Your router is like a hotel manager. Hacker: "Please tell me the room number for Mr. LAMP." Manager: "Sorry, sir, we can't give out that information and we can't confirm or deny that Mr. LAMP is even registered here."

Post back if we can help further.

---

