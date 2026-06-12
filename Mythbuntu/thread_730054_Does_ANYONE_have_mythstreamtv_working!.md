---
title: "Does ANYONE have mythstreamtv working!??"
date: 2008-03-20
forum: Mythbuntu
---

### Post by TheKorn2 on 2008-03-20
I've been pounding google (and many site-specific search engines) for the answer, and I've come up empty.

Does [SIZE="7"]ANYONE[/SIZE] have mythstreamtv working in mythtv version 0.21?

I can find a ton of links where it was working in version 0.19, then everything seems to have died.


I've tried the steps listed here:  [http://www.mythtv.org/wiki/index.php/MythStreamTV](http://www.mythtv.org/wiki/index.php/MythStreamTV)


Well, with slight modifications I was able to get FFMPEG to compile.  But when I go to compiling VLC, it falls apart inside the FFMPEG section.  So I don't know if my FFMPEG compile is good or not.

And before anyone asks, NO it doesn't work with the standard VLC package.  VLC complains there's no method to play streams of type myth://blahblahblah .




Here's my text log I kept open so that I could keep track of everything I've tried...  (all steps done from my home directory)

```

sudo apt-get install gcc g++

sudo apt-get install subversion


get FFMPEG source:

svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg



Now, get libfaac:

sudo apt-get install libfaac-dev

Now, get liblame:

sudo apt-get install liblame-dev



compile/install FFMPEG source:


cd ffmpeg
./configure --enable-ffmpeg --enable-libmp3lame --enable-libfaac --enable-zlib \
            --enable-liba52 --enable-libvorbis --enable-libtheora \
            --enable-debug --enable-gpl  --enable-postproc
            
make (you'll see ALL KINDS of warnings/errors... )
sudo make install
cd ..



get latest VLC source from http://www.videolan.org/vlc/download-sources.html

unzip/untar into a directory

cd into that directory



next, get random "other crap" that VLC insists it needs:

sudo apt-get build-dep vlc


(i.e. sudo apt-get install libwxgtk2.6-dev libdvbpsi4-dev libmpeg2-4-dev libmpeg3-dev libmad0-dev libasound2-dev libesd0-dev x11proto-video-dev libdvdnav-dev liba52-0.7.4-dev libflac-dev libfreetype6-dev libid3tag0-dev libogg-dev libpng12-dev libspeex-dev libtheora-dev libvorbis-dev libxml2-dev zlib1g-dev build-essential automake1.9 libtool libx11-dev libdvdread-dev libdvdnav-dev libebml-dev libmatroska-dev libmp4v2-dev libpostproc-dev libavformat-dev ffmpeg libavcodec-dev libvcdinfo-dev libdts-dev libslp-dev gettext liblivemedia-dev libsdl1.2-dev libdv4-dev libnotify-dev libcdio-dev libavc1394-dev libcddb2-dev )




Now, get all makey-makey with VLC:

./configure --disable-x11 --disable-xvideo --disable-gtk --disable-sdl --enable-ffmpeg \
            --with-ffmpeg-mp3lame --with-ffmpeg-zlib --enable-mad --enable-libdvbpsi \
            --enable-a52 --disable-dvdplay --enable-dvdnav --enable-vorbis --enable-ogg \
            --enable-theora --enable-mkv --enable-freetype --disable-cddax --disable-vcdx \
            --enable-speex --enable-flac --enable-goom --enable-livedotcom --enable-caca \
            --disable-skins2 --enable-modplug --enable-debug --enable-gpl --enable-mp3lame \
            --enable-pp --with-ffmpeg-tree=REPLACE WITH YOUR FFMPEG DIRECTORY FROM ABOVE
            

make  (lots of warnings and errors...  you know what to do.)

VLC make fails at this point, complaining about the contents in the FFMPEG tree.



Previously, I then followed the wiki on how to install mythstreamtv

```


(This is the last piece in my mythtv puzzle, and it's *driving me mad* trying to figure it out!)

Thanks in advance, though I have a feeling I'm tilting at windmills.

---

### Post by tgm4883 on 2008-03-20
Is mythstreamtv needed anymore?  You can stream shows from mythweb in .21

---

### Post by kameleon25 on 2008-03-20
Yep, sure can. I am doing it right as we speak. Watching the latest TopGear special. ;)

