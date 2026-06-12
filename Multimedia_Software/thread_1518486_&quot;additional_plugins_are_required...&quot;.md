---
title: "&quot;additional plugins are required...&quot;"
date: 2010-06-26
forum: Multimedia Software
---

### Post by pjstock on 2010-06-26
I've just done a clean re-install of 9.04.

on many web pages in Firefox I get the message "additionl plugins are required...." etc. (like many other people I see. though having searched the recent posts of similar problems I don't see an solution.)

clicking through I get "No suitable plugins were found..."

This system is an i386

can anyone suggest what I am missing or have done wrong?

Peter

---

### Post by new_tolinux on 2010-06-26
Probably you'll just need flash etc.

Part of the ubuntu-restricted-extras which can be installed with synaptics or by typing this in terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by waynemeat on 2010-06-26
Click on the Install Missing Plugin's button on the top left of the message. It normally shows you what is missing and gives you an option to install it.

---

### Post by new_tolinux on 2010-06-26
> **waynemeat said:**
> Click on the Install Missing Plugin's button on the top left of the message. It normally shows you what is missing and gives you an option to install it.
If I read correct that doesn't work:
> **pjstock said:**
> clicking through I get "No suitable plugins were found..
That is exactly what I had when I started to use Ubuntu/FF. Installing the restricted extras did do the trick.

---

### Post by pjstock on 2010-06-26
> **new_tolinux said:**
> Probably you'll just need flash etc.

Part of the ubuntu-restricted-extras which can be installed with synaptics or by typing this in terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

Brilliant!
you nailed it.
I hope others in the same boat find this thread and your suggestion.

Now, have you found a trick for sharing files across a LAN? 
I (and dozens of others) are finding configuring SAMBA ridiculously involved and complicated (why can they not make all this SIMPLE?)

if you have a SAMBA suggestion, I am all ears.(with a previous installation of Ubuntu on this same machine, an install that my inadvertent blowing away of required this reinstall which has left me right make at Square ONe of my Ubuntu learning curve, I've actually miraculously managed to see this Ubuntu laptop from my WIndows XP desktop. But I can never see the other way. or I can "see" the windows machine but I get a Cannot Mount the Device message when I try to click through to see files.)

see the snapshot attached


Peter

---

### Post by nonicutie on 2010-06-26
I have the same problem and try to install ubuntu extras but not work. :(

sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

Sorry to jump on this, hope this maybe helpful for others in the same problem.

---

### Post by new_tolinux on 2010-06-27
> **nonicutie said:**
> I have the same problem and try to install ubuntu extras but not work. :(

sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

Sorry to jump on this, hope this maybe helpful for others in the same problem.
Maybe you'll have to run this first:
```
sudo apt-get update
```
This will download the package-lists from the repositories you're using.

Although it seems a bit odd to me that this would not be in the repository list by default, but it's the only thing I can think of as a cause.

---

### Post by new_tolinux on 2010-06-27
> **pjstock said:**
> Brilliant!
you nailed it.
I hope others in the same boat find this thread and your suggestion.
It's in many how-to-install-ubuntu tutorials, at least that's where I found it when I started with Ubuntu.
> **pjstock said:**
> I've actually miraculously managed to see this Ubuntu laptop from my WIndows XP desktop. But I can never see the other way. or I can "see" the windows machine but I get a Cannot Mount the Device message when I try to click through to see files.)

That snapshot tells me you're using a spreadsheet, which is ofcourse very helpful to solve the problem as spreadsheets are the most common way to access a network or do network troubleshooting:lolflag: 
It would be nicer if you could tell what you did, but as I read "miraculously" I guess that's no option.
I'm in no way any kind of samba-guru, but I'll give it a try.

But before diving into shares, what version of XP are you using. The home or the professional version?

---

### Post by pjstock on 2010-06-27
"That snapshot tells me you're using a spreadsheet, which is ofcourse very helpful to solve the problem as spreadsheets are the most common way to access a network or do network troubleshooting"

Hey, a spreadsheet would be no more arcane than some of the Sudomudocrudo instructions I usually find out here.
actually that spread sheet was just the background that happened to be infront of the "Failed to Mount" message. 
I said "miraculously" because that was how it seemed. (and this was my previous incarnation, before I did this reinstall.) I fiddled around as best I could, ran a few sudocrudosmudo commands in terminal, poked around in Samba and PResto! I could suddenly "see" my ubuntu laptop from my XP desktop. But as I said, never the other way around.

anyway, I will check that XP version when I get back to my desk tomorrow. 
thanks for offering to help.

---

### Post by new_tolinux on 2010-06-27
> **pjstock said:**
> "That snapshot tells me you're using a spreadsheet, which is ofcourse very helpful to solve the problem as spreadsheets are the most common way to access a network or do network troubleshooting"

Hey, a spreadsheet would be no more arcane than some of the Sudomudocrudo instructions I usually find out here.
actually that spread sheet was just the background that happened to be infront of the "Failed to Mount" message. 
Note the :lolflag: smiley I placed behind it......... It's there for a reason ;)

> **pjstock said:**
>  I said "miraculously" because that was how it seemed. (and this was my previous incarnation, before I did this reinstall.) I fiddled around as best I could, ran a few sudocrudosmudo commands in terminal, poked around in Samba and PResto! I could suddenly "see" my ubuntu laptop from my XP desktop. But as I said, never the other way around.
No offense meant there also. Just a conclusion that it was unlikely that you knew how you did that, so you couldn't tell that either.

> **pjstock said:**
>  anyway, I will check that XP version when I get back to my desk tomorrow. 
thanks for offering to help.
That would be nice. Some functions are only availiable in XP Pro, so trying to present you a solution for XP Pro when you have XP home would only confuse you more.

---

