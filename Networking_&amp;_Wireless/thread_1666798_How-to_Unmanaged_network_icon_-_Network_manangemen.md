---
title: "How-to: Unmanaged network icon - Network manangement disabled"
date: 2011-01-14
forum: Networking &amp; Wireless
---

### Post by limotux on 2011-01-14
Hi guys, 
 
I would like to share with you what I did to solve a problem I faced.
I suddenly found my tablet switching down. On restart I had the knetwork icon saying something like Unmanaged network icon or Network manangement disabled (still I don't know why).

In brief I found several solutions, some of them worked for some users, some didn't.
So, I think doing the following steps (or some of them)  will finally get it working, doing a step that is not really neaded will not harm I think:

1 - ```
sudo init 0
```2- change:[INDENT]   managed=false
 [/INDENT]to[INDENT]   managed=true
 [/INDENT]in /etc/NetworkManager/nm-system-settings.conf


(use sudo kedit /etc/NetworkManager/nm-system-settings.conf ) to edit the file and make the change.

3- look at the contents of the file /var/lib/NetworkManager/NetworkManager.state. It should look something like this:  [main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
 Change anything from 'false' to 'true' to re-enable networking.

(you may use use sudo kedit /var/lib/NetworkManager/NetworkManager.state )

You may need to restart knetwork manager after each step to see if it works, or after doing all steps, or restart the computer.

I hope this helps.
Let me know if it works for you or add other methods that works for you to have a unified guide that solves everything for everybody.

As well, I'll appreciate if somebody can tell why it happened by itself initially. I was only training cwriter which has nothing to do with networks!

---

