---
title: "Wireless in 9.04, Bugs/Annoyances"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Nir Friedman on 2009-05-11
I'm having some wireless issues in Kubuntu. They're all non-critical; that is I am still able to connect to the internet in general and get work done. But I'm having several issues.
1) Kubuntu simply does not seem to recognize wireless networks as being the same as a previous network. E.g. at home, our network name is linksys, and it has a hex key. When I got home I set it up to connect automatically. It connects fine, but every time I reboot it doesn't realize that this is the "same" wireless network. I have to manually connect it to linksys again and re-enter the password. Incredibly annoying.
2) The access to kdewallet seems incredibly buggy or maybe just the default behaviour is annoying. It accesses the wallet at bizarre times. The old KDE network manager only ever accessed the wallet at two times: when entering a new connection, and the first time on boot that you tried to connect (note that I clicked the "allow always" behaviour). In KDE 4 despite choosing the same option this does not happen.
3) Sometimes it asks me for the network's password TWICE. I double click to connect, I enter the password once, KDE wallet comes up, I click "Allow Always", then it asks me for the password again. This is sporadic and I don't know why it happens sometimes but not always.
4) The applet itself for KDE 4 wireless is buggy, it doesn't consistently show the number of wireless networks you set it to, sometimes it comes almost everything off and you have to unlock widgets to get it to display right again.
5) The actual Network Manager organizes wireless networks very, very foolishly. It has a complete list of every wireless network you ever connected to, organized by when you last connected. By contrast, Vista only lists the wireless networks you choose to "save" (much smarter behaviour), and it lists them in order of priority. You can then of course move around networks to make the priority the way you want. I'm hardly a fan of Vista in general, but it seems hard to deny that Vista's method here is far superior.
6) I've had problems connecting to WEP2-EAP connections. I don't know whether I'm just not specifying every single parameter correctly or if its the wireless manager, so I'll withhold judgment on this one for now.

KDE 4 is overall fantastic, it looks great, plasmoids are great, krunner is great, USB manager is great, and so on. My hat is off to the KDE people. But the wireless manager seems like the biggest step back in the whole OS. Have other people been experiencing the same problems? Should I file bug reports for some of these, or have they already been filed?

---

### Post by Nir Friedman on 2009-05-12
Bump? Do other people have these bugs too?

---

