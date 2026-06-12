---
title: "Gui corrupted"
date: 2005-11-30
forum: Multimedia &amp; Video
---

### Post by goldsoundz on 2005-11-30
Hi! Yet another newbie here...

I have successfully installed Ubuntu; it boots great and I can work from command line. The thing is, GUI mode looks corrupted. I get to some kind of login screen, where I can type my username and password and after that I hear some music; I also have a cursor that I can move, but it's only a shapeless square. I can see the form of the KDE bar coming from the bottom of the screen, I can see the menu coming out of it, etc, but it all looks corrupted.

I've tried to switch to the VESA drivers on xorg.conf, but it only shows a different kind of corrupted screen (one where I can't see the cursor). Also tried with "radeon", didn't do a lot of help either.

I've tested the CD checksum and it was successful, and the installation process showed zero problem; it went really smooth. Even more, Ubuntu never really hangs or freezes; i can always go back to terminal and work from there, the problem is when I try to get into the GUI.

I believe it could be related with my monitor configuration, but I don't know enough about it to be sure, and I have no idea of how to solve it.

The zip attachment contains the xorg.conf and the xorg log. Conf's modeline's been made by a generator, not by myself. Adding it didn't do anything to the corruption. Xorg log's the one with vesa drivers.

I'd attach both files to the post with scroll bars like most of the people here but I don't know how....


My PC is:

AMD Sempron64 2600+
ASUS Radeon 9600SE
Monitor Philips 105E
Kubuntu Breezy Badger 64

---

### Post by goldsoundz on 2005-11-30
Sorry, this should go to Kubuntu. But I should add that, before Kubuntu, I tried with regular ubuntu and the results were pretty much the same, only with GNOME-looking corruption instead of KDE (and with vesa drivers the corruption looked exactly the same)

And I also tried with Hoary Hedgehog (regular ubuntu again, not Kubuntu) and it was all the same again...

---

### Post by Dr. Nick on 2005-11-30
Just for kicks edit your xorg.conf and change the defaultdepth from 24 to 16 under "screen" It may or may not work, It just solved my problem where the gui was corrupted and multicolored blocks with all text overlapping etc After changing that restart or just hit ctrl+alt+backspace to kill X and re login.

Hope it helps, If not I dont know what else would, just an idea

---

### Post by goldsoundz on 2005-11-30
Forgot to say I already tried that. But thanks anyway, really!

And different screen resolutions, too.

The funny thing to me is that I can't get a decent GUI even in VESA mode, which seems to be fine for, like, every single person in the world except for me! And, as I said, I don't think my VESA driver's corrupted because checksum did good and no problems were shown during the installation. So I suspect I'm probably missing a very obvious thing that I can't see because I'm such a newbie.

---

