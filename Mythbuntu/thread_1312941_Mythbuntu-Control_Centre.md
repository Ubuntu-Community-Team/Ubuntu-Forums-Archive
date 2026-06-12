---
title: "Mythbuntu-Control Centre"
date: 2009-11-03
forum: Mythbuntu
---

### Post by Al_Vampyre on 2009-11-03
Just a quick question, the auto-builds/repos are supposed to be configurable from the MCC but I can't find any options to do so? Any ideas?

---

### Post by pros456 on 2009-11-03
couldn't see any options either, so I tried starting it from the command line and got lots of errors (I am not home now) about some file missing.

---

### Post by tgm4883 on 2009-11-03
What version of mythbuntu do you have installed?

What version of mythbuntu-repos do you have installed?

What errors are you getting?

---

### Post by Al_Vampyre on 2009-11-03
Mythbuntu is 9.10, MCC is 0.570ubuntu1 karmic, mythbuntu-repos is 6.10ubunt0+mythbuntu.

I'm not getting any erros because I couldn't remember (or find!) the command line code I'm just not seeing anything in MCC at all.

---

### Post by tgm4883 on 2009-11-03
command line would be

mythbuntu-control-centre

---

### Post by pros456 on 2009-11-03
The errors I saw was probably from 910, but I can't remember exactly since I had other issues with that and went back to 904.

I just tested this in 904, downloaded repos-deb and installed. I get no errors now but I can't see any options for repos in mcc either, where is it supposed to be. But maybe that is not going to work for 904 either.

---

### Post by tgm4883 on 2009-11-03
The MCC portion will only show up and work on 9.10 and future releases. For 9.04 and previous, you need to run
```
dpkg-reconfigure mythbuntu-repos
```

---

### Post by Al_Vampyre on 2009-11-04
> **tgm4883 said:**
> The MCC portion will only show up and work on 9.10 and future releases. For 9.04 and previous, you need to run
```
dpkg-reconfigure mythbuntu-repos
```

That was the command line I couldn't remember, not the one for MCC, still no options in the MCC even after the reinstall caused by the partial upgrade that hosed mythtv this morning.

---

### Post by red321 on 2009-11-14
I did an online update to 9.10 form 9.04 I dont get an option to chose repos, and apt-get doesnt find mythbuntu-repos.

Not a problem, as I know how to do it all manually, but seemed that I needed the repos package to get the repos package ...

---

### Post by tgm4883 on 2009-11-14
> **red321 said:**
> I did an online update to 9.10 form 9.04 I dont get an option to chose repos, and apt-get doesnt find mythbuntu-repos.

Not a problem, as I know how to do it all manually, but seemed that I needed the repos package to get the repos package ...

