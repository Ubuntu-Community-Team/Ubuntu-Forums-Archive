---
title: "Why was 0.21.0 added to the Gutsy release???"
date: 2008-03-18
forum: Mythbuntu
---

### Post by elvis on 2008-03-18
I do hope the package maintainers for Mythbuntu are reading this...

0.21.0 appeared in gutsy-backports a short while ago (the version prior to that being 0.20.2).  Me being the trusting fool I am "apt-get upgrade"ed (at the time I needed to update my kernel to fix a problem with my IDE controller), and promptly broke my MythBuntu box badly.

Not that it's a huge drama.  I removed gutsy-backports from my sources.list, downgraded back to 0.20.2, and rolled back my database to the last good backup (6 days eariler).  There was a minor inconvenience of losing a week's worth of recordings, but nothing life threatening.

But it begs the question, why on earth was 0.21.0 thrown in?  Ubuntu 8.04 is just around the corner.  Wouldn't it have made sense to hold off the entire 30-something days and have 0.21.0 appear in MythBuntu 8.04?  

Look at other packages in Ubuntu 7.10 - OpenOffice, Pidgin IM, etc.  These are all lagging behind the bleeding edge, but the package maintainers don't go jumping into the bleeding edge in order to reduce breakages.  We can all mass upgrade to the latest and greatest when the next release of Ubuntu hit's stable.

I'm not trying to shift the blame here.  I'm completely aware that I should have taken the ten seconds to check the packages being upgraded before hitting the "Y" key.  But again, Ubuntu's policy has been for some time not to make radical version jumps in stable releases just for the hell of it, and I'd hope that in the future MythBuntu conforms a little better to these guidelines.

If people want the bleeding edge, they can go grab the source.  For the rest of us, having nice stable and reliable distros that don't make major version changes at the drop of a hat would be really nice.

FWIW, the upgraded kernel [the reason I upgraded in the first place) was not a major upgrade (2.6.22.14.20 to 2.6.22.14.21), and actually fixed my IDE controller issue (meaning my DVD watching doesn't die randomly any more).  A perfect example of how backports should actually work - keeping major releases the same, and only fixing known bugs, rather than upgrading to major version bumps in the middle of a stable release lifespan.

It should be added that I'm not the only one bitten by this.  There are many others not only in these forums, but also on various mailing lists and public forums around the web who also are left scratching their head as to why their MythBuntu setups are working fine one day, and are broken the next.

---

### Post by superm1 on 2008-03-18
Hi Elvis,

These were added because there was a demand for them.  Folks were expecting to be able to switch myth versions easily, and not necessarily have to risk moving all their apps when going to 8.04.

They were put into backports so that they were easy to opt in or out.

If people are having trouble with these builds, now is the time to file bugs...  We don't have much time between now and 8.04, so if they don't get fixed now, they won't be fixed for 8.04.

---

### Post by tgm4883 on 2008-03-18
Please note the comment for the backports repo

> ## Uncomment the following two lines to add software from the
'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

---

