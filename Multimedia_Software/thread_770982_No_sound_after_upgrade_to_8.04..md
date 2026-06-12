---
title: "No sound after upgrade to 8.04."
date: 2008-04-27
forum: Multimedia Software
---

### Post by RossAndGarfunkel on 2008-04-27
I am on Ubuntu 8.04, on an Acer 5600 laptop, with an Intel Corporation 82801G HD Audio card. I have been using 7.10 for months, until yesterday, when I upgraded to 8.04. Now, I have absolutely no sound. All volume controls work fine, but no matter what tests I run and options I mess with, I can not get my computer to even beep. 

I previously tried to get help in [this thread]("http://ubuntuforums.org/showthread.php?t=759338"), but no one knew what was wrong there. Thanks.

---

### Post by Glucklich on 2008-04-27
Since yesterday I'm looking for a solution. I think we have the same problem. But we can't find a solution. The only difference is that I installed the OS for the first time.

---

### Post by RossAndGarfunkel on 2008-04-28
Well I hate to bump up a thread, but as you can imagine this is a pretty significant issue.

---

### Post by Cannaregio on 2008-04-28
For what it is worth, here is how I solved my own sound problems on a sony vaio with a INTEL 82801DB. 
Sound disappeared totally when updating to Hardy from Gutsy.
Tried many modifications (adding a line at the end of /etc/modprobe.d/alsa-base along the lines of options snd-hda-intel model=xyz etcetera), didn't work.
What worked was adding users (and myself) to the pulse groups. (and restarting !!)

So go to System --> Administration --> Users and groups
Manage groups, unlock and choose properties for each pulse group.
Then add all the users that should have sound.
Then restart/reboot.

Hope it helps. It helped me!

Why the installation did not add users by default beats me.

---

### Post by RossAndGarfunkel on 2008-04-28
> **Cannaregio said:**
> For what it is worth, here is how I solved my own sound problems on a sony vaio with a INTEL 82801DB. 
Sound disappeared totally when updating to Hardy from Gutsy.
Tried many modifications (adding a line at the end of /etc/modprobe.d/alsa-base along the lines of options snd-hda-intel model=xyz etcetera), didn't work.
What worked was adding users (and myself) to the pulse groups. (and restarting !!)

So go to System --> Administration --> Users and groups
Manage groups, unlock and choose properties for each pulse group.
Then add all the users that should have sound.
Then restart/reboot.

Hope it helps. It helped me!

Why the installation did not add users by default beats me.

Nope. No such luck.

---

### Post by Lawrence Talbot on 2008-04-28
I'm sorry I don't have the commands with me at the present time but I ran sudo and got a list of my sound cards.  I then made the sound card I wanted to use as the default card.  I rebooted and the sound started to work again.  I will try and repost this with more information.  This worked for me in the last two versions of Ubuntu.  But Audacity will no longer record since I updated.

---

### Post by Lawrence Talbot on 2008-04-28
sudo asoundconf list

This will print out all sound cards you have. Then, use this command to set your default choice.

sudo asoundconf set-default-card CARD* *This would be your card.  

where CARD is your desired card as printed out by the first command.

Here is what I used.  I got it off the forums.

---

### Post by RossAndGarfunkel on 2008-04-28
> **Lawrence Talbot said:**
> sudo asoundconf list

This will print out all sound cards you have. Then, use this command to set your default choice.

sudo asoundconf set-default-card CARD* *This would be your card.  

where CARD is your desired card as printed out by the first command.

Here is what I used.  I got it off the forums.

Nope. Thanks for trying guys, by the way.

---

