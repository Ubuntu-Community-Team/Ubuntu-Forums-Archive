---
title: "Help choosing a release"
date: 2011-05-07
forum: Mythbuntu
---

### Post by aormond on 2011-05-07
I'm trying to decide which Mythbuntu release I should use on a new FE/BE machine, 10.04 LTS or 11.04. At the moment,  the things that concern me are:

**Mythtv upgradibility** - I want to make sure that I can keep upgrading Mythtv as much as possible before I need to upgrade to a new ubuntu version.

**Hardware compatibility** - My main concern is the GT430 video card I'm using. Would using the newer build improve support for the card? Or does it not matter since 10.04 is a LTS?

**Overall stability** - Obviously.

I'm not at all interested in the latest and greatest Ubuntu features; This is just a MythTV box.

I'd appreciate any thoughts/experiences! :) Are there any other factors that I should be considering?

---

### Post by LowSky on 2011-05-07
Eiteher release is fine. You can add MythTV .24 to 10.04 using the mythbuntu PPA off the mythbuntu upgrade page. The Nvidia card driver can be updated using a similar PPA.

Also there is a preconceived notion that 10.04 is better supported. It really is not. The community is usually supporting the latest version. Stability is also a relative term. For many 10.04 is just as stable as 11.04. Then there is the whole Unity subject with the newest release. My own preference is to use Ubuntu classic mode so that things just run and I don't need to worry about the menu.

---

### Post by tgm4883 on 2011-05-07
> **LowSky said:**
> Eiteher release is fine. You can add MythTV .24 to 10.04 using the mythbuntu PPA off the mythbuntu upgrade page. The Nvidia card driver can be updated using a similar PPA.

Also there is a preconceived notion that 10.04 is better supported. It really is not. The community is usually supporting the latest version. Stability is also a relative term. For many 10.04 is just as stable as 11.04. Then there is the whole Unity subject with the newest release. My own preference is to use Ubuntu classic mode so that things just run and I don't need to worry about the menu.

Mythbuntu doesn't has Unity, so you don't need to worry about that.

@OP - The Mythbuntu team will build new MythTV releases for LTS releases (eg. 10.04) until the next LTS release (eg. 12.04), as long as there isn't a required dependency on something that doesn't exist in 10.04 (eg. Like when 0.22 required a newer version of Qt than 8.04 had). So you should see 0.25, and possible 0.26 (providing it gets released in time) on 10.04

---

### Post by aormond on 2011-05-07
> **tgm4883 said:**
> Mythbuntu doesn't has Unity, so you don't need to worry about that.

@OP - The Mythbuntu team will build new MythTV releases for LTS releases (eg. 10.04) until the next LTS release (eg. 12.04), as long as there isn't a required dependency on something that doesn't exist in 10.04 (eg. Like when 0.22 required a newer version of Qt than 8.04 had). So you should see 0.25, and possible 0.26 (providing it gets released in time) on 10.04
Thanks! So my understanding is that 10.04 could possibly get me up to 0.26, whereas 11.04 will definitely get me to 0.25 but no further. That makes me think that 10.04 may be the better choice for me.

Thanks for the info!

---

### Post by nickrout on 2011-05-07
I would certainly go for the 10.04 LTS release.

---

### Post by scratman on 2011-05-07
Personally I'd go for 10.10, but then lock system updates so that you only upgrade the distro for LTS varieties.  10.10 has more features than 10.04, is at least as stable if not more so, and will be supported until April 2012, which conveniently is when the next LTS version comes out.  It also means that you don't ever have to deal with the unstable, V-Tech inspired hunk of excretia that is Unity.

---

### Post by tgm4883 on 2011-05-07
> **scratman said:**
> Personally I'd go for 10.10, but then lock system updates so that you only upgrade the distro for LTS varieties.  10.10 has more features than 10.04, is at least as stable if not more so, and will be supported until April 2012, which conveniently is when the next LTS version comes out.  It also means that you don't ever have to deal with the unstable, V-Tech inspired hunk of excretia that is Unity.

How does 10.10 have more features? (hint: please look at the forum you are in)

Both have access to 0.24, and as explained before 10.04 will get newer mythtv versions

---

### Post by scratman on 2011-05-08
Umm, well, there was that fancy new backup/restore tool, MythExport was improved, the themes were fixed, plus all the boring stuff, like the updated Linux Kernel providing improved hardware support among a few other things, but hey, it was only a piece of advice imparting accurate information, feel free to ignore me!

---

### Post by tgm4883 on 2011-05-08
> **scratman said:**
> Umm, well, there was that fancy new backup/restore tool, MythExport was improved, the themes were fixed, plus all the boring stuff, like the updated Linux Kernel providing improved hardware support among a few other things, but hey, it was only a piece of advice imparting accurate information, feel free to ignore me!

Sorry, don't get me wrong. Your feedback is great, a lot of the features you mentioned are stuff i've worked on and I'm not sure how much people are actually using. It's good to hear what users are seeing and like as new features. Thanks for the info.

---

### Post by scratman on 2011-05-09
@tgm4883 No worries, I just thought I'd recommend what is IMHO the better of two Mythbuntu distributions.  I'd go for 10.10 over 10.04 for the reasons previously described.

---

