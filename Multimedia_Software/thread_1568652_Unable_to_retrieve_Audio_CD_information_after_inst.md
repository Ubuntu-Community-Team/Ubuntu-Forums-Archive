---
title: "Unable to retrieve Audio CD information after installing ubuntu-restricted-extras"
date: 2010-09-05
forum: Multimedia Software
---

### Post by nastev on 2010-09-05
Hi,

I've got Ubuntu 10.4 and have been using Rhythmbox to play CDs.  When I put a CD in it would always be recognised and Rhythmbox would display the artist and song titles.  Today I installed the following package:

ubuntu-restricted-extras

This was so I could rip CDs to MP3s.  This worked, however it seems to have also had the side effect of preventing Rhythmbox from retrieving information about audio CDs.  If I run Rhythmbox from a shell I get the following debug:

** (rhythmbox:2271): DEBUG: Loading the real store page
** (rhythmbox:2271): DEBUG: navigation requested to [https://one.ubuntu.com/music/store-no-token](https://one.ubuntu.com/music/store-no-token)
** (rhythmbox:2271): DEBUG: navigation requested to [http://stores.7digital.com/default.aspx?shop=34&partner=983](http://stores.7digital.com/default.aspx?shop=34&partner=983)
This CD could not be queried: Cannot send/receive to/from server.

Does any one know how to fix this so I can get Rhythmbox to successfully retrieve CD information again?  Thanks in advance for any help you can give me.

Neil

---

### Post by nastev on 2010-09-05
Thanks to ne 1 who looked at this.  It seems to of sorted itself at now.  Sorry should of tried a reboot before posting.

---

