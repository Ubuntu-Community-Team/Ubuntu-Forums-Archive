---
title: "skype 2.2.0.25 ubuntu 11.04x64 crashes at login"
date: 2011-05-02
forum: Multimedia Software
---

### Post by 65 mustang on 2011-05-02
```
:/$ skype
Xlib:  extension "RANDR" missing on display ":0.0".
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3870): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3870): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3870): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3870): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:3870): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3870): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3870): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3870): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3870): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3870): Gtk-WARNING **: Loading IM context type 'ibus' failed
Aborted
```

```
:/$ skype --version
Xlib:  extension "RANDR" missing on display ":0.0".
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3867): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3867): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3867): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3867): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:3867): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3867): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3867): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3867): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3867): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3867): Gtk-WARNING **: Loading IM context type 'ibus' failed
Skype 2.2.0.25
Copyright (c) 2004-2011, Skype Limited
```

---

### Post by jeroenv on 2011-05-04
On 10.10, I get similar messages, but Skype works more or less (if the other party shares their desktop, Skype crashes.) Wanings With Skpe working:


skype 
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:16790): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:16790): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:16790): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Loading IM context type 'ibus' failed

---

### Post by luapub on 2011-05-15
> **jeroenv said:**
> On 10.10, I get similar messages, but Skype works more or less (if the other party shares their desktop, Skype crashes.) Wanings With Skpe working:


skype 
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:16790): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:16790): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:16790): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: verkeerde ELF-klasse: ELFCLASS64

(<unknown>:16790): Gtk-WARNING **: Loading IM context type 'ibus' failed
I have the same problem exactly. Skype seems to work ok though, except that I have the old "upside down" camera problem.

---

### Post by tyrielbr on 2011-05-26
i am experiencing the same problem... when i open it after 5-10 seconds it crashs, and just give the return on the terminal "aborted".

I run ubuntu 11.04 x386

The sux part is that i use this computer to work and skype is essential

---

### Post by zlochko on 2011-05-26
One of my colleagues started having the same problem one hour ago... It's probably something with the Skype super-node network... or similar...

---

### Post by ceverett on 2011-05-26
same thing for me.  I run 10.10 maverick, it was working yesterday, this morning it fails, and there have been no changes to my laptop at all.

---

### Post by Mangraviti on 2011-05-26
It's a global problem.

I tried to run Skype on Windows 7 as well and it simply doesn't open.

As an alternative, use IMO.IM at this address:

