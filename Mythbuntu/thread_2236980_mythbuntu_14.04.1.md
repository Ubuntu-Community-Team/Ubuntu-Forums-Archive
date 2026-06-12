---
title: "mythbuntu 14.04.1?"
date: 2014-07-30
forum: Mythbuntu
---

### Post by faginbagin on 2014-07-30
So, I noticed ubuntu has announced 14.04.1 and I thought maybe mythbuntu might have done the same. Not so, according to mythbuntu.org. However, when I check cdimage.ubuntu.com, the ISOs are there, dated Jul 22. Are these "safe" to use? Maybe the website just hasn't been updated?

---

### Post by ppattrsn on 2014-08-04
Since the release of mythbuntu 12.04.1 was announced in mythbuntu.org  latest news and 14.04.1 has not yet been announced there, I assume it is not yet ready.  Is this correct?  Any idea when it is expected?

---

### Post by tgm4883 on 2014-08-06
I didn't do a post on it but it's been released. Since there are at least two people that didn't know, I just did a post on it as well.

---

### Post by faginbagin on 2014-08-07
Thanks!

---

### Post by finn on 2014-08-10
Does updating from 12.04 LTS work well enough to recommend for people that must ensure kids/wife don't get deprived during a rebuild?

---

### Post by faginbagin on 2014-08-10
IMHO, I wouldn't upgrade from 12.04 unless there's a hardware problem that needs the newer kernel. I believe 12.04 will be supported until 2012+5 years, or April 2017. I'm keeping my older front ends at 12.04. I only wanted 14.04 for my newer master backend which has an i3-3220 CPU and a MoBo with a B75 chipset.

---

### Post by melben on 2014-08-11
> **faginbagin said:**
> IMHO, I wouldn't upgrade from 12.04 unless there's a hardware problem that needs the newer kernel. I believe 12.04 will be supported until 2012+5 years, or April 2017. I'm keeping my older front ends at 12.04. I only wanted 14.04 for my newer master backend which has an i3-3220 CPU and a MoBo with a B75 chipset.

I'm curious about this. I know the Ubuntu LTS release is supported for 5 years, but the Mythbuntu site is not so clear. I assume Ubuntu updates will continue for 5 years, but it looks like the MythTV packages come from the Mythbuntu team so will they continue for the 5 years too or stop shortly after each LTS release?
Ben

---

### Post by tgm4883 on 2014-08-12
> **melben said:**
> I'm curious about this. I know the Ubuntu LTS release is supported for 5 years, but the Mythbuntu site is not so clear. I assume Ubuntu updates will continue for 5 years, but it looks like the MythTV packages come from the Mythbuntu team so will they continue for the 5 years too or stop shortly after each LTS release?
Ben

You will continue to get the underlying Ubuntu updates for 5 years. As for the MythTV updates repo, it's more difficult to explain in text in a nice concise way. The easy short answer is to check the graphic on [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos) as it is automatically generated from our build scripts, although that just gives you the current days answer and doesn't give any indication for the future unless you know the long answer.

The longer answer is the Mythbuntu team has committed to doing builds for 3 versions of MythTV; dev, current, and last current (As of this writing, 0.28, 0.27, and 0.26). That is the easy explanation, where it gets difficult is explaining which releases get what MythTV builds. Non-LTS releases will get 2 versions of MythTV, no more than that. For LTS releases (which are the ones we recommend), we support the last two LTS releases (as of this writing, that is 14.04 and 12.04).  Starting with the MythTV version that shipped with the LTS release, we will build every MythTV release until the next LTS's first point release (eg. we commit to building MythTV for 12.04 until 14.04.1). Once that point release hits (eg. 14.04.1), we've fulfilled the commitment, but that doesn't mean that we will stop building MythTV for the previous distro release. What that means is that while we will continue to build for the previous distro release, if the builds break we will stop building for that release (eg. when 0.26 builds had dependency issues on 10.04, we stopped building for 10.04). 

After writing all of that, I made the following list that might make more sense (it's at least shorter)

[LIST]
[*]For non-LTS releases, we will build 2 MythTV versions. The shipped version and the shipped+1 version
[*]For LTS releases, we commit to building the shipped MythTV version, and all newer MythTV versions until the next LTS point release.
[*]We will continue to build MythTV versions for the old LTS release after the current LTS point release, but if the builds fail (eg. build dependency issues) we won't put much effort into fixing them.
[*]We only build for at most the last two LTS releases (Note that while an LTS is in development, it is not considered an LTS release.) and the supported non-LTS releases. 
[*]Since underlying infrastructure is from Ubuntu, LTS releases will continue to get the underlying improvements for the whole LTS duration (even after the Mythbuntu team stops supporting it)
[/LIST]

Definitions
Shipped version - The version of MythTV that a particular Ubuntu release shipped with. (eg. 14.04 shipped with 0.27)
Shipped+1 version - The version immediately next in line after the shipped version
LTS release - The current Long Term Support release for the distro. These are the same LTS releases as Ubuntu although the Mythbuntu team's LTS support is shorter.
non-LTS release - Any Ubuntu release that isn't an LTS release. While Mythbuntu doesn't provide non-LTS ISOs, it is possible to install MythTV from the repos on a non-LTS release.
LTS+1 - The next LTS release, either in development or development not yet started yet
LTS-1 - The former current LTS release.

---

### Post by melben on 2014-08-14
Very well explained, thank you. 

It may be worth adding a question to [http://www.mythbuntu.org/lts](http://www.mythbuntu.org/lts), something like:
"LTS releases are every 2 years, but Ubuntu supports them for 5 years. How long is a Mythbuntu LTS release supported for?"
Then a brief answer pointing to the repos page you mentioned.

Thanks
Ben

---

### Post by melben on 2014-08-14
deleted duplicate

---

