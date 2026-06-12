---
title: "Cancel apache redirect to /var/www/mythweb"
date: 2009-04-06
forum: Mythbuntu
---

### Post by odror on 2009-04-06
Hi,

I have installed mythbuntu 9.4. I do intend to have this machine also as my server for other things beside mythtv. One of the issues that I am having is mythweb redirection.

When I access the web page [http://localhost](http://localhost) I am redirected to http:/localhost/mythweb. This persist even when I uninstall mythweb and remove all references to mythweb from index.html and sites-enabled. Has apche2 been modified internally to support mythweb only. Does anyone know how to fix this problem. There other issue that I have with aopache is that I would like it to show the directory content for the root directory and not look for the file index.html.

-thanks

---

### Post by superm1 on 2009-04-06
> **odror said:**
> Hi,

I have installed mythbuntu 9.4. I do intend to have this machine also as my server for other things beside mythtv. One of the issues that I am having is mythweb redirection.

When I access the web page [http://localhost](http://localhost) I am redirected to http:/localhost/mythweb. This persist even when I uninstall mythweb and remove all references to mythweb from index.html and sites-enabled. Has apche2 been modified internally to support mythweb only. Does anyone know how to fix this problem. There other issue that I have with aopache is that I would like it to show the directory content for the root directory and not look for the file index.html.

-thanks
Just remove /var/www/index.html and the redirection goes away.  It's dynamically made if it finds that index.html hasn't been modified from apache's default when mythweb gets installed.

---

### Post by odror on 2009-04-06
Thanks now it is fixed. I hope that when I reinstall mythweb that the problem will not come back. I actually thought about that I renamed index.html. That did notwork I actually had to remove it.

-thanks

---

### Post by superm1 on 2009-04-06
> **odror said:**
> Thanks now it is fixed. I hope that when I reinstall mythweb that the problem will not come back. I actually thought about that I renamed index.html. That did notwork I actually had to remove it.

-thanks
Here's the current postinst:

[http://bazaar.launchpad.net/~ubuntu-mythtv/mythplugins/mythplugins-fixes/annotate/head%3A/debian/mythweb.postinst](http://bazaar.launchpad.net/~ubuntu-mythtv/mythplugins/mythplugins-fixes/annotate/head%3A/debian/mythweb.postinst)

The piece you are looking for is at the end with the index.html.  I believe right now as it stands if you are *removing* the index.html, it will come back with a reconfigure.  Can you please file a bug against mythplugins at [http://bugs.launchpad.net/ubuntu/+source/mythplugins](http://bugs.launchpad.net/ubuntu/+source/mythplugins) so that we can remember  to get this fixed in a future upload?

---

### Post by spicemuseum on 2009-05-28
> **superm1 said:**
> Just remove /var/www/index.html and the redirection goes away.Not for me it doesn't.
I've both rm'd index.html and I've moved the whole directory /var/www/apache2-default (which also contains an (identical) index.html) to somewhere else, and then restarted apache: /etc/init.d/apache2 restart

It still redirects to mythweb for me. What am I doing wrong?

I see an alternative solution to the same problem discussed over here: [http://ubuntuforums.org/showthread.php?t=1155353](http://ubuntuforums.org/showthread.php?t=1155353)

I'll try that a bit later.

...and the bug is reported fixed in Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/356798](https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/356798)

---

### Post by brian mcgee on 2009-06-13
> **spicemuseum said:**
> I see an alternative solution to the same problem discussed over here: [http://ubuntuforums.org/showthread.php?t=1155353](http://ubuntuforums.org/showthread.php?t=1155353)

Worked for me. Basically, uninstall Mythweb through the control centre, then reinstall using apt:

```
sudo apt-get install mythweb
```Then say "no" when asked if you want to use apache for mythweb exclusively.

---

### Post by tgm4883 on 2009-06-14
> **brian mcgee said:**
> Worked for me. Basically, uninstall Mythweb through the control centre, then reinstall using apt:

```
sudo apt-get install mythweb
```Then say "no" when asked if you want to use apache for mythweb exclusively.

Hmm, I wonder if this would have worked
```
sudo dpkg-reconfigure mythweb
```

---

### Post by superm1 on 2009-07-01
> **tgm4883 said:**
> Hmm, I wonder if this would have worked
```
sudo dpkg-reconfigure mythweb
```
Probably

---

### Post by tgm4883 on 2009-07-01
> **superm1 said:**
> Probably

Way to be on top of replying to threads ;) I'll never catch you at this rate. :)

---

