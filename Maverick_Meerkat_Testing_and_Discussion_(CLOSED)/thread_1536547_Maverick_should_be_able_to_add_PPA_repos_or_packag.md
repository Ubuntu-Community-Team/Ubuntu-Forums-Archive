---
title: "Maverick should be able to add PPA repos or packages through apt-url"
date: 2010-07-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-07-22
Getting rid of the need for the lengthy deb/deb-src lines was an empty gesture. We need to stop coddling our users and live with the expectation that they'll be using PPAs.

---

### Post by castrojo on 2010-07-22
Software center?

---

### Post by Starks on 2010-07-22
You still have to manually add the PPA repo and update sources.

---

### Post by castrojo on 2010-07-22
I'm confused, doesn't this cover it? [https://wiki.ubuntu.com/SoftwareCenter#apturl](https://wiki.ubuntu.com/SoftwareCenter#apturl)

---

### Post by Starks on 2010-07-22
Unless something like apt:some-mesa-crap?channel=ppa:xorg-edgers is an option, then no.

---

### Post by castrojo on 2010-07-22
Well I would assume if the software center itself had information about the PPAs already that that would work how you expect.

Maybe mpt can clarify.

---

### Post by Starks on 2010-07-22
I'm quite aware that apt-url allows for this, but it's been disabled because developers don't want to investigate a sane and secure way of implementing it.

---

### Post by dino99 on 2010-07-22
how many LTS's ppa around there ? how many can be trusted ?

so, a new ubuntu release come each 6 months, and only a few geeks want packages from the future ;)

i clearly understand devs to stay away from this kind of request

ubuntu is not a video game  :lolflag:

---

### Post by philinux on 2010-07-22
How would a new user trust a ppa?

---

### Post by MacUntu on 2010-07-22
I honestly don't think it should be made too easy to add PPAs, because of

> **philinux said:**
> How would a new user trust a ppa?

How many Windows problems are caused by dubious 3rd-party applications (not talking about Nvidia drivers :P)?

---

### Post by zekopeko on 2010-07-22
> **Starks said:**
> I'm quite aware that apt-url allows for this, but it's been disabled because developers don't want to investigate a sane and secure way of implementing it.

Why don't you suggest a solution then?

---

### Post by sisco311 on 2010-07-22
> **Starks said:**
> I'm quite aware that apt-url allows for this, but it's been disabled because developers don't want to investigate a sane and secure way of implementing it.

They want, check out the link posted by whiprush.

---

### Post by Starks on 2010-07-22
Unless that proposal will let me add a PPA or install a PPA package by clicking on an apt-url button in Firefox, it's not the same.

As far I can understand through my readthrough, USC will still require the add-apt-repository (ppa:blahblah) or deb/deb-src method of adding PPAs before they show up.

---

### Post by 23dornot23d on 2010-07-22
PPA's How do we know if they are good or not ?

These are what I found when I looked for the gthumb PPA

