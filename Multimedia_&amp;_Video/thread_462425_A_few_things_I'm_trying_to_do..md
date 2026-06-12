---
title: "A few things I'm trying to do."
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by Programmerfromthehood on 2007-06-02
Okay so I have keyboard that has a music icon, set that to have Rhythmbox to play when I press it. The thing is, I want Amarok to play when I press it. So when do I go to change that?

Also I would like to know where to go so when I pop a DVD in, Xine plays it, not Totem, so I won't have to manually start Xine.

Any help or tips?

Thanks in advance!!

---

### Post by Programmerfromthehood on 2007-06-02
Okay so I have keyboard that has a music icon, set that to have Rhythmbox to play when I press it. The thing is, I want Amarok to play when I press it. So when do I go to change that?

Also I would like to know where to go so when I pop a DVD in, Xine plays it, not Totem, so I won't have to manually start Xine.

Any help or tips?

Thanks in advance!!

---

### Post by yabbadabbadont on 2007-06-02
In Gnome it would be set using System->Preferences->Preferred Applications.

---

### Post by Programmerfromthehood on 2007-06-02
> **yabbadabbadont said:**
> In Gnome it would be set using System->Preferences->Preferred Applications.All that lets me do is change my web browser, terminal, and Mail reader.

---

### Post by yabbadabbadont on 2007-06-02
Doh!  :oops:

I think you need to use the keyboard-shortcuts preference to see if they are specified in there somewhere.  (which makes more sense than my first post)

---

### Post by Programmerfromthehood on 2007-06-02
> **yabbadabbadont said:**
> Doh!  :oops:

I think you need to use the keyboard-shortcuts preference to see if they are specified in there somewhere.  (which makes more sense than my first post)No, but getting closer, I think.

---

### Post by Fell on 2007-06-02
I'm not too sure about your first query but the second is easy enough.

Go to System, preferences, removable drives and media. Select the Multimedia tab and you can change your default DVD player there.

---

### Post by blackened on 2007-06-02
For the second question look in the "Multimedia" tab in System -> Preferences -> Removable Drives and Media.

---

### Post by Programmerfromthehood on 2007-06-02
> **Fell said:**
> I'm not too sure about your first query but the second is easy enough.

Go to System, preferences, removable drives and media. Select the Multimedia tab and you can change your default DVD player there.Thanks, it worked.

---

### Post by blackened on 2007-06-02
Per the first question, took some searching, but I've found a usable workaround. See the 4th post on this page: [https://bugs.launchpad.net/control-center/+bug/4265]("https://bugs.launchpad.net/control-center/+bug/4265").

Seems this "feature" is hardcoded into Gnome until Gutsy comes out. Ask back if you need help implementing the workaround.

---

### Post by Programmerfromthehood on 2007-06-03
> **blackened said:**
> Per the first question, took some searching, but I've found a usable workaround. See the 4th post on this page: [https://bugs.launchpad.net/control-center/+bug/4265]("https://bugs.launchpad.net/control-center/+bug/4265").

Seems this "feature" is hardcoded into Gnome until Gutsy comes out. Ask back if you need help implementing the workaround.Yeah, I do need a little help, can you just put what I need to put in the terminal in order to do this? Because it doesn't work with the stuff I'm typing. I feel like an idiot.

---

### Post by blackened on 2007-06-03
Ok, the order of directories in the path variable can be found by typing ```
echo $PATH
``` into the terminal.

Basically the path variable allows you to type only the program's short name (i.e. rhythmbox) into the terminal and the shell will search for that particular executable in all the directories listed in the path variable. So, in the preferred application hardcoded into Ubuntu, they didn't include the full path to the rhythmbox executable, but instead relied on the path variable to sort this out for them. To exploit this you need to create a symlink named *rhythmbox* in /usr/local/bin that points to the executable of the application you want to use instead that resides in (preferrably) /usr/bin. Since /usr/local/bin precedes /usr/bin in the path variable the shell will check that directory first and launch the symlink that it finds.

Sorry this is long-winded, but I figured maybe the background information would be useful. So here's the terminal line you need:

```
sudo ln -s /usr/bin/*mediaplayer* /usr/local/bin/rhythmbox
```

Replace *mediaplayer* with the executable of your preferred media application. Hope this helps.

---

### Post by captgadget on 2007-06-04
Blackened, I followed your link and found the fix.

thanx

here it is: ln -s /usr/bin/xmms /usr/local/bin/rhythmbox

with xmms being your choice of players you have assigned to play your files. For me it was Amarok

---

