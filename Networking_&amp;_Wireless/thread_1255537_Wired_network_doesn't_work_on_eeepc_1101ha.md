---
title: "Wired network doesn't work on eeepc 1101ha"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by raminaghrobis on 2009-09-01
Hi all, I've just installed Xubuntu 9.04 on my eeepc 1101ha, and I can't get the wired network connection to work. I haven't tried the wireless yet.
When I plug the cable in, it doesn't do anything...

Any help welcome, thanks in advance.

---

### Post by chilimac02 on 2009-09-01
I am having the same problem. My wifi will not work either. I have posted a couple of times about it and no one has helped me. Keep me in the loop, I'd love to get mine working too.

---

### Post by raminaghrobis on 2009-09-02
What desktop are you running chilimac02?

Could it be a problem with the hardware drivers (since it's a new computer, maybe the drivers weren't on the installation cd), or else with ubuntu?

---

### Post by chilimac02 on 2009-09-02
I'm pretty sure you hit that one right on the nose. I've tried several flavors of the jaunty kernel, but have had no luck. 

I did find a post about installing updated drivers, but ironically you need a network connection to do it. IF I had a network connection, well I wouldn't need to do it.

---

### Post by asedas on 2009-09-02
unfortunaltelly I have eee pc 1101ha also... no wifi, no lan :/ also no 1366x768 resolution... ANY help appreciated...

---

### Post by raminaghrobis on 2009-09-02
Presumably if you knew which drivers you needed and where they're supposed to go you could do it manually couldn't you? Have you got the link?

---

### Post by bkratz on 2009-09-02
> **raminaghrobis said:**
> Hi all, I've just installed Xubuntu 9.04 on my eeepc 1101ha, and I can't get the wired network connection to work. I haven't tried the wireless yet.
When I plug the cable in, it doesn't do anything...

Any help welcome, thanks in advance.


first, I know nothing about the eeepc's--but, look at this thread and see if it helps you. It appears to be about a similar unit. you might want to try a search for the exact unit.

[http://ubuntuforums.org/showthread.php?t=1230045&highlight=eeepc](http://ubuntuforums.org/showthread.php?t=1230045&highlight=eeepc)


Good Luck

---

### Post by chilimac02 on 2009-09-03
the alpha 4 of the new karmic version works with wired ethernet...

---

### Post by raminaghrobis on 2009-09-03
What's the "alpha 4 of the new karmic version"?

---

### Post by raminaghrobis on 2009-09-03
Holy IT miracle! It really does work!

What about wireless, has anybody tried that?

---

### Post by asedas on 2009-09-04
to get all working see:

[http://forum.ubuntuusers.de/topic/ubuntu-auf-dem-eee-1101-ha/2/](http://forum.ubuntuusers.de/topic/ubuntu-auf-dem-eee-1101-ha/2/)

---

### Post by chilimac02 on 2009-09-07
look up (google) "enable jaunty backports" in Karmic (9.10). When I did that and updated, my wifi works.

Now I just need a working video driver for the gma 500 and I'm in bizness!

---

### Post by asedas on 2009-09-12
I got everything working on my 1101ha. see my post here: [http://ubuntuforums.org/showthread.php?t=1260275](http://ubuntuforums.org/showthread.php?t=1260275)

---

### Post by pumex1990 on 2009-10-14
Hi,
i've just installed 9.10 on my 1101ha
i used this version for some days a few weeks ago, and wireless lan was working out of the box. but today it's not (i just have wired network)
so i tried to install linux-backports-modules-karmic (in 9.04 i did this but with jaunty and it was working), but it says 'It didn't worked out to install some packeges. This may be because you damand an impossible situation or they were not yet transferred from folder 'Incoming' This informations may help you to solve this situation: following packages has missing dependencies: linux-backports-modules-karmic: recuireds linux-backports-modules-karmic-generic but it wont be installes. E: Packeges are broken (of course this is just my poor translation as I get this info in Polish)

chilimac02 wrote 'look up (google) "enable jaunty backports" in Karmic (9.10). When I did that and updated, my wifi works.', but I didn't find anything about that. Can you help me? :)

---

### Post by lokutus25 on 2009-10-14
> **asedas said:**
> to get all working see:

[http://forum.ubuntuusers.de/topic/ubuntu-auf-dem-eee-1101-ha/2/](http://forum.ubuntuusers.de/topic/ubuntu-auf-dem-eee-1101-ha/2/)

Thanks but it's in German...useless to me. But seems very interesting, is there any translation? I'm asking too much I Know and I'm sorry :):)

---

