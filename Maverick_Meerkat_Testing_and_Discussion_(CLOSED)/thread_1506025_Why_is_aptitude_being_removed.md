---
title: "Why is aptitude being removed?"
date: 2010-06-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-06-09
I thought aptitude was supposed to deprecate apt-get, but according to
[http://manishtech.wordpress.com/2010/06/08/ubuntu-maverick-development-updates/](http://manishtech.wordpress.com/2010/06/08/ubuntu-maverick-development-updates/)
it won't be installed by default any more (but still available in repos).

Any ideas why it's the other way around (apt-get "deprecating" aptitude)?

---

### Post by ronacc on 2010-06-09
because aptitude sucked ?

---

### Post by ranch hand on 2010-06-09
> **ronacc said:**
> because aptitude sucked ?
Not a nice thing to say.

I do agree however.

---

### Post by MCVenom on 2010-06-09
> **ranch hand said:**
> Not a nice thing to say.

I do agree however.
I must agree also. :P

---

### Post by ronacc on 2010-06-09
sorry ,I couldn't think of a more APT way to say it :lolflag:

---

### Post by Luke has no name on 2010-06-09
It is odd, considering Debian officially endorses Aptitude over apt-get (which may be out dated, but is still present on their website).

---

### Post by taavikko on 2010-06-09
You'll never make me use apt-get...never..

aptitude is IMO superior compared to apt-get

---

### Post by VMC on 2010-06-09
> **taavikko said:**
> You'll never make me use apt-get...never..

aptitude is IMO superior compared to apt-get

Same here. I stopped using apt-get once I understood aptitude.
The defacto read [here]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/").

---

### Post by mmix on 2010-06-09
aptitude-1 is good, and synaptic-2 also good.

1: console
2: gui

---

### Post by taavikko on 2010-06-09
> **mmix said:**
> aptitude-1 is good, and synaptic-2 also good.

1: console
2: gui

who needs synaptic, when there's "sudo aptitude" ;)
See, aptitude has it all...

---

### Post by dagrump on 2010-06-09
Lazy old farts like me.

---

### Post by 3rods on 2010-06-09
What is the proposed replacement if aptitude is supposed to take over apt-get and aptitude is being deprecated?

---

### Post by taavikko on 2010-06-09
> **dagrump said:**
> Lazy old farts like me.

I thought they were the ones that installed Mint :-\"

---

### Post by dagrump on 2010-06-09
Don't really care for green.

---

### Post by dtfinch on 2010-06-09
I use aptitude whenever apt-get does weird things like saying a ton of vital packages need to be removed to install something, or fails with a vague error like like "...but it is not going to be installed" without saying why. Aptitude will actually tell you why, and try to find optimal resolutions to conflicts rather than trying to remove half your system without explanation.

---

### Post by ronacc on 2010-06-09
it also refuses to install something if the will cause the removal of something it considers critical , which rarely coincides with my idea of critical.

---

### Post by Reiger on 2010-06-10
I'd prefer aptitude over apt-get. safe-upgrade speaks volumes as to why.
OTOH: I can't see what the benefit of apt-get is over aptitude, someone care to enlighten me?

---

### Post by lisati on 2010-06-10
Another vote for keeping aptitude here: it has some abilities by default that make it a nice alternative to apt-get.

Having said that, each has its merits..... :)

---

### Post by boonenoob on 2010-06-10
apt-get is faster if you know what you are installing. thats the only good thing that i know of.

---

### Post by lykwydchykyn on 2010-06-10
> **Reiger said:**
> I'd prefer aptitude over apt-get. safe-upgrade speaks volumes as to why.
OTOH: I can't see what the benefit of apt-get is over aptitude, someone care to enlighten me?

I'll second this question.  I've never understood why the Ubuntu community defaults to apt-get in all its documentation.  About the only thing I can think of that apt-get can do that aptitude can't is fetch sourcecode (apt-get source), but I find apt-src better for that anyway.

I'd be interested in hearing an intelligent set of reasons (read: developer response) why apt-get is preferred over aptitude.

---

### Post by lykwydchykyn on 2010-06-10
> **boonenoob said:**
> apt-get is faster if you know what you are installing. thats the only good thing that i know of.

You do know that you don't have to use the ncurses interface, right?  aptitude supports all the same CLI syntax as apt-get, plus additional commands.

Unless you're referring to that bit of database indexing aptitude does every time it runs (which is a tad annoying).

---

### Post by boonenoob on 2010-06-10
> **lykwydchykyn said:**
> 
Unless you're referring to that bit of database indexing aptitude does every time it runs (which is a tad annoying).
yah, that's what I was talking about.

---

### Post by Longinus00 on 2010-06-10
I assume they will leave aptitude in the server edition. The reason you probably don't need aptitude in a desktop is synaptic does the same thing but has a gui (they are both frontends to apt). I suspect that the people who dislike aptitude don't have to deal with any servers or headless installations.

What's ironic is that there was a GSoC project for making a gtk+ gui for aptitude which would make it a complete replacement for synaptic. With the continued development of software center I suspect synaptic will itself eventually be dropped from the desktop install.

---

### Post by LiquidMeson on 2010-06-10
And here I thought it was just cus apt-get is shorter to type.

sudo tasksel is a nice app for packages :p

aptitude will be missed, definitely...

---

### Post by ranch hand on 2010-06-10
> **Longinus00 said:**
> I assume they will leave aptitude in the server edition. The reason you probably don't need aptitude in a desktop is synaptic does the same thing but has a gui (they are both frontends to apt). I suspect that the people who dislike aptitude don't have to deal with any servers or headless installations.

What's ironic is that there was a GSoC project for making a gtk+ gui for aptitude which would make it a complete replacement for synaptic. With the continued development of software center I suspect synaptic will itself eventually be dropped from the desktop install.
I have to admit that if I was working with a server I would really want to use aptitude myself.

I occasionally use it when installing the netboot versions and it does have nice features if you do not have a gui yet.

---

### Post by cariboo on 2010-06-10
The devs tried leaving aptitude off of the Live CD a couple of releases back, I bugged it, and it was decided because aptitude didn't take up all that much space on the CD, it could stay in. I almost think someone on the dev team doesn't like aptitude. :)

---

### Post by McDuff on 2010-06-10
> **LiquidMeson said:**
> And here I thought it was just cus apt-get is shorter to type.


And even this is not true. Aptitude is apti<tab> which is four keys to hit whereas apt-get is at least apt-g<tab> which is six keys to hit.

---

### Post by null_pointer_us on 2010-06-10
> **Longinus00 said:**
> The reason you probably don't need aptitude in a desktop is synaptic does the same thing but has a gui (they are both frontends to apt).

They might as well remove nano since we have gedit and openoffice.org. /sarcasm

---

### Post by taavikko on 2010-06-10
> **cariboo907 said:**
> The devs tried leaving aptitude off of the Live CD a couple of releases back, I bugged it, and it was decided because aptitude didn't take up all that much space on the CD, it could stay in. I almost think someone on the dev team doesn't like aptitude. :)

How about re-filing it....

---

### Post by MacUntu on 2010-06-10
Go home, aptitude! :>

---

### Post by John Bean on 2010-06-10
> **McDuff said:**
> And even this is not true. Aptitude is apti<tab> which is four keys to hit whereas apt-get is at least apt-g<tab> which is six keys to hit.

Erm... apti<tab> is *four* keys?

---

### Post by MacUntu on 2010-06-10
alias a='apt-get' :P

---

### Post by MCVenom on 2010-06-10
> **null_pointer_us said:**
> They might as well remove nano since we have gedit and openoffice.org. /sarcasm
Actually it's more like let's remove (insert CLI editor here; aptitude) because we have GEdit (Synaptic and USC) *and* nano (apt-get), and we don't need two CLI editors, especially since (insert editor here) doesn't have any obvious advantages over nano for the average desktop user.

---

### Post by ronacc on 2010-06-10
sudo apt-get install aptitude :lolflag:

---

### Post by null_pointer_us on 2010-06-10
> **BlackOtaku said:**
> Actually it's more like let's remove (insert CLI editor here; aptitude) because we have GEdit (Synaptic and USC) *and* nano (apt-get), and we don't need two CLI editors, especially since (insert editor here) doesn't have any obvious advantages over nano for the average desktop user.

:confused:

Its hard to tell, but you seem to be drawing an analogy between nano and apt-get, when I think the analogies are more like this:

[INDENT]vi/vim/etc. : nano = apt-*/dpkg : aptitude

<CLI text editors> : <GUI text editors> = <CLI package managers> : <GUI package managers>[/INDENT]

Note the *lack* of any symbol expressing a relationship between the two analogies. Specifically, I am *not* saying that CLI tools are inherently more or less easy than GUI tools (although that might be true).

nano is nice and noob-friendly (for a CLI editor) because it's simple and lists all the basic text editor functions at the bottom. Similarly, aptitude makes a simple, coherent CLI out of, what is to a new user, the complicated apt-*/dpkg mess.

I don't see the point in eliminating something, like aptitude, that supposedly takes up very little space and is noob-friendly [for times when one cannot (or do not wish to) do the work in a GUI program].

Maybe removing aptitude from the standard install is part of some larger let's-transition-everything-to-the-GUI initiative, or maybe it was just a mistake. I don't see the rationale here yet. This is just speculation.

