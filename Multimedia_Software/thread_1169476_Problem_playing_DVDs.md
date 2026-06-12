---
title: "Problem playing DVDs"
date: 2009-05-25
forum: Multimedia Software
---

### Post by bawig1 on 2009-05-25
Hi,

I am having some problems playing DVDs on 9.04 using totem. The problem happened today. Everything was working fine and I was watching a DVD with Totem, then I placed another DVD in the drive and got an error message. I searched the forums and found some posts that advised to do the following:

```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

``````

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```and

```

sudo apt-get install ubuntu-restricted-extras debhelper fakeroot build-essential

```now when I run totem and try to watch a dvd it comes up with a blue menu on the screen and does nothing. (see screenshot)

Brett.

[IMG]http://img195.imageshack.us/img195/8283/screenshotm.png[/IMG]
[IMG]http://ubuntuforums.org/%5BURL=http://img195.imageshack.us/my.php?image=screenshotm.png%5D%5BIMG%5Dhttp://img195.imageshack.us/img195/8283/screenshotm.th.png%5B/IMG%5D%5B/URL%5D[/IMG]

---

### Post by Sewje on 2009-05-25
Try VLC, it seems to be the best player for DVD of any sort.

---

### Post by DLG102282 on 2009-05-25
I second that

---

### Post by tacantara on 2009-05-25
I agree that VLC is a better DVD player.  I also recommend Movie Player (Xine), as I found that it works quite well.  That's what I presently use.

---

### Post by bawig1 on 2009-05-25
thanks for the info, got everything working now. :popcorn:

---

