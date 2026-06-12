---
title: "Zeitgeist-daemon: high memory usage"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nicocarbone on 2011-04-02
I am using Ubuntu 11.04 Natty Narwhal 64bits. Everything is running fine, but I have a unusually high memory usage, over 700mb at the beginning of the session with no open apps. 

I think that the guilty process is zeitgeist-daemon which uses more than 170mb at the start of the session (see the attached screenshot). 

Is anyone experiencing the same thing? Is this a bug or it is supposed to use this amount of memory?

Thanks you,

[IMG]http://i.imgur.com/bGgof.png[/IMG]

---

### Post by MacUntu on 2011-04-02
Mine uses 13 MiB, but maybe I don't use relevant services that much.

Edit: 18 MiB on a second machine. Both up-to-date, one is a Beta 1 install.

---

### Post by thiebaude on 2011-04-02
Yes, exactly the same here on the high ram usage, I had compiz showing 111 mb,so i swithced back to gnome-classic in 11.04 with no nvidia drivers installed, just the ubuntu default drivers, and now memory use is normal.I really don't use compiz anyway :)

---

### Post by thiebaude on 2011-04-02
I just noticed, look at all the memory that the different chrome processes is using.

---

### Post by nicocarbone on 2011-04-02
True, but that is Chrome with multiple tabs open, and it always used a lot of memory.

On the other hand, Zeitgeist didn't use this amount of memory in Maverick, and it seems a bit large for what it does.

For comparison, this is an screenshot at session startup: 

[IMG]http://i.imgur.com/LTjJG.png[/IMG]

---

### Post by cariboo on 2011-04-02
Zeitgeist Daemon uses 11.6Mb here, and I just used search to start System Monitor. On my system zeitgeist-datah is a zombie.

---

### Post by MacUntu on 2011-04-02
> **cariboo907 said:**
> On my system zeitgeist-datah is a zombie.
There should be a second instance, though. For the zombie thing, see [https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/739780](https://bugs.launchpad.net/ubuntu/+source/zeitgeist/+bug/739780)

---

### Post by cariboo on 2011-04-02
I do have zeitgeist-datahub

---

### Post by seiflotfy on 2011-04-02
> **nicocarbone said:**
> I am using Ubuntu 11.04 Natty Narwhal 64bits. Everything is running fine, but I have a unusually high memory usage, over 700mb at the beginning of the session with no open apps. 

I think that the guilty process is zeitgeist-daemon which uses more than 170mb at the start of the session (see the attached screenshot). 

Is anyone experiencing the same thing? Is this a bug or it is supposed to use this amount of memory?

Thanks you,

[IMG]http://i.imgur.com/bGgof.png[/IMG]
Hey guys this is a 64 bit bug we are fixing and that is related to the zeitgeist-fts-extension (which is needed by unity)
Also the zombie issues is being fixed. A 0.8 release is coming soon (2 weeks) and will have those issues fixed. Sorry for any trouble caused.
My Zeitgeist uses 16.1 MB (I have tones of extensions and stuff). Hopefully we can get it under 10 MB on all systems by 11.10. But with the 0.8 release you will experience an average of 15 MB.

---

### Post by nicocarbone on 2011-04-02
> **seiflotfy said:**
> Hey guys this is a 64 bit bug we are fixing and that is related to the zeitgeist-fts-extension (which is needed by unity)
Also the zombie issues is being fixed. A 0.8 release is coming soon (2 weeks) and will have those issues fixed. Sorry for any trouble caused.
My Zeitgeist uses 16.1 MB (I have tones of extensions and stuff). Hopefully we can get it under 10 MB on all systems by 11.10. But with the 0.8 release you will experience an average of 15 MB.

It is great to know that this is a known bug and it is been worked on. Looking forward to 0.8 release.

Could you please post the link to the launchpad bug page for this one?

By the way, great work with Zeitgeist and Ubuntu in general!

---

### Post by seiflotfy on 2011-04-03
> **nicocarbone said:**
> It is great to know that this is a known bug and it is been worked on. Looking forward to 0.8 release.

Could you please post the link to the launchpad bug page for this one?

By the way, great work with Zeitgeist and Ubuntu in general!
for the zombie process look at [https://bugs.launchpad.net/zeitgeist/+bug/739780](https://bugs.launchpad.net/zeitgeist/+bug/739780)

for the high memory look at
[https://bugs.launchpad.net/zeitgeist-extensions](https://bugs.launchpad.net/zeitgeist-extensions)

---

### Post by nicocarbone on 2011-04-03
Today I installed Natty 64 bits in another PC (actually, I updated Maverick to Natty) and the Zeitgeist-daemon memory problem is not present, it uses around 15mb at startup. Why the difference? Does this bug behave like this?

---

