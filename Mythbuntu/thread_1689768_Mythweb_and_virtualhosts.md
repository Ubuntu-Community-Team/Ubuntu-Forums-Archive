---
title: "Mythweb and virtualhosts"
date: 2011-02-17
forum: Mythbuntu
---

### Post by map7 on 2011-02-17
I'm using Mythbuntu 10.10 and have had mythweb working, but now I'm trying to configure apache as a web server for my Ruby on Rails projects.  

I've setup a virtual host to handle my projects like so:
```
   <VirtualHost *:80>
      ServerName myserver
      DocumentRoot /home/map7/webapps
      <Directory /home/map7/webapps>
         Allow from all       
      </Directory>

        RailsBaseURI /testapp
        <Directory /home/map7/webapps/testapp>
                Options -MultiViews
        </Directory>
   </VirtualHost>
```

When I enter this in my httpd.conf file and restart apache2 I can access my Rails projects by going to [http://myserver/testapp](http://myserver/testapp) and the default 'It works!' message from apache if I go to [http://myserver/](http://myserver/).  The problem is if I go to [http://myserver/mythweb](http://myserver/mythweb) then i get the error '404 Not Found'.

Is there a way to exclude that directory so I can still access mythweb?

---

