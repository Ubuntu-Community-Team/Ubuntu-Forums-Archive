---
title: "MythWeb &amp; Automatic Start of MythTV"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by Nelson-Ray on 2006-11-16
Hello,
I installed MythTV on Edgy with the help of the guide [https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop) ...I encountered two problems after the installation. 

1.) When I try to acess MythWeb via a browser I get this error 

Error: Please install the MySQL libraries for PHP. The package is usually called something like php-mysql.

From what I was able to find it seems MythWeb needs php4-mysql and the installation from the guide installed php5-mysql on my computer. I did an apt-get intall php4-mysql and I still get the same error. Could someone explain how to fix this and not hose my mythtv install?

2.) When I boot into Edgy...Mythtv does not start automatically. When I typed in :

sudo /etc/init.d/mythtv-backend restart

I get this message :

Restarting MythTV server: mythbackendNo /usr/bin/mythbackend found running; none killed.

when I type in :

sudo /etc/init.d/mythtv-backend start

I get this message :

mythbackend already running, use restart instead.

When I just type in at the terminal :

mythbackend 

then it seems to run and I can connect to it from the mythfrontends.

Could someone offer any help on getting this started automatically? 

Thanks...

---

### Post by superm1 on 2006-11-17
Nelson,

I've seen some people having difficulties starting the backend.  Check /var/log/mythtv/mythbackend.log.  Usually it ends up being that the place the recordings were mounted doesn't have write permissions for the "mythtv" user.  So if you run it as a normal user, this problem doesn't happen since the normal user has write permissions to this place.

As for mythweb missing php4-mysql or 5, either works.  Did you do something out of order when you installed mythweb?  Eg, you had apache installed already, or you had phpmyadmin already installed or something like that?

---

### Post by Nelson-Ray on 2006-11-17
Hey Superm1....

Indeed I did have permissions set in the Mythtv recording folder for the regular user account rather than mythtv. I did change it and that solved that problem. So thanks!

About MythWeb. What I did was install from the regular Ubuntu desktop install disc. Then followed the backend + frontend guide because I like to copy and paste the commands in the terminal. I had gnome installed ...added the necessary universe / multiverse repositories and followed the guide from there. I don't think I installed phpmyadmin before the mythplugins.  Other than a reinstall any recommendations you could offer to get mythweb running? Thank you...

---

### Post by superm1 on 2006-11-17
Added this solution to the wiki.

As for the mythweb problem, if you've got nothing else invested so far in the web server.  Open synaptic.  Search for apache.  "Completely" Remove any installed apache packages.  Search for php.  Rinse, rather, repeat.  Search for mythweb.  Same thing.

Once all that is finished up, if by chance /etc/php5 or /etc/php4 or /etc/apache2 still exist, remove them.

Once your sure your all clean, open back up synaptic.  Search for mythweb and mark it.  This will mark apache2, the appropriate php libraries, and the appropriate mysql libraries.

Hopefully that does it for you :)

---

### Post by Nelson-Ray on 2006-11-17
Superm1 - I did a reinstall and followed the guide step by step and mythweb is working (I think during the first install while filling up the database with guide data I jumped ahead and installed out of order). So thank you! Whoot! I would like to ask you two follow up questions and if you could answer it would be greatly appreciated.


1.) With MythVideo and multiple frontends. Is it possible to enter data (IMDB and thumbnails/movie posters) on one frontend only and have the other frontends synchronized when opened? I do have a lot of ripped dvd's and it would be much easier if the metadata could be entered once, rather than setting it up individually on each frontend. The video directory is mounted via NFS in the same directory structure on all computers.

2.) I am using a FusionHDTV5 card for MythTV. The frontend is running on a a 19" LCD monitor. The HD tv shows look great (it is letterboxed with correct aspect ratio). The problem I am having is that for standard resolution television shows (480i) the picture is framed by black bars on all four sides. I can select "Fill" as an option in MythTV, that will make the standard television shows fullscreen, but then the HD tv shows are zoomed in (like pan and scan). Would you know of a way to have fullscreen for standard tv shows and letterboxed for HD shows?

---

### Post by superm1 on 2006-11-17
The metadata for all of your dvds should be shared among frontends.  If you choose a location for the covers that is on your NFS mounted directory structure, you should be able to add this to mythvideo's place to look for DVD covers.  This setting will probably have to be added on all frontends, but then each frontend should be able to access all covers and such afterwords.

As for your playback problem, are all recordings being recorded by your Fusion5?  If so, these 480i shows, if they are recorded on a digital station through your fusion5, then the only way to view them correctly is with the zoom option.  You'll unfortunately have to switch aspect ratios each time.  

If they are being recorded at different resolutions though, eg these are 480x480, not a 480x480 box in 1280x720, then you can go into the appearance settings menu.  There is an option to force specific aspect ratios/resolutions for specific content.

---

### Post by Nelson-Ray on 2006-11-17
Suprm1 - Thanks Aagain

1.) About MythVideo and multiple frontends - it did not occur to me share & mount the movie covers directory on the different frontends. I did that and now they are all synchronized. This is awesome!

2.) All recordings are being done by that one FusionHDTV5 card. Hopefully I can spring for another one around xmas time. So I guess I will have to live with toggling the setting for Aspect Override between "off" for HD and "Fill" for standard definition. Anyways I can live with that.

One final question. I am about to install phpmyadmin. This last step in the guide says :

sudo apt-get install libapache2-mod-php5

When I type that in I get this message :

sudo apt-get install libapache2-mod-php5
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0c2 libopenexr2c2a mythmusic libarts1c2a libzzip-0-12 kdelibs4c2a libfaad2-0
  libdc1394-13 mythphone mytharchive mythbrowser libxml-libxml-common-perl libvorbisfile3
  mytharchive-data libxml-namespacesupport-perl python-mysqldb fftw2 kdelibs-data mythplugins
  mythdvd liblualib50 mythgallery php4-mysql gcc-3.4-base mythgame libavformat0d dvdauthor apache2
  mythflix mythweb python-imaging libavahi-qt3-1 libxml-libxml-perl libxml-sax-perl mythcontrols
  ffmpeg libmjpegtools0c2a php4-common libgsm1 phpmyadmin libdvdread3 libcdaudio1
  libxml-simple-perl libavcodec0d libmad0 mjpegtools mythweather mythvideo libid3tag0 php5-cgi
  liblua50 libg2c0 mythnews libquicktime0 libapache2-mod-php4 liba52-0.7.4
Use 'apt-get autoremove' to remove them.


..I selected "no" when it asked if I wanted to continue. Should it say that mythweb mythplugins etc are no longer needed? I am wondering if that is why mythweb did not work for me on the first install.

Anyways if it is ok..I will continue..if you say so. Otherwise will hold off on installing phpmyadmin until that part is straightened out. Thanks again.

---

### Post by superm1 on 2006-11-17
Well actually, try it without that last step, installing libapache2-mod-php5.  That may be unnecessary if mythweb is already installed ( since it included php4 support ).  If it works without it, i'll update the guide to reflect this.

---

### Post by Nelson-Ray on 2006-11-17
Suprm1 - phpmyadmin indeed does run fine without that last step. Thanks for your help.

---

