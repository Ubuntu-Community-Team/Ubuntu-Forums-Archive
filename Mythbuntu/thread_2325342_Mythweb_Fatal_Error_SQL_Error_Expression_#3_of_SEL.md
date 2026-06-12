---
title: "Mythweb Fatal Error SQL Error: Expression #3 of SELECT..."
date: 2016-05-21
forum: Mythbuntu
---

### Post by tim129 on 2016-05-21
Solved my first problem with setting up my mythbuntu box (with some help) which was that I couldn't get access to mythweb... turned out to be a setup issue with the ip address. Now I have a new problem to solve.

Using: Mythbuntu with 16.0.4 with MythTV 28

Backend is only being setup on this box.

When I go to Mythweb and click on listings I get:
[h=2]Fatal Error[/h]!!NoTrans: SQL Error: Expression #3 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'mythconverg.program.endtime' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [#1055]!!

With a box below it containing 

```
    datetime:  2016-05-21 10:36:23 (MDT)
    errornum:  256
  error type:  User Error
error string:  !!NoTrans: SQL Error: Expression #3 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'mythconverg.program.endtime' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [#1055]!!
    filename:  /usr/share/mythtv/mythweb/classes/Database/Query/mysqlicompat.php
  error line:  98


==========================================================================


Backtrace: 


    file:  /usr/share/mythtv/mythweb/classes/Database/Query/mysqlicompat.php
    line:  98
   class:  
function:  trigger_error
    type:  
    args:  Array
(
    [0] => SQL Error: Expression #3 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'mythconverg.program.endtime' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [#1055]
    [1] => 256
)


    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  261
   class:  Database_Query_mysqlicompat
function:  execute
    type:  ->
    args:  Array
(
    [0] => Array ( )
)


    file:  /usr/share/mythtv/mythweb/modules/tv/includes/programs.php
    line:  140
   class:  Database
function:  query
    type:  ->
    args:  Array
(
    [0] => SELECT program.*,
                         UNIX_TIMESTAMP(program.starttime) AS starttime_unix,
                         UNIX_TIMESTAMP(program.endtime) AS endtime_unix,
                         IFNULL(programrating.system, "") AS rater,
                         IFNULL(programrating.rating, "") AS rating,
                         channel.callsign,
                         channel.channum
                  FROM program USE INDEX (id_start_end)
                       LEFT JOIN programrating USING (chanid, starttime)
                       LEFT JOIN channel ON program.chanid = channel.chanid
                       LEFT JOIN credits ON (program.chanid = credits.chanid AND program.starttime = credits.starttime)
                       LEFT JOIN people ON (credits.person = people.person)
                 WHERE program.chanid='1021' AND (program.endtime > FROM_UNIXTIME('1463848200') AND program.starttime < FROM_UNIXTIME('1463859000') AND program.starttime != program.endtime)
GROUP BY channel.callsign, program.chanid, program.starttime ORDER BY program.starttime
)


    file:  /usr/share/mythtv/mythweb/modules/tv/classes/Channel.php
    line:  154
   class:  
function:  load_all_program_data
    type:  
    args:  Array
(
    [0] => 1463848200
    [1] => 1463859000
    [2] => 1021
)


    file:  /usr/share/mythtv/mythweb/modules/tv/tmpl/default/list_data.php
    line:  102
   class:  Channel
function:  display_programs
    type:  ->
    args:  Array
(
    [0] => 1463848200
    [1] => 1463859000
)


    file:  /usr/share/mythtv/mythweb/modules/tv/tmpl/default/list.php
    line:  78
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/modules/tv/tmpl/default/list_data.php
)


    file:  /usr/share/mythtv/mythweb/modules/tv/list.php
    line:  45
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/modules/tv/tmpl/default/list.php
)


    file:  /usr/share/mythtv/mythweb/modules/tv/handler.php
    line:  82
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/modules/tv/list.php
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


$_SESSION: Array
(
    [cache_engine] => Cache_Null
    [stream] => Array
        (
            [include_user_and_password] => 
        )


    [prefer_channum] => 1
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
                    [0] => mythweb
                    [1] => session
                )


        )


    [backend] => Array
        (
            [timezone] => Array
                (
                    [value] => America/Denver
                    [last_check_time] => 1463840794
                )


            [127.0.0.1] => Array
                (
                    [proto_version] => Array
                        (
                            [last_check_version] => 88
                            [last_check_time] => 1463848484
                        )


                )


        )


    [language] => English
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
    [tv] => Array
        (
            [last] => Array
                (
                    [0] => list
                )


        )


    
[list_time] => 1463848200
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


    [scheduled_recordings] => Array
        (
            [disp_scheduled] => 1
            [disp_duplicates] => 
            [disp_deactivated] => 
            [disp_conflicts] => 1
        )


    [] => Array ( )
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


)


==========================================================================


$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [HTTP_HOST] => localhost
    [HTTP_CONNECTION] => keep-alive
    [HTTP_ACCEPT] => text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    [HTTP_UPGRADE_INSECURE_REQUESTS] => 1
    [HTTP_USER_AGENT] => Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36
    [HTTP_DNT] => 1
    [HTTP_REFERER] => http://localhost/mythweb/
    [HTTP_ACCEPT_ENCODING] => gzip, deflate, sdch
    [HTTP_ACCEPT_LANGUAGE] => en-US,en;q=0.8
    [HTTP_COOKIE] => mythweb_id=31i2ha21m4pv2u0gudtf2cf2e7
    [PATH] => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.4.18 (Ubuntu) Server at localhost Port 80</address>


    [SERVER_SOFTWARE] => Apache/2.4.18 (Ubuntu)
    [SERVER_NAME] => localhost
    [SERVER_ADDR] => 127.0.0.1
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => 127.0.0.1
    [DOCUMENT_ROOT] => /var/www/html
    [REQUEST_SCHEME] => http
    [CONTEXT_PREFIX] => 
    [CONTEXT_DOCUMENT_ROOT] => /var/www/html
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/html/mythweb/mythweb.php
    [REMOTE_PORT] => 60228
    [REDIRECT_URL] => /mythweb/tv/list
    [GATEWAY_INTERFACE] => CGI/1.1
    [SERVER_PROTOCOL] => HTTP/1.1
    [REQUEST_METHOD] => GET
    [QUERY_STRING] => 
    [REQUEST_URI] => /tv/list
    [SCRIPT_NAME] => /mythweb/mythweb.php
    [PATH_INFO] => /tv/list
    [PATH_TRANSLATED] => /var/www/html/tv/list
    [PHP_SELF] => /mythweb/mythweb.php/tv/list
    [REQUEST_TIME_FLOAT] => 1463848583.64
    [REQUEST_TIME] => 1463848583
    [STATUS] => 200
    [URL] => /mythweb/tv/list
    [HTTP_X_FORWARDED_PROTO] => 
    [HTTPS] => 
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
    [WebDBSchemaVer] => 4
    [dupsin_all] => 15
    [dupsin_newepisodes] => 16
    [dupsin_oldrecorded] => 2
    [dupsin_recorded] => 1
    [error_email] => 
    [gb] => 1073741824
    [hostname] => tim-mythtv
    [http_host] => localhost
    [kb] => 1024
    [max_stars] => 4
    [mb] => 1048576
    [module] => tv
    [modules_path] => /usr/share/mythtv/mythweb/modules
    [num_time_slots] => 36
    [prefer_channum] => 1
    [rectype_always] => 4
    [rectype_daily] => 2
    [rectype_dontrec] => 8
    [rectype_findone] => 6
    [rectype_once] => 1
    [rectype_override] => 7
    [rectype_template] => 11
    [rectype_weekly] => 5
    [root] => /mythweb/
    [root_auth_url] => http://localhost/mythweb/
    [root_url] => http://localhost/mythweb/
    [searchtype_keyword] => 3
    [searchtype_manual] => 5
    [searchtype_people] => 4
    [searchtype_power] => 1
    [searchtype_title] => 2
    [skin] => default
    [skin_img_url] => http://localhost/mythweb/skins/default/img/
    [skin_url] => http://localhost/mythweb/skins/default/
    [star_character] => &#9733;
    [stream_url] => http://localhost:80//mythweb/
    [tb] => 1099511627776
    [timeslot_blocks] => 3
    [timeslot_size] => 300
    [timeslotbar_skip] => 20
    [tmpl] => default
    [tmpl_dir] => modules/tv/tmpl/default/
)







```

