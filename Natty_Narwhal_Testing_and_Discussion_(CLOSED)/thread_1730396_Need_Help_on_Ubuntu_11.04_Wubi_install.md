---
title: "Need Help on Ubuntu 11.04 Wubi install"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ashickur.noor on 2011-04-16
I have download Ubuntu 11.04 Beta 2 and trying to install it by wubi. But when I run wubi it wants to download the iso again. Now what should I do.

Please Help me ASAP.

---

### Post by bcbc on 2011-04-16
Turn off internet access (wubi downloads the latest checksum, and in beta they change a lot - so this way it should use the one supplied with the beta2 iso). Make sure you are using the 11.04 wubi.exe (either on the disk you've burned or if you downloaded it from [here]("http://people.canonical.com/~evand/wubi/natty/wubi-r207.exe"))

Natty is in beta. You should post inquiries to the [Natty forum]("http://ubuntuforums.org/forumdisplay.php?f=394"). Do not use it on your 'production' computer. Make sure you have backups.

PS it might also fail if the checksum on your beta2 iso fails. Check the log file in the %temp% directory (wubi-11.04-rev207.log) for more info on the failure.

---

### Post by ashickur.noor on 2011-04-16
Thnx.

I finally get it. I was trying it from local hard drive. Once I mount the iso it works. But unfortunately it not starting install. this is my laptop problem. All Linux distro I tried is same problem, accept Ubuntu 10.04 and it's all variants.

---

### Post by Rubi1200 on 2011-04-16
Post the full specifications as well as make and model for the laptop please so we know what you are dealing with.

Thanks.

---

### Post by ashickur.noor on 2011-04-16
Ok I will post is letter. Now I am trying to install it  in my desktop.

---

### Post by dino99 on 2011-04-16
for a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

