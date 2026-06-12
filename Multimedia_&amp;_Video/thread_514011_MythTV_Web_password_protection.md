---
title: "MythTV Web password protection"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by SadaraX on 2007-07-31
I have successfully setup MythTV frontend and backend on my install of Kubuntu/Ubuntu, but I am having trouble setting up password protection on the Apache Web access. Can someone help me with this? I love using mythweb.

---

### Post by Scorpuk on 2007-08-01
First you will need to create your password file. (.htpasswd)


Using an .htpasswd generator, such as : [http://home.flash.net/cgi-bin/pw.pl]("http://home.flash.net/cgi-bin/pw.pl").

With the results from above create a file somewhere that nobody from the outside can get to. I placed mine in /var.

```
sudo gedit /var/htpasswd
```

When you create the file ensure you have a blank line at the end of it. ie:

"name:swfuhsfduoh
 " <- blank line

If you need to add more names just add them to the end and always ensure you have a blank line. ie:

"name:wpofhfowhouhf
name:whwuhgugssrih
 " <- blank line

Once you have the file in the right  place you need to rename it to ".htpasswd" 

```
sudo mv /var/htpasswd /var/.htpasswd
```


Hope that was clear enough :)

Now you need to edit the .htaccess file located in /var/www/mythweb

```
sudo gedit /var/www/mythweb/.htaccess
```


In mine I have the following:

```

AuthType     Basic
AuthName     "MythTV"
AuthUserFile     /var/.htpasswd 
Require     valid-user

```


AuthName is the text to be displayed when the password request window pops up. Try and not to use apostrophes > ' <

AuthUserFile is the file we created above. If you placed it elsewhere please put the full path to it here and the filename. ie /the/place/you/put/the/file/.htpasswd


Hopefully you should now have mythweb password protected. :)

You may or may not need to restart apache, probably not. :D


If it doesnt work at all just re-edit the .htaccess file to the way it was before and you should be back to normal.


Good luck.

---

### Post by SadaraX on 2007-08-01
THANK YOU! This is ***exactly ***what I needed. I modified the default /var/www/mythweb/.htaccess file and include those lines you mentioned. Then I created a password file using _*htpasswd *_and it worked! Someone should make a sticky for this sort of issue. This is very useful.

---

### Post by Nightwalker07 on 2007-10-24
Thanks, exactly what I needed too, got my MythWeb password protected in a matter of minutes thanks to this guide. :)

---

