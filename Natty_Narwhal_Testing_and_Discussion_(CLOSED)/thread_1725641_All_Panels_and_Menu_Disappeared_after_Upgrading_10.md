---
title: "All Panels and Menu Disappeared after Upgrading 10.10 to 11.04"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by atul1412 on 2011-04-10
Hello.
This is Atul from India..
I have Upgraded My Ubuntu 10.10 to 11.04.. it was Upgraded Succesfully..
But when i changed its Settings, all the Panels Got Disappeared.
now i have no option 2 Open applications or panel...
my system is only showing the files and folders which was saved on desktop.. nothing else, No Other Functioning is working..
What to do Now...

---

### Post by Dutch70 on 2011-04-10
If you think it's a bug, report it.

---

### Post by zigorati on 2011-04-10
I have exactly the same problem!! I have upgraded from ubuntu 10.10 to 11.04 and it said the upgrade successfully finished. However, when I restart my system there is no panel or other menu. I tried to open my terminal and typed gnome-panel --replaced and the old panel has shown it face but the problem is, It is not look like ubuntu unity! It looks like the 10.10. when I check the version of the distro it shows Natty 11.04. I have done all updates and upgrades as well. please help I think this is a common issue for whoever upgrade to beta version.


cheers:popcorn:

---

### Post by hempanicker on 2011-04-10
I faced it too !

While logging in try changing the session to Normal Ubuntu and you should get all the panels back. But hey, you will not have the unity interface. I guess u can wait for a stable release.

---

### Post by atul1412 on 2011-04-10
My Case is Much More Pathetic... i am toh even Not able 2 open my Terminal or anthing else other than 3 Folders which was saved to Desktop.. nw i have Put 10.10 version on Download on my other system.. will Install that when get it DOWNLOADED....

---

### Post by Dutch70 on 2011-04-10
If you want to help by using a development release, use a virtual machine, such as Virtualbox, or a usb stick, or create a small partition on your hdd.

---

### Post by zigorati on 2011-04-10
> **atul1412 said:**
> My Case is Much More Pathetic... i am toh even Not able 2 open my Terminal or anthing else other than 3 Folders which was saved to Desktop.. nw i have Put 10.10 version on Download on my other system.. will Install that when get it DOWNLOADED....
I have an idea for you, you should open your terminal with its shortcut. I think the default shortcut is Ctrl+Alt+F1 and then type gnome-panel --replace after that I suggest you to install KDE desktop which you can find it in your Synaptic Package Manager. the next step you restart your ubuntu and change the session to kde desktop. for now you can use kde till this issue being solved.

---

### Post by atul1412 on 2011-04-10
I Dont Know about virtual Machines and Virtual Box..
I am New to this Technology Brother.. Will Learn it now Soon.. Learned about using live disks today only... But really waana Help !!!

---

### Post by zigorati on 2011-04-10
> **Dutch70 said:**
> If you want to help by using a development release, use a virtual machine, such as Virtualbox, or a usb stick, or create a small partition on your hdd.
I think people post their issues in this forum and they are looking for a solution for their problem not telling them to install all over again... personally I'm not looking for these kind of answers. people need solutions and I'm sorry to say this, your posts in here are not solution!!!

---

### Post by cariboo on 2011-04-10
IF you are new to Ubuntu, I'd suggest you wait until Natty is released, the scheduled release is April 28th. If you do want to try it, I'd suggest you keep your current install as a fallback, just in case something goes seriously wrong with Natty, then at least your computer is still usable.

If you are unsure about partitioning you can use the install beside option in the partitioning section of the installation process.

---

### Post by atul1412 on 2011-04-10
I tried ur Suggetion.. Terminal is opening but Command is Not Working Brother..

---

### Post by atul1412 on 2011-04-10
> **zigorati said:**
> I have an idea for you, you should open your terminal with its shortcut. I think the default shortcut is Ctrl+Alt+F1 and then type gnome-panel --replace after that I suggest you to install KDE desktop which you can find it in your Synaptic Package Manager. the next step you restart your ubuntu and change the session to kde desktop. for now you can use kde till this issue being solved.
I tried your Suggetion Brother.. Terminal is opening but Command is not working..

---

### Post by zigorati on 2011-04-10
> **atul1412 said:**
> I tried your Suggetion Brother.. Terminal is opening but Command is not working..

This command should work, or better to say it works for me. Just wanted to mention in case there is a space before --panel      "gnome-panel --replace"  . or if it didn't work post the error after typing this comment.

