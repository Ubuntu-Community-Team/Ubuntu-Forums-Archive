---
title: "Error accessing Movies on Mythweb since upgrade to .23"
date: 2010-05-22
forum: Mythbuntu
---

### Post by kyfehr on 2010-05-22
Hi,

I am receiving this error ONLY when trying to access my movie catalog on MythWeb.

Fatal error: Maximum execution time of 30 seconds exceeded in /usr/share/mythtv/mythweb/includes/translate.php  on line 142

I have gotten this since .23 upgrade. Before everything was fine. The only other change is that I have moved all my movies into Storage Groups, so if there is something I missed in settings for MythWeb to find them, I would be grateful if pointed in the right direction. Right now it is a pain to change Parental levels in mythfrontend.

Kyfehr

---

### Post by kyfehr on 2010-05-30
anyone know what to do? I tried to reinstal and that didn't fix it

---

### Post by hillcountry on 2010-06-01
I have a slower system (Atom 330 1.6) and am having the same issue with 856 current recordings. 

From the error message I assume this is simply a performance (30 second) timeout error. 

As such I've found two workarounds that work on my system. 

With mythweb installed goto "mythweb > Settings > TV"
aka [http://your-mythtv-ip-address-here/mythweb/settings/tv](http://your-mythtv-ip-address-here/mythweb/settings/tv)

Option 1> When I only had ~700 recordings, turning off "Show pixmaps" apparently made the page generation fast enough to finish in under 30 seconds.

With ~900 recordings I again encountered the error, and have now turned pixmaps back on, but limited the number of recordings shown to 100 per page (option 2).

Option 2> Change "Page recorded programs" from "Off" to "100" - or perhaps a smaller number if using a slower system. 

After either change be sure to click the "save" button at the bottom of the page, wait a few seconds, then reload your "Recorded Programs" page. 

Hopefully someone more knowledgeable will chime in on how to adjust or remove the 30 second page generation limit/timeout value. 

In the meantime, I hope this helps. :)

Best of luck to you.

---

### Post by hillcountry on 2010-06-01
Actually I think I've found a solution... 

First I made a copy of my php.ini
*sudo cp /etc/php5/apache2/php.ini /etc/php5/apache2/php.ini.original*

Then I edited the php.ini
*sudo nano /etc/php5/apache2/php.ini*

changing the following line under "Resource Limits" 
*max_execution_time = 30     ; Maximum execution time of each script, in seconds*
to 
*max_execution_time = 300     ; Maximum execution time of each script, in seconds*
(then exit with ctl-x to save)

then I restarted apache with
*sudo /etc/init.d/apache2 restart*

Mythweb's "Recorded Programs" page can now list all ~860 listings with pixmaps... in about 35 seconds. 

Hope this helps.
- hillcountry

---