---

### Post by TheKorn2 on 2008-03-20
Where in mythweb do you stream recordings from?  I can't see anywhere in mythweb that references streaming, *except* in the settings menu.  Is there a special add-on that is needed that's not included by default?

(I'm going to hate it if it's something simple, but I GOTTA ask!)

Thanks!



EDIT:  nevermind, I found it.  Still doesn't work (mythTV insists that EVERY recording doesn't exist) but at least I have a new white whale to hunt down.  It's in the "recordings" menu, for anyone wondering in the future.

---

### Post by dannyboy79 on 2008-03-20
> **TheKorn2 said:**
> Where in mythweb do you stream recordings from?  I can't see anywhere in mythweb that references streaming, *except* in the settings menu.  Is there a special add-on that is needed that's not included by default?

(I'm going to hate it if it's something simple, but I GOTTA ask!)

Thanks!



EDIT:  nevermind, I found it.  Still doesn't work (mythTV insists that EVERY recording doesn't exist) but at least I have a new white whale to hunt down.  It's in the "recordings" menu, for anyone wondering in the future.

if mythweb says this: "2003_20080318213000.mpg does not exist in the recordings directory." it's because the recording is located on a slave or other machine that's not nfs mounted where mythweb is. i have this issue as well due to having a slave backend which stores it's files locally and not on a nfs share from tthe master backend which runs mythweb. This is also an issue for me with xbmcmythtv, if the recording is stored on the slave backend, I can't watch it, I have to watch it without xbmcmythtv and just view it through a samba share. I use mythrename.pl to make human readable symlinks of all my recordings. Good luck

oh, I don't use mythstream so I can't help. When I click on a show within mythweb, Firefox tries to download the file and it doesn't attempt to stream it. They are .mpg files so it would take hours to download from my slow upload speed home server.

---

### Post by TheKorn2 on 2008-03-20
> **dannyboy79 said:**
> if mythweb says this: "2003_20080318213000.mpg does not exist in the recordings directory." it's because the recording is located on a slave or other machine that's not nfs mounted where mythweb is.

Good guess!  Only problem is that my frontend and backend (and where mythweb is running as well) is the same machine!  So I'm kind of assuming that means I don't have to share it with NFS, or is that a bad assumption?

Here's some background...  on install, I created a 10gig partition to hold the OS and mythtv.  Then I created a 450gig JFS partition, and automatically mount that at /mythtv .  The recordings are stored in /mythtv/videos , while everything that I download I store in /mythtv/downloads .  (mythtv group has full attributes to both those directories.)

Everything works great on the front end and also via a UPnP box; I can hit *everything*.  It's just mythweb itself is having a problem whenever I try and do a direct download or stream it.

So would I have to make /mythtv somehow reachable via NFS for mythweb to work?  That doesn't seem to make logical sense to me since it's already reachable via the frontend, but my brain fried a few hours ago when I was chasing my tail.

---

### Post by Gammell on 2008-03-20
> **TheKorn2 said:**
> Here's some background...  on install, I created a 10gig partition to hold the OS and mythtv.  Then I created a 450gig JFS partition, and automatically mount that at /mythtv .  The recordings are stored in /mythtv/videos , while everything that I download I store in /mythtv/downloads .  (mythtv group has full attributes to both those directories.)

...

So would I have to make /mythtv somehow reachable via NFS for mythweb to work?

The issue probably is that mythweb does not have rights to read /mythtv... It's happened to me before. Which groups does the webserver's user (for apache2, www-data) belong to? For anyone reading this later who doesn't know.
To check: ```
groups www-data
```
and to append groups: ```
sudo usermod www-data -aG mythtv
```

Also, FYI. Mythstream is actually a plugin to let mythtv PLAY internet, not stream your files out... So if you'd got it working, you'd probably have been more frustrated. ;) Mythweb will do the job when you get it working.
[quote=Synaptic]MythStream is an unofficial MythTV plugin that plays Internet audio and video streams. Besides playing your top 5 favourite streams, you can use MythStream to browse or search stream URL sources without configuring every stream URL explicitly.

