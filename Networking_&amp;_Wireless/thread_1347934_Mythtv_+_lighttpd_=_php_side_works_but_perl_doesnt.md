---
title: "Mythtv + lighttpd = php side works but perl doesnt."
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Amp_God on 2009-12-06
Anyone using lighttpd for hosting mythweb? The php side works perfectly but perl cant connect to the database for some reason.

Here is the lighttpd 10-mythweb.conf
```

server.modules   += ( "mod_cgi", "mod_fastcgi", "mod_rewrite", "mod_setenv" )

url.rewrite = (
    "^/mythweb(/tv.*|/music.*|/video.*|/weather.*|/settings.*|/status.*|/backend_log.*)$" => "/mythweb/mythweb.php/$1",
    "^/mythweb(/pl(/.*)?)$" => "/mythweb/mythweb.pl/$1"
 )

$HTTP["url"] =~ "^/mythweb/" {
    fastcgi.server = (
        ".php" => ((
            "bin-path" => "/usr/bin/php-cgi",
            "socket"   => "/var/run/lighttpd/mythtv-php-fcgi.socket",
            "min-procs" => 1,
            "max-procs" => 1,
            "max-load-per-proc" => 500,
            "idle-timeout" => 20,
            "broken-scriptfilename" => "enable",
            "bin-environment" => (
                "PHP_FCGI_CHILDREN" => "0",
                "PHP_FCGI_MAX_REQUESTS" => "10000",
                "db_server"   => "localhost",
                "db_name"     => "mythconverg",
                "db_login"    => "mythtv",
                "db_password" => "nicepassword"
            )
        ))
    )

    setenv.add-environment = (
        "db_server"   => "localhost",
        "db_name"     => "mythconverg",
        "db_login"    => "mythtv",
        "db_password" => "nicepassword"
    )

    cgi.assign = (
        ".pl"  => "/usr/bin/perl"
    )

    index-file.names = ( "mythweb.php" )
}

```The perl side throws this error:
```

Cannot connect to database:   
```Software versions:
```

lighttpd                                   1.4.22-1ubuntu4
php5-cgi                                   5.2.6.dfsg.1-3ubuntu4.4  
perl                                       5.10.0-19ubuntu1.1
```Quessing its trouble with the database variables on the cgi part.
Any suggestions?

---

