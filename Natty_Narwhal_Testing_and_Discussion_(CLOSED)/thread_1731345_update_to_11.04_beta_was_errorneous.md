---
title: "update to 11.04 beta was errorneous"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Rishi.r on 2011-04-17
i have recently updated to 11.04 b from 10.10 but while upgrading it displayed errors.I m new to ubuntu and wen i checked the linux image of 10.10 is still there and i am unable to update now as there some error in the linux image also grub-pc is corrupted.i tried through terminal to correct them but no progress.even update manager does not run and i cannot remove the 10.10;s linux image from synaptic.please help.also i got this error


E: linux-image-2.6.35-22-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.35-28-generic: subprocess installed post-removal script returned error exit status 1

---

### Post by sanderd17 on 2011-04-17
1) It's a beta, you should only install it for testing purposes.

2) are you able to boot? If not, can you run the bootscript: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

if you are able to boot, what is the problem?

---

### Post by Rishi.r on 2011-04-18
how to change the linux image of 10.10 to the latest of 11.04........i still get the old linux image option in boot up

---

### Post by howefield on 2011-04-18
Thread moved to "*Natty Narwhal Testing and Discussion*"

---

### Post by Harry33 on 2011-04-18
> **Rishi.r said:**
> i have recently updated to 11.04 b from 10.10 but while upgrading it displayed errors.I m new to ubuntu and wen i checked the linux image of 10.10 is still there and i am unable to update now as there some error in the linux image also grub-pc is corrupted.i tried through terminal to correct them but no progress.even update manager does not run and i cannot remove the 10.10;s linux image from synaptic.please help.also i got this error
E: linux-image-2.6.35-22-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.35-28-generic: subprocess installed post-removal script returned error exit status 1

Well well well,
I hope you have another Maverick (10.10) setup around to work with.
This because your upgrade procedure may have been screwed up badly.
Anyways, it happens.
I would not use the upgrade procedure at all in order to upgrade to an alfa or beta stage distro.
You may test Natty better by downloading Natty-beta2 ISO image, then creating an installation media (live CD or even better live-USB) with Maverick for example.

But of course you might yet try to take another look at your unhappy upgrade attempt.
Open Synaptic and then select from lower left hand side "Custom filters", then select from upper left hand side "Broken" and see which packages are broken.
Post that information here.

---

### Post by Rishi.r on 2011-04-19
no broken files are shown in synaptic except the old linux image for removal which cannot be removed

---

### Post by cariboo on 2011-04-19
I'd suggest your upgrade didn't complete, open a terminal and type:

```
sudo apt-get -f install
```

to make sure you have completed the upgrade.

---

### Post by beew on 2011-04-19
I hate to say "I told you so". First of all as Harry33 said upgrading (instead of clean install) is problematic especially for alpha and betas , secondly why, why why do you trade in your working system for a bug test release? What is with people with such short attention span than they are in a rush to upgrade a solid OS which is barely 6 months old and cannot even wait for the official release?

If I were you I wouldn't even try to fix your broken upgrade, even if you appear to succeed there may be hidden problems that won't manifest itself until later and it would be difficult to diagnosed. I hope you have a image of 10.10 from which you can restore your system but chances are you don't, in that case you are better off doing a clean install of either 10.10 (which you know works) or 11.04, which may or may not work but is getting better and give it a month after official release hopefully all majpr bugs would be worked out.

---

### Post by ikt on 2011-04-19
> **beew said:**
> What is with people with such short attention span than they are in a rush to upgrade a solid OS which is barely 6 months old and cannot even wait for the official release?

It's how we roll, waiting years for stable releases is so Microsoft. :popcorn:

---

### Post by beew on 2011-04-19
> **ikt said:**
> It's how we roll, waiting years for stable releases is so Microsoft. :popcorn:

Maybe for people who don't actually use their computers for work so it is ok to be in a constant alpha mode. Waiting for 1-1.5 year to upgrade your OS is hardly like MicroSoft. But here we are talking about new users who don't even have the patience to wait for the stable release to upgrade and then are surprised that their systems get hosed.

