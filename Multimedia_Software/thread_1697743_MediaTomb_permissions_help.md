---
title: "MediaTomb permissions help"
date: 2011-03-01
forum: Multimedia Software
---

### Post by SEMPERFIDELIS on 2011-03-01
Thanks to a previous post by a member here I got mediatomb up and running. However when I attempt to add my (username) file to the directory to access from my phone I get the "permissions denied" prompt. Is there any way to allow access for MediaTomb so I can access my files? TIA :-)

---

### Post by howefield on 2011-03-01
Use the terminal command.. (source being the current path to your file, and destination being where you want it to go)

```
sudo cp source destination
```

Or use 

```
gksudo nautilus
```

to open up nautilus with elevated rights, and copy your file. But be careful, remember this window has elevated rights.

---

### Post by SEMPERFIDELIS on 2011-03-01
Maybe my brains fried and I'm reading your post wrong, but I'm having a little trouble following. I'm trying to add the file to the online directory so I can access it from the DLNA app on my Droid X. Ill upload a few screenshots to show you what I'm talking about.

---

### Post by howefield on 2011-03-01
Ah ok, I thought you were copying to your local machine.

---

### Post by SEMPERFIDELIS on 2011-03-01
I'd just use my USB cable for that:P but so far this is as close as I've gotten to setting up any kind of wireless media sharing yet. My router config file is a format I can't open so I can't set up a VPN which is what I wanted to do in the first place. It would be nice to free up my SD card and keep all my music, pics and video on my laptop which stays at home.

---

### Post by SEMPERFIDELIS on 2011-03-01
I figured out the problem. My user and media folders are under root permission and I have no access to modify them in any way. How can I get control back of these folders?

---

### Post by SEMPERFIDELIS on 2011-03-02
bump it.

---

### Post by matt_symes on 2011-03-02
Hi

First things first. 

Why do you have vmlinuz, vmlinuz.old, initrd.img and initrd.img.old in your home partition ? They are system files owned by root.

Is your home folder owned by root ? I take it dustin is your user name and your home folder /home/dustin/. 

KInd regards

---

### Post by SEMPERFIDELIS on 2011-03-02
Whatever is there is whats been there. This computer has only been running Linux for about 3 months which is when my friend gave it to me(I installed Linux). All I did was load it up from a disk and set things up the way I wanted them, then put my files on it. Whatever is in the file system other than my files has been there since day 1. 

As for the rest, yes. All my files appear to be owned by root. I cannot copy anything into the folder "Dustin" or "media" both of which are under the filesystem and home folder.

---

### Post by matt_symes on 2011-03-02
Hi

I am really confused by your setup. What distro of Linux are you running ?

Go to the PC itself, login as your user, open a terminal and type

```
who
id
ps aux | grep [m]ediatomb
ls -l /home
ls -l /home/dustin
```

That is small L's in the -l above.

Post all the results back here.

Kind regards

---

### Post by SEMPERFIDELIS on 2011-03-02
I installed Ubuntu 10.10
Results:

**dustin@ScrapYardDogZ:~$ who**
dustin   tty7         2011-03-01 20:44 (:0)
dustin   pts/0        2011-03-02 21:06 (:0.0)
**dustin@ScrapYardDogZ:~$ id**
uid=1000(dustin) gid=1000(dustin) groups=1000(dustin),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)
**dustin@ScrapYardDogZ:~$ ps aux | grep [m]ediatomb**
**dustin@ScrapYardDogZ:~$ ls -l /home**
total 16
drwx------ 66 dustin dustin 16384 2011-03-01 20:44 dustin
**dustin@ScrapYardDogZ:~$ ls -l /home/dustin**
total 232560
-rw-r--r--  1 dustin dustin  83467939 2011-01-08 14:50 app.zip
drwxr-xr-x  2 dustin dustin      4096 2011-01-14 21:43 chromium_os_usb
drwxr-xr-x  7 dustin dustin      4096 2011-02-27 19:48 Desktop
drwxr-xr-x  4 dustin dustin      4096 2011-03-01 18:56 Documents
drwxr-xr-x  4 dustin dustin      4096 2011-03-01 07:32 Downloads
drwxr-xr-x  6 dustin dustin      4096 2011-03-01 20:45 Dropbox
drwxr-xr-x  2 dustin dustin      4096 2011-02-19 03:19 dvdrip-data
-rw-r--r--  1 dustin dustin   1372572 2011-01-29 03:43 Firefox_wallpaper.png
drwxr-xr-x  3 dustin dustin      4096 2011-03-01 06:48 Movies
drwxr-xr-x 60 dustin dustin     12288 2011-01-14 17:41 Music
drwxr-xr-x  9 dustin dustin     16384 2011-02-24 20:32 Pictures
drwxr-xr-x  2 dustin dustin      4096 2011-01-14 01:37 Public
-rw-r--r--  1 dustin dustin   3017631 2011-02-22 03:40 RZR-2.0.1-recovery_only.sbf
-rwxr-xr-x  1 dustin dustin     23722 2011-02-21 20:40 sbf_flash
drwxr-xr-x  2 dustin dustin      4096 2011-01-16 21:53 SCREENSHOTS
drwxr-xr-x  2 dustin dustin      4096 2011-01-14 01:37 Templates
drwxrwxr-x  2 dustin dustin      4096 2011-01-15 01:57 Ubuntu One
drwxr-xr-x  2 dustin dustin      4096 2011-01-14 02:09 Videos
-rw-r--r--  1 dustin dustin 150119524 2011-02-22 16:32 VZW_A855_FRG22D_QSC6085BP_C_01.43.01P_SW_UPDATE.sbf
drwxr-xr-x  5 dustin dustin      4096 2011-02-22 01:00 workspace
dustin@ScrapYardDogZ:~$

