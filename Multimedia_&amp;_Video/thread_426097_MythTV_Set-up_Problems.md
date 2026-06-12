---
title: "MythTV Set-up Problems"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by jacrider on 2007-04-28
I am running Feisty.  I have a PVR-150 card.

I have installed MythTV according to the tutorial in the help.ubuntu.com section for an existing desktop running both a backend and a frontend.  Install went fine.

I start mythtv-setup and everything looks fine.  I can detect my PVR-150 card in the "Capture cards" step.  I can locate by "Video source" and download my zap-to-it account.

The next step is setting up the "Input connections."  However, I have no connections when I go there.  

I am stumped.  Nothing seems to make them appear.  I have deleted all capture cards and video sources and tried again.  

Any ideas?

Thanks.

---

### Post by Erlander on 2007-04-28
When you setup your video source you must give it a name.  Any name. just one that means something to you. type it in the space for it at the top.

Then in Input Connections you select that name.

Its not obvious but I'm sure the Ubuntu documentation covers this.

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O)

Rob

---

### Post by jiffyloose on 2007-04-29
I am having the same problem...I named the source but still no connections listed please help!

---

### Post by superm1 on 2007-04-29
This sounds like the wrong type of capture card was chosen during the capture card page.  Go there and choose the option to delete all capture cards.  Re add it and make sure that you choes PVR-*** cards.

---

### Post by jiffyloose on 2007-04-29
pvr*** was chosen still no input connections...I did notice that the card is video0 but I can only choose tuner1 not tuner0

---

### Post by jiffyloose on 2007-04-30
ok I played with this all night.  I was wondering does it matter who I am logged in as ?  I am just logged in as my normal user.  I am using the [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop)
as my guide.  I believe it sets the local user to have permissions in the mythtv group.  

Also does it matter what I name my source ?  I see reference to pvr-150-1...does it have to be this ?

---

### Post by superm1 on 2007-04-30
> **jiffyloose said:**
> ok I played with this all night.  I was wondering does it matter who I am logged in as ?  I am just logged in as my normal user.  I am using the [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop)
as my guide.  I believe it sets the local user to have permissions in the mythtv group.  

Also does it matter what I name my source ?  I see reference to pvr-150-1...does it have to be this ?
Na, both of these things shouldn't be any trouble.  Your in the mythtv group if your able to run mythtv-setup.  Naming your source is a preference item too.  Do you see any items in dmesg related to ivtv errors?

---

### Post by jiffyloose on 2007-04-30
there are no errors...(I am at work or I would post)  I did the test and the card is working correctly.  I did notice that if I change things in the mythtv-setup ...they don't stick.  I choose video0 and tuner1 (tuner1 is the only option...or tuner2).  when I choose the card then go back to the screen it is not listed.  SHould it say add new card ., delete cards ....then list your card you just setup ?

---

### Post by superm1 on 2007-04-30
> **jiffyloose said:**
> there are no errors...(I am at work or I would post)  I did the test and the card is working correctly.  I did notice that if I change things in the mythtv-setup ...they don't stick.  I choose video0 and tuner1 (tuner1 is the only option...or tuner2).  when I choose the card then go back to the screen it is not listed.  SHould it say add new card ., delete cards ....then list your card you just setup ?
Sounds like you have something funky going on with your mysql database not storing your settings.  I say since you don't have anything invested into the database yet -

sudo apt-get remove --purge mysql-server-5.0 mythtv-database

Remove the database when it asks you to.

and then reinstall both.  The database will be rebuilt and hopefully take care of whatever corruption / problem you were encountering.

---

### Post by jiffyloose on 2007-04-30
Thanks ....I thought something was funky.  I will try to redo tonight and post tomorrow.  Everything we going to smoothly in the guide I thought this is a piece of cake !!!   Then my fun halted.:(

---

### Post by jacrider on 2007-05-01
Jiffyloose:  I am still stuck at the same point as you.

Could you pass on your results.

Thanks.

---

### Post by jiffyloose on 2007-05-01
I think something to do with the mysql database...if I run the myth-setup in the terminal I get all kinds of errors / problems...I am reinstalling maybe tonight.  I will let you know.

---

### Post by jiffyloose on 2007-05-01
Mythbackend setup not saving settings
This problem is caused by a database setup error. Syptoms include capture card setting not saving, and a database error when finishing backend setup. To fix: 

In mySQL drop the data base mythconverg If not confident with mySQL install phpmyadmin, and you can do it from a web browser 

Open Synaptic Package Manager and search for myth-database. Mark package for re-installation, and apply changes. 

Run mythbackend setup again and problems should have gone.

---

### Post by jiffyloose on 2007-05-02
I figured it out.  I basically got side tracked when following the guide ...and installed mythtv-backend.  This is after I install Mythtv.  I reinstalled everything and it worked!

---

### Post by jacrider on 2007-05-03
Ok, I will try again tonight and post results.

Thanks for keeping us up to date on your progress.

---

### Post by kbehel on 2008-04-08
While this is an old thread - has anyone else had this problem and been able to fix it without wiping out their database (or restoring an old one)? 

I've got too many programs to just wipe it out.

thanks,

kevin

---

