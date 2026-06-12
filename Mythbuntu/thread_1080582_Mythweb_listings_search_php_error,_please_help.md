---
title: "Mythweb listings search php error, please help"
date: 2009-02-25
forum: Mythbuntu
---

### Post by dannyboy79 on 2009-02-25
I was trying to add a new recording schedule for the show "House" and when I type in House within the search box and click on search, it brings me to this page.

[http://blahblahblah/mythweb/tv/search?type=q&s=house&search=Search](http://blahblahblah/mythweb/tv/search?type=q&s=house&search=Search)

my FQDN has been changed for obvious reasons despite having it password protected. Anyway, the errors are below:

Fatal error: Allowed memory size of 33554432 bytes exhausted (tried to allocate 35 bytes) in /usr/share/mythtv/mythweb/modules/tv/search.php on line 333

when I look at that .php file, line 333 shows this:
[PHP]                $Results[$key2]->extra_showings[] = array($show->chanid, $show->starttime);[/PHP]

Fatal error: Call to a member function query() on a non-object in /usr/share/mythtv/mythweb/includes/session.php on line 60

when I look at that .php file, line 60 it shows this:
[PHP]        $db->query('REPLACE INTO mythweb_sessions (id, modified, data) VALUES(?,NULL,?)',[/PHP]

Can anyone please out with this?

---

### Post by crez79 on 2009-02-25
I think there are too many results and are exceeding the filesize limit in php. You need to either narrow down the results or raise the filesize limit.

To raise the filesize limit, edit /var/www/mythweb/mythweb.conf.apache and find the php section. Raise the php_value memory_limit to something higher. Mine is set at 32M which works fine for me.

---

### Post by dannyboy79 on 2009-02-26
> **crez79 said:**
> I think there are too many results and are exceeding the filesize limit in php. You need to either narrow down the results or raise the filesize limit.

To raise the filesize limit, edit /var/www/mythweb/mythweb.conf.apache and find the php section. Raise the php_value memory_limit to something higher. Mine is set at 32M which works fine for me.

yeah, good catch, it states that the allowed memory size of 33554432 bytes was exhausted and that the search results were 35 bytes. I wonder how can I narrow down my search when looking for the show "House", maybe add a certain channel? Otherwise how would I narrow that down. I can certainly go in and change the allocation to something higher than 35 bytes like you suggested but what if this happens again on a different search, then I have to keep changing the allocation size???

thanks for the suggestion.

---

### Post by dannyboy79 on 2009-02-26
> **crez79 said:**
> I think there are too many results and are exceeding the filesize limit in php. You need to either narrow down the results or raise the filesize limit.

To raise the filesize limit, edit /var/www/mythweb/mythweb.conf.apache and find the php section. Raise the php_value memory_limit to something higher. Mine is set at 32M which works fine for me.
can't find that file you specified. I am using Feisty, mythweb version:  0.20.2-0ubuntu0.7.04
please help. Also, why does using HOUSE and channel name FOX as a search bring up shows like "Sunday Housecall With Dr. Rosenfeld", how do you do an exact match search in mythweb? It isn't finding any HOUSE although I know there's an episode on 3/9/2009?

---

### Post by dsbw on 2009-08-22
I get this same message:

```
Fatal error: Allowed memory size of 33554432 bytes exhausted ... [etc]
```

I've changed both:

```
/etc/php5/apache2

memory_limit = 128M ; from 32M

```
and:

```
/usr/share/mythtv/mythweb/mythweb.conf.apache

php_value memory_limit       64M     # from 32M

```
and neither changes the error message.

So which corner is it, exactly, that I have to piss in to make this work? ](*,)

---

### Post by crez79 on 2009-08-22
Did you edit  /var/www/mythweb/mythweb.conf.apache? That is the one that did it for me.

---

### Post by dsbw on 2009-08-23
> **crez79 said:**
> Did you edit  /var/www/mythweb/mythweb.conf.apache? That is the one that did it for me.

I did. I did that one first.

I'm not sure how the other one got changed, the /usr/share/mythtv/mythweb/mythweb.conf.apache one.

Oh, I see: Same file. Just for giggles I put that at 128M too.

No freakin' change. It insists it's got that 32MB limit. Half-tempted to search every file on the disk for "32M".

---

### Post by dsbw on 2009-08-25
Nothing? Can't be that big a deal, can it? Some other config file?

---

### Post by Twintop on 2009-10-01
I get exactly the same error message as well. I've gotten around the problem using RegEx trickery though: searching for "^house$" will only return, well, episodes of House. :)

---

