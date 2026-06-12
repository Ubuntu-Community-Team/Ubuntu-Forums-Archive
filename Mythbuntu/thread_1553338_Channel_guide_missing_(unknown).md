---
title: "Channel guide missing (unknown)"
date: 2010-08-14
forum: Mythbuntu
---

### Post by davidstoll on 2010-08-14
No channel guide (says "unknown") in mythtv frontend.

Can anyone please help me?

When I access Mythweb, I get this...


    datetime:  2010-08-14 22:37:02 (EDT)
    errornum:  256
  error type:  User Error
error string:  SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed
    filename:  /usr/share/mythtv/mythweb/modules/tv/classes/Program.php
  error line:  346

==========================================================================

Backtrace: 

    file:  /usr/share/mythtv/mythweb/modules/tv/classes/Program.php
    line:  346
   class:  
function:  trigger_error
    type:  
    args:  Array
(
    [0] => SQL Error: Table './mythconverg/program' is marked as crashed and last (automatic?) repair failed
    [1] => 256
)

    file:  /usr/share/mythtv/mythweb/modules/tv/classes/Program.php
    line:  320
   class:  Program
function:  update_fancy_desc
    type:  ->
    args:  Array ( )
    file:  /usr/share/mythtv/mythweb/modules/tv/includes/recording_schedules.php
    line:  89
   class:  Program
function:  __construct
    type:  ->
    args:  Array
(
    [0] => Array
        (
            [0] => 
            [1] => 
            [2] => 
            [3] => 
            [4] => 
            [5] => 
            [6] => 
            [7] => 
            [8] => 
            [9] => 0
            [10] => 0
            [11] => 1281843300
            [12] => 1281847020
            [13] => 0
            [14] => 0
            [15] => 0
            [16] => 
            [17] => 0
            [18] => 0
            [19] => 0
            [20] => 0
            [21] => 6
            [22] => 497
            [23] => 2
            [24] => 15
            [25] => 6
            [26] => 1281843300
            [27] => 1281847020
            [28] => 0
            [29] => 0
            [30] => Default
            [31] => 0
            [32] => 
            [33] => 
            [34] => 
            [35] => 1281839123
            [36] => 0.000000
            [37] => 
            [38] => 0
            [39] => Default
            [40] => 0
            [41] => 0
            [42] => Default
            [43] => 0
            [44] => 0
            [45] => 0
            [46] => 
        )

)

    file:  /usr/share/mythtv/mythweb/modules/tv/handler.php
    line:  62
   class:  
function:  require_once
    type:  
    args:  Array
(
    [0] => /usr/share/mythtv/mythweb/modules/tv/includes/recording_schedules.php
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

        )

    [backend] => Array
        (
            [*****] => Array
                (
                    [proto_version] => Array
                        (
                            [last_check_version] => 56
                            [last_check_time] => 1281839374
                        )

                )

            [timezone] => Array
                (
                    [value] => EST
                    [last_check_time] => 1281839374
                )

        )

)

==========================================================================

$_SERVER: Array
(
    [REDIRECT_STATUS] => 200
    [HTTP_HOST] => ****
    [HTTP_CONNECTION] => keep-alive
    [HTTP_USER_AGENT] => Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US) AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.125 Safari/533.4
    [HTTP_REFERER] => [http://*****/mythweb/tv/list](http://*****/mythweb/tv/list)
    [HTTP_ACCEPT] => application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
    [HTTP_ACCEPT_ENCODING] => gzip,deflate,sdch
    [HTTP_ACCEPT_LANGUAGE] => en-US,en;q=0.8
    [HTTP_ACCEPT_CHARSET] => ISO-8859-1,utf-8;q=0.7,*;q=0.3
    [HTTP_COOKIE] => mythweb_tmpl=default; mythweb_skin=default; mythweb_id=34ikile6nakig74ooqfj6a6vv2
    [PATH] => /usr/local/bin:/usr/bin:/bin
    [SERVER_SIGNATURE] => <address>Apache/2.2.14 (Ubuntu) Server at ***** Port ****</address>

    [SERVER_SOFTWARE] => Apache/2.2.14 (Ubuntu)
    [SERVER_NAME] => *****
    [SERVER_ADDR] => *****
    [SERVER_PORT] => ****
    [REMOTE_ADDR] => *****
    [DOCUMENT_ROOT] => /var/www
    [SERVER_ADMIN] => webmaster@localhost
    [SCRIPT_FILENAME] => /var/www/mythweb/mythweb.php
    [REMOTE_PORT] => 47375
    [REDIRECT_URL] => /mythweb/tv/list
    [GATEWAY_INTERFACE] => CGI/1.1
    [SERVER_PROTOCOL] => HTTP/1.1
    [REQUEST_METHOD] => GET
    [QUERY_STRING] => 
    [REQUEST_URI] => /mythweb/tv/list
    [SCRIPT_NAME] => /mythweb/mythweb.php
    [PATH_INFO] => /tv/list
    [PATH_TRANSLATED] => /var/www/tv/list
    [PHP_SELF] => /mythweb/mythweb.php/tv/list
    [REQUEST_TIME] => 1281839821
    [STATUS] => 200
    [URL] => /mythweb/tv/list
    [HTTP_PORT] => ****
)

