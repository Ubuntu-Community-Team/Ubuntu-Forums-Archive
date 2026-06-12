---
title: "Need help for firewire/raw1394 in kino, mainactor,cinelarra"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by dascraz on 2006-06-26
Hello,
 I cant capture with my video camera, in any video editing program. I know that my problem has been decuised before, and i try some of the things posted here, but still dosend work. 
 Any help??? 
 Thanks

---

### Post by dascraz on 2006-06-27
I get this ....


r~~@UbuntU:~$ sudo chmod 777 /dev/raw1394
Password:
chmod: cannot access `/dev/raw1394': No such file or directory
r~~@UbuntU:~$

---

### Post by dascraz on 2006-06-27
r~~@UbuntU:~$ ls -l /dev/raw1394
ls: /dev/raw1394: No such file or directory
r~~@UbuntU:~$ ls -l /dev/dv1394
ls: /dev/dv1394: No such file or directory
r~~@UbuntU:~$


Please, HELP me !

---

### Post by 4ebees on 2006-10-09
> **dascraz said:**
> r~~@UbuntU:~$ ls -l /dev/raw1394
ls: /dev/raw1394: No such file or directory
r~~@UbuntU:~$ ls -l /dev/dv1394
ls: /dev/dv1394: No such file or directory
r~~@UbuntU:~$


Please, HELP me !
Hi dascraz,

Did you get a solution to this problem or not?

Regards,

4ebees

---

### Post by wavesound on 2007-12-05
HI
I've used Kino for years without a problem.
Now on upgrading to 7.10 I get this error.
 I can run as sudo and I've added a video user group but still get the error.

It' s a shame but Video and sound seem to be less important on the newer systems now.
Developers shouldn't complain we leave our systems open and run as root, when we can't set our software correctly.

This problem seems to come up often.

Cheers
Bob

---

### Post by mozetti on 2007-12-05
Have you checked the /dev directory? Not using my ubuntu computer right now, but I seem to remember something having to do with /dev/raw1394-0 or something like that. Basically, a filename change. If /dev/raw1394 (or any variant similar to it) doesn't exist, why don't you just create it?
```
touch /dev/raw1394
```

---

### Post by wavesound on 2007-12-05
> **mozetti said:**
> Have you checked the /dev directory? Not using my ubuntu computer right now, but I seem to remember something having to do with /dev/raw1394-0 or something like that. Basically, a filename change. If /dev/raw1394 (or any variant similar to it) doesn't exist, why don't you just create it?
```
touch /dev/raw1394
```

Hi
Thanks for the very quick reply!
I have got it sorted by adding my user account to the raw1394, as from this forum.

I just cant export to mpeg and have tried to trans code to Theora to bypass mpeg.
I need to read up on this.

It's a shame kino can't output to Theora as it's open source.

Seems I need ffmpeg to use Kino export.

Cheers
Bob

---

### Post by jwalch on 2007-12-09
Same problem here, probably due to migration of raw1394 to a newer lib1394-0 that probably is better but doesn't really install and/or tell us what to do.

So, I found the old raw1394 in a hidden directory under /dev (.static/dev), created a link back into /dev  --and then my Kino was connected again. (The other sugegstions found in the Forums did not work for me.)

See id this solution works for you.

PS: this is all under ubuntu gusty, i386.

Jim

---

