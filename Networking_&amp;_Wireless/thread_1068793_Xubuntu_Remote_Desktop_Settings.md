---
title: "Xubuntu Remote Desktop Settings?"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-02-13
Hi. In Ubuntu it is straight forward to change the Remote Desktop Settings (System > Preferences > Remote Desktop).
How can change the Remote Desktop Settings in Xubuntu? For example I want this option for Xubuntu (picture attached).

---

### Post by ajoliveira on 2009-04-22
# sudo apt-get install vino

# vino-preferences
(that's the screen)

then add to your startup

/usr/lib/vino vino-server

that's it...

---

### Post by Rytron on 2009-04-23
> **ajoliveira said:**
> # sudo apt-get install vino

# vino-preferences
(that's the screen)

then add to your startup

/usr/lib/vino vino-server

that's it...

Thank you ajoliveira. :P

---

### Post by robyzu on 2009-05-23
You are the Man!!!! :D

It's works perfectly.

Thks.

RCM

---

### Post by martin051 on 2010-03-18
Found this usefull and wanted to say 'Thanks' :-)

---

### Post by Rytron on 2010-03-18
> **martin051 said:**
> Found this usefull and wanted to say 'Thanks' :-)

Your most welcome martin051. :D

---

### Post by martin051 on 2010-05-14
This is no longer working in Xubuntu Lucid Lynx 10.04, anyone any ideas - this is the script I am running from Application Autostart:

#/bin/sh

/usr/lib/vino/vino-server	#runs vino 'Remote Desktop'

Thanks.

Martin

---

### Post by martin051 on 2010-05-14
You can sure tell it's Friday afternoon, what a plank :(

All cos I had missed the ! at the start of the script, please ignore me folks... :)

---

### Post by Rytron on 2010-05-14
> **martin051 said:**
> You can sure tell it's Friday afternoon, what a plank :(

All cos I had missed the ! at the start of the script, please ignore me folks... :)

We all make mistakes martin051.;)
Learning from those mistakes are what counts.

---

### Post by darkeale on 2010-08-05
Hi,

Can someone explain how to get Vino to autostart on Xubuntu 10.04?
I can't seem to get it to work.

Thanks
Alex

---

### Post by darkeale on 2010-08-05
nevermind, problem solved.  I was typing in the command wrong!!!

Alex

---