---

### Post by matt_symes on 2011-03-02
Hi

Well that makes more sense. It looks like it's an issue with mediatomb

> dustin@ScrapYardDogZ:~$ ps aux | grep [m]ediatomb

That returned no results ? Is mediatomb not running ?

```
sudo /etc/init.d/mediatomb start
```

wait 10 seconds 

```
ps aux | grep [m]ediatomb
```

```
cat /etc/mediatomb/config.xml
```

Post results back here. Please use code tags though. It make it much easier to read. The code tags are the # button in the tool bar above where you type. Hightlight the text to wrap in code tags and press that # button.

Kind regards

---

### Post by SEMPERFIDELIS on 2011-03-02
No I didnt have mediatomb running at the time. I didnt think about it to be honest lol.

```
dustin@ScrapYardDogZ:~$ sudo /etc/init.d/mediatomb start
[sudo] password for dustin: 
 * Starting upnp media server mediatomb                                  [ OK ] 
dustin@ScrapYardDogZ:~$ ps aux | grep [m]ediatomb
115       1997  0.0  1.9 135556 29404 ?        Ssl  21:22   0:00 /usr/bin/mediatomb -c /etc/mediatomb/config.xml -d -u mediatomb -g mediatomb -P /var/run/mediatomb.pid -l /var/log/mediatomb.log
dustin@ScrapYardDogZ:~$ cat /etc/mediatomb/config.xml
<?xml version="1.0" encoding="UTF-8"?>
<config version="2" xmlns="http://mediatomb.cc/config/2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/2 http://mediatomb.cc/config/2.xsd"><!--
     Read /usr/share/doc/mediatomb-common/README.gz section 6 for more
     information on creating and using config.xml configration files.
    -->
  <server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:9d3ec305-3646-4394-992b-e6865eba7f95</udn>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage caching="yes">
      <sqlite3 enabled="yes">
        <database-file>mediatomb.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>localhost</host>
        <username>mediatomb</username>
        <database>mediatomb</database>
      </mysql>
    </storage>
    <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" --><!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    --><!--
    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    --><!-- Uncomment the line below if you have a Telegent TG100 --><!--
       <upnp-string-limit>101</upnp-string-limit>
    -->
    <extended-runtime-options>
      <ffmpegthumbnailer enabled="yes">
        <thumbnail-size>128</thumbnail-size>
        <seek-percentage>5</seek-percentage>
        <filmstrip-overlay>yes</filmstrip-overlay>
        <workaround-bugs>no</workaround-bugs>
      </ffmpegthumbnailer>
      <mark-played-items enabled="no" suppress-cds-updates="yes">
        <string mode="prepend">*</string>
      </mark-played-items>
    </extended-runtime-options>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/share/mediatomb/js/import.js</import-script>
        <dvd-script>/usr/share/mediatomb/js/import-dvd.js</dvd-script>
      </virtual-layout>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
        <map from="mp3" to="audio/mpeg"/>
        <map from="ogg" to="application/ogg"/>
        <map from="asf" to="video/x-ms-asf"/>
        <map from="asx" to="video/x-ms-asf"/>
        <map from="wma" to="audio/x-ms-wma"/>
        <map from="wax" to="audio/x-ms-wax"/>
        <map from="wmv" to="video/x-ms-wmv"/>
        <map from="wvx" to="video/x-ms-wvx"/>
        <map from="wm" to="video/x-ms-wm"/>
        <map from="wmx" to="video/x-ms-wmx"/>
        <map from="m3u" to="audio/x-mpegurl"/>
        <map from="pls" to="audio/x-scpls"/>
        <map from="flv" to="video/x-flv"/>
        <map from="mkv" to="video/x-matroska"/>
        <map from="mka" to="audio/x-matroska"/><!-- Uncomment the line below for PS3 divx support --><!-- <map from="avi" to="video/divx"/> --><!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 --><!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
        <map from="application/ogg" to="object.item.audioItem.musicTrack"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="audio/L16" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
        <treat mimetype="video/mp4" as="mp4"/>
        <treat mimetype="audio/mp4" as="mp4"/>
        <treat mimetype="application/x-iso9660" as="dvd"/>
        <treat mimetype="application/x-iso9660-image" as="dvd"/>
        <treat mimetype="video/x-matroska" as="mkv"/>
        <treat mimetype="audio/x-matroska" as="mka"/>
      </mimetype-contenttype>
    </mappings>
    <online-content><!-- Make sure to setup a transcoding profile for flv -->
      <YouTube enabled="no" refresh="28800" update-at-start="no" purge-after="604800" racy-content="exclude" format="flv" hd="no">
        <favorites user="mediatomb"/>
        <standardfeed feed="most_viewed" time-range="today"/>
        <playlists user="mediatomb"/>
        <uploads user="mediatomb"/>
        <standardfeed feed="recently_featured" time-range="today"/>
      </YouTube>
      <Weborama enabled="no" refresh="28800" update-at-start="no">
        <playlist name="Active" type="playlist" mood="active"/>
        <playlist name="Metal" type="playlist">
          <filter>
            <genres>metal</genres>
          </filter>
        </playlist>
      </Weborama>
      <AppleTrailers enabled="no" refresh="43200" update-at-start="no" resolution="640"/>
    </online-content>
  </import>
  <transcoding enabled="no">
    <mimetype-profile-mappings>
      <transcode mimetype="video/x-flv" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="vlcmpeg"/>
      <transcode mimetype="application/ogg" using="oggflac2raw"/>
      <transcode mimetype="audio/x-flac" using="oggflac2raw"/>
    </mimetype-profile-mappings>
    <profiles>
      <profile name="oggflac2raw" enabled="no" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ogg123" arguments="-d raw -o byteorder:big -f %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>
      <profile name="vlcmpeg" enabled="no" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="vlc" arguments="-I dummy %in --sout #transcode{venc=ffmpeg,vcodec=mp2v,vb=4096,fps=25,aenc=ffmpeg,acodec=mpga,ab=192,samplerate=44100,channels=2}:standard{access=file,mux=ps,dst=%out} vlc:quit"/>
        <buffer size="14400000" chunk-size="512000" fill-size="120000"/>
      </profile>
    </profiles>
  </transcoding>
</config>
dustin@ScrapYardDogZ:~$ 

```

