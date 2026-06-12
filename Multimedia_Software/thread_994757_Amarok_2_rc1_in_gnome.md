---
title: "Amarok 2 rc1 in gnome"
date: 2008-11-27
forum: Multimedia Software
---

### Post by thestig_992 on 2008-11-27
having some trouble installing amarok in gnome.
I used the command "sudo apt-get install amarok-kde4", which is apparently for RC1. I added the repos also...

```
I get an error message saying 
The following packages have unmet dependencies:
  amarok-kde4: Depends: kdelibs5 (>= 4:4.1.3) but 4:4.1.2-0ubuntu11 is to be installed
 
```

I checked kdelibs5 in package manager, reinstalled it, but still cant get later than 4:4.1.2, even after updating repos

Kinda stuck as to what to do now...

---

### Post by Konj on 2008-11-27
What's the repo?

---

### Post by Ouguiya on 2008-11-27
Hi there!

Well I'll try to help, even though I am still quite a newbie and am not sure this will solve anything.

Thing is that I am still using Amarok 1.4, thus meaning that the version you are installing seems to be a bit off the book, so to speak, at least for gnome.

I checked to see, and found this: [http://packages.debian.org/experimental/kdelibs5](http://packages.debian.org/experimental/kdelibs5)

Here it indicates that this is an experimental package, and thus may be very unstable. I think this is the reason why it isn't in the "tested" repositories yet. What you may be able to do is either add the repository which has all the experimental stuff (though I really wouldn't know where or how to find that), or you could try compiling this from source, if this is possible.

As far as I have seen, it may be possible to download this package (from the link I provided), and install it. Since ubuntu is a debian derivate, I think this should work, but am really unsure about it myself. (To be honest, I, personally, wouldn't do it. I'm a bit too scared of experimental things anyway)

These are just some ideas, like I said, I am sadly not expierienced enough to give you any instructions as to how to proceed. I hope this helps somewhat.

Yours,

Ouguiya

---

### Post by thestig_992 on 2008-11-27
ty, i just didnt know that kdelibs5 was an experimental package

---

