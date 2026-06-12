---
title: "mythweb access issue (goes to index page)"
date: 2008-06-18
forum: Mythbuntu
---

### Post by sr_guy on 2008-06-18
I'm not sure how to fix this. when I access my mythweb url with:

[http://my](http://my) ip/mythweb


I get the index list:

Index of /mythweb
[ICO]	Name	Last modified	Size	Description
[DIR]	Parent Directory	 	-
[ ]	INSTALL	21-Apr-2008 09:01 	7.5K
[DIR]	data/	17-Jun-2008 22:38 	-
[DIR]	includes/	17-Jun-2008 22:38 	-
[DIR]	js/	17-Jun-2008 22:38 	-
[DIR]	modules/	17-Jun-2008 22:38 	-
[ ]	mythweb.conf	17-Jun-2008 21:11 	8.8K
[ ]	mythweb.conf.apache	21-Apr-2008 09:01 	8.7K
[ ]	mythweb.conf.lighttpd	21-Apr-2008 09:01 	1.5K
[ ]	mythweb.php	21-Apr-2008 09:01 	1.2K
[TXT]	mythweb.pl	21-Apr-2008 09:01 	2.9K
[DIR]	objects/	17-Jun-2008 22:38 	-
[DIR]	skins/	17-Jun-2008 22:38 	-


How do I fix this?

---

### Post by uopjohnson on 2008-06-21
sounds like you are missing the apache configuration file for mythweb.  What happens when you run:
```
ls /etc/apache2/sites-enabled
```
I see:
```

jon@apollo:~$ ls /etc/apache2/sites-enabled
000-default  mythweb.conf

```

you might want to try disabling and re-enabling mythweb, I'm not sure what else might be wrong.  Have you messed with your apache configuration at all?

---

### Post by sr_guy on 2008-06-21
this is solved. I ended up doing a clean re-install. The SQL DB was screwed up

---

