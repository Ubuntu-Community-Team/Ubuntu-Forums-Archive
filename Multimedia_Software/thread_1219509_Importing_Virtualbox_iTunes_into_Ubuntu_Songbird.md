---
title: "Importing Virtualbox iTunes into Ubuntu Songbird"
date: 2009-07-21
forum: Multimedia Software
---

### Post by deathblossom on 2009-07-21
[B]Edited:

I did it the 'hard' way from a copy of the real thing.[/B]


-------
Sorry if this thread is really inappropriate, I didn't want to have to make account on their site if I could hopefully ask here. 

So, Songbird has some instructions on how to import iTunes libraries from Windows and Mac into Linux and they are really confusing me...

[http://wikifile://localhost/H:/file://localhost/H:/.songbirdnest.com/User:Mpurses/Importing_your_iTunes_Library_from_Windows_or_Mac_into_Songbird_on_Linux](http://wikifile://localhost/H:/file://localhost/H:/.songbirdnest.com/User:Mpurses/Importing_your_iTunes_Library_from_Windows_or_Mac_into_Songbird_on_Linux)

So, I have been using Virtualbox to sync with my iPod touch. My music isn't located in the virtual machine; however, I've been accessing my music from the VM by mapping a network drive to a shared folder (my home Music folder).

Now I want to import this library into Songbird in Ubuntu, while still keeping the ability to manage my library in Virtualbox. Which means I want to do this following the "Easy Way" listed in the guide instead of the more permanent "Hard Way", but...I can't figure out how to adapt it for my needs.

List format:
1. My iTunes library is at 
/home/user/Music/iTunes/iTunes Music Library.xml

2. Virtualbox iTunes thinks my Music is located at 
C:/Users/user

3. I tried to do 
ln -sf /home/user C:/Users/user

But it said that the directory C:/Users/user doesn't exist.

Even if you can't help me with this, if you can explain the general idea and what the commands mean, that would be helpful.

---

