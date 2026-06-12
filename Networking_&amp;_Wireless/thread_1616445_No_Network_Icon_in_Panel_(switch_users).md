---
title: "No Network Icon in Panel (switch users)"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by dr_duck on 2010-11-08
Hi,

Have a strange problem with the network icon on my laptop.

I have two users (me & my wife).  We often log in and use switch users so we're both logged in at the same time.

Whoever logs in first will get the network manager icon in the top panel, and whoever logs in second won't get the icon.

The second user does get a message (growl notification?) saying the wireless network <whatever> is now connected & it is indeed connected.

It's a bit annoying, as if I log in second, I can't chnage my wireless network to the other one we have, I'm stuck using whichever one my wife selected.

Help would be much appreciated.

---

### Post by grahammechanical on 2010-11-08
When you installed Ubuntu you were asked to set a username and password. That user has administrator privileges. What user privileges does the second user have?  See System > Administration > Users and Groups. Select the second user and Advance Settings or change the second user to Administrator just as the first user is. 

Now, in my case I am the only user yet for some reason the installation set me up with a custom setting. I am not prevented from doing anything and my password works to authenticate or with the sudo command. You might find the same on your system. The important thing, I think, is to make sure both users have equal privileges.

Regards.

---

### Post by grahammechanical on 2010-11-08
I have just thought of something else. One wireless network is the default connection. Is it set as Available to all users? If you uncheck this, then may be the second user will not get a wireless connection unless one is selected from those available? The the second user can choose the network connection that is preferred.

Regards.

---

### Post by dr_duck on 2010-11-09
Hi,

Yeah both users are set to have Admin rights, I'm the 'first' user (if that makes any difference).

The main wifi connection is set to be available to all users, there's another wifi connection as well that I can use as well, that isn't available to all.

Mainly the problem is that without the network icon I can't connect the vpn that is set up.  I'll uncheck the avialable to all & see if that makes the icon display.  I don't understand why it would do though - surely all users need a network manager, in case they want to connect a vpn, use a 3g dongle...

Oh, I'll check the permissions for both users as well - something makes me think its set to custom for both (I've set up a few new groups to control access to various things)

---

### Post by grahammechanical on 2010-11-09
I am sorry if I misunderstood the problem. I assumed that if a user was denied access to the network then a network icon would not appear in the panel for that user. I think that you need to add the network manager to the panel. The Add to the Panel menu might let you do that. Right click the panel. But on my system the option to put a network manger icon on the panel is absent. 

There are other ways to try to fix problems. System>Preferences>Network connections or System>Administration>Network tools. Select a network connection from the list and the button Configure will become usable. This might or might not put a network icon on the panel but it might let you do what you want. You may need to reboot or shutdown for the changes to have affect.

Regards.

---

### Post by grahammechanical on 2010-11-09
Hi

I have just seen a post that recommends that to get the network manager icon in the panel you open a terminal and type

```
sudo NetworkManger
```

You will need to enter your password. If network manager is already loaded you will get a message saying network manager is already running. If it is not running then it should started up and the icon should appear. It might work.

Regards.

---

