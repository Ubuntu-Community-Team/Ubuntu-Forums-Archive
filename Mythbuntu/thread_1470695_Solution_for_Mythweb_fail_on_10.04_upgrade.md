---
title: "Solution for Mythweb fail on 10.04 upgrade"
date: 2010-05-03
forum: Mythbuntu
---

### Post by hibit on 2010-05-03
Just a note in case this solution which worked for me might help others. On upgrading mythweb was inaccessible whereas previously it has been fine. I found that in my case apache didn't have a couple of the modules enables that are required for mythweb to work. Using sudo try the following which are suggested in the mythweb install instructions:

a2enmod deflate
a2enmod headers
a2enmod auth_digest

and then as suggested restart the webserver, again using sudo. You might find you have other problems, but this was what worked for me.

---

