---
title: "MCC &amp; Activate Mythbuntu Update repository - wrong ppa url"
date: 2014-07-07
forum: Mythbuntu
---

### Post by andrew-codrington on 2014-07-07
Hi there,
Sorry if this is a dupe, it wouldn't let me search for the ppa URL which was the best idea I had...

I upgraded to Trusty Taur on my old mythbuntu box on the weekend.

It started throwing errors from Software Updater that looked like incorrect repos were configured.

When I got a minute to check it looked like the mythbuntu updates ppa was the problem.

When I use MCC to 'Activate Mythbuntu Updates' it sets up a repo like this:
[http://ppa.launchpad.net/mythbuntu/testing/ubuntu/dists/](http://ppa.launchpad.net/mythbuntu/testing/ubuntu/dists/)

When I look there, there isn't a trusty folder.
I poked around the PPA site, and guessed that it should really be:
[http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/dists/](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/dists/)

That seems to make the system happier, and it's updating without errors now.

If this is just my machine, please go on and ignore this. If others hit the same snag I can probably help figure out what happened with some testing.

Cheers,
Andrew

---