[Official Site]("https://launchpad.net/%7Ewebupd8team/+archive/gthumb") as far as I know
deb [http://ppa.launchpad.net/webupd8team/gthumb/ubuntu](http://ppa.launchpad.net/webupd8team/gthumb/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/webupd8team/gthumb/ubuntu](http://ppa.launchpad.net/webupd8team/gthumb/ubuntu) lucid main 
But I am sometimes concerned when I see names that are not in the
list on the official one ..... it may be that this is a alias name and is ok.

it does give a warning

**Adding this PPA to your system**

                            You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:webupd8team/gthumb**           to your system's Software Sources.           ([Read about installing]("https://launchpad.net/+help/soyuz/ppa-sources-list.html"))         


But how do I know if its safe or not ?

sudo add-apt-repository ppa:nilarimogard/webupd8

I do a search on " nilarimogard " and get the following .... but is it good to use this
or not ?

[nilarimogard]("http://www.google.com/search?client=ubuntu&channel=fs&q=ppa+gthumb+nilarimogard&ie=utf-8&oe=utf-8")

this is just one of many - I am not picking on this .... it just happened to be the last one that I used

Is he a developer ?

( At least if you vet them and add them to an official listing then we have a good idea that we can use them safely - 
 to be a little more confident !!! )

---

### Post by Starks on 2010-07-22
Don't you need to be an Ubuntero to even make a PPA?

---

### Post by cariboo on 2010-07-22
Once you have signed the Ubuntu [Code of Conduct]("https://launchpad.net/codeofconduct/1.0.1"), you can create a ppa on your Launchpad profile page.

For more info on ppa's have a look [here]("https://help.launchpad.net/Packaging/PPA").

---

### Post by mc4man on 2010-07-23
> but is it good to use this
or not ?
If it does what you want without breaking anything or anything you care about then it's good, if not then it isn't.

> it does give a warning,,,,
Atm all lp ppa's say the same
> 
But how do I know if its safe or not ?
Till some other means, (and even then
Go to the lp package site for the ppa, there may be some  useful info
Look at the packages to be installed, do they remove and or upgrade any current installed packages, if so, decide if that's a problem.

If you add a ppa nothing changes till you install or update - pay attention to what's going to happen or review first in synaptic.

Ask around or do a little research on ppa, lp bugs filed, complaints ect.

As to the one you've mentioned, he does a very good job most of the time, - I'd consider him trustworthy, haven't used but have ck.'ed several packages,.diff's and control files, -  still would never install from  any ppa's blindly.

Atm I only use one on lucid, which I've come [to trust completely]("https://launchpad.net/~gstreamer-developers/+archive/ppa"), though always ck. the changelog

---

### Post by sisco311 on 2010-07-23
> **Starks said:**
> Unless that proposal will let me add a PPA or install a PPA package by clicking on an apt-url button in Firefox, it's not the same.



Don't get me wrong I like the idea, but for the time being, I think it's too early to implement it.

First they have to create a robust an updated rating system for the ppa repositories.

---

### Post by Nick_Jinn on 2010-07-23
Being slightly noobish, I am all in favor of coddling noobs by making it easy to customize....however, I dont think this should come at the expense of freedom or lack of options for devs and hackers who dont want to do things the easy way. Advanced options should not be sacrificed for ease of use for noobs, but I also like the direction linux is going in catering to people like me or me a few years ago.....thats how linux will grow and improve.



But maybe there is a way to work this? Maybe if there was better backup options, so that if you screw up your system you can completely restore it more easily, that could help......some users would like a better way to download third party software, even if it means more risk. I dont think we should limit those users just so you can have bragging rights about how they didnt have the opportunity to encounter problems. It should come with a warning that they act at their own risk.

Maybe there are ways to minimize the damage.....maybe you can try a virtual install and run your own desktop as a virtual machine to see how it would operate with the program installed, just to try it before committing to the change?

---

### Post by x-shaney-x on 2010-07-23
> **dino99 said:**
> how many LTS's ppa around there ? how many can be trusted ?

so, a new ubuntu release come each 6 months, and only a few geeks want packages from the future ;)

But PPA's aren't just about updated software.  I have several PPA's added and NONE of them include updated packages that exist in the repos, they contain packages that aren't available by any other means other than manual installation or compiling.

---

### Post by dino99 on 2010-07-23
> **x-shaney-x said:**
> But PPA's aren't just about updated software.  I have several PPA's added and NONE of them include updated packages that exist in the repos, they contain packages that aren't available by any other means other than manual installation or compiling.

of course my previous reply is not about special needs and awared users, but rather about those kids trying and installing everything they can find, even without security care, dependencies issues, ...

then complaining and whining because their great distro is broken or else

---

### Post by Nick_Jinn on 2010-07-23
lol


I remember just randomly intalling things from Synaptic thinking that it couldnt hurt to have them and might = better support down the line.....next thing you know I am doing a clean install. 

I have gotten pretty good at installations though.

---

### Post by jerrylamos on 2010-07-24
PPA's are a good tool for investigating possible bug fixes.  Most of the time on a launchpad bug I can follow the instructions for the PPA having a possible fix or bug investigation.  Sometimes I can't get the PPA on properly.

Since I've got several partitions busting one image doesn't blow me out of the water, just generates a couple hours work.

Jerry

---

### Post by ranch hand on 2010-07-24
> **jerrylamos said:**
> PPA's are a good tool for investigating possible bug fixes.  Most of the time on a launchpad bug I can follow the instructions for the PPA having a possible fix or bug investigation.  Sometimes I can't get the PPA on properly.

Since I've got several partitions busting one image doesn't blow me out of the water, just generates a couple hours work.

Jerry
Multiple installs are really nice.

If you do ISO testing you need to reinatall once in a while anyway.  I have one waiting for 
the A3 RC ISO right now.

---

### Post by nilarimogard on 2010-07-25
> **23dornot23d said:**
> PPA's How do we know if they are good or not ?

These are what I found when I looked for the gthumb PPA

[Official Site]("https://launchpad.net/%7Ewebupd8team/+archive/gthumb") as far as I know
deb [http://ppa.launchpad.net/webupd8team/gthumb/ubuntu](http://ppa.launchpad.net/webupd8team/gthumb/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/webupd8team/gthumb/ubuntu](http://ppa.launchpad.net/webupd8team/gthumb/ubuntu) lucid main 
But I am sometimes concerned when I see names that are not in the
list on the official one ..... it may be that this is a alias name and is ok.

it does give a warning

**Adding this PPA to your system**

                            You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:webupd8team/gthumb**           to your system's Software Sources.           ([Read about installing]("https://launchpad.net/+help/soyuz/ppa-sources-list.html"))         


But how do I know if its safe or not ?

sudo add-apt-repository ppa:nilarimogard/webupd8

I do a search on " nilarimogard " and get the following .... but is it good to use this
or not ?

[nilarimogard]("http://www.google.com/search?client=ubuntu&channel=fs&q=ppa+gthumb+nilarimogard&ie=utf-8&oe=utf-8")

this is just one of many - I am not picking on this .... it just happened to be the last one that I used

Is he a developer ?

( At least if you vet them and add them to an official listing then we have a good idea that we can use them safely - 
 to be a little more confident !!! )


This is why the Ubuntu Forums are sometimes better than just searching Google :)

Even though it was just an example, I'm going to answer to your post anyway: I am not a developer, I just maintain [some PPAs]("http://www.webupd8.org/p/ubuntu-ppas-by-webupd8.html") about applications I post about on WebUpd8.

---

### Post by 23dornot23d on 2010-07-25
Cheers for the reply and the full list of PPA's that you maintain ......

Will bookmark it for further use ..... 

Thank you ..... ;)

The [Blender 2,53 link is good]("http://www.webupd8.org/2010/07/blender-253-beta-3d-graphics.html") ,,,,,, was wanting the latest version. :D ty

---

