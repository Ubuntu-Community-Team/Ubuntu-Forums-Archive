---
title: "I'm getting paranoid"
date: 2008-05-22
forum: Multimedia Software
---

### Post by exbootie on 2008-05-22
Just done a new Install of hardy on my laptop.Is there a conspiracy to keep users from installing the medibuntu repo's . I have tried the latest "stickey" and various other wiki's and every time it will fail whilst importing the gpg key .This makes Synaptic unuseable and requires a complete re-install I getting a bit peeved and am thinking of going back to ubuntu 7.04 where I had multimedia working perfectly including libdvdcss and lame. anyone got any ideas for me ??. :confused:

---

### Post by .nedberg on 2008-05-22
It worked fine for me on 5 installs. Remember that they have changed the way to add the repositories since feisty.

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

From [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by cor2y on 2008-05-22
the gpg key works its just sometimes it times out is all.
keep trying

---

### Post by exbootie on 2008-05-22
thanks to you both.I will persevere for a while before I hang myself

---

### Post by exbootie on 2008-05-22
In case you check back on this post .thanks again, all sorted on fourth try

---