The default MythStream installation contains several external parsers for browsing stream index sites, playlists and RSS/XML feeds like the Icecast, Shoutcast and BBC sites and most podcasts. Several more complex parsers allow for querying sites through an interactive menu. Other sources can be supported by adding new parsers.[/quote]

---

### Post by thatkidandy on 2008-03-20
does mythweb use mythstreamtv that was mentioned earlier?

I cannot get mine to work and I think it is because I havent configured any of the transcoding on the backend. mythweb seems to be parsing the stream .asx file (meta data) fine, but it seems like there isnt any data provided to stream.

I have not tried to stream before (any setup I mean), just saw it was included in the 0.21 update...

tips? 

thank you! :)

---

### Post by kameleon25 on 2008-03-20
Mythstreamtv was an older plugin that has been retired due to mythweb doing the same thing now. Mythstream (note no TV) is for streaming content FROM the internet TO your mythtv box. The OP was talking about MythstreamTV. So yes if you upgrade to .21 you should have no issues. My only issue is I have to download the file directly since I use a nonstandard port (not port 80) to access my mythweb.

---

### Post by Gammell on 2008-03-20
> **kameleon25 said:**
> Mythstreamtv was an older plugin that has been retired due to mythweb doing the same thing now. Mythstream (note no TV) is for streaming content FROM the internet TO your mythtv box. I do apologise. Too many stray "TV"s kicking around I guess. ;)

> **thatkidandy said:**
> does mythweb use mythstreamtv that was mentioned earlier?
No. mythweb should be able to stream files 'on it's own' (it may require some other packages like ffmpeg, but it should pull those in itself I'd think). I've got to run, but you may find the mythtv wiki useful: [http://mythtv.org/wiki/index.php/Mythweb](http://mythtv.org/wiki/index.php/Mythweb)
I haven't used streaming that much but it shouldn't need transcoding... if anything, it might only work on non-transcoded files (.mpeg vs. .nuv). When I get a chance later, I'll try and see if I can think of anything that might help you out.
Best of luck.

---

### Post by dannyboy79 on 2008-03-20
yeah, that issue I described is for systems that have recordings stored on other slave backends. so obviously this doesn't apply to you. SOrry I can't help.

---

### Post by TheKorn2 on 2008-03-20
> **Gammell said:**
> The issue probably is that mythweb does not have rights to read /mythtv... It's happened to me before. Which groups does the webserver's user (for apache2, www-data) belong to? For anyone reading this later who doesn't know.
To check: ```
groups www-data
```
and to append groups: ```
sudo usermod www-data -aG mythtv
```

SUCCESS!  THANK YOU!!  :)

Though in my case, that usermod command didn't add www-data to the mythtv group.  But I already know addgroup, so I did

```

sudo addgroup www-data mythtv

```

Went back to mythweb, and it still didn't work, so I decided to cover the base I'd restart apache:

```

sudo /etc/init.d/apache2 restart

```

And now it all works!  THANKS SO MUCH!!

---

### Post by thatkidandy on 2008-03-21
> **Gammell said:**
> I do apologise. Too many stray "TV"s kicking around I guess. ;)


No. mythweb should be able to stream files 'on it's own' (it may require some other packages like ffmpeg, but it should pull those in itself I'd think). I've got to run, but you may find the mythtv wiki useful: [http://mythtv.org/wiki/index.php/Mythweb](http://mythtv.org/wiki/index.php/Mythweb)
I haven't used streaming that much but it shouldn't need transcoding... if anything, it might only work on non-transcoded files (.mpeg vs. .nuv). When I get a chance later, I'll try and see if I can think of anything that might help you out.
Best of luck.

Thank you! This clarifies a lot, I will look into this when I get home.

---

### Post by Gammell on 2008-03-22
> **TheKorn2 said:**
> Went back to mythweb, and it still didn't work, so I decided to cover the base I'd restart apache:
And now it all works!  THANKS SO MUCH!!Good point. I forgot... After making changes to www-data, you will always need to restart apache. Good to hear you've got it all figured out and thanks for documenting the missed step for anyone reading this later.

