---
title: "Mythweb/MythVideo reports 500 Internal server error using Firefox for MP4"
date: 2013-08-18
forum: Mythbuntu
---

### Post by nhtrader on 2013-08-18
MythTV v0.26.1
ubuntu 12.0.4.2 LTS (x86_64)
Firefox 23.0 with addon: HTTP Live Headers
VLC plugin 2.0.8 Twoflower installed

I'm trying to view a *.mp4 movie created with Handbrake 0.9.9 rev0 using Mythweb's MythVideo, but nothing happens. Why does Firefox display the error message "File not found" and the HTTP response header reports "HTTP/1.0 500 Internal Server Error" ?
Why can't Firefox play an *.mp4 movie?


Here are the headers from the HTTP request using Firefox as the webbrowser:

[http://10.10.10.10/mythweb/video/stream?Id=1](http://10.10.10.10/mythweb/video/stream?Id=1)

GET /mythweb/video/stream?Id=1 HTTP/1.1
Host: 192.168.0.58
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:23.0) Gecko/20100101 Firefox/23.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
DNT: 1
Referer: [http://10.10.10.10/mythweb/video](http://10.10.10.10/mythweb/video)
Cookie: mythweb_id=tj8g1us77pp3331ohn1m54i664
Connection: keep-alive

HTTP/1.0 500 Internal Server Error
Date: Mon, 19 Aug 2013 01:24:07 GMT
Server: Apache/2.2.22 (Ubuntu)
X-Powered-By: PHP/5.3.10-1ubuntu3.7
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Pragma: no-cache
Content-Disposition: filename="mymovie.mp4"
Status: mp4
Connection: close
Content-Type: video/mp4


BTW, the update released today v0.26.1 is still propagating a problematic PHP script. It contains 2 mistakes.
 The script containing the mistakes is /usr/share/mythtv/mythweb/modules/video/stream.php
 1. There is a typo with the line 52: the word "application" is misspelled
... original code:  $mime = 'applicatoin/octet-stream'; (semi-colon)
 ... it should be revised to: $mime = 'application/octet-stream';
 2. the code on line 23 doesn't work as intended using PHP/5.3.10-1ubuntu3.7 ( which is the version of php that was installed with a standard install of Myth v0.25 and then later upgraded to v0.26)
... original code: switch  (substr($fname, strrpos($fname, '.'))) {
 ... it should be revised to:  (substr($fname, strrpos($fname, '.')+1)) {

 This change can be verified by noticing that the HTTP request header changes from Content-Type: application/octet-stream to Content-Type: video/mp4 when the revised code is applied when attempting to view mp4 content.


For newbies, if you make these changes here are the commands:
Edit php script as root: sudo su
Edit php script: pico /usr/share/mythtv/mythweb/modules/video/stream.php (apply changes to code, then exit and save)
Restart apache webserver: /etc/init.d/apache2 restart
Now select an mp4 movie from Mythweb/MythVideo and view headers. You should now see the Content-Type changed from the misspelled type applicatoin/octet to video/mp4.

---

### Post by nhtrader on 2013-09-10
MythTV v0.26.1-14

I figured out how to stop getting the "500 Internal Server Error" using Firefox with the help of Andrew Waldram. Sadly, the new update 0.26.1-14 didn't update the critical stream.php file so you'll need to edit this file along with several others.

I finally got FireFox to serve up a *.mp4 and *.m4v movie while using password protection, but only after I make the following alterations to three files and creating one additional file. Below are the files and their contents, or the changes that I made to them. The contents are posted so that you can compare them to your files.


1. stream.php - this required 4 changes.
EDIT command: sudo pico /usr/share/mythtv/mythweb/modules/video/stream.php <E>

Here's the contents of my stream.php
```

<?php
/**
 * Stream a music file
 *
 * @license     GPL
 *
 * @package     MythWeb
 * @subpackage  Music
/**/

// Yes, a db connection
    global $db;

// Pull video ID
    $vid_id = $_GET['Id'];

// Get filename
    list($fname) = $db->query_row('SELECT filename
                                     FROM videometadata
                                    WHERE intid = ?', $vid_id);

// Mime type
// M20130910
       switch (substr($fname, strrpos($fname, '.')+1)) {
        case 'mpg':
        case 'mpeg':
            $mime = 'video/mpeg';
            break;
        case 'mp4':
            $mime = 'video/mp4';
            break;
        // M20130910
        case 'm4v':
            $mime = 'video/x-m4v';
            break;
        case 'ogg':
        case 'ogm':
        case 'ogv':
            $mime = 'video/ogg';
            break;
        case 'qt':
            $mime = 'video/quicktime';
            break;
        case 'webm':
            $mime = 'video/webm';
            break;
        case 'mkv':
            $mime = 'video/x-matroska';
            break;
        case 'wmv':
            $mime = 'video/x-ms-wmv';
            break;
        case 'flv':
            $mime = 'video/x-flv';
            break;
        default:
        // M20130910
            $mime = 'application/octet-stream';
    }
    header('Content-Type: '.$mime);

// N20130910 - code from Andrew Waldram
    if (ob_get_level()) {
    ob_end_clean();
    }

// Send the filename
    header('Content-Disposition: filename="'.$fname.'"');

// Send data via the backend
    $Master_Host = setting('MasterServerIP');
    $port = _or(get_backend_setting('BackendStatusPort', $Master_Host),
                get_backend_setting('BackendStatusPort'));
    if (stripos($Master_Host,':') !== false) {
        $Master_Host = '['.$Master_Host.']';
    }
    readfile("http://$Master_Host:$port/Content/GetVideo?Id=".$vid_id);

// Nothing else to do
    exit;

```

2. create this file: /usr/share/mythtv/mythweb/modules/stream/stream_m4v.pl
COPY command: sudo cp /usr/share/mythtv/mythweb/modules/stream/stream_mp4.pl /usr/share/mythtv/mythweb/modules/stream/stream_m4v.pl <E>
EDIT command: sudo pico /usr/share/mythtv/mythweb/modules/stream/stream_m4v.pl
change all occurrences of mp4 to m4v

Also change File type to:
    my $type   = 'video/x-m4v';
    my $suffix = '.m4v';

save changes and exit

3. change this file: /usr/share/mythtv/mythweb/modules/stream/handler.pl
insert code to recognize m4v
EDIT command: sudo pico /usr/share/mythtv/mythweb/modules/stream/handler.pl
here's the contents of my file:
```

#!/usr/bin/perl
#
# MythWeb Streaming/Download module
#
#

# Necessary constants for sysopen
    use Fcntl;

# Other includes
    use Sys::Hostname;

    require "modules/$Path[0]/tv.pl";

    unless ($filename) {
        print header(),
              "$basename does not exist in any recognized storage group directories for this host.";
        exit;
    }

# ASX mode?
    if ($ENV{'REQUEST_URI'} =~ /\.asx$/i) {
        require "modules/$Path[0]/stream_asx.pl";
    }
# Flash?
    elsif ($ENV{'REQUEST_URI'} =~ /\.flvp$/i) {
        require "modules/$Path[0]/stream_flvp.pl";
    }
    elsif ($ENV{'REQUEST_URI'} =~ /\.flv$/i) {
        require "modules/$Path[0]/stream_flv.pl";
    }
# Mpeg4?
    elsif ($ENV{'REQUEST_URI'} =~ /\.mp4$/i) {
        require "modules/$Path[0]/stream_mp4.pl";
    }
# M4V?
    elsif ($ENV{'REQUEST_URI'} =~ /\.m4v$/i) {
        require "modules/$Path[0]/stream_m4v.pl";
    }
# Raw file?
    else {
        require "modules/$Path[0]/stream_raw.pl";
    }

###############################################################################

# Escape a parameter for safe use in a commandline call
    sub shell_escape {
        $str = shift;
        $str =~ s/'/'\\''/sg;
        return "'$str'";
    }

# Return true
    1;


```

4. make changes to file: /etc/apache2/sites-available/mythweb.conf
EDIT command: sudo pico /etc/apache2/sites-available/mythweb.conf
NOTE: I password protect my MythWeb logins. So I uncommented several sections within mythweb.conf to allow browsers to work with m4v movies.
here's the contents of my mythweb.conf:
```


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

 # 20130910 - note that this is not simply a copy of the music entry above.  
#                using ".*/video/stream.php" will not work
    <LocationMatch .*/video/stream>
        Allow from all
    </LocationMatch>


#
# CHANGE THESE PATHS TO MATCH YOUR MYTHWEB INSTALLATION DIRECTORY!  e.g.
#
#    /var/www
#    /home/www/htdocs
#    /var/www/mythweb/mythweb
#    /srv/www/htdocs/mythweb
#

    <Directory "/var/www/mythweb/data">
        Options -All +FollowSymLinks +IncludesNoExec
    </Directory>
    <Directory "/var/www/mythweb" >

    ############################################################################
    # I *strongly* urge you to turn on authentication for MythWeb.  It is disabled
    # by default because it requires you to set up your own password file.  Please
    # see the man page for htdigest and then configure the following four directives
    # to suit your authentication needs.
    #
    Options Indexes FollowSymLinks
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

#20130910 - NOTE: despite the fact that I have set MythBackEnd IP address to 10.10.10.10 b/c I want Myth to appear as a UPNP Media Server on my network, I still kept the db_server = localhost I didn't need to change it to 10.10.10.10

            setenv db_server        "localhost"
            setenv db_name          "useyourown"
            setenv db_login         "useyourown"
            setenv db_password      "useyourown"

        #
        # By default, MythWeb uses the hostname program to look up the hostname of the
        # machine it runs on.  If this reports incorrect data, or you run MythWeb on a
        # machine without the hostname program, set this to your current hostname.
        #
         #   setenv hostname         "useyourown"
        #

        # By default, php will always search the current directory for include files,
        # but if you wish to install these directories outside of the current path
        # (eg. for security reasons), set this variable to the directory that
        # contains the directories like languages and templates.  eg.
        #
#20130910 - modified DIR
         #   setenv include_path      "/usr/share/mythtv/mythweb"

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
            php_value register_globals              0
            php_value magic_quotes_gpc              0
            php_value file_uploads                  0
            php_value allow_url_fopen               On

            php_value zlib.output_handler           Off
            php_value output_handler                NULL

        # If you have a large number of channels, you may need to increase
        # this value to prevent PHP from running out of memory during
        # searches.  The default is 64M.
#            php_value memory_limit                  64M
#20130910 - increased value
            php_value memory_limit                  128M
#            php_value memory_limit                  256M
#            php_value memory_limit                  512M

        # If you have a large number of channels, php may timeout creating
        # complex pages, so you will need to increase the amount of time
        # php has to create the page. The default is 30 seconds.
            php_value max_execution_time 30
#            php_value max_execution_time 60
#            php_value max_execution_time 120

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
        RewriteBase    /mythweb

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


#        Header append Vary User-Agent env=!dont-vary

    # Set up the perl handler so we can stream properly.  Do not use mod_perl
    # because it has a tendency to hold onto child processes, which causes
    # problems if the browser closes on an in-progress stream.
    #
        <Files *.pl>
            SetHandler cgi-script
            Options +ExecCGI
        </Files>

    </Directory>


```

save changes and exit

5. last step is to restart apache2 webserver:
command: sudo su <E>
command: service apache2 restart <E>
command: exit <E>

---

