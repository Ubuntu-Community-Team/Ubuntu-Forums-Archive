---
title: "mplayer plugin bug?"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by Bloch on 2006-10-25
My mplayer plugin stopped working after the recent update. It was not detected when I typed 
aboutlugins
in the address bar.
However when I uninstall and reinstall nothing changes. I tried a lot of things (including letting Automatix handle the installation) and nothing worked. Synaptic claims the plugins are there and uptodate; but Firefox doesn't see them.

I've searched through the forum but the info is quite old and doesn't help.

I would appreciate any help, but I would also like to know if this is a bug or if other people have the same problem. I do everything by synaptic: why should my system suddenly break?

It might be significant, but after the installation symlinks are created 

The file mplayerplug-in-wmp.xpt in the directory 
/usr/lib/firefox/plugins links to:
/usr/lib/firefox/plugins/mplayerplug-in-wmp.xpt

And there are 11 such apparently self-linking files in the same directory. These disappear when I uninstall mplayer plugin, and reappear when I install it again. Nautilus reports them as 
Type: Link (broken)

Why is apt-get installing broken links?

---

### Post by janbockaert on 2006-10-25
i am having the same problem. I believed it was because i added tuxfamily.org to my sources.list for installing flash 9 (stupid i know). It is annoying, but tomorrow i will upgrade to edgy, and in gnome 2.16 the mplayer plug-in is supposed to be working excellent. [http://www.gnome.org/start/2.16/notes/C/rnfeatures.html](http://www.gnome.org/start/2.16/notes/C/rnfeatures.html)

:D

---

### Post by janbockaert on 2006-10-25
oh, for the moment i am using the kaffeine starter plugin. That is not as neat as mplayer, but it is working

---

### Post by Bloch on 2006-10-25
aah, I too put in that line in sources.list to install flash 9. Why do you reckon that was stupid??

I will delete that line and update my system, but somehow I think I might have to do something more to get mplayer working.

I have no plans to update to Edgy.

Are the developers aware of this bug?

---

### Post by janbockaert on 2006-10-25
All i had to do to install flash 9, is unzip the .tar from adobe, and put the plugin in firefox/plugins folder :( no need to ad a repositorie and install a deb.

ok, i solved the problem.

go to synaptic. choose settings>packet-sources (or whatever it is called in english) and uncheck the tuxfamily repositories. Then reload synaptic.

now search for mplayer and uninstall it. in my case, synaptic asked me to uninstall a lot of other files also. Do so.

When mplayer is uninstalled, search for it again, and install mplayer-custom and mplayer-mozilla. restart firefox, and in my case, mplayer was back :)

---

### Post by Bloch on 2006-10-25
Thanks you for the help. 
That worked fine.

Correction: it works on only a few of the many clips at boreme.com, and fails to work at some clips which I remember viewing several weeks ago when I had the mplayer plugin before (installed by automatix that time)
It's not very usable when it takes several minutes to load up to 99% and then stops.

Just one thing that might be significant: synaptic reported that it couild not install mplayer-custom it said:
unresolvable dependancies
depends: mplayer

Well I installed mplayer and mozilla-mplayer, and custom-mplayer still reported the same error message.
But mplayer plugin worked to some extent anyway

---

### Post by janbockaert on 2006-10-25
trie installing mplayer again with automatix. Maybe it did not worked the first time because you had a newer version of mplayer on your system? 

I guess i have some different repositories installed in synaptic. I build my sources.list with the excellent source-o-matic (here: [http://www.ubuntulinux.nl/source-o-matic)](http://www.ubuntulinux.nl/source-o-matic)). So far i haven't met one file i can't play anymore.

well, glad i could help you (a little)

---

