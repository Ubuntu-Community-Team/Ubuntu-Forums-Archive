---
title: "Unison question"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by clegends on 2010-10-19
Hi folks, I'm using Unison to back up my netbook to my server over ssh. So far, it's working great. My question is about Unison's config files. I've done a lot of reading, and still can't make it work the way I want. Basically, I want to create a folder with symlinks in it of all the folders I want to backup, then get this synced with my server. Can anyone post an example from a config file below to help me do this? Thanks.

~Mitchell

---

### Post by mobilediesel on 2010-10-20
> **clegends said:**
> Hi folks, I'm using Unison to back up my netbook to my server over ssh. So far, it's working great. My question is about Unison's config files. I've done a lot of reading, and still can't make it work the way I want. Basically, I want to create a folder with symlinks in it of all the folders I want to backup, then get this synced with my server. Can anyone post an example from a config file below to help me do this? Thanks.

~Mitchell

You could try adding this to your config:
```
follow = Regex .*
```
and it should follow all symlinks rather than just copy the symlink itself.
Source: [http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html#symlinks](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html#symlinks)

---

