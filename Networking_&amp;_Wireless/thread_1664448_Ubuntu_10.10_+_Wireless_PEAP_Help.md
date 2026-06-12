---
title: "Ubuntu 10.10 + Wireless PEAP Help"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by Scion_of_Cthulhu on 2011-01-11
Before getting started, I would like to say I have searched around quite intensely all day today. The most noteworthy page I found was one from this site. [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

I am at a college campus that uses PEAP to log onto the network. I recently switched back over to linux and now it became an issue. They provided me a guide to setting it up, but some issues I am having at the moment is looking through the codes and what not, it says

ctrl_interface=/var/run/wpa_supplicant

When navigating to that folder I don't have the wpa_supplicant file, but I do have wpa installed. I am trying to use Wicd Network Manager along with the provided config file as shown:

ctrl_interface=/var/run/wpa_supplicant
network={
 ssid="$_ESSID"
 scan_ssid=1
 key_mgmt=IEEE8021X
 eap=PEAP
 phase2="auth=GTC"
 identity="$_IDENTITY"
 password="$_PASSWORD"
}


Any ideas? Even vague ones or questions that I didn't specify about? I will continue to delve into the issue, but hope someone else can help along the way.

---

### Post by kage52124 on 2011-02-12
Is this actually solved? I don't see a solution here...

Sorry to bring up an old thread, but it's one of the first hits on Google.

---

### Post by Scion_of_Cthulhu on 2011-02-12
I can't honestly tell you what i did to make it work. Step one was having to have both the default wireless manager installed along with WICD. I updated to the 11.04 alpha and it sucks and is very broken for me. May not be for others, but just for me.

I have to completely reinstall ubuntu and will have to reset my wireless device. If I fix it again and remember how, I will post it here.

---

### Post by kage52124 on 2011-03-04
Please do, as I'm still at a loss and IT here can't do anything for me, which I doubt is there fault.

---

### Post by Scion_of_Cthulhu on 2011-03-07
For starters if this is a hidden network you must click your default wireless manager *this guide is only for the basic network manager that comes pre-installed". This will be located up towards the top right of your screen. Upon clicking a drop down menu will appear, click connect to a hidden network.

Type in the provided network name or SSID as it is otherwise called. When asked for security choose Dynamic WEP 802.1X.

After changing that a whole set of more options will appear. For authentication choose Protected EAP (PEAP for short). Identity can be left blank. 

My college does not require a user certificate but if yours has provided one just navigate to it. Sometimes you will be warned about not having one, just ignore it. 

PEAP version should be left to automatic. Inner Authentication may vary depending on what your school uses. Mine uses GTC, if that doesn't work or you don't know, just experiment with the 3 choices. 

Finally enter the provided username and password for network access. I presume this will be what you use to log onto the computers at your school, but yet again this may vary.

I hope this helps, and am sorry about the late reply. I tend to get side tracked, classes have been quite hectic.

---

