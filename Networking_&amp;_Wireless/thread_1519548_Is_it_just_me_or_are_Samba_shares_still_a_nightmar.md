---
title: "Is it just me or are Samba shares still a nightmare?"
date: 2010-06-28
forum: Networking &amp; Wireless
---

### Post by beastrace91 on 2010-06-28
I was reminded yesterday of one of the last failing that is still present in Ubuntu for everyday desktop usage: Samba shares.

I do not have any shares setup on my home network so this has never been a big deal to me. My mother finally took enough interest in my operating system to allow me to dual boot 3 of her computers. Everything was up and running like a charm and then she asked "What about connecting to the file server?"

I click on "network" under nautilus and start clicking around - no where in here is the file server that every Windows system on the network can see (5 or so other systems with xp/vista/7 on them - so I know the share works). A small bit of time and some command life foo later I had hunted down and manually mounted the share and added and fstab entry for the drive so my mother would never have to go through that on her own.

That being said - did I do things the hardway here? Can someone please tell me there is an easy method that successfully detects and connects to samba shares without having to resort to CLI? Personally I do not mind doing this, but it is an issue when I am installing Linux for a beginner.

~Jeff

---

### Post by pricetech on 2010-06-28
I haven't had any issues.

Samba is one of the things I always install just after Ubuntu (system-config_samba) and is usually configured shortly thereafter.  I support a lot of windows boxen, so it's a necessity for me.

I don't normally browse for shares since I need to connect to administrative shares on the boxen I support, so I use Connect to Server and connect to c$ as a rule.

As such, I may not be "typical" of Ubuntu users who access windows shares, but I can honestly say it just plain works for me.

---

### Post by nerdy_kid on 2010-06-28
they're a nightmare :-|

---

### Post by dave_man137 on 2010-06-28
+1  nightmare... always takes more time then I think to make shares work

---

### Post by uRock on 2010-08-16
Haven't had any problems setting it up on my end.

---

### Post by TXpaniolo on 2010-08-17
Newb user here, one of my first tasks after installing Ubuntu was wanting access to 50gb of photos, music and video files on my son's Vista computer over our home network.  I think I did everything in GUI, but I can't remember for sure.  It was easy enough, but I am sure it helped that I knew what search terms to use in the forums and tutorials.  I am also not scared of terminal commands.  It took a minimum of effort.  Editing fstab to auto mount that computer so auto backups to a drive on that computer definitely involved terminal, but again easy to follow with proper search terms.

So it was relatively easy, but did require some effort/research.  Windows 7/Vista is probably a little easier for a beginning user to set up/ access a home network than Ubuntu.  But Ubuntu was easier than using Win XP for me.

---