---

### Post by MCVenom on 2010-06-10
> **null_pointer_us said:**
> :confused:

Its hard to tell, but you seem to be drawing an analogy between nano and apt-get, when I think the analogies are more like this:

[INDENT]vi/vim/etc. : nano = apt-*/dpkg : aptitude

<CLI text editors> : <GUI text editors> = <CLI package managers> : <GUI package managers>[/INDENT]

Note the *lack* of any symbol expressing a relationship between the two analogies. Specifically, I am *not* saying that CLI tools are inherently more or less easy than GUI tools (although that might be true).

nano is nice and noob-friendly (for a CLI editor) because it's simple and lists all the basic text editor functions at the bottom. Similarly, aptitude makes a simple, coherent CLI out of, what is to a new user, the complicated apt-*/dpkg mess.

I don't see the point in eliminating something, like aptitude, that supposedly takes up very little space and is noob-friendly [for times when one cannot (or do not wish to) do the work in a GUI program].

Maybe removing aptitude from the standard install is part of some larger let's-transition-everything-to-the-GUI initiative, or maybe it was just a mistake. I don't see the rationale here yet. This is just speculation.
I'm saying that the rationale was probably simply because two package managers was one too many and many seem to prefer apt-get; it is, after all as has been pointed out it's standard in much of the documentation.

---

### Post by Simian Man on 2010-06-10
I never understand why people like Debian package tools.  How about having one package manager that is really good instead of two that have various defects?

---

### Post by snowpine on 2010-06-10
I always assumed the Ubuntu devs prefer apt-get to aptitude because apt-get is what Sidux uses, and Ubuntu is based on Sid.

---

### Post by cariboo on 2010-06-10
Here's my original bug #[lpbug]252044[/lpbug], from Intrepid testing. Should we submit a new one?

---

### Post by ronacc on 2010-06-10
that ones marked "fix released " so bug it again . I'll add my me too , just because I detest aptitude is no reason to take it away from those who like it .

---

### Post by taavikko on 2010-06-10
> **ronacc said:**
> that ones marked "fix released " so bug it again . I'll add my me too , just because I detest aptitude is no reason to take it away from those who like it .

I too would file a new bug for it.
Wonder how somebody thinks that 1,562kB can't be fitted on a install CD.

Remove synaptic by all means and replace it with USC, but don't touch aptitude :)

---

### Post by VMC on 2010-06-10
> **cariboo907 said:**
> Here's my original bug #[lpbug]252044[/lpbug], from Intrepid testing. Should we submit a new one?

If we keep the pressure on, maybe they will realize that we find it useful, and stop trying to remove it.

---

### Post by ranch hand on 2010-06-10
Well you have to have room for slide shows, patches for plymouth and, most importantly, more eye candy OTB.

These things are a lot more important than silly things like a tool to maintain your system.

If it was any good it would take up more room.

All that understood, please post the bug here so we can all join in the FUN.  I use it maybe once a year for something but it is nice to know it is there.

---

### Post by cariboo on 2010-06-10
Bug #[lpbug]592336[/lpbug], add your me too if you don't want it removed from the base install.

---

### Post by ranch hand on 2010-06-10
Done.

---

### Post by Jordanwb on 2010-06-10
I use aptitude to search for packages and I don't have synaptic available. Otherwise I use apt-get because it has less letters.

---

### Post by VMC on 2010-06-10
> **cariboo907 said:**
> Bug #[lpbug]592336[/lpbug], add your me too if you don't want it removed from the base install.

Thank you! I added my comments as well.

---

### Post by ratcheer on 2010-06-10
Also done.

---

### Post by Arand on 2010-06-10
I just spoke to Colin Watson on IRC and the rationale is basically size; approximately 2MB (which in the scope of things are very precious) will be gained by removing tasksel and aptitude.

The initial reason why aptitude was included in ubuntu was that the desktop installer (ubiquity) depended on it, but now the desktop installer has been rewritten to not require it unless in particular cases, and hence it goes.

The alternate install CD will still install aptitude and tasksel, since the debian-installer which is used in installation requires it.

Likewise the server install of ubuntu will still include it (presumably also since it uses debian-installer)

This was part of the "Maverick Spring Cleaning" which was discussed during UDS-M and is specified here: [https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-spring-cleaning](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-spring-cleaning)
As "Install tasksel and aptitude dynamically"

