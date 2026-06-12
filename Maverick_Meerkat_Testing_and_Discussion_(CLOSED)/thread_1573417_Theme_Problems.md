---
title: "Theme Problems"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by HalfEmptyHero on 2010-09-12
I just installed the beta, and for some reason themes are not working. The only place where the themes are actually being used is in the appearance preferences window, in all other windows it is just the ugly theme that is used when there is no theme. I attached a screenshot to better explain. I haven't done anything to the beta besides installing updates and installing the nvidia driver, but the same thing happened before the updates.

---

### Post by exploder on 2010-09-12
Different themes require different theme engines to display properly. I think you are just needing to install the theme engine that the theme you have installed requires.

---

### Post by HalfEmptyHero on 2010-09-12
I am aware of that, however that can't be the issue since the appearance preferences gets rendered correctly.

---

### Post by 23meg on 2010-09-12
Is gnome-settings-daemon running? If not, that might be your problem

---

### Post by HalfEmptyHero on 2010-09-12
No, it doesn't look like it was. For some reason it will only run as root, if I run it normally the theme doesn't change and I get the error ```
** (gnome-settings-daemon:2147): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:2147): WARNING **: Could not acquire name

```

If I run it as root the theme starts working. I shouldn't have to run it as root, should I?

---

### Post by 23meg on 2010-09-12
[QUOTE=HalfEmptyHero]If I run it as root the theme starts working. I shouldn't have to run it as root, should I?[/QUOTE]

No. It should run by itself on startup as a process owned by you; that it doesn't is almost certainly the problem. Do a search for the errors you get and see if there are bugs that are reported already.

---

### Post by HalfEmptyHero on 2010-09-12
Thanks for all the help, this link fixed it for me.
[http://ubuntuforums.org/showpost.php?p=3776732&postcount=15](http://ubuntuforums.org/showpost.php?p=3776732&postcount=15)

---

### Post by exploder on 2010-09-12
I found some information that might help. 

> sudo cp -r /home/<user>/.themes/<your current applied theme> /usr/share/themes 

This thread seemed very similar.

[http://guide.ubuntuforums.org/showthread.php?p=4763943](http://guide.ubuntuforums.org/showthread.php?p=4763943)

Hope this helps. :)

Edit: We must have posted about the same time. Glad you found a solution.

---

