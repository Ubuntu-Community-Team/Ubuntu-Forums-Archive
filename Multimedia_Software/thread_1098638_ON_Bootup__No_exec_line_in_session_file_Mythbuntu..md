---
title: "ON Bootup:  No exec line in session file: Mythbuntu. Running Gnome failsafe session.."
date: 2009-03-17
forum: Multimedia Software
---

### Post by Committed on 2009-03-17
I installed mythtv on my ubuntu machine yesterday.  Quite an ordeal but got it running.  Now when I boot up I get the error message:

No exec line in session file: Mythbuntu. Running gnome failsafe session instead.


Any ideas where to start?

---

### Post by Committed on 2009-03-17
Please, please, pretty please...

Everything's working, got my schedules direct installed, but still when I boot up the machine, I get the same message.  It seems to me like maybe somethings pointing it to boot to Mythbuntu, but I have it set to boot to Ubuntu.????????????

---

### Post by Robsteranium on 2009-04-25
I've received a similar error after upgrading to jaunty.

As per the comments on this [bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-utils/+bug/354204") try:
[LIST=1]
[*]running ```
sudo gdmsetup
```
[*]or editing ```
$HOME/.dmrc
```
[/LIST]

I'm afraid I don't know enough about Mythbuntu to tell you what your settings ought to be.  On Xubuntu I needed to change "xfce4" to "xfce" in my .dmrc file.

---

### Post by ShelJ on 2009-04-25
Thanks [Robsteranium]("http://ubuntuforums.org/member.php?u=313302"),

Your suggestion helped me. so I'm going to redirect someone from another post to here.

---

