---
title: "Wireless Network Problems"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by newexperimentor on 2009-11-22
This is a partial repeat of a portion of a post originally on the Installation Issues Forum.

I just did an install of Ubuntu 9.04 into the largest fee space on a new system to have a dual boot system with Vista.

My system is an HP Pavillion p6130y with 8MB ram and a 700GB hard drive running Vista. The wireless modem is a 2Wire412 with an Atheros 802.11 a/b/g/n dual band card.

Everything worked first time in Vista, including wireless networking.


Wireless networking does not work.  The first time I was successful in booting into Ubuntu, I was originally asked for a key ring.  I don't know why and never had that arise with earlier Ubuntu installs.  When network question box for my access number opens, I repeatedly type the number on the modem.  This is the same number that works in Vista.  No matter how many times I edit/erase the number in the box, it shows numbers/letters I did NOT type in.  Even with the "view" box checked, and looking at the correct pass number being present, I still can not connect to the wireless network.

Any ideas on how to solve this?

Any help would be appreciated!

---

### Post by yumgnomeandthensome on 2009-11-22
the keyring is a method for encrypting passwords stored on your machine. There are a heap of posts about it causing grief for many people (including myself still).
 
Currently i've effectively turned it off (by clicking OK with the password field empty). the way to clear this if you've already entered a password is by deleting or renaming the default.keyring (I found mine in my username path/.gnome2/keyring from memory).
 
some people suggest to use the same password as your log on in the keyring and then tweak the way keyring works to use your log in password.
 
Happy hunting for a better solution than mine above....
 
Do you keep getting prompted for your Wpa password everytime you connect to your wireless connection? I do....very frustrating.

---

### Post by newexperimentor on 2009-11-22
Thank you for the information on the keyrings.  I will get rid of the current mess.

Yes, I have exactly the same problem with the WPA password.  No matter what I do or how many times I carefully type in the correct information, it hangs.

I noticed that there is another post above this one about wireless connection problems.  I am going to re-review it and see if I can find something that works.  

I would really like to get away from Macro$haft, but can only do that IF Ubuntu actually works.  I have neither the time, nor the technical expertise to live in the Fora looking for solutions to problems that should never have existed.  As a senior executive with my firm, there is absolutely no way I could allow us to migrate away from software and systems that work.  Until Ubuntu gets its act together, it will remain little more than an intellectual curiosity.  This is far too much trouble to tolerate!

---

