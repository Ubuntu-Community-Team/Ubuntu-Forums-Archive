---
title: "Auto-builds for Intrepid"
date: 2008-12-18
forum: Mythbuntu
---

### Post by fatmonk on 2008-12-18
The [Auto-Builds]("http://www.mythbuntu.org/auto-builds") page on the MythBuntu site still has instructions for Hardy...

Any news on the auto-builds for Intrepid?

I know the US repo was kind of working but the UK was still bad a couple of weeks ago...

What's the latest?

-FM

---

### Post by tgm4883 on 2008-12-18
> **fatmonk said:**
> The [Auto-Builds]("http://www.mythbuntu.org/auto-builds") page on the MythBuntu site still has instructions for Hardy...

Any news on the auto-builds for Intrepid?

I know the US repo was kind of working but the UK was still bad a couple of weeks ago...

What's the latest?

-FM

AFAIK, the uk repo has updates but there are issues with the US repo.  You can change the hardy to intrepid and that should work fine.

Trunk builds haven't started yet, but should soon.

---

### Post by lionsnob on 2008-12-21
Just wanted to let someone know that on the US trunk build repo on the Mythbuntu web site there is a typo.  The web site says this:

```
echo "deb http://weeklybuilds.mythbuntu.org/mythbuntu-trunk/ubuntu **inttrepid** main" | sudo tee /etc/apt/sources.list.d/mythbuntu-intrepid.list
```

Also, I still think the weekly fixes builds are broken (as stated above), as the US ones are still broken (not finding any new updates) and the UK one only finds updates for some modules.

I see  that trunk builds will be coming soon - will these be 0.22 trunk builds or 0.21?

Thanks!

---

### Post by blackoper on 2008-12-24
bumpity any idea when the trunk builds will start again. I've run trunk before but have no intention of compiling the whole thing by hand if I don't have to.

---

### Post by grytpype on 2009-01-03
Bump.

Anyone know when weekly builds for Intrepid will be available in the repos?

:confused::confused::confused:

---

### Post by tgm4883 on 2009-01-06
Weekly MythTV builds (for -fixes) are now fixed for both the US and UK mirrors.  If these are already in your sources.list then you have nothing else to add and it should work straight away.  The GPG key error for the UK mirror has also been fixed.  -fixes will contain MythTV updates for Hardy and Intrepid, and in the future Jaunty.

Trunk/0.22 - If you wish to run trunk please note that the trunk repo address has been changed to reflect 0.22 now.  If you have been previously running trunk or have added the repo before today, you have the wrong repo and will not get trunk updates.  Please go to [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) and add the new repo if desired.  Trunk repo will contain MythTV 0.22 updates for Hardy, Intrepid, and Jaunty.

---

