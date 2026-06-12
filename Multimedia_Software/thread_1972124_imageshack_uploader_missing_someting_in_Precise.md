---
title: "imageshack uploader missing someting in Precise?"
date: 2012-05-03
forum: Multimedia Software
---

### Post by shantiq on 2012-05-03
[ATTACH]217182[/ATTACH]

getting this on precise when it worked/works a dream on 11.10

Anything i need to do?

---

### Post by shantiq on 2012-05-03
any idea?   anyone got it going on Precise?   it is in the repos

---

### Post by kostkon on 2012-05-03
Is your 12.04 a clean install?

Maybe the imageshack server was down at the time. Does this happen every time? Are you behind a proxy or have you setup one?

Hmm, [I can see that it depends on libqt4-network.]("http://packages.ubuntu.com/precise/imageshack-uploader") for its networking. Make sure that you have all these dependencies installed in your system; maybe something happened and you are missing one of these.

Also, try running it in the terminal and check for any error messages.

Hope that helps.

I've tested it and it works fine on 10.04 (installed using the deb package provided by imageshack, some time ago).

---

### Post by shantiq on 2012-05-04
thanx for intervention kostkon


libqt4-network needed updating [question mark in synaptic]    and did that    but no change still same popup


from cli    no message it opens but popup still there




i still have 11.10 in a partition and fine there


So my question remains    has anyone got it going on 12.04?

I sense it is something really simple but cannot see it yet:KS

---

### Post by shantiq on 2012-05-04
bump:KS    anyone has installed it?

---

### Post by ron999 on 2012-06-02
> **shantiq said:**
> 

So my question remains    has anyone got it going on 12.04?



And my answer is YES. ):P

I had this problem with Pangolin imageshack-uploader "Can't find server..."
It's a bug.:(
Look here ---> [http://code.google.com/p/imageshack-uploader/issues/detail?id=243]("http://code.google.com/p/imageshack-uploader/issues/detail?id=243")
Solution is to compile imageshack-uploader with patched code.
But it would not compile for me. It disagreed with FFmpeg.

So I took the easy way out.
I'm using imageshack-uploader from this ppa here ---> [https://launchpad.net/~dr3mro/+archive/personal/+index?batch=75]("https://launchpad.net/~dr3mro/+archive/personal/+index?batch=75")

It's working fine.;)

---

### Post by shantiq on 2012-06-02
Thanx Ron for that



the good Dr Osman's remedy cured it:KS

---

