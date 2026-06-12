---
title: "Medibuntu"
date: 2013-10-22
forum: Multimedia Software
---

### Post by chideock on 2013-10-22
I guess Medibuntu is gone. How does one setup 12.04 to play dvds and run video files?

---

### Post by Bashing-om on 2013-10-22
chideock;Hi !

See this link for one discussion of this small issue.


[http://ubuntuforums.org/showthread.php?t=2174110&page=3&highlight=medibuntu](http://ubuntuforums.org/showthread.php?t=2174110&page=3&highlight=medibuntu)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by bapoumba on 2013-10-22
[http://gauvain.pocentek.net/node/61](http://gauvain.pocentek.net/node/61)

Please be aware I have not tried it yet.

Edit : also install the ubuntu-restricted-extras package, if you have not already done so (in the multiverse repo).

---

### Post by chideock on 2013-10-22
I have libdvdread4 installed on 12.04. I tried the command "sudo /usr/share/doc/libdvdread4/install-css.sh" it returns 'command not found'

---

### Post by bapoumba on 2013-10-22
[https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs](https://help.ubuntu.com/community/RestrictedFormats#Addlibdvdccs)
Have you installed the ubuntu-restricted-extras package (in multiverse) ?

---

### Post by chideock on 2013-10-23
bapoumba
when I installed a new download of 12.04 3 days ago I ticked the option to load restricted. The easy install on the page you gave me does not work. I tried the manual install it returns the statement "unable to locate the package ubuntu-restricted-extras". I ran the sudo for the "add libdvdcss and it returns "command not found".

Using 'synaptic package manager' I see that libdvdread4, libdvdnav4 & brasero are installed.

---

### Post by chideock on 2013-10-23
I finally figured out thru synaptic package manager that the ubuntu-restricked-extras package was not installed. Did that and did the process from the videolan site and then ran the command "sudo /usr/share/doc/libdvdread4/install-css.sh". It all seemed to install. Rebooted a couple of times afterward.

The dvd starts to play but is very jerky and then just stops altogether. I was using totem movie player.

---

### Post by mc4man on 2013-10-23
> **chideock said:**
> I have libdvdread4 installed on 12.04. I tried the command "sudo /usr/share/doc/libdvdread4/install-css.sh" it returns 'command not found'
It works fine here, could you try again by copying & pasting directly from code box below into a terminal

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

If it reports 'command not found' what does this do?
```
sudo apt-get update
```

---

### Post by chideock on 2013-10-23
mc4man
guess our posts crossed but I will try the update command maybe that will fix the jerky motion


no did not fix the jerky/stopped motion using the update

---

### Post by deadflowr on 2013-10-23
That sounds more like a hardware issue.
If the dvd is playing at all, then the libdvdcss(2?) package is working.

---

### Post by bapoumba on 2013-10-23
+1, please start another thread in the Multimedia and Video forum for ex, thanks.

---

### Post by chideock on 2013-10-23
Cant be hardware since running an avi file off the harddrive does the same jerky motion.

I will start another thread

Thanks for the help everyone.

---

### Post by deadflowr on 2013-10-23
Have you tried another media player, like VLC?

---

### Post by chideock on 2013-10-23
I tried XBMC - same thing

---