---

### Post by 23dornot23d on 2011-04-10
If you really want to try KDE ..... do the following .......

[COLOR=Red] if you break your system any worse than you 
have already done so - do not blame me though [/COLOR],,,,,, 

( But this is what I did to get KDE up and working ...... with the latest updates too .....  )

Warning before doing this make sure you have plenty of room on your hard drive .......
 could be a lot of files here to install ..... do them all in the same terminal session ....

or do as others say and stay safe .......

OPTION 1 ..........  Wait for the new release to be officially put out to everyone
on the 28th of Aprii ....

OPTION 2 ........... Here is a list of things to enter in the terminal one after the other ,,,,,,,,,

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude safe-uprade
sudo aptitude install kdm
sudo aptitude install kde-full

Hopefully your system will be fully up-to-date and you will have KDE ...... as well as having all your other choices too ......
**[COLOR=Red]IF YOU GET A LONG LIST OF ERRORS here ..... go to OPTION 1 ....... lols ....[/COLOR]**

Let me know what happens ..... :D

[COLOR=Red]Waiting till the 28th of April ...... is the safe option ..... with development work ...... you could possibly loose all your data .....
or worse ..... [/COLOR]

---

### Post by Dutch70 on 2011-04-10
> **zigorati said:**
> I think people post their issues in this forum and they are looking for a solution for their problem not telling them to install all over again... personally I'm not looking for these kind of answers. people need solutions and I'm sorry to say this, your posts in here are not solution!!!

You're new around here aren't you.
Installing a "stable" version of Ubuntu is a very good solution. 

When you install a development release, you are the one helping, not the one asking for help. Hence, the reason this thread was moved out of the support forum and into the "Natty testing & discussion" forum.

I'll have to agree with the forum staff, and suggest you wait until Natty is released to install it as your main OS.

---

### Post by atul1412 on 2011-04-10
> **Dutch70 said:**
> You're new around here aren't you.
Installing a "stable" version of Ubuntu is a very good solution. 

When you install a development release, you are the one helping, not the one asking for help. Hence, the reason this thread was moved out of the support forum and into the "Natty testing & discussion" forum.

I'll have to agree with the forum staff, and suggest you wait until Natty is released to install it as your main OS.
Yes i am Very New here... But i too wanted 2 Contribute thats why i started Using O.S.
Sorry Everybody.. Due to Me Your Precious Time is being Wasted.. I'll wait now for Realese.........
& thanks 2 all who suggested and helped Me..
Bye..

---

### Post by Dutch70 on 2011-04-10
First of all, my comment wasn't directed at you, I'm sorry if you think it was. Everyone is welcome & even asked to help. That's why I suggested Virtualbox, a usb stick, or a small partition on your hard drive. Virtualbox is not as difficult as you may think & if you/it messes up, it doesn't really hurt anything.

Second, it's not that you're wasting anyone's time. We're here because we enjoy helping others. The problem is that there isn't very many people that can help you with an operating system that hasn't even been released. There's not even very many people that know what it looks like other than what they've seen in pictures or video's. That's the reason there is a testing & discussion forum, so we can all learn about it together.

How are we really supposed to help you with an operating system that isn't even finished?
How much experience do you think we have with it? 
I hope this doesn't come off the wrong way, I just don't know how else to say it.
Out of the people that have installed it, even less have upgraded to it.

---

### Post by zigorati on 2011-04-10
> **atul1412 said:**
> Yes i am Very New here... But i too wanted 2 Contribute thats why i started Using O.S.
Sorry Everybody.. Due to Me Your Precious Time is being Wasted.. I'll wait now for Realese.........
& thanks 2 all who suggested and helped Me..
Bye..

hey my friend good news....  

I found myself how to fix this problem. I hope works for you as well.
The problem is about shortcut conflict which is for gnome and unity. when we upgrade from gnome to unity there are some (for me two) conflict.

Okay, back to solution. follow exactly the process.

1- open your terminal

type this in your terminal or just copy and paste.

2- sudo apt-get install compizconfig-settings-manager

after that

3- ccsm

you will see a new window is opened. then in the top left corner u can find "Filter". type unity in the text field. after that you will see an icon with purple color. Just tick it and it will show you that there are some conflict with gnome. then disable all shortcuts which are for gnome and replace it by unity.then close it and restart your OS. 

I hope it works for you as well.
:popcorn::KS

---

