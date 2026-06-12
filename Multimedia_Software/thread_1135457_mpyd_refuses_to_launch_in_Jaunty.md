---
title: "mpyd refuses to launch in Jaunty"
date: 2009-04-24
forum: Multimedia Software
---

### Post by DJ_Peng on 2009-04-24
I had pympd running on Intrepid but after upgrading to Jaunty I had enough problems with my user profile that I ended up blowing away my previous install and did a freash install of Jaunty with a new user profile. Unfortunately now I can't get pympd to launch. When I run it from the CLI I get this error> $ pympd
Traceback (most recent call last):
  File "/usr/bin/pympd", line 12, in <module>
    import pympd
ImportError: No module named pympdFrom what I can see I have all of the dependencies met and searching around the 'net doesn't turn up any info on what's borking. Has anyone managed to get this fixed?

---

### Post by threespacemen on 2009-06-02
Same thing happened to me on two different boxes after the upgrade to 9.04 - looks like a python upgrade might have been the issue. If you open /usr/bin/pympd in your favourite editor, you'll see that the first line reads:

#!/usr/bin/python2.5

Change the 2.5 to 2.6 so that it reads:

#!/usr/bin/python2.6

Worked perfectly for me, but ymmv...

---

### Post by DJ_Peng on 2009-06-04
Sweetness! That did the trick. Thanks for posting the solution. I'll blog it to help others that are also having this issue.

---

