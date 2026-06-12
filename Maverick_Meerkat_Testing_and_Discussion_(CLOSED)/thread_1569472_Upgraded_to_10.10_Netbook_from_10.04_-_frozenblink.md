---
title: "Upgraded to 10.10 Netbook from 10.04 - frozen/blinking desktop on boot?"
date: 2010-09-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zachin2036 on 2010-09-06
Hello everyone...I hope you can help me.  I got my wife a netbook recently, and installed UNR 10.04 for her.  She loves it so far, and I've been trying to acclimate myself to Linux, since I'm a native Windows user with a minor in Mac OS.  If you want the whole story, read through, but the most important part is in the last paragraph, for those short on patience for narrative!

Here's the problem:  Today, I saw articles talking about Ubuntu's update to 10.10 ([http://arstechnica.com/open-source/news/2010/09/ubuntu-1010-beta-arrives-with-new-netbook-ui.ars](http://arstechnica.com/open-source/news/2010/09/ubuntu-1010-beta-arrives-with-new-netbook-ui.ars)), and thought I'd give it a shot.  Yes, my official reasoning for upgrading was because the UNR screenshots looked neat.

So, as recommended on...some website (I forget which), I pressed Alt+F2, and typed in some update command.  I don't remember it being a sudo command.  I just remember "update" - something in the middle - and "-d".  

It took 2 hours to download and install the updates, and it let me know there was stuff it could and would delete because it wasn't needed anymore.  Cool, no problem.

Then it finished updating and asked if I wanted to restart.  So I did, and watched the boot process - nothing out of the ordinary.  UNR booted, and loaded the desktop wallpaper image fine - and then, here's where it went wrong.  The screen flashes white, then back to the desktop, and repeats infinitely.  I can't Alt+F2, but that's all I've tried, since I don't know any other linux-fu.  So it seems the interface just isn't loading.

Anyone have any ideas of what's going on and how to remedy it?

Thanks!

---

### Post by skyjacker on 2010-09-06
10.10 won't be released until next month...I wouldn't download new versions UNLESS you are very experienced with the software... There are bound to be bugs in this version. If I were you I would re-install 10.04 and use it until Nov. or Dec. That will give everyone time to work the bugs out of 10.10. Good Luck!

---

### Post by sandyd on 2010-09-06
> **zachin2036 said:**
> Hello everyone...I hope you can help me.  I got my wife a netbook recently, and installed UNR 10.04 for her.  She loves it so far, and I've been trying to acclimate myself to Linux, since I'm a native Windows user with a minor in Mac OS.  If you want the whole story, read through, but the most important part is in the last paragraph, for those short on patience for narrative!

Here's the problem:  Today, I saw articles talking about Ubuntu's update to 10.10 ([http://arstechnica.com/open-source/news/2010/09/ubuntu-1010-beta-arrives-with-new-netbook-ui.ars](http://arstechnica.com/open-source/news/2010/09/ubuntu-1010-beta-arrives-with-new-netbook-ui.ars)), and thought I'd give it a shot.  Yes, my official reasoning for upgrading was because the UNR screenshots looked neat.

So, as recommended on...some website (I forget which), I pressed Alt+F2, and typed in some update command.  I don't remember it being a sudo command.  I just remember "update" - something in the middle - and "-d".  

It took 2 hours to download and install the updates, and it let me know there was stuff it could and would delete because it wasn't needed anymore.  Cool, no problem.

Then it finished updating and asked if I wanted to restart.  So I did, and watched the boot process - nothing out of the ordinary.  UNR booted, and loaded the desktop wallpaper image fine - and then, here's where it went wrong.  The screen flashes white, then back to the desktop, and repeats infinitely.  I can't Alt+F2, but that's all I've tried, since I don't know any other linux-fu.  So it seems the interface just isn't loading.

Anyone have any ideas of what's going on and how to remedy it?

Thanks!
yeah. 
were having a LOT of issues with the UNR interface with the latest update that was made to maverick.
I can't find the thread right now, but im pretty sure its burried in the maverick forum somewhere...

---

### Post by zachin2036 on 2010-09-06
Is there a downgrade command I can do from boot?  My wife doesn't really have much on the netbook yet, but it'd be nice if I didn't have to redownload all of the Firefox plugins, Skype...stuff like that.  If not, no biggie - it is what it is.

Thanks everyone!

---

### Post by ilmanen on 2010-09-06
Hi
If you are able to reach Login window (for example by logging out), then select Ubuntu desktop session from the drop down selection in the lower panel. The desktop session still has your Skype etc installations. (Netbook session will show them too in the forthcoming updates).

---

### Post by zachin2036 on 2010-09-06
> **ilmanen said:**
> Hi
If you are able to reach Login window (for example by logging out), then select Ubuntu desktop session from the drop down selection in the lower panel. The desktop session still has your Skype etc installations. (Netbook session will show them too in the forthcoming updates).

Thanks ilmanen...

I *can* slide the power switch on the side of the netbook - and that brings up the Shutdown/Restart/Sleep/Hibernate menu.

Here's the catch - if I click Shutdown, I get "System will shut down in 60 seconds", it then tries to shut down and then pops up a window that says "A program is still running" and says that it's an unknown program that's not responding.  So...I can get to the login screen if I click on the "Lock Screen" button it offers me.  THEN, I move the cursor, that brings me to the password screen, and I click "Switch User".  I then click on her account, and I do get the dropdown you mentioned - but can't load the Desktop options on the menu either.  And whatever option I choose (Desktop, Netbook, Recovery Console), it tosses me back to that previous screen that told me a program's not responding.  If I then click "Cancel", I just see the desktop without any flashing or...anything.

But, it sounds like I've got a place to start the healing process.

Any ideas from here forward?

---

### Post by Peter09 on 2010-09-07
Can you get to a terminal by holding down the shift key during boot and selecting recovery mode? If you can the its worth trying to update to the latest as things are changing position all the time. Thats worth trying first.

---

### Post by zachin2036 on 2010-09-07
> **Peter09 said:**
> Can you get to a terminal by holding down the shift key during boot and selecting recovery mode? If you can the its worth trying to update to the latest as things are changing position all the time. Thats worth trying first.

Holy crap, Peter, that's the kind of forward-thinking I was looking for!

I was able to - now I'm at a prompt with 8 options:


[LIST]
[*]Ubuntu, with Linux 2.6.35-19-generic
[*]Ubuntu, with Linux 2.6.35-19-generic (recovery mode)
[*]Ubuntu, with Linux 2.6.32-24-generic
[*]Ubuntu, with Linux 2.6.32-24-generic (recovery mode)
[/LIST]

...then 4 memory tests.  Which recovery mode do you suggest?  I'm assuming those decimals are version numbers that I've installed/updated.

Which one of those should I choose?  I know, I know, I should have just TRIED one and come back here in a panic when it didn't work ;)

---

### Post by cariboo on 2010-09-07
Those numbers are different kernel versions. The newest is always at the top. 

It sounds like your upgrade may not have completed, once you get to the menu in recovery mode, use the arrow keys to select netroot. Once at the prompt type:

```
apt-get -f install
```

the above command should install any missing packages. Just to be on the safe side, have a network cable handy in case wireless doesn't work.

---

### Post by zachin2036 on 2010-09-07
> **cariboo907 said:**
> Those numbers are different kernel versions. The newest is always at the top. 

It sounds like your upgrade may not have completed, once you get to the menu in recovery mode, use the arrow keys to select netroot. Once at the prompt type:

```
apt-get -f install
```the above command should install any missing packages. Just to be on the safe side, have a network cable handy in case wireless doesn't work.

it returned:

```
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded
```

---

### Post by Peter09 on 2010-09-08
You could try typing

```
startx
```

once you et to the recovery mode prompt- It might get you to a GUI.

---

### Post by zachin2036 on 2010-09-08
> **Peter09 said:**
> You could try typing

```
startx
```once you et to the recovery mode prompt- It might get you to a GUI.

Hah!  Ubuntu!

...

now what? :|

---

### Post by cariboo on 2010-09-08
There are a couple of other things you can try. If you don't have auto login enabled, you can select either the 2D netbook interface or the gnome-desktop at the login screen. That will get you back to a gui, which you are probably more familiar with.

---

### Post by Peter09 on 2010-09-08
As Cariboo907 suggested try using a different desktop and keep updating the system.
 
Unity is supposed to be ready for the release of Maverick, which is middle of October. If you can get a workable desktop use that until Unity becomes workable for you.

---

### Post by zachin2036 on 2010-09-08
Ah, so I can try to update again from that Ubuntu desktop, and it'll upgrade both Ubuntu and UNR?

Would it be more advantageous for me to just wipe the drive and start over with 10.04?  I mean, this is my wife's netbook...so really, I was just dicking around with it when I was upgrading - she was fine with 10.04, and if it's more stable, that's probably what she'd prefer.

You guys ARE teaching me a lot about Ubuntu though - thank you - I have that troubleshooting instinct for Windows, where I know "what to do next", but definitely not yet with Ubuntu, so I really appreciate you guys helping me!

---

### Post by ranch hand on 2010-09-08
I would install 10.04 on her box and leave it alone.  It is an LTS so I would just leave it there until she want to change it.

 I mess with my desktop box all the time but I try to leave the wifes laptop alone.

---

### Post by cariboo on 2010-09-08
If you are going to re-installing 10.04, if you've got the room, you can create another partition for Maverick, and dual boot, that way you have the best of both worlds. :)

---

### Post by zachin2036 on 2010-09-08
> **ranch hand]I would install 10.04 on her box and leave it alone.  It is an LTS so I  would just leave it there until she want to change it.

 I mess with my desktop box all the time but I try to leave the wifes  laptop alone. 	[/QUOTE]

[QUOTE=cariboo907 said:**
> If you are going to re-installing 10.04, if you've got the room, you can create another partition for Maverick, and dual boot, that way you have the best of both worlds. :)


Hah, well, I think I might just wipe and restart with UNR 10.04.  I mean, my wife is not a tech by any stretch of the word.  I put UNR on the netbook and she has not EVER clicked out of the Favorites tab because Firefox and Skype are in there, and that's all she uses.

So I'll revisit 10.10 in Oct/Nov when it's stable - it *did* look cool though!

I'll just google how to wipe and start over with a flash drive install - you guys have done enough for me....thank you all!

---

### Post by ktp on 2010-09-08
> **ranch hand said:**
> I would install 10.04 on her box and leave it alone.  It is an LTS so I would just leave it there until she want to change it.

+1 to that.

---

