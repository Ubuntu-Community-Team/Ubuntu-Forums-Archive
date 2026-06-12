---
title: "[SOLVED] recommmend me a cd ripper (mp3)"
date: 2008-08-01
forum: Multimedia Software
---

### Post by wolfen69 on 2008-08-01
i do not want to have to try each one in the repos to find a good one. the default sound juicer will only rip to 256k (mp3) i believe. i'm looking for a ripper that will give me 320k. thanks.

---

### Post by vambo on 2008-08-01
Asunder will do that. In the repos.

---

### Post by wolfen69 on 2008-08-01
> **vambo said:**
> Asunder will do that. In the repos.

asunder is not in the repos. and yes, i have all repos enabled, plus medibuntu. i found it at getdeb.net. but it will only rip to 245k.

---

### Post by vambo on 2008-08-01
> **wolfen69 said:**
> asunder is not in the repos. and yes, i have all repos enabled, plus medibuntu. i found it at getdeb.net. but it will only rip to 245k.
My wrong - no it's not. I'm running 1.6 and that goes to 320k

---

### Post by wolfen69 on 2008-08-01
i tried 1.6 and it would only go to 245.

---

### Post by jtniehof on 2008-08-01
I use Grip (in universe) with lame (multiverse) as an encoding backend. Lame will do 320kbit.

---

### Post by vambo on 2008-08-01
> **wolfen69 said:**
> i tried 1.6 and it would only go to 245.
What version of lame is it pulling AFAIK, this is the backend

---

### Post by unoodles on 2008-08-01
I actually prefer the a full blown CD/DVD suite when dealing with my discs. So I use K3B, which is in the repo's. I am quite sure it can rip at 320 and higher.

---

### Post by wolfen69 on 2008-08-01
i have lame 3.97-0.0

---

### Post by wolfen69 on 2008-08-01
ok, i've ripped a cd with k3b. how can i check the bit rate of the mp3's?

edit: i found out how to get the bit rate. i'm going to close this thread as solved and start another one with a more appropriate title. thanks.

---

### Post by mc4man on 2008-08-01
if you want a very sophisticated and configurable ripper I'd use Rubyripper. 
For gutsy the getdeb is good, for hardy I'd build from source. If you build, a run thru ./configure will show what packages are missing in terms of functions and capabilities.
It will accept any valid parameters for the codec being used, a read thru <codec> --help or --longhelp is informative (ex. lame --longhelp).
A basic lame setting  would be -V n  (vbr, n=quality, 0=highest, 9=lowest)

After getting packages in order i configured as such
```
./configure --enable-lang-all --enable-gtk2 --enable-cli --prefix=/usr

```

Note: in hardy you must change the cdrom device in Rubyripper's preferences from a /dev link to a /dev device Ie. /dev/scd0 or dev/scd1 ect.
> 
how can i check the bit rate of the mp3's
r. click on mp3 -> properties ->  audio  , vbr will report as lowest used  i believe (or average)

---

