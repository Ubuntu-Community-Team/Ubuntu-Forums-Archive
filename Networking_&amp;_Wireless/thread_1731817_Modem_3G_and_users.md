---
title: "Modem 3G and users"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by josempans on 2011-04-17
Hi, I've recently installed Ubuntu, and I'm very happy with it, now will be the turn for my wife, hehe... However, we have a 3G connection, with a USB modem. At first I had some issues trying to do that Ubuntu look  for the modem and not for the disk; I've solved that with usb_modeswitch.
Now, this is my problem:

I have 2 users: Jose (me) and Vero (my wife). With Jose I have no problems to get connected I just go to the Antenna icon (network manager), and choose 3G connection. Now, when my wife is with her account, she has no way to connect through 3G, because the NetworkMan doesnt appear in the panel. I was trying to solve this without any success. The only thing I could make is to put the NetWork man icon on the panel, but this icon not shows any option with the right mouse button, and do nothing with the left click icon. Only thing it does is being there, :P.

Please let me know how can I solve this

Thanks in advance

---

### Post by fandango11 on 2011-04-17
is network manager activated......if not go to
preferences/startup applications and tick network manager.......if it is but not showing in the panel 
right click on the panel ....add to panel......and select
indicator applet 
should then show up
hope this helps

---

### Post by josempans on 2011-04-17
Yes, I did that. Will try to explain better about Network Manager:

User Jose (admin): I can see the icon, and the icon has all the functions available, for instance it have Connection selection with left click (showing the 3G connection available), and also it have properties selection with right click.

User Vero (desktop user): The icon is not there by default, however i can show it up with the steps you mention... BUT, left click doesnt do anything, right click don't show any properties... so there is no way that this user can choose to activate internet through 3G.

Another thing that can give more info: If I start with my user (admin) and connect internet, when I switch users, they have internet too... don't know if this helps

---

### Post by 741Baus on 2011-04-17
Hi josempans you may have to enable permissions for wifi to all users in users and groups go to -System-Administration-Users&Groups-User-Vero-Advanced Settings-User Privileges-connect to Wireless or ethernet network-OK this should work .
 By the way I don't have a wi-fi network but have in the past added new users and they didn't have internet access doing this gave them this access .

---

### Post by fandango11 on 2011-04-18
check the box enabling all users at
the bottom left of the edit wireless connection
in network manager ??

---

### Post by fandango11 on 2011-04-18
sorry ignore that i forgot you are on 3G

---

### Post by josempans on 2011-04-19
I've did all that. User "Vero" still can't control the 3G connection, very weird and annoying. What I'm going to try is an automatic connection, but with 3G is not a good option (need to initialize and sometimes ubuntu tries to connect before the 3G is ready)

---

### Post by robro on 2011-04-19
I have had somewhat similar problems and I think I can help, start up the terminal (Applications>Accessories>Terminal) and when it is ready type nm-applet and see if that works.

---

### Post by josempans on 2011-04-19
well... I don't know if that will work... because when I tried to do that, the icon were there!... What I did was starting from the beginning with user "Vero"... anyway, I think that "nm-applet" will work because when i wrote that in the terminal i get a message telling me that the app was already working... well, if i have any more troubles i'll let you know. THANKS! (to all)

---