I also notice that many people who yelp the loudest "let the breakage begins" are not even Linux users. These guys use Windoze or Apple as their main OSes and then keep a Linux install in an old decrepit machine or in a partition to mess around. I keep Natty on an external drive so I don't mind "rolling" but I wouldn't be crazy or stupid enough to "upgrade" my main OS (Maverick) to a bug infested box so I can file reports. 10.10 is working as close to perfection as I can get on my main machine. :)

---

### Post by ikt on 2011-04-21
> **beew said:**
> Maybe for people who don't actually use their computers for work so it is ok to be in a constant alpha mode. Waiting for 1-1.5 year to upgrade your OS is hardly like MicroSoft. But here we are talking about new users who don't even have the patience to wait for the stable release to upgrade and then are surprised that their systems get hosed.

This is the thing, you mention stable vs alpha, technically, we shouldn't be having this discussion right now, despite what we think there's no such thing as an alpha or beta ubuntu linux, it's just an arbitary name they give at an arbitrary time for a 'freeze' of all the packages into the universe.

There's no reason why every single release, (that includes the non-LTS ones as well) from Alpha 3 to RC should be anything less than LTS stable. 

[http://ubuntuforums.org/showpost.php?p=10695308&postcount=5](http://ubuntuforums.org/showpost.php?p=10695308&postcount=5)

> **beew said:**
> 
I keep Natty on an external drive so I don't mind "rolling" but I wouldn't be crazy or stupid enough to "upgrade" my main OS (Maverick) to a bug infested box so I can file reports.

That's ok, for every bug there's 4 bug reports, so I think we need less bug reports and more bug triage atm :P

---

### Post by seeker5528 on 2011-04-23
> **ikt said:**
> This is the thing, you mention stable vs alpha, technically, we shouldn't be having this discussion right now, despite what we think there's no such thing as an alpha or beta ubuntu linux, it's just an arbitary name they give at an arbitrary time for a 'freeze' of all the packages into the universe.

There's no reason why every single release, (that includes the non-LTS ones as well) from Alpha 3 to RC should be anything less than LTS stable.

Debian doesn't have Alphas and Betas, they just have feature freezes and RCs, but using their definition of stable/unstable seems the most appropriate, since doing otherwise leads people who are unfamiliar with the process to false expectations about what their experience might be like if they decide to go to the unstable stuff. 

Alphas and Betas are not releases, they are stages of development with goals that are intended to be reached in order to be ready for a release, by definition they are never going to be stable. Because of the changed  stuff going in, in addition to not being stable, it's expected that at different times during the development period a higher percentage of people will be afflicted with crashes too.

Upstream developers don't have the resources to test every distribution with every combination of hardware, have different approaches to development, different QA philosophies, and in some cases an upstream may not even release things in a way that you could apply the term stable to, so even if distributions stuck with what upstream considers stable, there are still going to be problems that come up when distributions start doing their distribution specific stuff and when stuff from one upstream source starts causing integration issues with stuff from another, whether it's because stuff from one upstream is old and needs to be updated, both are new and less tested together, or whatever.

When something affects a large group of packages, some eglibc updates, some X.org updates, some ffmpeg updates, major new version of python, the gnome 2 to gnome 3 transition, etc... things become even more unstable, so maybe instead of the normal shifting of the sands you *always* expect during a development cycle, where you might find yourself ankle deep or calf deep, maybe you suddenly find yourself neck deep.

The Ubuntu devs *could* make more conservative choices for non-LTS releases, but in the bigger picture what would be the cost in terms of the pace of advancement. 

IMHO, it's a choice between getting stuff out earlier in a reasonable if not complete state, getting the feedback and bug reports of a larger audience and finding out the more general issues and corner cases and adapting as you go or holding stuff on the sidelines for a longer period until it is more complete, but with a smaller pool of people to get feedback and bug reports from and increased risk that when it *is* finally released to the larger audience it will be found that some major re-factoring is necessary that would have been a whole lot easier if it was found out at an earlier stage.   

The people that want new stuff want new stuff, for the people who don't care so much there are the LTS releases. The people who's needs are dictated by the hardware they have selected will always be stuck with a more difficult choice, sometimes they may have to stick with an older version to keep support, sometimes they may have to move to a newer version to get support, and it's not always something you know without actually trying different releases.

Later, Seeker

---

### Post by ikt on 2011-04-23
> **seeker5528 said:**
> by definition they are never going to be stable.

Yet the last several releases they have been.

> **seeker5528 said:**
> 
 Because of the changed  stuff going in, in addition to not being stable, it's expected that at different times during the development period a higher percentage of people will be afflicted with crashes too.

Indeed, which is why I mentioned in my other post, this period should be the alpha 2 to alpha 3 period.

> **seeker5528 said:**
> 
Upstream developers don't have the resources to test every distribution with every combination of hardware

Which is what we're for.

> **seeker5528 said:**
> 
The Ubuntu devs *could* make more conservative choices for non-LTS releases, but in the bigger picture what would be the cost in terms of the pace of advancement. 

I don't suggest they be conservative, I suggest they go even faster.

> **seeker5528 said:**
> 
IMHO, it's a choice between getting stuff out earlier in a reasonable if not complete state, getting the feedback and bug reports of a larger audience and finding out the more general issues and corner cases and adapting as you go or holding stuff on the sidelines for a longer period until it is more complete

I suggested a cross between the two, some features need to be out there early, while others stay a little longer in development, this fine line in what is released early and what is released late seems to me to be the difference between a buggy release and a stable release.

- ikt

---

### Post by seeker5528 on 2011-04-23
> **ikt said:**
> Yet the last several releases they have been.

Not if you apply the Debian definition of stable/unstable. 

Crashing or not crashing is only one factor in measuring stability. If you can't rely on something to have uniform behavior from one day to the next, provide the same configuration options, be compatible with your configuration files, be compatible with your scripts, it's not stable whether it crashes or not.


> Indeed, which is why I mentioned in my other post, this period should be the alpha 2 to alpha 3 period.

The devs seem to think they have a handle on it.

> Which is what we're for.

I have reported some things upstream, but generally speaking if it was provided by my distribution vendor, I expect that to be something worked out between the distribution vendor/package maintainers and the upstream, depends on what it is and what the upstream process is for reporting bugs. If you consider Ubuntu as a whole you also have to factor in if it's something Canonical maintained and supported or if it is something that is community maintained and supported.

> I don't suggest they be conservative, I suggest they go even faster.

The non-LTS releases are the 'go faster' releases.

Either you go faster and focus more on features, or you play it conservative and and focus more on fixing the quirks and crashers, it's difficult to get the crashers to a low number if there is no stability and the corner cases take time to weed out. Once things have begun to stabilize then you can start to see which crashers were just caused because a lot of changes were happening, which are important to fix due to significance or frequency, which ones you would like to fix but could be pushed off until post release if necessary and which ones could be pushed until the next development cycle.    

During the LTS development cycle things slow down because more conservative choices are being made. This doesn't always translate into being less crashy, the devs sometimes have to go with stuff that is a little more raw in the LTS releases because they have to also choose based on what they will be best able to support over the next 3 to 5 year period instead of the 18 months of a non-LTS product.

Not being a software developer I relate to it like this, I've run into odd occasional situation fixing PCs where the changes are the problem.

The way it develops is you have an issue to fix, which you do, but over the course of making changes to fix that problem you notice another, so you keep making changes, keep having the problem, eventually to find out that once you stop making changes, the problem doesn't occur anymore. As long as you keep making changes you never figure this out, even after you figure it out, you are never quite sure until the PC has been in use for some number of days or weeks without a re-occurrence.

Back to Ubuntu, the more things are changing the more they are the issues (non-LTS), the more measured/conservative the changes the more you can focus on the real problem issues (LTS).

> I suggested a cross between the two, some features need to be out there early, while others stay a little longer in development, this fine line in what is released early and what is released late seems to me to be the difference between a buggy release and a stable release.

Every release is buggy. Fix something over here, something breaks over there, fix the thing over there, something breaks somewhere else. 

Sometimes a release might actually be more buggy, sometimes it might just seem more buggy because you just happened to be one of the lucky one that were affected by the bugs that time around.

Later, Seeker

---

