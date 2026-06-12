---
title: "Any word on the date 23.1 will be in repository?"
date: 2010-08-04
forum: Mythbuntu
---

### Post by bcg30506 on 2010-08-04
I notice on MythTV's main forum that 23.1 was released on 7/25.  Sounds like it has some nice fixes.  Anyone have a timeframe when we might see it in the mythbuntu repositories for an apt upgrade?

---

### Post by LowSky on 2010-08-04
activate mythbuntu's autobuilds 

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by bcg30506 on 2010-08-04
The only issue I have with this is stability and performance.  I do not want to be bleeding edge and running nightly beta builds on our living room system.  0.23-1 is a new official release of MythTV so it should be in the normal repository as a normal update manager package upgrade.  From reading about auto builds it seems they are built nightly and are more for those testing new features or fixes before a release.

---

### Post by tgm4883 on 2010-08-04
0.23.1 will be in Ubuntu 10.10. It will not be backported to 10.04 by the Mythbuntu team. You can activate auto-builds to get packages built from the upstream fixes branch. 

ATM, you can enable auto-builds for 0.23.0, but not 0.23.1. This will change once I get a chance to update the mythbuntu-repos package, but I will be unable to do that until I either A) finish this project i'm working on, or B) after feature freeze on Aug 12th

---

### Post by bcg30506 on 2010-08-04
Thanks for the update.  I'll wait for the repository.  :)

---

### Post by melevittfl on 2010-08-25
> **tgm4883 said:**
> 0.23.1 will be in Ubuntu 10.10. It will not be backported to 10.04 by the Mythbuntu team. You can activate auto-builds to get packages built from the upstream fixes branch. 

ATM, you can enable auto-builds for 0.23.0, but not 0.23.1. This will change once I get a chance to update the mythbuntu-repos package, but I will be unable to do that until I either A) finish this project i'm working on, or B) after feature freeze on Aug 12th

Hi,

I'm a bit confused by this message and I was hoping someone could clarify for more. 

From what I can tell, 23.1 is the new stable release of Mythtv. So first, you're saying it won't be available in 10.04, only in 10.10? But then you say you can enable auto-builds to get packages (for 23.1)?

Sorry, I'm sure I'm just being thick. I noticed there is a 23.1 choice in the auto-build selection, but I'm not sure it's safe to select it. 

I'm on 10.04 with 23.0 and I'm getting packages from the fixes branch. Will selecting 23.1 upgrade my 10.04 system to Mythtv 23.1? Is that safe (stable?)

---

### Post by tgm4883 on 2010-08-25
> **melevittfl said:**
> Hi,

I'm a bit confused by this message and I was hoping someone could clarify for more. 

From what I can tell, 23.1 is the new stable release of Mythtv. So first, you're saying it won't be available in 10.04, only in 10.10? But then you say you can enable auto-builds to get packages (for 23.1)?

Sorry, I'm sure I'm just being thick. I noticed there is a 23.1 choice in the auto-build selection, but I'm not sure it's safe to select it. 

I'm on 10.04 with 23.0 and I'm getting packages from the fixes branch. Will selecting 23.1 upgrade my 10.04 system to Mythtv 23.1? Is that safe (stable?)

Sorry for the confusion, let me try to explain a little better.

The OP (at least my understanding of it), was asking when 0.23.1 were going to be in the official Ubuntu repositories. 0.23.1 will not be in the official Ubuntu repositories for Lucid, but will be in for Maverick. The reason for this is the process for getting updates into frozen archives requires documenting what every fix does and is overall a lengthy process. A process that would need to be done frequently. This is something the Mythbuntu team doesn't have the manpower to do.

The Mythbuntu team does provide updates through a process called auto-builds. This is to get around us not having the manpower to get updates into the official Ubuntu repos. These updates are built from the same source and using the same process as the packages in the official Ubuntu archives, they are just more up to date. The Mythbuntu team usually recommends enabling these updates.

Note that you can upgrade to 0.23.1 on Lucid. Mythbuntu-repos will not (shouldn't) give you the option to upgrade to a release that isn't something we are willing to support (although the development release is iffy). If you do upgrade, note that 0.23.1 isn't compatible with 0.23.0, so you will need to upgrade all frontends and backends in your environment.

0.23.1 builds are pulled from the fixes branch upstream. There will be no more 0.23.0 builds (because there are no more 0.23.0 changes)

---

### Post by tgm4883 on 2010-08-26
So in summary,

Official Ubuntu repos for Lucid don't offer 0.23.1, but Mythbuntu repos do. The Mythbuntu repos aren't on by default, but you can enable them by updating to the latest version of the mythbuntu-repos package (8.2) from [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by tgm4883 on 2010-08-26
If there are any more questions let me know. I wrote this package so I know what it does, and I probably don't explain everything clearly since it makes sense in my brain.

---

### Post by agamotto on 2010-08-26
So, out of curiosity, why are the LTS users being left out of this update/patch?

---

### Post by tgm4883 on 2010-08-27
> **agamotto said:**
> So, out of curiosity, why are the LTS users being left out of this update/patch?

You aren't being left out of this update. I'll cite a few reasons.

1) You can update to 0.23.1 via the Mythbuntu team provided repos which you can enable with the mythbuntu-repos package.
2) To my knowledge, there has never been a Mythbuntu LTS release. To quote [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
> The LTS designation applies only to specific subsets of the Ubuntu archive. The LTS may not apply to all editions and remixes of Ubuntu. For example, for 8.04 LTS, Kubuntu chose to move to KDE 4.0 and didn't issue an LTS release. In 10.04, the Netbook Edition will not be an LTS. The project will decide which editions will be LTS early in the LTS development cycle.


Now, to reformat you question about why 10.04 isn't getting 0.23.1 in the Official Ubuntu repos.

From post #7 (3 posts above yours)
> This is something the Mythbuntu team doesn't have the manpower to do.

:EDIT:

I should note that you will still receive any updates provided by Canonical.

---

### Post by melevittfl on 2010-08-27
> **tgm4883 said:**
> Sorry for the confusion, let me try to explain a little better.


Hi,

Thanks very much for your further explanation. That has cleared up all of my confusion. And thanks for the effort in doing all of this!

Cheers,
Mark

---

### Post by nickrout on 2010-08-27
> **agamotto said:**
> So, out of curiosity, why are the LTS users being left out of this update/patch?

what are you on about? auto-builds works in LTS!

---

### Post by tgm4883 on 2010-08-27
US, UK, and FR repos should now work again for 0.23.1 (and shouldn't break for the same reason in the future)

---

### Post by Neon Dusk on 2010-08-27
> **nickrout said:**
> what are you on about? auto-builds works in LTS!

I think that he means that the standard Ubuntu 10.04 repos only have a pre-release version of MythTV 0.23. Of course all Ubuntu users can use the MythBuntu repos to update to the latest MythTv 0.23.1-fixes or trunk if they desire.

---

