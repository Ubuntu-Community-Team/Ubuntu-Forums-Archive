---
title: "If the current fglrx driver is not working then why is exist in jockey?"
date: 2010-06-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-16
I was just wandering since the current fglrx driver that jockey show it i mean the current version doesn't even support high kernels let alone xorg 1.8 so why does jockey recognize it in Maverick?

Thanks in advance.

---

### Post by jfernyhough on 2010-06-16
It's in alpha. It's broken. What do you expect?

---

### Post by ranch hand on 2010-06-16
> **jfernyhough said:**
> It's in alpha. It's broken. What do you expect?
What?!!?  This looks bad for Ubuntu to people just coming in.  Oh the Gods we can't have this.

I figured I better get that out of  the way now.  Sooner or later some one is going to have a rant on here like that.

You did, however, leave out that it is all part of the FUN.

---

### Post by jfernyhough on 2010-06-16
New people just coming in to an early Alpha release?

I started playing with alphas back with Edgy. I got burnt, I held on for the RCs. I learnt some more, and started earlier with the following releases (Feisty at Herd 4 IIRC), until I had Intrepid on as my main OS from Alpha 2 and Jaunty from the toolchain upload.

Yes, a non-working system doesn't look great. But you don't usually install this stuff unless you know what you are doing - look at Arch for example. A great, well-regarded distro but you wouldn't use it unless you know your way around in a substantial level of detail.

---

### Post by ranch hand on 2010-06-16
Yup, but we have had a thread ranting about how the Alpha made Ubuntu look bad the last 2 cycles from people that claimed that they were not warned enough.

I, personally, do not understand haow illiterate people can find the Alpha releases.  You would think it would be tough.  If they actually can read maybe they should try it out on the download pages, the first screen of the installer and the heading of this forum.

---

### Post by aviramof on 2010-06-16
What i meant is if it's not working then what is he doing in Maverick repositories isn't there any one who is checking what is in there for compatibility?

The current official version doesn't even support kernels higher then 2.6.32 let alon xorg 1.8 which even the new 10.6 ati driver doesn't support.

The same goes with xsplash for instance who is also not compatible any more and yet he still exist there and even have a ppa in ubuntu-tweak.

---

### Post by ronacc on 2010-06-17
this is TESTING inconsistencies are normal here , the same situation sometimes exists with the Nvidia drivers , not everything is always in sync during testing , jockey just checks which drivers are available not which ones actually work . If you demand consistency you wandered into the wrong woods .

---

### Post by aviramof on 2010-06-17
Xsplash for instance is not compatible since lucid alpah was released so it's not in testing anymore and the fglrx should not have been in the Maverick in the first place but it's all academic in the end but still i think that the repositories should be sync better with lucid and Maverick.

---

### Post by Seren on 2010-06-17
> **aviramof said:**
> Xsplash for instance is not compatible since lucid alpah was released so it's not in testing anymore and the fglrx should not have been in the Maverick in the first place but it's all academic in the end but still i think that the repositories should be sync better with lucid and Maverick.

It is a placeholder package.

Even if it doesn't work, it is easier to left it where it is, than removing it altogether and then reinstall it later in the development cycle.

What would be the point for a packager to create an upgrade script removing fglrx or jockey while doing the reverse 2 months later ?

It's been maybe two or three years that "fglrx" is broken during the alpha cycle and AMD delivers a compatible version in the last week or so of the development cycle.

---

### Post by aviramof on 2010-06-18
The question is does xsplash will ever work again and i don't think so because of plymouth.

---

### Post by rajeev1204 on 2010-06-18
I agree with aviramof here.

This is not some closed alpha test program and its open to everyone.Iam sure everyone here knows the risks but some obviously broken things should definitely be taken care of since it just wastes time where people could be up and running testing other software in the system.

You guys seem to think everyone knows every single thing about the OS including xserver and xorg version numbers and which ones work .

If fglrx is offered by jockey, it means its available for testing .But when its already known to the devs that its a 100 % failure with x server 1.8 ,then whats the point of it appearing it there?

Its not the risks here which is the problem, its pointless packages being offered for testing under the guise of an alpha.


rajeev

---

### Post by ranch hand on 2010-06-18
> **rajeev1204 said:**
> I agree with aviramof here.

