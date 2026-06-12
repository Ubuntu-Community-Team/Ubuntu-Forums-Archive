---
title: "k3b ok before, now, won't burn anything!"
date: 2010-08-26
forum: Multimedia Software
---

### Post by AlexanderDGreat on 2010-08-26
I don't really know where to begin, but I was using k3b to burn dvds, cds, only a month ago, EVERY WEEK, but now, it's NOT working anymore!

Where did I go wrong?

Here are some info about me:

1. Each time I burn a cd, during 15-30% it stops and has this error

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/writing_error.png[/IMG]

2. When I run k3bsetup, nothing seems to be the problem:

[IMG]http://i365.photobucket.com/albums/oo91/whatupdawg_photos/k3bsetup.png[/IMG]

3. I've also tried running k3b as root.

4. I've also tried to use Nero Linux 4 but that one also fails.

Some other info about me:

art@lgv-server:~$ id
uid=1000(art) gid=1000(art) groups=4(adm),7(lp),20(dialout),24(cdrom),46(plugdev),105(lpadmin),119(admin),122(sambashare),124(vboxusers),1000(art)

art@lgv-server:~$ ls /dev/cdrom -l
lrwxrwxrwx 1 root root 3 2010-08-27 00:50 /dev/cdrom -> sr0


Please help, as I don't know what's wrong. Thanks for reading.

---

### Post by AlexanderDGreat on 2010-08-26
I'm really starting to feel the helplessness, as I've seen other posts in Google, that no one has been able to resolve this.

Are we left for dead burning in Ubuntu? What a shame!

---

### Post by AlexanderDGreat on 2010-08-26
Turns out I'm the shamed one, my brand new Sony DVD burner is made from China.

I changed hardware with Lite-On (is it actually better?) and I was able to burn with k3b again, no changing of permissions and stuff, as others suggested.

It's a hardware problem. Whew! I was about to cry.

---