==========================================================================

$constant_list["user"]: Array
(
    [ERROR] => 512
    [E_ASSERT_ERROR] => 4096
    [FATAL] => 256
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
    [hostname] => *****
    [http_host] => *****
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
    [root_url] => http://*****/mythweb/
    [searchtype_keyword] => 3
    [searchtype_manual] => 5
    [searchtype_people] => 4
    [searchtype_power] => 1
    [searchtype_title] => 2
    [skin] => default
    [skin_img_url] => http://*****/mythweb/skins/default/img/
    [skin_url] => http://*****/mythweb/skins/default/
    [star_character] => &#9733;
    [stream_url] => http://*****//mythweb/
    [tb] => 1099511627776
    [timeslot_blocks] => 3
    [timeslot_size] => 300
    [timeslotbar_skip] => 20
    [tmpl] => default
    [tmpl_dir] => modules/tv/tmpl/default/
)

---

### Post by ian dobson on 2010-08-15
Hi,

Looks as if one of the tables in mysql is marked as corrupt.

Maybe try running :-

 mysql  -u USER -pPASSWORD -D mythconverg -e "repair TABLE program;"

where USER is your mysql user and PASSWORD is the password 

Regards
Ian Dobson

---

### Post by davidstoll on 2010-08-15
> **ian dobson said:**
> Hi,

Looks as if one of the tables in mysql is marked as corrupt.

Maybe try running :-

 mysql  -u USER -pPASSWORD -D mythconverg -e "repair TABLE program;"

where USER is your mysql user and PASSWORD is the password 

Regards
Ian Dobson




It seems to only give me the options I could try when I run it...kind of like when you run a program with incorrect options (or with no options or with -h) it shows you what you "could" or "should" do.

> 
$ mysql -u mythtv -p xxxxxxxx mythconverge -e "repair TABLE program;"

