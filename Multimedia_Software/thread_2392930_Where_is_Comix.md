---
title: "Where is Comix"
date: 2018-05-27
forum: Multimedia Software
---

### Post by hmag on 2018-05-27
Hello

Until recently I was using comix viewer on my xubuntu.
I installed a fresh 18.4 LTS and it seems that comix does no longer come with the software center.
I tried "sudo apt-get install comix" and apt does not find the packqge
Why ?
Comix used to be part of the distrib. How can get it ?

Thanks

---

### Post by PaulW2U on 2018-05-27
> **hmag said:**
> Until recently I was using comix viewer on my xubuntu.
I installed a fresh 18.4 LTS and it seems that comix does no longer come with the software center.
I tried "sudo apt-get install comix" and apt does not find the packqge

[http://comix.sourceforge.net/](http://comix.sourceforge.net/) and [https://tracker.debian.org/pkg/comix](https://tracker.debian.org/pkg/comix) suggest that comix had not been updated since 2009 so was removed from Debian Testing, upon which Ubuntu is based, in January. It would have been removed from what was to become Ubuntu 18.04 shortly after. You need to look for an alternative application as comix won't be coming back unless someone decides to update and maintain it again. Given the nine years that have passed since the last update that doesn't look very likely.

---

### Post by hmag on 2018-05-28
> **PaulW2U said:**
> [http://comix.sourceforge.net/](http://comix.sourceforge.net/) and [https://tracker.debian.org/pkg/comix](https://tracker.debian.org/pkg/comix) suggest that comix had not been updated since 2009 so was removed from Debian Testing, upon which Ubuntu is based, in January. It would have been removed from what was to become Ubuntu 18.04 shortly after. You need to look for an alternative application as comix won't be coming back unless someone decides to update and maintain it again. Given the nine years that have passed since the last update that doesn't look very likely.

Thanks PaulW2U

I found a "self-claimed-to-be" alternative in software Center, named "MComix.something". But I immediately faced 2 defects that are blocking for my usage. Is it supposed to be tested ? Should I file bugs ? Below are the 2 defects:

- I cant browse directories / open files that are beyond my Home directory, even if I have the required access privilèges. I generally store my multimedia files on a remote share that I mount somewhere Under '/mnt'. With MComix, it is impossible to browse/open such files while I can access them with other KDE Tools like Thunar, Image viewer, etc...

- "MComix.something" installation package comes with no association of the ".zip" extension (and/or other compressed archive files). As a result, I can't right-click from Thunar on a compressed archive and select "Open with... MComix" from context menu. Comix installation was coming with this feature...

Thanks & BR
HMag

---

### Post by #&amp;thj^% on 2018-05-28
Mcomix is just a bit different at first look.
To add to your library open "Mcomix" and use keyboard <ctrl+l> that should open another window, and at the bottom you will see "Watch list" now you add folders and others such as ".zip" extension or ".gz".
Just play with it for a bit.
EDIT I now see PaulW2U post below mine, and I installed mine differently, I used a .deb file to install which was no easy task.
But read PaulW2U's post #6 in the link.
Good Luck
BTW Mcomix is a fork off of Comix, for what it's worth. ;)
> MComix is a fork of the Comix project, and aims to add bug fixes and stability improvements after Comix development came to a halt in late 2009.

---

### Post by PaulW2U on 2018-05-28
Hi hmag, I'm glad you found an alternative.

That program is packaged as a "snap" rather than a "deb" package which I think makes browsing files other than in your home directory different to what you have experienced in the past. I installed **mcomix-tabetai** in my test installation and found the same problem. Hopefully someone will advise how you can get around that.

I know very little about snaps I'm afraid.  :(

---

### Post by PaulW2U on 2018-05-28
hmag, does this thread help? - [https://ubuntuforums.org/showthread.php?t=2392242](https://ubuntuforums.org/showthread.php?t=2392242)

You probably need to set permissions when installing the snap. I missed the button too.  :)

---

