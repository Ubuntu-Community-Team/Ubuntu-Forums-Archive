---
title: "Mythweb viewing recorded programs  Fatal Error"
date: 2010-05-05
forum: Mythbuntu
---

### Post by benlyboy on 2010-05-05
Today I went to look at a recording that I had made a couple of days back, and found that that when I click on a thumbnail to view a recording the page fails to load as it should. I used to work fine, not really sure when it stopped working, but I did do an updates a couple of nights ago.

Now when I open the page I get part of the page then this error report.

I am editing this, as I have just noticed that the same thing happens if I try to look at the program listings page on mythweb.

> 
  datetime:  2010-05-05 20:15:54 (EDT)
    errornum:  256
  error type:  User Error
error string:  SQL Error: Table './mythconverg/credits' is marked as crashed and last (automatic?) repair failed [#144]
    filename:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
  error line:  83

==========================================================================

Backtrace: 

    file:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
    line:  83
   class:  
function:  trigger_error
    type:  
    args:  Array
(
    [0] => SQL Error: Table './mythconverg/credits' is marked as crashed and last (automatic?) repair failed [#144]
    [1] => 256
)

    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  263
   class:  Database_Query_mysql
function:  execute
    type:  ->
    args:  Array
(
    [0] => Array
        (
            [0] => host
            [1] => 1056
            [2] => 1273028400
        )

)

    file:  /usr/share/mythtv/mythweb/modules/tv/classes/Program.php
    line:  640
   class:  Database
function:  query
    type:  ->
    args:  Array
(
    [0] => SELECT people.name
                                     FROM credits, people
                                    WHERE credits.person    = people.person
                                      AND credits.role      = ?
                                      AND credits.chanid    = ?
                                      AND credits.starttime = FROM_UNIXTIME(?)
    [1] => host
    [2] => 1056
    [3] => 1273028400
)

    file:  /usr/share/mythtv/mythweb/modules/tv/tmpl/default/detail.php
    line:  216
   class:  Program
function:  get_credits
    type:  ->
    args:  Array
(
    [0] => host
    [1] => 1
)

    file:  /usr/share/mythtv/mythweb/modules/tv/detail.php
    line:  353
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/modules/tv/tmpl/default/detail.php
)

    file:  /usr/share/mythtv/mythweb/modules/tv/handler.php
    line:  87
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/modules/tv/detail.php
)

    file:  /usr/share/mythtv/mythweb/mythweb.php
    line:  35
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/modules/tv/handler.php
)


==========================================================================

$_GET: Array
(
    [chanid] => 1056
    [starttime] => 1273029660
    [manualid] => 0
)

==========================================================================

