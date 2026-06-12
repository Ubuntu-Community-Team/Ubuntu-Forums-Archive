---
title: "Inkscape 'Pattern along Path' breaks"
date: 2010-07-10
forum: Multimedia Software
---

### Post by Jay Colfer on 2010-07-10
I am using Ubuntu 10.04, and:

inkscape:
  Installed: 0.47.0-2ubuntu2
  Candidate: 0.47.0-2ubuntu2
  Version table:
 *** 0.47.0-2ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status

------------------------------------

My problem: When trying to generate text along a curve via:

1. Select path of curve
2. Select path of text
3. Extensions > Generate from Path > Pattern along Path

And attempting to preview or apply with any or no settings at all, Inkscape informs me that:

Inkscape has received additional data from the script executed. The script did not return an error, but this may indicate the results will not be as expected.

Traceback (most recent call last):
  File "/usr/share/inkscape/extensions/pathalongpath.py", line 278, in <module>
    e.affect()
  File "/usr/share/inkscape/extensions/inkex.py", line 207, in affect
    self.effect()
  File "/usr/share/inkscape/extensions/pathalongpath.py", line 268, in effect
    self.applyDiffeo(ctlpt[1],(ctlpt[0],ctlpt[2]))
  File "/usr/share/inkscape/extensions/pathalongpath.py", line 166, in applyDiffeo
    i,t=self.lengthtotime(s)
  File "/usr/share/inkscape/extensions/pathalongpath.py", line 150, in lengthtotime
    l=l % sum(self.lengths)
ZeroDivisionError: float modulo
------------------------------------

And then nothing happens.

I tried running Inkscape-0.47-3 under WINE and it crashed when attempting the operation with the same .SVG file.

I filed a bug, but if there's a workaround I haven't figured out, that'd be great as I'm kind of in the middle of a project here :\

Thanks!

---

