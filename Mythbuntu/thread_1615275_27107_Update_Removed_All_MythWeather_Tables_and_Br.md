---
title: "27107 Update Removed All MythWeather Tables and Broke Mythweb"
date: 2010-11-06
forum: Mythbuntu
---

### Post by uncle hammy on 2010-11-06
As the title indicates.  The 0.24 autobuilds from this morning which upgraded me to 0.24+fixes build 27107 broke mythweb, causing the error below.  Further investigation reveals that all MythWeather related tables have been removed from the database.

According to the "good" folks at MythTV (I used the link from their own screen on the mythweb error screen), [http://svn.mythtv.org/trac/ticket/9190](http://svn.mythtv.org/trac/ticket/9190) this is not considered a bug.

If anyone is ever wondering why people don't use the "proper" methods to get things done, this would be why.  Submit a bug "it's not our problem, use the mailing list"...If you can figure out HOW to use the mailing list, "Huh, better submit a bug"...and around you go, chasing your tail, being belittled at every step.  And where do you submit the bug?  Is it MythTV, MythBuntu...Mailing Lists, forums, trac, svn...yep, sure is simple.

How on earth can ANYONE say "You ran updates, which broke it" is not a bug?

```

    datetime:  2010-11-06 19:49:41 (EDT)
    errornum:  256
  error type:  User Error
error string:  !!NoTrans: SQL Error: Unknown table engine 'InnoDB' [#1286]!!
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
    [0] => SQL Error: Unknown table engine 'InnoDB' [#1286]
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
            [0] => Array ( )
        )

)

    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  326
   class:  Database
function:  query
    type:  ->
    args:  Array
(
    [0] => SELECT COUNT(screen_id)
                                         FROM weatherscreens
    [1] => Array ( )
)

    file:  /usr/share/mythtv/mythweb/modules/weather/init.php
    line:  25
   class:  Database
function:  query_col
    type:  ->
    args:  Array
(
    [0] => SELECT COUNT(screen_id)
                                         FROM weatherscreens
)

    file:  /usr/share/mythtv/mythweb/classes/Modules.php
    line:  34
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/modules/weather/init.php
)

    file:  /usr/share/mythtv/mythweb/classes/Modules.php
    line:  54
   class:  Modules
function:  load
    type:  ::
    args:  Array ( )
    file:  /usr/share/mythtv/mythweb/mythweb.php
    line:  30
   class:  Modules
function:  getModule
    type:  ::
    args:  Array
(
    [0] => 
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
    [recorded_pixmaps] => 
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
    [recorded_paging] => null
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
                    [0] => database
                    [1] => settings
                )

            [host] => myth-backend
        )

    [backend] => Array
        (
            [192.168.25.252] => Array
                (
                    [proto_version] => Array
                        (
                            [last_check_version] => 63
                            [last_check_time] => 1289086053
                        )

                )

            [timezone] => Array
                (
                    [value] => America/Detroit
                    [last_check_time] => 1289086053
                )

        )

    [tv] => Array
        (
            [last] => Array
                (
                    [0] => upcoming
                )

            [show_advanced_schedule] => 1
        )

    [recorded_title] => 
    [recorded_recgroup] => Default
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

    [scheduled_recordings] => Array
        (
            [disp_scheduled] => 1
            [disp_duplicates] => 
            [disp_deactivated] => 
            [disp_conflicts] => 1
            [disp_recgroup] => 
            [disp_title] => 
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

    [recording_details] => Array
        (
            [show_Conflict] => 1
            [show_PreviousRecording] => 1
            [show_EarlierShowing] => 1
            [show_CurrentRecording] => 1
            [show_WillRecord] => 1
        )

    [list_time] => 1289440800
    [search] => Array
        (
            [type] => q
            [s] => monsters
            [ctype] => Array
                (
                    [0] => movie
                    [1] => series
                    [2] => sports
                    [3] => tvshow
                )

            [categories] => Array ( )
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

    [video_sortby] => Array
        (
            [0] => Array
                (
                    [field] => title
                    [reverse] => 
                )

        )

    [video] => Array
        (
            [path] => /
        )

    [tmpl] => default
    [skin] => default
    [cache_engine] => Cache_Null
    [stream] => Array
        (
            [include_user_and_password] => 
        )

    [weather] => Array
        (
            [active] => Array
                (
                    [0] => 104
                    [1] => 105
                    [2] => 106
                    [3] => 107
                    [4] => 108
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

    [file_url_override] => 
)

==========================================================================

$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [HTTP_HOST] => myth-backend
    [HTTP_USER_AGENT] => Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.2.12) Gecko/20101026 Firefox/3.6.12
    [HTTP_ACCEPT] => text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
    [HTTP_ACCEPT_LANGUAGE] => en-us,en;q=0.5
    [HTTP_ACCEPT_ENCODING] => gzip,deflate
    [HTTP_ACCEPT_CHARSET] => ISO-8859-1,utf-8;q=0.7,*;q=0.7
    [HTTP_KEEP_ALIVE] => 115
    [HTTP_CONNECTION] => keep-alive
    [HTTP_COOKIE] => mythweb_tmpl=default; mythweb_skin=default; mythweb_id=ke29v0k22js9vqv394c2mtsic5
    [PATH] => /usr/local/bin:/usr/bin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.2.14 (Ubuntu) Server at myth-backend Port 80</address>

    [SERVER_SOFTWARE] => Apache/2.2.14 (Ubuntu)
    [SERVER_NAME] => myth-backend
    [SERVER_ADDR] => 192.168.25.252
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => 192.168.25.100
    [DOCUMENT_ROOT] => /var/www
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/mythweb/mythweb.php
    [REMOTE_PORT] => 51154
    [REDIRECT_URL] => /mythweb/
    [GATEWAY_INTERFACE] => CGI/1.1
    [SERVER_PROTOCOL] => HTTP/1.1
    [REQUEST_METHOD] => GET
    [QUERY_STRING] => 
    [REQUEST_URI] => /
    [SCRIPT_NAME] => /mythweb/mythweb.php
    [PHP_SELF] => /mythweb/mythweb.php
    [REQUEST_TIME] => 1289087381
    [STATUS] => 200
    [URL] => /mythweb/
    [HTTP_PORT] => 80
)

==========================================================================

$constant_list["user"]: Array
(
    [ERROR] => 512
    [E_ASSERT_ERROR] => 4096
    [FATAL] => 256
    [PHP_MIN_VERSION] => 5.3
    [WARNING] => 1024
    [WebDBSchemaVer] => 2
    [error_email] => 
    [gb] => 1073741824
    [hostname] => myth-backend
    [http_host] => myth-backend
    [kb] => 1024
    [max_stars] => 4
    [mb] => 1048576
    [module] => 
    [modules_path] => ./modules
    [num_time_slots] => 36
    [prefer_channum] => 1
    [root] => /mythweb/
    [root_auth_url] => http://myth-backend/mythweb/
    [root_url] => http://myth-backend/mythweb/
    [skin] => default
    [skin_img_url] => http://myth-backend/mythweb/skins/default/img/
    [skin_url] => http://myth-backend/mythweb/skins/default/
    [star_character] => &#9733;
    [stream_url] => http://myth-backend:80//mythweb/
    [tb] => 1099511627776
    [timeslot_blocks] => 3
    [timeslot_size] => 300
    [timeslotbar_skip] => 20
    [tmpl] => default
    [tmpl_dir] => modules//tmpl/default/
)

```

---

### Post by nickrout on 2010-11-06
The response you received indicates a mysql problem, not a mythtv problem, so it's not sur[rising that the mythtv developers are not interested.

---

### Post by uncle hammy on 2010-11-06
Actually, it appears that the tables may be there (though I can't see them), and InnoDB engine has been turned off.  Now, I am trying to figure out how that happened and how to undo it.

---

