---
title: "Config video card on Asus UL30VT-X1K in Natty 64bit"
date: 2011-06-09
forum: Multimedia Software
---

### Post by Sonja on 2011-06-09
When I go in Additional Drivers, it says I have NVIDIA driver activated but not in use. How do I fix that? There is no wizard, is there?

Did I install Java or graphics drivers incorrectly on natty 64bit? [http://pastie.org/2045976](http://pastie.org/2045976)

What should my xorg.conf be optimized as?

---

### Post by CryptSphinx on 2011-06-10
so many questions!

So minecraft eh?

first off - the "activated but not currently in use" is on my system as well but my drivers are fine - see here

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788")

if your using unity without issue and can watch video , odds are you have the above bug.

I suspect that the issue with minecraft is a java issue.
I would Check that ubuntu-restricted-extras and restricted-addons are installed and also which packages show up under java in synaptic as installed.


It may also be some issue with minecraft , what version are you running, has it worked before and what setup have you on the machine.

So basically:
what version of ubuntu
are video / 3d applications working
have you the most recent version of minecraft
has it run before
when does it crash.

---

