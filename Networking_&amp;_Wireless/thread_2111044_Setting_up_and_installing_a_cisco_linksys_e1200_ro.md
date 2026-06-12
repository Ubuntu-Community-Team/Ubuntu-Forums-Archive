---
title: "Setting up and installing a cisco linksys e1200 router"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by missingno222 on 2013-01-31
I am trying to setup this router and both the CD and downloads on their website are only for Windows and MacOS.    Did I buy an incompatible router or is there another way to set it up?

---

### Post by steeldriver on 2013-01-31
You should be able to do everything via a web browser - the link below has the default IP address / username / password which should apply to that model

[http://homekb.cisco.com/Cisco2/GetArticle.aspx?docid=054ed35bec254d00b19c3b3d5c4c1e11_KB.xml#b](http://homekb.cisco.com/Cisco2/GetArticle.aspx?docid=054ed35bec254d00b19c3b3d5c4c1e11_KB.xml#b)

Post back if you get stuck

---

### Post by missingno222 on 2013-01-31
I have tried to go to 192.168.1.1.  However once I get there it keeps telling me in order to secure my network I need to Install Cisco Connect, which is only available for Windows and MacOS.  I think I am stuck.

---

### Post by papibe on 2013-01-31
Hi missingno222.

Are you using wireless? if so, try connecting with a ethernet cable.

Just a thought.
Regards.

---

### Post by williejones on 2013-01-31
Here is a link to sutup DD-Wrt
jaredheinrichs.com/how-to-setup-dd-wrt-on-a-cisco-e2000.html

The link keeps adding http:// which you will have to delete to get to the web page or copy and paste to find the link.  Deleted the link, just copy into the address bar.

---

### Post by missingno222 on 2013-01-31
I am connecting an ethernet cable from my modem to my router and then another cable from my router to my computer.

---

### Post by missingno222 on 2013-01-31
That seems complicated.  Would I have an easier time with a different router such as Apple Airport Extreme?

---

### Post by ahallubuntu on 2013-01-31
No, an Apple Airport is probably the worst thing you could buy for Linux.  The last Airport I tried to configure truly DID require Mac or Windows and special software (yuck!).

I don't believe you need any special software for your Linksys.  You don't even need a CD or any software.

If you go to [http://192.168.1.1](http://192.168.1.1) what happens exactly?  Do you get a prompt for username/password?  The defaults for that are probably in your user manual (but they might be "admin" and (no password) or "admin" and "password" - varies by the make/model).  Every router I've ever setup - dozens of them of varies makes/models - could be set up that way, except for an Apple Airport.  I've never needed the manufacturer's CD to setup a router otherwise.  (Sometimes 192.168.1.1 is a different address though.)

---

### Post by missingno222 on 2013-01-31
I am not able to secure my network :(

The only way cisco is letting me secure my network is by installing Cisco Connect.  Which I can't because they only offer it for Windows and MacOS.

---

### Post by ahallubuntu on 2013-01-31
> **missingno222 said:**
> I am not able to secure my network :(

The only way cisco is letting me secure my network is by installing Cisco Connect.  Which I can't because they only offer it for Windows and MacOS.

Again, you should NOT need any software from Cisco to set up this router.

Do it this way:

[http://homekb.cisco.com/Cisco2/ukp.aspx?vw=1&articleid=3676](http://homekb.cisco.com/Cisco2/ukp.aspx?vw=1&articleid=3676)

It says "Internet Explorer" and "Windows" but it works the same with with Firefox or Google Chrome.

You might also refer to this:

[http://homekb.cisco.com/Cisco2/ukp.aspx?pid=80&vw=1&articleid=3687](http://homekb.cisco.com/Cisco2/ukp.aspx?pid=80&vw=1&articleid=3687)

---

### Post by dnr1128 on 2013-01-31
> **missingno222 said:**
> I am not able to secure my network :(

The only way cisco is letting me secure my network is by installing Cisco Connect.  Which I can't because they only offer it for Windows and MacOS.

You should see an option to set up the network manually.  Click on that and a window should pop up asking for username and password.  Once you get past that, you're into the settings, go into the security and select the option you want.

---

### Post by cobitremolo on 2013-11-01
> **missingno222 said:**
> I am not able to secure my network :(

The only way cisco is letting me secure my network is by installing Cisco Connect.  Which I can't because they only offer it for Windows and MacOS.


Hey, I've just bought one of this, I had the same problem, I fixed it turning off the wireless card, and plugging the ethernet cable from the router to the laptop, then, went to the router typing **192.168.1.1 **in mozilla (user and password are the same: **admin**) and click on "Continue without secure..." (I don't remember exactly), and then configured the wireless security with a wpa key. And that's all!! u got your cisco lynksys e1200 "compatible" with linux.):P

---

