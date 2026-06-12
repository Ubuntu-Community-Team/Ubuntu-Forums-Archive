---
title: "Looking for Mpeg transcoder for Xbox 360, upnp server, etc"
date: 2008-07-11
forum: Multimedia Software
---

### Post by russfeld on 2008-07-11
Hello All-

I've been looking around for a while now, and I have found lots of promising answers, but none that fit the bill for what I need. 

Here is what I have:

[LIST]
[*]MythTV with Hauppauge PVR-150 card that records in MPEG-2 (.mpg), so lots of recordings in .mpg format
[*]Lots of music (.mp3 format) with complete ID3 tags
[*]An Xbox 360
[/LIST]

Here's what I've tried so far:

[LIST]
[*]x360mediaserve - works great for music but nothing else, doesn't run as daemon (but probably could...)
[*]uShare - the version I have doesn't work for music (only shows 50 songs), but videos work if in .wmv or .mov format
[*]MythTV - has UPnP support, so recording names show up fine, but under Music instead of Movies in the Xbox. Also, again, the recordings are .mpg, so Xbox won't read them anyway
[*]mp4tools with submitted mkxbox.sh script- should convert video to Xbox format, but no luck so far (maybe don't have correct settings)
[/LIST]

Here's what I'm looking for:

[LIST]
[*]A UPnP server that will allow my Xbox 360 to play music (correctly tagged by Artist/Album) and videos from my Ubuntu server.
[*]Something to convert my current videos (.mpg) to something that the Xbox can handle (.mov, .mp4, .wmv)
[/LIST]

I don't mind having to run more than one program to accomplish this. (I'm thinking x360mediaserve for music and uShare for videos) However, I have been very unsuccessful finding a way to convert the .mpg recordings made by MythTV to anything that the Xbox can play. 

It doesn't have to transcode on the fly (although that would be really cool), I can probably link it in to Mythweb or Mythtv so that recordings are transcoded automatically or by clicking a link in Mythweb. 

I'm pretty confident in my ability to play around with and try some command-line fu to get it to work. I've even considered looking at the source for x360mediaserve, since it seems to have the most promise. I'm just looking for anyone's advice on where to go from here. As I said my biggest concern is transcoding the .mpg files to something else. 

You guys have been great help in the past, and I look forward to any advice you may have!

Thanks,
russfeld

---

### Post by russfeld on 2008-07-12
OK, I found some answers (finally).

