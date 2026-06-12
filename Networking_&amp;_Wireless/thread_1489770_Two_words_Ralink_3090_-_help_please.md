---
title: "Two words: Ralink 3090 - help please"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by hammingen on 2010-05-21
Okay guys, sorry to ask this but I need some help with sorting the wireless out on my netbook. As you may know there aren't any packaged drivers for the Ralink 3090 in the Ubuntu package and my lack of Linux know how is really being a drag with sorting this problem out.

I'm pretty much a novice with sorting technical linux problems out and I don't know much when it comes to the terminal so if you can help me out simple terms please, no long words.

Thanks for any help you can offer me

---

### Post by chili555 on 2010-05-21
> there aren't any packaged drivers for the Ralink 3090 in the Ubuntu packageIt depends on your version. In Lucid, I see:```
$ locate rt3090sta
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt3090/rt3090sta.ko
/lib/modules/2.6.32-22-generic/kernel/drivers/staging/rt3090/rt3090sta.ko
```What version are you running?```
uname -r
```

---

