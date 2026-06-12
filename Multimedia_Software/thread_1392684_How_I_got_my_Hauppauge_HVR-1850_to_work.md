---
title: "How I got my Hauppauge HVR-1850 to work"
date: 2010-01-28
forum: Multimedia Software
---

### Post by goatgonads on 2010-01-28
I wanted to post this before I forgot what I did, if this is already posted, please disregard it.
 
This was installed on Ubuntu 9.10.
 
How I got my Hauppauge HVR-1850 to work with a lightweight television application.
 
Not being able to use a TV app in linux was the only thing keeping me chained to windows for years. Now that I have gotten it to work, I would like to try and help other people in my situation.
 
My second frustration was that most of the applications out there, and instructions are for European signals, which are quite different that those used in the United States.
 
The directions below are for receiving a Digital/QAM-256 signal. This requires that the coax cable connection be plugged into the antenna connection rather than the cable connection.
 
I was unable to find a stand alone channel scan application that worked well for me using Comcast cable, in Michigan, United States. Mythtv has proven to be the best and most compatible application for people in the United States, but I wanted a more lightweight, user friendly application. For this reason, I installed MythTV so that I can &#8220;extract' the channel scan information from it. I am sure there are easier ways, but this worked great for me the first try.
 
There are dozens of guides covering how to install Mythtv, so I will skip that part. Once installed, after you have scanned for channels, you will need to enter the Mythtv FRONTEND and record the password listed under &#8220;Setup&#8221;. It is case sensitive. Next, I used the following script to export my channel scan:
 
#!/usr/bin/perl -w
 
use strict;
use DBI;
use Getopt::Long;
 
my $dbhost="127.0.0.1";
my $database="mythconverg";
my $user="mythtv";
my $pass="INSERT PASSWORD HERE";
my $sourceid = 1;
my $hidden = 0;
 
GetOptions('dbhost=s'=>\$dbhost,
'database=s'=>\$database,
'user=s'=>\$user,
'pass=s'=>\$pass,
'sourceid=i'=>\$sourceid,
'hidden!'=>\$hidden
) || die "Usage:";
 
my $dbh = DBI->connect("dbi:mysql:database=$database:host=$dbhost","$user","$pass") || die "Cannot connect to database ($!)\n";
 
my $sql = sprintf("SELECT callsign, frequency, modulation, serviceid
FROM channel JOIN dtv_multiplex USING (mplexid)
WHERE channel.sourceid = ? %s
ORDER BY frequency",
($hidden ? "" : "AND channel.visible = 1")
);
my $sth = $dbh->prepare($sql);
$sth->execute($sourceid);
 
while (my @row=$sth->fetchrow_array) {
my $callsign = $row[0];
my $frequency = $row[1];
my $modulation = uc $row[2];
my $serviceid = $row[3];
 
printf "$callsign:$frequency:$modulation:0:0:$serviceid\n";
}
 
$dbh->disconnect;
 
 
Copy the aforementioned text, open up the terminal and type: gedit myth.sh
Paste the script into the opened window, and change the password on line 10, to the one that you recorded from the Mythtv frontend. Save, and close the open gedit window. 
 
From the terminal enter: chmod 777 myth.sh
Followed by: ./myth.sh
(you may have to use ./myth.sh >> channels.conf to export, I forget!)
 
From here, you should have a channels.conf file located in your home directory.
 
I uninstalled Mythtv myself at this point, but that is up to you.
 
The TV application that I have chosen to use is ME-TV. The developer is a geat guy, and he spent many hours helping me get this working. I cannot thank him enough.
 
You may need to install the following (I used synaptic package manager):
 
gnome-common
libsqlite3-dev
libgconf2-dev
libglib2.0-dev
libgconf2-dev
libgtkmm-2.4-dev
libgconfmm-2.6-dev
libvlc-dev
vlc
  libunique-dev

The following instructions are for the BETA (1.2) package that has fixed issues for me. 
Once this version becomes the stable release, you can follow the install guide at ([http://me-tv.sourceforge.net/building.html](http://me-tv.sourceforge.net/building.html))
 
You can check the current version at: [https://launchpad.net/me-tv](https://launchpad.net/me-tv)
 
To install Me-Tv I used the following, for the BETA version:
 
sudo apt-get install libgnomemm-2.6-dev libgnomeuimm-2.6-dev libgtkmm-2.4-dev libglademm-2.4-dev libxtst-dev libgnet-dev libsqlite3-dev libvlc-dev

sudo apt-get install build-essential bzr

**Edit** You could just install all of these with one command such as:
sudo apt-get install libgnomemm-2.6-dev libgnomeuimm-2.6-dev libgtkmm-2.4-dev libglademm-2.4-dev libxtst-dev libgnet-dev libsqlite3-dev libvlc-dev gnome-common libsqlite3-dev libgconf2-dev libglib2.0-dev libgconf2-dev libgtkmm-2.4-dev libgconfmm-2.6-dev libvlc-dev vlc libunique-dev build-essential bzr libxine-dev
 
bzr branch lp:~lamothe/me-tv/1.2
 
cd 1.2
 
./autogen.sh
 
make
 
sudo make install
 
 
Restart, not sure if needed, but I did.
 
Open Me-Tv, it should be under sound/tv apps
 
Click on &#8220;Import Existing Channels.conf&#8221; and direct it to your scan file that you produced in step one.
 
If tells you that there are duplicates, I would just exit me-tv because you will need to go through and rename your channels.
 
If this is the case, enter your home folder and open your channels.conf file.
 
You should have a bunch of lines that look like this:
 
69:369000000:QAM_256:0:0:8
 
you will need to change the numbers before the : in each line. In this case the numbers to change would be 69.
To fix duplicates, I just renumbered all of my channels starting at 1.
 
Once you are done, save the file and import your new file into me-tv.
 
Now, you can watch the channels, figure out what they are and rename them in your channels.conf file as you wish by editing the text before the first colon.
 
I also moved my channels around in my channels.conf file by the order that I liked to watch them, and removed the crappy channels that I do not watch. You will have to delete your channels from me-tv and re-import them for changes to take effect.
 
Lastly, right now before you forget, make a backup of your channels.conf file somewhere. Even if you have to email it to yourself.

Edit the EPG page size (under preferences in Me-TV) to however many channels you would like to appear in the menu.

---

### Post by merschdawg06 on 2010-02-12
O......M.....G.  It's finally working!  I was able to bypass MythTV altogether.  I just pointed Me TV to look at the us-ATSC-center-frequencies-8VSB scan file located in /usr/share/dvb/atsc.  It picked up all my digital channels(I pick up the Springfield, MO signals).  But yeah, after ignoring the first step in your guide I did everything else and it works!  Thanks so much!  Now I just need to get my Zune to work in Ubuntu and I think I can finally permanently switch.

---

### Post by goatgonads on 2010-02-15
Glad to hear that it helped someone.

---

