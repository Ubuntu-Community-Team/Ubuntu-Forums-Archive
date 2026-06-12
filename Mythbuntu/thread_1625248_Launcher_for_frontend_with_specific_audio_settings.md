---
title: "Launcher for frontend with specific audio settings?"
date: 2010-11-18
forum: Mythbuntu
---

### Post by embolalia1187 on 2010-11-18
Is it possible to make a launcher/shortcut/command that will launch the frontend with certain options changed?

Specifically, I have one video card that drives both my HDTV and my VGA monitor. Since one's sound is HDMI, and the other is analog, they use different sound devices. So every time I want to watch on the TV, I have to go into the settings and change the sound option to ALSA:HDMI, and if I want to go back to the VGA screen, I have to change it to ALSA:default. I'd like to be able to put a launcher on the HDMI part of the desktop that automatically changes the sound to HDMI when started from there, and one on the VGA desktop that changes it to default. Is that possible? (Or, is there a way to make ALSA change its "default", and work that into a launcher?)

---

### Post by duiker.ts on 2010-11-21
Hi,

I had a similar problem, and solved it with a toggle button on my remote. The button calls a perl script (on the frontend) that changes the SQL db on the backend. You can probably use some of it to construct your launcher.

```
#!/usr/bin/perl

# PERL MODULE WE WILL BE USING
use DBI;

# MySQL CONFIG VARIABLES
$host = "<IP address>";
$database = "mythconverg";
$tablename = "settings";
$user = "mythtv";
$pw = "<password";

# PERL MYSQL CONNECT
$dbh = DBI->connect("dbi:mysql:database=$database;host=$host",$user,$pw)
    or die "Couldn't connect to database: " . DBI->errstr;

# DEFINE A MySQL QUERY - CHECK AudioOutputDevice
$myquery = "SELECT * FROM $tablename where value = 'AudioOutputDevice' and hostname = 'myth-front'";

# EXECUTE THE QUERY
$sth = $dbh->prepare($myquery)
    or die "Couldn't prepare statement: " . $dbh->errstr;

$sth->execute()
    or die "Couldn't execute statement: " . $sth->errstr;

# FETCHROW ARRAY
@data = $sth->fetchrow_array();


# TOGGLE VALUES
if ($data[1] eq "ALSA:hdmi:CARD=NVidia,DEV=0") {
    $card = "ALSA:iec958:CARD=NVidia,DEV=0";
    $channels = "6";
} else {
    $card = "ALSA:hdmi:CARD=NVidia,DEV=0";
    $channels = "2";
};


# WRITE NEW VALUES
$myquery = "UPDATE $tablename SET data = '$card' WHERE value = 'AudioOutputDevice' and hostname = 'myth-front'";
$sth = $dbh->prepare($myquery)
    or die "Couldn't prepare statement: " . $dbh->errstr;
$sth->execute()
    or die "Couldn't execute statement: " . $sth->errstr;

$myquery = "UPDATE $tablename SET data = $channels WHERE value = 'MaxChannels' and hostname = 'myth-front'";
$sth = $dbh->prepare($myquery)
    or die "Couldn't prepare statement: " . $dbh->errstr;
$sth->execute()
    or die "Couldn't execute statement: " . $sth->errstr;

$sth->finish();
$dbh->disconnect;
```

---

