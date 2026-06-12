---
title: "Can see my wifi network, but can't connect"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by Fableflame on 2011-02-18
So recently we switched Internet Providers. While we had Bellsouth, my laptop would connect to our wireless internet flawlessly everytime. However, we just switched to Charter because it was both cheaper and faster. But now, my laptop will not connect to our wireless. If I hook it up to an Ethernet cord, it connects just fine. I believe they gave us a new modem/router or whatever it is that sends out the wifi signal.

I have tried to connect with this laptop on Ubuntu, Linux Mint, and Backtrack 4. On Ubuntu and Linux Mint, after I enter the correct WEP key, it sits there and tried to connect for a minute or two, but then the window pops up asking for the WEP key again, even though it's still filled out.

When I tried connecting on Backtrack, it told me that it could not obtain an IP address.

Anyone know how to fix this? I would appreciate it a lot, a laptop is kind of pointless without the wireless internet.

---

### Post by Fableflame on 2011-02-19
Bump. I'd really like to get on wifi with my laptop again.

---

### Post by Fableflame on 2011-02-20
Bump. Again. This community used to be helpful, what happened?

---

### Post by jerenept on 2011-02-20
> **Fableflame said:**
> So recently we switched Internet Providers. While we had Bellsouth, my laptop would connect to our wireless internet flawlessly everytime. However, we just switched to Charter because it was both cheaper and faster. But now, my laptop will not connect to our wireless. If I hook it up to an Ethernet cord, it connects just fine. I believe they gave us a new modem/router or whatever it is that sends out the wifi signal.

I have tried to connect with this laptop on Ubuntu, Linux Mint, and Backtrack 4. On Ubuntu and Linux Mint, after I enter the correct WEP key, it sits there and tried to connect for a minute or two, but then the window pops up asking for the WEP key again, even though it's still filled out.

When I tried connecting on Backtrack, it told me that it could not obtain an IP address.

Anyone know how to fix this? I would appreciate it a lot, a laptop is kind of pointless without the wireless internet.

I don't know, i have never had a wireless card in Ubuntu. I don't think that changing ISP's would affect the wireless connection, unless you got a new router or something. Did you do any updates or anything? 
What kind of wireless card does your laptop have? 
What version of Ubuntu are you using?

---

### Post by lisati on 2011-02-20
> **jerenept said:**
>  I don't think that changing ISP's would affect the wireless connection, unless you got a new router or something. 
Agreed. 

I'm wondering if there's some kind of filtering based on MAC addresses currently in the OP's router.

---

### Post by Fableflame on 2011-02-20
> **jerenept said:**
> I don't know, i have never had a wireless card in Ubuntu. I don't think that changing ISP's would affect the wireless connection, unless you got a new router or something. Did you do any updates or anything? 
What kind of wireless card does your laptop have? 
What version of Ubuntu are you using?

When the guy from Charter came to install everything I do believe he hooked up a new router. I don't know what kind of updates he did.

I'm pretty sure my laptop's wireless card is a Broadcom (I've tried enabling both of the additional drivers)

I was using the latest edition of Linux Mint when this problem started, then I tried the latest Ubuntu, and now I'm on Zorin 4. I encounter the same problem on each.


MAC filtering? Would that be pre-configured to not allow wireless to connect to the router?

---

### Post by IWantFroyo on 2011-02-20
System-Preferences-Network connections-Wireless-Add- Put in your SSID and key.
Some distros have this problem

---

### Post by Fableflame on 2011-02-20
> **IWantFroyo said:**
> System-Preferences-Network connections-Wireless-Add- Put in your SSID and key.
Some distros have this problem

Didn't work.
Do I also need my BSSID? Because I don't know how to find that.
I also have a Windows desktop connected to Ethernet if I can use that to help.

---

### Post by Talon2 on 2011-02-20
> **Fableflame said:**
> I believe they gave us a new modem/router or whatever it is that sends out the wifi signal.


Resolve this first.  If you don't know for certain that the new "whatever" has wifi capability then my bet is that it doesn't.

---

### Post by Fableflame on 2011-02-20
> **Talon2 said:**
> Resolve this first.  If you don't know for certain that the new "whatever" has wifi capability then my bet is that it doesn't.

It has wifi capability, I can see it when I try to choose a network to connect to.

---

### Post by thefasterblueone on 2011-02-20
Try connecting to your "whatever" by typing this in your browser.

```
192.168.1.1
```

or 

```
ping 192.168.1.1
```

in terminal.

---

### Post by Talon2 on 2011-02-20
> **Fableflame said:**
> It has wifi capability, I can see it when I try to choose a network to connect to.

Okay.

I've got to admit on this end I'm skeptical about your ability to setup a wireless "whatever."

You are giving us almost no information to help you with.

You mention that you have used the WEP code.  Where did you get this WEP code?

If it isn't the WEP code that you entered into this new "whatever," then there is one problem.

Have you went into the settings of this new "whatever" and set it to be an open system?  If the connection works well as an open system then that might indicate there is a problem with the WEP security.

Have you tried WPA2 security?

Can you tell us the make and model of the new "whatever?"

---

### Post by Talon2 on 2011-02-20
> **Fableflame said:**
> 

I'm pretty sure my laptop's wireless card is a Broadcom [COLOR="Red"](I've tried enabling both of the additional drivers)[/COLOR]


Whoa!  I recommend that you back away from your laptop and go take a break.

Let me get this straight:  You are messing with your laptop when the part of the equation that has changed is your internet service provider and the "whatever" that this ISP provided?  Maybe you should be concentrating on the things that have changed.

Loading 2 drivers for one device may not be a good idea.  I'll guess here:  You have both the BM43 and STA drivers installed.  I'll recommend you uninstall BM43.  Once that is complete and you have rebooted, go to a friend's house that has known good wifi available and see if all is well with your laptop.  Once you have determined that your laptop is good to go then you need to focus on the "whatever."

---

### Post by Fableflame on 2011-02-20
> **Talon2 said:**
> Whoa!  I recommend that you back away from your laptop and go take a break.

Let me get this straight:  You are messing with your laptop when the part of the equation that has changed is your internet service provider and the "whatever" that this ISP provided?  Maybe you should be concentrating on the things that have changed.

Loading 2 drivers for one device may not be a good idea.  I'll guess here:  You have both the BM43 and STA drivers installed.  I'll recommend you uninstall BM43.  Once that is complete and you have rebooted, go to a friend's house that has known good wifi available and see if all is well with your laptop.  Once you have determined that your laptop is good to go then you need to focus on the "whatever."

I didn't enable both of them at the same time, I mean that I enabled one, and when it didn't work I disabled it and tried the other one.

---

