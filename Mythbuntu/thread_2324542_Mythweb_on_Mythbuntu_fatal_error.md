---
title: "Mythweb on Mythbuntu fatal error"
date: 2016-05-14
forum: Mythbuntu
---

### Post by tim129 on 2016-05-14
First, I have some experience with linux but it was 20 years ago in college. Some of it is coming back as I attempt to set up a Mythbuntu box but some of it isn't.

 I'm installing Mythbuntu using the 16.04 version with MythTV version 0.28. I'm just in the initial phases of setting it up. But I have my HDhomerun configured, schedules direct configured as the source(though I think it may be failing to get data), and I'm should be pretty much there to getting it running... (have to figure out why the Hauppage 2225 card isn't being seen, but that is probably because the firmware isn't installed and it isn't the first priority on fixing the issues) ... 

Anyway, I'm trying to access Mythweb from my main machine so I can use it to setup recordings, and so I can see if schedule data is actually coming down from Schedules Direct.

When I connect thru my browser to the Mythbuntu machine, I get the following error:

*Fatal error: Uncaught Error: Call to undefined function t() in /usr/share/mythtv/mythweb/modules/database/init.php:10 Stack trace: #0 /usr/share/mythtv/mythweb/classes/Modules.php(30): require_once() #1 /usr/share/mythtv/mythweb/classes/Modules.php(50): Modules::load() #2 /usr/share/mythtv/mythweb/modules/_shared/tmpl/default/header.php(134): Modules::getModule('tv') #3 /usr/share/mythtv/mythweb/modules/_shared/tmpl/_errors/error.php(19): include('/usr/share/myth...') #4 /usr/share/mythtv/mythweb/includes/errordisplay.php(198): require_once('/usr/share/myth...') #5 /usr/share/mythtv/bindings/php/MythBackend.php(76): custom_error('Unable to conne...') #6 /usr/share/mythtv/bindings/php/MythBackend.php(137): MythBackend->connect(false) #7 /usr/share/mythtv/mythweb/includes/utils.php(56): MythBackend->sendCommand(Array) #8 /usr/share/mythtv/mythweb/includes/db_update.php(57): setting('recommend_enabl...', NULL, false) #9 /usr/share/mythtv/mythweb/includes/init.php(46): require_once('/usr/share/myth...') #10 /usr/share/mythtv/ in/usr/share/mythtv/mythweb/modules/database/init.php on line 10*

I know enough PHP to make me dangerous, so I recognize it as a problem with either the php in the modules or (and more likely) a problem with something not being correctly set up in the software reading the php files. I'm not sure of where to start to see what might be causing it. Any thoughts would be a great starting point. And if I didn't give something that might help you in helping me, please let me know. 

Thank you
Tim

---

### Post by tim129 on 2016-05-16
Ok. In doing some more research, I found a post stating the error is a result that mythweb cannot connect to the mythconverg database and suggests checking the /etc/apache2/sites-enabled/mythweb.conf username and password to verify they are correct... as it says they were incorrect for them. I've checked this, but the username and password are correct. And I verified access can be had by using a mysql -uusername -ppassword mythconverg in a terminal. (putting in the username and password to replace those placeholders). That worked. So I'm still not sure what the issue might be.

