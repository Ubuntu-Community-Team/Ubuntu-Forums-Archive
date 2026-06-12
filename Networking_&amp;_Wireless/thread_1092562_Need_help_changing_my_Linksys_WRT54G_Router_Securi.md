---
title: "Need help changing my Linksys WRT54G Router Security Password"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by Myth Buster 0018 on 2009-03-10
I have a Linksys WRT54G Router and I was able to change my security password from WEP to WPA. But the problem is that Linksys default for a WPA Algorithm is TKIP and I want to change it to AES, and I'm having trouble changing those settings.

Here's a picture of what the Linksys' Manual saids to do:
[IMG]http://i117.photobucket.com/albums/o53/ferristech/LinksysInstSettings.jpg[/IMG]

and here's what my Linksys settings look like via Firefox browser access:
[IMG]http://i117.photobucket.com/albums/o53/ferristech/MyLinksysSettings.jpg[/IMG]

Also here's the link for the user manual for the Linksys Router:
[http://downloads.linksysbycisco.com/downloads/WRT54GL_V11_UG_C-Web,0.pdf]("http://downloads.linksysbycisco.com/downloads/WRT54GL_V11_UG_C-Web,0.pdf")

So if anybody can help me out I would greatly appreciate it.

---

### Post by Neo_The_User on 2009-03-10
Does that router even support AES?

---

### Post by Myth Buster 0018 on 2009-03-10
Yes it does support AES algorithm coding

---

### Post by arcanewulf on 2009-03-10
I don't have much experience with WPA, but if I remember right, wpa-2 enterprise is the one that supports AES. I see WPA-2 personal in your photos

---

### Post by arcanewulf on 2009-03-10
so I guess I can find wpa2 personal with AES on google, so if I were you I'd look into firmware upgrades next to see if new firmware lets you change the right settings, and then talk with support about why you can't change your wireless settings if that doesn't work or there aren't any updates. Idk, can you change the security at all or is it completely locked?

---

### Post by Myth Buster 0018 on 2009-03-10
Yes it does support AES algorithm coding

---

### Post by arcanewulf on 2009-03-10
I read your post, does it support wpa personal/AES, or wpa2 enterprise/AES (I'm not saying your wrong). Like I said, check for firmware updates, it might be capable of it, but for some reason your firmware version isn't letting you turn it on. A firmware update might fix the menu and let you adjust it to AES. If you can't access the menu yourself with the info from the manual, there's something else keeping you from being able to, and if it's capable and you're in the right menu and can't select that, it's either a firmware problem, or there's a problem with your router.

Unless you really need the security, WPA and changing your password once a month should keep anyone out. When I looked into wpa brute forcing, the fastest they could do it was 3 months using a 13,000 dollar computer. I don't know who would want into your router that badly.

---

### Post by Jimmynemo2 on 2009-03-11
Just a tip from my same type of problem, have you tried getting onto the router in firefox within wine? I know it sounds like it shouldnt change anything, but i had a wrt54g and it displayed wrong a few pages on the router when i logged on from my ubuntu box- but from windows, or from wine's firefox, it worked just fine. Pissed me off enough that I changed to belkin once I read online and saw it wasnt just me, but a known problem with a few different firmware all for that router.

Anyway, give that a shot, let me know if it helps.

---

