---
title: "why is my Mythbuntu machine still on 10.04? Is that a problem?"
date: 2011-12-03
forum: Mythbuntu
---

### Post by tedder on 2011-12-03
I'm running updates on my mythbuntu machine, I see there are a few I need to apply as a dist-upgrade, but nothing that explains why I'm still on 10.04.3 (according to /etc/issue). Is the mythbuntu distro still on 10.04 because it is a LTS? Or am I missing some apt sources for mythbuntu?

I note I don't have anything that matches "mythbuntu" in my apt sources.list.

---

### Post by BC59 on 2011-12-03
If you don't make distribution upgrade manually, you are going to stay to the same version.

---

### Post by nickrout on 2011-12-03
> **tedder said:**
> I'm running updates on my mythbuntu machine, I see there are a few I need to apply as a dist-upgrade, but nothing that explains why I'm still on 10.04.3 (according to /etc/issue). Is the mythbuntu distro still on 10.04 because it is a LTS? Or am I missing some apt sources for mythbuntu?

I note I don't have anything that matches "mythbuntu" in my apt sources.list.

Don't go to a later version of *buntu unless there is a really pressing need to, ie a later version provides a kernel that fixes a driver issue.

If you want the latest mythtv (0.24-fixes) use mythbuntu repo.

The reason you have nothing called "mythbuntu" in your sources list is because mythbuntu is just ubuntu with a different desktop plus the mythtv packages, and some support packages like mythbutu-control-centre.

---

### Post by superm1 on 2011-12-05
Everything posted above is correct.  Some additional information:

* By default LTS releases will only offer you to switch to another LTS release.
* Since you are on the LTS track, you will continue to be transitioned to the rest of the 10.04.x releases as they happen
* Update manager will offer you to jump to 12.04.1, the next major LTS release.
* If you want to upgrade to a non-LTS release, open up update-manager and go to settings or software-sources-gtk

Mythbuntu is switching to only doing LTS CD images anyhow starting with 12.04, so you're just a little bit ahead of the curve.  This means that there will be no 12.10, 13.04, or 13.10 releases.  The PPA will still be active for these intermediate releases though.  After 12.04 the next release with a CD image will be 14.04.

---

### Post by newlinux on 2011-12-05
I do LTS to LTS mainly, and it works fine for me. I have one machine I just built (time to update my hardware in the functional hardware thread) that I put 11.10 on, but all my machines are running the myth .24 and I plan to upgrade them all to 12.04 a month or so after it's out. Nothing wrong with LTS to LTS.

---

### Post by agamotto on 2011-12-06
No, nothing wrong at all, as keeping to LTS versions will save you a lot of bother!

---

### Post by bluexrider on 2011-12-06
hey, when you do decide....do a fresh install.....trust me. a lot less issues

---

### Post by tedder on 2011-12-06
> **agamotto said:**
> No, nothing wrong at all, as keeping to LTS versions will save you a lot of bother!

I'm more than happy to stay on LTS, generally ubuntu backporting has been poor. I want to keep up with mythtv releases.

---

### Post by newlinux on 2011-12-08
> **bluexrider said:**
> hey, when you do decide....do a fresh install.....trust me. a lot less issues

I've done multiple upgrades of multiple machines from LTS to LTS and intermediate versions. I've only had a couple of cases where it was a problem. I'd say just make proper backups and its okay to try to upgrade instead of a fresh install, but be prepared for a fresh install.

> **tedder said:**
> I'm more than happy to stay on LTS, generally ubuntu backporting has been poor. I want to keep up with mythtv releases.

The mythbuntu repos will keep mythtv up to date on LTS releases.

---

### Post by nickrout on 2011-12-08
> **newlinux said:**
> I've done multiple upgrades of multiple machines from LTS to LTS and intermediate versions.  I've done one and it was a disaster, but I had the database backed up so all was well, did a fresh install> I've only had a couple of cases where it was a problem. I'd say just make proper backups and its okay to try to upgrade instead of a fresh install, but be prepared for a fresh install.



The mythbuntu repos will keep mythtv up to date on LTS releases.

Yes, they're good like that :)

---

