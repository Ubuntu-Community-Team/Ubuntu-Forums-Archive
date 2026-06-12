---
title: "iTunes Store access, please help"
date: 2010-01-04
forum: Multimedia Software
---

### Post by SchizmWolf on 2010-01-04
Hi. I got about 30 bucks worth of iTunes giftcards I'd like to redeem, but Apple doesn't have iTunes support for linux. I installed it via wine, but I can't get the itunes store to open up. I've been trying for several hours to get a workaround, with no success, as follows:

1) iTunes on Wine (didn't work, like I said)
2) Sharp Musique (old thread, all the links were broken and it's not in my Synaptics repos)
3) Banshee iTunes Store extension*****

   This last one with Banshee seems promising, but I'm getting nowhere. I've downloaded the third-party extension, installed the .deb, and followed the directions on the banshee webpage. Still, when I go under Edit>>>Preferences>>>Extensions, it doesn't show up. I found the install called "iTunesMusicStore.dll" in /usr/lib/banshee/Banshee.Plugins, and I've moved it to ~/.config/banshee-1/addin-db-001/addin-data, but it still won't show up in the plugins. 
I'd really like to redeem these cards, if only to make my grandparents happy ^.^;;;  Any help would be VERY appreciated.

---

### Post by tacantara on 2010-01-04
If virtualization is an option, install a VM such as Sun's VirtualBox, and install a Windows OS on the VM, and finally install iTunes.  Running iTunes in Wine is hit-or-miss at best.

---

### Post by SchizmWolf on 2010-01-04
Thanks for the speedy reply. I have thought about running Sun Vbox with XP on it, but my harddrive is pretty small, and I don't relish the thought of having to set aside a substantial partition for it. Also, I've run into issues with sharing across Vbox before, and I'd like to be able to access the music from Kubuntu without having to boot up XP. I might do it anyway, but... ugh.

---

### Post by prshah on 2010-01-04
> **SchizmWolf said:**
> Still, when I go under Edit>>>Preferences>>>Extensions, it doesn't show up. I found the install called "iTunesMusicStore.dll" in /usr/lib/banshee/Banshee.Plugins, and I've moved it to ~/.config/banshee-1/addin-db-001/addin-data, but it still won't show up in the plugins. 

I've not used iTunes, iTunesStore, Banshee or mono, so I have no idea of the validity of the following advice: Can you ensure that the dll in question is executable (+x permission set)?

---

### Post by SchizmWolf on 2010-01-04
> **prshah said:**
> I've not used iTunes, iTunesStore, Banshee or mono, so I have no idea of the validity of the following advice: Can you ensure that the dll in question is executable (+x permission set)?
I just checked the properties, and it says that it is executable. What I noticed that I somehow glossed over last night is that all the other banshee plugins are .maddin extenion types. Not a single .dll. So somehow I'd need an .maddin for it, or some way to make a dll into one.

---

