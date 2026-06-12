---
title: "OpenShowCenter install problem"
date: 2010-10-24
forum: Multimedia Software
---

### Post by dangerjunkie2002 on 2010-10-24
Hi,

I'm trying to install Openshowcenter on my Lucid-amd64 machine. I think I've done everything the instructions said and adapted them to Ubuntu OK.

When I visit [http://localhost:8000/](http://localhost:8000/) on the server machine with Firefox I see the elements of the GUI but there are lots of PHP error messages all over the page. These also appear in the Openshowcenter log:

[INDENT][I][24-Oct-2010 21:55:00] PHP Notice:  Undefined variable: zip in /var/www/openshowcenter/system/viewfunctions.php on line 46
[24-Oct-2010 21:55:00] PHP Notice:  Undefined variable: zip in /var/www/openshowcenter/system/viewfunctions.php on line 46
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: mid in /var/www/openshowcenter/system/viewfunctions.php on line 95
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: help in /var/www/openshowcenter/system/viewfunctions.php on line 96
[24-Oct-2010 21:55:00] PHP Notice:  Undefined variable: zip in /var/www/openshowcenter/system/viewfunctions.php on line 46
[24-Oct-2010 21:55:00] PHP Notice:  Undefined variable: zip in /var/www/openshowcenter/system/viewfunctions.php on line 46
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: mid in /var/www/openshowcenter/system/viewfunctions.php on line 55
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: help in /var/www/openshowcenter/system/viewfunctions.php on line 56
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index:  in /var/www/openshowcenter/system/viewfunctions.php on line 59
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: mid in /var/www/openshowcenter/system/viewfunctions.php on line 55
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: help in /var/www/openshowcenter/system/viewfunctions.php on line 56
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index:  in /var/www/openshowcenter/system/viewfunctions.php on line 59
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: mid in /var/www/openshowcenter/system/viewfunctions.php on line 55
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: help in /var/www/openshowcenter/system/viewfunctions.php on line 56
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index:  in /var/www/openshowcenter/system/viewfunctions.php on line 59
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: mid in /var/www/openshowcenter/system/viewfunctions.php on line 55
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index: help in /var/www/openshowcenter/system/viewfunctions.php on line 56
[24-Oct-2010 21:55:00] PHP Notice:  Undefined index:  in /var/www/openshowcenter/system/viewfunctions.php on line 59[/I][/INDENT]

If I go to other pages like "Music" I can see lists of media from the HD so some of it is working. These pages are also littered with PHP errors similar to those above.

I've never worked with Apache or PHP before so I'm sure there's something I've done wrong. I'm assuming there's some pre-requisite I haven't installed or permission that is wrong. I'd be really grateful if someone would give me a nudge in the right direction please.

Thanks,
Paul.

---