This is not some closed alpha test program and its open to everyone.Iam sure everyone here knows the risks but some obviously broken things should definitely be taken care of since it just wastes time where people could be up and running testing other software in the system.

You guys seem to think everyone knows every single thing about the OS including xserver and xorg version numbers and which ones work .

If fglrx is offered by jockey, it means its available for testing .But when its already known to the devs that its a 100 % failure with x server 1.8 ,then whats the point of it appearing it there?

Its not the risks here which is the problem, its pointless packages being offered for testing under the guise of an alpha.

rajeev
Once  again, read the stickies.  This question comes up all the time on  many packages during a development cycle.  It is answered in the Testing  FAQ stickie (or one of the others - I have not memorized them -  probably need to read them again myself).

As for xsplash, it should not even be in the repo.  Ii is in synaptic  right now on this install.  The only thing I can think of is that they  leave it there in case they decide to go back to it.

Do not make the mistake of thinking that because Ubuntu Tweeks has  something or does something that it has anything to do with Ubuntu  itself.  It is a 3rd party scripting device that may be dangerous on an  unstable (testing) install.

---

### Post by rajeev1204 on 2010-06-18
> **ranch hand said:**
> Once  again, read the stickies.  This question comes up all the time on  many packages during a development cycle.  It is answered in the Testing  FAQ stickie (or one of the others - I have not memorized them -  probably need to read them again myself).

As for xsplash, it should not even be in the repo.  Ii is in synaptic  right now on this install.  The only thing I can think of is that they  leave it there in case they decide to go back to it.

Do not make the mistake of thinking that because Ubuntu Tweeks has  something or does something that it has anything to do with Ubuntu  itself.  It is a 3rd party scripting device that may be dangerous on an  unstable (testing) install.


Ubuntu tweaks? I didnt mention it .:confused:

---

### Post by aviramof on 2010-06-18
I did for some reason it's still there in there sources list in maverick that is why i thought maybe it shoul work now but it didn't so just like the fglrx in jockey it is a package 
that should not be there and i'm sure that there are more not compatible packages in the main repos.

---

### Post by ranch hand on 2010-06-18
> **rajeev1204 said:**
> Ubuntu tweaks? I didnt mention it .:confused:
It was mentioned in one of the many whines by the OP.

Poor bugger insists on using a testing release and then wants it to work even using shortcuts designed for stable releases.

There gets to be a lot of self inflicted wounds that way.  I know this for a fact as I am very, very good at it myself.

---

### Post by exodus_ on 2010-06-18
This is alpha software!  There will ALWAYS be much more breakage than in even a beta or a release candidate.  This is normal whether or not the alpha release is public or private.  If you really need trouble-free operation using Alpha is not the route to go.  If you are testing and contributing to the project then you would already know such breakage is normal and to be expected.

Having the expectation for everything to work, or the packages to make sense during alpha stage is kind of silly in my opinion.  If you need or want to only have packages that are mostly going to work, then why aren't you using a current release?  This would be the only way to be sure that the packages are going to work in a reasonable manner.

If you were having this issue say under Lucid or Karmic, or one of the currently supported releases then I would probably have sympathy and be willing to help you out on this.  But complaining that there is breakage during alpha stage is really not the best way to get help.  Unfortunately the Ubuntu devs will just need to wait until a new version of the ATI drivers are provided upstream.

I am sorry if I am sounding a bit harsh, but I just never understood why people complain about alpha software like this, it just makes no sense to me!

---

### Post by rajeev1204 on 2010-06-18
Hi ranch

I was a nvidia user for 4 years and as we all know, nvidia is fast to add support for the latest x server and ati generally add support later on towards the ubuntu release dates.

I got a new ATI card and jumped into lucid alpha 3 without suspecting this and straightaway installed fglrx without anticipating this.Of course i did read the release notes before, but i had heard that (rumor) that xserver 1.7 support was coming, so when jockey offered it i jumped on it.Of course i was using the open source driver so i didnt really have trouble with display but still had to figure out that jockey made a mistake in offering the driver and that the xserver 1.8 support was still way off.Basically was misled .

Only later did they remove it from jockey after a bug was filed.

