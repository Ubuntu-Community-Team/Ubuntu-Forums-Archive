---
title: "Mythexport: Permission problems after upgrading to Natty"
date: 2011-05-24
forum: Mythbuntu
---

### Post by lingenfr on 2011-05-24
Prior to upgrading to natty, I was able to stream my recordings to my iPhone. Now I can't. I bring up the streaming webpage (with the video window and controls) but I can't start the video. Is there a fix?

---

### Post by lingenfr on 2011-06-04
Bump.

---

### Post by mhawkshaw on 2011-06-11
Try the following:

edit /etc/apache2/sites-enabled/mythexport.conf
replace SymLinksIfOwnerMatch with FollowSymLinks

Restart Apache with:

sudo service apache2 restart

I'll let you read up on any potential security risks that introduces

---

### Post by lingenfr on 2011-06-11
That worked. Thanks. That also fixed streaming.

---

### Post by SpaceBas on 2012-04-22
> **mhawkshaw said:**
> Try the following:

edit /etc/apache2/sites-enabled/mythexport.conf
replace SymLinksIfOwnerMatch with FollowSymLinks

Restart Apache with:

sudo service apache2 restart

I'll let you read up on any potential security risks that introduces

Just a bump to note that this is one of the many fixes still required in the version of mythexport in the repos for the latest Ubuntu releases... Although in my case, while it does get rid of the permissions error, it does not result in a working install. Now, with the followsymlinks config, I don't get _anything_. If you paste the URL of the file into a browser, it simply clears out the URL...no file download. Same result in iTunes. 

In addition, several changes need to be made to the .pm files as well: [http://ubuntuforums.org/showthread.php?p=11865337#post11865337](http://ubuntuforums.org/showthread.php?p=11865337#post11865337)

---

