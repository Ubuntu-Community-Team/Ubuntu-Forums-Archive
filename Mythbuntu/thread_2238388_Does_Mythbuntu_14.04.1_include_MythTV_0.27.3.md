---
title: "Does Mythbuntu 14.04.1 include MythTV 0.27.3?"
date: 2014-08-07
forum: Mythbuntu
---

### Post by David_Bright on 2014-08-07
Hi,

Please forgive me if this question has an answer elsewhere that I missed.

The _Mythbuntu 14.04.1 Released_ post mentions MythTV 0.27 and includes a link to the 0.27 release notes. When I look at the MythTV website, I see that the latest version is 0.27.3. Does Mythbuntu 14.04.1 include MythTV 0.27.3?

Thanks,
David.

---

### Post by Lester_Burnham on 2014-08-09
Hi,

If it doesn't, just open mythbuntu control centre (MCC), go to repositories and enable mythtv updates for 0.27
Exit, open software manager, check for new updates and install.
Otherwise
sudo apt-get update
sudo apt-get upgrade

Lester

---

### Post by neutron68 on 2014-08-18
I just ran a 12.04 to 14.04 update.

The myth version is:  fixes/0.27(v0.27.3-150-g082d5c1)

---

### Post by tgm4883 on 2014-08-18
It's not, but it's available from the mythbuntu provided repo. It's recommended that you run from those anyway.

---

### Post by neutron68 on 2014-08-19
> **tgm4883 said:**
> It's not, but it's available from the mythbuntu provided repo. It's recommended that you run from those anyway.
??????

When my 14.04.1 upgrade finished the myth version was: fixes/0.27(v0.27.3-150-g082d5c1)

---

### Post by tgm4883 on 2014-08-19
> **neutron68 said:**
> ??????

When my 14.04.1 upgrade finished the myth version was: fixes/0.27(v0.27.3-150-g082d5c1)

Then you got it from the mythbuntu provided repos. Here are the packages in the ubuntu repos.

[http://packages.ubuntu.com/search?keywords=mythtv&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=mythtv&searchon=names&suite=all&section=all)

---

