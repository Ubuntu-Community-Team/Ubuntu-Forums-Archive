---
title: "My laptop does not detect my wlan"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by Cotopaxi on 2012-08-05
The network manager of my laptop is displaying all wlans that are available EXEPT the my own wlan! So, logically, if this wlan is not detected, I can't configure it (WPA password) for accessing it.


The laptop is a lenovo Edge E325,

Operative System is 12:04,

Can anyone give me any hints?

Thanks!

---

### Post by tartalo on 2012-08-05
Is it a hidden network?

Can you connect with another computers or OS?

Did you try to reboot the router?

---

### Post by Cotopaxi on 2012-08-05
Hi tartalo, thanks for your reply.

1) No, it is not a hidden network,

2) Yes, a windows OS does recognize this wlan, it is also recognized from a mobile phone,

3) I am just rebooting the rooter right now,...... and it still does not recognize the wlan.

The Wlan standard of the router (Fritz!box) is 802.11n+g+b

When I switched to an elder standard, the network manager did find the Wlan, but did not manage to login.

Thanks again tartalo!

---

### Post by chili555 on 2012-08-05
Some drivers have difficulty with N speeds, some have difficulty with mixed mode WPA and WPA2, preferring WPA2 only.

Which card is yours? From a terminal, please run and post:```
lspci -nn | grep 0280
```

---

### Post by Cotopaxi on 2012-08-05
Hi chili,

Thanks for your reply, here is the output you instructed me to obtain:

> lspci -nn | grep 0280
01:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:0576] (rev 01)

Thanks!

Editing: the number [0280] is in RED colour, only the number, not the brackets.

---

### Post by chili555 on 2012-08-05
Your card uses the driver wl, supplied by bcmwl-kernel-source. I suggest you experiment with settings in the router by changing to WPA2 only and also turning off N speeds. Then do you see and can you connect to your router?

---

### Post by Cotopaxi on 2012-08-07
Thanks again for your help Chili!

I am on a trip right now, as soon as I am back home, I will try it out and post the result.

Thanks again!:popcorn:

---

### Post by Cotopaxi on 2012-08-13
Ok, I found the problem (and the solution):

On the wlan router, in my case a German "fritz!box", one has to indicate that a new computer is being allowed to establish connection with the router. I am on the wlan as a guest user, so I can't log into the setup screen of the router. As soon as I am able to describe what I did, I will post that in a separate thread.

In Europe I know of two routers that have this admission procedure for new computers:

The German fritz!box &

The French "Orange" wlan routers.

Again thanks very much indeed for your help!!

---

### Post by Cotopaxi on 2012-08-14
No I can explain what I had to do:

The “fritz!box” router has a “WPS” procedure (“Wi-Fi Protected Setup”). This procedure must be activated for a new computer to log into it's Wlan. Once this procedure is activated, the user has 2 minutes time to establish the first connection from the new computer to the router. Once this is done, all future logins will then be done automatically.

I will write a separate thread, to others about this setup procedure.

Again, thanks for your help!

---

### Post by Cotopaxi on 2012-08-14
There will be a new topic with the title:

"How to establish a first connection with a WPS Wlan."

There can be two different scenarios:

1)
Your network manager displays the wlan you want to log into, but on every login attempt you get error messages (wrong password or else).

2)
Your network does not display the wlan, you want to log into, at all, although it displays many other networks. In this case the wlan is hidden for computers that are not recognized by the router.

In both scenarios, there COULD be a “WPS” procedure (“Wi-Fi Protected Setup”), that your router requires to be carried out in order to establish a first connection with a new computer.

I will now give two examples, just for illustration purposes:

I) The German “fritz!box”:
The user has to log into the setup menu via Ethernet connection and via a browser. Now in the menu “wireless” > “security” two tabs appear: “WPA” and “WPS”.  In this tab “WPS” there are 3 choices offered, I only understood the first one: “The router establishes the WPS setup”. In this choice the user clicks on “establish setup”. Now  for 2 minutes the name of the wlan should become visible on the computer's network manager.  Just type the wlan password into the WPA key field and instruct your network manager to establish a connection (don't bother about the fact that you are still connected via Ethernet). Once the network manager established the wlan connection, on the screen of the fritz!box menu just click on “abort” and you are done! Log out and start surfing.

II) The French “Lifebook” router from “Orange”:
Here the Wlan is not hidden, but you will not manage to log in until you did a WPS setup, which in this case is quite simple: On the router itself there is a black button: just press this button for two seconds and, from your computer, establish the first connection. No need to be connected via Ethernet cable in this case, you are not in a setup menu.

In both examples, this action only has to be performed for the first connection attempt, all further connections from that computer will run automatically. Of course the WPA password has to be correct in both examples.

I just hope that I am helping someone, it took me more than a week to find this one out!

---

