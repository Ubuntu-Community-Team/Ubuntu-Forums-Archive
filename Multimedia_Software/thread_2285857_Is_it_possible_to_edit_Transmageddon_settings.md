---
title: "Is it possible to edit Transmageddon settings?"
date: 2015-07-08
forum: Multimedia Software
---

### Post by Rytron on 2015-07-08
Hi.

Is it possible to have Transmageddon to have the Output Format set at webm as default instead of ogg? Is it also possible to save output videos on the Desktop instead of in ~/Videos?
I see no config file in the home directory.

Thanks.

---

### Post by Rob Sayer on 2015-07-09
The config file may not be in /home.  That  type of thing may be in /usr/share.

---

### Post by mc4man on 2015-07-09
Transmageddon is a python script. to adjust to Desktop you'd edit /usr/share/transmageddon/transmageddon.py 
Easiest for ~/Desktop is to edit the default XDG UserDir line for videos -  Blue is by default VIDEOS

      ```
       # Set the Videos XDG UserDir as the default directory for the filechooser
       # also make sure directory exists
       #if 'get_user_special_dir' in GLib.__dict__:
       self.videodirectory = \
                   GLib.get_user_special_dir(GLib.UserDirectory.DIRECTORY_[COLOR="#0000CD"]DESKTOP[/COLOR])
       self.audiodirectory = \
                   GLib.get_user_special_dir(GLib.UserDirectory.DIRECTORY_MUSIC)
```

---

### Post by Rytron on 2015-07-09
> **Rob Sayer said:**
> The config file may not be in /home.  That  type of thing may be in /usr/share.

Ah yes, I found it here: /usr/share/transmageddon

Not sure what to edit though.

It seems odd that a program would not have a home dir config file.

---

### Post by Rytron on 2015-07-12
Is it also possible to add a queue to Transmageddon like the Enqueue feature in Handbrake?

---

### Post by Rytron on 2015-07-13
> **mc4man said:**
> Transmageddon is a python script. to adjust to Desktop you'd edit /usr/share/transmageddon/transmageddon.py 
Easiest for ~/Desktop is to edit the default XDG UserDir line for videos -  Blue is by default VIDEOS

      ```
       # Set the Videos XDG UserDir as the default directory for the filechooser
       # also make sure directory exists
       #if 'get_user_special_dir' in GLib.__dict__:
       self.videodirectory = \
                   GLib.get_user_special_dir(GLib.UserDirectory.DIRECTORY_[COLOR="#0000CD"]DESKTOP[/COLOR])
       self.audiodirectory = \
                   GLib.get_user_special_dir(GLib.UserDirectory.DIRECTORY_MUSIC)
```

Thanks you mc4man. This works fine.

---

### Post by Rytron on 2015-07-13
Would it be ok to run multiple instances of Transmageddon to run lets say 2 to 3 transcodings at once?

---

