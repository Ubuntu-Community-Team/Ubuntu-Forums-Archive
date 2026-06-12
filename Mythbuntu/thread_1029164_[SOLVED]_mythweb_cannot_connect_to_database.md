---
title: "[SOLVED] mythweb cannot connect to database"
date: 2009-01-03
forum: Mythbuntu
---

### Post by iitywygms on 2009-01-03
I messed up my system today but have mostly everything back and running as normal.  (I messed up the database/mysql)
I still have this issue
When accessing mythweb I get.

Not Found

The requested URL /mythweb/ was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch Server at 192.168.2.3 Port 80 

I did a purge of mythweb and reinstalled it.  I went to setup and entered my user and password.  

Still no fix.
Any help?
Thanks

---

### Post by iitywygms on 2009-01-03
bump

---

### Post by ian dobson on 2009-01-04
Hi,

What do you see when you do a ls of the root directory of your web server?
Is apache/web server running?
What do you see in the error logs on the webserver?

Alot of questions I know, but without any more information it's had to say whats wrong.

Regards
Ian Dobson

---

### Post by iitywygms on 2009-01-04
> **ian dobson said:**
> Hi,

What do you see when you do a ls of the root directory of your web server?
Is apache/web server running?
What do you see in the error logs on the webserver?

Alot of questions I know, but without any more information it's had to say whats wrong.

Regards
Ian Dobson

Hi and thank you.

Question 1.  I do not know what that means or how to check.  Please explain how to check.

Question 2.  kevin@mythtv:~$ sudo /etc/init.d/apache2 restart
[sudo] password for kevin: 
 * Restarting web server apache2                                         [ OK ]

So I assume it is running okay.

Question 3.  Where should I check?

I really appreciate your help.  When I "fix" something I am basically copying and pasting from what I find on the net.  I wish I knew what I was doing but sadly I do not.  But, I am learning.

---

### Post by newlinux on 2009-01-04
what is in your:

/etc/apache2/sites-enabled/mythweb.conf

file?

Do you you have a
/var/www/mythweb directory?

---

### Post by iitywygms on 2009-01-04
> **newlinux said:**
> what is in your:

/etc/apache2/sites-enabled/mythweb.conf

file?

Do you you have a
/var/www/mythweb directory?

/etc/apache2/sites-enabled/mythweb.conf


#
# Apache configuration directives for MythWeb.  Please read INSTALL for setup
# requirements and troubleshooting, along with the comments in this file.
#

############################################################################
# If you intend to use authentication for MythWeb (see below), you will
# probably also want to uncomment the following rules, which disable
# authentication for MythWeb's download URLs so you can properly stream
# to media players that don't work with authenticated servers.
#
#    <LocationMatch .*/pl/stream/[0-9]+/[0-9]+>
#        Allow from all
#    </LocationMatch>
#
#    <LocationMatch .*/music/stream.php>
#        Allow from all
#    </LocationMatch>


