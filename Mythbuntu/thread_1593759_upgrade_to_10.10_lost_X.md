---
title: "upgrade to 10.10 lost X"
date: 2010-10-11
forum: Mythbuntu
---

### Post by portwojc on 2010-10-11
I went from mythbuntu 8 (I think that was it) to 10.4 on my backend with no problems.  Then I upgraded my front end and had an error with grub that I couldn't get past.  No biggie I just reinstalled with the disk.  Not thinking I grabbed the 10.10 download.  So flash forward my backend then didn't work with the front end because of the mythtv versions.  So then I moved the backend to version 10.10.

During that upgrade I got the error message:

Couldn't configure pre-depend x11-common for x11-xkb-utils, probably a dependency cycle.

I read this is the fix for that:

sudo apt-get remove x11-xkb-utils

That let me get past the error and install the 10.10 update.

Now after upgrading my backend won't start up X.  I can watch TV from the front end so it's not a huge problem but I would like to fix the backend obviously so I can watch TV from there.

How do I get the x-windows interface back to the mythbuntu version of x-windows / auto login and such?

I did try reinstalling that x11-xkb-utils but it didn't help.  As well as xubuntu-desktop.

Thank you,

Jason

---