I hope now its clear from my perspective. Anyway its not something critical for me ,but just wanted to add some of my opinion.Not sure if the OP ran into big trouble with this .


rajeev

---

### Post by aviramof on 2010-06-18
All i said was that packages that are known not to work and most likely never will should not be in the repositories that all and the 
current fglrx driver will never work and xsplash is not working since ubuntu 9.10 or early alpah versions of lucid so he should have 
been remove from there along time ago and i'm sure that are a lot more things that should not be there anymore period.

And to be honest it's hard enaf to try to find good softwares from a 31 thousand packages and check softwares without the broken packages
let alone with them so some sort of effort not to add if not remove broken packages would be much appreciated.

---

### Post by exodus_ on 2010-06-18
> **aviramof said:**
> All i said was that packages that are known not to work and most likely never will should not be in the repositories that all and the 
current fglrx driver will never work and xsplash is not working since ubuntu 9.10 or early alpah versions of lucid so he should have 
been remove from there along time ago and i'm sure that are a lot more things that should not be there anymore period.

And to be honest it's hard enaf to try to find good softwares from a 31 thousand packages and check softwares without the broken packages
let alone with them so some sort of effort not to add if not remove broken packages would be much appreciated.

You're also complaining about this in an alpha release.  As mentioned read the stickies. this is normal!  If you had the same problem of a package being this badly broken in a released version (10.04 and below) then you would have something valid to complain about.

Why are you using alpha anyway?  Are you doing testing?  or are you just trying to stay with the "latest and the greatest"?  If it's the former, then cool, but don't come to the FORUMS to complain about broken packages because it's not going to solve ANYTHING.  If it's the latter, then you should be running 10.04 because that's the most STABLE release of "the newest and greatest".

xsplash is likely there because SOMEONE somewhere may have a valid use for it.  Just because it does not work for you, or have an apparent use does not mean the same is true for someone else.

Please, please go and [read the stickies]("http://ubuntuforums.org/forumdisplay.php?f=385") that are in the development forum.  They will show you how to PROPERLY report such issues as you are trying to do here.

Broken packages are very very normal during development while the devs work to make them all work together.  removing a package completely from the repos would not make much sense during development when it's just going to be part of the final release, now would it?  You just have to accept that there will be broken things, broken packages, and hey sometimes something may be done that breaks the whole darn system!

If you can't deal with this, then in my opinion, you should not be running ALPHA stage software.

Again, sorry if i sound harsh, but I just don't see the sense in these kinda of issues while the software is still clearly NOT READY for production use!

---

### Post by aviramof on 2010-06-18
I didn't read all of that but as i said xsplash is also not working in 10.04 because of plymouth so i do have a valid point you said so your self.

And i did tried ubuntu 10.04 but it didn't worked well for me not even the stable version it had problems with ubiquity and with installing grub 2 and other problems maverick is much better then the "stable" lucid.

---

### Post by ranch hand on 2010-06-18
So contact the devs and ask them or file a bug or both.  Complaining here is a waste of everyones time.

---

### Post by exodus_ on 2010-06-18
> **ranch hand said:**
> so contact the devs and ask them or file a bug or both.  Complaining here is a waste of everyones time.

+1

---

### Post by exodus_ on 2010-06-18
> **aviramof said:**
> I didn't read all of that but as i said xsplash is also not working in 10.04 because of plymouth so i do have a valid point you said so your self.

And i did tried ubuntu 10.04 but it didn't worked well for me not even the stable version it had problems with ubiquity and with installing grub 2 and other problems maverick is much better then the "stable" lucid.

I am not even going to attempt to help you if you're not even going to attempt to completely read what I said to you.  Xsplash is not being used anymore, and AFAIK you would need to do more than just install it to have it work.  10.04 uses Plymouth, so you would need to replace plymouth with xsplash.  Not something the average end user will need or want to do, but someone with special needs might be able to make use of xsplash and THAT is why it's in the repos. At least this would make sense to me, and I could be wrong!  If I am, someone feel free to correct me.

I am sorry you have issues with Lucid.  I personally think it's a nice release, but my experience is not yours.

