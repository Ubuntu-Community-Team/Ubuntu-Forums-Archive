---
title: "manually deleted shows..."
date: 2010-02-15
forum: Mythbuntu
---

### Post by linuxhippy on 2010-02-15
My disk was 100% full-I knew this when everything on the mythtv frontend stopped working.  I've run it more then 14 days now so it should have started to auto delete things but I still saw the titles available to watch.  So I went CLI and manually deleted all the nuv and png files I no longer needed.

Now I have a lot more disk space and again see that I have shows on my drive to watch.  BUT-most of those shows won't play because I deleted them.  How can I update the mythdatabase so that I only see the shows that are on my drive now?

---

### Post by iponeverything on 2010-02-15
Just create an empty files with same names so that it has something to delete..

---

### Post by linuxhippy on 2010-02-15
they're around 70 nuv files and 70 png files with weird names...that's why I deleted everything because I couldn't differentiate them by filename.  Now I have directories for each show.  I guess I would use touch to create these files...can I name them the tv show name.nuv or does it need the strange naming convention with the nuv and png files?

---

### Post by linuxhippy on 2010-02-15
Also, how's it going to delete these...they weren't auto-expiring?

---

### Post by iponeverything on 2010-02-15
> **linuxhippy said:**
> they're around 70 nuv files and 70 png files with weird names...that's why I deleted everything because I couldn't differentiate them by filename.  Now I have directories for each show.  I guess I would use touch to create these files...can I name them the tv show name.nuv or does it need the strange naming convention with the nuv and png files?

They are going to have the name that had before you deleted them.

If you can see the Original names by:

```
ls -l /myth/pretty
```

something to recreate the nuv's might be:

```
ls -l |awk -F "->" '{print "touch "$2}' | sh

```

I have no idea why the autoexpire didn't work.. have a 1Tb drive and a wife that loves to delete stuff, so I have never filled up..

---

### Post by nickrout on 2010-02-15
go to the mythtv wiki and look at the page for mythfindorphans.

---

### Post by linuxhippy on 2010-02-15
> **nickrout said:**
> go to the mythtv wiki and look at the page for mythfindorphans.

found this:

[http://www.mythtv.org/wiki/Myth.find_orphans.pl]("http://www.mythtv.org/wiki/Myth.find_orphans.pl")

I couldn't find out how to use the script.  I found it in:

/usr/share/doc/mythtv-backend/contrib/maintenance

and tried unsuccessfully to execute it with:

sudo ./myth.find_orphans.pl
AND
sudo sh myth.find_orphans.pl

How do I run this?

---

### Post by SiHa on 2010-02-15
From memory, the scripts that are in the contrib directory aren't executable by default (though God knows why!).
```
sudo chmod 777 myth.find_orphans.pl
```
...will make it executable by all

---

### Post by linuxhippy on 2010-02-16
> **SiHa said:**
> From memory, the scripts that are in the contrib directory aren't executable by default (though God knows why!).
```
sudo chmod 777 myth.find_orphans.pl
```
...will make it executable by all

I got this error:

DBI connect('database=mythconverg:host=FreeVo','mythtv',...) failed: Can't connect to MySQL server on 'FreeVo' (111) at ./myth.find_orphans.pl line 114
Cannot connect to database mythconverg on host FreeVo:

---

### Post by laffinet on 2010-02-16
Found this bit [here]("http://www.acetylcholine.com/node/5959").

Maybe this will help:

> ./myth.find_orphans.pl --help

Tells you what the script is defaulting to with its connection options.

Try:

./myth.find_orphans.pl --dbhost=localhost

---

### Post by linuxhippy on 2010-02-17
still not able to do this...though now I got a third error that's the same thing the poster in that link got:

sudo ./myth.find_orphans.pl --dbhost=localhost

DBI connect('database=mythconverg:host=localhost','mythtv',...) failed: Access denied for user 'mythtv'@'localhost' (using password: YES) at ./myth.find_orphans.pl line 114
Cannot connect to database mythconverg on host localhost: 

I also followed that link and tried these:

sudo mysql -u mythtv -p- h mediaserver
AND
sudo mysql -u mythtv -p- h localhost

I just got a listing of available options but when I tried the myth.find_orphans.pl I got that same error.

---

### Post by nickrout on 2010-02-17
what password is the script using?

---

### Post by linuxhippy on 2010-02-18
> **nickrout said:**
> what password is the script using?

whatever is the default password...I never changed it.

---

### Post by nickrout on 2010-02-18
The unamended script contains the following lines:

```
my $opt_host =          hostname;
my $opt_dbhost =        $opt_host;
my $opt_database =      "mythconverg";
my $opt_user =          "mythtv";
my $opt_pass =          "mythtv";

```

change the last line to match your password, which you can find by:

```
grep DBPassword /etc/mythtv/mysql.txt
```

---

### Post by linuxhippy on 2010-02-18
woohoo!!  fixed!!

I changed the pass file from "mythtv" to "ht158z" and then did:


sudo ./myth.find_orphans.pl --dbhost=localhost

and it listed the 101 bad files and said if that was right use --dodbdelete...so I followed up with this and all is fixed:

sudo ./myth.find_orphans.pl --dbhost=localhost --dodbdelete

Thanks for the help :)

---

### Post by nickrout on 2010-02-18
> **linuxhippy said:**
> 

Thanks for the help :)

Yeah we got there in the end didn't we :)

---

