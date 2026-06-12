---
title: "Ubuntu Linux 20.04 - uninstall Cheese, Rhythmbox, Gnome videos?"
date: 2021-03-07
forum: Multimedia Software
---

### Post by la.khan on 2021-03-07
Hi all,

Recently, I installed Ubuntu Linux 20.04.2 LTS (64 bit). When playing multimedia files (like MP3s/MP4s), I prefer to use VLC instead of Rhythmbox and Gnome Videos, guvcview instead of Gnome Cheese and I have installed these applications.

Now, can I remove Rhythmbox, Gnome Videos, Gnome Cheese from my system as I feel these are redundant? Or, these applications have common files/libraries that are also used by VLC & guvcview?

Appreciate any insights/views on this. Thanks for your replies!

---

### Post by Dennis N on 2021-03-07
Removing an application X will not remove any of its dependencies, That includes libraries it shares with other applications.

Removing an application X WILL remove another application Y that depends on X.

---

### Post by cmcanulty on 2021-03-07
Also good to know , if you uninstall via synaptic it will show what other pkgs are also going to be removed. You can experiment with remove and completely remove in synaptic and see the details of each action before hitting apply.

---

### Post by CelticWarrior on 2021-03-07
> **cmcanulty said:**
> Also good to know , if you uninstall via synaptic it will show what other pkgs are also going to be removed. You can experiment with remove and completely remove in synaptic and see the details of each action before hitting apply.
Yes, but there's no need to install an additional complex frontend to the package manager when you can simulate any such operation just by adding a "-s" argument.

---

### Post by la.khan on 2021-03-07
Dennis N, cmcanulty, CelticWarrior: Thanks for your replies. I prefer to  use the terminal application, use command  
```
apt remove <package  name>
``` to remove applications.

I could find packages for cheese & rhythmbox but no packages for videos.
```

$dpkg -l | grep cheese
ii  cheese                                     3.34.0-1ubuntu1                     amd64        tool to take pictures and videos from your webcam
ii  cheese-common                              3.34.0-1ubuntu1                     all          Common files for the Cheese tool to take pictures and videos
ii  libcheese-gtk25:amd64                      3.34.0-1ubuntu1                     amd64        tool to take pictures and videos from your webcam - widgets
ii  libcheese8:amd64                           3.34.0-1ubuntu1                     amd64        tool to take pictures and videos from your webcam - base library

```
```

$dpkg -l | grep rhythmbox
ii  gir1.2-rb-3.0:amd64                        3.4.4-1ubuntu2                      amd64        GObject introspection data for the rhythmbox music player
ii  librhythmbox-core10:amd64                  3.4.4-1ubuntu2                      amd64        support library for the rhythmbox music player
ii  rhythmbox                                  3.4.4-1ubuntu2                      amd64        music player and organizer for GNOME
ii  rhythmbox-data                             3.4.4-1ubuntu2                      all          data files for rhythmbox
ii  rhythmbox-plugin-alternative-toolbar       0.19.3-1.1                          all          Enhanced play controls and interface for Rhythmbox
ii  rhythmbox-plugins                          3.4.4-1ubuntu2                      amd64        plugins for rhythmbox music player

```

Any idea the package name for Videos?

---

### Post by deadflowr on 2021-03-07
> Any idea the package name for Videos?

Totem

---

### Post by la.khan on 2021-03-07
> **deadflowr said:**
> Totem
deadflowr: Thanks for the reply and passing through!

Note: Today must be a Blue Moon ;)

---

