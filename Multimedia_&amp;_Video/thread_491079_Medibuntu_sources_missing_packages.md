---
title: "Medibuntu sources: missing packages?"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by darkfox on 2007-07-03
I have added free and non-free Medibuntu sources for Feisty, but some packages listed on their website do not appear to be available. These include RealPlayer and Opera. Am I doing something wrong or is there a problem that I need to workaround?

My sources file looks like this:
```

## deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted #Added by software-properties
## official Ubuntu sources
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe multiverse
## Medibuntu - Ubuntu 7.04 "feisty fawn"
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
 
```

---

### Post by darkfox on 2007-07-03
I should add that I've asked the Medibuntu maintainers the same question and if I here anything back I'll be sure to add to this post, but they are busy guys so in the mean time if you can spot a mistake on my part I'd be grateful to know about it

---

### Post by darkfox on 2007-07-03
I have a reply from the Medibuntu chaps.  Apparently they withdrew things like RealPlayer and Opera from their repositories when the Canonical Commercial sources came online (although Canonical Commercial doesn't supply RealPlayer as far as I know).

I'm sure the Medibuntu gang will get around to updating their website one day ;)

---

### Post by Gremlinzzz on 2007-07-03
[https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29)
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
[https://help.ubuntu.com/community/Medibuntu?action=fullsearch&context=180&value=realplayer&titlesearch=Titles](https://help.ubuntu.com/community/Medibuntu?action=fullsearch&context=180&value=realplayer&titlesearch=Titles)
let me know if it works:D

---

### Post by Gremlinzzz on 2007-07-03
And or [http://www.real.com/linux](http://www.real.com/linux)
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)
Good night and Good Luck:D

---

### Post by darkfox on 2007-07-03
Thank you Gremlinzzz.  I did already have these packages installed.  If you re-read my original post you will see that I was not posting some kind of lazy install question, merely trying to work out what was in and what was out of Medibuntu's repositories as there seemed to be a difference between what they state on their website and what their repositories actually provide to a Feisty user.  I was wondering if I was using their repositories incorrectly as I am quite new to this, but as you'll see from my later posts there really is a discrepancy.

I am sorry you mistook me for a lazy idiot and hope that you have not wasted too much time on this.

---