More info here: [https://wiki.ubuntu.com/FoundationsTeam/Specs/MaverickSpringCleaning](https://wiki.ubuntu.com/FoundationsTeam/Specs/MaverickSpringCleaning)
"We could substantially reduce the size of the minimal seed by installing tasksel and aptitude  dynamically, so that we don't end up with them on live-installed systems. We will still need to keep tasksel in the server seed."

I do personally disagree with the decision, and think that the usefulness of it DOES outweigh the duplication of a program (apt-get), and that the space gained by removal is considerable.

But by now I have also realised that Ubuntu WILL kill by babies, unavoidably, such is life.

And it's always just an apti.. hrm, apt-get, away.

- arand

---

### Post by McDuff on 2010-06-10
> **John Bean said:**
> Erm... apti<tab> is *four* keys?
more or less +/-1 :D
counting beyond 2 is not that easy :D

---

### Post by seeker5528 on 2010-06-10
Personally I don't find the curses interface of aptitude to be all that friendly and if I am not using the curses interface and want something more than apt-get then aptsh seems like the better way to go to me.....

[http://aptsh.berlios.de/howto.html](http://aptsh.berlios.de/howto.html)

If I type:

```
aptitude install mythtv*
```

It tells me:

> 0 packages upgraded, 0 newly installed, 86 to remove and 56 not upgraded.
Need to get 0B of archives. After unpacking 69.1MB will be freed.

If I type:

```
aptsh install mythtv*
```

It tells me:

> 0 upgraded, 39 newly installed, 0 to remove and 56 not upgraded.
Need to get 110MB of archives.
After this operation, 257MB of additional disk space will be used.

So aptitude doesn't support wild cards, I can deal with that. But why the hell does it want to remove 86 packages? :shocked:

And then there is command completion with aptsh when you are in the shell, if you have an idea what you are looking for, but don't know the exact package name.

Later, Seeker

---

### Post by null_pointer_us on 2010-06-10
> **seeker5528 said:**
> So aptitude doesn't support wild cards, I can deal with that. But why the hell does it want to remove 86 packages? :shocked:
Answer:

1. It doesn't support wildcards, so you are supplying it a different set of actions than you supplied to aptsh. Apples to oranges.

2. The media packages may still be broken? The packaging issue was apparently fixed, but possibly you ran into other broken packaging, or you updated from Lucid -> Maverick and still had some of the problematic packages on your system. I had to do a bit of manual removal/reinstallation to get it working again.

---

### Post by mc4man on 2010-06-10
> 2. The media packages are still broken

What makes you think that? - see absolutely no issues.

> But why the hell does it want to remove 86 packages?

Most likely marked as automatically installed with no current deps, aptitude by default will always want to remove, (though not always correctly or even  wanted.

---

### Post by eumel on 2010-06-10
> **ronacc said:**
> sudo apt-get install aptitude :lolflag:
+1

> **Jordanwb said:**
> I use aptitude to search for packages and I don't have synaptic available. Otherwise I use apt-get because it has less letters.

you can do it with less letters if you set an alias ;-) 

```
$ alias agi="apt-get install"
```
or 
```
$ alias install="aptitude install"
```

whatever you want.. i like the second way :-)

---

### Post by ronacc on 2010-06-10
> **mc4man said:**
> 
Most likely marked as automatically installed with no current deps, aptitude by default will always want to remove, (though not always correctly or even  wanted.

That is exactly the reason I totally detest aptitude and will NEVER use it . In addition to automatically installed with no current deps , aptitude insists on removing any non repo packages you have installed ,and since several of those are sine quo non for me ,aptitude is worthless.

---

### Post by mc4man on 2010-06-10
I don'y hve any use for it either but to each their own.
Obviously if one wants they can instll, as is there is the emerging sc for some, apt-get for suggesting commands and the most versatile - synaptic.

Too bad command-not-found doesn't work with sudo whatever, otherwise a small edit...

> doug@doug-desktop:~$ aptitude install yo-moma
The program 'aptitude' is currently not installed.  You can install it by typing:
sudo apt-get install aptitude
Install it for you now? ([Y]/n)  y

ect.ect.



---

### Post by VMC on 2010-06-10
> **mc4man said:**
> I don'y hve any use for it either but to each their own.
Obviously if one wants they can instll, as is there is the emerging sc for some, apt-get for suggesting commands and the most versatile - synaptic.

Too bad command-not-found doesn't work with sudo whatever, otherwise a small edit...

I'm tired of hearing , if you need it then just install it. 
With that kind of logic why not remove everything and if you need something just install it?!

---

### Post by ranch hand on 2010-06-10
> **VMC said:**
> I'm tired of hearing , if you need it then just install it. With that attitude why not remove everything, and if you need something just install it?!
There you go again, we are getting all this pretty, useless stuff (that could be easily installed) and you are complaining about the removal of useful things.

Just think a bit and you will see that with the room saved we could easily have an even bigger, better slide show at the end of installing the OS.  That would be awesumness personified.  Something we REALLY need to attract new users.

Sorry, couldn't resist.  Nah, not even really sorry.

Seems like the only things taken out are the tools you use on or for your computer and the ones added are fluff.

---

### Post by mc4man on 2010-06-10
> Im tired of hearing , if you need it then just install it. With that attitude why not remove everything, and if you need something just install it?!


^That's a bit melodramatic..

Personally I didn't remove it, nor think it matters if included or not and you all may get it restored - even though there hasn't been any compelling reasons stated here as to why it needs to be in the default install.

I certainly don't have any problem with non-essential and somewhat redundant packages being removed, no big deal either way.

I'm sure everyone has some packages and or things not enabled in the default install, so what. 
(Probably some more useful things to newer users that aptitude will ever be.

---

### Post by lisati on 2010-06-10
> **VMC said:**
> I'm tired of hearing , if you need it then just install it. 
With that kind of logic why not remove everything and if you need something just install it?!

Doesn't part of the fun of setting things up include anticipating what you might find useful? That is why I'm posting in the MM thread even though I haven't tried it yet....

---

### Post by ronacc on 2010-06-10
> **VMC said:**
> I'm tired of hearing , if you need it then just install it. 
With that kind of logic why not remove everything and if you need something just install it?!

[http://www.linuxfromscratch.org/ ](http://www.linuxfromscratch.org/ )

---

### Post by seeker5528 on 2010-06-10
> **mc4man said:**
> Most likely marked as automatically installed with no current deps, aptitude by default will always want to remove, (though not always correctly or even  wanted.

Doing ```
aptsh orphans | less -N
```

or from inside aptsh:

```
orphans | less -N
```

shows me 91 orphans, so that seems like a likely scenario, but it rarely seems like a good idea to automatically get rid of all those things. I've never seen any of the tools create a list of so called orphans that is limited only to just the things I actually want to get rid of. 

Comparing to Synaptic......

I think synaptic uses aptitude for the 'installed (auto removable' feature, aptitiude is recommended by Synaptic and Synaptic shows me 86 'installed (auto removable)' packages, but it doesn't just dump those packages without me telling it to. Unfortunately Synaptic also doesn't seem to provide a way to indicate those things should not be considered auto removable, but then again since it doesn't automatically want to remove them, it doesn't really make it a pressing issue.

The biggest complaint I see about aptitude is something along the lines of.... 'I used X to install some packages, now aptitude wants to remove a bunch of stuff'. If there is something that needs to be solved in dpkg or the apt utilities, it should be solved there, aptitude shouldn't be doing things in it's own way if that results in it not playing well with others.

IMHO, if there are no conflicts causing something to be removed and you didn't ask for something to be removed, it shouldn't be removed. So when I ask for something to be installed, don't ask for anything to be removed, and it tells me that if I proceed 0 packages will be installed, 0 packages will be upgraded, and 86 packages will be removed, that's a '**** you, if I wanted packages to be removed I would have asked for them to be removed, I'll use something else for my package management' offense. But maybe that's just me. ;)

Later, Seeker

---

### Post by Reiger on 2010-06-10
Aptitude only `wants' to remove packages which are either: no longer used by anything else on your system and not manually installed (through aptitude).

In order to tell aptitude not to mess with certain packages you can use hold and unmarkauto (sudo aptitude unmarkauto aptitude, sudo aptitude hold aptitude).

---

### Post by MacUntu on 2010-06-11
> **VMC said:**
> I'm tired of hearing , if you need it then just install it.

A bit misplaced in this case. apt-get and aptitude are used to complete the same tasks, so if they want to clean up and/or make place on the CD, removing one of them is more logical than eg. throwing out GIMP for Pitivi. :P

*I* am tired of hearing about the CD size limit. People that can download 700MB also can download 800MB or 900MB - I'm not buying the bandwidth argument. If it's about CD vs. DVD media: dedicated CD drives haven't been sold for years now. If your optical drive isn't ancient it at least can read DVDs. Price difference for (rewritable) blanks is (~0.10€) ~0.05€ around here.

So why don't they just make two versions: one without all the bells and whistles that easily would fit a CD, and one without this annoying size limitation.

// this is the end, my only rant, the end

---

### Post by null_pointer_us on 2010-06-11
Don't DVDs offer faster transfer rates, too?

---

### Post by xir_ on 2010-06-11
> **MacUntu said:**
> A bit misplaced in this case. apt-get and aptitude are used to complete the same tasks, so if they want to clean up and/or make place on the CD, removing one of them is more logical than eg. throwing out GIMP for Pitivi. :P

*I* am tired of hearing about the CD size limit. People that can download 700MB also can download 800MB or 900MB - I'm not buying the bandwidth argument. If it's about CD vs. DVD media: dedicated CD drives haven't been sold for years now. If your optical drive isn't ancient it at least can read DVDs. Price difference for (rewritable) blanks is (~0.10€) ~0.05€ around here.

So why don't they just make two versions: one without all the bells and whistles that easily would fit a CD, and one without this annoying size limitation.

// this is the end, my only rant, the end

Id suggest that if you have a cd drive then you should be using xbuntu or lubuntu. 


I think a blueprint should be made for defining what a xbuntu user should be and what a Ubuntu user should be. For example, Ubuntu should be i686 compiled whilst xbuntu should be i386. Ubuntu could be on a dvd with no file compression whilst xbuntu can be on a cd. 

Also there should be an easy migration tool, for newbies to convert between distros. There is no reason you couldn't change from a 386 xbuntu to a 686 Ubuntu via synaptics if you have a compatible chip.

---

### Post by slakkie on 2010-06-11
Removing aptitude, someone was high.

---

### Post by phillw on 2010-06-11
> **cariboo907 said:**
> Bug #[lpbug]592336[/lpbug], add your me too if you don't want it removed from the base install.

added

---

### Post by paul_in_london on 2010-06-11
> **cariboo907 said:**
> Bug #[lpbug]592336[/lpbug], add your me too if you don't want it removed from the base install.

+1 (even though I haven't done a fresh install via a Live CD for quite a while)

---

### Post by ibuclaw on 2010-06-11
Personally, I'm rather happy it is going.

With aptitude, since around 2008, I've always had to uninstall applications *twice*, as aptitude marks them for reinstallation immediately afterwards.

---

### Post by taavikko on 2010-06-11
> **ibuclaw said:**
> Personally, I'm rather happy it is going.

With aptitude, since around 2008, I've always had to uninstall applications *twice*, as aptitude marks them for reinstallation immediately afterwards.

Could you give us an example of such an package?
Never had issues like that.

Only thing that comes to mind that would trigger such behaviour is meta-packages.

---

### Post by blur xc on 2010-06-11
> **MacUntu said:**
> A bit misplaced in this case. apt-get and aptitude are used to complete the same tasks, so if they want to clean up and/or make place on the CD, removing one of them is more logical than eg. throwing out GIMP for Pitivi. :P

*I* am tired of hearing about the CD size limit. People that can download 700MB also can download 800MB or 900MB - I'm not buying the bandwidth argument. If it's about CD vs. DVD media: dedicated CD drives haven't been sold for years now. If your optical drive isn't ancient it at least can read DVDs. Price difference for (rewritable) blanks is (~0.10€) ~0.05€ around here.

So why don't they just make two versions: one without all the bells and whistles that easily would fit a CD, and one without this annoying size limitation.

// this is the end, my only rant, the end

I'll 2nd that...  Everything comes on DVD's now...  Ubuntu should do the same.  Or at least an Ubuntu lite that fits on CD and full featured Ubuntu that goes on a dvd.

BM

---

### Post by ratcheer on 2010-06-11
There ***is*** a DVD release of 10.04. I don't know what all it contains, but it is 4.1 GB in size.

[http://cdimage.ubuntu.com/releases/lucid/release/](http://cdimage.ubuntu.com/releases/lucid/release/)

Tim

---

### Post by ranch hand on 2010-06-11
> **ratcheer said:**
> There ***is*** a DVD release of 10.04. I don't know what all it contains, but it is 4.1 GB in size.

[http://cdimage.ubuntu.com/releases/lucid/release/](http://cdimage.ubuntu.com/releases/lucid/release/)

Tim
It is a very nice version of the alt install ISO with a huge system rescue deal.  Very powerful rescue tool.

---

### Post by taavikko on 2010-06-11
> **ratcheer said:**
> There ***is*** a DVD release of 10.04. I don't know what all it contains

Basically just the language packs.
[http://cdimage.ubuntu.com/releases/lucid/release/ubuntu-10.04-dvd-amd64.manifest](http://cdimage.ubuntu.com/releases/lucid/release/ubuntu-10.04-dvd-amd64.manifest)

@ranch hand, you have the same rescue tools with common CD-media.

---

### Post by cariboo on 2010-06-11
> **ibuclaw said:**
> Personally, I'm rather happy it is going.

With aptitude, since around 2008, I've always had to uninstall applications *twice*, as aptitude marks them for reinstallation immediately afterwards.

Boo for adding a -1 to the bug. :)

---

### Post by ibuclaw on 2010-06-11
> **cariboo907 said:**
> Boo for adding a -1 to the bug. :)

All in the service from your friendly neighborhood Spider-Man. :P

---

### Post by ibuclaw on 2010-06-11
> **taavikko said:**
> Could you give us an example of such an package?
Never had issues like that.

Only thing that comes to mind that would trigger such behaviour is meta-packages.

Let us know if you have trouble getting it: 
[http://download865.mediafire.com/myxn31jzzm9g/zkwzkawibwf/aptitude.ogv](http://download865.mediafire.com/myxn31jzzm9g/zkwzkawibwf/aptitude.ogv)

Regards.

---

### Post by seeker5528 on 2010-06-11
> **Reiger said:**
> Aptitude only `wants' to remove packages which are either: no longer used by anything else on your system and not manually installed (through aptitude).

Aptitude doesn't know what packages are used by something else and keeping track of manually installed packages in a way that is not shared among the different front ends is bad.

Keeping track of which package caused another to be pulled in is at best marginally better than just making a determination based on which packages list another package in their depends, recommends, or suggests fields. 

How it determines what is an orphan package isn't really the issue though, the issue is I don't want the few packages that I would like to continue to be showed as orphans to be removed automatically and the others I don't want to have to mark them as manually installed to keep them from being removed.

I don't see an obvious way to list the orphaned packages from within the aptitude curses interface so you can select them and choose to mark them as manually installed and doing this from the command line for 80+ packages is something I would rather skip.

Later, Seeker

---

### Post by ibuclaw on 2010-06-11
> **seeker5528 said:**
> Aptitude doesn't know what packages are used by something else and keeping track of manually installed packages in a way that is not shared among the different front ends is bad.

Keeping track of which package caused another to be pulled in is at best marginally better than just making a determination based on which packages list another package in their depends, recommends, or suggests fields. 

How it determines what is an orphan package isn't really the issue though, the issue is I don't want the few packages that I would like to continue to be showed as orphans to be removed automatically and the others I don't want to have to mark them as manually installed to keep them from being removed.

I don't see an obvious way to list the orphaned packages from within the aptitude curses interface so you can select them and choose to mark them as manually installed and doing this from the command line for 80+ packages is something I would rather skip.

Later, Seeker

For orphaned packages, that is kinda what deborphan is for... Not sure if janitor can do a similar thing though. :)

---

### Post by phillw on 2010-06-11
> **ibuclaw said:**
> Personally, I'm rather happy it is going.

With aptitude, since around 2008, I've always had to uninstall applications *twice*, as aptitude marks them for reinstallation immediately afterwards.

I have had instances when the behaviour of aptitude Vs apt-get is ever so slightly different. I know you tech-heads know of all the switches, but us mere mortals do not :lolflag:

Phill.

---

### Post by d3v1150m471c on 2010-06-11
> **taavikko said:**
> who needs synaptic, when there's "sudo aptitude" ;)
See, aptitude has it all...

some people are horrified by having to use the keyboard to navigate their computers. IE terminal. Sadly they're on linux, too. I say, if it isn't broken don't fix it *cough* 10.04 left side buttons *cough*

---

### Post by ibuclaw on 2010-06-11
> **d3v1150m471c said:**
> some people are horrified by having to use the keyboard to navigate their computers. IE terminal. Sadly they're on linux, too. I say, if it isn't broken don't fix it *cough* 10.04 left side buttons *cough*

But the thing is, not many people complained about that.

I didn't mind it, got used to it, and now I get confused if the buttons **aren't** on the left... ;)

---

### Post by ibuclaw on 2010-06-11
> **phillw said:**
> I have had instances when the behaviour of aptitude Vs apt-get is ever so slightly different. I know you tech-heads know of all the switches, but us mere mortals do not :lolflag:

Phill.

Which actually draws up to another annoyance of aptitude vs apt-get.

When you hit a dependency error, aptitude will *always* try to remove the packages you just marked for installation. Whereas apt-get will try to *upgrade* the broken packages so that the dependencies meet.

I like apt-get being like that. It always assumes you know what you are doing, and what you are doing is correct (unless there really are 0 solutions for a dependency mismatch). In comparison to aptitude, which IMO tries to be smarter than you, the user. Something it fails at time and time again.

But, maybe I'm trying too hard. :)
This user case certainly wouldn't happen on a stable system.

---

### Post by lisati on 2010-06-11
> **ibuclaw said:**
> 
I didn't mind it, got used to it, and now I get confused if the buttons **aren't** on the left... ;)

I was using Vista yesterday, and found myself looking for the buttons on the left..... :)