Yea, you do need the -repos packages to get the -repos package.  Read this [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by neutron68 on 2009-11-14
I'm getting an odd message from the Mythbuntu-Control Centre

```
Repositories:
- Reconfigure (as root) the following items:
	WeeklyLocation 
```

How do I do this as root?  
Do I have to activate the MCC with the sudo command?

Eric

---

### Post by Al_Vampyre on 2009-11-15
IIRC that isn't an instruction to you, that is the list of things MCC is going to carry out when you click apply.

---

### Post by neutron68 on 2009-11-15
> **neutron68 said:**
> I'm getting an odd message from the Mythbuntu-Control Centre

```
Repositories:
- Reconfigure (as root) the following items:
	WeeklyLocation 
```

How do I do this as root?  
Do I have to activate the MCC with the sudo command?

Eric
The reason I ask, is that when I click APPLY, the window goes dim and sits there doing nothing for HOURS.  I left it sit there for 2 hours and finally gave up on it and stopped it.  Thus, I believe it is unable to complete the task.  Given the message I quoted for you, my guess is that it can't complete the task because the MCC was started with a double click of the mouse, under control of the "eric" user, rather than root.  

Bottom Line questions:  
How do I get the command/function to complete successfully?  

Do I activate MCC with the sudo command (thus it would be running under root privilages)?

Eric

---

### Post by tgm4883 on 2009-11-15
> **neutron68 said:**
> The reason I ask, is that when I click APPLY, the window goes dim and sits there doing nothing for HOURS.  I left it sit there for 2 hours and finally gave up on it and stopped it.  Thus, I believe it is unable to complete the task.  Given the message I quoted for you, my guess is that it can't complete the task because the MCC was started with a double click of the mouse, under control of the "eric" user, rather than root.  

Bottom Line questions:  
How do I get the command/function to complete successfully?  

Do I activate MCC with the sudo command (thus it would be running under root privilages)?

Eric

You should be getting prompted for root privlidges when you click apply for that. You do not need to run MCC as root

---

### Post by neutron68 on 2009-11-15
> **tgm4883 said:**
> You should be getting prompted for root privlidges when you click apply for that. You do not need to run MCC as root
That sounds like a reasonable expectation.  In practice, there is no prompt asking for the root password, etc.  It would seem something is broken here?  Any suggestions on how to gather clues?

Appreciated,
Eric

---

### Post by Castrato on 2009-11-16
> **neutron68 said:**
> That sounds like a reasonable expectation.  In practice, there is no prompt asking for the root password, etc.  It would seem something is broken here?  Any suggestions on how to gather clues?

Appreciated,
Eric

I had this same issue.  To fix it, I opened the MCC, navigated to Repositories, then selected US from the dropdown.  Upon clicking Apply, I was prompted for my password.  This eliminated MCC from hanging after this change was made.

Before I did this I noticed that the Repositories tab had no server selected from which to download the weekly-build updates.  I do not know how this happened.  But what I described above fixes it.

---

### Post by novellahub on 2009-11-16
> **Castrato said:**
> I had this same issue.  To fix it, I opened the MCC, navigated to Repositories, then selected US from the dropdown.  Upon clicking Apply, I was prompted for my password.  This eliminated MCC from hanging after this change was made.

Before I did this I noticed that the Repositories tab had no server selected from which to download the weekly-build updates.  I do not know how this happened.  But what I described above fixes it.

I had the same issue.  After I set the server to PPA everything worked.  Without a server selected, the MCC would hang.

---

### Post by neutron68 on 2009-11-16
> **Castrato said:**
> I had this same issue.  To fix it, I opened the MCC, navigated to Repositories, then selected US from the dropdown.  Upon clicking Apply, I was prompted for my password.  This eliminated MCC from hanging after this change was made.

Before I did this I noticed that the Repositories tab had no server selected from which to download the weekly-build updates.  I do not know how this happened.  But what I described above fixes it.
**Thank you!! ** 

I didn't see the Repositories choice in the MCC.  After you mentioned it, I looked closer and noticed the elevator control on the right side of the window.  A scroll in the downward direction revealed Repositories.

I just set the country selector to US and THEN I got the password window for the sudo password.
All seems to be working as it was intended.
Thanks for the clues!

As a side thought...
**Why the heck would the makers of the MCC window not make the MCC window bigger so that ALL the MCC menu items could be visible??**  
Making the window big enough seems like an obvious design to me!

Eric

---

### Post by tgm4883 on 2009-11-16
> **neutron68 said:**
> **Thank you!! ** 

I didn't see the Repositories choice in the MCC.  After you mentioned it, I looked closer and noticed the elevator control on the right side of the window.  A scroll in the downward direction revealed Repositories.

I just set the country selector to US and THEN I got the password window for the sudo password.
All seems to be working as it was intended.
Thanks for the clues!

As a side thought...
**Why the heck would the makers of the MCC window not make the MCC window bigger so that ALL the MCC menu items could be visible??**  
Making the window big enough seems like an obvious design to me!

Eric

Because MCC is plugable, which means that third parties can make plugins that will work with MCC. The fact that you were able to select Repositories in MCC means that you have installed plugins that did not ship with MCC (because Mythbuntu-repos contains a plugin for MCC, it isn't shipped with it)

---

### Post by neutron68 on 2009-11-16
> **tgm4883 said:**
> Because MCC is plugable, which means that third parties can make plugins that will work with MCC. The fact that you were able to select Repositories in MCC means that you have installed plugins that did not ship with MCC (because Mythbuntu-repos contains a plugin for MCC, it isn't shipped with it)
Interesting.  What other Mythtv plugins are able to show up in the MCC window?  MythTube?  MythStream?

---

### Post by tgm4883 on 2009-11-17
> **neutron68 said:**
> Interesting.  What other Mythtv plugins are able to show up in the MCC window?  MythTube?  MythStream?

MCC plugin != MythTV plugin.

AFAIK, mythbuntu-repos is the only current external plugin for MCC

---

