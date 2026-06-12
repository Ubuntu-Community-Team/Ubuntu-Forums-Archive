---
title: "What happened to Plymouth today?"
date: 2011-02-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-02-12
Does anyone else have issues with new Plymouth in Natty repos?
I have tried both new versions of today:
- 0.8.2-2ubuntu15
- 0.8.2-2ubuntu16.

The thing is I don't anymore see the whole bugger anymore, it's gone.

However, after downgrading to the version 0.8.2-2ubuntu14, the good old Plymouth is back.
I have nvidia-current_270.18 and xserver 1.9.2 installed, otherwise all up to date.

---

### Post by mc4man on 2011-02-12
See the same on 1 install, pretty much the same only using natty nvidia-current instead. On shutdown there is some text presented, goes by too fast though did catch 'plymouth ...' at the top.

On a fully updated nouveau 3d install plymouth still shows as before, boot up & shutdown

---

### Post by tjeremiah on 2011-02-12
I get a black screen on boot up. I guess it will reappear again in future updates.

---

### Post by Harry33 on 2011-02-13
> **mc4man said:**
> See the same on 1 install, pretty much the same only using natty nvidia-current instead. On shutdown there is some text presented, goes by too fast though did catch 'plymouth ...' at the top.

On a fully updated nouveau 3d install plymouth still shows as before, boot up & shutdown

Yes I figured this one.
One more joke for the nvidia-current people.

---

### Post by Harry33 on 2011-02-13
Here is the bug report on this:
Bug #718044
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/718044](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/718044)

---

### Post by plun on 2011-02-13
Yep, and I confirmed this "joke"......

---

### Post by Harry33 on 2011-02-13
> **plun said:**
> Yep, and I confirmed this "joke"......

Thanks Plun.
Yeah I called this a joke, because this bug seems to be pretty harmless, not actually even annoying one.

---

### Post by Quackers on 2011-02-13
Yep, Plymouth has done a runner for me too. Just black screen for a while, then the desktop. I'm using nvidia-current too.
Will "me too" bug.

---

### Post by coffeecat on 2011-02-13
Probably not to do with nvidia. [I first saw this yesterday]("http://ubuntuforums.org/showpost.php?p=10452870&postcount=9") with ATI graphics + open source driver.

---

### Post by PaulW2U on 2011-02-13
> **coffeecat said:**
> Probably not to do with nvidia. [I first saw this yesterday]("http://ubuntuforums.org/showpost.php?p=10452870&postcount=9") with ATI graphics + open source driver.
I think I need to add a "me too" here. :)

---

### Post by Quackers on 2011-02-13
yabbadabbadooooo  :-)

---

### Post by Harry33 on 2011-02-14
This bug is fixed with this:
plymouth_0.8.2-2ubuntu17

---

### Post by coffeecat on 2011-02-14
> **Harry33 said:**
> This bug is fixed with this:
plymouth_0.8.2-2ubuntu17

Yup. Fixed. It's good to see Plymouth again. All 3½ seconds of it! :)

---

### Post by Quackers on 2011-02-14
Yep, for me too, but 7 seconds of it :-)

---

### Post by nm_geo on 2011-02-14
The update to 17 fixed mine here.

---

