---
title: "Problem adding GPG key for medibuntu repos..."
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by rainwalker on 2007-10-21
I was trying to upgrade to Gutsy yesterday and in the process messed with my software sources a bit and I think I need to re-add the GPG key for the medibuntu repos ([http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624))
However, when I run ```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
```
I get this:> gpg: no valid OpenPGP data found.

What's going on here?

---

### Post by Mark Bowers on 2007-10-21
I think the problem is with Medibuntu ie the non-free repositories for Feisty are down. I have the same problem you are having. I went to Medibuntu and followed their instructions for requesting repository availability. Their instructions are to use this command from the terminal.

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

The response is posted to the file location noted in the command. When I do this, their response in the medibuntu.list file is as below:

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

I'm still pretty much a noob - been using Feisty for about 6 months, but I interpret the response from Medibuntu above to be telling me that the non-free repository for Feisty is not available.

I was searching the forum to see if anyone had confirmed that Medibuntu was down when I found your post.

M. Bowers

---

### Post by rainwalker on 2007-10-21
Hm...so what are you saying? I'm confused

---

### Post by rainwalker on 2007-10-21
If it helps, the reason I'm trying to add the GPG key is because I get this error while trying to upgrade to Gutsy:> Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

---

### Post by Mark Bowers on 2007-10-21
Sorry about that - I was making it too complicated. The problem is simple - Medibuntu changed their repository address and I didn't catch it the first time I ran their instructions; AND they've combined the free and non-free repositories (I think).

Change your sources.list to read the following for Medibuntu:

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free


Delete or use # to get rid of the old Medibuntu address. Then get a new key and run an update.

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Mine now works fine.

Hope this helps.

M. Bowers

---

### Post by froy02 on 2007-10-21
Thanks for the info.  I had the same problem and that solved it.

---

### Post by rainwalker on 2007-10-21
Why do I leave that second line commented?

---

### Post by Mark Bowers on 2007-10-21
I'm enough of a noob yet I'll have to answer "I'm not sure". I tried to uncomment it, get the key, and run a 'sudo apt-get update" but ran into error messages. When I left the last lline commented, then ran the update and got the key; everything works and I've installed the codecs I was looking for without a hitch.

As I said earlier, I think they've combined the free and non-free repositories and made other changes on the Medibuntu end - likely as part of the release of Gutsy.

Incidentally, I have an IBM T60p that runs great under Feisty, but there's all kinds of problems with Gutsy, which is why I'm reinstalling 7.04. Do I need to post my problems as a 'bug report'? How does this work with a new release? I've only been using Ubuntu since a month or so after Feisty was released so I've never been through this before.

Any suggestions are appreciated.

---

### Post by rainwalker on 2007-10-22
Yep! That all worked for me
Now I've just got to get the kinks ironed out of this Gutsy install...

---

