---
title: "Rhythmbox password protected podcasts in Intrepid"
date: 2008-11-03
forum: Multimedia Software
---

### Post by lmonast on 2008-11-03
I am a subscriber of lbc.co.uk podcasts and they have username / password protected podcast. It used to work perfectly in ubuntu 8.04. After the upgrade it is not working anymore. I get "There was a problem adding this podcast: Unable to parse the feed contents.  Please verify the URL: http://82.136.33.201/podcast.php?channel=subjames"

Any help? BTW, why banshee is not able of dealing with password protected feeds?
Thank you very much.

---

### Post by lopatoid on 2008-11-10
I have the same problem with every feed i've got. Looks like Rhythmox podcast plugin completely broken.

UPD: Just reinstalled gvfs-backend. Problem solved.

---

### Post by cytenticle on 2010-05-23
Have a solution for password protected podcasts and rhythmbox

When you add the podcast feed add it in this format

```
http://username:password@podcasturl.com
```
for example

your username - user
your password - password
podcasturl - secretpodcast.com/podcast.xml

the way you would add the feed is -

```
http://user:password@secretpodcast.com/podcast.xml
```

Hope that helps - worked for me.

---

### Post by MakOwner on 2011-01-12
I'm reviving an old thread, but I have this exact issue with rhythmbox and this solution doesn't work for me.

The directory structure on the web server is protected by .htaccess password protection.  Using the syntax below, rhtythmbox still fails with an invalid  

When you add the podcast feed add it in this format it reports "error in podcast" and the apache logs show an authentication error.


Any ideas?


> **cytenticle said:**
> Have a solution for password protected podcasts and rhythmbox



```
http://username:password@podcasturl.com
```
for example

your username - user
your password - password
podcasturl - secretpodcast.com/podcast.xml

the way you would add the feed is -

```
http://user:password@secretpodcast.com/podcast.xml
```

Hope that helps - worked for me.

---

### Post by adstro on 2011-02-11
This seems to work for me...unless the username contains "@".  In my case, the username is an email address.  Any ideas?

> **cytenticle said:**
> Have a solution for password protected podcasts and rhythmbox

When you add the podcast feed add it in this format

```
http://username:password@podcasturl.com
```
for example

your username - user
your password - password
podcasturl - secretpodcast.com/podcast.xml

the way you would add the feed is -

```
http://user:password@secretpodcast.com/podcast.xml
```

Hope that helps - worked for me.

---

### Post by aaronmcadam on 2011-05-09
Hi found the solution for adding a username that's an email, you URL encode the @ symbol! Like this: ```
http://user%40user.com:password@podcast.rss
```

---

