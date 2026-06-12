---
title: "nmApplet?"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by llednar on 2009-06-04
When I start Ubuntu, a dialogue box pops up, and says something about "Enter the default keyring password for nmApplet" and I put in my CORRECT keyring password, and it just pops up again immediately, over and over again until I click Deny about 5 times. I don't know exactly how to get rid of that.

Also, is there a way to save a WPA key so I don't have to enter it everytime I boot Ubuntu and try to connect to my network?

Thank you!

---

### Post by rohitfeb14 on 2009-06-04
no option
reinstall ubuntu

---

### Post by llednar on 2009-06-04
Real answers please.

---

### Post by aysiu on 2009-06-04
The keyring is designed to save your WPA key.

It sounds as if maybe you set the keyring and mistyped the password or had some weird caps-lock issue? Just delete the keyring (I think the keyrings are in the Applications or System menu) and when you are asked to set it again (the next time you connect to wireless), set the password as blank so you won't be pestered to enter it again.

---

### Post by llednar on 2009-06-04
I remembered the password(I putin the wrong one) but how exactly do I have it remember it? Or how do I change it to be blank?

---

### Post by coffeeaddict22 on 2009-06-04
Network manager WEP/WPA passwords are stored as part of the connection information.  You can get there with System/Preferences/Network connections, or right click on the 4 vertical bar icon, choose edit connections.
Once the panel is open, find the wireless page, click on the connection of interest and then the edit button.

---

### Post by llednar on 2009-06-05
But the WEP/WPA key isn't the problem, I knew how to do that.

I would like it to stop asking for my keyring password.

---

### Post by nechus on 2009-09-26
I'm a genius!!!!!!!! I found the solution and now i don't need to enter a password for nmapplet to "access the ring"!!!! I love myself!!

---

### Post by nechus on 2009-09-26
Oh, what a moron! I was so happy, that I forgot to post the solution.
Here it is:
Right click on the network manager icon (Gnome panel notification area)
Click on "Edit connections" (I'm translating from Spanish, so the actual words could be a little different in English)
Go to "Wireless" tab
Choose your current connection (the one that's giving you the problem)
Click on "Edit"
You will probably be prompted to enter your password.
Chceck the "Available for all users" checkbox.
Restart the computer
Listo! (Done!)
That worked for me, at least.:P
Whenever you are asked to enter your password, click on "Always remember"

---