### Post by zigorati on 2011-04-10
> **Dutch70 said:**
> First of all, my comment wasn't directed at you, I'm sorry if you think it was. Everyone is welcome & even asked to help. That's why I suggested Virtualbox, a usb stick, or a small partition on your hard drive. Virtualbox is not as difficult as you may think & if you/it messes up, it doesn't really hurt anything.

Second, it's not that you're wasting anyone's time. We're here because we enjoy helping others. The problem is that there isn't very many people that can help you with an operating system that hasn't even been released. There's not even very many people that know what it looks like other than what they've seen in pictures or video's. That's the reason there is a testing & discussion forum, so we can all learn about it together.

How are we really supposed to help you with an operating system that isn't even finished?
How much experience do you think we have with it? 
I hope this doesn't come off the wrong way, I just don't know how else to say it.

My friend I still stand my position and telling you that this forum is made for helping people.:D
second of all, knowledge of people in here are not counting and weighting by their beans ):P):P . 
me with 5 beans could solve a problem that 1000+ beans said .....  . I can have 5k beans in 1 week;) if I want and just go to all posts and tell them install a new fresh version or wait for stable release. you know what I'm talking about;).
think Linux and help people to be a part of it.
By the way you may think I use Linux since two hours ago if you feel better :lolflag: . I hope you don't offer anymore solutions related to wait for stable version or..... when the problem can be fix in few simple steps.

think Linux and help people to be a part of it.
think Linux and help people to be a part of it.:guitar::guitar:

---

### Post by Dutch70 on 2011-04-10
Good for you, :roll: I still stand by mine as well & most would agree. 
Maybe one of these days, you'll understand why.

---

### Post by atul1412 on 2011-04-10
> **zigorati said:**
> hey my friend good news.... 
 
I found myself how to fix this problem. I hope works for you as well.
The problem is about shortcut conflict which is for gnome and unity. when we upgrade from gnome to unity there are some (for me two) conflict.
 
Okay, back to solution. follow exactly the process.
 
1- open your terminal
 
type this in your terminal or just copy and paste.
 
2- sudo apt-get install compizconfig-settings-manager
 
after that
 
3- ccsm
 
you will see a new window is opened. then in the top left corner u can find "Filter". type unity in the text field. after that you will see an icon with purple color. Just tick it and it will show you that there are some conflict with gnome. then disable all shortcuts which are for gnome and replace it by unity.then close it and restart your OS. 
 
I hope it works for you as well.
:popcorn::KS
 
 
I tried it...
after "sudo apt-get install compizconfig-settings-manager" comand it is showing 
compizconfig-settings-manager is already the newest version. :-( 
after that i tytped ccsm then it is saying Attribute error 
even terminal is not getting closed also...
;-( :-(

---

### Post by zigorati on 2011-04-10
> **atul1412 said:**
> I tried it...
after "sudo apt-get install compizconfig-settings-manager" comand it is showing 
compizconfig-settings-manager is already the newest version. :-( 
after that i tytped ccsm then it is saying Attribute error 
even terminal is not getting closed also...
;-( :-(

mm .. I'm sure the solution will fix the problem because I had the same problem and I did the same thing which I told you and now its done. Okay I just can tell you one thing, you should only follow these steps and you try it. I hope you get it solve buddy.

---

### Post by atul1412 on 2011-04-10
> **zigorati said:**
> mm .. I'm sure the solution will fix the problem because I had the same problem and I did the same thing which I told you and now its done. Okay I just can tell you one thing, you should only follow these steps and you try it. I hope you get it solve buddy.
Again tried but same errors and evrything Same without any Positive Results...
Lets C.. Hope 4 the Best.. m still trying out here..

---

### Post by andyatnimbin on 2011-04-17
> **atul1412 said:**
> Again tried but same errors and evrything Same without any Positive Results...
Lets C.. Hope 4 the Best.. m still trying out here..

I have been using ubuntu for years and still consider myself pretty dumb.  Here's my solution that seems to work:

I opened a folder on my desktop, navigated my way to /usr/share/applications scrolled down to "Terminal" and clicked on it, my terminal opened, I then typed in the command "gnome-panel" (minus the quotes) and got my original 10.10 panel and menus back.  I then went to System>Preferences>Startup Applications and added an item "Panel", with the command "gnome-panel". I then rebooted and it seems fine, I have my 10.10 panel and menus back and it works OK so far.  Hope this solves this for someone until the full release.

---

