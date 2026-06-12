---
title: "Samba network to XP"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by pbryd on 2012-03-15
I need some help setting Samba up to share files from my ubuntu machine across the home network.

I have added the folders I'd like to share by via system/administration/samba
Set the permission to 'read/write' and visibility to 'visible'


I can see the machine from my laptop running XP but the folders I've added in samba aren't showing up.

What do I have to do next?

---

### Post by gordintoronto on 2012-03-15
It's not as difficult as you think.

Run the Nautilus file manager. Highlight a folder you want to share, and right-click on it. Select "Sharing Options." Click on "Share this folder." Give it a name, which could be the same as the folder name. Click on the other two boxes, "Allow others..." and "Guest access." Click on Create Share. All done.

You might need to undo anything you did previously.

If you have any problem, tell us what version of Ubuntu you are using. For example, some versions do not use Nautilus -- so maybe my instructions won't work on your computer.

---

### Post by pbryd on 2012-03-15
I'm running 11.04 Natty Narwhal which is using Gnome 2.32.0

There's no 'Share' option but there is properties/permissions ..... owner. group. others.

---

### Post by gordintoronto on 2012-03-15
Your statements are not consistent.

Nautilus under Ubuntu (gnome) 11.04 offers Sharing options.

---

### Post by pbryd on 2012-03-16
That's what I thought, i was sure i'd seen it before too.

Here's a screen grab

[IMG]http://img525.imageshack.us/img525/1817/screenshotxb.jpg[/IMG]

---

### Post by pbryd on 2012-03-16
I'm downloading 11.10 - going to give that a try.

I only want to set up a box with a couple of drives in to stream media over a home network.

Media tomb installed fine and was picked up by the TV (dlna enabled) but then media tomb doesn't automatically start when you reboot. 

Which kind of makes it useless for this.

---

### Post by pbryd on 2012-03-16
Got Ubuntu 11.10 talking to XP across the home network.

Thanks for trying to help me out with this

Cheers

Phil

---

