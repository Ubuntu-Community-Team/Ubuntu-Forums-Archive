---
title: "Hacking, javascript, and networking"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by savagenator on 2009-10-25
Hello everyone!

I have gotten in a certain predicament with a certain proprietary router. In adhering to capitalism, I bought a Rosewill RNX-N4 router. Yesterday, I updated the firmware to get rid of a stupid bug that restarts the router twice when I click Save. Well, short story is that now the router refuses to give an ip address to all hard-wired computers. Strange isn't it?

Please assume that I have spend over 4 hours (an accurate amount) messing with settings and testing hardware to come up with this conclusion. I also cannot downgrade the firmware. Why? Because those people at Rosewill put some clever javascripting that disables the field when it detects a computer that is logging in as a wireless connection. Good security practice, except when hard-wiring refuses to work. 

My solution is to now hack the router to enable the firmware update feature from wireless computers and downgrade. 

Information:
The computers that get hard wired can receive multicast messages from any wireless computer. I can't ping anything, but I do receive packets like gratitious arp packets.(src: wireshark)

I don't know enough javascript to really solve this problem on my own but i know the firmware update contains a do_load() function with a few variables. I'm not sure if I am allowed to post the code (i just do a page source on it using chrome), but I am, please tell me. Otherwise, it would be helpful to give me hints on how to call functions and change variables. A command like Javascript: documents.forms.uploadform.upfile.value = "true" doesn't seem to do anything, nor does calling the function. 


WARNING:
I'm not going to infringe any proprietary laws by doing this. This is simply an act of penetration testing, troubleshooting, and fixing crappy software. I am asking for someone to first tell me (preferably an administrator) that I can post the source of the web page on this site. This is my personal router, I bought it.

PS: i am very very glad only two computers (only mine) are connected by hard wire. Otherwise my house would be on fire.

EDIT: PSS: I'm posting on a linux forum because all my computers have linux on them, and I can use any tools available.

---

### Post by FuturePilot on 2009-10-25
Couldn't you just static assign a wired computer temporarily to access the router?

---

### Post by savagenator on 2009-10-25
> **FuturePilot said:**
> Couldn't you just static assign a wired computer temporarily to access the router?

Something I tried multiple times. I tried making the router assign a static ip adress and a computer assign a statiic ip adress using ifconfig and  networkmanager. All fails. 

Strangely with ifconfig, I get strange MDNS, icmpv6, and IGMP packets goingto 224.0.0.251. No clue whats up with that. Keep in mind, this doesn't happen on only one computer, my laptop has ipv6 disabled. AND the icmpv6 packets are only using ipv6 adresses. 

ODD.

---

### Post by Cuddles McKitten on 2009-10-25
Is there no button in the back to do a hard reset?  It's usually a little hole that you have to shove a pen into in order to put the settings back to how they were out of the box.

---

### Post by savagenator on 2009-10-25
> **Cuddles McKitten said:**
> Is there no button in the back to do a hard reset?  It's usually a little hole that you have to shove a pen into in order to put the settings back to how they were out of the box.

Negative. This was a firmware update. I did reset the router after the update because of the problem though. No go.

---

### Post by FuturePilot on 2009-10-25
> **Cuddles McKitten said:**
> Is there no button in the back to do a hard reset?  It's usually a little hole that you have to shove a pen into in order to put the settings back to how they were out of the box.

That will only reset the settings. It won't reflash the firmware.

---

### Post by savagenator on 2009-10-26
Update: I have made a temporary fix by getting an old linksys router and putting in between the nicer router and the modem. From tehre, my computer connects to the old router while everyone else connects to the faster router (wireless N) connected to the old router. 

 Is anyone still interested in tackling this problem?

---

### Post by Ostracus on 2009-10-30
> **savagenator said:**
> Update: I have made a temporary fix by getting an old linksys router and putting in between the nicer router and the modem. From tehre, my computer connects to the old router while everyone else connects to the faster router (wireless N) connected to the old router. 

 Is anyone still interested in tackling this problem?

For some reason your forum ate my post so here goes, cliff notes version.
Access via wireless connection.
Router in default state via hardware reset.
Downgrade from 1.3.02 to 1.3.00
No need to disable Javascript. Try different browsers.
Be patient, watch front-panel lights to settle.
Full connectivity, modem, router, PC off. Turn on in order modem, settle. The router, settle. Then PC. Enjoy.

---

