---
title: "&quot;Arial Not-Rotated&quot; instead of &quot;Arial&quot;"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by stuffedZ on 2007-04-29
After upgrading to Feisty, almost all of the truetype fonts I have have been renamed to "Fontname Not-Rotated".

The "Not-Rotated" suffix comes from Pango so it and defoma must be to blame. The question is how to solve the problem.

The fonts which are not affected are Sans, Serif and Monospace. All three exist in /etc/defoma/fontconfig.subst-rule. Removing the names or adding Arial & co to the file has no effect on the file names.

Any ideas?

---

### Post by stuffedZ on 2007-04-29
The problem seems to appear when I have all of my 3000+ fonts activated.
With just the basic fonts installed the "Not Rounded" disappears.

Don't know why.

---