---

### Post by phillw on 2010-06-11
> **ibuclaw said:**
> Which actually draws up to another annoyance of aptitude vs apt-get.

When you hit a dependency error, aptitude will *always* try to remove the packages you just marked for installation. Whereas apt-get will try to *upgrade* the broken packages so that the dependencies meet.

I like apt-get being like that. It always assumes you know what you are doing, and what you are doing is correct (unless there really are 0 solutions for a dependency mismatch). In comparison to aptitude, which IMO tries to be smarter than you, the user. Something it fails at time and time again.

But, maybe I'm trying too hard. :)
This user case certainly wouldn't happen on a stable system.

Heck, I'm still struggling with [http://forum.phillw.net/viewtopic.php?f=4&t=9](http://forum.phillw.net/viewtopic.php?f=4&t=9) after a certain person kindly put more information on. :confused:


But that is what you tech people are good at :lolflag:

Phill.

---

### Post by ronacc on 2010-06-11
> **lisati said:**
> I was using Vista yesterday, and found myself looking for the buttons on the left..... :)

get a mac :lolflag:

---

### Post by cariboo on 2010-06-11
I setup two systems yesterday, Win7 and XP, strangely enough I only had a problem with XP looking for the buttons on the left.:lolflag:

---

### Post by jppr on 2010-06-12
today's kubuntu alternate install  aptitude assumptions are again, yesterday, it  was not ubuntu or Kubuntu live-cd installation...[IMG]http://www.google.fi/images/cleardot.gif[/IMG]

---

### Post by lykwydchykyn on 2010-06-12
> **ibuclaw said:**
> Which actually draws up to another annoyance of aptitude vs apt-get.

When you hit a dependency error, aptitude will *always* try to remove the packages you just marked for installation. Whereas apt-get will try to *upgrade* the broken packages so that the dependencies meet.

I like apt-get being like that. It always assumes you know what you are doing, and what you are doing is correct (unless there really are 0 solutions for a dependency mismatch). In comparison to aptitude, which IMO tries to be smarter than you, the user. Something it fails at time and time again.

But, maybe I'm trying too hard. :)
This user case certainly wouldn't happen on a stable system.

Aptitude offers you options of how to resolve the issue. The first option is usually the simplest, i.e. don't install these packages.  You can switch through all the possible dependency resolutions, something you can't do at all with apt-get.

And nearly every "aptitude wants to remove all these packages" problems I see people mention comes from mixing the use of apt-get and aptitude.  People who consistently use aptitude don't see these issues (I know I don't, and heaven knows I install/uninstall packages constantly).

It boggles my mind.  Aptitude, from an interface standpoint, is light years ahead of apt-get in so many respects, but people will still insist apt-get is better on the basis of trivial or anecdotal problems.

Removing duplicate tools I can appreciate.  Removing the one with far more features and a superior interface I can't.

---

### Post by taavikko on 2010-06-12
> **lykwydchykyn said:**
> 

Removing duplicate tools I can appreciate.  Removing the one with far more features and a superior interface I can't.

Ditto.

Mixing apt-get and aptitude is a sure way to eventually mess things up. IIRC synaptic is supposed to be dropped to be replaced by USC.
So why remove all the tools? one app one task?

---

### Post by jppr on 2010-06-12
People should understand a simple thing  ... when  package dependencies are not correct in what microdermabrasion is the  same you try to do updates, all packages are not updated and the system  can propose the removal of other packages. Myself is not a  problem to upgrade systems or to install new packages, aptitude or  synaptic. If package dependencies are not  correct synaptic suggests a partial update of which I never do. now, at least in  Kubuntu aptitude is again the default and to me it's ok

---

### Post by khelben1979 on 2010-06-12
> **taavikko said:**
> You'll never make me use apt-get...never..

aptitude is IMO superior compared to apt-get

For me it's the opposite. Using the apt-get has worked pretty good although it's far from perfect. aptitude did not work well in comparison the last time I used it a couple of years ago.

**Go apt-get!** :guitar:

*B.t.w. I'm writing this message from my old "resurrected powerbook lombard" using MacOS 9.1 with 64 MB of RAM.*

---

### Post by taavikko on 2010-06-12
> **khelben1979 said:**
> For me it's the opposite. Using the apt-get has worked pretty good although it's far from perfect. aptitude did not work well in comparison the last time I used it a couple of years ago.

**Go apt-get!** :guitar:


It's not just which works better, aptitude offers in features much more than apt-get, which makes it superior against apt-{get-cache}

Though, I never hardly use the ncurses interface of aptitude.

---

### Post by WitchCraft on 2010-06-12
Because APT now can do anything that aptitude could.
So why still have a wrapper around apt anymore, when the wrapper doesn't have more functions than apt...

---

### Post by jppr on 2010-06-12
Those  who begin to use the development versions should be the Ubuntu already a  basic knowledge that can be updated safely and understand the system  when the package dependencies are not correct, what then to do and how  to deal with that system decomposition, used them to update, then  apt-get, aptitude, update-manager or synaptic.

---

### Post by taavikko on 2010-06-12
> **jppr said:**
> Those  who begin to use the development versions

