---
title: "No sound through headphones and unable to update alsa driver"
date: 2012-03-10
forum: Multimedia Software
---

### Post by nicolaneedshelp on 2012-03-10
Hello,
I'm hoping someone can help me, cause I have crawled through multiple different solutions and still haven't had any luck.
I have a Toshiba Satellite C650D laptop running Lucid Lynx 10.04 LTS.
After an update my sound started playing through both speakers and headphones when attached. After a more recent update, there is no longer any sound through my headphones.
I'm a laptop tech and I've tested the hardware with a image of Windows correct for this type of machine and haven't had any issues. I've checked the headphones and tried different ones without any success.
From what I've seen in the error messages I've gotten, my problem _seems_ to be that I can't update the alsa driver from what I have 1.0.23 to 1.0.24
When running command:
"sudo apt-get install linux-alsa-driver-modules-$(uname -r)"
I get error:
"E: Couldn't find package linux-alsa-driver-modules-2.6.32-39-generic"

I'm newish to Ubuntu, my ex-boyfriend was the one to get me on it, but I want to stay with it. Any help would be amazing, and I will get any addition information that's needed.

---

### Post by Chris Musampa on 2012-03-12
.

---

