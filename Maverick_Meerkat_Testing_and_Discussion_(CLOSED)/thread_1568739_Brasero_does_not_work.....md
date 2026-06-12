---
title: "Brasero does not work...."
date: 2010-09-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by exploder on 2010-09-05
I tried burning a DVD image with Brasero, it segfaults....

Here is the terminal output.

** (brasero:2427): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


(brasero:2427): GLib-CRITICAL **: g_variant_new_strv: assertion `length == 0 || strv != NULL' failed
Segmentation fault (core dumped)
don@don-desktop:~$ 

Anyone know if this bug has been reported? Gnomebaker works, so this has to be specif to Brasero.fine,

---

### Post by ranch hand on 2010-09-05
If you ran the updates for brasero that are being held back you do not have a working Brasero and won't until you install it, if it will install with out the updates we are supposed to be waiting for.

Works fine here but I do have 4 packages, 2 for Brasero held back.

---

### Post by exploder on 2010-09-05
Thanks! You nailed the problem. I should have waited, now I will have to wait for the other 2 packages to be updated. Oh well, at least I learned something and Gnomebaker will do the job in the meantime. Thanks again for the explanation, much appreciated.

---

### Post by ranch hand on 2010-09-05
Gnome Baker is a real handy little bugger.  I do not have it on here but I do on my 9.04 that I use at night (need a break from all this FUN).

---

### Post by VinDSL on 2010-09-05
I had this issue, the other day, too.

First of all, when I did an update (using Update Manager) it gave me a 'partial update' dialog box -- something about Brasero. 

So, instead...

I went into Synaptic and clicked 'Mark all upgrades'.  Brasero is the only one that was marked, and I upgraded it.

When I went back to Update Manager... no more 'partial update' dialog, and I continued with the regular updates.

Second part...

When I went to burn an ISO via Brasero, I noticed the missing 'logo.png' error. I guess 'they' forgot to put that file in the package...  :D

I fixed this by going into my 10.04 Lucid partition, and copying the '/usr/share/brasero/logo.png' file across to my 10.10 Maverick partition.

---

### Post by ronacc on 2010-09-05
K3b is another alternative , it drags in a bunch of KDE libs but runs just fine under gnome and at least for me works in situations where nothing else will .

---

### Post by VMC on 2010-09-05
> **ronacc said:**
> K3b is another alternative , it drags in a bunch of KDE libs but runs just fine under gnome and at least for me works in situations where nothing else will .
I much prefer K3B. If I need to work with dvd/cd's i will fire up my Kubuntu and K3B.

---

### Post by ronacc on 2010-09-05
no need to fire up Kubuntu , it runs fine under gnome at least as far as lucid , I haven't tried it with maverick yet , brassero hasn't given me any crap yet .

---

### Post by IanW on 2010-09-06
> **ronacc said:**
> no need to fire up Kubuntu , it runs fine under gnome at least as far as lucid , I haven't tried it with maverick yet , brassero hasn't given me any crap yet .

K3B works perfectly on gnome-flavored maverick.

---

### Post by ratcheer on 2010-09-06
Now, I have both Brasero and Rhythmbox on hold. Brasero had been on hold due to conflicts with Rhythmbox packages. I wonder what we are waiting for, now?

Tim

---

### Post by exploder on 2010-09-06
I started over and am now waiting for all of the packages to come in too. It's been a while since I have gone though a development cycle. :D

---

### Post by karmila on 2010-09-06
> **ratcheer said:**
> Now, I have both Brasero and Rhythmbox on hold. Brasero had been on hold due to conflicts with Rhythmbox packages. I wonder what we are waiting for, now?

Tim

I did the update and everything just fine. Yes, it removed a package... something like rythmbox-cdrecorder.

---