---

### Post by matt_symes on 2011-03-02
Hi

Change the configuration file from

```
<server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
```

to

```
<server>
    <ui enabled="yes" show-tooltips="yes">
      <accounts enabled="yes" session-timeout="30">
        <account user="dustin" password="*your user password*"/>
      </accounts>
    </ui>
```

where *your user password* is your Ubuntu password then resart mediatomb

```
sudo /etc/init.d/mediatomb restart
```

You will have to log with that user name and password to mediatomb web interface and try checking your home folder again.

To be honest i am not sure if that will fix it and i have to sleep now. 
However i have mediatomb running on my server (it's great) and i'm sure, between the pair of us, we can get it fixed.

If it does not work post the output of (between code tags)

```
cat /var/log/mediatomb.log
```

We can pick this up tomorrow.

Kind regards

---

### Post by SEMPERFIDELIS on 2011-03-02
Here is the output. Thank you for your assistance. Its greatly appreciated :-)

```
pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty31 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty32 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty32 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty33 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty33 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty34 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty34 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty35 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty35 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty36 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty36 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty37 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty37 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty38 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty38 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty39 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty39 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty40 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty40 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty41 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty41 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty42 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty42 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty43 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty43 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty44 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty44 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty45 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty45 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty46 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty46 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty47 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty47 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty48 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty48 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty49 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty49 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty50 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty50 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty51 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty51 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty52 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty52 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty53 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty53 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty54 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty54 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty55 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty55 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty56 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty56 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty57 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty57 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty58 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty58 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty59 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty59 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty60 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty60 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty61 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty61 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty62 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty62 , Too many levels of symbolic links
2011-03-01 10:31:27 WARNING: skipping //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/drivers/serial8250/serial8250/tty/ttyS0/device/tty/ttyS0/device/tty/ttyS2/device/tty/ttyS3/subsystem/tty63 : Failed to stat //sys/devices/platform/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/devices/pcspkr/subsystem/de

```

---

### Post by SEMPERFIDELIS on 2011-03-04
to the top. im guessing that output is no good.

---

### Post by matt_symes on 2011-03-08
Hi

Is that the only information in your log file ? That is certainly different than the contents on mine.

You config file is pretty much exactly the same as mine. Maybe the database has become corrupted.

```
sudo /etc/init.d/mediatomb stop
sudo mv /var/lib/mediatomb/mediatomb.db /var/lib/mediatomb/mediatomb.db.bak
sudo /etc/init.d/mediatomb start
```

If that does not fix it you can put the database file back

```
sudo /etc/init.d/mediatomb stop
sudo mv /var/lib/mediatomb/mediatomb.db.bak /var/lib/mediatomb/mediatomb.db
sudo /etc/init.d/mediatomb start
```

Kind regards

---

