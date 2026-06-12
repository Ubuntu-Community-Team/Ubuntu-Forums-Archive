---
title: "Mythweb Mythbuntu 7.10 update: What happened?!"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by jpgscca on 2008-03-23
Just updated (03/22/08)  my Mythbuntu (7.10) box and now Mythweb is not working. The error states that mythweb and the backend have incompatible protocols. What happened? Was there a backend update that I didn't get? Did the Mythbuntu team put a newer version of Mythweb out that's not compatible with the backend? Anybody have any ideas?

Here's the error message I'm getting:
Note: The backend is running... I'm watching TV right now:

Error at /usr/share/mythtv/mythweb/includes/mythbackend.php, line 172:
Incompatible protocol version (mythweb=40, backend=31)

Fatal Error at /usr/share/mythtv/mythweb/includes/mythbackend.php, line 39:
Unable to connect to mythbackend, is it running?

If you choose to submit a bug report, please make sure to include a
brief description of what you were doing, along with the following
backtrace as an attachment (please don't paste the whole thing into
the ticket).
Backtrace:

    datetime:  2008-03-23 19:11:28 (PDT)
    errornum:  256
  error type:  User Error
error string:  Unable to connect to mythbackend, is it running?

    filename:  /usr/share/mythtv/mythweb/includes/mythbackend.php
  error line:  39

==========================================================================

Backtrace: 

    file:  /usr/share/mythtv/mythweb/includes/mythbackend.php
    line:  39
   class:  
function:  trigger_error
    type:  
    args:  Array
(
    [0] => Unable to connect to mythbackend, is it running?

    [1] => 256
)

    file:  /usr/share/mythtv/mythweb/includes/init.php
    line:  52
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/includes/mythbackend.php
)

    file:  /usr/share/mythtv/mythweb/mythweb.php
    line:  20
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/includes/init.php
)


==========================================================================

$_SESSION: Array
(
    [language] => English
    [tmpl] => default
    [skin] => default
    [prefer_channum] => 1
    [date_statusbar] => %a %b %e, %Y, %I:%M %p
    [date_scheduled] => %a %b %e, %Y (%I:%M %p)
    [date_scheduled_popup] => %a %b %e, %Y
    [date_recorded] => %a %b %e, %Y<br />(%I:%M %p)
    [date_search] => %a %b %e, %Y, %I:%M %p
    [date_listing_key] => %a %b %e, %Y, %I:%M %p
    [date_listing_jump] => %a %b %e, %Y
    [date_channel_jump] => %a %b %e, %Y
    [time_format] => %I:%M %p
    [recorded_pixmaps] => 1
    [guide_favonly] => 
    [timeslot_size] => 300
    [num_time_slots] => 36
    [timeslot_blocks] => 3
    [timeslotbar_skip] => 20
    [max_stars] => 4
    [star_character] => &diams;
    [list_time] => 1206250200
    [recorded_title] => 
    [recorded_recgroup] => 
    [recorded_sortby] => Array
        (
            [0] => Array
                (
                    [field] => airdate
                    [reverse] => 1
                )

            [1] => Array
                (
                    [field] => title
                    [reverse] => 
                )

        )

    [] => Array ( )
    [scheduled_recordings] => Array
        (
            [disp_scheduled] => 1
            [disp_duplicates] => 1
            [disp_deactivated] => 1
            [disp_conflicts] => 1
        )

    [siunits] => 
    [video_sortby] => Array
        (
            [0] => Array
                (
                    [field] => title
                    [reverse] => 
                )

        )

    [scheduled_sortby] => Array
        (
            [0] => Array
                (
                    [field] => airdate
                    [reverse] => 
                )

            [1] => Array
                (
                    [field] => title
                    [reverse] => 
                )

        )

    [schedules_sortby] => Array
        (
            [0] => Array
                (
                    [field] => airdate
                    [reverse] => 
                )

            [1] => Array
                (
                    [field] => title
                    [reverse] => 
                )

        )

    [search] => Array
        (
            [type] => q
            [s] => Jericho
            [ctype] => Array
                (
                    [0] => movie
                    [1] => series
                    [2] => sports
                    [3] => tvshow
                )

            [stars_gt] => 0
            [stars_lt] => 1
            [starttime] => now
            [endtime] => + 2 weeks
            [as] => Array
                (
                    [0] => wine
                )

            [af] => Array
                (
                    [0] => Array
                        (
                            [0] => description
                        )

                )

            [aj] => Array
                (
                    [0] => AND
                )

            [hd] => 
            [commfree] => 
            [airdate_start] => 
            [airdate_end] => 
        )

    [search_sortby] => Array
        (
            [0] => Array
                (
                    [field] => airdate
                    [reverse] => 
                )

            [1] => Array
                (
                    [field] => title
                    [reverse] => 
                )

        )

)

==========================================================================

$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [HTTP_HOST] => pinot.ath.cx
    [HTTP_USER_AGENT] => Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.8.1.12) Gecko/20080201 Firefox/2.0.0.12
    [HTTP_ACCEPT] => text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
    [HTTP_ACCEPT_LANGUAGE] => en-us,en;q=0.5
    [HTTP_ACCEPT_ENCODING] => gzip,deflate
    [HTTP_ACCEPT_CHARSET] => ISO-8859-1,utf-8;q=0.7,*;q=0.7
    [HTTP_KEEP_ALIVE] => 300
    [HTTP_CONNECTION] => keep-alive
    [HTTP_REFERER] => [http://pinot.ath.cx/](http://pinot.ath.cx/)
    [HTTP_COOKIE] => mythweb_id=287606c22a427b95ea64ace8a46c578d
    [PATH] => /usr/local/bin:/usr/bin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3 Server at pinot.ath.cx Port 80</address>

    [SERVER_SOFTWARE] => Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.3
    [SERVER_NAME] => pinot.ath.cx
    [SERVER_ADDR] => 192.168.1.13
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => 71.198.242.186
    [DOCUMENT_ROOT] => /var/www
    [SERVER_ADMIN] => [email]john.goodman@gmail.com[/email]
    [SCRIPT_FILENAME] => /var/www/mythweb/mythweb.php
    [REMOTE_PORT] => 2174
    [REMOTE_USER] => mythtv
    [AUTH_TYPE] => Basic
    [REDIRECT_URL] => /mythweb/
    [GATEWAY_INTERFACE] => CGI/1.1
    [SERVER_PROTOCOL] => HTTP/1.1
    [REQUEST_METHOD] => GET
    [QUERY_STRING] => 
    [REQUEST_URI] => /mythweb/
    [SCRIPT_NAME] => /mythweb/mythweb.php
    [PHP_SELF] => /mythweb/mythweb.php
    [PHP_AUTH_USER] => someusername
    [PHP_AUTH_PW] => pleasedontfarkme
    [REQUEST_TIME] => 1206324688
    [argv] => Array ( )
    [argc] => 0
    [STATUS] => 200
    [URL] => /mythweb/
)

---

### Post by warp99 on 2008-03-24
You have to uninstall mythweb 0.20, then install mythweb 0.21 since there are some dependencies that 0.21 uses that 0.20 does not. :)

---

### Post by jpgscca on 2008-03-24
> **warp99 said:**
> You have to uninstall mythweb 0.20, then install mythweb 0.21 since there are some dependencies that 0.21 uses that 0.20 does not. :)

Thanks for the help. I though when you run apt-get update/upgrade it updated the repositories and then upgraded anything that needed it? Oh well... I'll definitely try this. Thanks. :)

edit: Just did an apt-get dist-upgrade.... got everything up dated to 0.21.... umm.... Wow! New MythTV and MythWeb are good!

---

