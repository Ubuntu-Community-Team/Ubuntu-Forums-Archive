---
title: "free dvd burning software?"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by hairmetal4ever on 2006-12-25
Is there a good, free, Nero-like DVD burning software out there?

---

### Post by meng on 2006-12-25
Please define "good". For example, GNOME/Nautilus has a simple DVD burner functionality that I frequently use.

---

### Post by NeoLithium on 2006-12-25
I like using k3b with my Kubuntu installation; GNOMEBaker is also another good one.  Nero For Linux from what I've heard, is not remotely as good as the windows version, mainly it seems no one has bothered to put the time in to make it good.

---

### Post by hairmetal4ever on 2006-12-25
Is the GNOME one built-in?  If not where do I get it?

---

### Post by NeoLithium on 2006-12-25
It's in the repositories. 
```
sudo aptitude install gnomebaker
```

I'm not sure if it's in the multiverse or not; may want to have them enabled just in case.

---

### Post by hairmetal4ever on 2006-12-25
> **NeoLithium said:**
> It's in the repositories. 
```
sudo aptitude install gnomebaker
```

I'm not sure if it's in the multiverse or not; may want to have them enabled just in case.

How do I do that?  I tried running the command, there's no file there.

---

### Post by circ on 2006-12-25
sudo nano /etc/apt/sources.list

uncomment whatever says multiverse at the end

sudo aptitude update

if by some chance you dont have aptitude,

sudo apt-get install aptitude

then update

sudo aptitude install gnomebaker

should show up in your gnome menu somewhere

---

### Post by hairmetal4ever on 2006-12-25
> 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

              [ line 1/34 (2%), col 1/1 (100%), char 0/1784 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

OK, I did the first command and this is what it said.  I'm a noob, what does all that mean?  I knew some DOS back in the day but I don't yet know Linux commands.

---

### Post by hairmetal4ever on 2006-12-26
> **circ said:**
> sudo nano /etc/apt/sources.list

uncomment whatever says multiverse at the end

sudo aptitude update

if by some chance you dont have aptitude,

sudo apt-get install aptitude

then update

sudo aptitude install gnomebaker

should show up in your gnome menu somewhere

Went to install gnomebaker, here is what it said:

> 
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "gnomebaker"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


---

### Post by qalimas on 2006-12-26
Go to System > Administration > Synaptic.

Go to Settings > Repositories

Check all the boxes on the first tab (5 total), then close.

Press Reload.

Then click Search, and type gnomebaker.

Click the white box to the left of the application name and press Mark for Installation.

A window may come up saying more packages are needed, click mark.

Click Apply.

Click Apply again.



Hope that was clear enough to help =D

---

