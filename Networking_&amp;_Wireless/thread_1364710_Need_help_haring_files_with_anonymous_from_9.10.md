---
title: "Need help haring files with anonymous from 9.10"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by schwim on 2009-12-26
hi there everyone,

I have found that many things in linux and most notably Ubuntu no longer require the long and arduous processes of old to get certain things working.  I've followed some of the old tutorials full of cryptic terminal commands and edited config files only to be told later that you simply right-click a box and choose something, hence my question:

What's the easiest way to set up a network share in 9.10 that can be used without a password across a network with both Windows and linux computers?

I've currently got all of my shares on a Windows XP machine, but I'm contemplating moving the files to one of my work machines so I can have one less computer running all the time.

Sorry for the broad question, but all my Googles ended in the Ubu 7 era.  I didn't want to make it harder than it needed to be in case things have been simplified.

thanks,
json

---

### Post by Iowan on 2009-12-26
I still prefer the "good ol' days" with the finer control provided by config files - ain't it nice to have the choice?  Nautilus has a sharing option (stores it's files in a different place). Some GUI options mentioned [here.]("http://ubuntuforums.org/showpost.php?p=8466082&postcount=6")

---

### Post by ELGL on 2009-12-26
I think it's a good idea to know how to configure samba with text files if you consider moving all your file shares there. When something goes wrong, you will be able to troubleshoot it if you understand it. When it's done just with gui tools (which write the config for you) without understanding the actual configuration file you'll have a hard time in the case something happens to the shares. It's rare that something like that happens.. but it's good to understand what you're doing anyway.

It's not that hard, I've just written a post to explain how to set up basic file sharing.

[http://ubuntuforums.org/showthread.php?p=8561354#post8561354](http://ubuntuforums.org/showthread.php?p=8561354#post8561354)

If you add 'guest ok = yes' under [share] that should be it.

---

