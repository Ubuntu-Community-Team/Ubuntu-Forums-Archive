---
title: "Network manager seems not to work"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by Kottizen on 2010-05-08
Hi

I upgraded the following packages:
language-pack-en, language-pack-en-base, language-pack-kde-en, language-pack-kde-en-base, libsoup2.4-1, libsoup-gnome2.4-1, pm-utils today on my laptop. Some hours later, I had to force the computer to shut down by pressing the power button, since it got totally lagged when I started it after an automatic sleep due to no power left. I started it, logged in and saw that the network manager was unmanaged. I got that message when I clicked the icon at the right-bottom bar.

So, I tried with "ifconfig" in a Terminal, as root. It said only lo (= 127.0.0.1) was up. Therefor, I did "sudo ifconfig eth1 up", and the same with eth0. The network manager did not work anyways. I killed it using "sudo killall -9 knetworkmanager" and started it with "knetworkmanager" from the Terminal. The icon got removed and it appeared again, but nothing changed - it said "network manager disables", as before.

I logged off and select "Restart X server" from the login screen. I logged in again and tried. Didn't work. When I restarted my computer I saw that eth0 and eth1 was down again. I took them up and then I checked the hardware settings. I saw that I could use either KNetworkManager, Fake Net or Wicd. I tried to locate if I had Wicd or Fake Net installed, but I hadn't.

Neither the wireless or the wired connection works now. I'd like to know how to fix the Network Manager, or whatever is wrong. Also, I'd like to know if I can install Wicd using a CD or something. Maybe Wicd works better, I have no idea. I'm using Kubuntu 10.04, the final release.

Thanks for replies,
Martin

---

### Post by Naitsirhc Hsem on 2010-05-08
try suspending the computer and turning it back on, that fixed it for me

---

### Post by Kottizen on 2010-05-08
> **Naitsirhc Hsem said:**
> try suspending the computer and turning it back on, that fixed it for me
Thank you, it works now! =]

---

### Post by Naitsirhc Hsem on 2010-05-08
Excelent

---

### Post by Iowan on 2010-05-08
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

