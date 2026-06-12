---
title: "Watching Yahoo video kicks Ubuntu in the nuts"
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by dwhitney67 on 2007-07-21
I was attempting to view a Yahoo video news clip and the most bizarre thing happened.... my current login session was blown away (along with everything else) and I was then staring at the login prompt.

On my Ubuntu system, which is installed with Version 7.04, I have Firefox 2.0.0.4.  Firefox has the following plugin for WMP video:  libtotem-gmp-plugin.so (version 2.18.1).

Now, I can understand a plugin or other application failing, but to be able to kick my login session in the "nuts" (i.e. cause it to crash) indicates that there is something unaccounted for in the Ubuntu distro that needs to be addressed.  How Firefox (or the plugin) could trample over another application's memory is worrisome.

Here's the link to the video I was trying to view:  javascript:void(window.open('http://cosmos.bcst.yahoo.com/up/localnews?ch=952695&cl=3408621&lang=en', 'playerWindow','width=792,height=666,scrollbars=no'));

I'd love to see if anyone else has experienced this issue or has a solution to it.  I believe my Ubuntu system to be up to date with all the newest software releases.

---

### Post by Gremlinzzz on 2007-07-21
you say you have Firefox 2.0.0.4. Firefox
i have Mozilla Firefox 2.0.0.5 the old firefox has serious issues maybe you should check your updates
:guitar:

---

### Post by hanzomon4 on 2007-07-21
Works here, it sounds like something caused your xsession to restart. You could have pressed a key combination (ctrl+alt+backspace) or something else could have happened. I doubt it was firefox but I can't be sure.

---

### Post by Gremlinzzz on 2007-07-21
> **Gremlinzzz said:**
> you say you have Firefox 2.0.0.4. Firefox
i have Mozilla Firefox 2.0.0.5 the old firefox has serious issues maybe you should check your updates
:guitar:
how to check your firefox install just type in the terminal
firefox -version 
:guitar:

---

