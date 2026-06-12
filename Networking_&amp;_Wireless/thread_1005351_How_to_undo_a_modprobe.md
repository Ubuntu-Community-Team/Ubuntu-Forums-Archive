---
title: "How to undo a modprobe ?"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-12-08
I was trying to fix a wireless problem (USB related), and saw a post on these forums about using modprobe, so did these 2 commands

```
# sudo modprobe -r uhci-hcd
# sudo modprobe uhci-hcd
```

Now the whole networking doesn't work at all, so how can I 'undo the changes made by modprobe please ?

I had a look in the blacklist file, but uhci-hcd is not there ?

---

### Post by lovelyvik293 on 2008-12-08
Just use the modprobe again to install that driver.

---

### Post by oygle on 2008-12-08
> **lovelyvik293 said:**
> Just use the modprobe again to install that driver.

Can you please supply the command to do that.  :)

---

### Post by gTinker on 2008-12-08
[QUOTE=oygle]
```
# sudo modprobe -r uhci-hcd
# sudo modprobe uhci-hcd
```

Now the whole networking doesn't work at all, so how can I 'undo the changes made by modprobe please ?
[/QUOTE]

Look carefully at what you did with those commands. First you removed the module uhci-hcd and the second one put the module back. What is it you were trying to do? Are you sure you understood the instructions that you were following? What problem were you trying to fix? Tell us the post you referred to so we can confirm that it applies to your issue. 

If you type, man modprobe, into a terminal it will show you the manual for the modprobe command and you should probably read and understand about any commands you are going to use before you try them, that would be my advice.

---

### Post by kevdog on 2008-12-08
modprobe -r <modname>
rmmod <modname>

The statements are the same.  They both unload the module.

---

### Post by oygle on 2008-12-08
> **gTinker said:**
> Look carefully at what you did with those commands. First you removed the module uhci-hcd and the second one put the module back.

Okay thanks, so the module is still there. I have networking problems soon after, and assumed those commands have stopped all networking, but possibly some other factor.

> **gTinker said:**
> 
What is it you were trying to do? Are you sure you understood the instructions that you were following? What problem were you trying to fix? Tell us the post you referred to so we can confirm that it applies to your issue.

It was related to trying to get a USB wireless going. The post was either on these forums or somewhere else, i have tried to find it agan, but no luck. In short, the commands were suggested for someone trying to find USB devices, for example /dev/ttyUSB0, etc.  After I did those 2 commands, I was finally able to 'see' that device. However, now I have no network on that computer. It was using the LAN to use a shared internet connection. It has worked for a few weeks without a problem, and now it is dead.

I did have to change the network manager settings, and that may have caused the network problem. No messages in sstem log though, as to why the network is not working.

---

### Post by gTinker on 2008-12-08
[QUOTE=oygle]
 However, now I have no network on that computer. It was using the LAN to use a shared internet connection. It has worked for a few weeks without a problem, and now it is dead.

I did have to change the network manager settings, and that may have caused the network problem. No messages in sstem log though, as to why the network is not working.[/QUOTE]

Did you try restarting the networking after you did the modprobe?
sudo /etc/init.d/networking restart

What might help is to tell us what changes you made to the network manager. And, if it was working, what caused you to make those changes.

Is your network card 'up'? What are the results when you type ifconfig -a in a terminal?

---

### Post by oygle on 2008-12-11
> **gTinker said:**
> Did you try restarting the networking after you did the modprobe?
sudo /etc/init.d/networking restart


Got a msg like 'reconfiguring network interfaces, and an 'okay', but still no internet connection (it was working before).

> **gTinker said:**
> 
Is your network card 'up'? What are the results when you type ifconfig -a in a terminal?

I have no way of posting the results, as it's on another computer with no internet connection, but that command supplied a fair bit of info back for 'etho' and 'lo'

---

### Post by Ayuthia on 2008-12-11
Just some additional information--modprobe commands only work for the current session.  Once you reboot, the modules will come back.

---