mysql  Ver 14.14 Distrib 5.1.41, for debian-linux-gnu (i486) using readline 6.1
Copyright 2000-2008 MySQL AB, 2008 Sun Microsystems, Inc.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license
Usage: mysql [OPTIONS] [database]
  -?, --help          Display this help and exit.
  -I, --help          Synonym for -?
  --auto-rehash       Enable automatic rehashing. One doesn't need to use
                      'rehash' to get table and field completion, but startup
                      and reconnecting may take a longer time. Disable with
                      --disable-auto-rehash.
  -A, --no-auto-rehash 
                      No automatic rehashing. One has to use 'rehash' to get
                      table and field completion. This gives a quicker start of
                      mysql and disables rehashing on reconnect. WARNING:
                      options deprecated; use --disable-auto-rehash instead.
  -B, --batch         Don't use history file. Disable interactive behavior.
                      (Enables --silent)
  --character-sets-dir=name 
                      Directory where character sets are.
  --column-type-info  Display column type information.
  -c, --comments      Preserve comments. Send comments to the server. The
                      default is --skip-comments (discard comments), enable
                      with --comments
  -C, --compress      Use compression in server/client protocol.
  -#, --debug[=#]     This is a non-debug version. Catch this and exit
  --debug-check       Check memory and open file usage at exit.
  -T, --debug-info    Print some debug info at exit.
  -D, --database=name Database to use.
  --default-character-set=name 
                      Set the default character set.
  --delimiter=name    Delimiter to be used.
  -e, --execute=name  Execute command and quit. (Disables --force and history
                      file)
  -E, --vertical      Print the output of a query (rows) vertically.
  -f, --force         Continue even if we get an sql error.
  -G, --named-commands 
                      Enable named commands. Named commands mean this program's
                      internal commands; see mysql> help . When enabled, the
                      named commands can be used from any line of the query,
                      otherwise only from the first line, before an enter.
                      Disable with --disable-named-commands. This option is
                      disabled by default.
  -g, --no-named-commands 
                      Named commands are disabled. Use \* form only, or use
                      named commands only in the beginning of a line ending
                      with a semicolon (;) Since version 10.9 the client now
                      starts with this option ENABLED by default! Disable with
                      '-G'. Long format commands still work from the first
                      line. WARNING: option deprecated; use
                      --disable-named-commands instead.
  -i, --ignore-spaces Ignore space after function names.
  --local-infile      Enable/disable LOAD DATA LOCAL INFILE.
  -b, --no-beep       Turn off beep on error.
  -h, --host=name     Connect to host.
  -H, --html          Produce HTML output.
  -X, --xml           Produce XML output
  --line-numbers      Write line numbers for errors.
  -L, --skip-line-numbers 
                      Don't write line number for errors. WARNING: -L is
                      deprecated, use long version of this option instead.
  -n, --unbuffered    Flush buffer after each query.
  --column-names      Write column names in results.
  -N, --skip-column-names 
                      Don't write column names in results. WARNING: -N is
                      deprecated, use long version of this options instead.
  -O, --set-variable=name 
                      Change the value of a variable. Please note that this
                      option is deprecated; you can set variables directly with
                      --variable-name=value.
  --sigint-ignore     Ignore SIGINT (CTRL-C)
  -o, --one-database  Only update the default database. This is useful for
                      skipping updates to other database in the update log.
  --pager[=name]      Pager to use to display results. If you don't supply an
                      option the default pager is taken from your ENV variable
                      PAGER. Valid pagers are less, more, cat [> filename],
                      etc. See interactive help (\h) also. This option does not
                      work in batch mode. Disable with --disable-pager. This
                      option is disabled by default.
  --no-pager          Disable pager and print to stdout. See interactive help
                      (\h) also. WARNING: option deprecated; use
                      --disable-pager instead.
  -p, --password[=name] 
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty.
  -P, --port=#        Port number to use for connection or 0 for default to, in
                      order of preference, my.cnf, $MYSQL_TCP_PORT,
                      /etc/services, built-in default (3306).
  --prompt=name       Set the mysql prompt to this value.
  --protocol=name     The protocol of connection (tcp,socket,pipe,memory).
  -q, --quick         Don't cache result, print it row by row. This may slow
                      down the server if the output is suspended. Doesn't use
                      history file.
  -r, --raw           Write fields without conversion. Used with --batch.
  --reconnect         Reconnect if the connection is lost. Disable with
                      --disable-reconnect. This option is enabled by default.
  -s, --silent        Be more silent. Print results with a tab as separator,
                      each row on new line.
  -S, --socket=name   Socket file to use for connection.
  --ssl               Enable SSL for connection (automatically enabled with
                      other flags). Disable with --skip-ssl.
  --ssl-ca=name       CA file in PEM format (check OpenSSL docs, implies
                      --ssl).
  --ssl-capath=name   CA directory (check OpenSSL docs, implies --ssl).
  --ssl-cert=name     X509 cert in PEM format (implies --ssl).
  --ssl-cipher=name   SSL cipher to use (implies --ssl).
  --ssl-key=name      X509 key in PEM format (implies --ssl).
  --ssl-verify-server-cert 
                      Verify server's "Common Name" in its cert against
                      hostname used when connecting. This option is disabled by
                      default.
  -t, --table         Output in table format.
  --tee=name          Append everything into outfile. See interactive help (\h)
                      also. Does not work in batch mode. Disable with
                      --disable-tee. This option is disabled by default.
  --no-tee            Disable outfile. See interactive help (\h) also. WARNING:
                      option deprecated; use --disable-tee instead
  -u, --user=name     User for login if not current user.
  -U, --safe-updates  Only allow UPDATE and DELETE that uses keys.
  -U, --i-am-a-dummy  Synonym for option --safe-updates, -U.
  -v, --verbose       Write more. (-v -v -v gives the table output format).
  -V, --version       Output version information and exit.
  -w, --wait          Wait and retry if connection is down.
  --connect_timeout=# Number of seconds before connection timeout.
  --max_allowed_packet=# 
                      Max packet length to send to, or receive from server
  --net_buffer_length=# 
                      Buffer for TCP/IP and socket communication
  --select_limit=#    Automatic limit for SELECT when using --safe-updates
  --max_join_size=#   Automatic limit for rows in a join when using
                      --safe-updates
  --secure-auth       Refuse client connecting to server if it uses old
                      (pre-4.1.1) protocol
  --server-arg=name   Send embedded server this as a parameter.
  --show-warnings     Show warnings after every statement.

Default options are read from the following files in the given order:
/etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf 
The following groups are read: mysql client
The following options may be given as the first argument:
--print-defaults	Print the program argument list and exit
--no-defaults		Don't read default options from any options file
--defaults-file=#	Only read default options from the given file #
--defaults-extra-file=# Read this file after the global files are read

