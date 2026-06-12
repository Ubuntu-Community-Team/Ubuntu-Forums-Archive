---
title: "HowTo: Play DVD's in Kubuntu Feisty"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by kwilliam on 2007-04-04
I just installed Kubuntu Feisty Beta, and to my dismay, EasyUbuntu does not work at all.  I'm told Automatix isn't available for Feisty user's yet either.  So how do you get DVD's to play in Kaffeine?  After searching on kubuntuforums.net, I found [the answer]("http://kubuntuforums.net/forums/index.php?topic=3080415.msg57386#msg57386").  I figure a LOT of people will be asking the same question in just a few weeks when Feisty is officially released, so I thought I'd share, especially since a lot of beginners are not aware of [kubuntuforums.net]("http://kubuntuforums.net").

[SIZE="3"]What to do:[/SIZE]
Add the Medibuntu gpg key to your system's list of trusted APT keys.
```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```

Add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository.
```
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

Update the package list.
```
sudo apt-get update
```

And install the following packages.
[COLOR="Red"]Note:   These packages may be illegal in your country.[/COLOR] (for more detail, see [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/))
```
sudo apt-get install libxine-extracodecs w32codecs libdvdcss2
```

Note: It may also be necessary to install *libdvdread3*.  Because of the order I installed the packages, I don't know for sure.

Side note:  I don't know about you, but I can't wait for Click 'N' Run.  It should make things so much easier.

---

### Post by crispy_420 on 2007-04-05
I think Click 'N' Run may already be available and it does look good. But then again you will have to pay to get a licensed DVD player, which I believe is a old version on WinDVD.

---

