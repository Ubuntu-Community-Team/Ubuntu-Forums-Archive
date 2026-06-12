---
title: "I want to upgrade VLC to 0.9.2"
date: 2008-09-20
forum: Multimedia Software
---

### Post by thunderdan on 2008-09-20
This is probably something really simple that I am just ignorant about, so I hope you can help me. I have VLC 0.8.6. I know that VLC has been updated to 0.9.2 and I want to get the new version. I tried this:

```
sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
```

but the terminal output was this:

```
daniel@olivehillsyndicate-desktop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
vlc-plugin-esd is already the newest version.
mozilla-plugin-vlc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daniel@olivehillsyndicate-desktop:~$ 

```

But when I open VLC and go to Help > About, it says it's 0.8.6.

So how do i get it to install 0.9.2 instead of 0.8.6?

Thanks,
Thunder Dan

---

### Post by IanW on 2008-09-20
VLC 0.9.2 has not yet been packaged for Hardy. It may go into the Backports repository after Intrepid's release.
Track [Bug #270404](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/270404) for more info

---

### Post by thunderdan on 2008-09-20
I don't really understand that bug thing, but I think what your saying is I should wait for the new version of Ubuntu next month before I upgrade VLC?

---

### Post by dualpretop on 2008-09-20
[http://ubuntuforums.org/showthread.php?t=920204&page=3&highlight=vlc](http://ubuntuforums.org/showthread.php?t=920204&page=3&highlight=vlc)

---

### Post by gandaran on 2008-09-20
you could look for a .deb VLC 0.9.2 package, try looking in getdeb or google for a vlc 0.9.2 .deb , one sure way of getting it is from Intrepid's repositories, to install just double click the .deb package.

---

### Post by mc4man on 2008-09-20
A hardy .deb is available, several threads around. I tried it and while overall it had some nice features and look, there are issues, overall and with the package.
The package is a debug ver. which has some annoying elements. 
Opening directories from vlc is (or was) broken, opening vlc from a directory worked.

I'd wait for a more polished vlc and package.

If you install and don't like make sure to remove *everything* associated with vlc marked with green in synaptic before *reinstalling* the old one. (in other words search vlc and remove everything with vlc in the name

[http://ubuntuforums.org/showthread.php?t=922149](http://ubuntuforums.org/showthread.php?t=922149)

---

### Post by thunderdan on 2008-09-20
> **dualpretop said:**
> [http://ubuntuforums.org/showthread.php?t=920204&page=3&highlight=vlc](http://ubuntuforums.org/showthread.php?t=920204&page=3&highlight=vlc)

Cool, cool. I tried that command and it did something. I'm not exactly sure what. There was a LOT of output in the terminal when I did it.

But when I started up VLC again, it still said 0.8.6. But it's OK.

---

### Post by thunderdan on 2008-09-20
> **mc4man said:**
> A hardy .deb is available, several threads around. I tried it and while overall it had some nice features and look, there are issues, overall and with the package.
The package is a debug ver. which has some annoying elements. 
Opening directories from vlc is (or was) broken, opening vlc from a directory worked.

I'd wait for a more polished vlc and package.

If you install and don't like make sure to remove *everything* associated with vlc marked with green in synaptic before *reinstalling* the old one. (in other words search vlc and remove everything with vlc in the name

[http://ubuntuforums.org/showthread.php?t=922149](http://ubuntuforums.org/showthread.php?t=922149)

OK, cool, cool. I think I should probably wait until Intrepid comes out.

By the way, doesn't "Intrepid" sound so much cooler than "Hardy," "Gutsy" or "Feisty?"

---

### Post by mc4man on 2008-09-20
> I tried that command and it did something. I'm not exactly sure what
you installed some compiling 'tools', no harm to have, though one 'should 'be careful running commands at random

---