> **thatkidandy said:**
> Thank you! This clarifies a lot, I will look into this when I get home.If you still can't get things working, take a look in your access.log and error.log to see if there's any hints in there.

---

### Post by thatkidandy on 2008-03-22
> **TheKorn2 said:**
> SUCCESS!  THANK YOU!!  :)

Though in my case, that usermod command didn't add www-data to the mythtv group.  But I already know addgroup, so I did

```

sudo addgroup www-data mythtv

```

Went back to mythweb, and it still didn't work, so I decided to cover the base I'd restart apache:

```

sudo /etc/init.d/apache2 restart

```

And now it all works!  THANKS SO MUCH!!

Followed the same and mine is working too. Thank you everyone for the support :)

---

### Post by RLovelett on 2008-04-27
I've followed all of the steps above, and mine keeps asking for a user name and password for the ASX streams.  When I just click download, works superbly and downloads the files no permission errors.  I've tried typing in the password that I've set for the mythweb install.  I've also tried using my user name and password.  Nothing seems to work.

I've added www-data to the mythtv group, and restarted apache as well.  Just to know where I'm coming from.

Ryan

---

### Post by Gammell on 2008-04-27
> **RLovelett said:**
> I've followed all of the steps above, and mine keeps asking for a user name and password for the ASX streams.  When I just click download, works superbly and downloads the files no permission errors.  I've tried typing in the password that I've set for the mythweb install.  I've also tried using my user name and password.  Nothing seems to work.

I've added www-data to the mythtv group, and restarted apache as well.  Just to know where I'm coming from.

Ryan
Do you have access logging turned on (I don't remember if it's on by default). If you do, look in your logs to see if there are any clues to why downloading is behaving differently than streaming.

---

### Post by RLovelett on 2008-04-27
Logging was already enabled on my machine.  So I looked through my logs...

> xx.xxx.xxx.xxx - RLovelett [27/Apr/2008:11:43:30 -0400] "GET /mythweb/pl/stream/1027/1209288480.asx HTTP/1.1" 200 251 "http://myip/mythweb/tv/recorded" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008041514 Firefox/3.0b5"
xx.xxx.xxx.xxx - - [27/Apr/2008:11:43:44 -0400] "GET /mythweb/pl/stream/1027/1209288480 HTTP/1.1" 401 543 "-" "gnome-vfs/2.22.0 neon/0.25.4"
xx.xxx.xxx.xxx - - [27/Apr/2008:11:43:46 -0400] "GET /mythweb/pl/stream/1027/1209288480 HTTP/1.0" 401 543 "-" "xine/1.1.11.1"

Basically it looks like I'm seeing the login of RLovelett (which is the username of the mythweb install), but then when it tries to read the asx file the next two lines I'm getting 401 and 543 errors.

I'm not sure what those errors mean, to really start trouble shooting where they come from.  The only thing I can say is that even after typing in the username for the accesses the streams still do not see my user name.

---

### Post by TheKorn2 on 2008-04-27
> **RLovelett said:**
> Basically it looks like I'm seeing the login of RLovelett (which is the username of the mythweb install), but then when it tries to read the asx file the next two lines I'm getting 401 and 543 errors.

401 is unauthorized (i.e. password not accepeted)

Just to make sure, you're typing in your MYTHWEB username and password (the u/p used when you first fire up mythweb), correct?  (When it hands over the connection to your media player, it has to also log in.)  Your mythweb u/p can be entirely different than your linux u/p, for example.

---

### Post by TheKorn2 on 2008-04-27
> **RLovelett said:**
> Basically it looks like I'm seeing the login of RLovelett (which is the username of the mythweb install), but then when it tries to read the asx file the next two lines I'm getting 401 and 543 errors.

Also, you are not getting a 401 AND a 543 error; http requests can only send one status code back.  You are receiving a 401, twice in a row.  I believe the second field is the number of bytes transmitted in the reply.  (Don't hold me to that; it's been a while since I knew what every field was for in the apache log.)

