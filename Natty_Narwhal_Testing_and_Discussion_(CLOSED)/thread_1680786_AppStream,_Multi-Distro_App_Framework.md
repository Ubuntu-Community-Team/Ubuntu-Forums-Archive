---
title: "AppStream, Multi-Distro App Framework"
date: 2011-02-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ikt on 2011-02-03
> Recently in Germany there was a cross-distribution meeting among the major vendors (Red Hat, **Canonical**, Novell, Debian, Mandriva, etc) to discuss a common application installer for Linux and one unified application store / market-place. The goal would be to have a common user-interface for application installation, how/what meta-data to use, determine a defined protocol for non-static meta-data, and decide what meta-data to share across distributions. Fortunately, this was a very successful meeting. 

[http://www.phoronix.com/scan.php?page=news_item&px=OTA1MA](http://www.phoronix.com/scan.php?page=news_item&px=OTA1MA)

Any news for us? I didn't see anything mentioned any where.

---

### Post by cariboo on 2011-02-03
There have been a couple of blog post on the Planet about the meeting, but that's all I've seen so far.It would mean a load of new work for the developers, so I wouldn't expect to see anything soon.

---

### Post by Starks on 2011-02-03
Is PackageKit USC planned for Natty or Natty+1?

---

### Post by ikt on 2011-02-03
> **Starks said:**
> Is PackageKit USC planned for Natty or Natty+1?

I think that's the thing I'm wondering as well, is it something we should look forward to in 11.10 or 12.04?

---

### Post by seeker5528 on 2011-02-03
> **Starks said:**
> Is PackageKit USC planned for Natty or Natty+1?

My question would be.... 

Are they planning on turning PackageKit into something it currently isn't?

I would certainly view having a common simplified GUI app warehouse/installer that is common across multiple distributions to be a good thing, but.....

How does this help ISVs package once for multiple distributions? 

If it doesn't help ISVs package once for multiple distributions, calling it a 'Multi-Distro App Framework' seems a little misrepresentative.

Disclaimer, I have not watched the video *yet* at the time of this writing. Maybe this is something that is covered there?

Later, Seeker

---

### Post by kklimonda on 2011-02-03
@seeker5528: AFAIR it hasn't been called "Multi-Distro App Framework" by the attendees of this meeting and the focus of the discussion was on how to share application meta data, and not how to create some multi-distro packaging format. If I were to guess, I'd say that Phoronix is doing everything to bring more ad-viewers/readers to the page, as always. Flashy titles do sell.

---

### Post by Mr. Picklesworth on 2011-02-03
I like this :)

I was thinking it would be nice if we accept that Debian / RPM package systems are great for core system stuff (things applications depend on and distros have good reason to spend time maintaining for themselves) but not very great at application packages. Having two parallel systems, where one remains distro-specific but only expecting to be used within its distro, could be a nice move.

I'm quite curious about what they've come up with.

---

### Post by Merk42 on 2011-02-03
Standards? In *my* Linux?
[SIZE="1"]It's more likely than you think[/SIZE]

---

### Post by Starks on 2011-02-04
AppStream is needed because things like apt-url simply aren't sufficient for bypassing official repository versions.

Furthermore, the "Year of the Linux desktop" can't happen without a standard packaging system.

---

### Post by ronacc on 2011-02-04
things like this have been promised many times , I'll believe it when It actually arrives and we can use it.

---

### Post by seeker5528 on 2011-02-04
> **Starks said:**
> AppStream is needed because things like apt-url simply aren't sufficient for bypassing official repository versions.

Apt-url isn't designed for that, it is designed to allow a url to be supplied on a web page that will initiate the installation of something that is in the official repositories or whatever repositories you have in /etc/apt/sources.list.d/XXX.list files.

Everything I have heard so far, and after watching the video it doesn't make it seem any different, the actual installations will be from your distributions official repositories. 

After watching the video, it seems less about providing a common "warehouse" and more about creating a shared location on the net that distributions can set up their version of the installer to access for things like application icons to use in the installer, ratings, reviews, screen shots, etc...

Later, Seeker

---

