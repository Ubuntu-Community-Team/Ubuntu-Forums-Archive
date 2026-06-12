---
title: "ubuntu 10.10 trouble with today's updates"
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mindblower on 2010-09-22
hi...this morning i've done a sudo apt-get update && sudo apt-get upgrade on my ubuntu 10.10...there was about 40 updates (and among these also compiz)...i use only officials ubuntu ppa...

after the upgrade the system become unusable...when i log in its starts a loop and open infinity windows on the panel and slow down the system until it crash...can someone help me?

forgive my bad english :'(

---

### Post by kerry_s on 2010-09-22
ouch! you should use synaptic, on the command line things get held back. synaptic also keeps a history so you can go back & check what was installed.

have you tried the fail safe log in?

---

### Post by searchfgold6789 on 2010-09-22
What sort of windows are they? Just blank ones, or are they of a certain program?

---

### Post by mindblower on 2010-09-22
> **kerry_s said:**
> ouch! you should use synaptic, on the command line things get held back. synaptic also keeps a history so you can go back & check what was installed.

have you tried the fail safe log in?

also with the fail safe log in it doesn't work... i'll try to search in synaptic


> **searchfgold6789 said:**
> What sort of windows are they? Just blank ones, or are they of a certain program?

wndows don't appear on the desktop, they're just in the panel and they have no name...

---

### Post by mindblower on 2010-09-22
now i've re installed compiz and metacity, windows don't appear again but inferior panel doesn't work and also compiz doesn't work

---

### Post by mastablasta on 2010-09-22
why are you using beta (testing) version?

---

### Post by mindblower on 2010-09-22
> **mastablasta said:**
> why are you using beta (testing) version?

why are you making nonsense questions? i'm using the beta because on HOME pc i don't need a stable system and if i find some bugs i can report them and help the community...
is it so difficult to avoid useless post?

---

### Post by Mark Phelps on 2010-09-22
Why don't YOU post in the correct forum?

This forum is reserved for Released versions of Ubuntu.

You should be posting this to the Maverick Development forum.

And next time, don't be rude to someone else who merely asked a question!

---

### Post by s.fox on 2010-09-22
Thread Moved to Maverick Development.

---

### Post by mindblower on 2010-09-22
> **Mark Phelps said:**
> Why don't YOU post in the correct forum?

This forum is reserved for Released versions of Ubuntu.

You should be posting this to the Maverick Development forum.

And next time, don't be rude to someone else who merely asked a question!

that question was "a little" teasing otherwise i wouldn't be rude

sorry for my posting mistake

---

### Post by recluce on 2010-09-22
> **kerry_s said:**
> ouch! you should use synaptic, on the command line things get held back. synaptic also keeps a history so you can go back & check what was installed.



Very bad advice here. Synaptic will happily do a "partial upgrade" that may bork your installation, read the Development Forum Sticky about that.

The safest way:

```

sudo aptitude update
sudo aptitude safe-upgrade

```

The key here is the "safe-upgrade" option, which will hold back on installing updates that have unresolvable dependency issues. apt-get does not have such an option, IIRC.

Maverick will not install aptitude by default, so you may have to install it:

```

sudo apt-get install aptitude

```

As to the OP's problem: I have no idead - and I assume that there is not enough information given to work with. Can you boot to a text console?

---

### Post by mindblower on 2010-09-22
> As to the OP's problem: I have no idead - and I assume that there is not enough information given to work with. Can you boot to a text console?

i've done the safe upgrade from aptitude...

yes, i've installed plasma desktop and on KDE session the system works... (but not compiz)

---

### Post by seeker5528 on 2010-09-22
> **recluce said:**
> Very bad advice here. Synaptic will happily do a "partial upgrade" that may bork your installation, read the Development Forum Sticky about that.

The safest way:

```

sudo aptitude update
sudo aptitude safe-upgrade

```

If you don't actually read what the package managers are telling you they are going to do before allowing the install to proceed or not, then none of the methods are going to be "safe". 

Outside of that...

Don't the Ubuntu devs still default Synaptic to a system install of type 'Default Upgrade'?

The 'Default Upgrade' in Synaptic will be the same as 'apt-get upgrade' at the command line. Which is probably safer than 'aptitude safe-upgrade' is during a development cycle since the safe-upgrade in aptitude will install things that 'apt-get upgrade' and the Synaptic equivalent won't.

