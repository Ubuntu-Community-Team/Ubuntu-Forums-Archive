---
title: "eMusic Download Manager emusicdlm won't start on Ubuntu 10.04"
date: 2010-05-18
forum: Multimedia Software
---

### Post by gotgenes on 2010-05-18
I can't get the [eMusic Download Manager]("http://www.emusic.com/dlm/download.html") (emusicdlm) to start up in a fresh install on Lucid even though it worked fine in Karmic. It doesn't even give a helpful error message, it just says 
```

$ ./emusicdlm 
bash: ./emusicdlm: No such file or directory
```

Even using the absolute path to the executable just gives the same error.

I checked permissions and they are correct:
```

$ ll emusicdlm 
-rwxr-xr-x 1 chris chris 28864 2010-01-20 11:53 emusicdlm
```

Are there any other eMusic members who have tried using the download software to get their tracks in Lucid?

---

### Post by sgosnell on 2010-05-18
I keep meaning to resuscribe, to see what's new there, but I haven't gotten a round tuit.  I wasn't even aware that they had a Linux app.  I might give it a try and see if I can get a quick free download to try, just to see if it works.

Update:  I downloaded and installed the tarball, and it runs fine for me.  It extracted to /home/username/emusicdlm, and changing to that directory and running ./emusicdlm works.  It also works by double-clicking on the executable in Nautilus.  Are you sure you're in the correct directory?  It appears from your post that you're running it from your home directory, not a subdirectory.  That might be correct if you extracted it to home, but you might try checking to see if it's in a subdirectory.

---

### Post by gotgenes on 2010-05-25
@sgosnell are you using 32-bit Ubuntu 10.04, by chance? I'm using 64-bit. I'm wondering if this has something to do with it, although it did work in 9.10 64-bit.

As for the location of the download, I extracted it to a subdirectory of my home directory, cd'd into that directory, then executed the command above. Also, as I mentioned in the original post, even using the absolute path to the executable won't run it, and gives that error of being not found.

---

### Post by gotgenes on 2010-05-25
> **gotgenes said:**
> @sgosnell are you using 32-bit Ubuntu 10.04, by chance? I'm using 64-bit. I'm wondering if this has something to do with it, although it did work in 9.10 64-bit.

It *was* a 64-bit issue. To solve this problem, I installed the ia32-libs package:

```
sudo aptitude install ia32-libs
```

Back in business!

---

