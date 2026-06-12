---
title: "vlc update issue"
date: 2010-01-13
forum: Multimedia Software
---

### Post by 3l3vans on 2010-01-13
i am using gnewsense 2.3 which is pretty much ubuntu jaunty as i understand it.

last night my updates available icon popped up and i proceeded to update

the update was for a package called vlc-nox

BUT when i ran the update i got this error

dpkg: parse error, in file `/var/lib/dpkg/status' near line 14967 package `vlc-nox':
`Conflicts' field, reference to `vlc-plugin-lirc': version contains `)'

if i try to update with apt-get or aptitude i get the same error.

if i try to remove the package vlc with apt-get,aptitude, or synaptic i get the same error

i tried to reconfigure vlc with dpkg and got the same error

kinda scary

has anyone else had this problem?

any ideas?


EDIT BY AUTHOR:

My /var/lib/dpkg/status file had somehow become corrupted. The error tells me that near line 14967 there's an error. so i go there an i find some crazy looking square characters where the version number should be for package vlc-plugin-lirc. so i make a backup of he file, and then replace the corrupted characters with the proper version number. i had to make an educated guess, based on the version numbers of most of the other packages. save the file and run apt-get reinstall and abracadabra it works!

i think the corrupted characters were confusing dpkg which is why it was telling me i needed an update, and apt-get was confused by them as well, which is why i couldn't reinstall. just thought i'd post this in case anyone else runs into this problem. not sure what category it should go in. i'll let the admins decide.

---

