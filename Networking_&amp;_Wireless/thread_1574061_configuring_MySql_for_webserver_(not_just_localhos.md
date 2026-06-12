---
title: "configuring MySql for webserver (not just localhost)"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by Lakeside5 on 2010-09-13
I have a new 10.04 install and then installed LAMP, then tested the php etc. I followed the directions here: [http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)  which went great but then got to the 'configure MySQL' part and now have a question.  The writer wants to use his server for development purposes only, which is also what I will be using mine for, most of the time BUT I also want to 'have my site out there' sometimes for friends to see and give advice on so...how would I configure MySql for a server that's actually serving files to the public (webhosting) instead of just localhost? Any help appreciated, thanks.

---

### Post by Lakeside5 on 2010-09-13
I actually have another related question/problem, if that's allowed :)  I followed the same tutorial to install phpmyadmin: [http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/) , followed the advice to install it, even did it twice, bu I still get the error message when I enter in the address bar  [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  NOT FOUND the requested url phhpmyadmin was not found ont his server  Apache/2/2/14 server at localhost port 80.  I guess I have forgotten something, maybe a configuration in my router to do with port 80?  thanks for any help.*SOLVED* Sorry, did it again lol I read further down the tutorial in the comments and found a soluting someone else had, it was to add a line at the bottom of the apache2.conf file. Now I can access phpmyadmin :)

---

### Post by BkkBonanza on 2010-09-13
In a typical situation like yours Mysql would be connected to by only the local PHP processes you have. It wouldn't be accessed by end users directly via the net. It "can" be done that way but not using a browser. It would be some software that uses low-level "client" access to the database. So typically you do not want to configure Mysql for direct net access. 

BUT you do want to make your web server available to the net (not mysql). And the way you do that is by forwarding port 80 on your router to the server IP. For specific info on your router model google "make/model# port forward", and you should find a guide for that. It's just a fairly simple setting usually. This will allow net access by IP number. For a domain name you either need to register one and/or setup a dynamic name such as available via DynDns.com (as one example).

Phpmyadmin only needs localhost access to Mysql. Regarding not getting the the phpmyadmin page you should check the /var/www directory and make sure permissins are correct and that the phpmyadmin directory is there. 

----Aside----
I don't think you want all this and just mis-worded the question...
If by some chance you actually do need external access to Mysql (for some remote program), then you would adjust my.cnf to enable listening on a TCP port (usually 3306). If I recall correctly you comment out the "skip networking" line, and make sure it binds to your real IP, not localhost. Also, you would have to port forward from your router for this port. In such a case it usually best to also configure SSL access for security but that is another subject.

---

### Post by Lakeside5 on 2010-09-14
Thanks BkkBonaza, I seem to have phpmyadmin working now, things seem find (crosses fingers) Only issues now are, I think I installed Joomla wrong as there doesn't seem to be a Joomla database when I go into phpmyadmin, and the joomla website looks quite wrong! I shall address that problem on the Joomla forums I guess though, and will look into your great advice if/when I need to do what you suggest, such as remote access etc. so thanks again.

---

