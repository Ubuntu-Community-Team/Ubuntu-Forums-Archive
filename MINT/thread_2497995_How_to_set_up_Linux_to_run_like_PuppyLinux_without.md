---
title: "How to set up Linux to run like PuppyLinux without Password(s)?"
date: 2024-05-25
forum: MINT
---

### Post by 909mjolnir on 2024-05-25
I have been using Linux for a few years to do music on.  
It's been OK, except I tend to forget my passwords.  

Is there any way to set up Linux (like MsWindows with UAC (user account control) disabled), with all the password prompts disabled?  

I just can't remember my passwords at all sometimes.  
I hate having to do $ sudo [...] all the time.  

PuppyLinux doesn't have the support that I need

Can you help me?

---

### Post by TheFu on 2024-05-26
This is a terrible idea and you are likely to break your computer.  

To allow logins to happen automatically, it is dependent on the DE and the login manager.  There will be a config file under /etc/somewhere for the login manager where a default user can be set.  I use slim as my login manager and there is a /etc/slim.conf file.  Inside that text file, it is well commented to explain the options.  

It is highly unlikely you use slim for a login manager, so you'll need to figure out what is being used.  Perhaps gdm?  So, look for a gdm.conf file and look at it with **sudoedit** so you can make changes.  If you screw this up, you may not be able to get into the system.  To make recovery easier, I'd start by making a copy of the gdm.conf ---> gdm.conf-orig before doing anything else.

As for sudo not needing a password, yes it is possible.  It is crazy dangerous to set up a system that way, since a tiny script can be used to provide persistent remote access into your system if it has internet access.  You can make the sudo timeout much longer. Maybe that's a better compromise?
Better to use a yellow sticky and write your password, or half your password on it and put it on your screen.  *man sudoers* has the full documentation for the sudoers config file.  use **sudo visudo /etc/sudoers** to modify it.  Beware that if you screw up the file, you may need a flash "Try Ubuntu" drive to boot from to fix it.  Again, before modifying the file, best to make a copy of the original first.

Also, the GUI password prompts don't use sudo and I have NO idea if those can be forced off. I haven't launched any GUI program that prompted for elevated privileges in perhaps 20 yrs. Sorry.

---

### Post by 909mjolnir on 2024-05-27
@theFu

Thanks.  It's amazing how you know all these things.  
I appreciate your help.  I guess I'll leave it alone.

---

### Post by TheFu on 2024-05-27
> **909mjolnir said:**
> @theFu

Thanks.  It's amazing how you know all these things.  
I appreciate your help.  I guess I'll leave it alone.

I've been at this a long time. If you'd been doing something for 30 yrs, you'd expect some level of knowledge, right?

The other 99.9995% topics in the world - I'm clueless. The farther you get away from computers and networking, the less I know, unless it is a hobby or related to former work or formal training.  Everyone has their areas of expertise.

It is your system. Feel free to break it.  Just don't be surprised when that happens.

---

### Post by 909mjolnir on 2024-07-13
LOL, I'm not trying to break my system :D

---

### Post by currentshaft on 2024-07-13
What commands are you running that need sudo so frequently?

Alias them to your sudoers file and you won't be asked for a password to use them.

---

### Post by currentshaft on 2024-07-13
> **TheFu said:**
> This is a terrible idea and you are likely to break your computer. 

Sigh, the FUD.

You're not going to "break" your computer by using passwordless sudo. Nor is it "dangerous".

If you boot to a live Ubuntu image, you will have passwordles sudo.

If you've ever provisioned a cloud instance from Amazon or Google, you will have passwordless sudo.

If you've ever used any embedded system, it will likely not even have sudo, but only a root account.

Please stop reinforcing false notions that the sudo password provides some meaningful security boundary on Linux, or that all Linux systems need protection.

---

### Post by TheFu on 2024-07-13
currentshaft I consider much of what you post to be FUD as well. 

You've been here, mostly adding good stuff to the conversation for under 3 months. Thanks for that, but recognize many things are opinion and having a different opinion isn't bad.  We each have to guest/assess the person asking the question and tailor a reply based on that.  Sometimes I fail. Sometimes other people fail and I'm correct.  Only the OP can decide.

Puppy doesn't use passwordless sudo. You do know that, right?  My answer was specific to knowing how puppy works.

> Please stop reinforcing false notions that the sudo password provides some meaningful security boundary on Linux, or that all Linux systems need protection. 
This is false.  To an expert attacker, it may be true, but to the vast majority of attackers it is not.  Book learning seldom replaces experience in the real world.

---

### Post by currentshaft on 2024-07-13
> **TheFu said:**
> currentshaft I consider much of what you post to be FUD as well. 

I sincerely hope you will call it out as you see it and challenge incorrect assumptions or facts.

What happened here is OP asked to do something that millions of people do daily, in personal and enterprise computing environments, largely without consequence or a care in the world.

You contrived a boogeyman story about how it will "break" OP's computer and how it is "crazy dangerous", which is objectively and demonstrably false; the judgemental security "assessment" was not solicited nor warranted.

This sort of gatekeeping (which is not subtle, at all) is what keeps people from learning. And sometimes breaking systems and realizing consequences is part of learning. Any good parent^Wsysadmin knows that.

---

### Post by genesis170 on 2024-07-20
Hey 909mjolnir,


Skipping passwords entirely can be risky, but I get the frustration! Maybe a light desktop environment like Lubuntu could help? It's faster and less prompt-happy. Also, password managers are a lifesaver. There are some good ones out there that can integrate with your music apps. For physical and mental well-being, consider incorporating regular exercise into your routine. [Physical Education & Exercise Science]("https://fit-30.online/") has plenty of resources to guide you.

---