$_SESSION: Array
(
    [language] => English
    [prefer_channum] => 1
    [date_statusbar] => %a %b %e, %Y, %I:%M %p
    [date_scheduled] => %a %b %e, %Y (%I:%M %p)
    [date_scheduled_popup] => %a %b %e, %Y
    [date_recorded] => %a %b %e, %Y (%I:%M %p)
    [date_search] => %a %b %e, %Y, %I:%M %p
    [date_listing_key] => %a %b %e, %Y, %I:%M %p
    [date_listing_jump] => %a %b %e, %Y
    [date_channel_jump] => %a %b %e, %Y
    [date_job_status] => %a %b %e, %Y, %I:%M %p
    [time_format] => %I:%M %p
    [recorded_pixmaps] => 1
    [guide_favonly] => 
    [timeslot_size] => 300
    [num_time_slots] => 36
    [timeslot_blocks] => 3
    [timeslotbar_skip] => 20
    [max_stars] => 4
    [star_character] => &#9733;
    [show_popup_info] => 1
    [show_channel_icons] => 1
    [sortby_channum] => 1
    [recorded_paging] => 
    [genre_colors] => 1
    [show_video_covers] => 1
    [settings] => Array
        (
            [screens] => Array
                (
                    [tv] => Array
                        (
                            [upcoming recordings] => Array
                                (
                                    [title] => on
                                    [channel] => on
                                    [record date] => on
                                    [length] => on
                                )

                        )

                )

            [last] => Array
                (
                    [0] => video
                    [1] => settings
                )

            [host] => mythbox
        )

    [backend] => Array
        (
            [127.0.0.1] => Array
                (
                    [proto_version] => Array
                        (
                            [last_check_version] => 56
                            [last_check_time] => 1273103633
                        )

                )

            [timezone] => Array
                (
                    [value] => America/New_York
                    [last_check_time] => 1273103633
                )

        )

    [tv] => Array
        (
            [last] => Array
                (
                    [0] => detail
                    [1] => 1056
                    [2] => 1273029660
                )

            [show_advanced_schedule] => 
        )

    [list_time] => 1273081500
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

    [recording_details] => Array
        (
            [show_Conflict] => 1
            [show_PreviousRecording] => 1
            [show_EarlierShowing] => 1
            [show_CurrentRecording] => 1
            [show_WillRecord] => 1
        )

    [scheduled_recordings] => Array
        (
            [disp_scheduled] => 1
            [disp_duplicates] => 
            [disp_deactivated] => 
            [disp_conflicts] => 1
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

    [video_sortby] => Array
        (
            [0] => Array
                (
                    [field] => title
                    [reverse] => 
                )

        )

    [] => Array ( )
    [weather] => Array
        (
            [active] => Array
                (
                    [0] => 1
                    [1] => 2
                    [2] => 3
                )

            [inactive] => Array
                (
                    [0] => 18 Hour Forecast
                    [1] => Animated Map
                    [2] => Current Conditions
                    [3] => Severe Weather Alerts
                    [4] => Six Day Forecast
                    [5] => Static Map
                    [6] => Three Day Forecast
                )

        )

    [search] => Array
        (
            [s] => canned:Non-Music Specials
            [type] => a
            [ctype] => Array
                (
                    [0] => sports
                )

            [categories] => Array
                (
                    [0] => Sports event
                )

            [stars_gt] => 0
            [stars_lt] => 1
            [starttime] => now
            [endtime] => + 2 weeks
            [as] => Array
                (
                    [0] => 
                )

            [af] => Array
                (
                    [0] => Array
                        (
                            [0] => title
                        )

                )

            [aj] => Array
                (
                    [0] => AND
                )

            [hd] => 
            [commfree] => 
            [unwatched] => 
            [scheduled] => 
            [generic] => 
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
    [HTTP_HOST] => xxxxxxxxxxxx
    [HTTP_USER_AGENT] => Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.19) Gecko/2010040119 Ubuntu/8.04 (hardy) Firefox/3.0.19
    [HTTP_ACCEPT] => text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    [HTTP_ACCEPT_LANGUAGE] => en-us,en;q=0.5
    [HTTP_ACCEPT_ENCODING] => gzip,deflate
    [HTTP_ACCEPT_CHARSET] => ISO-8859-1,utf-8;q=0.7,*;q=0.7
    [HTTP_KEEP_ALIVE] => 300
    [HTTP_CONNECTION] => keep-alive
    [HTTP_REFERER] => [http://xxxxxxxx/mythweb/tv/recorded](http://xxxxxxxx/mythweb/tv/recorded)
    [HTTP_COOKIE] => mythweb_tmpl=default; mythweb_skin=default; mythweb_id=76504afc49d7def2cf710dd2dabc989e
    [HTTP_CACHE_CONTROL] => max-age=0
    [PATH] => /usr/local/bin:/usr/bin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.2.12 (Ubuntu) Server at xxxxxxxxxx Port 80</address>

    [SERVER_SOFTWARE] => Apache/2.2.12 (Ubuntu)
    [SERVER_NAME] => xxxxxxxxxxxxx
    [SERVER_ADDR] => xxxxxxxxxxx
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => xxxxxxxxxxx
    [DOCUMENT_ROOT] => /var/www
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/mythweb/mythweb.php
    [REMOTE_PORT] => 62270
    [REMOTE_USER] => xxxxxxx
    [AUTH_TYPE] => Digest
    [REDIRECT_URL] => /mythweb/tv/detail/1056/1273029660
    [GATEWAY_INTERFACE] => CGI/1.1
    [SERVER_PROTOCOL] => HTTP/1.1
    [REQUEST_METHOD] => GET
    [QUERY_STRING] => 
    [REQUEST_URI] => /mythweb/tv/detail/1056/1273029660
    [SCRIPT_NAME] => /mythweb/mythweb.php
    [PATH_INFO] => /tv/detail/1056/1273029660
    [PATH_TRANSLATED] => /var/www/tv/detail/1056/1273029660
    [PHP_SELF] => /mythweb/mythweb.php/tv/detail/1056/1273029660
    [PHP_AUTH_USER] => xxxxxxxx
    [PHP_AUTH_DIGEST] => username="xxxxxxx", realm="MythTV", nonce="xpbZyuGFBAA=e71dcc953799789488e90abfe388d9568c697293", uri="/mythweb/tv/detail/1056/1273029660", algorithm=MD5, response="ffc48f38c58bf5ca5535bbcb29534fa0", qop=auth, nc=00000074, cnonce="634358b489245a3d"
    [REQUEST_TIME] => 1273104953
    [argv] => Array ( )
    [argc] => 0
    [STATUS] => 200
    [URL] => /mythweb/tv/detail/1056/1273029660
    [HTTP_PORT] => 80
)

==========================================================================

$constant_list["user"]: Array
(
    [ERROR] => 512
    [E_ASSERT_ERROR] => 4096
    [FATAL] => 256
    [JOB_ABORTED] => 288
    [JOB_ABORTING] => 9
    [JOB_CANCELLED] => 320
    [JOB_COMMFLAG] => 2
    [JOB_DONE] => 256
    [JOB_ERRORED] => 304
    [JOB_ERRORING] => 8
    [JOB_EXTERNAL] => 4
    [JOB_FINISHED] => 272
    [JOB_LIST_ALL] => 1
    [JOB_LIST_DONE] => 2
    [JOB_LIST_ERROR] => 8
    [JOB_LIST_NOT_DONE] => 4
    [JOB_LIST_RECENT] => 16
    [JOB_LIVE_REC] => 2
    [JOB_NONE] => 0
    [JOB_NO_FLAGS] => 0
    [JOB_PAUSE] => 1
    [JOB_PAUSED] => 6
    [JOB_PENDING] => 2
    [JOB_QUEUED] => 1
    [JOB_RESTART] => 8
    [JOB_RESUME] => 2
    [JOB_RETRY] => 7
    [JOB_RUN] => 0
    [JOB_RUNNING] => 4
    [JOB_STARTING] => 3
    [JOB_STOP] => 4
    [JOB_STOPPING] => 5
    [JOB_SYSTEMJOB] => 255
    [JOB_TRANSCODE] => 1
    [JOB_UNKNOWN] => 0
    [JOB_USERJOB] => 65280
    [JOB_USERJOB1] => 256
    [JOB_USERJOB2] => 512
    [JOB_USERJOB3] => 1024
    [JOB_USERJOB4] => 2048
    [JOB_USE_CUTLIST] => 1
    [PHP_MIN_VERSION] => 5.1
    [WARNING] => 1024
    [WebDBSchemaVer] => 2
    [dupsin_all] => 15
    [dupsin_ex_generic] => 64
    [dupsin_ex_repeats] => 32
    [dupsin_newepisodes] => 16
    [dupsin_oldrecorded] => 2
    [dupsin_recorded] => 1
    [error_email] => 
    [gb] => 1073741824
    [hostname] => mythbox
    [http_host] => xxxxxxxx
    [kb] => 1024
    [max_stars] => 4
    [mb] => 1048576
    [module] => tv
    [modules_path] => ./modules
    [num_time_slots] => 36
    [prefer_channum] => 1
    [rectype_always] => 4
    [rectype_channel] => 3
    [rectype_daily] => 2
    [rectype_dontrec] => 8
    [rectype_finddaily] => 9
    [rectype_findone] => 6
    [rectype_findweekly] => 10
    [rectype_once] => 1
    [rectype_override] => 7
    [rectype_weekly] => 5
    [root] => /mythweb/
    [root_url] => http://xxxxxxxx/mythweb/
    [searchtype_keyword] => 3
    [searchtype_manual] => 5
    [searchtype_people] => 4
    [searchtype_power] => 1
    [searchtype_title] => 2
    [skin] => default
    [skin_img_url] => http://xxxxxxxxx/mythweb/skins/default/img/
    [skin_url] => http://xxxxxxxxx/mythweb/skins/default/
    [star_character] => &#9733;
    [stream_url] => http://xxxxxxxxx:80//mythweb/
    [tb] => 1099511627776
    [timeslot_blocks] => 3
    [timeslot_size] => 300
    [timeslotbar_skip] => 20
    [tmpl] => default
    [tmpl_dir] => modules/tv/tmpl/default/
)






any ideas???

---

### Post by iamlindoro on 2010-05-05
The answer is right there in your error message-- you have a broken table in your database.  You need to repair it.  This likely happened because you shut down the machine ungracefully/while the table was being written to/etc.

[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Optimize_the_Database](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Optimize_the_Database)

Do the above.

---

### Post by benlyboy on 2010-05-05
ok

So how does one go about fixing that...?

---

### Post by iamlindoro on 2010-05-05
> **benlyboy said:**
> ok

So how does one go about fixing that...?

Read the link.  Alternately, google mysqlcheck.

---

### Post by benlyboy on 2010-05-06
Thanks for the reply

But I have one question before I start playing around with my database.
His problem only seems to affect mythweb, the frontend is working ok
wouldn't a database problem also affect the frontend...?

---

### Post by iamlindoro on 2010-05-06
It would, if you were to navigate to a screen in the frontend that used this table.  There's only one, and it's fairly well hidden.

Your database *is* damaged, and you *do* need to fix it.

---

### Post by benlyboy on 2010-05-06
ok will do thanks

however it seem that the optimize_mythdb.pl script has been move or removed as I can't find it..


I'm running 9.10  and 023

---

