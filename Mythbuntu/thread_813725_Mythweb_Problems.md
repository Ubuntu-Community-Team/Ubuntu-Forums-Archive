---
title: "Mythweb Problems"
date: 2008-05-31
forum: Mythbuntu
---

### Post by atomicfire on 2008-05-31
I had a problem with mythweb just listing the directory of files when accessing /mythweb in the browser. I then did

```
apt-get remove --purge apache2 php5 mythweb
```

then:

```
rm -r /etc/apache2
```

then reinstalled with:

```
apt-get install mythweb
```

Now when I try to start apache2 with:

```
/etc/init.d/apache2 start
```

I get:

```
 * Restarting web server apache2                                                .: 197: Can't open /etc/apache2/envvars
ERROR: APACHE_PID_FILE needs to be defined in /etc/apache2/envvars




apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory
                                                                         [fail]
```


Any ideas? No amount of removing and reinstalling apaceh2 fixes it :(

---

### Post by OldGaf on 2008-05-31
When you removed apache2, did you do a find on it?

> sudo find / -name apache2

then blow away anything you find.....

---

### Post by OldGaf on 2008-07-03
> **atomicfire said:**
> I had a problem with mythweb just listing the directory of files when accessing /mythweb in the browser. I then did

```
apt-get remove --purge apache2 php5 mythweb
```

then:

```
rm -r /etc/apache2
```

then reinstalled with:

```
apt-get install mythweb
```

Now when I try to start apache2 with:

```
/etc/init.d/apache2 start
```

I get:

```
 * Restarting web server apache2                                                .: 197: Can't open /etc/apache2/envvars
ERROR: APACHE_PID_FILE needs to be defined in /etc/apache2/envvars




apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory
                                                                         [fail]
```


Any ideas? No amount of removing and reinstalling apaceh2 fixes it :(

Had a similar problem. Uninstalled apache2 and then deleted the /etc/apache2 folder. Then on install, this was not created again. Found this solution:

sudo apt-get remove --purge $(dpkg -l apache* | grep ii | awk '{print $2}') && sudo apt-get install apache2

---

### Post by Pjokken on 2008-07-05
Tusen takk!

Dette hjalp meg masse! Er nesten irritert over hvor lett det var når man får løsningen servert! :popcorn:

---

