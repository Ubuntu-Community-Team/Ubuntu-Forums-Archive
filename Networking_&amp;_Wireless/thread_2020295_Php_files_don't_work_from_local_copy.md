---
title: "Php files don't work from local copy"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by SillySod on 2012-07-08
I've downloaded a local copy of a website I refer to regularly, using wget, but many of the files are php or php3 suffixed.  When I try to navigate to one of these from the locally stored copy, Firefox tries to download the file instead of displaying it as a web page.

What is the solution to this?

---

### Post by spjackson on 2012-07-08
There are a couple points where I am not quite clear what you mean.

First, have you done something like this?
```
wget http://www.php.net/tut.php
```In this case, the file saved locally as a .php actually contains html. If this what you want?

If you wanted the php source instead, then you couldn't normally get it via http, but if you had ftp access, you could get it by something like
```
wget ftp://some.site/tut.php
```Second, are you opening the local file as, for example,
```
http://localhost/tut.php
```or are you opening it by clicking from Nautilus?

If what you want is to display the html that was downloaded by wget via php, then the simplest option is to rename the file from .php to .html. You can do this with your wget command, or manually afterwards.
```
wget -o tut.html http://www.php.net/tut.php
```

---

### Post by SillySod on 2012-07-08
I used this syntax, maybe it's wrong:

```
wget --mirror -p --convert-links -P ./localdir http://website.com
```

To use the local copy, I just clicked on the files from Thunar in the directory where they are stored.

I did read something about needing Apache so I could use the "localhost" method, but I did install Apache and drop some of the php files in the Apache /var/www directory but Firefox still tried to get me to save them.

I suppose what I want to do is just be able to download the website and have it working from the local copy with the minimum of trouble.  I don't think I want to have to rename all the php files to html files, because presumably this would break all the links in the local copy of the site.

If I download the site using ftp (assuming I can), would the php files then work from the local copy?

---

### Post by spjackson on 2012-07-09
> **SillySod said:**
> If I download the site using ftp (assuming I can), would the php files then work from the local copy?
This could work, if you use the apache and [http://localhost/](http://localhost/) method. However, sites that use php also often use a database such as MySQL, and the php scripts don't work without the database.

---

### Post by Merrattic on 2012-07-09
Most likely problem is you Apache2 is not corrctly configured to serve php pages. See here:
[http://ubuntuforums.org/showthread.php?t=287876](http://ubuntuforums.org/showthread.php?t=287876)

---

### Post by SeijiSensei on 2012-07-09
> **SillySod said:**
> I've downloaded a local copy of a website I refer to regularly, using wget, but many of the files are php or php3 suffixed.  When I try to navigate to one of these from the locally stored copy, Firefox tries to download the file instead of displaying it as a web page.

What is the solution to this?

Since the downloaded versions are HTML, just change the extensions on the files from .php to .html.  Firefox should then be happy.

I presume you realize that downloading a .php page will only give you the rendered HTML.  You cannot download the underlying PHP scripts that generated the page unless the web site owner has really poor security in place.

---

