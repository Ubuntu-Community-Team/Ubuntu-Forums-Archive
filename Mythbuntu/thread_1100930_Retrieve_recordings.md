---
title: "Retrieve recordings"
date: 2009-03-19
forum: Mythbuntu
---

### Post by xfred on 2009-03-19
Hi

After having my mythbuntu box running for a few years it finally crashed in what seems to be a non-fixable manner, at least for me in - it can't reach the database, possibly due to an untimely power failure in the middle of recording a show.  Anyhow I'm going to reinstall, after making some long overdue mods to the hardware, which I'm actually looking forward to.  But before I do so I was wondering:

Q: how to grab the old recordings off the hard-drive and put them back so the fresh install sees them?

Ideally I'd prefer them to appear as recordings on the new installation, but if that's not possible can you just dump files into the video library?  Also, which directory are recordings stored in, and would they need to be transcoded first?

Also I've just bought myself a shiny new NAS and was wondering if it's possible to make mythbuntu get video files off that rather than the local hard-drive?  That way I can remove 2 hard-drives from the box to make it quieter.

All help appreciated.

---

### Post by nickrout on 2009-03-19
> **xfred said:**
> Hi

After having my mythbuntu box running for a few years it finally crashed in what seems to be a non-fixable manner, at least for me in - it can't reach the database, possibly due to an untimely power failure in the middle of recording a show.  Anyhow I'm going to reinstall, after making some long overdue mods to the hardware, which I'm actually looking forward to.  But before I do so I was wondering:

Q: how to grab the old recordings off the hard-drive and put them back so the fresh install sees them?

yes you will need to back up your database as well as the recordings files themselves.

> 

Ideally I'd prefer them to appear as recordings on the new installation, but if that's not possible can you just dump files into the video library?  Also, which directory are recordings stored in, and would they need to be transcoded first?

That would work but the files are oddly named and you'd not know what each one was. They are named like:

2035_2009032000.mpg

> 

Also I've just bought myself a shiny new NAS and was wondering if it's possible to make mythbuntu get video files off that rather than the local hard-drive?  That way I can remove 2 hard-drives from the box to make it quieter.

All help appreciated.

yes mount the drives via nfs or cifs and point your storage groups setting to the mounted drive.

---

### Post by xfred on 2009-03-19
> **nickrout said:**
> yes you will need to back up your database as well as the recordings files themselves.
Where are these located?  I must admit I know next to nothing about databases.

> **nickrout said:**
> That would work but the files are oddly named and you'd not know what each one was. They are named like:

2035_2009032000.mpg


yes mount the drives via nfs or cifs and point your storage groups setting to the mounted drive.
Cool, thanks.

---

### Post by nickrout on 2009-03-19
> **xfred said:**
> Where are these located?  I must admit I know next to nothing about databases.


If all else fails read the [instructions ]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.7"):)

EDIT just re-read your original post. Try repairing the data base by running

[http://www.mythtv.org/wiki/Optimize_mythdb.pl](http://www.mythtv.org/wiki/Optimize_mythdb.pl)

---

### Post by xfred on 2009-03-20
> **nickrout said:**
> If all else fails read the [instructions ]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.7"):)
:oops:

> **nickrout said:**
> EDIT just re-read your original post. Try repairing the data base by running

[http://www.mythtv.org/wiki/Optimize_mythdb.pl](http://www.mythtv.org/wiki/Optimize_mythdb.pl)
Thanks, I'll give it a go.

EDIT: "cannot connect to database".  Ah well, was worth a try.

---

### Post by nickrout on 2009-03-20
can you connect to the database by running

```
mysql -host localhost -u user -p mythconverg 
```

?

---

### Post by xfred on 2009-03-20
> **nickrout said:**
> can you connect to the database by running

```
mysql -host localhost -u user -p mythconverg 
```

?

I get ERROR 1045 (28000): Access denied for user '###'@'localhost' (using password : YES)

where ### is my username on the machine.

---

### Post by nickrout on 2009-03-20
the username you should use is the mysql username, which you can get from 

```
cat /etc/mythtv/mysql.txt
```

the password is there too.

---

### Post by xfred on 2009-03-20
Never mind.  I found and copied the recordings directory last night, directly copied it out and worked out what I wanted to convert and keep and what could go.  System has been reinstalled and is working fine.  I'll just put the old recordings in the video directory on the NAS.

Thanks anyhow.

---

