---
title: "backing up dvds to .iso"
date: 2012-05-22
forum: Multimedia Software
---

### Post by w1ll1am on 2012-05-22
Hello I have been making a HTPC for about a month now and I have been backing up all of my dvds to .iso so I can play them in mythtv. I have run into a few issues and was wondering if anyone else has had this issue and can help. 

I am assuming both of my issues are caused by some sort of copy protection. I am using k9copy and with a few dvd it grinds to a halt and never finishes the backup. if I try to back it up with brasero I get and input/output error. 

Things I have tried different computer with different drive. Using windows and powerISO to make an image of the disc. Another disc of the exact same movie. All of these end with the same errors. I am currently trying dvdisaster to run but it is not looking good. 

This has to be a dvd encryption problem because using a different disc should have fixed the problem if it was a damaged disc.

---

### Post by DexterF on 2012-05-22
Medibuntu, decss enabled k9copy.

---

### Post by w1ll1am on 2012-05-22
i have run the commands from medibuntu and have libdvdread4 and libdvdcss2 installed  is there something else i need?

---

### Post by Nutria on 2012-05-22
> **w1ll1am said:**
> i have run the commands from medibuntu and have libdvdread4 and libdvdcss2 installed  is there something else i need?

Did you run this script after installing libdvdread4?
```
/usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by w1ll1am on 2012-05-24
> **Nutria said:**
> Did you run this script after installing libdvdread4?
```
/usr/share/doc/libdvdread4/install-css.sh
```

I was not sure if i had run it or note so i ran it. after i ran it i still have the same problem.

---

### Post by |{urse on 2012-05-24
Just curious, does

sudo cat /dev/sr0 > /home/whatever/dvd.iso 

Do what youre wanting? It could be /dev/scd0 or /dev/cdrom

---

### Post by Nutria on 2012-05-24
> **|{urse said:**
> Just curious, does

sudo cat /dev/sr0 > /home/whatever/dvd.iso 

Do what youre wanting? It could be /dev/scd0 or /dev/cdrom

No CLI program that I've tried (dd, dvdread, ddrescue) has a 100% rate in copying encrypted movie/TV DVDs.  Brasero, OTOH, **always** works.

---

### Post by |{urse on 2012-05-24
Well by all means then, continue to use it. :)

---

### Post by w1ll1am on 2012-05-25
Here is a list of DVDs that i have tried to backup that i have not got too work. ( in linux with brasero, dd, ddrescue, dvd95, or just copying the folders over)

21
cars 2
pirates of the Caribbean on strange tides
The Smurfs
underworld evolution ( tried two different dvds )

So out of the 150 or so dvds i have backup for my htpc so far 5 have not worked thats 96% success it is possible you just have not run into a disc like this.

I have managed to copy all of these with a windows program called dvdfab which can just copy the folders over to disk. Then i run k9copy from a folder and not disc. 

sudo cat /dev/sr0 > /home/whatever/dvd.iso 

I get the same error with this as well input/output error



The above is too much work especially since dvdfab is only a 30 day trial.

---

### Post by Nutria on 2012-05-25
> **w1ll1am said:**
> sudo cat /dev/sr0 > /home/whatever/dvd.iso 

I get the same error with this as well input/output error

As do I with "mount" and "cp".

---

### Post by w1ll1am on 2012-05-25
> **Nutria said:**
> As do I with "mount" and "cp".

But you don't get this error in brasero?

---

