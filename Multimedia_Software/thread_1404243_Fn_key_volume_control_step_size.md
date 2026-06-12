---
title: "Fn key volume control step size"
date: 2010-02-11
forum: Multimedia Software
---

### Post by vadarfone on 2010-02-11
Evening

Was wondering; is there a way to adjust the size of the steps the Fn key makes to the volume control in Ubuntu.

As standard, the steps are very large and do not offer me enough control; if something is too loud when it is playing, and I touch my volume control once, it drops it by quite a large step, and makes it too quiet!

Any way to adjust this?

Thanks in advance.

---

### Post by linusr on 2010-02-11
will be really nice to adjust the step size for both volume & brightness..

---

### Post by vadarfone on 2010-02-12
Yeah, that too.

Any idea how this can be achieved?

Really need to get this done, as audio is a very large part of what I use computers for.

---

### Post by rb-cohen on 2010-02-19
You can change the step size using gconf-editor.

[LIST=1]
[*]Alt + F2
[*]Type "gconf-editor" and press Enter
[*]Browse to Apps > gnome_settings_daemon
[*]On the right hand side, change volume_step to a lower number
[/LIST]

The default seems to be 6, I find 3 works a lot better.

[http://www.blograndom.com/blog/2010/02/change-volume-key-step-size-in-ubuntu/]("http://www.blograndom.com/blog/2010/02/change-volume-key-step-size-in-ubuntu/")

---

### Post by Zookalicious on 2011-03-26
Not an original poster but thank you rb-cohen! Your advice helped me out a lot.

---

### Post by kid1000002000 on 2012-01-15
Workarounds are good, but don't forget to subscribe to this bug to get this fixed in 11.10.
[https://bugs.launchpad.net/ubuntu/+s...on/+bug/871133]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133")

---

