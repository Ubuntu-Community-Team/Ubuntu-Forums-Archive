---
title: "Why compiz in intrepid is slower than on hardy?"
date: 2009-03-05
forum: Multimedia Software
---

### Post by syms on 2009-03-05
im using ati open source driver. i have ati radeon 9600 pro its old but compiz should work fine. in hardy compiz worked perfectly, now in intrepid i see that its slower, glide 1 animation lags, but in hardy everything was fine. i think that problem is related with xorg 7.4, anyone know a solution?
thanks

---

### Post by wolfen69 on 2009-03-05
> **syms said:**
> anyone know a solution?
thanks

yeah, get an nvidia card. ati is notoriously bad at handling 3D in linux. just because it once worked means nothing. anyone who has used both ati and nvidia will tell you the same thing.

---

### Post by Skripka on 2009-03-05
> **wolfen69 said:**
> yeah, get an nvidia card. ati is notoriously bad at handling 3D in linux. just because it once worked means nothing. anyone who has used both ati and nvidia will tell you the same thing.

Also there is a known progression of Ubuntu getting slower and slower in general as the version numbers go higher.

---

### Post by wolfen69 on 2009-03-05
> **Skripka said:**
> Also there is a known progression of Ubuntu getting slower and slower in general as the version numbers go higher.

alot of that has to do with people's computers getting older and older. alot of people are clinging to 7-8 year old computers, thinking that a modern linux distro will continue to run good forever. people with more recent hardware won't experience these issues.

---

### Post by Skripka on 2009-03-05
> **wolfen69 said:**
> alot of that has to do with people's computers getting older and older. alot of people are clinging to 7-8 year old computers, thinking that a modern linux distro will continue to run good forever. people with more recent hardware won't experience these issues.

IIRC, Phoronix did tests with clean installs of Gutsy, Hardy, and Intrepid all on the same (recent) hardware...and the progression was there....don't have a linky immediately handy.

---

### Post by Seq on 2009-03-05
> **wolfen69 said:**
> yeah, get an nvidia card. ati is notoriously bad at handling 3D in linux. just because it once worked means nothing. anyone who has used both ati and nvidia will tell you the same thing.

I assumed since he is using the open source radeon driver (and is aware of the issue such as to make a note of it) he had a reason for not using the binary catalyst driver (which does support his card). So sticking with open source, nv does not do 3D, and nouveau likely won't give very good performance (if compiz runs on it at all. I have not tried).

If he were willing to switch to a binary driver, I'd say to try the catalyst driver before purchasing an nvidia card.

---

### Post by Seq on 2009-03-05
> **Skripka said:**
> IIRC, Phoronix did tests with clean installs of Gutsy, Hardy, and Intrepid all on the same (recent) hardware...and the progression was there....don't have a linky immediately handy. IIRC, Phoronix also compared to Fedora and found Ubuntu has comparable performance to the related release of Fedora. It's not an Ubuntu issue specifically, just the effect of the parts used at the moment.

---

### Post by Simian Man on 2009-03-05
> **Skripka said:**
> IIRC, Phoronix did tests with clean installs of Gutsy, Hardy, and Intrepid all on the same (recent) hardware...and the progression was there....don't have a linky immediately handy.

Yeah stupid developers adding new features and stuff.  They should leave everything the same in all releases!

---

### Post by Skripka on 2009-03-05
> **Simian Man said:**
> Yeah stupid developers adding new features and stuff.  They should leave everything the same in all releases!

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1)

I'm not talking features.  I'm talking performance.  Why should new "features", slow down the same video or audio encoding task?  Hmmmm?

Why should Intrepid be twice as slow as Feisty at making an MP3 of the same bitratefrom the same WAV file?  What do new features have to do with this task?

---

### Post by Simian Man on 2009-03-05
> **Skripka said:**
> [http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1)

I'm not talking features.  I'm talking performance.  Why should new "features", slow down the same video or audio encoding task?  Hmmmm?

Why should Intrepid be twice as slow as Feisty at making an MP3 of the same bitratefrom the same WAV file?  What do new features have to do with this task?

I wasn't talking just about the features that distributions and desktops add, but also new kernel features.  For distros to work with as much hardware as possible, they include the latest kernel with all the new features and device drivers.  That adds a little bit of bloat and will affect every task on your machine, whether it uses the new stuff or not.  

If playing OpenArena with one extra FPS is important to you, stick with an older version.  I don't really buy their benchmark of music encoding, that is just too big a difference, they must have made a mistake.

---

### Post by Skripka on 2009-03-05
> **Simian Man said:**
> 

If playing OpenArena with one extra FPS is important to you, stick with an older version.  I don't really buy their benchmark of music encoding, that is just too big a difference, they must have made a mistake.

Playing games isn't.  It is the other performance drops that bother me.  I don't keep a *buntu install around and I never bothered to run their Phoronix suite when I did.

Either way-their data backs the OPs observations.  And what many people have griped about over the long term.

---

### Post by syms on 2009-03-14
The performance with fglrx in intrepid is much worse than in hardy too.
I agree with Skripka, some people dont know what they say, they say newer kernel needs better computer but they cant say what new feature requires better machine, and saying that better hardware support requires better computer is quite stupid

---

