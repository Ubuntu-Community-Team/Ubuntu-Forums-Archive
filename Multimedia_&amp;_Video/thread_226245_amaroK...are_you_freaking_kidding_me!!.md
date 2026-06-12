---
title: "amaroK...are you freaking kidding me??!!"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by lonelypauly on 2006-07-31
I've gone from xmms to beep and now to amaroK...holy maceral...are you freaking kidding me??? This blows Winamp away completely...what the hell??? I'm giddy like a school girl...staying up way too late fiddling with this awesome app...yay!  I can't imagine anything else being better than this.

that is all.

---

### Post by bbzbryce on 2006-07-31
I agree amaroK is the most amazing music player there is.  It does tend to use 100% of one of my cores though, it's fine though I have two.  That bugged me a bit on my old computer though when it was updating or something; I'm not entirely sure what it was doing.

---

### Post by adamkane on 2006-07-31
amaroK has radio station and podcast support also.

--------------

Install MySQL and add an amaroK database to maintain large collections:

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

Add amaroK database.

--------------

Install Ruby to enable lyric viewing.

--------------

Install 686 or k7 kernel and kernel-headers to improve Ubuntu performance. You'll need it to run amaroK in the background while you're working.

---

### Post by lonelypauly on 2006-07-31
so when i try and click on a wikipedia link from inside amaroK...i get the message:

"Could not launch the browser

Could not find service kfmclient"

This is a KDE thing no? any possible way to fix that, like configure those links to open with firefox?

---

### Post by scxtt on 2006-07-31
i've used amarok in gnome and  the wiki links worked fine ... of course i had to install a portion of kde-base when i installed amarok ...

---

### Post by ltmon on 2006-07-31
> **lonelypauly said:**
> so when i try and click on a wikipedia link from inside amaroK...i get the message:

"Could not launch the browser

Could not find service kfmclient"

This is a KDE thing no? any possible way to fix that, like configure those links to open with firefox?

It doesn't launch in an external browser, it embeds it inside amarok.

This is why it needs the KDE core: you can't embed gnome stuff inside a KDE app (well not easily).

```

sudo apt-get install kde-base

```

should get it working for you, as long as you don't mind the extra HD space it takes up.

---

### Post by lonelypauly on 2006-07-31
thanks but the command line says "E: Couldn't find package kde-base" 

i went into synaptic but there are dozens of "kde-base" search results...which one am i after?

ALSO...i can't seem to get amaroK to see my iaudio X5L mp3 player...anyone know where i find the mount point info to get amaroK to see my player?  heres a screenshot:

[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/Screenshot.png[/IMG]

---

### Post by ltmon on 2006-08-01
Sorry, that should have been:
```

sudo apt-get install kdebase

```

The version of amarok you have I think does not support much more than just Ipods.  Their media device support has been much improved and expanded in more recent builds, but you've got to pretty much compile it yourself to get that functionality at the moment.

You might want to ask on [http://amarok.kde.org](http://amarok.kde.org) (have a look in the wiki and the forums linked from that page).

L.

---

