---
title: "Mythweb doesn't work"
date: 2010-12-22
forum: Mythbuntu
---

### Post by williammanda on 2010-12-22
I just tried to start mythweb using the latest .24 and i get a blank page. I get this error in the backend log:

2010-12-22 10:17:28.286 MainServer, Warning: Unknown socket closing MythSocket(0x1ec5160)

I tried re-installing but get the same result. I enabled the password and get the same result.

---

### Post by 4dognight on 2010-12-22
anything useful in the apache logs?

---

### Post by williammanda on 2010-12-23
Where and how do I do that?

---

### Post by 4dognight on 2010-12-23
They are in /var/log/apache2

---

### Post by williammanda on 2010-12-24
I don't have that file.

---

### Post by newlinux on 2010-12-24
What does

```
ls /var/log/apache2/
```

return?

If you don't have any logs do you have apache2 installed or started?

what does ```
sudo service apache2 restart
```

yield?

---

### Post by 4dognight on 2010-12-24
Are you looking for the logs on your backend server? They wont be there on a frontend.

---

### Post by williammanda on 2010-12-24
Sorry I was looking on a frontend. Here is the log output:

Error log:

```
[Fri Dec 24 12:27:00 2010] [error] [client 192.168.1.100] PHP Warning:  file_get_contents(modules_path/_shared/lang/English.lang): failed to open stream: No such file or directory in /usr/share/mythtv/mythweb/classes/Translate.php on line 168
[Fri Dec 24 12:27:00 2010] [error] [client 192.168.1.100] PHP Fatal error:  Failed to open translation file:  modules_path/_shared/lang/English.lang in /usr/share/mythtv/mythweb/classes/Translate.php on line 172
```

Access log:

```
192.168.1.100 - williammanda [24/Dec/2010:12:27:00 -0600] "GET /mythweb/ HTTP/1.1" 401 762 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
192.168.1.100 - williammanda [24/Dec/2010:12:27:00 -0600] "GET /mythweb/ HTTP/1.1" 500 274 "-" "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13"
```

---

### Post by williammanda on 2010-12-27
Any ideas?

---

### Post by 4dognight on 2010-12-28
Looks like your not the only one with this problem.

[http://ubuntuforums.org/showthread.php?t=1648653&highlight=http+500](http://ubuntuforums.org/showthread.php?t=1648653&highlight=http+500)


You might want to try and uninstall mythweb and then reinstall mythweb, as it looks like your missing some file.

Im disappointed with all the bugs in mythbuntu 10.10 and .24. It is far more bug riddled than previous versions. But, since I want the new features, I will have to get out my can of Raid. The other poster on your problem, has him doing a reinstall.  In your case I would just reinstall mythweb first. Another possibilty is if its just missing some file(s), is to copy them over from another server if you have one.

---

### Post by williammanda on 2010-12-28
> **4dognight said:**
> Looks like your not the only one with this problem.

[http://ubuntuforums.org/showthread.php?t=1648653&highlight=http+500](http://ubuntuforums.org/showthread.php?t=1648653&highlight=http+500)


You might want to try and uninstall mythweb and then reinstall mythweb, as it looks like your missing some file.

Im disappointed with all the bugs in mythbuntu 10.10 and .24. It is far more bug riddled than previous versions. But, since I want the new features, I will have to get out my can of Raid. The other poster on your problem, has him doing a reinstall.  In your case I would just reinstall mythweb first. Another possibilty is if its just missing some file(s), is to copy them over from another server if you have one.

I have re-installed it 3 times and that's the limit of my knowledge to troubleshoot it. I only have a MBE with multiple FE's. This setup is a clean install of 10.10 ubuntu and mythtv .24.

---

### Post by newlinux on 2010-12-28
perhaps take a look at this ticket and the suggestions in it:

[http://code.mythtv.org/trac/ticket/9255](http://code.mythtv.org/trac/ticket/9255)

---

### Post by williammanda on 2010-12-28
> **newlinux said:**
> perhaps take a look at this ticket and the suggestions in it:

[http://code.mythtv.org/trac/ticket/9255](http://code.mythtv.org/trac/ticket/9255)

I read through the posts and it looks like a fix is coming:

> Should be fixed in master 7cb9061 fixes/0.24 1a998aa

So I will wait for the update and try again.

---

### Post by newlinux on 2010-12-28
I didn't read through the ticket in great detail, but the weird thing to me is that it seems to work fine for some people or we'd see a lot more threads on it here. Mythweb works fine for me (although I've customized it a bit and run a few other PHP apps), but mine is a system upgraded via autobuilds from .23 to .24.

I hope that gets it fixed for you.

---

### Post by williammanda on 2010-12-28
> **newlinux said:**
> I didn't read through the ticket in great detail, but the weird thing to me is that it seems to work fine for some people or we'd see a lot more threads on it here. Mythweb works fine for me (although I've customized it a bit and run a few other PHP apps), but mine is a system upgraded via autobuilds from .23 to .24.

I hope that gets it fixed for you.

I believe you have hit the root of the problem. It worked fine for me when I upgraded from .23 to .24. When I had issues and did a clean install with .24, that was when this error started.

---

### Post by williammanda on 2010-12-28
I went ahead and tried the solution:

```
ln -s /usr/share/mythtv/mythweb/modules /usr/share/mythtv/mythweb/modules_path
```

and it worked!

---

### Post by 4dognight on 2010-12-28
Did you try the workaround one of the users suggested.



```
I used the fix at  http://www.gossamer-threads.com/lists/mythtv/users/459835

Or more specifically, I entered [COLOR="Red"]ln -s /usr/share/mythtv/mythweb/modules /usr/share/mythtv/mythweb/modules_path[/COLOR]

I'm using MythTV 0.24 on Mythbuntu 10.04.
```

---

### Post by williammanda on 2010-12-28
> **4dognight said:**
> Did you try the workaround one of the users suggested.



```
I used the fix at  http://www.gossamer-threads.com/lists/mythtv/users/459835

Or more specifically, I entered [COLOR="Red"]ln -s /usr/share/mythtv/mythweb/modules /usr/share/mythtv/mythweb/modules_path[/COLOR]

I'm using MythTV 0.24 on Mythbuntu 10.04.
```

The fix you have supplied is the same as the fix supplied on the bug report.

---

### Post by thatguruguy on 2010-12-28
Wow. I had completely forgotten that I had set up the soft link, or I would have recommended it to you. Sorry about that.

---

### Post by Lem on 2010-12-29
I modified Translate.php to manually correct the path. Still get some warnings in some modules, but it largely works.
Hadn't thought about soft linking the path!

---

### Post by GooKing on 2011-10-10
Getting the same issue here after the most recent round of updates. Done a mythweb remove/reinstall. After adding the soft link as above I get the error:

**Warning** at /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php, line 16:
!!NoTrans:  Cannot modify header information - headers already sent by (output  started at  /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php:50)!!

Still working on it....

---

