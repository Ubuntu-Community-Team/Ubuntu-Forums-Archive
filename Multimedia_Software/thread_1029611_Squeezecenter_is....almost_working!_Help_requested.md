---
title: "Squeezecenter is....almost working! Help requested!"
date: 2009-01-03
forum: Multimedia Software
---

### Post by perryrt on 2009-01-03
So I have this Squeezebox I've been trying to get working again. It used to work great... under Windows.

Now that I'm using Ubuntu, though, I've got issues. I'm hoping someone can help me. I'm not a complete noob, but I'm far from an Ubuntu savant, too.

Anyway, I installed Squeezecenter using the .deb package from SlimDevices (ok, ok, Logitech.) using the most current stable version (7.3.1) and the instructions in their wiki ([here]("http://wiki.slimdevices.com/index.php/DebianPackage").) Seemed to install with no problems.

However..... I can't get it to read my mp3 library.

Specifically, when I ask it to scan my "Music" directory, it only finds the one file in the root of that directory, not all the files in the subdirectories. Additionally, I tried moving some random files to a "Test" directory and I couldn't get Squeezecenter to read them at all!

Here's what the "information" tab on the settings web tool reports:

[HTML]
SqueezeCenter Status

Version: 7.3.1 - 24372 @ Fri Dec 19 17:38:52 PST 2008

Hostname: perryrt-desktop

Server IP Address: 192.168.126.76

Server HTTP Port Number: 9000

Operating system: Debian - EN - utf8

Platform Architecture: i686-linux

Perl Version: 5.8.8 - i486-linux-gnu-thread-multi

MySQL Version: 5.0.51a-3ubuntu5.4

Total Players Recognized: 1
 
Library Statistics

Total Tracks: 1

Total Albums: 1

Total Artists: 1

Total Genres: 1

Total Playing Time: 0:04:08
 
Music Scan Details
Directory Scan   (1  of  1)   Complete  00:00:01

Playlist Scan   (  of  )   Complete  00:00:00

Merge Various Artists   (1  of  1)   Complete  00:00:00

Artwork Scan   (1  of  1)   Complete  00:00:00

Database Optimize   (  of  )   Complete  00:00:00

   (  of  )    

   (  of  )    

   (  of  )    

   (  of  )    

   (  of  )    

   (  of  )    

SqueezeCenter has finished scanning your music collection.
Total Time: 00:00:01 (Saturday, January 3, 2009 / 15:35)
 
Player Information
Information on all identified devices connected to SqueezeCenter
 
NextToTV

Player Model: squeezebox3

Firmware: 121

Player IP Address: 192.168.126.78

Player MAC Address: 00:04:50:09:46:f9
 
Folders
 
Cache Folder
/var/lib/squeezecenter/cache
Preferences Folder
/var/lib/squeezecenter/prefs
Plugin Folders
/var/lib/squeezecenter/cache/InstalledPlugins/Plugins, /usr/sbin/Plugins, /usr/share/squeezecenter/Plugins
SqueezeCenter Log File
SqueezeCenter keeps a log file for all application related activities (Audio Streaming, Infrared, etc) here:
/var/log/squeezecenter/server.log (100, 500, 1000 lines)
 
Scanner Log File
SqueezeCenter keeps a log file for all scanning related activities, including iTunes & MusicIP here:
/var/log/squeezecenter/scanner.log (100, 500, 1000 lines)
 

 [/HTML]

and here's the output (last few lines) of the "server" log file after I forced a restart (via *sudo /etc/init.d/squeezecenter restart*) a few minutes ago.

