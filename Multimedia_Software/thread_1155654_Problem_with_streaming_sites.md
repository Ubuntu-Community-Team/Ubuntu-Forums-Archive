---
title: "Problem with streaming sites"
date: 2009-05-11
forum: Multimedia Software
---

### Post by a8j8i8t8 on 2009-05-11
Hi,

Somehow I am not able to watch videos from following sites.

[LIST]
[*][http://www.mightyfootball.com/](http://www.mightyfootball.com/)
[*][http://www.eplmatches.com/](http://www.eplmatches.com/)
[/LIST]
Please help me out.

I can watch YouTube videos, but many times it makes browser unresponsive.
I am using Ubuntu 9.04- the Jaunty Jackalope - released in April 2009.

Thanks in advance.

~Ajit

---

### Post by lovinglinux on 2009-05-11
Flash is really problematic. I'm currently experiencing difficulties with several sites, but I can play the first site you provided.

Try removing gnash and swfdec, then install adobe plugin.

[sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-installer ](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by a8j8i8t8 on 2009-05-13
Thanks.
That resolved the problem.

---

