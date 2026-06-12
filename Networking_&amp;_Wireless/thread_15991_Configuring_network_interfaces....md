---
title: "Configuring network interfaces..."
date: 2005-02-18
forum: Networking &amp; Wireless
---

### Post by christooss on 2005-02-18
When I installed Ubuntu I was connected to network and installation made work properly and setup network fine. But now I am on dial-up and comp stil checks for network at start-up. I want too turn that off beacause it takes 2 min to check.

Can you help to turn this off?

---

### Post by nemin on 2005-02-19
[QUOTE=christooss]When I installed Ubuntu I was connected to network and installation made work properly and setup network fine. But now I am on dial-up and comp stil checks for network at start-up. I want too turn that off beacause it takes 2 min to check.

Can you help to turn this off?[/QUOTE]
You can remove the network connection: "System -> Systemsettings -> Network". Select your connection and press "Remove". 
I don't use the English Ubuntu version, so I hope I translated the menu names correctly  :wink:.

---

### Post by christooss on 2005-02-19
I dont have gnome installed. So I will have to change this in console.

Any clue anybody

---

### Post by GilGalad on 2005-02-19
[QUOTE=christooss]I dont have gnome installed. So I will have to change this in console.

Any clue anybody[/QUOTE]
 In /etc/network/interfaces remove the line "auto eth0" (or whatever your network interface/s is/are). This will prevent them from being activated at boot time.

---

