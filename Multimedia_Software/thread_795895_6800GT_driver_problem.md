---
title: "6800GT driver problem"
date: 2008-05-15
forum: Multimedia Software
---

### Post by Damned666 on 2008-05-15
Hi guys,

Sorry for double posting, i seems to have a hard time finding help about this in the beginners thread. I have a 6800GT installed in Hardy and am unable to get it to be recognized correctly. I can't get past 800*600 for now with driver 96.xx.xx from nvidia. With newer driver i'm unable to get any Gui. Tried envyng without any success.

Please help, i'm about to reinstall windows on this one.

---

### Post by overdrank on 2008-05-15
> **Damned666 said:**
> Hi guys,

Sorry for double posting, i seems to have a hard time finding help about this in the beginners thread. I have a 6800GT installed in Hardy and am unable to get it to be recognized correctly. I can't get past 800*600 for now with driver 96.xx.xx from nvidia. With newer driver i'm unable to get any Gui. Tried envyng without any success.

Please help, i'm about to reinstall windows on this one.

Hi and is this a clean install of hardy or a upgrade? I see in your previous threads that you have tried envy and reconfiguring your xorg and still no luck. If you try envy you will need to uninstall any previous nvidia drivers before installing with envy. Have you tried the restricted drivers also?

---

### Post by frokki on 2008-05-16
I have the same card and it works ok with the restrected drivers (169.12) that ubuntu offers to install at first run. I had a clean hardy install though.

---

### Post by Damned666 on 2008-05-16
Hi,

it's a fresh install. I reinstalled about 20 times just this week to make it work. Envyng gave me black screen as does the restricted drivers install. Cannot see the login screen at all. Every test has been done on a clean install, i tried displayconfig-gtk yesterday but it doesn't change my situation. I still have a message telling me ubuntu is running in low-graphics mode. Any idea anyone ?? (my card is a BFG 6800GT OC)

---

### Post by overdrank on 2008-05-16
> **Damned666 said:**
> Hi,

it's a fresh install. I reinstalled about 20 times just this week to make it work. Envyng gave me black screen as does the restricted drivers install. Cannot see the login screen at all. Every test has been done on a clean install, i tried displayconfig-gtk yesterday but it doesn't change my situation. I still have a message telling me ubuntu is running in low-graphics mode. Any idea anyone ?? (my card is a BFG 6800GT OC)

Hi after using envy or the restricted drivers have you tried to reconfigure you xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` if you receive a blank screen then try and use the ctrl, alt, F1 keys and this should bring you to the command line and then reconfigure and reboot.

---

### Post by Damned666 on 2008-05-16
With the restricted driver i had a complete lockup last time i tried with both Envy & restricted driver. No CTRL-ALT-F1 was possible. I could probably try it again tonight both.

---

### Post by Damned666 on 2008-05-16
Hi,

After trying envyng & the restricted driver the computer completely freeze with a black screen. Any other idea ?

---

### Post by Xiong Chiamiov on 2008-05-17
Try [this]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329"), and tell me what happens (I'm trying to gather feedback).

---

### Post by Damned666 on 2008-05-20
This still gives me a complete lockup .. numlock doesn't even respond, it's very weird.

---

### Post by Damned666 on 2008-05-20
Upon reboot a get a black screen but numlock is working so the computer isn't frozen.

---

