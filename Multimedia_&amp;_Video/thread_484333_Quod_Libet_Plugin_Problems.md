---
title: "Quod Libet Plugin Problems"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by loversriot on 2007-06-25
I've been trying to find a music player for a while now, and I've given many a shot. I'm liking Quod Libet, and know it has plugins that would be helpful, but I'm an idiot so I'm not sure how I'm supposed to install them.

I've searched through the forums for an answer, and was hoping the quodlibet-plugins package that is referred to most of the time would be helpful, but it wouldn't install.

The idea is that I should have
~/.quodlibet/plugins/editing/
~/.quodlibet/plugins/events/
~/.quodlibet/plugins/songsmenu/
but I'm not sure how to make those folders.
I realize I don't really NEED those folders, but I guess knowing how to create them would be pretty good in the future.

Also, how am I supposed to add .py files to those folders? Once again, I'm an idiot. But I'd like to figure these things out, so that I can hopefully learn how to solve these problems on my own at some point. Thanks for any help.

---

### Post by hugmenot on 2007-06-25
First, what happens if you try to install that package? Error messages?
Then, the dot in .quodlibet indicates that this folder is hidden in the file system. You can make it visible in the file browser by hitting Ctrl+H. Then you proceed to create the folder structure you cited.

It &#8217;s a lot easier to just install the package, though.

---

### Post by loversriot on 2007-06-25
I was getting error messages, yes. It was saying I didn't have Ex Falso installed, but I did. After multiple uninstall/reinstalls, the quodlibet-plugins package finally "found" the dependencies (Ex Falso) necessary.

It was a lot easier, yes, but I'd still like to know how to create that folder structure. I knew where to get to in the filesystem, the problem for me is not knowing how to access/create as root. .debs are my best friend, haha.

---

### Post by hugmenot on 2007-06-26
Oh you do not need root since these folders you want to create are in your own home folder.

the tilde ~ is a shorthand for /home/loversriot for instance, so the folders to create are right in your home dir.

---