Later, Seeker

---

### Post by cariboo on 2010-09-22
I've found that aptitude safe-upgrade to be safer than synaptic when it comes to partial upgrades. If you don't cancel the upgrades in synaptic, it will go ahead and uninstall the programs that it listed, whereas safe-upgrade will not upgrade or remove packages that are in conflict.

---

### Post by kerry_s on 2010-09-22
i prefer to use synaptic, because the gui is what most people will be using.
i've never had the cli break, the gui on the other hand, well the more people using it & reporting the problems the better.

off topic:
has anyone figured out where the mutter theme file is?

i figured out changing the dock icons & the panel background, but mutter is suppose to have a theme file. it even has a viewer "mutter-theme-viewer" to test the theme.

---

### Post by jerrylamos on 2010-09-23
> **recluce said:**
> Very bad advice here. Synaptic will happily do a "partial upgrade" that may bork your installation, read the Development Forum Sticky about that.

The safest way:

```

sudo aptitude update
sudo aptitude safe-upgrade

```

The key here is the "safe-upgrade" option, which will hold back on installing updates that have unresolvable dependency issues. apt-get does not have such an option, IIRC.

Maverick will not install aptitude by default, so you may have to install it:

```

sudo apt-get install aptitude

```



Amen!! Partial upgrades send you down the path to re-install.

Amen!! apt-get doesn't have any safeguards and on Maverick Beta hung apt-get caused me to have to re-install on two test pc's.

Update Manager no better.  I've had Update Manager kill a running Ubuntu.

All through Alpha updates with apt-get worked fine, until the updates from a base of 2.6.35-19 to 2.6.35-20, -21, -22 crashed three of my four test pc's and on each I had to install a new daily CD build, and even one of these updating with update manager got crashes with "Serious kernel problems".  More like Alpha problems than Beta.  Oof.

Wrote a bunch of launchpad bugs, now up and running O.K.

Jerry

---

### Post by jerrylamos on 2010-09-23
Achtung!  By default on install, CD Daily Build 20100920 Update Manager Software Sources had selected "third party software" and "third party software sources"!

Bad news.  Even aptitude had trouble with that. "third party" stuff could lead to all kinds of problems.

I un-checked the third party sources but did check partner.

I'll have to download latest daily build to see if that bad default still there.

Jerry

---

### Post by ronacc on 2010-09-23
both apt-get and synaptic have safegaurds , they both tell you what they are going to do and don't do anything until you tell them to go ahead , if you don't pay attention and tell them to remove something vital it's not their fault , it is yours .

---

### Post by recluce on 2010-09-23
> **ronacc said:**
> both apt-get and synaptic have safegaurds , they both tell you what they are going to do and don't do anything until you tell them to go ahead , if you don't pay attention and tell them to remove something vital it's not their fault , it is yours .

Of course you are right there, but it still doesn't help a bit. Many people don't read everything thrown at them. So it is much easier and safer to drive home "Use aptitude safe-upgrade" than to change human nature.

---

### Post by seeker5528 on 2010-09-23
> **jerrylamos said:**
> Amen!! apt-get doesn't have any safeguards and on Maverick Beta hung apt-get caused me to have to re-install on two test pc's.

Packaging errors are a whole different discussion, they will bite you no matter which package manager you use.

> **ronacc said:**
> both apt-get and synaptic have safegaurds , they both tell you what they are going to do and don't do anything until you tell them to go ahead , if you don't pay attention and tell them to remove something vital it's not their fault , it is yours .

There are no safegaurds against packaging errors and I have not read anything that indicates to me that aptitude has what I would call "safegaurds" against problems that arise as a result of packaging errors either.

 I do believe based on what others have posted in the past that in some small number of cases aptitude may provide better information about what went wrong and possible solutions. But I haven't seen an indication that makes me think the difference in that regard makes *that* much difference, certainly not enough to make me want to put up with aptitiude's ****.

Later, Seeker

---

### Post by ronacc on 2010-09-23
I agree that packaging errors are bugs and no package manager can protect against bugs . Also no package manager can completely protect against inattention or ignorance especially in a development environment . When people jump in at late alpha or beta status and blindly accept partial upgrades they will get bit , sad , but hopefully they will learn something .

---

