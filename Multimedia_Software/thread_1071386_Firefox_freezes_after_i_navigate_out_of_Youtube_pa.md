---
title: "Firefox freezes after i navigate out of Youtube page"
date: 2009-02-16
forum: Multimedia Software
---

### Post by kiruch on 2009-02-16
and not only Youtube - basically any page with flash video on it (Youtube, Tudou, Vkontakte).
the page loads okay, the video plays okay, but when i either close the tab or click a link inside the tab, Firefox absloutely stops responding.

is there a way to fix it?

(Kubuntu 8.04 / Firefox 3.0.6 / Adobe Flash Player 9)

---

### Post by ajgreeny on 2009-02-16
I suggest you use flash v10 from the ubuntu partner repositories.  In synaptic go to Settings > Repositories > Third Party Software tab and there make sure the **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) partner** is checked.  Now refresh your repos by clicking the icon at the top and then completely uninstall the *flashplugin-nonfree* and install the *adobe flashplugin*.  It is so much better than flash v9, and may solve your problem.

---

### Post by kiruch on 2009-02-17
i'm using Kubuntu, so there are some minor differences. there's Adept instead of Synaptic, am i right?

anyway, i've found a tab "Third Party Software" somewhere in Adept and checked the repository you mentioned. when i pressed Apply, though, Adept told me that some other process was using Adept's files ("probably another instance of Adept or apt-get", as it said), so the database couldn't be updated.
i checked the Process Table - no trace of such processes. i'm kind of confused.

by the way, can i add repositories via terminal? there's nothing about it in "man apt-get", but i think there should be some option for "apt-get".

thanks in advance.

---

### Post by kiruch on 2009-02-19
guys?

---

### Post by itang sanjana on 2009-02-19
Getting the flash player:
[http://ubuntuforums.org/showpost.php?p=6705128&postcount=6](http://ubuntuforums.org/showpost.php?p=6705128&postcount=6)

For the concept of apt-get:
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/apt-get.html)

For the concept of sudo in Kubuntu:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

HTH

---

### Post by kiruch on 2009-02-21
It doesn't work!

I've removed flashplayer-nonfree and "clean"ed the apt-get. Then i've downloaded and executed install_flash_player.deb (for Ubuntu 8.04+).

It says "installation complete". 

Then i open my Firefox, and the flash player is gone. It's not in the Plugins section, either.
When i decided to install the .deb file one more time, and instead of the button "install" there was a button "reinstall".

So, to cut a long story short, a program that installs debian packages thinks it's installed correctly, while firefox doesn't want to admit it.

---

