---
title: "Can't figure out how to access WPA/WPA2 Personal wireless router"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by QuizasQuizas on 2009-07-06
Hi, all,
as a disclaimer, this is probably going to sound quite stupid.
So, I come home for the week only to find that my parents have recently set up a wireless network, and, stupid me, I can't figure out how to access the wireless here on Jaunty. I have the router password and WPA / WPA2 Personal key in front of me, but Network Manager's 'Wireless Security' menu (upon trying to connect to their home wireless network) offers only the follow options: WEP 40/128-bit Key, WEP 128-bit Passphrase, LEAP, Dynamic WEP (802.1x).

Where/how can I enter a WPA/WPA2 key to gain access if these are the only options (of which I'm aware)?

Again, this is probably a silly question, the solution to which I've probably overlooked a hundred times by now, but thank you!

---

### Post by JC Cheloven on 2009-07-06
So you have a working network card in your computer. When you click on NM icon, you see your home network, and perhaps others. Alright.

I think network manager should detect the type of security of the network, and show you the proper options when you try to connect. But you don't see the wpa option, which is the one of your network. 

-Right-click NM icon, -> edit connections
-Choose your network
-In the tab "security" choose the wpa option, among other applicable settings you may configure here.
-Save/exit.
-You should be connected. If not, click (normal,left) on NM icon and click your network. 

Have fun.

---

### Post by deankovell on 2009-07-07
I had issues with the wpa when I installed jaunty, also. What I had to do was install a program called Wicd to get wpa security options. You should be able to get it from synaptic package manager, but If you can't connect try this on a different computer.

[**wicd**.sourceforge.net]("http://ubuntuforums.org/wicd.sourceforge.net")

Maybe it's not necessary, but it works. I think you also have to uninstall the gnome network manager.

---

### Post by alphacrucis2 on 2009-07-07
> **deankovell said:**
> I had issues with the wpa when I installed jaunty, also. What I had to do was install a program called Wicd to get wpa security options. You should be able to get it from synaptic package manager, but If you can't connect try this on a different computer.

[**wicd**.sourceforge.net]("http://ubuntuforums.org/wicd.sourceforge.net")

Maybe it's not necessary, but it works. I think you also have to uninstall the gnome network manager.

Interesting. Jaunty worked out of the box using WPA2 with network manager for me. Maybe it has something to do with the particular wireless driver being used.

---

