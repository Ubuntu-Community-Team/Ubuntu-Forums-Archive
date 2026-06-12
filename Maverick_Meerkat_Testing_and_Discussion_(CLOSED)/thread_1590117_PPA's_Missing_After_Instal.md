---
title: "PPA's Missing After Instal"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2010-10-07
Just did a fresh install on my desktop and the PPA's for 'canonical partners' and 'independent' are missing. I installed the exact same way as I had on my netbook (10.10 UNE RC) and laptop (10.10 Desktop RC) but like I said the software sources seem to be missing.

I used the daily build from the 6th October.

Can somebody please tell how to add manually?

Thank you!

---

### Post by viralmeme on 2010-10-07
> **victor9098 said:**
> the PPA's for 'canonical partners' and 'independent' are missing

[Adding Canonical Partner Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by victor9098 on 2010-10-07
> The "Third-Party Software" tab is where you will be able to add the Canonical Partner Repositories. You will see two Canonical Partner repositories listed - one for applications and another for source code (src). The partner repositories offer access to proprietary and closed-source software and are not enabled by default. Users must specifically enable these 'partner' repositories. Select "Close" and "Reload" to save and update the database if you chose to add either or both of them. 

Problem is there is nothing there! Just a lot of blank space.

I know it is the > ppa:[username]/[ppaname] format, but is it just ppa:canonical/ppa??

---

### Post by donniezazen on 2010-10-07
> **victor9098 said:**
> just did a fresh install on my desktop and the ppa's for 'canonical partners' and 'independent' are missing. I installed the exact same way as i had on my netbook (10.10 une rc) and laptop (10.10 desktop rc) but like i said the software sources seem to be missing.

I used the daily build from the 6th october.

Can somebody please tell how to add manually?

Thank you!

+1

---

### Post by cariboo on 2010-10-07
There was a problem, a fix has been released. Bug #[lpbug]656037[/lpbug]

---

### Post by victor9098 on 2010-10-07
I ended up creating a 'false' apt entry in the 'other software' tab, then inputting all the correct details from my other installs. Ran update and everything seems to be working fine now with the correct details and getting updates.

Thanks for pointing me in the direction of the bug report

---

