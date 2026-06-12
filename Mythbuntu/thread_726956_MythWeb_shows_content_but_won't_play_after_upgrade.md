---
title: "MythWeb shows content but won't play after upgrade to 0.21"
date: 2008-03-17
forum: Mythbuntu
---

### Post by daviding on 2008-03-17
i'm a Mythbuntu newbie, and would appreciate some help after the automatic upgrade.

I had Mythbuntu 7.10 working well, and had a few problems figuring out MythWeb.  I finally figured out how to do a symlink to the directory where I'm storing the content (i.e. \home\mythtv\ ), after I realized that \var\www\mythweb\data\recordings\ was on the tiny first partition.

Before I ran Upgrade Manager, I could see the list of Recorded Programs, and when I clicked on the file, the "download" would start.  (I'm doing this all on my local machine, but would like to pull content onto other PCs in the house).

After the upgrade, I now see a PNG of each Recorded Program, and links to an "ASX stream" and a "Direct Download".  Clicking on the "Direct Download" gives a message such as ...

> 1053_20080316230000.mpg does not exist in any recognized storage group directories for this host.

I've been playing around with more symlinks, but don't really know what I'm doing.  Could anyone please help?  Thanks.

---

### Post by sgunther on 2008-03-17
I had a similar problem that was caused by the MythWeb user not being able to use the videos correctly. Try;

Assuming /home/mythtv is the loaction of your mpg files then.....

> sudo chmod 775 /home/mythtv/

It worked for me....  I think this may only affect people not storing their video in the standard Mythbuntu locations.

Let me know if this fixes it for you.

---

### Post by daviding on 2008-03-21
> **sgunther said:**
> ITry;

Assuming /home/mythtv is the loaction of your mpg files then.....

sudo chmod 775 /home/mythtv/


Thanks very much for the help.  (I'm sorry for the slow reply, but I've been travelling, and not close to my machine!)

Using mythweb on the local machine, when I now select the "Direct Download", I the file downloads and plays.  However, everything isn't quite clear, yet.

(a) Selecting "ASX stream" on my local machine brings up a panel to launch "Movie Player", but I then get the message ...

> Totem could not play 'http://192.168.1.21:80/mythweb/pl/stream/1037/1206085800'.  The server refused access to this file or stream

(b) I seem to get a similar message on a remote XP machine, when I start a download from Firefox, and Windows Media Player comes up.

We're getting closer ....

---

### Post by DVoid on 2008-05-02
I had this problem as well - the problem is totem/kaffeine etc can't handle digest level security properly (maybe they will in the future) - so authentication is failing when you launch the media player (Which is why you can download but not stream.

You can fix this by either turning off web security completely, or using basic level security - for the ubuntu and apache dist, this is done by editing the /etc/apache2/sites-enabled/mythweb.conf file.

The easiest way is to just comment out the security entirely:
    #AuthType           Digest
    #AuthName           "MythTV"
    #AuthUserFile       /etc/mythtv/mythweb-digest
    #Require            valid-user
    #BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
    #Order              allow,deny
    #Satisfy            any

Otherwise, you can configure basic security on your server - check out [http://httpd.apache.org/docs/2.2/howto/auth.html](http://httpd.apache.org/docs/2.2/howto/auth.html) to see how to do this for your server.

Hope this helps.

---

### Post by marotoweb on 2009-03-13
```
sudo gedit /etc/apache2/sites-enabled/mythweb.conf
```
Play attention in this lines

```
############################################################################
# If you intend to use authentication for MythWeb (see below), you will
# probably also want to uncomment the following rules, which disable
# authentication for MythWeb's download URLs so you can properly stream
# to media players that don't work with authenticated servers.
#
    <LocationMatch .*/pl/stream/[0-9]+/[0-9]+>
        Allow from all
    </LocationMatch>

    <LocationMatch .*/music/stream.php>
        Allow from all
    </LocationMatch>


```

---

