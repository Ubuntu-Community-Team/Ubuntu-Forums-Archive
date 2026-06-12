---
title: "Automatically Unlock Keyring for NetworkManager without GDE"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by Buce on 2009-03-17
I'm running fluxbox instead of GDE, and whenever I log in, the Unlock Keyring pops up. Is there any way to get nm-applet to work without typing in my keyring every time I log in? Some googling indicates that installing gdm would fix it, but I don't want to install a whole desktop environment just to avoid entering my password.

---

### Post by Buce on 2009-03-17
After doing some digging, I found [this wiki]("http://wiki.archlinux.org/index.php/Gnome_Tips#Unlock_Gnome-keyring_on_Login"), which suggests installing seahorse. After doing that and seeing no obvious solution in the GUI, I found [this forum topic]("http://bbs.archlinux.org/viewtopic.php?id=62766"), which suggests going to Edit -> Preferences -> Password Keyrings tab within Seahorse.

There's an option there to add a new keyring. Not knowing what to put in the "New Keyring Name" field, I tried putting "nm-applet". Then, I looked on my Ubuntu box and saw that the keyring there was named "login", so I added that, too. Unlike the nm-applet keyring, this one has "Automatically unlocked when user logs in" next to the name; so does the login keyring on my Ubuntu computer, which makes me hopeful.

Still, nm-applet prompts me for my password when I startx. The only difference in seahorse that I can see between Arch (this computer; should have mentioned that earlier) and Ubuntu is that, on the Ubuntu computer under the Passwords tab on the main Seahorse screen, there's a key that says "Passphrase for wireless network linksys". If I right click on it and select properties, I can see under the Applications tab that it's the one controlling nm-applet. I can't figure out how to recreate this key on my Arch install, though. If I try to add a new key, I only have the option to create a Secure Shell or a PGP key, and I'm pretty sure I don't want either of those options. Is there some way I could copy a file over from my Ubuntu computer to get this thing working?

---

