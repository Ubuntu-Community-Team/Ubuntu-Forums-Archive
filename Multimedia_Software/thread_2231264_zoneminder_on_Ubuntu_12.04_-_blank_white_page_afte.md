---
title: "zoneminder on Ubuntu 12.04 - blank white page after install instructions"
date: 2014-06-24
forum: Multimedia Software
---

### Post by Jemmyn_Buchanan on 2014-06-24
Ubuntu 12.0.4

Installed zoneminder through Ubuntu Software Center following the instructions located here:

[http://www.zoneminder.com/wiki/index.php/Ubuntu_12.04/13.04_Desktop](http://www.zoneminder.com/wiki/index.php/Ubuntu_12.04/13.04_Desktop)

All the dependant services said they were running: apache2, mysql, zoneminder but all I could get is a blank white page in the browser when I went to [http://localhost/zm](http://localhost/zm) or [http://127.0.0.1/zm](http://127.0.0.1/zm)

Finally found the issue here, the only change I had to make was the path to php.ini was actually /etc/php5/apache2/php.ini

[http://www.zoneminder.com/wiki/index.php/CentOS#Troubleshooting_Blank_Page](http://www.zoneminder.com/wiki/index.php/CentOS#Troubleshooting_Blank_Page)[B]

Troubleshooting Blank Page[/B]

 If everything went ok but when accessing zoneminder's web page at [http://localhost/zm](http://localhost/zm),  the page is blank this means that there is a problem with PHP short  tags. Edit setting short_open_tag in php.ini (/etc/php.ini) and change  it to On. 
 
[LIST]
[*] Restart apache server with: 
[/LIST]
 service httpd restart and you should be up and running.

---

