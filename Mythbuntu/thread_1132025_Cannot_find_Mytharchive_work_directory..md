---
title: "Cannot find Mytharchive work directory."
date: 2009-04-21
forum: Mythbuntu
---

### Post by thafemann on 2009-04-21
Have you set the correct path in settings?

Okay, I haven't a clue.

I just got the ability to play DVD's working.  Now I want to import a DVD into the system.  It appears to import just fine; appears.  I haven't a clue on where it is located, if anywhere.

I poked around a bit and got these errors.

Cannot find MythArchive work Directory.  have you set the correct path in settings?

What settings where?  And what would be the correct path :)

Tom

---

### Post by klc5555 on 2009-04-21
> **thafemann said:**
> Have you set the correct path in settings?

Okay, I haven't a clue.

I just got the ability to play DVD's working.  Now I want to import a DVD into the system.  It appears to import just fine; appears.  I haven't a clue on where it is located, if anywhere.

I poked around a bit and got these errors.

Cannot find MythArchive work Directory.  have you set the correct path in settings?

What settings where?  And what would be the correct path :)

Tom

In Utilities/Setup | Setup | Media Settings menu is the item "Archive Files Settings".

Somewhere in here will be a blank to enter a path to a directory where you wish mytharchive to stick temporary stuff while it works.

Mytharchive is a frontend process, and usually runs with the privileges of your primary desktop account. For this reason I've found permissions problems to be a pain in the butt unless this working directory is put in this user's home directory. Therefore (in my case) the directory is set to:

/home/[me]/mytharchivetemp

Not terribly creative. Mytharchive will blow this directory away and recreate it every time it runs.

Standard mytharchive reference is here: [http://www.mythtv.org/wiki/Mytharchive#MythTV_Setup](http://www.mythtv.org/wiki/Mytharchive#MythTV_Setup)

---

### Post by thafemann on 2009-04-21
Trying it right now.  I'll let you know.

Ultimately, I have a DVD that I want to import.  This DVD needs to be played by several users on their computers.

Is there any way I can get paid support for doing this?  It sure would be nice to be able to talk to someone for $xxx dollars, instead of spend 2 weeks messing with something.

Tom

---

### Post by thafemann on 2009-04-21
You are right about the permissions thing.

Right now the share is set to

/usr/share/mythtv/mytharchive

The share permissions are 755, which you would think should be enough.

I am logged on with a local account (bob).  And I do not have SU rights.  I run SU but...for some reason, I don't know the password.  Hummmmmmmm....

Can you help with that?

I created the archive under /home/<bob>/mytharchive and it still complained about the path, with 777 permissions.

Any other idea?

Tom

---

### Post by klc5555 on 2009-04-21
> **thafemann said:**
> Trying it right now.  I'll let you know.

Ultimately, I have a DVD that I want to import.  This DVD needs to be played by several users on their computers.

Is there any way I can get paid support for doing this?  It sure would be nice to be able to talk to someone for $xxx dollars, instead of spend 2 weeks messing with something.

Tom

Only 2 weeks? Some of us have been messing with this for years and are only now occasionally getting a few things right!

Mythtv is powerful stuff, but it's hobbyware: people work with it because it's more fun than socializing with the neighbors and generally less dangerous than bowling. When this isn't the case, it's time to turn to the world of commercial products. :)

All the best!

---

### Post by thafemann on 2009-04-21
Got it!  :)

It has been one of those hobbies that I do, like sticking a knife in a light socket.

Truth be told, I have been messing with this on and off for years.  I get something working, and then something doesn't work.  I get another thing working, and then I run out of hard drive space.

I have been promising a few people a project for about 6 months now so it is getting a little old for them for me to say "wait".

Thanks for your help.  I actually did get something working.

Now, onto another issue.....another post.

Tom

---

### Post by DominicF on 2009-05-22
Hi,

I've been playing with Mythbuntu 9.04 for a weeks and now looking at Mytharchive I'm having the same problem as you describe.  I tried numerous suggestions but still not getting to a solution (in mycase I am tring to create a DVD iso from a recorded TV item).  

Have you managed to solve the issue in defining Mytharchive work directory and the permissions problem?

---

### Post by hundred1906 on 2009-07-11
I have the same "cannot find mytharchive work directory" problem. I tried changing the directory as above but no progress.

I am using a clean very recent MythBuntu on top of Ubuntu Jaunty 9.04. Straight out of the box - so to speak.

Has anyone found an answer yet. Is this the correct forum - would the code originator be looking in? or is there a better forum to seek an answer?

---

### Post by hundred1906 on 2009-07-26
Stupid of me. I was changing the entry for the archive shared directory. The entry I needed was just above that on the page. I had not noticed it because it is blank by default.

---