The mp4tools seem to actually do the trick for video encoding. They have Ubuntu packages listed here:
[http://teknoraver.net/software/mp4tools/](http://teknoraver.net/software/mp4tools/)

However, the default config file for uShare (at least from the packages I installed from [http://ushare.geexbox.org/](http://ushare.geexbox.org/)) in /etc/ushare.conf has a typo in it. All of the settings should be prefixed with USHARE_ but in their config file some are and some aren't. Mine is posted below:

```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=UltraLinuxBox-uShare

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=eth0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=49429

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/russfeld/uShare

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=no

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=no
```

I put symbolic links to my mythtv storage directory and other media directories in /home/russfeld/uShare to make things easier to play with

I also downloaded a mkxbox script for mp4tools that was posted in this thread (see reply #9):
[http://ph.ubuntuforums.com/showthread.php?t=684571](http://ph.ubuntuforums.com/showthread.php?t=684571)

Once I downloaded it, I changed the TWIDTH and THEIGHT variables to 1440 and 1080 to match my big screen TV (and the fact that all my recordings are standard def 4x3 ratio). Your settings/results may vary

I planted that script in /usr/bin with the same permissions and owner as the other mp4tools scripts. 

After that, in the MythTV setup, I enabled UserJob1 (very important) and set this as the command 

```
mkxbox %DIR%/%FILE% %DIR%/mythtv/%TITLE%_%SUBTITLE%.mov && wget http://192.168.0.22:49429/web/ushare.cgi?action=refresh -O /dev/null
```

That command will run the encoder and then cause uShare to refresh its shares (by using the cgi script it uses on its config website). Again, you will need to change the IP address and port to match your configuration.

I created a new folder in my MythTV storage directory called mythtv to store the transcoded recordings in. I also changed the uShare configuration to share that folder.

The most important part is to make sure the file created my mkxbox has a .mov extension and not .mp4. For some reason (ask M$ why) the Xbox won't read files with .mp4, but it will play them if they have .mov or .wmv file extensions.

I still haven't come up with a good solution to the music sharing problem yet. It sounds like MythTV is looking to implement that sometime in the future, and also uShare should be able to get it working, but for now the only thing that works is x360mediaserve. However, since it is Java based, it isn't well suited to run all the time. I may play with that some more this weekend and see what I get. 

If you find this guide useful, please let me know and I'll try and actually write it up a little better and post it other places. Also, if you find any errors, let me know. I'll be playing with it over the weekend and post any updates I have!

Thanks,
russfeld

---

### Post by russfeld on 2008-07-12
More notes as I've been playing around with it:

First of all, my command for the UserJob1 was missing quotation marks. It should read as follows:

```

mkxbox '%DIR%/%FILE%' '%DIR%/mythtv/%TITLE%_%SUBTITLE%.mov' && wget http://192.168.0.22:49429/web/ushare.cgi?action=refresh -O /dev/null
```

Also, I am now using the patched version of uShare from this thread:
[http://ubuntuforums.org/showthread.php?t=789118](http://ubuntuforums.org/showthread.php?t=789118)

I'm not sure how well it works yet, since I haven't done enough testing to know for sure. It would be nice to see it parse ID3 tags as well as x360mediaserve though.

I also made a link to my config file in /usr/local/etc/ so the patched version could see it as well (I think you can change that in the configure options but I was too lazy).

Thanks,
russfeld

---

### Post by russfeld on 2008-07-12
Yet another update...

For the music, I decided to go with x360mediaserve. However, I wanted to make it run as a daemon on the system, so I wouldn't have to worry about starting it when I wanted it, and if it crashed I would not have to restart it.

I found the Java Service Wrapper at:
[http://wrapper.tanukisoftware.org/doc/english/download.jsp](http://wrapper.tanukisoftware.org/doc/english/download.jsp)

I followed the instructions at:
[http://wrapper.tanukisoftware.org/doc/english/integrate-simple-nix.html](http://wrapper.tanukisoftware.org/doc/english/integrate-simple-nix.html)

but basically changed the config so all the files were in the root of the x360mediaserve directory. So, you will need to copy libwrapper.so, wrapper, wrapper.conf.in, wrapper.jar and sh.script.in to the root of the x360mediaserve directory. 

Here is my wrapper.conf file:

```

#********************************************************************
# Wrapper License Properties (Ignored by Community Edition)
#********************************************************************
#include ../conf/wrapper-license.conf

#********************************************************************
# Wrapper Java Properties
#********************************************************************
# Java Application
wrapper.java.command=/usr/bin/java

# Java Main class.  This class must implement the WrapperListener interface
#  or guarantee that the WrapperManager class is initialized.  Helper
#  classes are provided to do this for you.  See the Integration section
#  of the documentation for details.
wrapper.java.mainclass=org.tanukisoftware.wrapper.WrapperSimpleApp

# Java Classpath (include wrapper.jar)  Add class path elements as
#  needed starting from 1
wrapper.java.classpath.1=./wrapper.jar
wrapper.java.classpath.2=./x360mediaserve.jar
wrapper.java.classpath.3=./lib/cyberlink/clink170.jar
wrapper.java.classpath.4=./lib/cyberlink/cmgatejava120.jar
wrapper.java.classpath.5=./lib/jetty/commons-logging.jar
wrapper.java.classpath.6=./lib/entagged/entagged-audioformats-0.15.jar
wrapper.java.classpath.7=./lib/jetty/servlet-api-2.5-6.0.1.jar
wrapper.java.classpath.8=./lib/jetty/jetty-6.0.1.jar
wrapper.java.classpath.9=./lib/jetty/jetty-util-6.0.1.jar
wrapper.java.classpath.10=./lib/xerces/xercesImpl.jar
wrapper.java.classpath.11=./lib/xerces/xml-apis.jar
wrapper.java.classpath.12=./lib/cyberlink/clinkwrap.jar

# Java Library Path (location of Wrapper.DLL or libwrapper.so)
wrapper.java.library.path.1=./

# Java Additional Parameters
#wrapper.java.additional.1=

# Initial Java Heap Size (in MB)
#wrapper.java.initmemory=3

# Maximum Java Heap Size (in MB)
#wrapper.java.maxmemory=64

# Application parameters.  Add parameters as needed starting from 1
wrapper.app.parameter.1=Run

#********************************************************************
# Wrapper Logging Properties
#********************************************************************
# Format of output for the console.  (See docs for formats)
wrapper.console.format=PM

# Log Level for console output.  (See docs for log levels)
wrapper.console.loglevel=INFO

# Log file to use for wrapper output logging.
wrapper.logfile=./wrapper.log

# Format of output for the log file.  (See docs for formats)
wrapper.logfile.format=LPTM

# Log Level for log file output.  (See docs for log levels)
wrapper.logfile.loglevel=INFO

# Maximum size that the log file will be allowed to grow to before
#  the log is rolled. Size is specified in bytes.  The default value
#  of 0, disables log rolling.  May abbreviate with the 'k' (kb) or
#  'm' (mb) suffix.  For example: 10m = 10 megabytes.
wrapper.logfile.maxsize=0

# Maximum number of rolled log files which will be allowed before old
#  files are deleted.  The default value of 0 implies no limit.
wrapper.logfile.maxfiles=0

# Log Level for sys/event log output.  (See docs for log levels)
wrapper.syslog.loglevel=NONE

#********************************************************************
# Wrapper Windows Properties
#********************************************************************
# Title to use when running as a console
wrapper.console.title=@app.long.name@

#********************************************************************
# Wrapper Windows NT/2000/XP Service Properties
#********************************************************************
# WARNING - Do not modify any of these properties when an application
#  using this configuration file has been installed as a service.
#  Please uninstall the service before modifying this section.  The
#  service can then be reinstalled.

# Name of the service
wrapper.ntservice.name=@app.name@

# Display name of the service
wrapper.ntservice.displayname=@app.long.name@

# Description of the service
wrapper.ntservice.description=@app.description@

# Service dependencies.  Add dependencies as needed starting from 1
wrapper.ntservice.dependency.1=

# Mode in which the service is installed.  AUTO_START or DEMAND_START
wrapper.ntservice.starttype=AUTO_START

# Allow the service to interact with the desktop.
wrapper.ntservice.interactive=false


```

I then created a symlink in the /etc/init.d/ directory to the new sh.start file (renamed x360mediaserve) and ran 

```
update-rc.d /etc/init.d/x360mediaserve defaults
```

to register it. That seems to be working for the music.

---

