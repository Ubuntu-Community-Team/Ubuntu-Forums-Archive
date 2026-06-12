---
title: "MythTV 0.26 PPA for lucid 3 months old"
date: 2012-08-15
forum: Mythbuntu
---

### Post by evuraan on 2012-08-15
MythTV 0.26 PPA for lucid is from May 2012, and is 3 months older than the .debs for oneiric et al

mythtv-backend_0.26.0~master.[COLOR="Red"]20120508[/COLOR].0d8e93c-0ubuntu0mythbuntu1_i386.deb

vs. 

mythtv-backend_0.26.0~master.[COLOR="Red"]20120815[/COLOR].b1f38e4-0ubuntu0mythbuntu3_i386.deb


I am on 0.26.0~master.20120508.0d8e93c-0ubuntu0mythbuntu1, and i am having issues with mythbackend, and was wondering whether there will be updates to 0.26 PPA for ubuntu lucid. 

thanks in advance!

---

### Post by nickrout on 2012-08-15
> **evuraan said:**
> MythTV 0.26 PPA for lucid is from May 2012, and is 3 months older than the .debs for oneiric et al

mythtv-backend_0.26.0~master.[COLOR="Red"]20120508[/COLOR].0d8e93c-0ubuntu0mythbuntu1_i386.deb

vs. 

mythtv-backend_0.26.0~master.[COLOR="Red"]20120815[/COLOR].b1f38e4-0ubuntu0mythbuntu3_i386.deb


I am on 0.26.0~master.20120508.0d8e93c-0ubuntu0mythbuntu1, and i am having issues with mythbackend, and was wondering whether there will be updates to 0.26 PPA for ubuntu lucid. 

thanks in advance!

Well of course you have to expect breakage when using master, it is expected to break once in a while.

As to the age of the packages, i am not sure that master is still supported for lucid. The website says > Mythbuntu will provide Bundled Version & Bundled Version+1 of MythTV for regular releases and every MythTV version released during the lifetime (2 years) of an LTS release. 

As myth 0.26 has not been released when lucid's 2 year support window finished in April 2012 (and still has not been released) I am guessing you won't get any more master for lucid.

---

### Post by evuraan on 2012-08-15
> **nickrout said:**
> 
As myth 0.26 has not been released when lucid's 2 year support window finished in April 2012 (and still has not been released) I am guessing you won't get any more master for lucid.


lucid is LTS, and is supported until 2015, [https://wiki.ubuntu.com/LTS/](https://wiki.ubuntu.com/LTS/)

---

### Post by tgm4883 on 2012-08-15
> **evuraan said:**
> lucid is LTS, and is supported until 2015, [https://wiki.ubuntu.com/LTS/](https://wiki.ubuntu.com/LTS/)

While what you are saying it technically true, it is not true that you will receive new versions of all software for every LTS (usually just security and major bug fixes). Further, Mythbuntu LTS releases are only 2 years not 5 (although the underlying stuff from Ubuntu still gets the 5 year treatment, we've only committed to doing new MythTV builds for 2 years). nickrout is quoting the official support statement from the Mythbuntu team regarding the MythTV updates PPA (which is where you are getting 0.25 and 0.26 for Lucid). 

Although the official statement is "...every MythTV version released during the lifetime (2 years) of an LTS release." (which 0.26 falls outside of), we would like to build 0.26 for Lucid. The issue is that because of the new features in 0.26 (and thus new dependencies), building 0.26 on Lucid is non-trivial. We continue to attempt to backport and resolve the necessary dependencies in order to build 0.26 on Lucid, but it may prove to be more work than it is worth.

---