[https://imo.im/](https://imo.im/)

Log in using your Skype name. It can make and receive audio calls (you must have Shockwave installed). Works on Firefox and similar browsers and it also run on Internet Explorer (use it if you really like bad software).

There is a post at Skype's "Heartbeat", saying that "some of you may have problems signing in". Check it out:

[http://heartbeat.skype.com/](http://heartbeat.skype.com/)

I have to say that Microsoft just bought the damn thing and it already crashed. It's like a curse. Whatever Microsoft touches turns into absolute sh*t.

---

### Post by AlienWolf on 2011-05-26
Had this problem this morning in the office on our Ubuntu network. All the desktops running Ubuntu 10.04 seemed OK running Skype 2.1.0.81 but me and the other sysadmin running Ubuntu 11.04 with Skype 2.2.X.X experienced the crash.

I eventually decided to uninstall Skype 2.2 and rollback to 2.1.0.81 and it has been working fine ever since :D
FYI the commands I used to do this:

```

sudo aptitude remove skype

# For 64-bit installs
wget http://archive.canonical.com/pool/partner/s/skype/skype_2.1.0.81-1ubuntu5_amd64.deb
sudo dpkg -i skype_2.1.0.81-1ubuntu5_amd64.deb

# For 32-bit installs
wget http://archive.canonical.com/pool/partner/s/skype/skype_2.1.0.81-1ubuntu5_i386.deb
sudo dpkg -i skype_2.1.0.81-1ubuntu5_i386.deb

```

I just can't help but wonder if this has anything to do with M$... ;)

Update:

Just had a tip off from a colleague that removing ~/.Skype/shared.xml prevents Skype from crashing at start up.
I reinstalled Skype 2.2 to try this out and before I even removed this file, Skype 2.2 is now starting up OK for me now. I can't say if downgrading then upgrading again solved the problem, or if this was a issue with the Skype network which has now been resolved. Either way it works :D

---

### Post by Mangraviti on 2011-05-26
By the way. I got it working on Virtual Box running Windows 2000.

I installed Skype 3.8.0.154 and it connected (That was the only one that worked - don't try other versions)

If you have a Virtual Machine running Windoze, try using that version.

It won't work on Win7 (it needs to be at least version 4.2.X). So if you are running XP or Vista on VBox, go for it.

What do you guys think if we officially make Skype's funeral now that Microsoft bought it? We could make an online party about it soon, couldn't we?

---

### Post by Mangraviti on 2011-05-26
> **AlienWolf said:**
> Had this problem this morning in the office on our Ubuntu network. All the desktops running Ubuntu 10.04 seemed OK running Skype 2.1.0.81 but me and the other sysadmin running Ubuntu 11.04 with Skype 2.2.X.X experienced the crash.

I eventually decided to uninstall Skype 2.2 and rollback to 2.1.0.81 and it has been working fine ever since :D
FYI the commands I used to do this:

```

sudo aptitude remove skype

# For 64-bit installs
wget http://archive.canonical.com/pool/partner/s/skype/skype_2.1.0.81-1ubuntu5_amd64.deb
sudo dpkg -i skype_2.1.0.81-1ubuntu5_amd64.deb

# For 32-bit installs
wget http://archive.canonical.com/pool/partner/s/skype/skype_2.1.0.81-1ubuntu5_i386.deb
sudo dpkg -i skype_2.1.0.81-1ubuntu5_i386.deb

```I just can't help but wonder if this has anything to do with M$... ;)

Update:

Just had a tip off from a colleague that removing ~/.Skype/shared.xml prevents Skype from crashing at start up.
I reinstalled Skype 2.2 to try this out and before I even removed this file, Skype 2.2 is now starting up OK for me now. I can't say if downgrading then upgrading again solved the problem, or if this was a issue with the Skype network which has now been resolved. Either way it works :D


Thanks man!

Got it working with your downgrade. I won't try removing shared.xml as it's not worth it. Just leave it as it is and maybe I will upgrade to version 3.0 (if M$ doesn't kill it before).

---

### Post by theronmuller on 2011-05-26
I just had this problem and was able to resolve it completely by renaming the .skype folder in my home directory, then starting Skype. It created a new settings directory that ran correctly. Then I copied my history files (the folder inside .skype with your userid) to the new .skype folder.

---

### Post by tranaweera on 2011-05-26
I also had the same problem. After removing the .Skype direcory in my home directory fix the issue. I lost my previous conversation logs and account saved locally. but skype started normally after removing the directory

---

### Post by vallero on 2011-05-26
I confirm that removing .Skype/shared.xml on lucid 64bit fixes the problem
Cheers

---

### Post by Bugsy22 on 2011-05-26
but does removing that file affects the history? or should i first copy the history files and only then remove it?

PS: as my first post, i have to say i didn't read the intro topics for beginners, but if someone has time/patience to tell me how to copy history files, cause i can't do it following what it's said here on another forums.. can't find it  :(   TNX

---

### Post by lancelot04 on 2011-05-26
I doesn't even start here. After downgrading to 2.1.0.47, it works now.

---

### Post by sakabatou on 2011-05-26
confirm removing shared.xml does help

follow the instruction here
[http://heartbeat.skype.com/](http://heartbeat.skype.com/)

---

### Post by ghbarratt on 2011-05-26
> Just had a tip off from a colleague that removing ~/.Skype/shared.xml prevents Skype from crashing at start up.This worked for me too. Thanks!

---

### Post by PhonicLynx on 2011-05-27
> **AlienWolf said:**
> 
Update:

Just had a tip off from a colleague that removing ~/.Skype/shared.xml prevents Skype from crashing at start up.
I reinstalled Skype 2.2 to try this out and before I even removed this file, Skype 2.2 is now starting up OK for me now. I can't say if downgrading then upgrading again solved the problem, or if this was a issue with the Skype network which has now been resolved. Either way it works :D

I did this and it worked beautifully :)

---

### Post by goranp on 2011-05-27
I am confirming that removing ~/.Skype/shared.xml helps and skype is now working on maverick x86_64. No need to downgrade. Shame on Skype.

---

### Post by Mike BFD on 2011-05-27
> **AlienWolf said:**
> 
```

sudo aptitude remove skype

# For 64-bit installs
wget http://archive.canonical.com/pool/partner/s/skype/skype_2.1.0.81-1ubuntu5_amd64.deb
sudo dpkg -i skype_2.1.0.81-1ubuntu5_amd64.deb

# For 32-bit installs
wget http://archive.canonical.com/pool/partner/s/skype/skype_2.1.0.81-1ubuntu5_i386.deb
sudo dpkg -i skype_2.1.0.81-1ubuntu5_i386.deb

```I just can't help but wonder if this has anything to do with M$... ;)

Update:

Just had a tip off from a colleague that removing ~/.Skype/shared.xml prevents Skype from crashing at start up.
I reinstalled Skype 2.2 to try this out and before I even removed this file, Skype 2.2 is now starting up OK for me now. I can't say if downgrading then upgrading again solved the problem, or if this was a issue with the Skype network which has now been resolved. Either way it works :D
Thank you AlienWolf, this downgrade worked for me, too!

Meanwhile, regarding to that M$ purchase, I'm afraid I'll have to "switch" all my teammates and business partners to some other messenger...

Suggestions welcomed!))

---

### Post by stevh0 on 2011-05-27
You rock man! Thank you! 

Skype has been giving me issues over the last few days. But now its fixed!

Rolling back made all the difference!

---

### Post by ozicecool on 2011-05-28
Thanks folks. Removing the shared.xml actually did the trick for me. Do you think Microsoft will make a better version of Skype for LINUX? I am not sure folks. I am actually thinking of moving completely out of Skype in the coming months.

Personally it would be great if the Open Source community could come-up with something similar or better than Skype. If you hear anything let me know. 

I am currently trialling: 

1. Empathy using Google Account (Google Talk)

2. Just installed Ekgia

Next biggest problem is to convince people to move to what I use. People are hooked so much in to Skype. I thinking Google Talk wouldn't be that much of an issue as most of the people I know have a Google account.

Anyway I thought share some of my thoughts as well. :)

---

### Post by marin1961 on 2012-09-29
I am confirming that removing ~/.Skype/shared.xml helps and skype is now working on Ubuntu 12.04.

---

