---
title: "MythBuntu vs Ubuntu + MythTV?"
date: 2009-01-23
forum: Mythbuntu
---

### Post by PeteCress on 2009-01-23
Greater minds than mine have advised me to stick with MythBuntu as opposed to installing Ubuntu and then MythTV.

But there are few things about Plan B that I find attractive:
------------------------------------------------------------
1) A more functional desktop.  e.g. ability to easily create
   shortcuts by dragging/dropping from dropdowns

2) A more consistant desktop - same look/feel as other Ubuntu
   PCs

3) (this is the biggie) The ability to image my initial 
   bare-bones-but-up-to-date Ubuntu install before bringing 
   MythTV into the picture. 
------------------------------------------------------------
  
I've enough problems installing Myth that the ability
re-image from a bare Ubuntu sys and then try Yet Another 
MythTV Install on top of it would save significant time.

MythBuntu for me is about 1.75 man hours to parititon,
format, install, update to the latest  and config.

I'm thinking that restoring Ubuntu from an image and just
installing/configuring Myth could cut that to 30 minutes
per go-around.

So, bottom line, is there anything special about MythBuntu
besides having been pared back to a lighter-weight OS?

If so, any caveats/procedures/tips/tricks that will let me
perform a seamless MythTV install over top of Ubuntu 8.10?

---

### Post by singedwings on 2009-01-24
I have tried 

1.mythbuntu,
2.ubuntu + mythbuntu install script,
3.ubuntu + mythtv.

1 and 2 are quite easy for a bit of a novice like me, but add things that you might not want (loading screens bits of xfce etc). 3 allows your complete customization, but I found the biggest bit missing is how to set up mysql, something I have not mastered at all yet.

---

### Post by PeteCress on 2009-01-24
> **singedwings said:**
> biggest bit missing is how to set up mysql
At about 0200 this morning, I woke up wondering what happens to MySQL when one shuts down the system via System | Quit.

I've had varied/recurring problems that could be explained by a corrupted database.   

Now I'm thinking that my practice of taking an image after each install might be a player.    To take the image, I have to reboot the PC.  At that time, just after an install, I visualize MySQL as being busy acquiring program information (I use EIT) and just pulling the plug on it so-to-speak might be corrupting it.   

Even though I'm not literally pulling the plug.... I'm using System | Quit | Restart to shut down gracefully; there would have to be some code behind Quit that tells MySQL to also shut down gracefully.

I'm testing that hypothesis right now - restoring a bare Ubuntu image, re-installing Myth.... and then I'll Google until I find the command line magic to tell MySQL to shut down before I reboot to take the image.

---

### Post by fenian on 2009-01-24
I have no issues using Mythtv and Ubuntu together.I have two displays set up as seperate X screens and I can watch Mythtv on one while I work on the other.I have never had any problms with mysql that were related to Mythtv being installed on top of Ubuntu.

My preferred metod of installing Ubuntu and Mythtv would be...

Install Ubuntu
Update Ubuntu
Make all necessary changes to fstab,etc...
Add codecs (you can also do this later from MCC)

To add Mythtv (with the Mythbuntu stuff:Lirc generator,Control Centre) in a terminal enter...

> sudo apt-get install mythbuntu-control-centre

You can then use the control centre (from he mnu ystem>Administraion>Mythbuntu Control Centre) to install and set-up Mythtv and all assocated packages (i.e:Mysql)

---