You don't use devel versions, you test them and report bugs, it isn't for day-to-day usage.

> **jppr said:**
> how  to deal with that system decomposition, 

What's breaking down of organic matter got to do with computers or software used on them?
Other than that most of the materials used here won't...

---

### Post by jppr on 2010-06-12
I mean  that if the updates make the safe and the new packages to install is  too difficult to whether the development versions use the correct option

---

### Post by 23meg on 2010-06-12
> **lykwydchykyn said:**
> 
Removing duplicate tools I can appreciate.  Removing the one with far more features and a superior interface I can't.

The obvious candidate for removal is easily revealed by comparing the reverse dependencies of apt and aptitude.

---

### Post by taavikko on 2010-06-12
> **23meg said:**
> The obvious candidate for removal is easily revealed by comparing the reverse dependencies of apt and aptitude.

And if you search deeper, most of them are already installed via other software...

---

### Post by 23meg on 2010-06-12
> **taavikko said:**
> And if you search deeper, most of them are already installed via other software...

"Installed via other software"? I don't quite follow that.

---

### Post by lithorus on 2010-06-12
Even inside X I still prefer aptitude over apt-get and synaptic. It's the only GUI (I consider it so) version of apt which is DE independent AFAIK.

---

### Post by mc4man on 2010-06-12
Putting aside any of the various advantages, personal preferences, mini lessons,  ect. as being irrelevant to the question, I still haven't seen even one decent reason why aptitude *needs to be part of the default install.*

Those that feel strongly about it will install it, those that don't won't even notice, and I doubt new users will be affected adversely whatsoever by it's absence.

I wouldn't doubt that the majority of the posters who are strongly 'backing' aptitude, when advising others in related matters, use apt-get most, if not all of the time in their recommended commands...

---

### Post by seeker5528 on 2010-06-12
> **lykwydchykyn said:**
> And nearly every "aptitude wants to remove all these packages" problems I see people mention comes from mixing the use of apt-get and aptitude.  People who consistently use aptitude don't see these issues (I know I don't, and heaven knows I install/uninstall packages constantly).

The way you state that might make one think that you think not playing well with others is completely legitimate, OK, behavior.

People should be able to use what's best for a given situation without having to worry that 'Oh my Supreme Deity!!! Aptitude, jealous **** that it is, is going to throw a fit about this.' 

Wouldn't it be better if all the apt front ends just got along.:p

Later, Seeker

---

### Post by ronacc on 2010-06-12
given that we will never agree on which to keep and which to dump , the only logical solution is to remove all of them leaving the user with a WYSWYG system that cannot be modified,changed or added to in any way .

---

### Post by Slug71 on 2010-06-12
Bugger it, take both and give us smart package manager. :p

---

### Post by lykwydchykyn on 2010-06-12
> **seeker5528 said:**
> The way you state that might make one think that you think not playing well with others is completely legitimate, OK, behavior.

People should be able to use what's best for a given situation without having to worry that 'Oh my Supreme Deity!!! Aptitude, jealous **** that it is, is going to throw a fit about this.' 

Wouldn't it be better if all the apt front ends just got along.:p

Later, Seeker

What makes you assume that it's aptitude, and not apt-get, that is not playing well with others?

Remember that upstream (Debian) has designated aptitude as the official package management front-end.

---

### Post by ronacc on 2010-06-12
just goes to prove s**t runs down hill .

---

### Post by TerminX on 2010-06-13
> **taavikko said:**
> You don't use devel versions, you test them and report bugs, it isn't for day-to-day usage.
Heh, not necessarily.  I've used nothing but the development branch of Ubuntu for years (and before that, Debian unstable, dating back to early 2003).  For me it's about wanting updated packages but not wanting to switch back to Debian.

I rather enjoy the constantly changing collection of packages and incremental upgrades to the overall experience during development.  Hell, when things are frozen before a release I even end up analyzing the changes between the Debian and Ubuntu versions of particular packages and pull down new versions from Debian half the time when the updates stop rolling in.

Then again, I still build my own kernel packages too and don't think I've run a distro supplied kernel since before 2.6.0, and up until a few months ago my installation was so old originally that it had been migrated from OSS to ALSA back when ALSA was first merged into the kernel.  I used to feel like I was a pretty good representation of the average Linux user but now I guess I'm just a freak. :p  I think of all the things Ubuntu has brought to the table my favorite would have to be PPAs full of random development builds of things.

It is kind of a pain in the *** when I don't reboot for a few months and discover something in the boot process has been changed enough to break my setup though, I'll admit that. ;)

---

### Post by taavikko on 2010-06-13
> **23meg said:**
> "Installed via other software"? I don't quite follow that.

Aptitude's dependencies
```
Depends: <libapt-pkg-libc6.10-6-4.8>
    apt
  Depends: libc6
  Depends: libcwidget3
  Depends: libept0
  Depends: libgcc1
  Depends: libncursesw5
  Depends: libsigc++-2.0-0c2a
  Depends: libstdc++6
  Depends: libxapian15
  Depends: zlib1g
```
Most of them are installed by default, regardless is aptitude installed or not.

---

### Post by 23meg on 2010-06-13
> **taavikko said:**
> Aptitude's dependencies
```
Depends: <libapt-pkg-libc6.10-6-4.8>
    apt
  Depends: libc6
  Depends: libcwidget3
  Depends: libept0
  Depends: libgcc1
  Depends: libncursesw5
  Depends: libsigc++-2.0-0c2a
  Depends: libstdc++6
  Depends: libxapian15
  Depends: zlib1g
```
Most of them are installed by default, regardless is aptitude installed or not.

I was talking about *reverse* dependencies, though; as in stuff that depends on aptitude / apt, not the other way round.

---

### Post by ibuclaw on 2010-06-13
> **lykwydchykyn said:**
> Aptitude offers you options of how to resolve the issue. The first option is usually the simplest, i.e. don't install these packages.  You can switch through all the possible dependency resolutions, something you can't do at all with apt-get.

That is via the CLI interface, I was referring to the curses interface.
> **lykwydchykyn said:**
> 
And nearly every "aptitude wants to remove all these packages" problems I see people mention comes from mixing the use of apt-get and aptitude.  People who consistently use aptitude don't see these issues (I know I don't, and heaven knows I install/uninstall packages constantly).

And I didn't say it tries to remove already installed applications. If I decide to mark package X for installation, and there is dependency issues, it just decides to untac that mark at the moment I press 'G'. So I need to go back and figure out just what is preventing it from being installed. And 'E' is usually completely useless to what the actual problem is.

The problem is that aptitude favours packages marked as "Manually Selected" for installation much too high.

---

### Post by fluteflute on 2010-06-14
As I see it: 
1. aptitude used to be superior to apt-get
2. as a result lots of people switched to aptitude
3. apt-get caught up
4. today: it doesn't make much difference which you use, as long as you don't switch between them.

---

### Post by lithorus on 2010-06-14
> **fluteflute said:**
> 
3. apt-get caught up
Does apt-get provide a ncurses user interface?
Until it does I don't see any reason to remove aptitude from standard.

---

### Post by 23meg on 2010-06-14
> **lithorus said:**
> Does apt-get provide a ncurses user interface?

Better questions: Why do we need an ncurses interface for package management in the default desktop installation in the first place? What are the use cases for it? Are they covered by other default applications? Who are the projected user groups that benefit from this interface? And if it were to be removed, how much worse off would they be?

---

### Post by fr3ak.m3 on 2010-06-14
> **taavikko said:**
> I too would file a new bug for it.
Wonder how somebody thinks that 1,562kB can't be fitted on a install CD.

Remove synaptic by all means and replace it with USC, but don't touch aptitude :)
I wonder why somebody doesn't want to download 1562k if they really want to use it.

---

### Post by _khAttAm_ on 2010-06-14
> **VMC said:**
> I'm tired of hearing , if you need it then just install it.
With that kind of logic why not remove everything and if you need something just install it?!
You can always get Debain Disks with everything in them and install them all that you want.

Removing everything and asking user to install everything is already implemented. it is called netinstall.. but since it is difficult for a newbie user to do it, there exists the desktop edition which has tried to incorporate whatever is required for a newbie to use.

Ubuntu still has a very small user base compared to other competitor OS. What if removing a package (which can be installed with one command for those who absolutely need it) made room for usability, beauty and user-friendliness...

what if vim or emacs was installed by default and was being removed.. I can assume similar responses here in the forum.. which are pretty useless.. install whatever you want to use.. remove whatever you don't like.. if your system does not have something that you need, you can always switch to another one that does.. and still if it is not good enough, you can collect like minded people and create another distro which has all you want...... I thought that was why "Linux" had "freedom" attached with it...

---

