---
title: "Apache 2 Access Issues"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by throese on 2010-08-12
Okay, before I start, I know I don't answer people or try to help others as much as I should, but that's because I'm also new to Ubuntu still even though I've been using it for about a month now. If I knew as much as all of these other experienced users, I'd help out a lot more, honest.

Here's my problem:

[http://i204.photobucket.com/albums/bb125/throese/access_problems.png](http://i204.photobucket.com/albums/bb125/throese/access_problems.png)

I don't know why I can't access that folder and all the files within, but I can access these two files:

[http://i204.photobucket.com/albums/bb125/throese/location.png](http://i204.photobucket.com/albums/bb125/throese/location.png)

The index.html and the info.php files work just fine.

In my Windows partition, WAMP lets me access all of the folders and files within the WWW folder, but why won't Ubuntu 10.04 LTS?

Please, help.

---

### Post by Kerubu on 2010-08-12
I think this is just a permissions issue.

If (using Nautilus, the Ubuntu file browser) you right-click on your folder 'php_tutorials' and then click on 'Properties'. From there look at 'Permissions'. Make sure that 'Others' have their access enabled. Note also you should select the option 'Apply permissions to enclosed files' so that files within php_tutorials can be read.

The reason why it works under windows is that windows doesn't pay any attention to permission settings. That's not a good idea and insecure way of doing things.

---

### Post by throese on 2010-08-12
Thank you Kerubu. =)

---

### Post by Kerubu on 2010-08-12
No problem. Just so that everyone knows you've solved your problem, can you mark your thread as 'SOLVED'. To do this click on the 'Thread Tools' and select 'Mark as solved'

---

### Post by throese on 2010-08-16
Thanks again and set it to [SOLVED]

---

