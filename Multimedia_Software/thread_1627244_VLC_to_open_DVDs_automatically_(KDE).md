---
title: "VLC to open DVDs automatically (KDE)"
date: 2010-11-21
forum: Multimedia Software
---

### Post by tpprynn on 2010-11-21
Doesn't seem as straightforward in KDE, but I'd like to put my dvd's in and have VLC start them, i.e. open them to their features' menu automatically as I could in Gnome.  Can anyone describe me the steps clearly if this can be done?

When I put a dvd in so far I get the right-hand options slide up in a box which mentions Dragon Player and K3b and so on. Dragon Player sems to get stuck if you accidentally hit the touchpad in the wrong place during a film, so I'd rather keep away from it.

Thanks.

---

### Post by SeijiSensei on 2010-11-21
Go to System Settings > File Associations.  If you type "dvd" in the search box, you'll see the "x-content" type.  Click that to drop down the list of subtypes and choose "video-dvd".

If you've already got VLC installed, it might appear in the list of applications.  Otherwise, click "Add" and choose VLC from the menu (probably under Multimedia).  Use the "Move Up/Down" buttons to put VLC at the top of the list, then click "Apply" to save the association.

You can use this tool to change the order of applications as well.  I find Handbrake tends to put itself at the top of some of these lists when it's installed, whereas I'd prefer to have SMPlayer be the default application.  Just open the File Associations tool and move the applications around to the order you'd prefer.

---

### Post by tpprynn on 2010-11-21
thanks for replying. I had used that File Associations thing for other file types before, but when I looked where you suggested just now only VLC was listed for DVDs - not even Dragon Player.

I am using Mint 9 KDE, built on Kubuntu 10.04. Do you have any other ideas? Maybe there is something about the mint setup that causes this. I'll ask my friend, who I'd installed Kubuntu 10.04 for this week, to try the same and see what she says.

It's odd that given this file association setup it's still five other options and not VLC that shows up in that sliding box.

Thanks so far.

---

### Post by SeijiSensei on 2010-11-21
> **tpprynn said:**
> It's odd that given this file association setup it's still five other options and not VLC that shows up in that sliding box.

OK, I stumbled upon the answer -- you need to edit "Device Actions" not "File Associations".  This is quite a confusing application.  I "solved" the problem by editing the entry for Dragon Player and changing the name and command line.  I use smplayer, so I changed the program entry to "smplayer dvd://".

However I can't remove the Dragon Player entry; it must be coming from a configuration file belonging to root.  I tried using kdesudo to run Device Actions but still couldn't delete the entry.

You'll also have to log out of KDE to make the change appear in your session.  Apparently it reads this list at login and uses it throughout the KDE session.

---

### Post by tpprynn on 2010-11-21
Thanks for your input but this hasn't worked for me. Maybe it's something ot do with VLC, and I don't have the facilities ot download smplayer at present. I'm going ot replace Mint 9 KDE with Kubuntu in case that solves things but otherwise I may have to look on another forum, like if VLC's makers have one themselves.

---

