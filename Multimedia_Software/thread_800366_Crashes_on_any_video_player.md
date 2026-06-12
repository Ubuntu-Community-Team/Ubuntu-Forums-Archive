---
title: "Crashes on any video player"
date: 2008-05-19
forum: Multimedia Software
---

### Post by ilmw on 2008-05-19
Hi all,

After installed Ubuntu Hardy (8.04), any video player will crash my Dell 700m: vlc, xine, totem, etc. The screen goes to black, no response on any keystroke. The only way to get back is to shutdown.

Does anyone has such problem? Thanks!

My pc:
Dell 700m (pretty old, I know. But everything else runs smoothly)
Ubuntu 8.04 Hardy
60GB hard drive
2GB Ram

---

### Post by warbread on 2008-05-20
What are you trying to play?  DVD?  .AVI?  

Try this from your Home directory:

```
:-$ vlc 2> vlcerror.file
```

If it crashes, reboot like normal and then open that file and post the contents here.  If it doesn't, congrats!

---

### Post by aerorahul on 2008-06-01
Here is the response I get:

signal 1 received, terminating vlc - do it again in case it gets stuck

X crashes and I believe it is because compiz crashes. After this, all I can do is reboot.

Any thoughts will be appreciated to get compiz working. I am using metacity for my purposes with no desktop effects :(

Thanks,
r.

---

### Post by Nirva on 2008-06-09
I have exactly the same error....

---

### Post by ilmw on 2008-06-19
> **warbread said:**
> What are you trying to play?  DVD?  .AVI?  

Try this from your Home directory:

```
:-$ vlc 2> vlcerror.file
```

If it crashes, reboot like normal and then open that file and post the contents here.  If it doesn't, congrats!
I just figured out xine crash reason:
Somehow xine did not normally exit, so $HOME/.xine/session.0 stayed in the folder. It won't crash if you delete this file before starting xine.

I believe it is same to vlc, but I haven't found the corresponding file.

HTH.

---

