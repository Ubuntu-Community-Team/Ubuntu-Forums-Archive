---
title: "Problems with codecs on Edgy Eft"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by s1k3st on 2006-10-27
For some reason when I try to "sudo apt-get install w32codecs" I'm told 

"Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

I have updated my sources list so... what could be the problem?

---

### Post by Kateikyoushi on 2006-10-27
Do you use the universe, multiverse repository  ?
In synaptic check settings >> repositories.
This link might help as well. [LINK]("https://help.ubuntu.com/community/RestrictedFormats#head-fb5aea408a5e1bcc63400bda9300800bc65b272a")

---

### Post by n00b0id on 2006-10-27
> **s1k3st said:**
> For some reason when I try to "sudo apt-get install w32codecs" I'm told 

"Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"

I have updated my sources list so... what could be the problem?

Its because the 3rd party PFL repositories have been shut down, see my thread on this forum: [http://ubuntuforums.org/showthread.php?t=285833](http://ubuntuforums.org/showthread.php?t=285833)

I am investingating, and looks like debian-multimedia.org might be a solution...

---

### Post by n00b0id on 2006-10-27
> This link might help as well. [LINK]("https://help.ubuntu.com/community/RestrictedFormats#head-fb5aea408a5e1bcc63400bda9300800bc65b272a")
Yes, that works!

I read this also, and managed to get all necessary repos in the sources.list
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by s1k3st on 2006-10-27
Thanks guys I got the codecs installed.  Does anyone know if/when the servers will be back up?

---

### Post by n00b0id on 2006-10-27
Well if you read that PLF info, its been shut down unless they get volunteers to run the servers.

But it seems that if you add multiverse and universe in your sources plf isnt needed (?) see the ubuntu help on repos [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