### Post by _khAttAm_ on 2010-06-14
> **Reiger said:**
> Aptitude only `wants' to remove packages which are either: no longer used by anything else on your system and not manually installed (through aptitude).

In order to tell aptitude not to mess with certain packages you can use hold and unmarkauto (sudo aptitude unmarkauto aptitude, sudo aptitude hold aptitude).

well, thats so convenient.. however, i like the apt way to do that.. without having to do anything...

if I really want those packages removed, I can always do apt-get autoremove..

---

### Post by seeker5528 on 2010-06-14
> **lykwydchykyn said:**
> What makes you assume that it's aptitude, and not apt-get, that is not playing well with others?

Remember that upstream (Debian) has designated aptitude as the official package management front-end.

Unlike aptitude, apt-get and most, if not all, other tools don't suddenly want to remove a bunch of stuff if you have used another utility to do installations.

Later, Seeker

---

### Post by lykwydchykyn on 2010-06-14
> **23meg said:**
> Better questions: Why do we need an ncurses interface for package management in the default desktop installation in the first place? What are the use cases for it? Are they covered by other default applications? Who are the projected user groups that benefit from this interface? And if it were to be removed, how much worse off would they be?

For gramma using the desktop it's irrelevant.  I think we can all agree on that.

I think the biggest issue is server users.  IMO having an interactive interface for package management makes server administration a lot easier.  Unless Ubuntu plans to start shipping a GUI with the server edition, it makes sense to include aptitude.

Anyway, I'm done, I've had my say and it won't likely change anything.

---

### Post by cariboo on 2010-06-14
Aptitude will still be included in the server installation and the alternate install.

---

### Post by zekopeko on 2010-06-14
> **lykwydchykyn said:**
> For gramma using the desktop it's irrelevant.  I think we can all agree on that.

I think the biggest issue is server users.  IMO having an interactive interface for package management makes server administration a lot easier.  Unless Ubuntu plans to start shipping a GUI with the server edition, it makes sense to include aptitude.

Anyway, I'm done, I've had my say and it won't likely change anything.

I fail to see how this affects server users. Aptitude is removed for the ubuntu-meta source package which builds ubuntu-desktop , ubuntu-minimal and ubuntu-standard. No mention of server in there.

---

### Post by linux-hack on 2010-06-14
I think is because they added a lot of aptitude feetchers to the apt-get and as it is the first one they decided may be to keep that one. and aptitude was taking to much space on the CD.

---

### Post by 23meg on 2010-06-14
> **lykwydchykyn said:**
> 
I think the biggest issue is server users.  IMO having an interactive interface for package management makes server administration a lot easier.  Unless Ubuntu plans to start shipping a GUI with the server edition, it makes sense to include aptitude.

More so than aptitude itself, tasksel is a must-have for the server variant, and it depends on aptitude, so removing aptitude from server is out of question, and isn't happening.

---

### Post by 23dornot23d on 2010-06-14
I am waiting to see where the removal of some of  the main Linux based applications and now the best command line installer (in my mind) will be leading us all to ..... 

Is there a hidden agenda here , has someone been employed to see how much they can stir up the Linux community.

One Question remains ..... GIMP   FIREFOX  and now what I consider to be the best of the command line package managers and installers is being removed ......

 ..... does it add value to the overall user experience removing this or does it just annoy the people that like it and will now have yet another package to go to the repositories for and download.

I really can see this heading to charging for programs that need downloading out of the repositories at some point - just me being cynical ..... 
When a billionaire runs a company I find it hard to believe that he is NOT going to reap some rewards back ...... but hey thats maybe me just worrying about having to spend some MONEY at some point.

But seeing as nobody has answered the question - a bit like Politics really .... when they don't want you to know whats really going on .... 

But a yes or no answer would be suffice.

So the one question - why is it really being removed .... is it for a better user experience. ?         and the music played on :guitar: .....

Lets just guess that the answer ....... should be YES ......

So when I go to look for a package from the command line and am not quite sure of its full title ..... aptitude will give me a list of packages 
(as long as its not over 40 with the text in the title)
and when I have installed a system like I did with KDE4 desktop when it was released
aptitude was the only thing that gave me reasonable information back to sort out my
problems ......

So how does apt-get give information back to the normal user thats useful for them to
track down problems ...... as I found it to be next to useless ..... maybe its changed
like F-spot has ...... as a replacement for GIMP. :lolflag:

---

### Post by seeker5528 on 2010-06-14
> **23dornot23d said:**
> So how does apt-get give information back to the normal user thats useful for them to
track down problems ...... as I found it to be next to useless 

What kind of information are we talking, the reporting of errors from dpkg will be the same no matter what front end is used, the way they display those errors may be different. If you are in a VT as opposed to a terminal window, then scrolling may be an issue or in a terminal window scrolling may be an issue if you are installing a lot of packages and some relevant error stuff scrolled out of the terminal buffer already.

Later, Seeker

---

### Post by 23dornot23d on 2010-06-14
One example .... when I do a upgrade .... 

I first get a list of items like this ......

[IMG]http://sites.google.com/site/23dornot23d/home/snapshot1.png[/IMG]


I then choose from this list what I consider will not destroy my system ......... say for instance the wrong graphics driver
being loaded up automatically .......

............ but usually with using part of a string of what I require to load up ......... 

I can find whats available ..... in the repository from the command line without going anywhere else ........

[IMG]http://sites.google.com/site/23dornot23d/home/snapshot2.png[/IMG]


What you get in apt-get is the following ,,,,,,,, no use whatsoever

[IMG]http://sites.google.com/site/23dornot23d/home/snapshot3.png[/IMG]

---

### Post by Atermoon on 2010-06-14
Ever tried
```
sudo aptitude search nvidia
```
?

---

### Post by linux-hack on 2010-06-14
> **Atermoon said:**
> Ever tried
```
sudo aptitude search nvidia
```
?

:lolflag:

---

### Post by 23dornot23d on 2010-06-14
Its **apt-get **that does not return a list ..... please show me how to do the list using apt-get

or does **apt-ge**t do the same ?

---

### Post by Atermoon on 2010-06-14
My bad, I thought you were talking about something completely different... although looking at it better, even if you were I don't get the meaning of my own post. Meh, I guess that's what happens when you stay awake for 39 hours backing up your damaged hard disk ](*,)
Sorry again :p

---

### Post by ronacc on 2010-06-14
> **23dornot23d said:**
> 

What you get in apt-get is the following ,,,,,,,, no use whatsoever

[IMG]http://sites.google.com/site/23dornot23d/home/snapshot3.png[/IMG]

use ```
 sudo apt-get install nvidia* 
``` note the wild card (*) and you will get the list .

---

### Post by 23dornot23d on 2010-06-14
ok ty ..... my bad too did not realize that you could do it that way ....... ty

using the * wild card works fine thanks ..... 

------------------------------------------------------------------------
[Edit added later ...]

I still like aptitude for the points system it adapts though ..... maybe someone

could show me how that works in apt-get too ......

---

### Post by xebian on 2010-06-14
> **23dornot23d said:**
> Its **apt-get **that does not return a list ..... please show me how to do the list using apt-get

or does **apt-ge**t do the same ?

The equivalent of 

aptitude search <pkg-name | regxpression>  is


apt-cache search <pkg-name | regexpression>

---

### Post by 23dornot23d on 2010-06-15
Cheers too Xebian ......

I found the points system to be useful in aptitude when there was a problem with packages that would conflict ...... 
maybe that is not too much of a problem if you do not start to mix and match repositories ...... 

I used to do it to get enlightenment running .... but have not succeeded yet on the latest version of Ubuntu ...... 
it works great in Mandriva 2010 though .... the package can be loaded as a separate desktop ...... DR17 ..... not e16

I have not seen it here in any of the package managers ...... but its a nice to have ....

---

### Post by ibuclaw on 2010-06-15
> **23dornot23d said:**
> Its **apt-get **that does not return a list ..... please show me how to do the list using apt-get

or does **apt-ge**t do the same ?

```
apt-cache search ^nvidia
```
Also, try not to talk with long pauses in-between your sentences. It breaks readability. ;)

Regards

---

### Post by Slug71 on 2010-06-15
[IMG]http://i45.photobucket.com/albums/f53/courtney2721/Screenshot-06152010-100236AM.png[/IMG]

:p

---

### Post by lithorus on 2010-06-16
> **Atermoon said:**
> Ever tried
```
sudo aptitude search nvidia
```?
And where would you find this information? This could be from a scenario where X is broken and you want to install the right driver...

> **ronacc said:**
> use ```
 sudo apt-get install nvidia* 