Again, why are you using alpha software?  Do you fully understand this?  Right now, it's working for you, what happens when they release an update that could potentially leave your system in a non-bootable state?  What happens if they release something that BREAKS those things that are working?  Are you going to come whining on the forums where VERY FEW of the ubuntu devs hang out to complain about this?

Just because the alpha is working "better" for you NOW does not mean that tomorrow it will, too.  like i said tomorrow you could be left with a system that won't work.

IMHO, you'd be better off running lucid or another version and then post and get support or search in the forums for this.  Complaining about what you feel to be problems in the ALPHA release is not going to net you a whole lot of sympathy on here, mine included.

Again, sorry to sound so stern, but you're going about it in the wrong way if you actually want to get support on an alpha release.

---

### Post by aviramof on 2010-06-18
Forget about it i don't have to hear all your whining all i said is that the repositories should be maintain better and that it and don't worry about me i can handle with every update the developers would release.

---

### Post by ronacc on 2010-06-18
Us whining ??? every one of the multiple threads you have started here sounds like a spoiled 2 year old demanding his candy .

---

### Post by ranch hand on 2010-06-18
> **aviramof said:**
> Forget about it i don't have to hear all your whining all i said is that the repositories should be maintain better and that it and don't worry about me i can handle with every update the developers would release.
If, and I know this is tough, you would stop yelling and try thinking, you would realize that the repos are being developed along with the OS.  This is covered in one of the stickies by the way.

Some things are in there not because they work but because they are place holders.  I use an ATI card my self, I am aware, as you should be, that ATI does not put out a driver until close to the release date.  It will have to be in thee repo along with related packages.

I am sure that the devs would be real happy to put off putting all that stuff in the repos, just for you, so that they could be swamped with work right at the end of the cycle.  They, even less than us, really do not have time for your raving about things that are common knowledge and have been for several cycles.

Your type of ranting really belongs over in the community forums where pointless pissing and moaning is pretty much the norm.

---

### Post by exodus_ on 2010-06-18
@Ranch Hand - 

I agree with your whole post.  i just wish people would realize what is truly means to run an alpha release!

---

### Post by aviramof on 2010-06-19
What is so difficult to understand that i think that jockey should not detect a driver that is known not to work and a package like xsplash who doesn't work 
ever since the developers started using plymouth and most likely will never work again is that too much to ask?

---

### Post by exodus_ on 2010-06-19
> **aviramof said:**
> What is so difficult to understand that i think that jockey should not detect a driver that is known not to work and a package like xsplash who doesn't work 
ever since the developers started using plymouth and most likely will never work again is that too much to ask?

And if you were using an official release that is meant to be in production I would wholeheartedly agree with you!

However, and this has been my beef with you the whole time, you are running an ALPHA release of an operating system that is in ACTIVE DEVELOPMENT!  This means that new things are being brought into the mix, people are figuring out what works, what does not, and working to fix the things that do not work.

This is why breakage on an alpha release is normal and expected.  Why should they remove the package completely when they will be working to make the package work in the final release anyway?  Alpha software is really not something to use in daily production because maybe tomorrow they will change some software version, or some setting and "poof!" something else is broken!  Maybe a few days later they fix it, but then change something else and oops! it's broken again!

With a stable release, any updates are going to be mainly security and bug fixes, leaving it up to you, the sysop, to upgrade and maintain your system beyond that.

---

### Post by mc4man on 2010-06-19
aviramof
I think possibly you're missing the idea here - 
There will be from time to time packages available that can't be installed and or packages available that can be installed but absolutely shouldn't be.

The responsibility of what to do  - wait it out, use a ppa, not install, modify, update anyway, ect. lies solely with you.
If you don't know then again it's up to you to educate yourself - there is no hand-holding going on.

I don't have ati but recently a similar sitution existed with nvidia
If you had nvidia-current installed the available new xorg packages were uninstallable - one had to decide what to do.

If you had nouveau installed then xorg could be updated - after which nvidia-current could be installed, nothing would stop you from doing so except hopefully some common sense as doing so would bork your install to no small degree.

As I remember from lucid, while there were times things went south globaly (for everyone), you also on your own made some poor choices and suffered the consequences, no big deal really but nothing to complain about either...

---

### Post by Elfy on 2010-06-19
This is going nowhere. The thread was marked solved. The thread is now closed.

---

