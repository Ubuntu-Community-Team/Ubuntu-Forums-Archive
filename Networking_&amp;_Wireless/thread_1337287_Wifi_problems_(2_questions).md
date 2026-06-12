---
title: "Wifi problems (2 questions)"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by a_z1_9scores on 2009-11-25
Good morning all! (unless of course you're halfway around the world from me then it's good evening all) 
 
I just installed both Windows 7 and a Wubi installation of Kubuntu Netbook Remix on my new netbook. Wifi wasn't working so I ran updates and restarted and it worked like magic. After using it for awhile, it froze up randomly. Not sure what happened but now my wifi refuses to connect. I press the button for it to connect and it says that it's setting up orsomething like that when I roll over it with my mouse. Then, it keeps popping up the connection setup menu as if I logged in the wrong network key. I tried changing it from open to shared key. I tried changing from passcode to key. Nothing.
 
I looked online and found that there were many problems with the kde network manager and saw that people were having success with the gnome network manager. To make a long story short, I installed it using "sudo apt-get install network-manager-gnome" (no quotes) and restarted.
 

My two questions are:[LIST=1]
[*]Is there any way to get the KNetworkManager to work on my netbook?
[*]If not, how do I run the Gnome Network Manager (and purhaps replace the KNM with GNM)?
[/LIST]Thanks in advance for your help :D

---

### Post by a_z1_9scores on 2009-11-25
bump

---

### Post by Calixte on 2009-11-27
I have exactly the same problem, both with my fresh kubuntu install and with the kde desktop I installed on my current ubuntu desktop. Strange because the same install (but with GNOME) connects to wifi just fine. I must be missing something in kde network manager

---

### Post by a_z1_9scores on 2009-11-28
I think so too. How did you get gnome to work in Kubuntu? I can't find a good guide anywhere!

---

### Post by Calixte on 2009-11-28
> **a_z1_9scores said:**
> How did you get gnome to work in Kubuntu?
actually, I did the opposite (I installed KDE on ubuntu)

I think the command is 
```
sudo apt-get install ubuntu-desktop
```
(for installing GNOME on Kubuntu). I'm not sure though.

However, that won't help you since you don't have an Internet connection to start with. :icon_frown:

---

### Post by a_z1_9scores on 2009-11-28
I can get a wired connection and I actually got the Gnome Network Manager on the computer, but I'm not sure what the command is to run it.

---

### Post by walt.smith1960 on 2009-11-28
> **a_z1_9scores said:**
> I can get a wired connection and I actually got the Gnome Network Manager on the computer, but I'm not sure what the command is to run it.

I've gotten Network manager to work in gnome by doing <Alt+F2> then nm-applet. What CAN be irritating is that network manager appears to be running but there's no icon in the panel. Logging out then logging in or restarting sometimes cause the icon to appear.

---

### Post by a_z1_9scores on 2009-11-28
I'm using the kde environment, but I will try it.

---

### Post by a_z1_9scores on 2009-12-01
I tried alt-f2 and it worked! I'm actually typing this on my Kubuntu Netbook install :D Problem solved!

---

