---
title: "How do i..."
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by TrueTenacity on 2006-06-01
Okay, i've installed this "Network Manager" thing to configure my wireless newtorking, but how the hell do you start it? it's not on any of the menus and it hasn't replaced any of the windows that relate to networking...

---

### Post by pelle.k on 2006-06-01
I've never installed anything to use my wireless card. I just configure it with the default networking tool.

What exactly is it that you want to do other than that?

---

### Post by Ateoto on 2006-06-01
Im in the same boat. Supposedly you can just drop to a terminal and type

sudo NetworkManager

it executes the command without any errors, but nothing shows up. I also have network-manager-gnome installed.

---

### Post by markmcspadden on 2006-06-01
As I found out and noted on my own thread/call for help...make sure that the Notification Area applet is added to one of your panels. Without it, you can't see the Network Manager magic.

---

### Post by Ateoto on 2006-06-02
I've got a Notification Area on my top panel,  still no NetworkManager. I guess Im doomed to just try to use the other ways to get access to the WPA networks I need to join.

EDIT:
Im going to try this guide.

[http://doc.gwos.org/index.php/Network_Manager_with_WPA]("http://doc.gwos.org/index.php/Network_Manager_with_WPA")

EDIT Again:
On my laptop I restarted and Network Manager magically appeared in the notification area. Note that I had rebooted previously and it did not show up. I'm confused, but pleased that it is working. I was able to connect to my WPA network here at work, yet I am experiencing the "default keyring" bug that others have.

---

### Post by joshpelkey on 2006-06-02
To get network manager to show up in the notification area each to you log in to Ubuntu, you need to do this:

Go to System > Preferences > Sessions
Go to the Startup Tab
Add this: /usr/bin/nm-applet

Now network manager will start everytime you login.  In order to get it to come up just once you can type this in the term. "sudo nm-applet &"

Edit: Also make sure you have the network-manager-gnome package installed.

---

