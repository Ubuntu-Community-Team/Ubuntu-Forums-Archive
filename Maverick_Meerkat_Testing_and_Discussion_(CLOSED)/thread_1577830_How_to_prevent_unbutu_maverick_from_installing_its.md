---
title: "How to prevent unbutu maverick from installing itself with unbutu 10.10.update?"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by reza1717s on 2010-09-19
I had to reinstall my O.S.(ubuntu 10.10) several times in last few days,because after automatic update i couldn't boot & log to my system,& when i log in with live cd,it seemed that all system file are there,the advise of one of you more experienced guy was:"i can log in to my older version with boot screen",but in my boot screen ,i had just "ubuntu maverick development branch.."+vista + diagnostic tools & ...,(for more detail you can see my previous post :"http://ubuntuforums.org/showthread.php?t=1577570&highlight=can%27t+boot+log+update."then i install ubuntu again,& during install i realise that my automatic update actually created the third partition on my HDD ,(vista + ubuntu maverick + ubuntu 10.10),  & this was the source of my problem,now my question is how to prevent it? i guess that i can disable automatic update,but i don't think this is a really good solution,any advise or suggestion?
I appreciate your help & knowledge.

---

### Post by Tibuda on 2010-09-20
I don't think it is a good idea to enable auto updates in a pre-release testing system.

---

### Post by coffeecat on 2010-09-20
@reza1717s, your post is almost unreadable. I'm telling you this in a kindly way because people will be put off answering by this. Please split your posts into paragraphs - give them some air. Also - your URL is not clickable. Perhaps that's because you wrapped it in quotes - I don't know. I'm happy to click on a link, but not to copy and paste a URL into another browser window/tab. I'm sure others feel the same.

Anyway....

> **reza1717s said:**
> during install i realise that my automatic update actually created the third partition on my HDD 

An update creating a partition? :? Can you explain that? I've never heard of an update creating a partition.

> **reza1717s said:**
> i guess that i can disable automatic update,but i don't think this is a really good solution,any advise or suggestion?

In fact, that is a good idea. Enabling automatic updates in the development cycle is a very bad idea, imo. When you are running a pre-release version you need to be in control of updates, or risk breaking your system. More here:

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

(And that's how you post a URL.)

---

### Post by reza1717s on 2010-09-20
Hi coffeecat,
First of all i like to say thank you for your kind advise about my post & how to post my questions,but i guess the main reason my post was almost unreadable as you mentioned,was because i couldn't use my computer & i posted it with my android phone without pay attention to auto spelling,EXCUSE ME!(but also i couldn't see what is the problem with the link i have posted,it gave more detail explanation about my problem !).
& yes,exactly as i explained,i had one extra partition on my HDD that i didn't create or had any knowledge of it,just after i couldn't login to my system & i install ubuntu one more time,during installation process i saw that i have a one extra partition on my HDD,my HDD was in three  partition:1-ubuntu maverick development branch 2-ubuntu 10.10, 3-windows vista ,
but pay attention that before installing ubuntu again,i didn't have a multi choice boot screen,i had just "ubuntu maverick development branch"  boot screen that i couldn't login !
this is a brief explanation of my problem.
As you mentioned :" Enabling automatic updates in the development cycle is a very bad idea",can you tell me  how can i disable automatic update,i guess i knew that but i can't find it any more )!
thank you for your help .

---

### Post by reza1717s on 2010-09-20
Hi coffeecat,
First of all i like to say thank you for your kind advise about my post & how to post my questions,but i guess the main reason my post was almost unreadable as you mentioned,was because i couldn't use my computer & i posted it with my android phone without pay attention to auto spelling,EXCUSE ME!(but also i couldn't see what is the problem with the link i have posted,it gave more detail explanation about my problem !).
& yes,exactly as i explained,i had one extra partition on my HDD that i didn't create or had any knowledge of it,just after i couldn't login to my system & i install ubuntu one more time,during installation process i saw that i have a one extra partition on my HDD,my HDD was in three serrate partition:1-ubuntu maverick development branch 2-ubuntu 10.10, 3-windows vista ,
but pay attention that before installing ubuntu again,i didn't have a multi choice boot screen,i had just "ubuntu maverick development branch"  boot screen that i couldn't login !
this is a brief explanation of my problem.
As you mentioned :" Enabling automatic updates in the development cycle is a very bad idea",can you tell me  how can i disable automatic update,i guess i knew that but i can't find it any more )!
thank you for your help.

---

### Post by cariboo on 2010-09-20
You can go to System->Administration->Software Sources->Updates, and disable automatic updates. The best way to update during the testing phase is to use either the terminal or Synaptic Package Manager to do your updates. To update in a terminal type the following command:

```
sudo apt-get update && sudo apt-get upgrade
```

I personally update a couple of times a day, using the terminal or synaptic I can see what will get updated and what will be removed.

---

### Post by seeker5528 on 2010-09-20
> **reza1717s said:**
> As you mentioned :" Enabling automatic updates in the development cycle is a very bad idea",can you tell me  how can i disable automatic update,i guess i knew that but i can't find it any more )!
thank you for your help.

It used to be on the menu at 'System --> administration --> software sources', but I'm not seeing that on the menu at the moment, so to get to sofware sources you might have to go to 'System --> administration --> update manager' then in update manager click on settings or you can hit the key combination 'Alt'+'F2' to bring up the run application dialog and type in ```
sudo software-properties-gtk
```.

How ever you get there, once software sources is running, go to the updates tab. I believe as long as 'install security updates without confirmation' is not select, updates should not install automatically, I guess if they were worded more plainly the 3 options listed are equivalent to 'notify only', 'download, but don't install', 'install automatically'.

Of course you could tell it not to check for updates at all and use Synaptic or apt-get to do updates instead.

Later, Seeker

---

### Post by mc4man on 2010-09-20
> It used to be on the menu at 'System --> administration --> software sources', but I'm not seeing that on the menu at the moment
Software sources will not be enabled by default in the main menu anymore, though  is available in the Software Center under 'edit'

> ,i had one extra partition on my HDD that i didn't create or had any knowledge of it

During one of your 're-installs' you must added a 2nd 10.10 install, probably by shrinking vista or the existing 10.10 install

---

### Post by 23dornot23d on 2010-09-20
Just went into 
System - Admin - Update Manager .... it just starts to do upgrades (**CANCEL**) was the one and only option other than to let it continue and I for one want to see what is going onto my system ..... no list no warning .... guess its a bug ?

I agree with that .... the system upto now has not managed to make a new partition on my machine ..... without me having some part in accepting a new partition - maybe as said you used the free space or added it alongside Windows.

---

### Post by cariboo on 2010-09-20
That's what I get for not actually looking :), it is available in Synaptic->Settings->Repositories->Updates.

---

