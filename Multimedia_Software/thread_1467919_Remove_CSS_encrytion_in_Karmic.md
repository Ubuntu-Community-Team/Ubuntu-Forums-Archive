---
title: "Remove CSS encrytion in Karmic"
date: 2010-05-01
forum: Multimedia Software
---

### Post by Dyffo on 2010-05-01
When I was with Windows I used DVD Decrypter to remove CSS encryption - is there a porgramme for Ubuntu that will do this. I am not doing anything dodgy here !! - my daughter has bought a couple of DVD's  from the states, I want to copy these to run on my Player at home.

---

### Post by ron999 on 2010-05-01
Hi
Make sure that libdvdcss is installed.
The information is here:-[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
Then use a program such as k9copy. Information here:-[http://k9copy.sourceforge.net/]("http://k9copy.sourceforge.net/")

---

### Post by Dyffo on 2010-05-01
> **ron999 said:**
> Hi
Make sure that libdvdcss is installed.
The information is here:-[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")
Then use a program such as k9copy. Information here:-[http://k9copy.sourceforge.net/]("http://k9copy.sourceforge.net/")

mike@mike-desktop:~$ sudo apt-get install libdvdcss 
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate
mike@mike-desktop:~$ 

Any ideas on this one ???:confused:

---

### Post by ron999 on 2010-05-01
> Any ideas on this one ???

> **ron999 said:**
> 
Make sure that libdvdcss is installed.
The information is here:-[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")


....

---

### Post by Dyffo on 2010-05-01
Hi and THANKS - problem solved - my stupidity for not reading the full post.As soon as I went to the thread you suggested , then installed K9 Copy, whoosh we are up and running. Many thanks.

---

