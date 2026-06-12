---
title: "Ubuntu is running in low graphics mode"
date: 2011-01-10
forum: Multimedia Software
---

### Post by AlexanderDGreat on 2011-01-10
Hello, I have a server Ubuntu LTS 10.04 32-Bit:

Asus P5KPL-EPU AM
4 gb Ram ddr2
Intel e5400 dual core
Built-in Graphics
> 
$lspci | grep Graphics

Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

No proprietary drivers.

So... I start the SERVER with Auto Login

There are important services in this server like a VirtualBox MS Exchange Server for MS Clients, Samba / NFS / File Server and Squid Proxy Server.

**BUT** - It's inconsistent, **Randomly**, it DOES NOT Boot TO Desktop, Why?

_It says Ubuntu is running in low graphics mode, and waits for user confirmation WHICH IS REALLY Annoying!_

**How can the server start when this stupid Error comes up? What can I do?**

Can anyone help me why this is happening? This server should be Auto-Login and Auto-Start its services, but because of the LOW GRAPHICS SH*T - I'm dead end, and it's really frustrating for Ubuntu! :confused::(

Please help!

---

### Post by AlexanderDGreat on 2011-01-11
> [http://ubuntuforums.org/showthread.php?t=1661395](http://ubuntuforums.org/showthread.php?t=1661395) - I hope this works.

If not, I'm going to install a graphics card on the server to use Proprietary Drivers as they are more stable.

BUT A GRAPHICS CARD ON A SERVER! Geesh, I thought this OS was friendly! It bites!

---

### Post by tjones00 on 2011-01-11
It could be kms messing up with your card/display.

When everything is behaving itself create a static xorg.conf

```
sudo Xorg -configure
```

Then turn off kms with the nomodeset boot paramater update grub and reboot.

```
gksudo gedit /etc/default/grub
```

replace the line "quiet splash" with "nomodeset" save the file and update grub

```
sudo update-grub
```

---

### Post by AlexanderDGreat on 2011-01-27
@tjones00 - hi thank you for reading my problem, however this code:

```
sudo Xorg -configure
```

Produces this error:
> 
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


What do I do next? Again, thanks for your response.

---

### Post by AlexanderDGreat on 2011-01-27
I've also tried stopping gdm and ran the code from CLI only.

---

### Post by AlexanderDGreat on 2011-01-27
**Anyone can help? PLEASE...**

---

### Post by AlexanderDGreat on 2011-01-30
bump!

---

### Post by xc3RnbFO8P on 2011-01-30
Did you check wiki.x.org:
[http://www.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Serverisalreadyactivefordisplay0.22]("http://www.x.org/wiki/FAQErrorMessages#Ikeepgettingthemessage.3A.22Serverisalreadyactivefordisplay0.22")

---

### Post by AlexanderDGreat on 2011-01-30
Ok thank you so much Ringi, I will try this as soon as I go home, can't mess with the Office server. Have a nice day. :)

---

