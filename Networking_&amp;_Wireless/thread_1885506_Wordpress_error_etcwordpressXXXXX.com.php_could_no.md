---
title: "Wordpress error /etc/wordpress/XXXXX.com.php could not be found"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by sffvba[e0rt on 2011-11-23
Hi,

In an ongoing saga I am trying to host Wordpress on my own little home server (Ubuntu 10.04 LAMP installed + Wordpress).

Due to not having a static IP and also having port 80 closed by the ISP I have had to do some "work-arounds" to get to where I am now (which might be part of the problem I am having).

At the moment my domain nlsthzn.com is being managed by DynDNS as I don't have a static IP.  I have set up [www.nlsthzn.com](www.nlsthzn.com) to map to nlsthzn.com:13555 on dynDNS cause port 80 is closed by ISP.  This same port I mapped to 80 on my router.

So when browsing [www.nlsthzn.com](www.nlsthzn.com) I get the apache default page.
From my home network if I go to [www.nlsthzn.com/wordpress](www.nlsthzn.com/wordpress) I get my blog I installed and have been configuring.

Problem is, as soon as anybody outside of my home network tries to access [www.nlsthzn.com/wordpress/](www.nlsthzn.com/wordpress/) they get:

**/etc/wordpress/config-nlsthzn.com.php could not be found. The file is either not readable by this process or does not exist.  Please check if /etc/wordpress/config-nlsthzn.com.php exists and contains the right password/username.**

So now I am not sure where I messed up... any suggestions welcome :D



Regards
404

---

### Post by Dangertux on 2011-11-23
> **not found said:**
> Hi,

In an ongoing saga I am trying to host Wordpress on my own little home server (Ubuntu 10.04 LAMP installed + Wordpress).

Due to not having a static IP and also having port 80 closed by the ISP I have had to do some "work-arounds" to get to where I am now (which might be part of the problem I am having).

At the moment my domain nlsthzn.com is being managed by DynDNS as I don't have a static IP. I have set up [www.nlsthzn.com](www.nlsthzn.com) to map to nlsthzn.com:13555 on dynDNS cause port 80 is closed by ISP. This same port I mapped to 80 on my router.

So when browsing [www.nlsthzn.com](www.nlsthzn.com) I get the apache default page.
From my home network if I go to [www.nlsthzn.com/wordpress](www.nlsthzn.com/wordpress) I get my blog I installed and have been configuring.

Problem is, as soon as anybody outside of my home network tries to access [www.nlsthzn.com/wordpress/](www.nlsthzn.com/wordpress/) they get:

/etc/wordpress/config-nlsthzn.com.php could not be found. The file is either not readable by this process or does not exist. Please check if /etc/wordpress/config-nlsthzn.com.php exists and contains the right password/username.

So now I am not sure where I messed up... any suggestions welcome



Regards
404

Hey sorry I didn't respond to this earlier, I meant to.

However, When I visited the site earlier I got

```

Database Connection Refused

```

In conjunction with what you're saying it sounds like your database credentials may be wrong in your config file. I'm really not sure where you messed up either, as you said you did some workarounds. 

I noticed you installed Wordpress from the repos, it's a royal pain to manage that way as it installs files all over the place. I would recommend installing it manually, for two reasons. One it's an up to date version (there are always vulnerabilities in WP) and two it's a LOT easier to set up.

Incidentally here is a quick one shot guide I put together about installing it manually maybe it is helpful, even if you stick with repos, it might give you an idea of where things went wrong. I'm willing to bet though the database credentials are wrong in your config file.

[http://dangertux.wordpress.com/tutorials/installing-wordpress-cms-on-ubuntu/](http://dangertux.wordpress.com/tutorials/installing-wordpress-cms-on-ubuntu/)

---

### Post by sffvba[e0rt on 2011-11-23
Hi Dangertux,

Thanks for all the info.  Turns out I missed the step of actually creating the config file :redface: (not sure how I missed that step).

When I made it I got it to work (and then when installing a new theme I got the dreaded Wordpress White Screen of Death).

So as this is as much for learning than it is to host a blog I am again slowly re-doing everything and setting it up again :) - I will have a look at your blog post, thanks for that.


Regards
404

---

### Post by Dangertux on 2011-11-23
> **not found said:**
> Hi Dangertux,

Thanks for all the info.  Turns out I missed the step of actually creating the config file :redface: (not sure how I missed that step).

When I made it I got it to work (and then when installing a new theme I got the dreaded Wordpress White Screen of Death).

So as this is as much for learning than it is to host a blog I am again slowly re-doing everything and setting it up again :) - I will have a look at your blog post, thanks for that.


Regards
404


Glad it's working out for you, WP is a lot of fun enjoy it :-)

---

### Post by narcisgarcia on 2013-03-01
You need to see which local configuration file is there:
```
sudo ls /etc/wordpress/
```
For example, if the file was **config-localhost.php** , then this command solves the problem with any visitor from any network:
```
sudo ln -s /etc/wordpress/config-localhost.php /etc/wordpress/config-default.php
```
(this is because at last wp-config.php looks for config-default.php)

---