here is the place I found that info: [http://www.gossamer-threads.com/lists/mythtv/users/434845](http://www.gossamer-threads.com/lists/mythtv/users/434845)

---

### Post by tim129 on 2016-05-16
i also did get Schedules direct downloading data... I think . Saw it actually working this time after running mythfilldatabase. But mythweb still won't run. Getting the same error as the first message.

---

### Post by tim129 on 2016-05-18
Still trying to diagnose the issue. I tried to connect Kodi on my main system (and then also on a android tablet) to the mythbuntu backend. It should work as I had it connecting with another mythbuntu release that I tried before trying this install. But they are both reporting they aren't getting a response from mythtv backend. Could this be a related issue to the database issue? I know mysql is running by using "mysqladmin -u root -p status"  to check. I got an uptime of 184467. If it wasn't running I'd get an error.

Does anyone know what the Owner of the mythweb webfiles should be? Currently they are set to root, but I'm wondering if they should be mythtv instead.

 I did change the php file I was getting an error in and commented out the php and added a print "hello world"; line instead. It printed the text, so php appears to be working... but connections to the databases do not. 

Perhaps bad databases? I'm just guessing at this point.

---

### Post by hollywoodpete on 2016-05-19
You won't like my answer but I would suggest installing 14.04 LTS [http://cdimage.ubuntu.com/mythbuntu/releases/14.04.4/release/](http://cdimage.ubuntu.com/mythbuntu/releases/14.04.4/release/). It is a painless install and uses 0.28 fine. I am having similar struggles with 16.04 and storage groups. What do you get with sever.ip:6544? I'm pretty sure your backend error log is going to be loaded with permission errors. You could try and upload a pastebin link to your error log and may get help from someone smarter than me. Good luck

---

### Post by Lester_Burnham on 2016-05-19
Hi,

Sounds like an IP issue
What IP are you using to log into mythweb? 127.0.0.1 or a 192.*.*.* etc.
What is the master backend IP address set at in mythtv-setup?
What address did you use to connect to mysql?

You could try commenting out the bind address in /etc/mysql/conf.d/mythtv.cnf (I think that's where it is)

Lester

---

### Post by tim129 on 2016-05-19
> **hollywoodpete said:**
> You won't like my answer but I would suggest installing 14.04 LTS [http://cdimage.ubuntu.com/mythbuntu/releases/14.04.4/release/](http://cdimage.ubuntu.com/mythbuntu/releases/14.04.4/release/). It is a painless install and uses 0.28 fine. I am having similar struggles with 16.04 and storage groups. What do you get with sever.ip:6544? I'm pretty sure your backend error log is going to be loaded with permission errors. You could try and upload a pastebin link to your error log and may get help from someone smarter than me. Good luck

Hollywoodpete... to be honest I have seriously considered moving to it. I initially tried 14.04 with 27, but figured I should move to 28 and noticed 16.04 was the newest.... Both of those gave me a hicup or two that just made it frustrating. I couldn't get 14.04 with 27 to download anything from schedules direct but seemed to have pretty much everything else functioning, I think. This one it's getting stuck here so far. I might just punt this version and go to 14.04 with 28 instead but I'm going to give it the rest of this week to work on.

If I go to the server.ip:6544 on either the mythbuntu box or my main system I get the site can't be reached by both... interestingly if I go to localhost:6544 I get MythTV Web frontend page.... which makes me go hmmmmmmm....

---

### Post by tim129 on 2016-05-19
> **Lester_Burnham said:**
> Hi,

Sounds like an IP issue
What IP are you using to log into mythweb? 127.0.0.1 or a 192.*.*.* etc.
What is the master backend IP address set at in mythtv-setup?
What address did you use to connect to mysql?

You could try commenting out the bind address in /etc/mysql/conf.d/mythtv.cnf (I think that's where it is)

Lester

Lester, I'm using 192.*.*.* as the Local Backend IPv4 address and Master Backend IP address in mythtv-setup. I know I can connect to the box as I've SSHed into it and used NoMachine as the way to graphically work with the box.

 I'm not sure what address I used to connect to mysql. Is that set somewhere? Or perhaps I'm misunderstanding the question. (lack of sleep due to work overtime lately) 

I'll look at the bind address you mentioned tomorrow if I get time. Too much overtime required at work right now.

---

### Post by Lester_Burnham on 2016-05-19
Hi,

Try using localhost/mythweb or 127.0.0.1/mythweb and see what you get.
If that works, you'll need to comment out the bind address or add your 192 address and reboot.

The bind address limits mythtv to what ip address it can access mysql on. It's normally set to 127.0.0.1
You may have been able to use the 192 IP in a terminal, because the bind address only applies to mythtv (I'm pretty sure)

Lester

---

### Post by tim129 on 2016-05-21
> **Lester_Burnham said:**
> Hi,

Try using localhost/mythweb or 127.0.0.1/mythweb and see what you get.
If that works, you'll need to comment out the bind address or add your 192 address and reboot.

The bind address limits mythtv to what ip address it can access mysql on. It's normally set to 127.0.0.1
You may have been able to use the 192 IP in a terminal, because the bind address only applies to mythtv (I'm pretty sure)

Lester

localhost/mythweb gives me the same error as the first post. 

However..... I now changed the MythTV's backend ip addresses for Local Backend and Master Backend back to 127.0.0.1 and when I go to localhost/mythweb now mythweb works (well sort of)! It at least shows Mythweb now instead of getting a php error. I can also access mythweb through my normal computer by going to 192.*.*.*/mythweb 

But success is slow going as I'm now getting a new error... but it is a step in the right direction!

When I click on TV listings I get:

Fatal Error

!!NoTrans: SQL Error: Expression #3 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'mythconverg.program.endtime' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by [#1055]!!

Followed by a box with this info in it:

```
    datetime:  2016-05-21 08:46:25 (MDT)    errornum:  256
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
                 WHERE program.chanid='1021' AND (program.endtime > FROM_UNIXTIME('1463841900') AND program.starttime < FROM_UNIXTIME('1463852700') AND program.starttime != program.endtime)
GROUP BY channel.callsign, program.chanid, program.starttime ORDER BY program.starttime
)


    file:  /usr/share/mythtv/mythweb/modules/tv/classes/Channel.php
    line:  154
   class:  
function:  load_all_program_data
    type:  
    args:  Array
(
    [0] => 1463841900
    [1] => 1463852700
    [2] => 1021
)


    file:  /usr/share/mythtv/mythweb/modules/tv/tmpl/default/list_data.php
    line:  102
   class:  Channel
function:  display_programs
    type:  ->
    args:  Array
(
    [0] => 1463841900
    [1] => 1463852700
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


        )


    [backend] => Array
        (
            [127.0.0.1] => Array
                (
                    [proto_version] => Array
                        (
                            [last_check_version] => 88
                            [last_check_time] => 1463841214
                        )


                )


            [timezone] => Array
                (
                    [value] => America/Denver
                    [last_check_time] => 1463841214
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


    
[list_time] => 1463841900
)


==========================================================================


$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [HTTP_HOST] => 192.168.0.17
    [HTTP_CONNECTION] => keep-alive
    [HTTP_CACHE_CONTROL] => max-age=0
    [HTTP_ACCEPT] => text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    [HTTP_UPGRADE_INSECURE_REQUESTS] => 1
    [HTTP_USER_AGENT] => Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36
    [HTTP_DNT] => 1
    [HTTP_REFERER] => http://192.168.0.17/mythweb/
    [HTTP_ACCEPT_ENCODING] => gzip, deflate, sdch
    [HTTP_ACCEPT_LANGUAGE] => en-US,en;q=0.8
    [HTTP_COOKIE] => mythweb_id=s7seitnqv3aett8hai3viben81
    [PATH] => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.4.18 (Ubuntu) Server at 192.168.0.17 Port 80</address>


    [SERVER_SOFTWARE] => Apache/2.4.18 (Ubuntu)
    [SERVER_NAME] => 192.168.0.17
    [SERVER_ADDR] => 192.168.0.17
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => 192.168.0.17
    [DOCUMENT_ROOT] => /var/www/html
    [REQUEST_SCHEME] => http
    [CONTEXT_PREFIX] => 
    [CONTEXT_DOCUMENT_ROOT] => /var/www/html
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/html/mythweb/mythweb.php
    [REMOTE_PORT] => 45870
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
    [REQUEST_TIME_FLOAT] => 1463841985.446
    [REQUEST_TIME] => 1463841985
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
    [hostname] => tmythtv
    [http_host] => 192.168.0.17
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
    [root_auth_url] => http://192.168.0.17/mythweb/
    [root_url] => http://192.168.0.17/mythweb/
    [searchtype_keyword] => 3
    [searchtype_manual] => 5
    [searchtype_people] => 4
    [searchtype_power] => 1
    [searchtype_title] => 2
    [skin] => default
    [skin_img_url] => http://192.168.0.17/mythweb/skins/default/img/
    [skin_url] => http://192.168.0.17/mythweb/skins/default/
    [star_character] => &#9733;
    [stream_url] => http://192.168.0.17:80//mythweb/
    [tb] => 1099511627776
    [timeslot_blocks] => 3
    [timeslot_size] => 300
    [timeslotbar_skip] => 20
    [tmpl] => default
    [tmpl_dir] => modules/tv/tmpl/default/
)
```

---

### Post by tim129 on 2016-05-21
I'd mark the initial issue as solved. And I'll have a new issue to ask a question about now instead. 

I had followed guides I saw online which say to set both the backend ip addresses for Local Backend and Master Backend back to the computer's IP address (192.168.0.17 in my case).... I have since changed the LocalBackend IP back to 192.168.0.17. No ill effect. 

Oddly..just to test something... I again set the Local Backend to the 192.*.*.* address for the box and it doesn't seem to be causing an issue.  If I also set the Master Backend IP address to 192.168.0.17 and it isn't giving me the error in the first post, but the box is not reachable through Mythweb as the status instead of displaying information about the box says isntead that it cannot reach MythTV. So I have changed the Master Backend IP back to 127.0.0.1.

---

### Post by Lester_Burnham on 2016-05-21
Hi,

Did you comment out the bind address in /etc/mysql/conf.d/mythtv.cnf?

I'd also make sure ~/.mythtv/config.xml and /etc/mythtv/config.xml contain the same info. (mainly IP address)
I normally make the one in /etc/mythtv/ a shortcut to the one in your home directory. So the info is the same.

My test system here, I'm just using 127.0.0.1 as the backend IP and I can reach mythweb from another box using the machines external 192.*.*.* IP

Lester

---

### Post by tim129 on 2016-05-23
> **Lester_Burnham said:**
> Hi,

Did you comment out the bind address in /etc/mysql/conf.d/mythtv.cnf?

I'd also make sure ~/.mythtv/config.xml and /etc/mythtv/config.xml contain the same info. (mainly IP address)
I normally make the one in /etc/mythtv/ a shortcut to the one in your home directory. So the info is the same.

My test system here, I'm just using 127.0.0.1 as the backend IP and I can reach mythweb from another box using the machines external 192.*.*.* IP

Lester

I didn't comment it out, but if I look at /etc/mysql/conf.d/mythtv.cnf all that is in the file is:

```
[mysqld]
bind-address=::

```

~/.mythtv/config.xml and /etc/mythtv/config.xml contain the same information.

---

### Post by vharper on 2016-07-18
The second problem described above:
[FONT=courier new] !!NoTrans: SQL Error: Expression #3 of SELECT list is not in GROUP BY clause ...[/FONT]
is described here: [https://code.mythtv.org/trac/ticket/12713](https://code.mythtv.org/trac/ticket/12713)

As described in ticket 12713 I added the following lines to the end of /etc/mysql/conf.d/mythtv.cnf and it solved the problem:

[FONT=courier new] max_connections=100[/FONT]
[FONT=courier new] sql_mode=NO_ENGINE_SUBSTITUTION[/FONT]

---

### Post by patrickchamberlain on 2017-01-02
After verifying the username and password in[COLOR=#000000] /etc/apache2/sites-enabled/mythweb.conf , I changed the IP address of the mysql server to "127.0.0.1" to match what was in my mythtv backend setup - after restarting apache this fixed the no connection issue for me (both on the same machine and connecting from another machine).


[/COLOR]

---

