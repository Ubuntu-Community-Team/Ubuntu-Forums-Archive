---
title: "Freevo Question"
date: 2009-02-20
forum: Multimedia Software
---

### Post by zdunham on 2009-02-20
Hi. I just installed Xubuntu on a old machine I had lying around and I installed Freevo and all of its dependencies.

Then I did:

```

freevo config

```

I get this message:

"You are not part of the group 'freevo', you cannot exploit shared resources (such as the cache). Your data will be save in /home/myusername/.freevo
can't find helper config"

Any ideas on how to fix this would be greatly appreciated. It is probably something obvious and I am just a Linux idiot haha. Thanks in advance.

---

### Post by zdunham on 2009-02-21
OK I got the previous part all figured out by adding myself to the proper groups and setting the permissions accordingly.

I now have another problem when I try to launch Freevo I get this:

"Can't find all Python dependencies:
no module named utils."

I've searched everywhere and I can't figure out what I am missing.
I tried python-apport-utils and that it tells me is a sub-package of python-apport which I already have installed. Any ideas on this one?

---

### Post by mikeserv on 2009-02-22
Ok, I just did this today, too.  I'm using Xubuntu Intrepid.  Anyway, the problem is Freevo is expecting a python package that you probably have, but that has been moved to a new directory in the python site-packages because it's being phased out or something.

Anyway, first (in terminal) you need to make sure you have the missing package.  So do: "sudo apt-get install python-xml". Then go to /usr/lib/python2.5/site-packages and link the installed package directory with the name Freevo expects:

cd /usr/lib/python2.5/site-packages
sudo ln -s oldxml/_xmlplus/

And that should do it.

-Mike

---

### Post by zdunham on 2009-02-22
Thanks a lot, that worked perfectly!

---

### Post by can8dnSix on 2009-03-17
Wow.. Mike that is perfect and awesome. Thanks.
L

---

