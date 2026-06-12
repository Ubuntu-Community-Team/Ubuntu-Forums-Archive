---
title: "ZoneMurder"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Fitch on 2009-11-02
I posted this on the zoneminder forum and got zero replies.
I hope there may be some more feedback here as I am at my wits end with this.

The beginning:
I have an Emachines E4026 computer with a "Stealth Big Brother Au4" video surveillance card (4 cameras) working on XP

XP has changed so much that the file system no longer allows the automatic changing of directory names (this is done at midnight so that the directory day00 becomes day01, the day01 directory becomes day02, etc up to day28 which is deleted.
This means that I can instantly find what happened e.g 3 days ago without having to trawl through thousands of files in one directory.
No more.

I thought 'why not try Linux', couldn't be any worse....

I partitioned the directory with the Ubuntu CD, kept my Windows system with everything on it and installed Ubuntu on the other partition.

I then went about installing Zoneminder - or not.....
Zoneminder will not install at all, and there is no help in the forum.  The installation is badly flawed and the instruction manuals are well out of date as are the download sites, some which no longer exist.
I now believe this program to be obsolete due to lack of interest.

I thought I was being careful by installing Ubuntu in a partition and thereby keeping the original windows XP setup safe.
No.

Starting up Windows results in a "Please insert the recovery CD" screen
(No, I don't have one and Emachines haven't replied yet as to how much the CD will cost)
so I've lost the functionality of XP and therefore my surveillance system.
My business is located in what would be called a "tough neighbourhood" so I can't afford the downtime.

This is as far as I got with the damn zoneminder installer: 

brafferton@Cameras:~$ sudo aptitude update 
[sudo] password for brafferton:  
Writing extended state information... Done 
Hit [http://archive.canonical.com]("http://archive.canonical.com/") jaunty Release.gpg 
Ign [http://archive.canonical.com]("http://archive.canonical.com/") jaunty/partner Translation-en_GB    
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic Release.gpg                     
Hit [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports Release.gpg         
Ign [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports/main Translation-en_GB 
Ign [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports/restricted Translation-en_GB 
Get:1 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/main Translation-en_GB [63.7kB] 
Hit [http://archive.canonical.com]("http://archive.canonical.com/") jaunty Release                                  
Ign [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports Release                        
Hit [http://archive.canonical.com]("http://archive.canonical.com/") jaunty/partner Packages                         
Hit [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports/main Packages  
Get:2 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/restricted Translation-en_GB [3,402B] 
Get:3 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/universe Translation-en_GB [33.2kB] 
Hit [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports/restricted Packages 
Hit [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports/universe Packages 
Hit [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") jaunty-backports/multiverse Packages 
Get:4 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/multiverse Translation-en_GB [43.8kB] 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates Release.gpg                      
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/main Translation-en_GB 
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/restricted Translation-en_GB 
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/universe Translation-en_GB 
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/multiverse Translation-en_GB 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security Release.gpg 
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/main Translation-en_GB 
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/restricted Translation-en_GB 
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/universe Translation-en_GB 
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/multiverse Translation-en_GB 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic Release 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates Release 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security Release 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/main Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/restricted Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/main Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/restricted Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/universe Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/universe Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/multiverse Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/multiverse Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/main Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/restricted Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/main Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/restricted Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/universe Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/universe Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/multiverse Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-updates/multiverse Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/main Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/restricted Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/main Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/restricted Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/universe Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/universe Sources 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/multiverse Packages 
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic-security/multiverse Sources 
Fetched 144kB in 0s (192kB/s) 
Reading package lists... Done              
 
brafferton@Cameras:~$ sudo aptitude safe-upgrade 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Reading extended state information       
Initialising package states... Done 
The following packages will be REMOVED: 
  binutils-static{u}  
The following partially installed packages will be configured: 
  zoneminder  
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 1,425kB will be freed. 
Do you want to continue? [Y/n/?] y 
(Reading database ... 127591 files and directories currently installed.) 
Removing binutils-static ... 
Setting up zoneminder (1.24.2-1) ... 
Update agent starting at 09/10/31 15:10:58 
 
Initiating database upgrade to version 1.24.2 
Please ensure that ZoneMinder is stopped on your system prior to upgrading the database. 
Press enter to continue or ctrl-C to stop :  
 
Do you wish to take a backup of your database prior to upgrading? 
This may result in a large file in /tmp if you have a lot of events. 
Press 'y' for a backup or 'n' to continue : n 
 
Upgrading database to version 1.24.2 
Loading config from DB 
Saving config to DB 
Can't find upgrade from version '1.24.2' at /usr/bin/zmupdate.pl line 889, <STDIN> line 2. 
dpkg: error processing zoneminder (--configure): 
 subprocess installed post-installation script returned error exit status 255 
Errors were encountered while processing: 
 zoneminder 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
A package failed to install.  Trying to recover: 
Setting up zoneminder (1.24.2-1) ... 
Update agent starting at 09/10/31 15:11:09 
 
Initiating database upgrade to version 1.24.2 
Please ensure that ZoneMinder is stopped on your system prior to upgrading the database. 
Press enter to continue or ctrl-C to stop :  
 
Do you wish to take a backup of your database prior to upgrading? 
This may result in a large file in /tmp if you have a lot of events. 
Press 'y' for a backup or 'n' to continue : n 
 
Upgrading database to version 1.24.2 
Loading config from DB 
Saving config to DB 
Can't find upgrade from version '1.24.2' at /usr/bin/zmupdate.pl line 889, <STDIN> line 2. 
dpkg: error processing zoneminder (--configure): 
 subprocess installed post-installation script returned error exit status 255 
Errors were encountered while processing: 
 zoneminder 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Reading extended state information        
Initialising package states... Done 
Writing extended state information... Done 
 
brafferton@Cameras:~$ sudo aptitude install zoneminder 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Reading extended state information       
Initialising package states... Done 
The following partially installed packages will be configured: 
  zoneminder  
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 0B will be used. 
Writing extended state information... Done 
Setting up zoneminder (1.24.2-1) ... 
Update agent starting at 09/10/31 15:11:50 
 
Initiating database upgrade to version 1.24.2 
Please ensure that ZoneMinder is stopped on your system prior to upgrading the database. 
Press enter to continue or ctrl-C to stop :  
 
Do you wish to take a backup of your database prior to upgrading? 
This may result in a large file in /tmp if you have a lot of events. 
Press 'y' for a backup or 'n' to continue : n 
 
Upgrading database to version 1.24.2 
Loading config from DB 
Saving config to DB 
Can't find upgrade from version '1.24.2' at /usr/bin/zmupdate.pl line 889, <STDIN> line 2. 
dpkg: error processing zoneminder (--configure): 
 subprocess installed post-installation script returned error exit status 255 
Errors were encountered while processing: 
 zoneminder 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
A package failed to install.  Trying to recover: 
Setting up zoneminder (1.24.2-1) ... 
Update agent starting at 09/10/31 15:11:59 
 
Initiating database upgrade to version 1.24.2 
Please ensure that ZoneMinder is stopped on your system prior to upgrading the database. 
Press enter to continue or ctrl-C to stop :  
 
Do you wish to take a backup of your database prior to upgrading? 
This may result in a large file in /tmp if you have a lot of events. 
Press 'y' for a backup or 'n' to continue : n 
 
Upgrading database to version 1.24.2 
Loading config from DB 
Saving config to DB 
Can't find upgrade from version '1.24.2' at /usr/bin/zmupdate.pl line 889, <STDIN> line 2. 
dpkg: error processing zoneminder (--configure): 
 subprocess installed post-installation script returned error exit status 255 
Errors were encountered while processing: 
 zoneminder 
Reading package lists... Done              
Building dependency tree        
Reading state information... Done 
Reading extended state information        
Initialising package states... Done 
 
Done.. I have been 
 
Please help.

---

### Post by Fitch on 2009-11-03
This is the result if I try to install from:
[http://packages.ubuntu.com/karmic/i386/zoneminder/download](http://packages.ubuntu.com/karmic/i386/zoneminder/download),
using their suggestion of adding the site to the sources.lst
(after several attemts at installing, then removing...

root@Cameras:~# apt-get install zoneminder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libemail-date-format-perl libmime-lite-perl libmime-types-perl
  libmysqlclient15off libphp-serialization-perl nullmailer
The following NEW packages will be installed
  libemail-date-format-perl libmime-lite-perl libmime-types-perl
  libmysqlclient15off libphp-serialization-perl nullmailer zoneminder
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3,485kB of archives.
After this operation, 11.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libemail-date-format-perl.
(Reading database ... 128835 files and directories currently installed.)
Unpacking libemail-date-format-perl (from .../libemail-date-format-perl_1.002-1_all.deb) ...
Selecting previously deselected package libmime-lite-perl.
Unpacking libmime-lite-perl (from .../libmime-lite-perl_3.023-1_all.deb) ...
Selecting previously deselected package libmime-types-perl.
Unpacking libmime-types-perl (from .../libmime-types-perl_1.27-1_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.1.30really5.0.83-0ubuntu3_i386.deb) ...
Selecting previously deselected package libphp-serialization-perl.
Unpacking libphp-serialization-perl (from .../libphp-serialization-perl_0.32-1_all.deb) ...
Selecting previously deselected package zoneminder.
Unpacking zoneminder (from .../zoneminder_1.24.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package nullmailer.
Unpacking nullmailer (from .../nullmailer_1%3a1.04-1.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
Setting up libemail-date-format-perl (1.002-1) ...
Setting up libmime-lite-perl (3.023-1) ...
Setting up libmime-types-perl (1.27-1) ...
Setting up libmysqlclient15off (5.1.30really5.0.83-0ubuntu3) ...

Setting up libphp-serialization-perl (0.32-1) ...
Setting up zoneminder (1.24.1-1ubuntu2) ...
DBI connect('database=zm;host=localhost','zmuser',...) failed: Unknown database 'zm' at /usr/share/perl5/ZoneMinder/Config.pm line 89
Can't call method "prepare_cached" on an undefined value at /usr/share/perl5/ZoneMinder/Config.pm line 91.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/bin/zmupdate.pl line 49.
BEGIN failed--compilation aborted at /usr/bin/zmupdate.pl line 49.
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 255
Setting up nullmailer (1:1.04-1.1) ...
 * Starting mail-transfer-agent:                                         [ OK ] 

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Fitch on 2009-11-04
For crying out loud!
Somebody please answer...

Setting up zoneminder (1.24.1-1ubuntu2) ...
DBI connect('database=zm;host=localhost','zmuser',...) failed: Unknown database 'zm' at /usr/share/perl5/ZoneMinder/Config.pm line 89
Can't call method "prepare_cached" on an undefined value at /usr/share/perl5/ZoneMinder/Config.pm line 91.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/bin/zmupdate.pl line 49.
BEGIN failed--compilation aborted at /usr/bin/zmupdate.pl line 49.
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)


/usr/share/perl5/ZoneMinder/Config.pm is below.

# ==========================================================================
#
# ZoneMinder Config Module, $Date: 2008-07-25 10:48:16 +0100 (Fri, 25 Jul 2008) $, $Revision: 2612 $
# Copyright (C) 2001-2008  Philip Coombes
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
#
# ==========================================================================
#
# This module contains the common definitions and functions used by the rest 
# of the ZoneMinder scripts
#
package ZoneMinder::Config;

use 5.006;
use strict;
use warnings;

require Exporter;
require ZoneMinder::Base;

our @ISA = qw(Exporter ZoneMinder::Base);

# Items to export into callers namespace by default. Note: do not export
# names by default without a very good reason. Use EXPORT_OK instead.
# Do not simply export all your public functions/methods/constants.

# This allows declaration    use ZoneMinder ':all';
# If you do not need this, moving things directly into @EXPORT or @EXPORT_OK
# will save memory.
our @EXPORT_CONFIG; # Get populated by BEGIN

our %EXPORT_TAGS = (
    'constants' => [ qw(
        ZM_PID
    ) ]
);
push( @{$EXPORT_TAGS{config}}, @EXPORT_CONFIG );
push( @{$EXPORT_TAGS{all}}, @{$EXPORT_TAGS{$_}} ) foreach keys %EXPORT_TAGS;

our @EXPORT_OK = ( @{ $EXPORT_TAGS{'all'} } );

our @EXPORT = qw();

our $VERSION = $ZoneMinder::Base::VERSION;

use constant ZM_PID => "/var/run/zm/zm.pid"; # Path to the ZoneMinder run pid file
use constant ZM_CONFIG => "/etc/zm/zm.conf"; # Path to the ZoneMinder config file

use Carp;

# Load the config from the database into the symbol table
BEGIN
{
    no strict 'refs';

    my $config_file = ZM_CONFIG;
    ( my $local_config_file = $config_file ) =~ s|^.*/|./|;
    if ( -s $local_config_file && -r $local_config_file )
    {
        print( STDERR "Warning, overriding installed $local_config_file file with local copy\n" );
        $config_file = $local_config_file;
    }
    open( CONFIG, "<".$config_file ) or croak( "Can't open config file '$config_file': $!" );
    foreach my $str ( <CONFIG> )
    {
        next if ( $str =~ /^\s*$/ );
        next if ( $str =~ /^\s*#/ );
        my ( $name, $value ) = $str =~ /^\s*([^=\s]+)\s*=\s*(.+?)\s*$/;
        $name =~ tr/a-z/A-Z/;
        *{$name} = sub { $value };
        push( @EXPORT_CONFIG, $name );
    }
    close( CONFIG );

    use DBI;
    my $dbh = DBI->connect( "DBI:mysql:database=".&ZM_DB_NAME.";host=".&ZM_DB_HOST, &ZM_DB_USER, &ZM_DB_PASS );
    my $sql = "select * from Config";
    my $sth = $dbh->prepare_cached( $sql ) or croak( "Can't prepare '$sql': ".$dbh->errstr() );
    my $res = $sth->execute() or croak( "Can't execute: ".$sth->errstr() );
    while( my $config = $sth->fetchrow_hashref() )
    {
        *{$config->{Name}} = sub { $config->{Value} };
        push( @EXPORT_CONFIG, $config->{Name} );
    }
    $sth->finish();
    $dbh->disconnect();
}

1;
__END__

=head1 NAME

ZoneMinder::Config - ZoneMinder configuration module.

=head1 SYNOPSIS

  use ZoneMinder::Config qw(:all);

=head1 DESCRIPTION

The ZoneMinder::Config module is used to import the ZoneMinder configuration from the database. It will do this at compile time in a BEGIN block and require access to the zm.conf file either in the current directory or in its defined location in order to determine database access details, configuration from this file will also be included. If the :all or :config tags are used then this configuration is exported into the namespace of the calling program or module.

Once the configuration has been imported then configuration variables are defined as constants and can be accessed directory by name, e.g.

 $lang = ZM_LANG_DEFAULT;

=head2 EXPORT

None by default.
The :constants tag will export the ZM_PID constant which details the location of the zm.pid file
The :config tag will export all configuration from the database as well as any from the zm.conf file
The :all tag will export all above symbols.

=head1 SEE ALSO

[http://www.zoneminder.com](http://www.zoneminder.com)

=head1 AUTHOR

Philip Coombes, E<lt>philip.coombes@zoneminder.comE<gt>

=head1 COPYRIGHT AND LICENSE

Copyright (C) 2001-2008  Philip Coombes

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself, either Perl version 5.8.3 or,
at your option, any later version of Perl 5 you may have available.


=cut

---

### Post by stuman on 2009-11-04
I'm sorry you are having these difficulties.

I decided to grab a zone minder virtual machine to try and run, but I am stuck on trying to get usb cameras to work, as I have a couple already and don't want to purchase any IP addressable ones.

---

### Post by uniden9 on 2009-11-04
Fitch I'm having the same problem.  I had it working in 9.04, but a no go in 9.10.  The last hurdle left on my plate from the upgrade.

---

### Post by uniden9 on 2009-11-05
After messing around with my configuration, I finally got it to work.  I had to build an older version of the source. I download one of the 1.23, and just ran the 
./configure --with-webdir=your web dir --with-cgidir=you cgi dir

If you download a 1.24 version it seems to break on trying to upgrade.  

Its not important as to what you put in the --with commands as you do not need to install it.  You just the .configure to finish so it will create the db/zm_create.sql script. Unfortunately you will have to probably add a few -dev packages.

Then setup you database
sudo mysql < db/zm_create.sql

sudo mysql 
mysql> grant select,insert,update,delete on zm.* to 'zmuser'@localhost identified by 'zmpass';
mysql> exit;

After that I could get the package to install, and not error out on database connect errors.  But not that I already had it install, the mysql database got dropped in the ubuntu dist upgrade. I suspect it was another application that did that.  So I was not really installing, but more repairing.

Maybe this help you, or at least progress to a solution.

---

### Post by Fitch on 2009-11-05
I get no such file or directory when I type in ./configure --help 
I cannot get into mysql in root or my own (brafferton) account. 
I just says "ERROR 1045 (28000) Access denied for user 'brafferton'@'localhost' (using password YES). 
 
Not going according to plan so far....

---

### Post by Fitch on 2009-11-05
As suggested earlier, I have downloaded the code for ZoneMinder 1.23.3 and tried to use ./configure as per the installation instructions.
Again I hit the mysql dead end .
It bangs out with:
 "configure error: zm requires mysql/mysql.h"
I've checked, and actually have mysql server 5.1
But is this the right package.  Trying to install e.g. mysql client comes up "package failed", so again, no matter where I turn, there is something I am missing.
I can't get the right turning 'cos I'm on the wrong road.

---

### Post by Fitch on 2009-11-06
I think I managed to get past mysql.h  Haven't a clue how as I've tried so many things.

As for: sudo mysql < db/zm_create.sql
it just comes up:  bash: db/zm_create.sql: No such file or directory

When compiling Zoneminder 1.23.1, it comes up:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error 

I've checked the /var/run/mysqld/ and it's empty.

How does that get filled?

---

### Post by Fitch on 2009-11-07
I've actually managed to get zoneminder on (apparently). but when I call it up using the web browser http:\\localhost I get virtually the same problem:

Warning: mysql_pconnect() [function.mysql-pconnect]: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) in /usr/share/zoneminder/includes/database.php on line 32 
Could not connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

There is nothing in '/var/run/mysqld/ so no wonder it goes tits up.

Anybody got any ideas?

Is there anybody out there at all?, anywhere?

---

### Post by Fitch on 2009-11-08
This is an update: if anyone is interested, the previous posts show /var/run when apparently it should be /var/lib.
I altered my.conf to correct the fault.
Did it work?
did it Hell!
 
I tried to install zoneminder 1.24 which is why I need all this sql nonsense. ZM1.24 was uninstallable, so I installed (or so I thought) ZM 1.23
When having to apt-get install all the other stuff - which has taken a week so far with no joy, I always get at the end of the failed mission, "ZoneMinder 1.24 failed to install" ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/lib/mysqld/mysqld.sock' (2) 
 
This is driving me up the wal!

---

### Post by cratesthecynic on 2009-11-10
Fitch

I've seen your posts on the ZM forum and do sympathise with your situation.  I'm a bit of a noob with linux too and it seems ZM is notorious for being a pig to get running.

That said, I think you should bear in mind that ZM is FREE software and anyone who does offer you any help is doing it for nothing !  

When I set out to use/learn linux (this time.. after a couple of false starts) I selected ubuntu because of the size of its community.  Zm is a much smaller community and I think its only fair to assume proportionately LESS support !

In the past I've used the ZM 1.2x LiveCD installer (under Mandriva) which worked well.  I struggled installing the other bits & bobs I needed but my lack of Linux knowledge is what held me back.  This time I select Ubuntu 9.10 as my OS of choice specifically because of the amount of community help I might find... then installed the DEB file in the Ubuntu repositories - 1.24.1 - onto my box.  

I needed to hack the shared memory size, configure BTTV to detect my card, setup VNC, remove a load of default packages I didn't need and various other bits - but, I got it working.

I want to upgrade to 1.24.2 but don't know what's involved.  I too am waiting for an answer on the ZM forums.  I'd also like to know if 1.24.2 addresses the 'Apache hangs/socks' error.... no answer on that question yet either..... so you're not on your own.   If you want great support, BUY your software - the ZM developers owe us nothing.

A couple of thoughts...

Given that you've tried installing 1.23, why not scrap your dodgy setup altogether and go for the old Mandriva LiveCD ?  If you want the latest version, try the ZMLArch livecd instead from the same author. 

If ubunto it must be, then I think I'd splat the box, reinstall and bung ubuntu's own DEB of 1.24.1 onto it (as I did).  If that fails go for the ZMLarch CD.

Happy to help out if I can.... for what its worth ;o)

crates

---

### Post by Fitch on 2009-11-10
I do apologise for seeming "grumpy" on the posts.  My frustration is not really with Zoneminder or Ubuntu.  It is with a system that I did actually buy along with the relevant Windows XP proprietary application.  Sorry I seem to be taking it out on you lot.
 
AEI's "support" is to produce a web site with installation instructions, and that's your lot.  I only asked one question from that company who refused even to answer until I involved CPC - the distributor.  They categorically do not support this card any more as they have gone on to bigger and better things.  This was 3 months after I bought the thing.
 
My business premises have had this 4 camera system for 5 years now, running under XP.  The constant upgrades reduced the capability drastically for some unknown reason.
Hence the switch to Linux.
 
Both operating systems were on for a few days when the Ubuntu 9.10 package installed.  The XP partition died the same night, which was unfortunate as there was now no surveillance available (I used to try to get Zoneminder working during the day, and then switch to XP for night time security).
 
The panic started just about then.
 
The Christmas season is now upon us, and the likeliehood of enough guests using our accomodation is dwindling daily.  Hence the thought of a new camera system is dwindling with it.  I have to make do with what I've got,  which at the moment is 4 black screens.
 
I have indeed gone back to Jaunty, using the entire drive as XP was fried.  I also succeeded in installing ZoneMinder 1.23 and have now had both apparently working grea for 2 days now, except for that last little eensy teesy wee bit - the 4 black screens.
 
I hope this clarifies why I have been in such a bad mood, and I do hope you all accept my sincere apologies.
 
Now about these black screens..........

---

### Post by cratesthecynic on 2009-11-11
Sounds like BTTV isn't detecting your capture cards correctly. I had the same issue. Search the ZM site for "BTTV card type" for tips. 

I have an ebay 8*bt878 similar to this one [http://www.zoneminder.com/forums/viewtopic.php?t=12713](http://www.zoneminder.com/forums/viewtopic.php?t=12713) .  In my BTTV config I identify mine as:
card=102,102,102,102,102,102,102,102

I know the cheap pico cards - 4 input, single bt878 - are:
card=77

Read here [http://tldp.org/HOWTO/html_single/BTTV/#TUNING](http://tldp.org/HOWTO/html_single/BTTV/#TUNING)

Bung a photo of your card on the ZM forum and see if anyone knows.

---

### Post by Fitch on 2009-11-11
Thanks for the link. MAKEDEV didn't work unfortunately, should I now delete it?
 
xawtv gives 4 nice pictures though, with a couple of errors:
 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-16-generic)
xinerama 0: 1280x1024+0+0
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
get fences failed: -1
param: 6, val: 0
 
xawtv -hwscan produces
 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-16-generic)
looking for available devices
port 70-85
type : Xvideo, image scaler
name : Intel(R) Textured Video
 
port 86-86
type : Xvideo, image scaler
name : Intel(R) Video Overlay
 
/dev/video0: OK [ -device /dev/video0 ]
type : v4l2
name : BT878 video (GrandTec Multi Cap
flags: overlay capture
 
(If I set capture to "off")

---

### Post by Fitch on 2009-11-15
3 days later and I have pictures come up on Firefox.
 
I've done so much, I can't really remember how though!
 
I think, originally, I must have installed zoneminder as root then apache as the normal user, so permissions were all over the place.
 
Lots and lots of permissions later, all I'm left with is trying to see the stills on the event list. It records and saves and even exports the pictures, it just doesn't show them.

[IMG]http://www.braffertonguesthouse.co.uk/screen.png[/IMG]
 
Presumably I've got a couple of permissions to go.
 
I don't suppose anyone's got a list of what should be owned by www-data,and what should be owned by root?

---

### Post by grapnell on 2009-11-16
Fitch, I had the exact same problem as you.

Do this, and it will fix it.

Open synaptic, and completely remove the following packages: 

zoneminder, mysql-server- mysql-server5.1 and mysql-server-core ... 

***MAKE SURE YOU MARK THEM FOR COMPLETE REMOVAL*** This will remove all of the configuration files and everything... DO NOT just uninstall them... Use synaptic, it's the easiest.  AFTER you have COMPLETELY REMOVED the packages, then reinstall, and it should work. 

Good luck to you.

---

### Post by Fitch on 2009-11-16
I did actually try at first with those applications in mind, but soon found out that you had to include apache2 for complete removal.
 
So, Using Synaptic Package Manager, I deleted everything again plus apache 2 and apache2 common, did an apt-get autoremove, restarted the computer as user, reinstalled, did the instructions as per:
[http://www.zoneminder.com/wiki/index.php/Ubuntu_9.04_%28Jaunty%29_desktop_with_graphical_interface]("http://www.zoneminder.com/wiki/index.php/Ubuntu_9.04_%28Jaunty%29_desktop_with_graphical_interface")
 
and hey presto:
 
**Warning:** Division by zero in **/usr/share/zoneminder/zm_html_view_montage.php** on line **46** 
 
I first installed after logging into the computer as root on startup and did not notice this error as everything is absolutely perfect when the computer is root.
 
It's when it starts up as normal user.
 
So I de-installed everything again using Synaptic and installed as normal user, but the error won't go away.  This is on the computer with Zoneminder installed.
 
The other computers are fine!!  Open up Safari, call up the index page, select montage, Brilliant!!  All 4 cameras come up a treat!
 
I'm not going to throw the computer out the window, but I am slowly nudging it.

---

### Post by Fitch on 2009-11-16
Oops! Heads up!
 
I created a new group for all 4 monitors and, of course it works!!
 
You don't know how happy I am.
 
Yippee!!:popcorn:

---

### Post by Capetownlad on 2009-12-11
> **Fitch said:**
> For crying out loud!
Somebody please answer...

Setting up zoneminder (1.24.1-1ubuntu2) ...
DBI connect('database=zm;host=localhost','zmuser',...) failed: Unknown database 'zm' at /usr/share/perl5/ZoneMinder/Config.pm line 89
Can't call method "prepare_cached" on an undefined value at /usr/share/perl5/ZoneMinder/Config.pm line 91.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/bin/zmupdate.pl line 49.
BEGIN failed--compilation aborted at /usr/bin/zmupdate.pl line 49.
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)


/usr/share/perl5/ZoneMinder/Config.pm is below.

# ==========================================================================
#
# ZoneMinder Config Module, $Date: 2008-07-25 10:48:16 +0100 (Fri, 25 Jul 2008) $, $Revision: 2612 $
# Copyright (C) 2001-2008  Philip Coombes
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
#
# ==========================================================================
#
# This module contains the common definitions and functions used by the rest 
# of the ZoneMinder scripts
#
package ZoneMinder::Config;

use 5.006;
use strict;
use warnings;

require Exporter;
require ZoneMinder::Base;

our @ISA = qw(Exporter ZoneMinder::Base);

# Items to export into callers namespace by default. Note: do not export
# names by default without a very good reason. Use EXPORT_OK instead.
# Do not simply export all your public functions/methods/constants.

# This allows declaration    use ZoneMinder ':all';
# If you do not need this, moving things directly into @EXPORT or @EXPORT_OK
# will save memory.
our @EXPORT_CONFIG; # Get populated by BEGIN

our %EXPORT_TAGS = (
    'constants' => [ qw(
        ZM_PID
    ) ]
);
push( @{$EXPORT_TAGS{config}}, @EXPORT_CONFIG );
push( @{$EXPORT_TAGS{all}}, @{$EXPORT_TAGS{$_}} ) foreach keys %EXPORT_TAGS;

our @EXPORT_OK = ( @{ $EXPORT_TAGS{'all'} } );

our @EXPORT = qw();

our $VERSION = $ZoneMinder::Base::VERSION;

use constant ZM_PID => "/var/run/zm/zm.pid"; # Path to the ZoneMinder run pid file
use constant ZM_CONFIG => "/etc/zm/zm.conf"; # Path to the ZoneMinder config file

use Carp;

# Load the config from the database into the symbol table
BEGIN
{
    no strict 'refs';

    my $config_file = ZM_CONFIG;
    ( my $local_config_file = $config_file ) =~ s|^.*/|./|;
    if ( -s $local_config_file && -r $local_config_file )
    {
        print( STDERR "Warning, overriding installed $local_config_file file with local copy\n" );
        $config_file = $local_config_file;
    }
    open( CONFIG, "<".$config_file ) or croak( "Can't open config file '$config_file': $!" );
    foreach my $str ( <CONFIG> )
    {
        next if ( $str =~ /^\s*$/ );
        next if ( $str =~ /^\s*#/ );
        my ( $name, $value ) = $str =~ /^\s*([^=\s]+)\s*=\s*(.+?)\s*$/;
        $name =~ tr/a-z/A-Z/;
        *{$name} = sub { $value };
        push( @EXPORT_CONFIG, $name );
    }
    close( CONFIG );

    use DBI;
    my $dbh = DBI->connect( "DBI:mysql:database=".&ZM_DB_NAME.";host=".&ZM_DB_HOST, &ZM_DB_USER, &ZM_DB_PASS );
    my $sql = "select * from Config";
    my $sth = $dbh->prepare_cached( $sql ) or croak( "Can't prepare '$sql': ".$dbh->errstr() );
    my $res = $sth->execute() or croak( "Can't execute: ".$sth->errstr() );
    while( my $config = $sth->fetchrow_hashref() )
    {
        *{$config->{Name}} = sub { $config->{Value} };
        push( @EXPORT_CONFIG, $config->{Name} );
    }
    $sth->finish();
    $dbh->disconnect();
}

1;
__END__

=head1 NAME

ZoneMinder::Config - ZoneMinder configuration module.

=head1 SYNOPSIS

  use ZoneMinder::Config qw(:all);

=head1 DESCRIPTION

The ZoneMinder::Config module is used to import the ZoneMinder configuration from the database. It will do this at compile time in a BEGIN block and require access to the zm.conf file either in the current directory or in its defined location in order to determine database access details, configuration from this file will also be included. If the :all or :config tags are used then this configuration is exported into the namespace of the calling program or module.

Once the configuration has been imported then configuration variables are defined as constants and can be accessed directory by name, e.g.

 $lang = ZM_LANG_DEFAULT;

=head2 EXPORT

None by default.
The :constants tag will export the ZM_PID constant which details the location of the zm.pid file
The :config tag will export all configuration from the database as well as any from the zm.conf file
The :all tag will export all above symbols.

=head1 SEE ALSO

[http://www.zoneminder.com](http://www.zoneminder.com)

=head1 AUTHOR

Philip Coombes, E<lt>philip.coombes@zoneminder.comE<gt>

=head1 COPYRIGHT AND LICENSE

Copyright (C) 2001-2008  Philip Coombes

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself, either Perl version 5.8.3 or,
at your option, any later version of Perl 5 you may have available.


=cut

Hi Fitch
I am new to Ubuntu but have CCTV experience and have just found your post and wondered if you have had any success yet? I too am installing a security cam and Will see this through.
-Capetownlad

---

### Post by Fitch on 2009-12-11
Yes I eventually managed it.

Took 3 weeks, but after complete removal of Apache 2, Mysql, mysql server, mysql core, and zoneminder.
[FONT=Verdana]Again, using Synaptic,[/FONT] [FONT=Verdana]I then installed libdirac-dev and libdirac0c2a.
Then, Zoneminder 1.24.1.
[/FONT]
[http://www.zoneminder.com/forums/viewtopic.php?p=57717#57717](http://www.zoneminder.com/forums/viewtopic.php?p=57717#57717)

---

### Post by pibri on 2010-01-28
Fitch,

I have been trying on and off to get this working since the early Autumn!

HOW DID YOU DO IT???? 

I have posted on that zm forum you linked to.

I really want to get this running but I am on the verge of giving up.:(

Using Ubuntu 9.10 for every day use but 9.04 (partiton) for zm

---

### Post by danensis on 2010-02-02
I too have been struggling with ZoneMinder. I shouldn't say it on here, but I quite liked the Mandriva version, but they're no longer supporting the newer releases, and the version its on is not upgraded any more.

I tried the Arch version, but it is so basic it takes me back to RedHat version 2, and we've moved on a bit from those days.

I also had the issue where the first time I added new cameras nothing worked - or rather the same image appeared on all four cameras. By deleting them all and adding them again I got it to work.

I'm now going to try Ubuntu, as I want a version of Linux that is upgradeable - there are so many security problems these days I can't trust an out-of-date OS.

---

### Post by Aacron on 2011-05-06
My issue lately is that the Zoneminder .deb packages always seem to have something broken.  I made the *huge* mistake of using do-release-upgrade on my box, thinking that 11.x would be faster/more secure/etc than 10.04.  Zoneminder already had an issue or 20, but it worked well enough.  The upgrade completely screwed up the system.  I had all sorts of issues, with the monitor and video events working, but no stills, then it would do crazy things with camera every so often.  I've also noticed that the packages have almost always had issues on start-up or shutdown (something dealing with php/perl/something compilation errors).

I really wish that Zoneminder packages would be repaired to work 100% properly. The quality of the packages seems to be getting worse, too.

---