#
# CHANGE THIS PATH TO MATCH YOUR MYTHWEB INSTALLATION DIRECTORY!  e.g.
#
#    /var/www
#    /home/www/htdocs
#    /var/www/html/mythweb
#    /srv/www/htdocs/mythweb
#
    <Directory "/var/www/mythweb/" >

    ############################################################################
    # I *strongly* urge you to turn on authentication for MythWeb.  It is disabled
    # by default because it requires you to set up your own password file.  Please
    # see the man page for htdigest and then configure the following four directives
    # to suit your authentication needs.
    #
    AuthType           Digest
    AuthName           "MythTV"
    AuthUserFile       /etc/mythtv/mythweb-digest
    Require            valid-user
    BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
    Order              allow,deny
    Satisfy            any
    #
    #  * If you're running Apache earlier than 2.2, you will need to use
    #    the AuthDigestFile command instead of AuthUserFile (3rd line above).
    #
    ############################################################################
    # Some special instructions for the MythWeb controller files
    #
        <Files mythweb.*>

        #
        # Use the following environment settings to tell MythWeb where you want it to
        # look to connect to the database, the name of the database to connect to, and
        # the authentication info to use to connect.  The defaults will usually work
        # fine unless you've changed mythtv's mysql.txt file, or are running MythWeb on
        # a different server from your main backend.  Make sure you have mod_env enabled.
        #
            setenv db_server        "localhost"
            setenv db_name          "mythconverg"
            setenv db_login         "mythtv"
            setenv db_password      "deletedbymeforthisforum"

        #
        # By default, MythWeb uses the hostname program to look up the hostname of the
        # machine it runs on.  If this reports incorrect data, or you run MythWeb on a
        # machine without the hostname program, set this to your current hostname.
        #
        #   setenv hostname         "my_mythbox"
        #

        # By default, php will always search the current directory for include files,
        # but if you wish to install these directories outside of the current path
        # (eg. for security reasons), set this variable to the directory that
        # contains the directories like languages and templates.  eg.
        #
        #   setenv include_path      "/usr/share/mythweb"

        # If you want MythWeb to email php/database errors (and a backtrace) to you,
        # uncomment and set the email address below.
        #
        #   setenv error_email       "mythweb_errors@example.com"
        #

        # If your local file system is something other than UTF-8, set this variable
        # so that the music and video portions of MythWeb can provide proper links
        # to your downloadable files.
        #
        #   setenv fs_encoding       "ISO-8859-1"

        </Files>

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

    ############################################################################
    # The settings below relate specifically to mod_rewrite and the rewrite
    # engine used to make the MythWeb user experience a little easier to deal
    # with by simplifying the URLs needed to access the various sections.  Do
    # not touch these settings unless you really know what you're doing..
    #

    # Turn on the rewrite engine
        RewriteEngine  on

    # If MythWeb is installed outside of the document root (eg. using Alias) then
    # you will need to set this directive to the base URL that MythWeb is visible
    # from externally.  If you do not, the web server will return 'not found'.
    #    RewriteBase    /mythweb

    # Skip out early if we've already been through rewrites,
    # or if this is a /css/, /js/ or /cache/ directory request.
        RewriteRule    ^(css|data|images|js|themes|skins|README|INSTALL|[a-z_]+\.(php|pl))(/|$)     -     [L]

    # Redirect /pl/ requests to the perl cgi handler.
        RewriteRule     ^(pl(/.*)?)$            mythweb.pl/$1               [QSA,L]

    # Redirect most of the remaining URL requests to the main mythweb script.
    # It will then handle any requests given to it.
        RewriteRule     ^(.+)$                  mythweb.php/$1              [QSA,L]

    # If you're experiencing trouble with the previous two lines in your copy of
    # apache, you could instead use something like:
    #    RewriteRule     ^(pl(/.*)?)$           mythweb.pl?PATH_INFO=/$1    [L,QSA]
    #    RewriteRule     ^(.+)$                 mythweb.php?PATH_INFO=/$1   [L,QSA]

    # Catch anything else that comes through and send it to mythweb.php with no parameters.
        RewriteRule     ^(.*)$                  mythweb.php                 [QSA,L]

    ############################################################################
    # You really shouldn't need to edit anything below this line, so please
    # don't unless you know what you're doing.
    #

    # Allow .htaccess to override whatever it wants from the server config.
        AllowOverride   All

    # Allow browsers to follow symlinks that point outside of the web document
    # tree.  This is how we access music, videos, etc.
        Options         FollowSymLinks

    # MythTV now uses the correct file suffix for mpeg files, so all .nuv files
    # should actually be NuppleVideo.  However, apache probably doesn't know what
    # those are, so we should tell it.
        AddType video/nuppelvideo   .nuv

    # Specify the MIME type for favicon.ico in case the server configuration
    # doesn't or in case the server configuration uses the IANA-approved MIME type
    # (image/vnd.microsoft.icon)--which most browsers won't recognize.
        AddType image/x-icon        .ico

    # Enable mod_deflate.  This works MUCH more reliably than PHP's built-in
    # gzip/Zlib compressors.  It is disabled here because many distros seem not
    # to enable mod_deflate by default, but I strongly recommend that you
    # enable this section.
    #
    #    BrowserMatch ^Mozilla/4 gzip-only-text/html
    #    BrowserMatch ^Mozilla/4\.0[678] no-gzip
    #    BrowserMatch \bMSIE !no-gzip !gzip-only-text/html
    #
    #    AddOutputFilterByType DEFLATE text/html
    #    AddOutputFilterByType DEFLATE text/css
    #    AddOutputFilterByType DEFLATE application/x-javascript

    # This is helpful for mod_deflate -- it prevents proxies from changing
    # the user agent to/from this server, which can prevent compression from
    # being enabled.  It is disabled here because many distros seem not to
    # enable mod_headers by default, but I recommend that you enable it.
    #
    #    Header append Vary User-Agent env=!dont-vary

    # Set up the perl handler so we can stream properly.  Do not use mod_perl
    # because it has a tendency to hold onto child processes, which causes
    # problems if the browser closes on an in-progress stream.
    #
        <Files *.pl>
            SetHandler cgi-script
            Options +ExecCGI
        </Files>

    </Directory>


