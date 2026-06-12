---
title: "What is a default key ring?"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by binglebob on 2009-04-18
Hey guys,

I'm really new to ubuntu. I actually just installed it today. when I go to set up a network connection and i enter my WEP key it asks me to choose a password for the "default keyring'. I'm not sure what that is and i don't want my router to get messed up because of it. I currently have 3 computers/laptops using that connection including the laptop I'm using. It would be a great help if someone got back to me soon!

- binglebob

---

### Post by lfaraone on 2009-04-18
The "default keyring" is the safe, so to speak, in which GNOME stores all of your saved passwords etc. Usually it's the same as your login password, but you can make it whatever you want. Just remember it, because you'll need it to reauthenticate to your wifi later. (or just remember you WEP password :)

---

### Post by binglebob on 2009-04-18
> **lfaraone said:**
> The "default keyring" is the safe, so to speak, in which GNOME stores all of your saved passwords etc. Usually it's the same as your login password, but you can make it whatever you want. Just remember it, because you'll need it to reauthenticate to your wifi later. (or just remember you WEP password :)

so if i set it it won't do anything to thew connection on the other computers?

---

### Post by lfaraone on 2009-04-18
Of course not.

---

### Post by binglebob on 2009-04-18
thanks so much! :)

---

### Post by CTolley on 2009-05-01
Okay, so now that part of my issure is resolved, how do I set the keyring?  I had my wireless set up and working great after my first boot with Jaunty, then I rebooted and now I can't access my network because of the keyring issue.  It's really anoying...

---

### Post by CTolley on 2009-05-01
Okay, I found the keyring fix for any others with the question.  

[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1")

---

### Post by jacktar on 2009-05-01
This is not necessary. To avoid being asked for the password tick the box 'Make available to all users' in the network connections.

Preferences > Network Connections > wireless tab, and edit your connection.

---

### Post by CTolley on 2009-05-02
That's not an option I see in 9.04.  And checking the boxes in System>Administration/Users and Groups> Properties>User Privileges didn't work either.  System>Preferences>Encryption and Keyrings did nothing for me, nor did Applications>Accessories>Passwords and Keys.  The only thing that did work for me was the directions in the page above.

---

### Post by Ichido on 2009-05-02
> **CTolley said:**
> That's not an option I see in 9.04.  And checking the boxes in System>Administration/Users and Groups> Properties>User Privileges didn't work either.  System>Preferences>Encryption and Keyrings did nothing for me, nor did Applications>Accessories>Passwords and Keys.  The only thing that did work for me was the directions in the page above.

Get "Network Connections" from 
1) System>Preferences>Network Connections
or
2) Right Click on the "Blue Bars" Wireless Signal Icon, top Bar next to Sound Icon.

Next, in the Network Connections 'Window' click on the "Wireless" Tab, then Select your Connections and Click on the "Edit" Button.
Finally, at the bottom of the "Editing Wireless Connection", Check the "Available to all users" Box and Choose "Apply".

---

### Post by CTolley on 2009-05-03
Did that, but the "Connect" box is grayed out when I select my network for connection.

---

### Post by ghayden on 2009-05-21
I am attempting to deal with "keyring" but I can't follow your path!.  Using xubuntu, there is no System > Preferences option.  From the Applications panel icon, I can select System, but System  doesn't offer Preferences.  Is there another path to get to this?

---

### Post by blastbar on 2009-05-22
how do i change the password for the keyring? i've done it once and can't remember how:p

---

### Post by crazybuntu on 2009-05-23
thats the problem with linux.... everything that could be done with a aingle click in windows is  a multiple step command using the terminal crap ... i wonder why...

---

### Post by ianmillington on 2009-06-08
Brilliant! Right clicking on the wireless icon and checking the box solved this one for me.

Thanks

---

### Post by Shawn K on 2009-08-02
Okay, I'm feeling like an idiot.  I've looked all over Network Connections, and I don't find a single box marked "Make available to all users" or anything similar.  

The only thing I've found is a "System Setting" box.  Is this it?

I've also included the "Wireless Security" tab for learning's sake.

---

