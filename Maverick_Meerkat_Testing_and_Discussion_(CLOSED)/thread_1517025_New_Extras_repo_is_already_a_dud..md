---
title: "New Extras repo is already a dud."
date: 2010-06-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-06-24
[http://www.webupd8.org/2010/06/ubuntu-wont-become-rolling-release.html](http://www.webupd8.org/2010/06/ubuntu-wont-become-rolling-release.html)

What a terrible decision.

Why not just follow the rolling upgrade model that the Ubuntu-MozillaTeam is following? All supported releases get up-to-date Firefox in the main repo as a pushed upgrade.

Hardy, Jaunty, Karmic, and Lucid are all getting Firefox 3.6.4 whether Rick likes it or not.

---

### Post by VH-BIL on 2010-06-24
I agree.

---

### Post by nilarimogard on 2010-06-24
I'm not a developer but isn't it a bit hard to keep everything up to date and test all the apps depending on some package to make sure nothing breaks?

But then again other distros do it so Ubuntu could do it too, but it seems they like to take everything done by others and just modify it slightly (I remember a comment on a blueprint that said something like: "let's wait and see if some distro comes with [I don't know what patch for BTRFS] and we can use it without having to write it ourselves" (quote from memory, might the real one might be completely different but the idea is the same).

---

### Post by VH-BIL on 2010-06-24
What is the difference between the distributions, If I can not find a Lucid package I have installed a Karmic one and it worked fine.

---

### Post by 23meg on 2010-06-24
> **Starks said:**
> [http://www.webupd8.org/2010/06/ubuntu-wont-become-rolling-release.html](http://www.webupd8.org/2010/06/ubuntu-wont-become-rolling-release.html)

What a terrible decision.

You make it sound like it's a new decision. It was the intention from the start; Rick merely clarified it now.

> **Starks said:**
> Why not just follow the rolling upgrade model that the Ubuntu-MozillaTeam is following? All supported releases get up-to-date Firefox in the main repo as a pushed upgrade.

Hardy, Jaunty, Karmic, and Lucid are all getting Firefox 3.6.4 whether Rick likes it or not.

The reason that's happening isn't the desire to ship the latest Firefox in every supported Ubuntu release; it's [a change in the stable release support model]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model") in accordance with the upstream release schedule changes.

---

### Post by davideotape on 2010-06-24
That's confused me. I though the whole idea of that bluprint and spec was that developers could get the latest versions of their applications in older Ubuntu releases.

---

### Post by Luke has no name on 2010-06-24
Ubuntu should not be a rolling release. It would be hard to coordinate another repo made for this purpose, and stable releases certainly should not have rolling software upgrades outside bugfixes.

If you want that, get Arch, Debian Sid, or Ubuntu's alpha releases.

---

### Post by seeker5528 on 2010-06-24
> **Starks said:**
> Why not just follow the rolling upgrade model that the Ubuntu-MozillaTeam is following?

Just because the combination of development and trademark policies of one upstream project make it more difficult to deal with security issues without updating to newer versions of their software, doesn't mean quicksand should be spread out across the release.

People that choose rolling releases know, or should know, by definition it's not stable. People that want stable don't want the sand shifting under their feet all the time.

That's not to say people shouldn't be offered a choice, but generally speaking, it should be something they have to choose, whether it's by distribution or by application.

Later, Seeker

---

### Post by ronacc on 2010-06-24
> **seeker5528 said:**
> 
People that choose rolling releases know, or should know, by definition it's not stable. People that want stable don't want the sand shifting under their feet all the time.

Later, Seeker

you don't spend much time at the beach do you ?

---

### Post by ronacc on 2010-06-24
while ubuntu is not a "rolling release " and I am not in anyway advocating that it become one, insisting that what it was released with is what you are "stuck" with , is almost criminally stupid . there are several things that for real practical security reasons MUST be absolutely the latest available , For instance your browser ( which ever one you choose ) , mail and contact prg , and these days even your PDF reader . While linux is nowhere near as big a problem as MS in this respect we are not bullet proof .

---

### Post by oOarthurOo on 2010-06-24
> **Luke has no name said:**
> Ubuntu should not be a rolling release. It would be hard to coordinate another repo made for this purpose, and stable releases certainly should not have rolling software upgrades outside bugfixes.

If you want that, get Arch, Debian Sid, or Ubuntu's alpha releases.

You're probably the first person I've ever seen describe Debian as a rolling release. Their motto is never release till its done. They're famous for stability. Sid is never released. Testing is not a release. If you want a rolling release based on Sid, use Sidux.

---

### Post by MCVenom on 2010-06-24
I for one, love the idea, and am ecstatic it is being implemented. :D

---

### Post by seeker5528 on 2010-06-26
> **ronacc said:**
> you don't spend much time at the beach do you ?

Recreational activities are something you have to choose. :p

[http://www.youtube.com/watch?v=pjHDpcfMI7I&feature=related](http://www.youtube.com/watch?v=pjHDpcfMI7I&feature=related)

Not something I have done, but probably something I would like.

Later, Seeker

---

### Post by MadCookie on 2010-06-26
Let me **bold** that for you!

> **ronacc said:**
> while ubuntu is not a "rolling release " and I am not in anyway advocating that it become one, insisting that what it was released with is what you are "stuck" with , is almost criminally stupid . there are several things that for real **practical security reasons MUST be absolutely the latest available** , For instance your browser ( which ever one you choose ) , mail and contact prg , and these days even your PDF reader . While linux is nowhere near as big a problem as MS in this respect we are not bullet proof .

---

### Post by PGHammer on 2010-06-27
> **oOarthurOo said:**
> You're probably the first person I've ever seen describe Debian as a rolling release. Their motto is never release till its done. They're famous for stability. Sid is never released. Testing is not a release. If you want a rolling release based on Sid, use Sidux.

While Debian itself is not a rolling release, the current testing platform (Sid, which is being largely replaced by Squeeze) is largely following behind 'buntu (in fact, most of what is now in Squeeze was released with Lucid).  Ubuntu itself is Debian-based, but Canonical is further ahead than Debian's base (despite it being a Debian fork) because of the difference in philosophies.

I had recently taken a look at Lenny (mostly to compare it to Lucid) and, as surprising as it sounds, Lucid is more stable than Lenny (despite Lenny being in the oven for nearly two years; 22 months according to the press release).  Lenny has become the Debian equivalent of RedHat Enterprise Linux - great if you want a server-based distribution, but horrid as a desktop-focussed one.  I may yet take a look at Sidux, if only to compare it to Lucid and Maverick.  However, Debian's core team is in danger of becoming another RedHat.

There's an old saying - first you're ripe, then you rot.

Mandrake (now Mandriva) and even RedHat itself nearly found that out the hard way (the vast majority of RPM-based distributions are RedHat-based forks; however, most are far more suitable for general use than  RHEL is).

Canonical (and 'buntu) got to their very enviable position as the leading Debian-based Linux distribution by *not* being staid, not sitting on their laurels, and remaining true to their vision of a human-centric Linux distribution (quite bluntly, Lucid is a lot friendlier, both on installation or daily usage, than Lenny).  Debian has a reputation (pre-Ubuntu) of being almost newbie-hostile - to a large extent, Lenny reflects that; it's almost as unfriendly, even in the graphical installer, than *Gentoo*, which is a rolling release!  Does Canonical really want to move away from how it got to where it is?
(Further, that same philosophy is taking root outside Canonical; Sabayon Linux 5.3 is a Gentoo-based distribution that instead follows the Canonical/'buntu school of human-centricity, and does it darn well; if you didn't know better, you would think that Sabayon is based on Lucid, not Gentoo.)
Being a rolling release need not be a bad thing (as Sabayon proves); however, being too "obstinate" isn't necessarily a good thing, either (as proven by Debian Lenny).

It's not necessarily where you start, as opposed to how you get here.

---

### Post by ranch hand on 2010-06-27
10.04 being a LTS release was synced with Squeeze as the more stable branch of Debian development.  10.10 is back to syncing with the more unstable branch of Debian development.

I have never found Debian to less easy to use or set up than Ubuntu.  The Debian forum community is, to put it gently, not ready to clasp the noob to its breast but they are a pretty knowledgeable bunch and ready to help with well put questions.

I have had Lenny on here for some time and found it extremely stable but boring.  Squeeze is going to be my stable, secure install instead of 10.04 because plymouth just does not like my box and Debian was smart enough not to put that on there.  It boots 4 times as fast as 10.04 on this box and it shuts down.  Shut down of 10.04, if it does at all, is about 3 minutes.

10.10 is a lot better than 10.04 on here and that is a relief.  I like Debian but Ubuntu is more FUN.

---

### Post by Linuxforall on 2010-06-27
Having used Hardy LTS, all security patches when needed were released by Canonical and till now, I am yet to see a compromised PC running Hardy. Ubuntu has six months release schedule for its non LTS offering which is pretty close to a rolling release, also bear in mind, in rolling release, be prepared for breakage eventually, having run a rolling release server, I speak from experience.

---

### Post by Mr. Picklesworth on 2010-06-28
I expected this and it's good to see it (somewhat) clarified. Really nothing to be too bothered by in theory; Ubuntu has used this approach and it has worked well.

There is one situation I *am* concerned about, though. When a package is in Extras, I expect it would receive continuous updates as its original creator deems appropriate. (If it can't, Extras is doomed, by the way). So, &#8220;promoting&#8221; a package from Extras to Main or Universe would actually be *detrimental* to the developers of that software and to our users.

And that is where this whole thing will become a source of inconsistency. Personally, I think the best approach would be to gradually move all those apps to Extras (or something like it) &#8212; especially games &#8212; leaving the current three repositories to their dependencies and development packages.

---

### Post by MCVenom on 2010-06-28
To those saying they don't want Ubuntu to be a rolling release; bear in mind that the Extras repo does not make Ubuntu a rolling release, and even if it did; just disable it if it bothers you. Problem solved, no one is holding a gun to your head and forcing you to use the new repo. :P

---

### Post by MCVenom on 2010-06-28
> **Mr. Picklesworth said:**
> I expected this and it's good to see it (somewhat) clarified. Really nothing to be too bothered by in theory; Ubuntu has used this approach and it has worked well.

There is one situation I *am* concerned about, though. When a package is in Extras, I expect it would receive continuous updates as its original creator deems appropriate. (If it can't, Extras is doomed, by the way). So, &#8220;promoting&#8221; a package from Extras to Main or Universe would actually be *detrimental* to the developers of that software and to our users.

And that is where this whole thing will become a source of inconsistency. Personally, I think the best approach would be to gradually move all those apps to Extras (or something like it) &#8212; especially games &#8212; leaving the current three repositories to their dependencies and development packages.
It sounds like under that we could have a repo layout like this:


[LIST]
[*]main-desktop (or main-applications, main-programs, main-extras, etc.): A repo  for Canonical maintained, non-core applications that will recieve  upgrades as seen fit
[*]main-core (or simply main): A repo for Canonical maintained system  packages, libraries, dependencies, Gnome, et cetera that will only  recieve security and bug fix updates
[*]universe-desktop: Where the bulk of desktop apps will be  available, and could be upgraded by maintainers
[*]universe-core: A repo for libraries and dependencies and whatnot  that won't be upgraded
[*]restricted: There's not really much here that would need (or be  wise) to be upgraded to a newer version, I should think.
[*]multiverse: Same as before.
[/LIST]
Am I correct here?

---

### Post by zekopeko on 2010-06-28
> **BlackOtaku said:**
> It sounds like under that we could have a repo layout like this:


[LIST]
[*]main-desktop (or main-applications, main-programs, main-extras, etc.): A repo  for Canonical maintained, non-core applications that will recieve  upgrades as seen fit
[*]main-core (or simply main): A repo for Canonical maintained system  packages, libraries, dependencies, Gnome, et cetera that will only  recieve security and bug fix updates
[*]universe-desktop: Where the bulk of desktop apps will be  available, and could be upgraded by maintainers
[*]universe-core: A repo for libraries and dependencies and whatnot  that won't be upgraded
[*]restricted: There's not really much here that would need (or be  wise) to be upgraded to a newer version, I should think.
[*]multiverse: Same as before.
[/LIST]
Am I correct here?

This was exactly my line of thought. The development platform should be stable and only in bugfix mode while the apps should be updated (as far as the stable dev platform allows it).

The problem are the new dependencies that the app might introduce. How to deal with that? I don't see them as a problem in the non-main sections but in main it would potentially be extra burden for Canonical to maintain. OTOH does it really matter since new depens will be in the next Ubuntu release?

BTW This model is what Android is going to do to combat the fragmentation of their ecosystem. Stable core + updating apps.

---

### Post by 23meg on 2010-06-28
> **Mr. Picklesworth said:**
> There is one situation I *am* concerned about, though. When a package is in Extras, I expect it would receive continuous updates as its original creator deems appropriate. (If it can't, Extras is doomed, by the way). So, &#8220;promoting&#8221; a package from Extras to Main or Universe would actually be *detrimental* to the developers of that software and to our users.

And that is where this whole thing will become a source of inconsistency. Personally, I think the best approach would be to gradually move all those apps to Extras (or something like it) &#8212; especially games &#8212; leaving the current three repositories to their dependencies and development packages.

> **BlackOtaku said:**
> It sounds like under that we could have a repo layout like this:

<snip>

The whole notion of archive components and the related restrictions are being undone by the [archive reorganisation]("https://wiki.ubuntu.com/ArchiveReorganisation/"), and with a bit of additional governance, this effort can tie in well with that. For example, people who get new packages accepted into the new PPA / pocket and maintain it without major packaging bugs for a reasonable period can be given per-package upload privileges for their respective packages and maintain them.

---

### Post by 23meg on 2010-06-28
> **zekopeko said:**
> This was exactly my line of thought. The development platform should be stable and only in bugfix mode while the apps should be updated (as far as the stable dev platform allows it).

The problem are the new dependencies that the app might introduce. How to deal with that? I don't see them as a problem in the non-main sections but in main it would potentially be extra burden for Canonical to maintain. OTOH does it really matter since new depens will be in the next Ubuntu release?

BTW This model is what Android is going to do to combat the fragmentation of their ecosystem. Stable core + updating apps.

I'm not sure as to what detail you read the previous posts and the specs, but the specs only cover leaf-node applications that require no new dependencies, and no other packages depend on. If something requires new dependencies, and those dependencies can go into backports, and there are people who are willing to do the backporting, it *may* be a good idea to allow that (note that the process spec isn't final yet), but this effort is essentially not about new upstream versions of existing applications in the archive; it's all about getting in new applications that aren't in the archive, and build-depend and depend on existing packages in the archive ("But which parts of the archive?" still being an open question).

---

### Post by Starks on 2010-06-28
Ubuntu should have a stable archive and an optional rolling archive.

People that use testing releases are having a pseudo-rolling experience pretty much up until RC freeze and even then, there's usually only a 2 week window between release and the next toolchain release.

For those of us that like to live on the edge and jump from development release to development release, true rolling would be nice. Don't make us run a stable Ubuntu for that brief 2 week period or face freezes.

---

### Post by Mr. Picklesworth on 2010-06-28
> **23meg said:**
> The whole notion of archive components and the related restrictions are being undone by the [archive reorganisation]("https://wiki.ubuntu.com/ArchiveReorganisation/"), and with a bit of additional governance, this effort can tie in well with that. For example, people who get new packages accepted into the new PPA / pocket and maintain it without major packaging bugs for a reasonable period can be given per-package upload privileges for their respective packages and maintain them.

Excellent! I somehow had no idea that was happening. Thanks, 23meg. I'm watching that excitedly now :)



> **zekopeko said:**
> The problem are the new dependencies that the app might introduce. How to deal with that? I don't see them as a problem in the non-main sections but in main it would potentially be extra burden for Canonical to maintain. OTOH does it really matter since new depens will be in the next Ubuntu release?
In the general case, I don't think that should be a concern. That's why major releases should exist: to upgrade the core that apps depend on. If something is depending on shiny new stuff, it depends on the shiny new Ubuntu release. An extra application should not depend on Ubuntu being completely up to date (as in minor updates over the Internet) in order to be installed.
Besides, the situation with having too many APIs for the same job would never get better if that kind of thing was encouraged ;)

---

### Post by zekopeko on 2010-06-28
> **23meg said:**
> I'm not sure as to what detail you read the previous posts and the specs, but the specs only cover leaf-node applications that require no new dependencies, and no other packages depend on. If something requires new dependencies, and those dependencies can go into backports, and there are people who are willing to do the backporting, it *may* be a good idea to allow that (note that the process spec isn't final yet), but this effort is essentially not about new upstream versions of existing applications in the archive; it's all about getting in new applications that aren't in the archive, and build-depend and depend on existing packages in the archive ("But which parts of the archive?" still being an open question).

I wasn't referring to the the spec for new apps in maverick but the broader possibility.

EDIT: If a new dependency is required for the application to work fully I see no problem with that situation. Only new apps will depend on it and the dependency itself would developed on the stable core/toolchain in that specific Ubuntu version.

The problem part as you highlighted is the definition of "stable core" aka "which parts of the archive".

---

### Post by zekopeko on 2010-06-28
> **Mr. Picklesworth said:**
> In the general case, I don't think that should be a concern. That's why major releases should exist: to upgrade the core that apps depend on. If something is depending on shiny new stuff, it depends on the shiny new Ubuntu release. An extra application should not depend on Ubuntu being completely up to date (as in minor updates over the Internet) in order to be installed.
Besides, the situation with having too many APIs for the same job would never get better if that kind of thing was encouraged ;)

I was thinking more along the line of not having stale applications in Ubuntu if possible. Lucid is going to be supported until 13.04. 3 years in the tech industry is a long time.

This solution would alleviate the problem of "no new features for stable versions of apps" in Ubuntu. The devs would have an option to build against a particular Ubuntu version and bring new features to end users.

---