If I go to the status page (which seems to take quite while to load), but eventually it shows:  


Last mythfilldatabase run started on Sat May 21 2016, 10:31 AM and ended on Sat May 21 2016, 10:31 AM. 
Suggested next mythfilldatabase run: Sun May 22 2016, 11:33 AM.
There's no guide data available! Have you run mythfilldatabase?
DataDirect Status: Your subscription expires on Sun Apr 23 2017 3:22 PM


And yes, mythfilldatabase has been run as it says. And I do see data being downloaded, but there appears to be either something wrong with the database or ???  Any thoughts on a solution?

---

### Post by blm-ubunet on 2016-05-21
[https://code.mythtv.org/trac/ticket/12713](https://code.mythtv.org/trac/ticket/12713)

Not sure if you need update to mythweb (should be in mythbuntu) or change in /etc/mysql/conf.d/mythtv.cnf file or both..
Maybe package installer didn't / couldn't update the mysql cnf file.

---

### Post by tim129 on 2016-05-23
> **blm-ubunet said:**
> [https://code.mythtv.org/trac/ticket/12713](https://code.mythtv.org/trac/ticket/12713)

Not sure if you need update to mythweb (should be in mythbuntu) or change in /etc/mysql/conf.d/mythtv.cnf file or both..
Maybe package installer didn't / couldn't update the mysql cnf file.


Thank you, I will see if that info can get me past that hurdle. I saw this when I did a google search on the issue, but I decided it wasn't what I needed (and I don't remember why I decided that). Will try it out.

---

### Post by tim129 on 2016-05-23
And making that adjustment.... now shows me the TV listings... awesome. And the next error I will hit is....

Trying to create a recording causes an error. But I think I saw something about this in the comments for the error that was mentioned.... I'll have to get back to it.

---

### Post by tim129 on 2016-05-24
Yup. I added the repositories to keep mythtv updated for 28 and once I updated, the problem went away. I could schedule recordings and mythweb went from taking 45 seconds to update each screen to updating within seconds... the only thing next to figure out is why the recordings aren't happening. That will be a trip into the log file I presume and that will be for another day.

---

