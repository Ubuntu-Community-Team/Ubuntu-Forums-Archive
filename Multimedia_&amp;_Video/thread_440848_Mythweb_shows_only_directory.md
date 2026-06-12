---
title: "Mythweb shows only directory"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by brandon_r87 on 2007-05-12
Hello,

I have a working install of MythTV on kubuntu feisty.  I had also installed mythweb, which worked once, but now only shows a directory listing at [http://localhost/mythweb]("http://localhost/mythweb").  I found the folder that it points to, which is /usr/share/mythtv/mythweb.  I also tried opening mythweb.php, which is in the directory, but it only gives me the option of saving it.  I've uninstalled and reinstalled mythweb several times, but I continue to get this error.

Brandon

---

### Post by michwill on 2007-05-12
I'm having similar problem here:  [http://ubuntuforums.org/showthread.php?t=440798&highlight=mythweb](http://ubuntuforums.org/showthread.php?t=440798&highlight=mythweb)

Please post in both places upon finding a fix.  Thanks.

---

### Post by jkays94 on 2007-05-22
You might want to see this thread:
[http://ubuntuforums.org/showthread.php?t=418253&]("http://ubuntuforums.org/showthread.php?t=418253&")

---

### Post by brandon_r87 on 2007-05-22
I followed the instructions from [http://ubuntuforums.org/showthread.php?t=418253&]("http://ubuntuforums.org/showthread.php?t=418253&") but they didn't help.  Here they are for anyone else:

> **Sloebervos said:**
> Hi,

I had the same problem after upgrading my server from Edgy to Feisty. I just found the solution on the mythtv wiki:

Edit the /var/www/mythweb/.htaccess file and comment out these 3 lines:

        php_value zlib.output_handler           Off
        php_value zlib.output_compression       16384
        php_value zlib.output_compression_level 4

Restart apache and it should work (tested with IE 7).

My problem is different from the problem they're talking about, which is only Internet Explorer can't use mythweb.  I can't use mythweb with any browser, it simply shows a directory when I go to [http://localhost/mythweb](http://localhost/mythweb)

Edit:  OK, my problem was with apache2.  It wasn't starting correctly.  It would give me an error, saying port 80 was already in use.  So I stopped apache, started apache2, then restarted apache.  Do I really need apache and apache2, and is there a way to make sure apache2 starts first?

---

### Post by FXFman1209 on 2007-06-19
No, you do not need apache. Only apache2. You can use synaptic or something to uninstall the old apache.

---