Do you you have a
/var/www/mythweb directory?

yes

kevin@mythtv:/var/www/mythweb$ ls
data      js                   mythweb.conf.lighttpd  objects
includes  modules              mythweb.php            skins
INSTALL   mythweb.conf.apache  mythweb.pl

---

### Post by murbanci on 2009-01-04
Are you able to connect to id if you turn off authentication?  This is the only difference I can find between my config file and yours.  Maybe try turning this off and then see if it works.

---

### Post by newlinux on 2009-01-04
Yep, that config looks okay. Can you access the root apache page ([http://nameorIPofyourmythwebmachine)?](http://nameorIPofyourmythwebmachine)?) Maybe it's an apache problem... also, what are the permissions on /var/www/mythweb?

---

### Post by iitywygms on 2009-01-04
This is what I type in the address bar ([http://192.168.2.3/](http://192.168.2.3/)) without quotes.
I get the same results.

How to I turn off authentication?


kevin@mythtv:/var/www$ ls -l
total 8
-rw-rw-rw- 1 root mythtv 21 2009-01-03 12:41 htpasswd
-rw-rw-rw- 1 root mythtv 45 2009-01-03 14:02 index.html
lrwxrwxrwx 1 root root   25 2009-01-03 19:34 mythweb -> /usr/share/mythtv/mythweb
kevin@mythtv:/var/www$ 

I appreciate the help.

---

### Post by iitywygms on 2009-01-05
bump

---

### Post by newlinux on 2009-01-05
> **iitywygms said:**
> This is what I type in the address bar ([http://192.168.2.3/](http://192.168.2.3/)) without quotes.
I get the same results.

How to I turn off authentication?


kevin@mythtv:/var/www$ ls -l
total 8
-rw-rw-rw- 1 root mythtv 21 2009-01-03 12:41 htpasswd
-rw-rw-rw- 1 root mythtv 45 2009-01-03 14:02 index.html
lrwxrwxrwx 1 root root   25 2009-01-03 19:34 mythweb -> /usr/share/mythtv/mythweb
kevin@mythtv:/var/www$ 

I appreciate the help.

You must get some different message, because it shouldn't be saying it can't find /mythweb/ if you are asking for root. So are you saying the message is the same except for that part? Since your root Apache web site doesn't seem to work, I'm leaning towards an apache problem, but we'll see...

You can turn off authentication in mythbuntu-control-centre or comment out these lines in your mythweb.conf:
```

AuthType Digest
AuthName "MythTV"
AuthUserFile /etc/mythtv/mythweb-digest
Require valid-user
BrowserMatch "MSIE" AuthDigestEnableQueryStringHack=On
Order allow,deny
Satisfy any

```
and restart apache

```

sudo /etc/init.d/apache2 restart
```

---

### Post by iitywygms on 2009-01-05
"You must get some different message, because it shouldn't be saying it can't find /mythweb/ if you are asking for root. So are you saying the message is the same except for that part? Since your root Apache web site doesn't seem to work, I'm leaning towards an apache problem, but we'll see..."

Yes, you are correct.  It is the same except for that part.  (I should be more careful when I respond)

If authentication means require password, then I have tried that, several times.  I will try again when I get home just to be sure.

I agree, I think it is a apache problem.  I just have no idea how to troubleshoot.  I am not even sure what questions I should be asking.

Again, thanks for the help.

---

### Post by iitywygms on 2009-01-05
Okay, I turned off authentication and tried again, same result.
What next thing should I try next?

Thanks

---

### Post by iitywygms on 2009-01-05
Fixed!

I followed this thread

[http://ubuntuforums.org/showthread.php?t=813725](http://ubuntuforums.org/showthread.php?t=813725)

did this

sudo apt-get remove --purge $(dpkg -l apache* | grep ii | awk '{print $2}') && sudo apt-get install apache2

then this

sudo apt-get install mythweb

All good now.
Thanks to all for the help.

---

