---
title: "Please help, wifi won't work after installation"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by seekingelysium on 2010-12-17
Ok, so I recently installed ubuntu and I like it, but my family members are complaining because now their computers can't connect to the wifi. We have two pc's and a laptop at our house. My computer is the main computer. It has the internet modem, and the linksys WRT54G router connected to it. My internet works fine, but now that I've installed ubuntu the other pc and the laptop cannot access the wifi anymore. Also I've tried putting the linksys installation cd into my computer to see if I can re-install the router and setup the wifi network again, but ubuntu says that it can't auto-run the cd.

Please help

---

### Post by garvinrick4 on 2010-12-17
Using another OS does not effect the router for other computers. From what I gather you are wired and they are wireless. Same name and password did you change security in router or something like that for wireless the wpa and wep. Ubuntu uses different driver but just for machine in use with Ubuntu not in router. Had to change wireless settings in router.

---

### Post by corncob on 2010-12-17
I too don't see what installing Ubuntu in your computer has to do with the other two.  Anyway, you should be able to access your router without the CD.  On my Netgear router the URL is [http://www.routerlogin.net](http://www.routerlogin.net) or [http://192.168.1.94](http://192.168.1.94) with a log in username of "admin" and a password of "password" (default settings).  See what your package insert says or go to the manufacturer's website.  When I had a Linksys router the username was "linksys" and the password was "admin" and I got the IP address by running
```
ifconfig
```

---

### Post by seekingelysium on 2010-12-17
Thanks for replying so quickly. To tell the truth, I think I installed ubuntu last Friday and everything worked fine until Monday, so it may not have anything to do with ubuntu. I typed in ifconfig and got the ip address but when I put the ip address into firefox it wouldn't display the page. Another weird thing is that for some reason the network name got changed. It was cread and now its linksys something. I don't know if this has something to do with the warranty running out last month and them somehow programming there machines to mess up so that I have to sign up and pay for more tech support or what because it doesn't make any sense that it would just stop working.

---

### Post by corncob on 2010-12-18
'linksys", at least in the past, was the default SSID for their routers (with a password of 'admin').  Sounds like yours got reset to the factory settings.  Truthfully, I have trouble with ifconfig too but the linksys website should have the router manual with the URL of the router where you can log on and change things back.  Was there any lightening last Monday?  Is there an on/off button for wireless on the router that somehow got itself turned off?  Did you try rebooting the modem along with the router?

---

### Post by gordintoronto on 2010-12-18
If you can't find your manual, it's easy to download. Just Google: wrt54g manual
and there it is.

You don't need the setup CD, you can completely configure the router from your web browser. Just connect to 192.168.1.1 and enter admin and admin as the userid and password. The first thing you should do is change that password. Then change the SSID, specify an encryption type (perhaps this router only allows WEP, which is not very secure) and a password. You probably want to make those what they used to be before the router got reset.

The reset was done by a person in your home, and had nothing to do with Linksys or your warranty.

---

### Post by corncob on 2010-12-18
I started following this thread because I was having a similar problem.  I finally ended up following my own advice and pulling the plugs on both the router and the modem at the same time.  Now the wireless is working again.  I shouldn't talk too soon though -- my wife hasn't fired up her Windows machine which seemed to have started the problem :p.

---

### Post by dutchgirl on 2010-12-18
This is starting to sound like someone connected to your router and played a few games. Such as, changing the router name and or changing you serial key or mac address list. If you are unable to connect to your router through explorer: 192.168.1.1 or what ever you have it set too, try reseting your router to default with the reset switch. On my netgear the default login is user: admin 
                              password: password
other models vary. For example my linksys was admin for the user name, but the password field left blank. Definitely sounds like someone had a little fun with you. :p

---

### Post by TBABill on 2010-12-18
Sounds like it just went through a hard reset and defaulted back to its original settings. Should just be able to log into it and re-establish your security settings so everyone can connect again.

---

### Post by corncob on 2010-12-19
> **corncob said:**
> I started following this thread because I was having a similar problem.  I finally ended up following my own advice and pulling the plugs on both the router and the modem at the same time.  Now the wireless is working again.  I shouldn't talk too soon though -- my wife hasn't fired up her Windows machine which seemed to have started the problem :p.

Follow-up: Wife reports her windows laptop is connecting again.  Rebooting the router alone didn't help the problem but rebooting the modem (actually, both together) fixed it.

---

