---
title: "[SOLVED] [8.04] Upgraded, now mythweb broken."
date: 2008-03-11
forum: Mythbuntu
---

### Post by TehSnarf on 2008-03-11
Did an upgrade from Mythbuntu 7.10 to 8.04 last night, fixed a VNC issue, now when I try to browse MythWeb, it's giving me a "Cannot load page" error. So I did some investigating, and noticed Apache wasn't running, so attempted to manually start. Now I'm getting the error:


```

Syntax error on line 104 of /etc/apache2/sites-enabled/mythweb.conf:
Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configureation

```

So I checked my mythweb.conf file, at line 104-ish:

```

    ############################################################################
    # The following settings relate to PHP config.
    #

        <Files *.php>

        #  These settings are intended for apache 2.x.  If your version of apache
        #  doesn't support php_value, or things like memory_limit aren't working
        #  as expected, then use these settings as examples for your own php.ini
        #  files.
            php_value safe_mode                     0

            php_value memory_limit                  32M

            php_value register_globals              0
            php_value magic_quotes_gpc              0
            php_value file_uploads                  0
            php_value allow_url_fopen               On

            php_value zlib.output_handler           Off
            php_value output_handler                NULL

        # Note: php_flag does not work in older versions of php
            php_flag output_handler                 "NULL"

        </Files>

```

Any idea's where I would start looking in to fixing this?

---

### Post by TehSnarf on 2008-03-11
... If I remove the lines it complains about, apache starts, but I then get a "Index of /mythweb" followed by a listing of what's in the /var/www/mythweb directory. If I click on the php file, it asks me to or save, instead of actually displaying the file (like it would normally).

... And if I browse to [http://USERNAME:PWORD@localhost/mythweb/mythweb.php](http://USERNAME:PWORD@localhost/mythweb/mythweb.php), where USERNAME/PWORD are what I was using in 7.10, it will actually show me a "Database Setup Error" page now. Hmmm... Maybe the security is left over somewhere?

Also tried removing/reinstalling mythweb, to no avail.

---

### Post by superm1 on 2008-03-11
First off, please file a bug.

Next,
Can you please try to remove and purge mythweb, and reinstall it.  See if things resolve themselves.

---

### Post by TehSnarf on 2008-03-11
Not sure what did it, but I did the following:

```

sudo apt-get remove --purge php* apache* mythweb*
sudo rm -rf /etc/apache2
[reboot]
sudo apt-get install apache2-dev php5-dev libapache2-mod-php5 apache2-doc mythweb

```

Opened mythbuntu-control-centre...
--selected Primary Backend, Xubuntu Desktop, Applied

seems to be working now.

---

### Post by p$y on 2008-03-26
Edit: sry, wrong thread

---

### Post by zmerch on 2008-03-27
> **TehSnarf said:**
>  {snip}sudo apt-get install php5-dev libapache2-mod-php5
[/code]

Opened mythbuntu-control-centre...
--selected Primary Backend, Xubuntu Desktop, Applied
seems to be working now.

I'd bet from your previous errors (not recognizing a .php file as being web-based) that your PHP was broken during the MythWeb step of the upgrade... but that's just a guess.

Hope this helps,
Roger "Merch" Merchberger

---