But I don't believe your problem is in your mythweb config at all.  The hint is in your log, speifically the *browser* column:

> xx.xxx.xxx.xxx - RLovelett [27/Apr/2008:11:43:30 -0400] "GET /mythweb/pl/stream/1027/1209288480.asx HTTP/1.1" 200 251 "http://myip/mythweb/tv/recorded" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008041514 Firefox/3.0b5"
xx.xxx.xxx.xxx - - [27/Apr/2008:11:43:44 -0400] "GET /mythweb/pl/stream/1027/1209288480 HTTP/1.1" 401 543 "-" "gnome-vfs/2.22.0 neon/0.25.4"
xx.xxx.xxx.xxx - - [27/Apr/2008:11:43:46 -0400] "GET /mythweb/pl/stream/1027/1209288480 HTTP/1.0" 401 543 "-" "xine/1.1.11.1"

So, here's what I believe is happening:

firefox asks for the file.  Since firefox is already logged in, apache sends back an "OK!" (200), and starts sending the asx data.  Firefox CAN'T natively handle an asx file, and for some reason (default action, maybe?) passes it to gnome-vfs.


gnome-vfs knows how to talk http (apparently), so it tries to retrieve the file.  Apache sees something *new* asking for the same file, and that area needs a password, so it generates a 401 and sends it back to gnome.  Gnome now asks you for the username and password.

gnome then does a "uh-oh" when it sees the file content, and hands it off to xine.



xine ALSO knows how to talk http, so IT tries to retrievethe file.  Apache sees yet someone *else* asking for the same file, generates a second 401 for xine, and I believe that's the point at which you probably gave up typing in your username and password.


Either that, or your copy of xine knows how to talk http but not what to do with an ASX stream.  :)


How to straighten it out would be to configure firefox to directly give the asx stream over to xine.  You'll still need to type in your username and password a second time as there's no way around that, and it's normal behavior.

---

### Post by dcherryholmes on 2008-05-23
Does the streaming feature of mythweb only work for recorded tv shows, and not video files?  I went rtorrent + pytvshows + screen FTW, and I don't have cable.  I'd like to stream the shows I have saved in video.  Is this possible?

---

### Post by dcherryholmes on 2008-05-23
> **dcherryholmes said:**
> Does the streaming feature of mythweb only work for recorded tv shows, and not video files?  I went rtorrent + pytvshows + screen FTW, and I don't have cable.  I'd like to stream the shows I have saved in video.  Is this possible?

Nevermind.  Click on the title of the video.  Duh.

---

### Post by entourage on 2008-06-12
> **kameleon25 said:**
> Mythstreamtv was an older plugin that has been retired due to mythweb doing the same thing now. Mythstream (note no TV) is for streaming content FROM the internet TO your mythtv box. The OP was talking about MythstreamTV. So yes if you upgrade to .21 you should have no issues. My only issue is I have to download the file directly since I use a nonstandard port (not port 80) to access my mythweb.

I have had to change my port to 8081...could this be why mine isn't working?

---

### Post by Gammell on 2008-06-12
> **entourage said:**
> I have had to change my port to 8081...could this be why mine isn't working?

Are you trying it within a LAN or remotely over the internet? Some ISPs block higher ports.

---

### Post by entourage on 2008-06-30
> **Gammell said:**
> Are you trying it within a LAN or remotely over the internet? Some ISPs block higher ports.
Trying over LAN.

---

