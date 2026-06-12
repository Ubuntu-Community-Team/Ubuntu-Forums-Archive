---
title: "Adding Trac to existing Apache2 virtual host."
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by SailBlue5 on 2012-11-05
I currently have apache2 running from a mythtv/mythweb install. This made two config files available in sites-enabled. One of them ("default-mythbuntu") has the VirtualHost directive and seems like a normal VirtualHost file (except a change to the directory index). There is also a mythweb.conf file that only has directives and sets various variables for mythweb, it does not specify a virtualhost. I want to host a trac site as well on this virtualhost (just a different directory under the www/). According to this site: [http://trac.edgewall.org/wiki/TracOnUbuntu](http://trac.edgewall.org/wiki/TracOnUbuntu) there are some setting I need to set for the Trac site. They give me directions for making a VirtualHost, but I think I should use the current VirtualHost and just add the directives (I'll need to change the default location they point to from the site above to just point to the trac location). Where should I put these directives? Can I make a Trac.conf with just the settings for Trac and enable it, or do I need to put them in the default-mythbuntu file? I don't like the later because it doesn't separate out the Trac configs. How does Apache know that the mythweb (and the trac.conf I want to make) belong to the virtualhost defined in the default-mythbuntu? It is the only virtualhost that is being defined on my system if that matters.

---

### Post by SailBlue5 on 2012-11-06
I did as I suggested, I made a trac.conf (filename shouldn't mater) and put all the all the <Location> directives (and what was inside it) in to that file and enabled it.  I needed to modify the locations on the file system my trac enviorment was but that was easy.  Things seem to be working now.

---