```

2009-01-03 15:17:41 squeezecenter_safe started.
[09-01-03 15:17:47.6066] Slim::Utils::PluginManager::enablePlugins (423) Couldn't load Slim::Plugin::PreventStandby::Plugin. Error: Plugin is incompatible with your platform.
[09-01-03 15:17:47.7692] main::checkDataSource (909) Warning: Schema updated or no tracks in the database, initiating scan.
[09-01-03 15:17:48.2368] Slim::Web::JSONRPC::requestMethod (383) request not dispatchable!
[09-01-03 15:19:56.0991] Slim::Schema::Storage::throw_exception (70) Error: Error executing 'SELECT me.id, me.url, me.content_type, me.title, me.titlesort, me.titlesearch, me.album, me.tracknum, me.timestamp, me.filesize, me.disc, me.remote, me.audio, me.audio_size, me.audio_offset, me.year, me.secs, me.cover, me.vbr_scale, me.bitrate, me.samplerate, me.samplesize, me.channels, me.block_alignment, me.endian, me.bpm, me.tagversion, me.drm, me.musicmagic_mixable, me.musicbrainz_id, me.lossless, me.lyrics, me.replay_gain, me.replay_peak, me.extid FROM tracks me WHERE ( id IN (  ) ) ORDER BY RAND()': DBD::mysql::st execute failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ') ) ORDER BY RAND()' at line 1 at /usr/share/squeezecenter/CPAN/DBIx/Class/Storage/DBI.pm line 771.
[09-01-03 15:19:56.0995] Slim::Schema::Storage::throw_exception (70) Backtrace:

   frame 0: Slim::Utils::Log::logBacktrace (/usr/share/perl5/Slim/Schema/Storage.pm line 70)
   frame 1: Slim::Schema::Storage::throw_exception (/usr/share/squeezecenter/CPAN/DBIx/Class/Storage/DBI.pm line 773)
   frame 2: DBIx::Class::Storage::DBI::_execute (/usr/share/squeezecenter/CPAN/DBIx/Class/Storage/DBI.pm line 826)
   frame 3: DBIx::Class::Storage::DBI::_select (/usr/share/squeezecenter/CPAN/DBIx/Class/Storage/DBI/Cursor.pm line 118)
   frame 4: DBIx::Class::Storage::DBI::Cursor::all (/usr/share/squeezecenter/CPAN/DBIx/Class/ResultSet.pm line 945)
   frame 5: DBIx::Class::ResultSet::all (/usr/share/perl5/Slim/Plugin/RandomPlay/Plugin.pm line 466)
   frame 6: Slim::Plugin::RandomPlay::Plugin::findAndAdd (/usr/share/perl5/Slim/Plugin/RandomPlay/Plugin.pm line 741)
   frame 7: Slim::Plugin::RandomPlay::Plugin::playRandom (/usr/share/perl5/Slim/Plugin/RandomPlay/Plugin.pm line 1207)
   frame 8: Slim::Plugin::RandomPlay::Plugin::handleWebMix (/usr/share/perl5/Slim/Plugin/RandomPlay/Plugin.pm line 1236)
   frame 9: Slim::Plugin::RandomPlay::Plugin::handleWebSettings (/usr/share/perl5/Slim/Web/HTTP.pm line 1163)
   frame 10: Slim::Web::HTTP::generateHTTPResponse (/usr/share/perl5/Slim/Web/HTTP.pm line 992)
   frame 11: Slim::Web::HTTP::processURL (/usr/share/perl5/Slim/Web/HTTP.pm line 803)
   frame 12: Slim::Web::HTTP::processHTTP (/usr/share/perl5/Slim/Networking/IO/Select.pm line 268)
   frame 13: (eval) (/usr/share/perl5/Slim/Networking/IO/Select.pm line 268)
   frame 14: Slim::Networking::IO::Select::select (/usr/sbin/squeezecenter-server line 541)
   frame 15: main::idle (/usr/sbin/squeezecenter-server line 486)
   frame 16: main::main (/usr/sbin/squeezecenter-server line 1048)

[09-01-03 15:19:56.0999] Slim::Networking::IO::Select::select (271) Error: Select task failed: Carp::Clan::__ANON__(): Error executing 'SELECT me.id, me.url, me.content_type, me.title, me.titlesort, me.titlesearch, me.album, me.tracknum, me.timestamp, me.filesize, me.disc, me.remote, me.audio, me.audio_size, me.audio_offset, me.year, me.secs, me.cover, me.vbr_scale, me.bitrate, me.samplerate, me.samplesize, me.channels, me.block_alignment, me.endian, me.bpm, me.tagversion, me.drm, me.musicmagic_mixable, me.musicbrainz_id, me.lossless, me.lyrics, me.replay_gain, me.replay_peak, me.extid FROM tracks me WHERE ( id IN (  ) ) ORDER BY RAND()': DBD::mysql::st execute failed: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ') ) ORDER BY RAND()' at line 1 at /usr/share/squeezecenter/CPAN/DBIx/Class/Storage/DBI.pm line 771

```

So there's obviously an error there, but I have NO idea of what it means. Any ideas would be appreciated, as this one is ...annoying.

The only difference between the files in the subdirectories and the one in the base Music directory (other than the directory structure) is that I downloaded (legally) the one in the root directory. The others are all ripped by me from CD's (using the Audio Disc Extractor tool in Ubuntu.) They are all MP3's, not Ogg, ac4, or whatever. They also play fine with Rhythmbox or Amarok, etc.

In the "I have no idea if this is related or not" department, I can get the one file (or alternately, media streams from the internet) to play, but I get no sound. This is on all machines in the house, Ubuntu or Windows. So I'm thinking that something's really, really broke.

Again, any help would really be appreciated.

---

### Post by perryrt on 2009-01-03
As a followup to this, I have discovered that my squeezebox will play both the one tune that the server "sees" as well as internet radio etc., so....

I guess that means that parts of it are working?

Still kerflummoxed about the music search, though.

---

### Post by perryrt on 2009-01-10
Bump - still nothing on this. Anybody got any ideas?

---

### Post by plskeggs on 2009-01-18
Hi,

What ownership and permissions do you have on your mp3 files?

They need to be readable by the squeezecenter user.  What I did was create a new user and group named media, and then added all of my users login names to the group media, along with the squeezecenter user.  I then chmod'd my mp3s to be readable / writeable by the group media.  This enables me and my family to rip and store new CDs to our media folder, but also allows squeezecenter to read / playback the files.

Anyway, at least do this:
chown squeezecenter:squeezecenter /your-media-folder-name -R
chmod u+r /your-media-folder-name -R

You'll probably want to add yourself to the squeezecenter group so you can read the files for other purposes.

Hope this helps.

---

### Post by Peter Bell on 2009-01-20
Have you tried asking on the Slim Devices forums?

---

### Post by berte on 2009-05-23
Hello,

I had a similar problem. I installed the testing version (7.3.3 - deb [http://debian.slimdevices.com](http://debian.slimdevices.com) testing main) and gave full acess to my library directory and it is working like a charm now. I thing the problem was related to perl 5.10.

Hope this help,
Berte

---

### Post by arc2v on 2009-06-03
I've seen this problem as well.  The user "squeezecenter" needs read permissions on all the files and execute permissions on all the directories.

from your root directory, you can either make squeezecenter the owner:

sudo chown -R squeezecenter ./Music

or you can make sure everyone has read/execute permissions on the whole directory:

sudo chmod -R 755 ./Music

The latter was the default setting for my Music directory and it worked right off the install.

Also, make sure the user squeezecenter has write permissions to your Playlists directory, or they won't save.

Hope this helps.

---