```  note the wild card (*) and you will get the list .
That command will just try to **install** all packages beginning with nvidia. Not sure that's a good idea...

---

### Post by ranch hand on 2010-06-16
It just gives you the list with the option of installing them. "n" + "enter" is not real hard to do.

Even I can do it so it can't be hard.

---

### Post by ronacc on 2010-06-16
> **lithorus said:**
> 
That command will just try to **install** all packages beginning with nvidia. Not sure that's a good idea...

since there are multiple packages beginning  with nvidia , it presents the list and waits for you to confirm , just say no, and rerun apt-get with the package name you want . If you have an itchy trigger finger and just say yes without thinking about what you are doing , thats not apt-gets fault .

---

### Post by 23dornot23d on 2010-06-16
I think that it has been proved now that we can get a list ......

The way of getting a list of packages was why the command was shown
as ronacc says ...... it asks for a Y/N answer to install by answering N
you do not install anything .........

but still nobody has answered the second part of the question

[B]............ There is a points system when using aptitude ....... ?

Does this exist in apt-get[/B]* ?*

I have not seen this in apt-get - can anybody shed any light on how you judge how bad
a install is going to be using apt-get ........

If you do not understand this question ...... please do not continue on the list theme
it is obvious that this can be done now ...... even if not as straightforward as the aptitude
command .............. which for any new user is brilliant ....... they see straight away what
is available ...... (they have no need to know about wild cards or apt-cache) to use it.

---

### Post by Longinus00 on 2010-06-16
> **ronacc said:**
> since there are multiple packages beginning  with nvidia , it presents the list and waits for you to confirm , just say no, and rerun apt-get with the package name you want . If you have an itchy trigger finger and just say yes without thinking about what you are doing , thats not apt-gets fault .

Why not just tab complete?

---

### Post by 23dornot23d on 2010-06-16
Ok another example ...... 


apt-get **FAILS** here ...... 

**apt-get install python-qwt5-qt4**

  python-qwt5-qt4: Depends: python-sip4 (>= 4.9) but it is not going to be installed
E: Broken packages


yet

aptitude **SORTS IT OUT      ( I know I am wasting my time here - last post )**

[IMG]http://sites.google.com/site/23dornot23d/python/python-files/aptitude.png?attredirects=0[/IMG]

---

### Post by ronacc on 2010-06-16
you obviously dislike apt-get , don't use it , use aptitude if that is what you prefer . worst case you can install it from synaptic or USC . BUT note I and several others who do prefer apt-get added our me too's to the bug about removing aptitude to support your choice so stop bashing apt-get.

---

### Post by ranch hand on 2010-06-16
> **ronacc said:**
> you obviously dislike apt-get , don't use it , use aptitude if that is what you prefer . worst case you can install it from synaptic or USC . BUT note I and several others who do prefer apt-get added our me too's to the bug about removing aptitude to support your choice so stop bashing apt-get.
Yup, I think aptitude is grossly confusing and a pain to navigate and use.

My me too is up there as the 1st or 2nd.  I think we need these tools because not everyone works the same way.

I don't even think that folks working the same way is a good idea.  As Bob Dylan said "Ain't no use talkin' to you, it's just like talkin' to me."   What a miserably boring way to live.

---

### Post by Longinus00 on 2010-06-16
> **ranch hand said:**
> Yup, I think aptitude is grossly confusing and a pain to navigate and use.

My me too is up there as the 1st or 2nd.  I think we need these tools because not everyone works the same way.

I don't even think that folks working the same way is a good idea.  As Bob Dylan said "Ain't no use talkin' to you, it's just like talkin' to me."   What a miserably boring way to live.

How is aptitude more confusing that apt get? It has exactly the same syntax.

---

### Post by ranch hand on 2010-06-16
I am talking about the silly menu stuff on it that you have to wade through when doing a netboot install for instance.

I usually just get out of there and use apt when I log in with no gui rather than bother doing it in aptitude.  Just too much fluff.

Now when I did it the first couple times or when installing Debian instead of Ubuntu, I use Aptitude because of all that "fluff".

For the net boot installs now I have a list of things I want installed and it is just easier to use apt and type it in at login.

---

### Post by lykwydchykyn on 2010-06-16
> **ranch hand said:**
> I am talking about the silly menu stuff on it that you have to wade through when doing a netboot install for instance.

Are you talking about aptitude or tasksel?

---

### Post by ranch hand on 2010-06-16
I have never seen much difference in them.

---

### Post by lykwydchykyn on 2010-06-16
> **ranch hand said:**
> I have never seen much difference in them.

huh...  ok.

---

### Post by 23dornot23d on 2010-06-16
> **ronacc said:**
> you obviously dislike apt-get , don't use it , use aptitude if that is what you prefer . worst case you can install it from synaptic or USC . BUT note I and several others who do prefer apt-get added our me too's to the bug about removing aptitude to support your choice so stop bashing apt-get.

They both have there uses ..... don't say I obviously dislike something ...... 

I can use my own words thank you and nowhere have I said that I dislike it ........ 

Here is what is getting me ...... 
Gimp went so ok I now have to install that ..... and also remove F-spot for Shotwell
 
Firefox is going for Chromium ... I will probably at some point have to re-install that ......... 

Aptitude looks as if its going so at some point ...... I will have to re-install that ....

I have no problems with what any body prefers ..... its just that they seem to be kicking out everything I was brought up with and still use .......

Not a problem you may say** I am but one user** ........ your turn may come one day .....
see how it feels to watch this take place ....... I have used linux for 36 years ...

I really do not want to say anything more I am too old to get upset or wound up about the lead developer removing package after package .......** that I use **........

As said I can go to the repository and re-install everything you take away ......

Just what is the reason ..... I have not got my head around any of this removal of applications yet ...... Its good that you ask but on the other hand people try to give valid reasons for why they like some thing and they take it they dislike the other thing.

A bit like a wife asking which dress do you like you point to one and she gets upset and says whats wrong with the other one then ...... but she really does not want to know !!!

:lolflag:

---

### Post by xebian on 2010-06-16
> **23dornot23d said:**
> Ok another example ...... 


apt-get **FAILS** here ...... 

**apt-get install python-qwt5-qt4**

  python-qwt5-qt4: Depends: python-sip4 (>= 4.9) but it is not going to be installed
E: Broken packages


yet

aptitude **SORTS IT OUT      ( I know I am wasting my time here - last post )**

[IMG]http://sites.google.com/site/23dornot23d/python/python-files/aptitude.png?attredirects=0[/IMG]

The only problem is you are not even using Maverick because python-sip4 is being replaced by python-sip.

But even then in real Ubuntu lucid this is what apt-get install will tell you
```

root@luci1:~# apt-get install  python-qwt5-qt4 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libblas3gf libdrm-dev libgfortran3 libgl1-mesa-dev libglu1-mesa-dev liblapack3gf libpthread-stubs0
  libpthread-stubs0-dev libqt4-declarative libqt4-dev libqt4-multimedia libqt4-opengl-dev libqwt5-qt4
  libqwt5-qt4-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev mesa-common-dev python-numpy python-sip4
  qt4-qmake x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev
Suggested packages:
  qt4-dev-tools qt4-doc libmysqlclient-dev libsqlite0-dev libsqlite3-dev libpq-dev unixodbc-dev python-numpy-doc
  python-numpy-dbg python-nose
The following NEW packages will be installed:
  libblas3gf libdrm-dev libgfortran3 libgl1-mesa-dev libglu1-mesa-dev liblapack3gf libpthread-stubs0
  libpthread-stubs0-dev libqt4-declarative libqt4-dev libqt4-multimedia libqt4-opengl-dev libqwt5-qt4
  libqwt5-qt4-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev mesa-common-dev python-numpy python-qwt5-qt4
  python-sip4 qt4-qmake x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev
0 upgraded, 27 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.6MB of archives.
After this operation, 74.3MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
root@luci1:~# 