### Post by anonymousdog on 2008-09-14
I've been hacking on mythstreamtv on and off for a while to get it working better with 0.21.  I think I have a pretty good, working install that makes use of storage group information, includes some new bit rate options, includes a wap theme (yes, this works on mobile devices), allows (on the web server) concurrent vlc instances not owned by www-data user, corrects a handful of small errors and syntax problems, and makes a few minor additions and changes.  This package is intended for Mythbuntu 8.0.4.x, but may work with other distros and MythTV 0.21.  Two caveats: no storage group can have more than one directory defined, or mythstreamtv won't be able to find the recordings files (and it won't work).  The scripting assumes that the recordings files are locally accessible on the web server at the path defined for each storage group's only directory; for web servers that don't house the recordings' physical disks, you can accomplish that with remote mounts.

Attached are a tgz archive and a deb of the package.  This is my first deb package and totally untested, but the tgz should be fool-proof.  The deb does nothing more than automatically unpack the archive; you still have to do most of the steps below.

Dl the package, open a terminal at / (root), and 'sudo tar -xzvf <path_to_package>/mythstreamtv_1.30-10-amk.tar.gz'.  Now, 'cd /usr/share/mythstreamtv'.  'sudo nano ./install.sh &' to edit the options in a block beginning on line 100; the defaults are just fine in most cases.  Now, 'sudo ./install.sh'.  That's pretty much it.  The script should run without error unless mythstreamtv has been installed before. In that case, you'll see some errors as the script attempts to create already existing folders and symlinks.

Browse to mythweb, and you'll see a new "StreamTV" option in the header (or in the list on a wap device).  Select a recording on the first page and click the "Select a Recording & Continue" button.  On the next page you can select some bit rate and other options.  The default page has reasonable defaults for a LAN device with VGA or better screen, while the wap page's defaults are "worst quality" settings designed to work over limited bandwidth to "small" screens.  Click the "Start Live Stream" button, and mythweb will take you to a streaming status page where some very obvious management functions are available.  Click on the "Stop Streaming" button to free up web server resources (due to vlc's significant CPU needs) and/or stream a different recording.  The one on the bottom is a bit broken in that it doesn't refresh the page header and leaves you on the status page (I'll have to fix that), but the "Stop Streaming" button in the header stops the stream and reloads the page where you select a recording.

Stream URLs are available on the status page.  You can copy them (or setup a default mms player) to play the stream with vlc, WMP, tcpmp (probably the Core), etc by opening the URL as a network stream, or, if not available, a file (e.g., WMP).  WMP gives me grief playing some rescaled resolutions; so I usually use VLC on PCs and tcpmp on PDAs.

This plugin was obviously originally intended to play multiple recordings as a playlist for vlc, but I've never gotten the multiple recording functionality to work.  If you select multiple recordings, the system logs no errors, but none but the first recording plays.

---

### Post by IrishGent on 2009-07-02
```
Starting Stream of /var/lib/mythtv/recordings/myth://10.0.1.44:6543/1358_20090620224443.mpg
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000370] inhibit interface error: Failed to connect to the D-Bus session daemon: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

[00000370] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000373] main interface: creating httpd
[00000384] access_directory access error: 10.0.1.44:6543/1358_20090620224443.mpg: No such file or directory
[00000384] access_file access error: cannot open file 10.0.1.44:6543/1358_20090620224443.mpg (No such file or directory)
[00000376] main input error: open of `/var/lib/mythtv/recordings/myth://10.0.1.44:6543/1358_20090620224443.mpg' failed: could not create access: no suitable access module
 
```I have Mythbuntu 9.04 running, and I am interested in getting MythStreamTV to run.  I have downloaded and installed AnonymousDogs updated version of MythStreamTV.  BTW - Big THANKS!

I am having 2 problems currently.  The first is that 'myth://10.0.1.44:6543' is programmatically getting inserted into the path to the stored video, and the process is bombing out.  I cannot find where that is coming from either in the code or in the settings of MythTV.  If I edit that out the the URL and resubmit, I get beyond that error.

The second problem is that there doesnt seem to be an active stream to connect to.  VLC on a WinXP client never connects...

Any help for either of these issues is greatly apprecaited.

Thanks!

---

### Post by IrishGent on 2009-07-03
> **IrishGent said:**
> 
The first is that 'myth://10.0.1.44:6543' is programmatically getting inserted into the path to the stored video, and the process is bombing out.  I cannot find where that is coming from either in the code or in the settings of MythTV.  If I edit that out the the URL and resubmit, I get beyond that error.

OK - I think this is a 'nevermind' problem as i have seen a number of other logs so far with the same construct, and no one else is complaining.  

That leaves problem 2 if anyone has a suggestion?  I know this is an old thread.  If I dont see some activity, I may open a new thread...

Thanks!

---

### Post by newlinux on 2009-07-03
This is somewhat related I think...

What kind of bandwidth (upstream) does the asx stream need to work for SD nd HD mpeg-2 recordings over WAN? It works fine for me on my LAN, but WAN recordings seem to freeze using VLC... I think this is where the old mysthstreamtv might be better, because it can do on the fly transcoding. Maybe I'll spend some time to setup a system to use VLC on the mythweb machine to setup streams...

---

### Post by NativeRaver on 2010-02-18
> **anonymousdog said:**
> I've been hacking on mythstreamtv on and off for a while to get it working better with 0.21.  I think I have a pretty good, working install that makes use of storage group information, includes some new bit rate options, includes a wap theme (yes, this works on mobile devices), allows (on the web server) concurrent vlc instances not owned by www-data user, corrects a handful of small errors and syntax problems, and makes a few minor additions and changes.  This package is intended for Mythbuntu 8.0.4.x, but may work with other distros and MythTV 0.21.  Two caveats: no storage group can have more than one directory defined, or mythstreamtv won't be able to find the recordings files (and it won't work).  The scripting assumes that the recordings files are locally accessible on the web server at the path defined for each storage group's only directory; for web servers that don't house the recordings' physical disks, you can accomplish that with remote mounts.

Attached are a tgz archive and a deb of the package.  This is my first deb package and totally untested, but the tgz should be fool-proof.  The deb does nothing more than automatically unpack the archive; you still have to do most of the steps below.

Dl the package, open a terminal at / (root), and 'sudo tar -xzvf <path_to_package>/mythstreamtv_1.30-10-amk.tar.gz'.  Now, 'cd /usr/share/mythstreamtv'.  'sudo nano ./install.sh &' to edit the options in a block beginning on line 100; the defaults are just fine in most cases.  Now, 'sudo ./install.sh'.  That's pretty much it.  The script should run without error unless mythstreamtv has been installed before. In that case, you'll see some errors as the script attempts to create already existing folders and symlinks.

Browse to mythweb, and you'll see a new "StreamTV" option in the header (or in the list on a wap device).  Select a recording on the first page and click the "Select a Recording & Continue" button.  On the next page you can select some bit rate and other options.  The default page has reasonable defaults for a LAN device with VGA or better screen, while the wap page's defaults are "worst quality" settings designed to work over limited bandwidth to "small" screens.  Click the "Start Live Stream" button, and mythweb will take you to a streaming status page where some very obvious management functions are available.  Click on the "Stop Streaming" button to free up web server resources (due to vlc's significant CPU needs) and/or stream a different recording.  The one on the bottom is a bit broken in that it doesn't refresh the page header and leaves you on the status page (I'll have to fix that), but the "Stop Streaming" button in the header stops the stream and reloads the page where you select a recording.

Stream URLs are available on the status page.  You can copy them (or setup a default mms player) to play the stream with vlc, WMP, tcpmp (probably the Core), etc by opening the URL as a network stream, or, if not available, a file (e.g., WMP).  WMP gives me grief playing some rescaled resolutions; so I usually use VLC on PCs and tcpmp on PDAs.

This plugin was obviously originally intended to play multiple recordings as a playlist for vlc, but I've never gotten the multiple recording functionality to work.  If you select multiple recordings, the system logs no errors, but none but the first recording plays.

I currently run an old school xbox with xbmc as my frontend. I'd love to stream live tv directly to my xbox. Unfortunately 90% of the channels are HD and the xbox isn't really powerful enough. I have 0.21 running on my backend. I will give this a try and post back.

---

### Post by Gamalier on 2010-12-19
Hi, i'm new to mythbuntu and wanted to know if this plugin is working on version 10.10. If someone has it working please let me know. 
your replays will be most appreciated.

---

### Post by newlinux on 2010-12-19
> **Gamalier said:**
> Hi, i'm new to mythbuntu and wanted to know if this plugin is working on version 10.10. If someone has it working please let me know. 
your replays will be most appreciated.

What do you need to do with it? A lot of the functionality that used to be in mythstreamTV is now built in.

---

### Post by tgm4883 on 2011-09-20
Reviving a dead thread? Nope, Chuck Testa.

---

