---
title: "Help Quick- Browser Connection Issue"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by ddixonr on 2009-04-05
I lost power to my laptop in the last hour and when I rebooted, Firefox won't pull up any sites. I have a connection because I restarted some torrents and they continued downloading. I opened a couple other programs that access the internet like skype and it connected no problem. I tried Konqueror and IE6 as well and they are in the same state as firefox. 

I vnc'd to another machine on my network and it connects to the internet and every site I tried. I don't have any complicated proxy setups or anything, so I'm really stumped. Please help.

Edit: "Work Offline" is not checked. I am getting the "Address Not Found" error.

---

### Post by ddixonr on 2009-04-05
No responses in this category, but I did manage to get it working. Not sure what the problem was because 'init.d/networking restart' didn't fix it. 'ifconfig wlan0 up/down' didn't fix it. Right clicking on the nm applet in the panel and disabling networking, then restarting seemed to do the trick. Again, I don't know why, but I know the fix for next time. Hopefully someone benefits from this.

---