```

As you can see it will install extra packages as needed including the python-sip4.

---

### Post by lykwydchykyn on 2010-06-16
> **23dornot23d said:**
> I have used linux for 36 years ...


Whoa, did I oversleep and it's 2027 already? :confused::p

---

### Post by ronacc on 2010-06-16
@ 23dornot23d I agree with you about what they are dropping ( gimp ,etc ) and the really stupid thing is that the excuse is to "save space " on the cd when if you go to [http://cdimage.ubuntu.com/releases/ ](http://cdimage.ubuntu.com/releases/ ) you will only find DVD's for all the later releases .So maybe it is only for the "testing" cd's .

edit , if you search prior forums you will see that I have bitched loudly about other removals also .

---

### Post by 23dornot23d on 2010-06-16
Sorry to have wasted all your time .... and mine too .... 
I started when I was 16 ....... I am 52 now .... Maverick is for youngsters I guess no problems
You are right too .... maybe I should stop using Linux .....
I am not using Maverick .... but where does it say that I have to use it to comment on it ...
I tried to give examples between the two commands ..... the usefulness of the points system in aptitude still has not been answered ....... because apt-get cannot do it ....
cheers ronacc ..... glad I do not stand alone on everything .....
(By keeping the development on a CD they are maybe trying to keep the workload down which I can understand and fewer packages to keep on top of)

---

### Post by Chesamo on 2010-06-16
> **23dornot23d said:**
> see how it feels to watch this take place ....... I have used linux for 36 years ...
I'm just going to cut in and remind you that Linux is [only nineteen years old](http://en.wikipedia.org/wiki/Linux).

---

### Post by ronacc on 2010-06-16
You are not the only geezer here , a suprising # of us were around when theese infernal boxes were born ( I'm 65  ) . Probably they are keeping the cd's for developement to save bandwidth and make it easier to d/l the dailys .So stick around and help us prove that linux isn't just for babies  .:lolflag:

---

### Post by 23dornot23d on 2010-06-16
Sorry I was using Unix before that .... my bad .... 

I feel better knowing that there are some older than me on here .... thats good to know
I never really know who I am addressing when I leave a comment and whether they
understand what it is I try to get across and has been pointed out before my use of
the language is not that good ...... but I can design and also think I have a useful
contribution to make ........ if people can understand why I am passionate about
Linux getting better ....... for all of us ....

---

### Post by Chesamo on 2010-06-16
> **23dornot23d said:**
> Sorry I was using Unix before that .... my bad ....
While Linux is UNIX-insipred, Linux is *not UNIX*. There are a lot of conventions in Linux that don't exist in UNIX, and vice-versa.

---

### Post by ronacc on 2010-06-16
I think we know the difference .

---

### Post by cariboo on 2010-06-16
This thread is about the removal of aptitude, not who's right and who's wrong, please keep on topic.

---

### Post by seeker5528 on 2010-06-17
> **23dornot23d said:**
> I then choose from this list what I consider will not destroy my system ......... say for instance the wrong graphics driver
being loaded up automatically .......

That part is no different than with apt-get. Small nitpick, the package management software doesn't load drivers, it just installs/upgrades them, only the upgrades are automatic and in a default install there will be several drivers installed that don't apply to your hardware, which ones actually get used is a whole other question.

> I can find whats available ..... in the repository from the command line without going anywhere else ........

Search stuff has already been discussed so let me just say.....

For me personally, aptitude doesn't really do much for me over apt-get relative to the way I work at the command line.

Typically if I just need to quickly install something I will just do apt-get. If I need more than that then aptsh fits my working style better.

You can compare for yourself from the manpages..... [aptitude manpage](http://manpages.ubuntu.com/manpages/jaunty/man8/aptitude.8.html), [aptsh manpage](http://manpages.ubuntu.com/manpages/karmic/man1/aptsh.1.html).

Of course aptsh is just a shell, it requires other utilities to be installed which may or may not be part of the default install.

To bring this back on topic, the real issue isn't that aptitude is being removed from the CD, the CD is too small these days. It's good to be committed to providing a CD sized image, but there will continue to be sacrifices and trade offs, because of the space concerns.

Even [Opendisk](http://www.theopendisc.com/) developers don't try to limit themselves to a CD sized image any more.

To me, the question is.... 

Why isn't there a DVD version of Ubuntu that provides the same installation experience with extra stuff included? 

That's compared to the current DVD experience where you either get the same installation experience, same packages, or you can choose to use the alternate installer, in which case you have to choose type of install, additional packages, etc....

The way I would envision that working is that the CD would still be the primary, so trade-offs in order to fit things on the CD would still apply to the DVD, the DVD should just include additional stuff, so things omitted from the CD could still be included on the DVD.

Later, Seeker

---

### Post by 23dornot23d on 2010-06-17
Its a old list ..... but ...... one command does all ......



Aptitude is the superior way to install, remove, upgrade, and  otherwise administer packages on you system with apt.  For one, since  it&#8217;s inception, aptitude has been solving orphaned dependencies.   Second, it has a curses interface that blows the doors off of dselect.   Finally, and most importantly, it takes advantage of one tool, doing  many many functions.  Let&#8217;s take a look:
 
[LIST]
[*]aptitude:  Running it with no arguments brings up a beautiful  interface to search, navigate, install, update and otherwise administer  packages.
[*]aptitude install:  Installing software for your system, installing  needed dependencies as well.
[*]aptitude remove:  Removing packages as well as orphaned  dependencies.
[*]aptitude purge:  Removing packages and orphaned dependencies as well  as any configuration files left behind.
[*]aptitude search:  Search for packages in the local apt package  lists.
[*]aptitude update:  Update the local packages lists.
[*]aptitude upgrade:  Upgrade any installed packages that have been  updated.
[*]aptitude clean:  Delete any downloaded files necessary for  installing the software on your system.
[*]aptitude dist-upgrade:  Upgrade packages, even if it means  uninstalling certain packages.
[*]aptitude show:  Show details about a package name.
[*]aptitude autoclean:  Delete only out-of-date packages, but keep  current ones.
[*]aptitude hold:  Fix a package at it&#8217;s current version, and don&#8217;t  update it
[/LIST]


And still nobody ..... yet has said anything about the last question ..........

Can Apt-get give you any indication using a points system as to how bad a screw up you
could get using it as opposed to using aptitude ....

Aptitude has saved my system in the past ..... instead of re-format and start again
aptitude has lead me the safest way back to recovering it .......

One command ...... its that simple ....

How much space are you expected to save by removing it ?

---

### Post by ranch hand on 2010-06-17
I think that you will find that most of us who do not use aptitude and are on this thread have joined the bug to leave aptitude on the default install.  Some have not.

This is not a thread that needs to make excuses for aptitude or apt.  We are not the ones removing aptitude.

Basically you keep asking th same question over and over and it is getting really old.  My response to the question is "who cares" as it has never, ever been a problem for me.

I suggest pulling in your horns on this one.  We may not use aptitude but most of us see no reason to remove it either.

Take it up with the devs if it is that important to you.

---

### Post by teh603 on 2010-06-17
So here's a problem.

I was under the impression that Synaptic was a frontend for Apt(itude). Does this mean that with the removal of Aptitude, that Synaptic will no longer work or be installed?

I'm using kpackagekit right now because I'm running kubuntu, but its just something that makes me a little worried. I don't like the Ubuntu Software Center, and would rather use Synaptic if its available and still works.

---

### Post by cariboo on 2010-06-17
Synaptic will still be around for another few releases, at least until The Software Center gets closer to being finished.

---

### Post by ranch hand on 2010-06-17
Synaptic is not going anywhere.  Even if it were you could install it just as you have to now.

If you go to synaptic>Settings>Preferences and check all the boxes there except the last one under the General tab, you will get more complete information.  In the lower left pane you will then see a Dependencies tab.

If you highlight synaptic and click on that tab you will find no mention of aptitude at all.

---

### Post by ronacc on 2010-06-17
as long as they don't dump dpkg and disable downloads in my browser I will be able to install apps .

---

### Post by mc4man on 2010-06-17
As long as the "untrusted" deal isn't taken to an extreme without providing for overrides then one should be able to do as they please.

The update manager now joins sc as not allowing installs from untrusted sources.

---

### Post by ranch hand on 2010-06-18
> **mc4man said:**
> As long as the "untrusted" deal isn't taken to an extreme without providing for overrides then one should be able to do as they please.

The update manager now joins sc as not allowing installs from untrusted sources.
That is a good one.  UM is an untrusted source.  This will do little to make it better.

---

### Post by ronacc on 2010-06-18
and when all else fails build from source !

---

### Post by ranch hand on 2010-06-18
> **ronacc said:**
> and when all else fails build from source !
Or use Squeeze.

---

### Post by ronacc on 2010-06-18
> **ranch hand said:**
> Or use Squeeze.

I haven't played with that one I'll give it a whirl .

---

### Post by ranch hand on 2010-06-18
I prefer Ubuntu but with plymouth seeming to be getting worse on my box and the dumbing down of Ubuntu to appeal to the shallow  end of the gene pool, I have got it installed and it will be taking the place the 10.04LTS was supposed to take.

This is an extreme bummer but an LTS is what I need for my boring, secure business OS.  One that will even boot without having to change the default menu.

An OS that is more interested in giving you tools to use than take them away is nice too, even if that means that you are to blame if you fry your install and do not have the advantage of an installation time slide show.

---

### Post by Zteam on 2010-06-18
Well, I would really miss aptitude thats for sure...

Of course I signed up on the bug report to keep aptitude.

One thing I really like is that aptitude gives more choice, if you need to fix a broken package.

And I also like that it will do a quick search for you, if you try to install a package with the wrong name.

Not to mention it actually tells you how many MB you gonna free then you ask it to remove package

---

### Post by teh603 on 2010-06-18
> **ronacc said:**
> and when all else fails build from source !If you know how to do that. From what I've read, the only way to do that right now is on the command prompt, and requires I use apt-get to download and install certain packages. Shouldn't I be able to do it from within Gnome or KDE without having to use Bash?

---

### Post by ronacc on 2010-06-18
> **teh603 said:**
> If you know how to do that. From what I've read, the only way to do that right now is on the command prompt, and requires I use apt-get to download and install certain packages. Shouldn't I be able to do it from within Gnome or KDE without having to use Bash?

If you are going to be poking around into the territory where building from source can take you , you really should have some familiarity with the command line . It is not considered an activity for the casual user .

---

### Post by jppr on 2010-06-20
[https://launchpad.net/ubuntu/maverick/+source/aptitude/0.6.1.5-3ubuntu1](https://launchpad.net/ubuntu/maverick/+source/aptitude/0.6.1.5-3ubuntu1)

---

### Post by cariboo on 2010-06-20
> **jppr said:**
> [https://launchpad.net/ubuntu/maverick/+source/aptitude/0.6.1.5-3ubuntu1](https://launchpad.net/ubuntu/maverick/+source/aptitude/0.6.1.5-3ubuntu1)

That means nothing, aptitude will still be in the repositories, it is just being removed from the Live CD. it can still be installed afterwards, and is still in the alternate install & server iso's.

---

### Post by teh603 on 2010-06-20
> **ronacc said:**
> If you are going to be poking around into the territory where building from source can take you , you really should have some familiarity with the command line . It is not considered an activity for the casual user .If its not an activity for the casual user, then why do I see it recommended so much?

If Bug # 1 is to ever get fixed, Ubuntu in some flavor is going to have a lot more users who won't be comfortable using the command prompt. I'm going to leave the exact implications of that up to y'all, but its just something to think about.

---

### Post by ronacc on 2010-06-20
I wouldn't know why you see building from source recommended in some of the other forum sections . this is the development and testing section most of the people here are definitely not casual users . As far as the command line is concerned I agree , it should not be needed ( at least not often) in the released version . Again what we discuss in this forum is the version under development , it is expected to be sometimes broken and buggy and abnormal procedures may be required to correct it .

---