Variables (--variable-name=value)
and boolean options {FALSE|TRUE}  Value (after reading options)
--------------------------------- -----------------------------
auto-rehash                       TRUE
character-sets-dir                (No default value)
column-type-info                  FALSE
comments                          FALSE
compress                          FALSE
debug-check                       FALSE
debug-info                        FALSE
database                          (No default value)
default-character-set             latin1
delimiter                         ;
vertical                          FALSE
force                             FALSE
named-commands                    FALSE
ignore-spaces                     FALSE
local-infile                      FALSE
no-beep                           FALSE
host                              (No default value)
html                              FALSE
xml                               FALSE
line-numbers                      TRUE
unbuffered                        FALSE
column-names                      TRUE
sigint-ignore                     FALSE
port                              3306
prompt                            mysql> 
quick                             FALSE
raw                               FALSE
reconnect                         FALSE
socket                            /var/run/mysqld/mysqld.sock
ssl                               FALSE
ssl-ca                            (No default value)
ssl-capath                        (No default value)
ssl-cert                          (No default value)
ssl-cipher                        (No default value)
ssl-key                           (No default value)
ssl-verify-server-cert            FALSE
table                             FALSE
user                              mythtv
safe-updates                      FALSE
i-am-a-dummy                      FALSE
connect_timeout                   0
max_allowed_packet                16777216
net_buffer_length                 16384
select_limit                      1000
max_join_size                     1000000
secure-auth                       FALSE
show-warnings                     FALSE


---

### Post by ian dobson on 2010-08-15
Hi,

Works for me:-

```
mysql -u mythtv -pXXXXX -D mythconverg -e "repair TABLE program;"
+---------------------+--------+----------+----------+
| Table               | Op     | Msg_type | Msg_text |
+---------------------+--------+----------+----------+
| mythconverg.program | repair | status   | OK       |
+---------------------+--------+----------+----------+
```

Note the -D infront of mythconverg and no space between the -p and the password

Regards
Ian Dobson

---

### Post by davidstoll on 2010-08-15
> **ian dobson said:**
> Hi,
```
mysql -u mythtv -pXXXXX -D mythconverg -e "repair TABLE program;"
+---------------------+--------+----------+----------+
| Table               | Op     | Msg_type | Msg_text |
+---------------------+--------+----------+----------+
| mythconverg.program | repair | status   | OK       |
+---------------------+--------+----------+----------+
```

Note the -D infront of mythconverg and no space between the -p and the password


Shhesh, I can't follow directions.  :(

$ mysql -u mythtv -pxxxxxxxx -D mythconverge -e "repair TABLE program;"

gives me...

ERROR 1044 (42000): Access denied for user 'mythtv'@'localhost' to database 'mythconverge'

---

### Post by ian dobson on 2010-08-15
Hi,

Do you have mythweb installed? If yes you can repair the tables through the setup,database menu.

Otherwise I think your passowrd is incorrect and the copy paste of the command is still missing the -D

Have a look in  /etc/mythtv/mysql.txt for the correct login name/password.

Regards
Ian Dobson

---

### Post by davidstoll on 2010-08-15
> **ian dobson said:**
> Hi,

Do you have mythweb installed? If yes you can repair the tables through the setup,database menu.

Otherwise I think your passowrd is incorrect and the copy paste of the command is still missing the -D

Have a look in  /etc/mythtv/mysql.txt for the correct login name/password.

Regards
Ian Dobson

Yeah, what the %$#*&???  I have no idea why it didn't copy paste...I guess I thought it copied, but didn't and I pasted the old one and didn't realize it.  I did use -D and the password is correct.  Thanks for the path to that file, I didn't know it was even there.


$ mysql -u mythtv -pxxxxxxxx -D mythconverge -e "repair TABLE program;"
ERROR 1044 (42000): Access denied for user 'mythtv'@'localhost' to database 'mythconverge'

I wonder if that is because the backend is running...?


I'm repairing by mythweb right now...also didn't know that existed.

uh, yup, that fixed it!!!  Hurray!  It didn't give me any indication that it was "working"...it was basically instantaneous I guess...?

Thank you Ian Dobson!  You're the man!  I just can't get over the helpfulness that the opensource community gives...for free.

I hope that one day I'll have enough knowledge to be able to give back.

My wifes computer has a problem with Windows and hell if I can find any help.

:D

---

### Post by ian dobson on 2010-08-16
Hi,

Glad to be of service. 

Maybe pm me with a description of the problem with your wifes computer. I can't promise that I can solve all problems but it's worth a try.

Regards
Ian Dobson

---

