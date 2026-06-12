---
title: "Schedules Direct Updates Required"
date: 2014-10-15
forum: Mythbuntu
---

### Post by tgm4883 on 2014-10-15
Schedules Direct is making a change that is requiring an update to MythTV. The MythTV update is already available via the Mythbuntu MythTV Update repo. See the following post for more info

[http://www.mythbuntu.org/home/news/actionsrequiredbynov1stduetoschedulesdirectchange](http://www.mythbuntu.org/home/news/actionsrequiredbynov1stduetoschedulesdirectchange)

---

### Post by aircarver on 2014-10-16
I am running 5 Mythbuntu 12.04 boxes (that I don't wish to upgrade [If it ain't broke don't 'fix' it ])

I tried:
> 

**The */etc/hosts* file solution**

[COLOR=#000000][FONT=sans-serif]Perhaps the simplest is to make the following entry in the backend's */etc/hosts* file:[/FONT][/COLOR]
54.85.117.227 webservices.schedulesdirect.tmsdatadirect.com

and the result is that they all say they ran successfully, but the number of days of program data keeps incrementing down

Any help for this ?

---

### Post by tgm4883 on 2014-10-16
> **aircarver said:**
> I am running 5 Mythbuntu 12.04 boxes (that I don't wish to upgrade [If it ain't broke don't 'fix' it ])

I tried:

and the result is that they all say they ran successfully, but the number of days of program data keeps incrementing down

Any help for this ?

You can get 0.27 for 12.04   [http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)



But if you really want to troubleshoot it, we'll need to see some logs. Probably /var/log/mythtv/mythfilldatabase.log

---

### Post by neutron68 on 2014-10-20
Is this a valid how-to for updating Mythbuntu 12.04 to mythtv to 0.27?

1.  go into the Mythbuntu Control Centre
2.  go to the Repositories tab
3.  change from 0.25 to 0.27
4.  click Apply
5.  exit from the Mythbuntu Control Centre
6.  run the Update manager.  It will pull the updates necessary to bring mythtv up to 0.27.
7.  reboot

---

### Post by aircarver on 2014-10-20
I don't want to update to .27.
I have built 2 .27 clean install machines for test.
I don't like the reduced number of ways to record programs, an there were problems with the ir blaster function.
I want to preserve .25 Myth machines that were functioning perfectly before the schedules data debacle ....

---

### Post by tgm4883 on 2014-10-20
> **neutron68 said:**
> Is this a valid how-to for updating Mythbuntu 12.04 to mythtv to 0.27?

1.  go into the Mythbuntu Control Centre
2.  go to the Repositories tab
3.  change from 0.25 to 0.27
4.  click Apply
5.  exit from the Mythbuntu Control Centre
6.  run the Update manager.  It will pull the updates necessary to bring mythtv up to 0.27.
7.  reboot

yes, that is valid for 12.04

---

### Post by tgm4883 on 2014-10-20
> **aircarver said:**
> I don't want to update to .27.
I have built 2 .27 clean install machines for test.
I don't like the reduced number of ways to record programs, an there were problems with the ir blaster function.
I want to preserve .25 Myth machines that were functioning perfectly before the schedules data debacle ....

To my knowledge, there isn't a reduced number of ways to record a program. That said, if you read the wiki page (which is linked from the page I posted), you can see a workaround for 0.26 and previous.

---

### Post by neutron68 on 2014-10-20
Is there a file (or files) I can check the date or version of to see if the Schedules-Direct update has been pulled from the repo and applied on my system?

---

### Post by tgm4883 on 2014-10-20
> **neutron68 said:**
> Is there a file (or files) I can check the date or version of to see if the Schedules-Direct update has been pulled from the repo and applied on my system?

If you do a "dpkg -l | grep mythtv" you should get an output similar to the following. The versions that you have installed are in the second column (it's worth mentioning that the ones you will care about say "ii" at the beginning of the line, meaning that it's the installed package)


```
thomas@ares:/var/log/mythtv$ dpkg -l | grep mythtv
ii  libmythtv-perl                               2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           A PERL library to access some MythTV features
ii  mythtv-backend                               2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           Personal video recorder application (server)
ii  mythtv-backend-master                        2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           Metapackage to setup and configure a "Master Backend" profile of MythTV.
ii  mythtv-common                                2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           Personal video recorder application (common data)
ii  mythtv-database                              2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           Personal video recorder application (database)
ii  mythtv-dbg                                   2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           Debug symbols for mythtv packages
ii  mythtv-status                                0.10.2-1~ppa                                       Show the status of a MythTV backend
ii  mythtv-theme-mythbuntu                       2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           The mythbuntu MythTV Theme
ii  mythtv-transcode-utils                       2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           Utilities used for transcoding MythTV tasks
ii  php-mythtv                                   2:0.27.3+fixes.20141012.5cc83b8-0ubuntu1           PHP Bindings for MythTV
thomas@ares:/var/log/mythtv$ 
```

---

### Post by neutron68 on 2014-10-21
OK on typing "dpkg -l | grep mythtv"
My list didn't have any lines with mythfilldatabase or schedules direct.

I just typed "locate mythfilldatabase" and found it in /usr/bin/mythfilldatabase
When I run the "mythfilldatabase" command I get this version info:

> 2014-10-21 13:46:48.043882 C  mythfilldatabase version: fixes/0.27 [v0.27.4-4-gb305eb5] [www.mythtv.org](www.mythtv.org)

Is this the updated version?

---

### Post by tgm4883 on 2014-10-21
Yes it is

---

### Post by diesel48 on 2014-10-22
I have the new update from the repos but my guide is still not pulling in new data. Just ran a mythfilldatabase --dd-grab-all and I only have 13 days of guide data. I get did not get new guide data, failed to fetch new data. I am down to only 13 days of guide data. I thought upgrading to the latest version fixed the guide data issue?

---

### Post by neutron68 on 2014-10-22
> **diesel48 said:**
> I have the new update from the repos but my guide is still not pulling in new data. Just ran a mythfilldatabase --dd-grab-all and I only have 13 days of guide data. I get did not get new guide data, failed to fetch new data. I am down to only 13 days of guide data. I thought upgrading to the latest version fixed the guide data issue?
I noticed the same thing - no new data, unless I forced an update from the command line "mythfilldatabase --refresh 14".
After doing that, I have guide data out to 6pm, November 3.

I just went into the Mythtv Backend Setup (under the General heading) and UNchecked the box that allows Schedules Direct to specify when the update occurs.  I've got mine manually set to occur between 2 and 5.  I believe that means 2am-5am.

Tomorrow morning, I'll see if I have new guide data for November 4...

---

### Post by tgm4883 on 2014-10-22
I believe the new service only gives 12 days of guide data.

---

### Post by neutron68 on 2014-10-22
> **tgm4883 said:**
> I believe the new service only gives 12 days of guide data.
That change from 14 days of data to 12 days of data occurs on Nov.1, correct?
For now, we should still be getting 14 days of data, correct?

---

### Post by tgm4883 on 2014-10-22
> **neutron68 said:**
> That change from 14 days of data to 12 days of data occurs on Nov.1, correct?
For now, we should still be getting 14 days of data, correct?

No. The 12 days starts as soon as you upgrade. Even if you didn't upgrade, it might still be only 12 days as TMS changed their DNS to send half of the users to the new SD servers for testing. So half of the people that haven't done anything necessary for the Nov 1st change will only be getting 12 days

---

### Post by neutron68 on 2014-10-22
I'm noticing that /var/log/mythtv/mythfilldatabase.log isn't getting added to, since I updated from myth0.25 to myth 0.27 repos.

Is this expected and normal?

---

### Post by mathog on 2014-10-26
My system is running 0.21 on Ubuntu 8.10, so it is much too old to find an update.

I fixed this by using hexedit on /var/lib/libmyth-0.21.so.0.21.0.  The original target string is
present in that file as a null terminated plain text string.  The new URL is, thankfully, shorter, so
I just edited it into the same position and padded out the end with extra nulls.  Here is a diff of
the resulting od -c outputs:
```

< 44402320   S   e   r   v   i   c   e  \0   h   t   t   p   :   /   /   w
< 44402340   e   b   s   e   r   v   i   c   e   s   .   s   c   h   e   d
< 44402360   u   l   e   s   d   i   r   e   c   t   .   t   m   s   d   a
< 44402400   t   a   d   i   r   e   c   t   .   c   o   m   /   s   c   h
< 44402420   e   d   u   l   e   s   d   i   r   e   c   t   /   t   v   l
< 44402440   i   s   t   i   n   g   s   /   x   t   v   d   S   e   r   v
< 44402460   i   c   e  \0   G   r   a   b   b   i   n   g       n   e   x
---
> 44402320   S   e   r   v   i   c   e  \0   h   t   t   p   :   /   /   d
> 44402340   d   .   s   c   h   e   d   u   l   e   s   d   i   r   e   c
> 44402360   t   .   o   r   g   /   s   c   h   e   d   u   l   e   s   d
> 44402400   i   r   e   c   t   /   t   v   l   i   s   t   i   n   g   s
> 44402420   /   x   t   v   d   S   e   r   v   i   c   e  \0  \0  \0  \0
> 44402440  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
> 44402460  \0  \0  \0  \0   G   r   a   b   b   i   n   g       n   e   x
```

On the next reboot after the change it picked up data from the new address.

This is the process:

1. cp /usr/lib/libmythtv-0.21.so.0.21.0 /usr/lib/libmythtv-0.21.so.0.21.0.dist
2.  as root or sudo
     hexedit /usr/lib/libmythtv-0.21.so.0.21.0 
3.  tab to get into ascii mode
4.  / to start a search, enter "tmsdatadirect.com" (without the double quotes) to find it.
5. Type in the new URL, overwriting the original.  Note, to enter "/" and "\0" use tab to get 
back to the hex window and enter "2F" and "00" respectively.
6. ^X to exit and save.
7. Reboot, and all is well.

For a different version just use the appropriate library name.

---

### Post by tgm4883 on 2014-10-27
> **mathog said:**
> My system is running 0.21 on Ubuntu 8.10, so it is much too old to find an update.

I fixed this by using hexedit on /var/lib/libmyth-0.21.so.0.21.0.  The original target string is
present in that file as a null terminated plain text string.  The new URL is, thankfully, shorter, so
I just edited it into the same position and padded out the end with extra nulls.  Here is a diff of
the resulting od -c outputs:
```

< 44402320   S   e   r   v   i   c   e  \0   h   t   t   p   :   /   /   w
< 44402340   e   b   s   e   r   v   i   c   e   s   .   s   c   h   e   d
< 44402360   u   l   e   s   d   i   r   e   c   t   .   t   m   s   d   a
< 44402400   t   a   d   i   r   e   c   t   .   c   o   m   /   s   c   h
< 44402420   e   d   u   l   e   s   d   i   r   e   c   t   /   t   v   l
< 44402440   i   s   t   i   n   g   s   /   x   t   v   d   S   e   r   v
< 44402460   i   c   e  \0   G   r   a   b   b   i   n   g       n   e   x
---
> 44402320   S   e   r   v   i   c   e  \0   h   t   t   p   :   /   /   d
> 44402340   d   .   s   c   h   e   d   u   l   e   s   d   i   r   e   c
> 44402360   t   .   o   r   g   /   s   c   h   e   d   u   l   e   s   d
> 44402400   i   r   e   c   t   /   t   v   l   i   s   t   i   n   g   s
> 44402420   /   x   t   v   d   S   e   r   v   i   c   e  \0  \0  \0  \0
> 44402440  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0  \0
> 44402460  \0  \0  \0  \0   G   r   a   b   b   i   n   g       n   e   x
```

On the next reboot after the change it picked up data from the new address.

This is the process:

1. cp /usr/lib/libmythtv-0.21.so.0.21.0 /usr/lib/libmythtv-0.21.so.0.21.0.dist
2.  as root or sudo
     hexedit /usr/lib/libmythtv-0.21.so.0.21.0 
3.  tab to get into ascii mode
4.  / to start a search, enter "tmsdatadirect.com" (without the double quotes) to find it.
5. Type in the new URL, overwriting the original.  Note, to enter "/" and "\0" use tab to get 
back to the hex window and enter "2F" and "00" respectively.
6. ^X to exit and save.
7. Reboot, and all is well.

For a different version just use the appropriate library name.

But why? You can do a hosts file change which is much much easier than that? Did you read the wiki page that is linked from the page I posted?

---

### Post by mathog on 2014-10-27
> **tgm4883 said:**
> But why? You can do a hosts file change which is much much easier than that?

I didn't want to have to mess with this again and there was no guarantee that the IP number associated with that address would be stable.   This method changes the URL and is equivalent to a rebuild from source, just without actually doing the rebuild.

Why this URL was hardwired into a library, instead of being read in from a config file, is a question we can leave for another day.

---

### Post by dannyboy79 on 2014-10-29
darn it, i thought there was no user intervention required with this change? i just now noticed i don't have any guide data. i haven't got any new recordings since around the 21st and it says there's no recordings scheduled. i missed the walking dead now because of this. i went back into mythtv-setup and sure enough, my username and password were missing from the settings and I know i didn't remove them. this needs to be mentioned to everyone IMO. i ran mythfilldatabase and the backend restarted but here's what mythweb shows on the listings tab
!!NoTrans: SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed [#144]!!
```
    datetime:  2014-10-29 01:00:00 (CDT)
    errornum:  256
  error type:  User Error
error string:  !!NoTrans: SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed [#144]!!
    filename:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
  error line:  79

==========================================================================

Backtrace: 

    file:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
    line:  79
   class:  
function:  trigger_error
    type:  
    args:  Array
(
    [0] => SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed [#144]
    [1] => 256
)

    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  261
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
    line:  324
   class:  Database
function:  query
    type:  ->
    args:  Array
(
    [0] => SELECT TO_DAYS(min(starttime)) - TO_DAYS(NOW()) FROM program
    [1] => Array ( )
)

    file:  /usr/share/mythtv/mythweb/modules/tv/list.php
    line:  69
   class:  Database
function:  query_col
    type:  ->
    args:  Array
(
    [0] => SELECT TO_DAYS(min(starttime)) - TO_DAYS(NOW()) FROM program
)

    file:  /usr/share/mythtv/mythweb/modules/tv/tmpl/default/list_data.php
    line:  29
   class:  
function:  date_select
    type:  
    args:  Array
(
    [0] => id="date_select" onchange="list_update($('date_select')[$('date_select').selectedIndex].value);"
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
            [192.168.0.5] => Array
                (
                    [proto_version] => Array
                        (
                            [last_check_version] => 77
                            [last_check_time] => 1414561572
                        )

                )

            [timezone] => Array
                (
                    [value] => America/Chicago
                    [last_check_time] => 1414561572
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

    [search] => Array
        (
            [type] => q
            [s] => pitbulls and paroles
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

    [list_time] => 1414562400
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

    [recorded_title] => 
    [recorded_recgroup] => 
)

==========================================================================

$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [HTTP_HOST] => 192.168.0.5
    [HTTP_CONNECTION] => keep-alive
    [HTTP_ACCEPT] => text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    [HTTP_USER_AGENT] => Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.111 Safari/537.36
    [HTTP_REFERER] => http://192.168.0.5/mythweb/status
    [HTTP_ACCEPT_ENCODING] => gzip,deflate,sdch
    [HTTP_ACCEPT_LANGUAGE] => en-US,en;q=0.8
    [HTTP_COOKIE] => mythweb_id=u8igs6qkhq36vluoao5n3hkib4
    [PATH] => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.4.7 (Ubuntu) Server at 192.168.0.5 Port 80</address>

    [SERVER_SOFTWARE] => Apache/2.4.7 (Ubuntu)
    [SERVER_NAME] => 192.168.0.5
    [SERVER_ADDR] => 192.168.0.5
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => 192.168.0.6
    [DOCUMENT_ROOT] => /var/www/html
    [REQUEST_SCHEME] => http
    [CONTEXT_PREFIX] => 
    [CONTEXT_DOCUMENT_ROOT] => /var/www/html
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/html/mythweb/mythweb.php
    [REMOTE_PORT] => 38499
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
    [REQUEST_TIME_FLOAT] => 1414562400.094
    [REQUEST_TIME] => 1414562400
    [STATUS] => 200
    [URL] => /mythweb/tv/list
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
    [hostname] => dell
    [http_host] => 192.168.0.5
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
    [root_auth_url] => http://192.168.0.5/mythweb/
    [root_url] => http://192.168.0.5/mythweb/
    [searchtype_keyword] => 3
    [searchtype_manual] => 5
    [searchtype_people] => 4
    [searchtype_power] => 1
    [searchtype_title] => 2
    [skin] => default
    [skin_img_url] => http://192.168.0.5/mythweb/skins/default/img/
    [skin_url] => http://192.168.0.5/mythweb/skins/default/
    [star_character] => &#9733;
    [stream_url] => http://192.168.0.5:80//mythweb/
    [tb] => 1099511627776
    [timeslot_blocks] => 3
    [timeslot_size] => 300
    [timeslotbar_skip] => 20
    [tmpl] => default
    [tmpl_dir] => modules/tv/tmpl/default/
)
```
someone please help me get my mythtv back up and running.

UPDATE: i had googled the error and found others having a similar issue. not sure how or why but my mysql tables were corrupted so I ran 
```
perl /usr/share/doc/mythtv-backend/contrib/maintenance/optimize_mythdb.pl
```
and then I ran
```
mythfilldatabase --refresh 14
```
and now i'm all sorted out. got worried there for a moment. lol

---

### Post by tgm4883 on 2014-10-29
> **dannyboy79 said:**
> darn it, i thought there was no user intervention required with this change? i just now noticed i don't have any guide data. i haven't got any new recordings since around the 21st and it says there's no recordings scheduled. i missed the walking dead now because of this. i went back into mythtv-setup and sure enough, my username and password were missing from the settings and I know i didn't remove them. this needs to be mentioned to everyone IMO. i ran mythfilldatabase and the backend restarted but here's what mythweb shows on the listings tab
!!NoTrans: SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed [#144]!!
```
    datetime:  2014-10-29 01:00:00 (CDT)
    errornum:  256
  error type:  User Error
error string:  !!NoTrans: SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed [#144]!!
    filename:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
  error line:  79

==========================================================================

Backtrace: 

    file:  /usr/share/mythtv/mythweb/classes/Database/Query/mysql.php
    line:  79
   class:  
function:  trigger_error
    type:  
    args:  Array
(
    [0] => SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed [#144]
    [1] => 256
)

    file:  /usr/share/mythtv/mythweb/classes/Database.php
    line:  261
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
    line:  324
   class:  Database
function:  query
    type:  ->
    args:  Array
(
    [0] => SELECT TO_DAYS(min(starttime)) - TO_DAYS(NOW()) FROM program
    [1] => Array ( )
)

    file:  /usr/share/mythtv/mythweb/modules/tv/list.php
    line:  69
   class:  Database
function:  query_col
    type:  ->
    args:  Array
(
    [0] => SELECT TO_DAYS(min(starttime)) - TO_DAYS(NOW()) FROM program
)

    file:  /usr/share/mythtv/mythweb/modules/tv/tmpl/default/list_data.php
    line:  29
   class:  
function:  date_select
    type:  
    args:  Array
(
    [0] => id="date_select" onchange="list_update($('date_select')[$('date_select').selectedIndex].value);"
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
            [192.168.0.5] => Array
                (
                    [proto_version] => Array
                        (
                            [last_check_version] => 77
                            [last_check_time] => 1414561572
                        )

                )

            [timezone] => Array
                (
                    [value] => America/Chicago
                    [last_check_time] => 1414561572
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

    [search] => Array
        (
            [type] => q
            [s] => pitbulls and paroles
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

    [list_time] => 1414562400
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

    [recorded_title] => 
    [recorded_recgroup] => 
)

==========================================================================

$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [HTTP_HOST] => 192.168.0.5
    [HTTP_CONNECTION] => keep-alive
    [HTTP_ACCEPT] => text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    [HTTP_USER_AGENT] => Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2125.111 Safari/537.36
    [HTTP_REFERER] => http://192.168.0.5/mythweb/status
    [HTTP_ACCEPT_ENCODING] => gzip,deflate,sdch
    [HTTP_ACCEPT_LANGUAGE] => en-US,en;q=0.8
    [HTTP_COOKIE] => mythweb_id=u8igs6qkhq36vluoao5n3hkib4
    [PATH] => /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.4.7 (Ubuntu) Server at 192.168.0.5 Port 80</address>

    [SERVER_SOFTWARE] => Apache/2.4.7 (Ubuntu)
    [SERVER_NAME] => 192.168.0.5
    [SERVER_ADDR] => 192.168.0.5
    [SERVER_PORT] => 80
    [REMOTE_ADDR] => 192.168.0.6
    [DOCUMENT_ROOT] => /var/www/html
    [REQUEST_SCHEME] => http
    [CONTEXT_PREFIX] => 
    [CONTEXT_DOCUMENT_ROOT] => /var/www/html
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/html/mythweb/mythweb.php
    [REMOTE_PORT] => 38499
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
    [REQUEST_TIME_FLOAT] => 1414562400.094
    [REQUEST_TIME] => 1414562400
    [STATUS] => 200
    [URL] => /mythweb/tv/list
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
    [hostname] => dell
    [http_host] => 192.168.0.5
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
    [root_auth_url] => http://192.168.0.5/mythweb/
    [root_url] => http://192.168.0.5/mythweb/
    [searchtype_keyword] => 3
    [searchtype_manual] => 5
    [searchtype_people] => 4
    [searchtype_power] => 1
    [searchtype_title] => 2
    [skin] => default
    [skin_img_url] => http://192.168.0.5/mythweb/skins/default/img/
    [skin_url] => http://192.168.0.5/mythweb/skins/default/
    [star_character] => &#9733;
    [stream_url] => http://192.168.0.5:80//mythweb/
    [tb] => 1099511627776
    [timeslot_blocks] => 3
    [timeslot_size] => 300
    [timeslotbar_skip] => 20
    [tmpl] => default
    [tmpl_dir] => modules/tv/tmpl/default/
)
```
someone please help me get my mythtv back up and running.

UPDATE: i had googled the error and found others having a similar issue. not sure how or why but my mysql tables were corrupted so I ran 
```
perl /usr/share/doc/mythtv-backend/contrib/maintenance/optimize_mythdb.pl
```
and then I ran
```
mythfilldatabase --refresh 14
```
and now i'm all sorted out. got worried there for a moment. lol

Glad you got that sorted. Not sure why you didn't have stuff in there, but it sounds like it was because of the mysql corruption. The only user intervention required in the change would be the regular mythtv updates, what you found is not typical and not caused by the schedules direct change.

Out of curiosity, did you try any of the other methods (eg. the JSON grabber by the Schedules Direct guys)

---

### Post by dannyboy79 on 2014-10-29
No, i did not try any other grabber solutions. what i find most alarming is that the username and password were blank when i opened mythtv-setup. i was already running 0.27 long ago so I did literally nothing in regards to this scheduledirect thing. i read here that I didn't need to do anything so I did nothing. i just happen to check mythweb last night and noticed that i had no recordings upcoming and then at the bottom of the status page it said i had no guide data. weird and weird.

even if one of the tables was corrupt, why would it remove my username and password?

---

### Post by tgm4883 on 2014-10-29
> **dannyboy79 said:**
> No, i did not try any other grabber solutions. what i find most alarming is that the username and password were blank when i opened mythtv-setup. i was already running 0.27 long ago so I did literally nothing in regards to this scheduledirect thing. i read here that I didn't need to do anything so I did nothing. i just happen to check mythweb last night and noticed that i had no recordings upcoming and then at the bottom of the status page it said i had no guide data. weird and weird.

even if one of the tables was corrupt, why would it remove my username and password?

Do you want me to continue speculating? I don't know why it removed those considering it was the program table that was marked as crashed. The credentials are stored in the DB, so is it possible that table was corrupt as well?

---

