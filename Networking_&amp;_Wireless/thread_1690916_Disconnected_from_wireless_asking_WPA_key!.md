---
title: "Disconnected from wireless asking WPA key!"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by Flaxis on 2011-02-19
Hello,

This morning I connected to internet, using the 'hidden network' feature of Ubuntu, like I always do.
In the beginning it worked well, but after a while, while playing a game, I got disconnected. As I closed this game, I discovered that Ubuntu was asking for the WPA key (it was already filled out correctly)
There were no changes made in the network while I was playing. My brother and his girlfriend can both connect using their Windows 7 laptops, so the network itself should be allright.

Does anyone know what the solution might be?

Thanks in advance.

(Oops! It's UBUntu, and not KUBuntu!)

---

### Post by Flaxis on 2011-02-19
Ok, I'm now using another laptop of the same brand, with which connecting works, so I guess the network card crashed while I was playing this game.

---

### Post by An Sanct on 2011-02-19
I've had a lot of problems, when I wanted my router to hide its SSID, Ubuntu permanently asked me for the WPA2 key, or to be more exact, to hit [Ok], since the correct key was already entered.

Try out [wicd]("http://wicd.sourceforge.net/"), its a network manager for Ubuntu, that supports hidden SSIDs.

Me, personally, i just gave up, a hidden SSID is no security upgrade, so I just revealed it and everything worked.

---

### Post by Flaxis on 2011-02-19
> **An Sanct said:**
> I've had a lot of problems, when I wanted my router to hide its SSID, Ubuntu permanently asked me for the WPA2 key, or to be more exact, to hit [Ok], since the correct key was already entered.

Try out [wicd]("http://wicd.sourceforge.net/"), its a network manager for Ubuntu, that supports hidden SSIDs.

Me, personally, i just gave up, a hidden SSID is no security upgrade, so I just revealed it and everything worked.

Thanks for your reply. If the problem will not resolve itself when I'm back home, I will try this application.
Now that I am on this laptop, I realize another sympton: on the crashed laptop, I can't receive non-hidden networks, and on this computer I can. That leads me back to the crashed network card.

---

### Post by mr_luksom on 2011-02-19
+1 for wicd. I had the exact same issue where it would constantly ask for the WPA key.

Moved to wicd and all my problems went away. Its a little tricky to install though (need to compile), and you have to remove/disable the gnome network manager.

---

