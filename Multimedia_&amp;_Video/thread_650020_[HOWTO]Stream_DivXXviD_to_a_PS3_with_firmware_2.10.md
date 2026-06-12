---
title: "[HOWTO]:Stream DivX/XviD to a PS3 with firmware 2.10 using MediaTomb and Ubuntu 7.10"
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by mrhorrible78 on 2007-12-25
After spending the last day and a half trying to get my newly build media server to stream my DivX/XviD movies to my PS3 I figured I'd share what I have learned and gather all the information I have so that people just setting this up for the first time have what will hopefully be an End to End account of how to set this up.  I know the following steps worked for me.  If you have any comments or additions please let me know!  First time I've written one of these so be nice...

**Step 1: Get Mediatomb**
First we have to add the Mediatomb repository to Apt
```
sudo wget http://apt.mediatomb.cc/key.asc -O- -q | sudo apt-key add -
echo "deb http://apt.mediatomb.cc/ feisty main" >> /etc/apt/sources.list 
```

Run the following Apt-Get Commands to get everything you need to run Mediatomb
```
sudo apt-get update
sudo apt-get install mediatomb
```

**Step 2: Configure Mediatomb**
Start Mediatomb for the first time to create initial config files and whatnot:
```
sudo mediatomb
```
After messages stop scrolling by press Ctrl-C to stop Mediatomb

Edit Mediatomb config File
```
gedit ~/.mediatomb/config.xml
```

Right under <server> add the following line:
```
<protocolInfo extend="yes"/>
```

Under <mappings>  <extension-mimetype ignore-unknown="no"> add the following:
```
<map from="avi" to="video/x-divx"/>
```
This allows the PS3 to recognize DivX and XviD, otherwise this will show up as video/x-msvideo or some such for mime type and the PS3 will just show all your videos as "Unrecognized File Type".  There are other useful mappings you might want to put in here to help Mediatomb give the PS3 some clues about what media type you're trying to serve to it, however that's beyond what I'm trying to accomplish here.

**Step 3: Start Mediatomb and Point it to your media files**
Here we will start Mediatomb and get it ready to start serving up your files.
```
sudo Mediatomb
```

Messages will scroll by, however you'll notice on the last line it'll give you a url that you can connect to to configure Mediatomb.  Just plug that in to your browser and it'll take you to a configuration page.  Click on filesystem and then browse to where your media is stored.  When you get there, click the little plus sign in the upper right hand corner to add a directory to the database.  The database side lets you take stuff back out if you need to.  If you want to run Mediatomb as a daemon you can add -d to the end of the command, that way you don't have to leave a console open.  

**Step 4: Start your PS3**
This presumes that you have already upgraded your PS3 to the 2.10 firmware.  If you haven't do this now.  If you have already upgraded, then you should be able to navigate to Video where you'll see your Mediatomb server and will be able to navigate to your DivX files and should hopefully be able to play most of them!

**Issues:**
The PS3 seems to be really picky about how media files are encoded.  Not all of my XviD or DivX files were able to play through the PS3 as is.  You may need to transcode some of your files to something compatible.  I found that the information listed here worked for me,
[http://www.tenshu.net/archives/2007/06/03/transcoding-video-for-the-ps3-in-ubuntu/]("http://www.tenshu.net/archives/2007/06/03/transcoding-video-for-the-ps3-in-ubuntu/")

*Edit:* Found that the following ffmpeg command works well for converting one of my AVIs that was not working into an Xvid file that does work:

```
ffmpeg -i <input file> -s 640x352 -vcodec xvid -b 1037k -acodec mp3 -ab 96k <output file>
```

YMMV - The settings I picked were from an XVID encoded file that works, and when I re-encoded the broken file it started working as well.

Another thing I noticed is that after some time, or after a few files were opened the PS3 stopped being able to access the media files.  Rebooting the PS3 seems to fix the issue.

Thanks to the folks who posted the following threads where I gathered this information from:
Dshipp - [http://www.avforums.com/forums/showthread.php?p=6045717]("http://www.avforums.com/forums/showthread.php?p=6045717")
Anthony Taylor - [http://www.freesoftwaremagazine.com/blogs/upnp_mediatomb_ps3_and_me]("http://www.freesoftwaremagazine.com/blogs/upnp_mediatomb_ps3_and_me")

---

### Post by arrrghhh on 2007-12-26
the first step doesn't really work right for me.  the first command asks for my pw 2x in one line, and only lets me enter it once.  just ran as root.  the "sudo joe /etc/apt/sourcs.list" - change it to ```
echo "deb http://apt.mediatomb.cc/ feisty main" >> /etc/apt/sources.list
``` no need to even open an editor.

also, change all the 'joe' references to 'gedit' - more ppl use gedit in these forums.  it's ubuntu default, and it's always nice to make things easy on people.

oh and you explained the second line addition in the .xml file, but what about "<protocolInfo extend="yes"/>" that one?  just curious as to what it does...


thanks for the great post, it worked like a charm!  very good how-to.  and don't worry about my criticalness, i just want to make your how-to better!

almost forgot, you should also add instructions so it runs all the time (at boot) so you don't have to have a terminal open for it when you want it running.

---

### Post by mrhorrible78 on 2007-12-27
Sweet, thanks for the suggestions!  I've updated joe to gedit and added the echo command to put the MediaTomb repository in the config file. The deal with joe was that I was installing  everything on a headless machine, so when it came time to write...well I just put down what I did!  Good call though, gedit is better if you've actually got something a bit better than a terminal to work with.

As for the <protocolInfo extend="yes"/> line, I'm not exactly sure what it does.  Near as I can tell it instructs MediaTomb to send along extended information to the end device.  I know that if you don't have it, everything shows up as "Unrecognized Format", much like if the mime type mapping wasn't updated.

---

### Post by arrrghhh on 2007-12-27
mrhorrible78:  you can remove the  "Add this to the sources.list file: Code: deb  [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main" as well... the echo line actually concatenates that onto the sources.list file... notice the >> - that delinates that it is pushing whatever is on the left onto the right side, so the source onto /etc/apt/sources.list

but enough of my rambling - what about a good way to run it at boot?  would the easiest just to be add an entry to /usr/share/autostart?  and a symbolic link or what, because everything else there is a .desktop file... sorry maybe i'm asking something that's off-topic, but i'd really rather not have a terminal running constantly just to have mediatomb serving media to my ps3...


so when i run "gksu mediatomb" in the run dialog, mediatomb runs (and it asks for my admin pw) but the ps3 doesn't recognize any of the content, except for old mpg stuff etc... like it's using a different .xml file.  because when i run 'sudo mediatomb' in a terminal it works fine with all the divx stuff... strange.  i'd really like to figure out how to get this to run outside of a terminal so it'll go at boot!

---

### Post by Subban on 2007-12-27
> **arrrghhh said:**
> mrhorrible78:  what about a good way to run it at boot?  would the easiest just to be add an entry to /usr/share/autostart?  and a symbolic link or what, because everything else there is a .desktop file... sorry maybe i'm asking something that's off-topic, but i'd really rather not have a terminal running constantly just to have mediatomb serving media to my ps3...

I simply added it to my session (panel menu System, Preferences, Sessions) on my machine at home.  I would be interested in a better method to start for all users though for at my brothers house  before I add it to all users sessions on his machine, at the moment I have him starting it manually as I only set it up for him via SSH from home.

---

### Post by mrhorrible78 on 2007-12-27
I haven't yet figured out how to get it to start automatically using just a terminal.  The instructions from the mediatomb site are as follows:

> There are basically two ways of starting MediaTomb: you can either start it directly as a normal user or run it as a deamon. For the latter a “mediatomb” user and group will be added automatically and you’ll find the configuration under /etc/mediatomb/config.xml, the logfile under /var/log/mediatomb and the database under /var/lib/mediatomb/. If you want MediaTomb to be started at boot time, change the NO_START option from "yes" to "" in the file /etc/default/mediatomb. To access the UI of the MediaTomb daemon open the file /var/lib/mediatomb/mediatomb.html in your browser.

This is from:
[http://mediatomb.cc/pages/download]("http://mediatomb.cc/pages/download")

However taking these steps didn't work for me...if someone wants to try it out and verify that it works for them then let me know I'll be glad to add it to the HOWTO.

---

### Post by mrhorrible78 on 2007-12-27
Also, if you run mediatomb -d it'll free your terminal session back up and run mediatomb in the background.

---

### Post by Subban on 2007-12-28
> **mrhorrible78 said:**
> I haven't yet figured out how to get it to start automatically using just a terminal.  The instructions from the mediatomb site are as follows:



This is from:
[http://mediatomb.cc/pages/download]("http://mediatomb.cc/pages/download")

However taking these steps didn't work for me...if someone wants to try it out and verify that it works for them then let me know I'll be glad to add it to the HOWTO.

Yes I had seen that, but it won't actually autorun it, that would just run it as a daemon once it is run, the same as 'mediatomb -d' that mrhorrible mentions.

I'll just add it to the users sessions at my brothers house, currently its goning to take longer to look for a faster, easier method than doing it the long way ;)

Incidently, has anyone had luck using the methods to automatically check for new media in the folders having media shared, i'm not sure its working here, more specifically the inotify method, does Ubuntu use that? If it does, should it recurse into subfolders ?

---

### Post by mrhorrible78 on 2007-12-28
I have mine set to check on a timer which seems to work just fine, it recurses into subfolders and everything.  I had tried inotify, but it didn't seem to update.

---

### Post by Subban on 2007-12-29
> **mrhorrible78 said:**
> I have mine set to check on a timer which seems to work just fine, it recurses into subfolders and everything.  I had tried inotify, but it didn't seem to update.

I had set up a couple of folders on timed updates, but I didn't really want to do pointless updates on my TV Eps folders and mp3 ones, they have quite a large number of files etc which is pointless scanning with no changes, especially as its my main pc here and I can do without the resource impact of the HD scans when not needed ;)

---

### Post by Finn61 on 2008-01-10
I just followed Mr Horrible's HOWTO and it installed a treat. Thanks for a good HOWTO.

> **Subban said:**
> Yes I had seen that, but it won't actually autorun it, that would just run it as a daemon once it is run, the same as 'mediatomb -d' that mrhorrible mentions.


As for the autostart business I noticed after installing it has placed an init script in /etc/init.d. There are also S20mediatomb links in /etc/rc2.d to /etc/rc5.d and K20mediatomb link in /rc6.d.  This suggests to me that it should start as a daemon when booting in any of these run levels and end nicely when shutting down.

When I booted however it didn't start. I will do a bit more digging and see if I can find out why.

---

### Post by Finn61 on 2008-01-10
I got Mediatomb running as a daemon from startup. This will ensure the server is always running when you reboot your system. Here is the method I used that works on Kubuntu 7.10 Gutsy (using Mr Horribles HOWTO with some changes)

Note: I recommend removing and re-installing mediatomb if you already have it installed. If you try and use this process with an existing database you created under your home user it gets messy.

**Step 1: Get Mediatomb**
If you haven't already done this add the repository to Apt
```

sudo wget http://apt.mediatomb.cc/key.asc -O- -q | sudo apt-key add -
echo "deb http://apt.mediatomb.cc/ feisty main" >> /etc/apt/sources.list

```

Run the following Apt-Get Commands to get everything you need to run Mediatomb
```

sudo apt-get update
sudo apt-get install mediatomb

```

**Step 2: Configure Mediatomb**
Note: There is no need to start Mediatomb as the config files are already in /etc.

Edit Mediatomb config File
```

sudo gedit /etc/mediatomb/config.xml

```

Right under <server> add the following line:
```

<protocolInfo extend="yes"/>

```

Under <mappings> <extension-mimetype ignore-unknown="no"> add the following:
```

<map from="avi" to="video/x-divx"/>

```

Now edit the Mediatomb defaults so it starts automagically
```

sudo gedit /etc/default/mediatomb

```

Comment the line NO_START="yes" by inserting a # at the beginning.
```

#NO_START="yes"

```

Uncomment the line #NO_START="" by removing the #
```

NO_START=""

```

This would normally be all the editing required but there is a bug in the startup script due to a variable not set at startup. So to resolve this you need to edit /etc/init.d/mediatomb

```

sudo gedit /etc/init.d/mediatomb

```

Replace this line
```

D_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -P $PIDFILE -l $LOGFILE"

```

With this
```

D_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -P $PIDFILE -l $LOGFILE -m /etc"

```

**Step 3: Reboot and Mediatomb Should Start**

After rebooting you can check the mediatomb daemon is running
```

ps -ef | grep mediatomb

```

Check the log to see messages indicating it created a new database and find the URL for the web interface
```

cat /var/log/mediatomb

```

Now continue from Step 4 in Mr Horrible's HOWTO.

Let me know if you have any issues. This worked fine for me.

Thanks again to Mr Horrible for the original configuration.

Cheers,

Finno

---

### Post by mrhorrible78 on 2008-01-12
OOooohhh, I'll have to give this a try, thanks Finno!

---

### Post by EXCiD3 on 2008-01-13
Whoo! Cant wait to try this! My roommate just got a PS3...:D No time for class/homework now!

---

### Post by hebetude on 2008-01-13
Getting back on topic ....

This worked for me, just add the avi -> x-video/divx mapping and mediatomb is setup to feed the divx information the PS3 is looking for.  You have to reimport all your *.avi movies after doing this, just rebooting mediatomb isn't good enough.  

No more transcoding to mp4, finally a reason to turn on my PS3!  If it's lucky I'll even unpair all my ps3 devices from Ubuntu :guitar:

---

### Post by dgray_from_dc on 2008-01-17
Has anyone tried gmediaserver?  I just pointed someone to this thread who was trying gmediaserver and couldn't figure out how to get started with it.  I use mediatomb and am quite happy with it.  I was just wondering how the two compare.

---

### Post by Subban on 2008-01-17
> **dgray_from_dc said:**
> Has anyone tried gmediaserver?  I just pointed someone to this thread who was trying gmediaserver and couldn't figure out how to get started with it.  I use mediatomb and am quite happy with it.  I was just wondering how the two compare.

I installed it prior to mediatomb and it just appeared to be a bit fiddly to setup and so I looked for something better, that something was mediatomb but as I didn't get gmediaserver working I can't really comment too much, it did seem geared towards music if I recall rather than video though.

---

### Post by mjwalfredo on 2008-01-17
Has anyone followed these directions with Ubuntu 7.04?  Does anyone know if it will work or not with 7.04?  Should I just go ahead and try it and let everyone know what I find?  Thanks!

---

### Post by njparton on 2008-01-17
I've just followed this excellent how to and mediatomb is up and running.

Does anyone know how to get Windows Media Player to receive/interface with mediatomb so that I can play mp3's remotely?

I can open the server config in a browser remotely so I know I don't have a firewall issue.  Can't seem to find anything in Windows media player that will allow me to get access to my music. 

Thanks

---

### Post by Finn61 on 2008-01-22
> **njparton said:**
> 
Does anyone know how to get Windows Media Player to receive/interface with mediatomb so that I can play mp3's remotely?


Hi njparton,

The easiest way to do this is to set up Samba to share out your music directory. Then just map a drive from your windows machine if you want to play your music from there.

Cheers,

Finno

---

### Post by njparton on 2008-01-22
That's what I already have set up but gradually vista somehow manages to mess up my music collection or it's own library references.  Every week or so I have to reset WMP - it's a real pain on a HTPC.

I may try just sharing it read-only, but ideally I'm looking for a media server solution.

---

### Post by Kriiiz on 2008-01-22
Nice work on this problem. It works fine.
Altough I managed to screw things up by messing with auto-scans.
After reinstall everything worked fine again.

If you wish to uninstall or reinstall mediatomb you have to undo the autostart script in /etc/default/mediatomb, otherwise it gives an error while uninstalling (because the daemon keeps running).

Just undo these steps:

> 
Now edit the Mediatomb defaults so it starts automagically

```
sudo gedit /etc/default/mediatomb
```

Comment the line NO_START="yes" by inserting a # at the beginning.

```
#NO_START="yes"
```



By uncommenting #NO_START="yes" the daemon won't start itself anymore when it is stopped, and you can uninstall/reinstall it.

---

### Post by mgm2rr on 2008-01-29
Hey, I got MediaTomb running on my Ubuntu 7.10 machine and it was great, I could watch movies on the PS3 very smoothly, but now all of the sudden Mediatomb doesnt show up on the PS3, even when I manually search for media servers.  Mediatomb is running in the terminal with no major error messages, and the internet connections of both machines are working, but for some reason the PS3 stopped seeing Mediatomb.  Does anyone know why this might happen and what the fix is?

---

### Post by mrhorrible78 on 2008-01-30
> **mgm2rr said:**
> Hey, I got MediaTomb running on my Ubuntu 7.10 machine and it was great, I could watch movies on the PS3 very smoothly, but now all of the sudden Mediatomb doesnt show up on the PS3, even when I manually search for media servers.  Mediatomb is running in the terminal with no major error messages, and the internet connections of both machines are working, but for some reason the PS3 stopped seeing Mediatomb.  Does anyone know why this might happen and what the fix is?

I had that happen when I left my PS3 on while I rebooted the Media server.  I wasn't able for some reason to re-discover the MediaTomb server.  I rebooted the PS3 and that would solve the problem for me.  You might want to see if you can connect to media tomb through some other device/program as well if you have that available...it'd help you isolate the problem to the PS3 or it's connection to your network.

---

### Post by mgm2rr on 2008-01-31
I never figured out what initially went wrong, but I was able to force mediatomb to use its original IP address with the "mediatomb -i 192.168.2.5" and its running fine now.

---

### Post by kulims on 2008-01-31
>> echo "deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main" >> /etc/apt/sources.list

What is the difference between the "feisty" version and the "gutsy" version.

---

### Post by kulims on 2008-01-31
I have installed mediatomb and trying to play mpg files (ripped from DVD) and an avi file.  My PS3 has 2.10 FW but it always says"  Unsupported Data"

I have 
protocolExted = "yes"

have inserted

from "avi" to "video/x-divx"
from "mpg" to "video/mp2p"


What am I missing. Thanks.

---

### Post by aboy on 2008-02-08
Thanx for the guides! I did the installation as described (using Ubuntu 7.10 and PS3 version 2.10), but when i start playing music i get a message on my PS3: "This PS3 system has been disconnected from the media server". But after that i can go right back and start the video or music file again.

Has anyone anyone seen this problem, or a solution to what i can do?

---

### Post by TechMansoor on 2008-02-17
I've tried a couple of things, but off hand, can anyone tell me why the ps3 will not recongize any of my files?



<?xml version="1.0" encoding="UTF-8"?>
<config xmlns="http://mediatomb.cc/0.10.0/config" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/0.10.0/config http://mediatomb.cc/0.10.0/config.xsd">
  <server>
	<protocolInfo extend="yes"/>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30"/>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:9798d1fc-d73a-47b9-b579-35c10b178663</udn>
    <home>/home/mansoor/.mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage driver="sqlite3">
      <database-file>mediatomb.db</database-file>
    </storage>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/share/mediatomb/js/import.js</import-script>
      </virtual-layout>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
	<map from="avi" to="video/x-divx"/>
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
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="application/ogg" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
      </mimetype-contenttype>
    </mappings>
  </import>
</config>

---

### Post by fulmitz on 2008-02-18
I tried this as you suggested but still mediatomb won't load on startup.  I cut and pasted right out of your post.  It works if I add the command to my sessions but I would like it to run on startup.  I had done a fresh install and did the original edit as per mediatomb's website.  for changing the nostart comment.  I then loaded my files.  When it didn't work I came accross your post.  I figured it was a pretty fresh install so I just changed the part you recommended at the end with

 D_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -P $PIDFILE -l $LOGFILE -m /etc"

Then I rebooted and when I went to localhost:49152 it says problem loading page.  If I open up terminal and run mediatomb -d it then finds it.  Any other suggestions?

Thanks,

Fulmitz

---

### Post by TechMansoor on 2008-02-19
> **kulims said:**
> I have installed mediatomb and trying to play mpg files (ripped from DVD) and an avi file.  My PS3 has 2.10 FW but it always says"  Unsupported Data"

I have 
protocolExted = "yes"

have inserted

from "avi" to "video/x-divx"
from "mpg" to "video/mp2p"


What am I missing. Thanks.

I'm experiencing the same exact thing. The only thing I can view is pictures? Have you resolved this issue yet?

---

### Post by paradoxni on 2008-02-21
Streaming media to the ps3 is great, but mediatomb and others for that matter annoy the hell out of me because I cant seem to limit which type of media is imported from each folder.

An example of what I mean is if I import my Photos folder and Music folder from my PC HDD into mediatomb, it will import any images found in the Photos AND Music folders (e.g. album art) which means my Photos section on the PS3 is full of thousands of images that I do not want to see, making it rather tedious to find holiday snaps etc

I would rather it just import ONLY images from the Photos folder and ONLY music from my Music folder. Is this possible?

---

### Post by TechMansoor on 2008-02-21
I'll address all the issues I"m having this weekend but, indeed, I see what you're saying. It does import all photos. But for me, thats all it streams, is the photo's. The video's section will not work for me period! Xvid, or divx both will not work. No one seems to be answering on this post so I guess I'll have to look for just as populated forums this weekend. Maybe you can take your question to linuxforums.com I think...

---

### Post by seensegal on 2008-02-21
Originally Posted by kulims  
I have installed mediatomb and trying to play mpg files (ripped from DVD) and an avi file. My PS3 has 2.10 FW but it always says" Unsupported Data"

I have
protocolExted = "yes"

have inserted

from "avi" to "video/x-divx"
from "mpg" to "video/mp2p"


What am I missing. Thanks.

I to have followed all the advice for getting mediatomb working with my PS3 but continue to get "Unsuported Data"....

---

### Post by paradoxni on 2008-02-21
> **seensegal said:**
> Originally Posted by kulims  
I have installed mediatomb and trying to play mpg files (ripped from DVD) and an avi file. My PS3 has 2.10 FW but it always says" Unsupported Data"

I have
protocolExted = "yes"

have inserted

from "avi" to "video/x-divx"
from "mpg" to "video/mp2p"


What am I missing. Thanks.

I to have followed all the advice for getting mediatomb working with my PS3 but continue to get "Unsuported Data"....

once u add the above to your config, you need to goto the web panel and remove your imported folders and re-add them.

---

### Post by seensegal on 2008-02-21
I have rebuilt the database, restarted the mediatomb daemon, reboot my box and PS3, ran the ffmpeg command to convert the file (copied from the net and a working example from my friend - his PS3/mediatomb works).  Alas, it is still not working

---

### Post by nonloso on 2008-02-27
> **TechMansoor said:**
> I've tried a couple of things, but off hand, can anyone tell me why the ps3 will not recongize any of my files?



<?xml version="1.0" encoding="UTF-8"?>
<config xmlns="http://mediatomb.cc/0.10.0/config" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/0.10.0/config http://mediatomb.cc/0.10.0/config.xsd">
  <server>
	<protocolInfo extend="yes"/>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30"/>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:9798d1fc-d73a-47b9-b579-35c10b178663</udn>
    <home>/home/mansoor/.mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage driver="sqlite3">
      <database-file>mediatomb.db</database-file>
    </storage>
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/share/mediatomb/js/import.js</import-script>
      </virtual-layout>
    </scripting>
    <mappings>
      <extension-mimetype ignore-unknown="no">
	<map from="avi" to="video/x-divx"/>
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
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="application/ogg" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
      </mimetype-contenttype>
    </mappings>
  </import>
</config>

I noticed this at 01:00  tonight...  look at which config.xml file you are changing...most likely it is not the same one mediatomb is using. There are visible files and none visible files.

In this example it says the following when I boot Mediatomb on linux

*2008-02-28 00:52:28    INFO: Loading configuration from: /root/.mediatomb/config.xml*
the one I had been changeing all day long was /etc/mediatomb/config.xml and not /root/.mediatomb/config.xml

Try to edit this file, restart mediatomb and add the directory where the movies are again. This will work.

---

### Post by knowitman on 2008-02-29
> josh@josh-desktop:~$ sudo wget [http://apt.mediatomb.cc/key.asc](http://apt.mediatomb.cc/key.asc) -O- -q | sudo apt-key add -
OK
josh@josh-desktop:~$ echo "deb [http://apt.mediatomb.cc/](http://apt.mediatomb.cc/) feisty main" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied


I can not get the second command in the instructions to work for me.  What can I possibly be doing wrong?

---

### Post by seensegal on 2008-03-01
Hey all..well after much digging and reading around, it became apparent that there where multiple config.xml files for mediatomb.  While I had been changing the /etc/mediatomb/config.xml file with the changes posted above, I was still getting the dreaded "unsupported data" error.  Reading the mediatomb website I was finally able to get it up and the files I loaded to play on my PS3, here is the command....

root@Stickville:/home/seen# mediatomb -p 41234 -c /home/seen/.mediatomb/config.xml -d

with the "-c" option I specified mediatomb to use the config.xml file that I wanted read and used for the PS3.  Now I can view my movies (given the files are in the proper format).

Thank you nonloso for the lead on figuring this problem out.

---

### Post by grammatonklaric on 2008-03-13
I finally got mine to work too, using Mediatomb 0.11.0, and PS3 firmware 2.17. Here is the text of my config file:

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:c4425c07-a131-403b-88a6-e1e2dc163b7f</udn>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>sqlite3.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>localhost</host>
        <username>mediatomb</username>
        <database>mediatomb</database>
      </mysql>
    </storage>
    <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
    <!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    -->
    <!--
    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    -->
    <!-- Uncomment the line below if you have a Telegent TG100 -->
    <!--
       <upnp-string-limit>101</upnp-string-limit>
    -->
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/share/mediatomb/js/import.js</import-script>
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
        <!-- Uncomment the line below for PS3 divx support -->
        <map from="avi" to="video/divx"/>
        <map from="divx" to="video/divx"/>
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
      </mimetype-contenttype>
    </mappings>
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
        <agent command="ogg123" arguments="-d raw -f %out %in"/>
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

This works perfectly with VLC installed.  I can see divx and xvid in AVI containers, as well as mpeg 2 files.  The only thing i need now is thumbnail support!

BTW, here were the two locations of my config files:

/home/<user>/.meditatomb/config.xml
/etc/mediatomb/config.xml

---

### Post by TechMansoor on 2008-03-13
> **grammatonklaric said:**
> I finally got mine to work too, using Mediatomb 0.11.0, and PS3 firmware 2.17. Here is the text of my config file:

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
  <server>
    <ui enabled="yes">
      <accounts enabled="no" session-timeout="30">
        <account user="mediatomb" password="mediatomb"/>
      </accounts>
    </ui>
    <name>MediaTomb</name>
    <udn>uuid:c4425c07-a131-403b-88a6-e1e2dc163b7f</udn>
    <home>/var/lib/mediatomb</home>
    <webroot>/usr/share/mediatomb/web</webroot>
    <storage>
      <sqlite3 enabled="yes">
        <database-file>sqlite3.db</database-file>
      </sqlite3>
      <mysql enabled="no">
        <host>localhost</host>
        <username>mediatomb</username>
        <database>mediatomb</database>
      </mysql>
    </storage>
    <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
    <!--
       Uncomment the lines below to get rid of jerky avi playback on the
       DSM320 or to enable subtitles support on the DSM units
    -->
    <!--
    <custom-http-headers>
      <add header="X-User-Agent: redsonic"/>
    </custom-http-headers>

    <manufacturerURL>redsonic.com</manufacturerURL>
    <modelNumber>105</modelNumber>
    -->
    <!-- Uncomment the line below if you have a Telegent TG100 -->
    <!--
       <upnp-string-limit>101</upnp-string-limit>
    -->
  </server>
  <import hidden-files="no">
    <scripting script-charset="UTF-8">
      <common-script>/usr/share/mediatomb/js/common.js</common-script>
      <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
      <virtual-layout type="builtin">
        <import-script>/usr/share/mediatomb/js/import.js</import-script>
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
        <!-- Uncomment the line below for PS3 divx support -->
        <map from="avi" to="video/divx"/>
        <map from="divx" to="video/divx"/>
        <!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
        <!-- <map from="avi" to="video/avi"/> -->
      </extension-mimetype>
      <mimetype-upnpclass>
        <map from="audio/*" to="object.item.audioItem.musicTrack"/>
        <map from="video/*" to="object.item.videoItem"/>
        <map from="image/*" to="object.item.imageItem"/>
      </mimetype-upnpclass>
      <mimetype-contenttype>
        <treat mimetype="audio/mpeg" as="mp3"/>
        <treat mimetype="application/ogg" as="ogg"/>
        <treat mimetype="audio/x-flac" as="flac"/>
        <treat mimetype="image/jpeg" as="jpg"/>
        <treat mimetype="audio/x-mpegurl" as="playlist"/>
        <treat mimetype="audio/x-scpls" as="playlist"/>
        <treat mimetype="audio/x-wav" as="pcm"/>
        <treat mimetype="video/x-msvideo" as="avi"/>
      </mimetype-contenttype>
    </mappings>
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
        <agent command="ogg123" arguments="-d raw -f %out %in"/>
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

This works perfectly with VLC installed.  I can see divx and xvid in AVI containers, as well as mpeg 2 files.  The only thing i need now is thumbnail support!

BTW, here were the two locations of my config files:

/home/<user>/.meditatomb/config.xml
/etc/mediatomb/config.xml

2.17..thats the newest ps3 update right? Did it come out yesterday or something? Ok, if you say it worked for you, I'll mimic your config file exactly and see if it'll work for me.

---

### Post by darkmdbeener on 2008-03-14
thanks for the how to help alot
do you think this could work on a xbmc xbox?

EDIT im rewrighting my statment

Some play realy good sound and everything is fine.
then for the ones that dont play, one of two things happen
      they say its unsoported 
      or i get and error 80028801

how would you fix this?

thanks

---

### Post by breaking on 2008-03-15
Ok, similar problems here. I got mediatomb working, my PS3 finds every file I indexed. Audo works fine, MPEG and DIVX too. However most of my Xvids don't work. I just get unsupported filetype, when I try to play them on my PS3. 

I have no idea what this could be about. e.g. 

```

foo.avi: RIFF (little-endian) data, AVI, 640 x 480, 25.00 fps, video: XviD, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)

```
plays well
```

foo2i: RIFF (little-endian) data, AVI, 720 x 544, 25.00 fps, video: XviD, audio: ADPCM (stereo, 44100 Hz)
foo3.avi: RIFF (little-endian) data, AVI, 640 x 480, 25.00 fps, video: XviD, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)

```

don't. Strange thing. Any idea?

Btw. I got thumbnails working, just install ffmpegthumbnailer from [http://code.google.com/p/ffmpegthumbnailer/](http://code.google.com/p/ffmpegthumbnailer/) and transcode as follows in mediatombs config:

```

<transcoding enabled="yes">
        <mimetype-profile-mappings>
                <transcode mimetype="video/divx" using="video-thumbnail"/>
        </mimetype-profile-mappings>

                <profile name="video-thumbnail" enabled="yes" type="external">
                        <mimetype>image/jpeg</mimetype>
                        <accept-url>yes</accept-url>
                        <thumbnail>yes</thumbnail>
                        <resolution>128x128</resolution>
                        <agent command="/usr/bin/ffmpegthumbnailer" arguments="-i %in -o %out -s 128"/>
                        <buffer size="524288" chunk-size="512" fill-size="1024"/>
                </profile>
        </profiles>
</transcoding>


```

---

### Post by brodie.hodges on 2008-03-21
> **mgm2rr said:**
> Hey, I got MediaTomb running on my Ubuntu 7.10 machine and it was great, I could watch movies on the PS3 very smoothly, but now all of the sudden Mediatomb doesnt show up on the PS3, even when I manually search for media servers.  Mediatomb is running in the terminal with no major error messages, and the internet connections of both machines are working, but for some reason the PS3 stopped seeing Mediatomb.  Does anyone know why this might happen and what the fix is?

I had this same problem.  My mediatomb was working great then one day it stopped showing up on my PS3.  I reinstalled the latest MediaTomb but my PS3 (on version 2.17 currently) still would not detect it.  So I went into ~/.mediatomb/ and renamed my config.xml to old.config.xml and restarted mediatomb without the -d option.  I noticed that the server is now starting 192.168.25.1:49153 instead of my computer's assigned IP.  This created a new config.xml but i was still not able to connect.  After opening vi and changed it to <protocolInfo extend="yes" /> and uncommented  <map from="avi" to="video/divx"/>
for PS3.  I then changed the uuid value to the value that was contained in my old.config.xml and restarted mediatomb using mediatomb -i (My Computer's IP).  Now it works again.

Hope this helps.
-Brodie

---

### Post by Lonergan on 2008-03-25
I have had much luck with mediatomb and the various versions of ubuntu.  My PS3 is running the latest firmware and at present I am running HH beta.  

Under XP, running Tversity, I have FLAC to PCM working (though Tversity is flaky as hell at the moment and I hate being in Windows anyway) and Twonkmedia can't seem to operate well with transcoding.  

Given that I know the PS3 can accept a PCM/WAV file from a transcoded FLAC, and Mediatomb is purported to do this, I was wondering if anyone has had success getting a successful stream from Ubuntu/mediatomb to the PS3?

Do I need to run some ffmpeg command or add some line in the config.xml? Or should the oggflac2raw command work?  So far I have nothing...so I'm assuming the latter is not sufficient.

---

### Post by dema on 2008-03-28
I've install mediatomb with this file:
[http://apt.mediatomb.cc/pool/main/m/mediatomb/mediatomb_0.11.0-1gutsy1_all.deb](http://apt.mediatomb.cc/pool/main/m/mediatomb/mediatomb_0.11.0-1gutsy1_all.deb)

Can anybody tell me, how to uninstall mediatomb now?

---

### Post by staaka on 2008-04-02
Nonloso, that was awesome, i would have never considered to re-add the directories, Much Thanks!!

---

### Post by Literati on 2008-04-06
Guys,

I'm getting this error when entering 'sudo mediatomb'
I didn't get it the first few times, but since I tried to make it start automatically, I'm getting it. 

2008-04-06 15:19:47   ERROR: SQLITE3: (5) database is locked
Query:UPDATE "mt_autoscan" SET "touched"=0 WHERE "persistent"=1 AND "scan_mode"='timed'
error: database is locked

I'll try a reinstall...
EDIT: Reinstall didn't fix it :(

---

### Post by Literati on 2008-04-06
Also, could someone please post the original of this line. I'm an idiot and didn't back it up... 

DAEMON_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -P $PIDFILE -l $LOGFILE"

There's more after LOGFILE that I took out, like $OPTIONS or something and something else...
Crap.

---

### Post by Zames007 on 2008-04-09
Hi
I don't know if this helps, but I was getting the very same thing as you, ERROR: SQLITE3: (5) database is locked. I found that if I hit Ctrl + C it closes mediatomb and then can be restarted again with no errors. It worked for me...

---

### Post by Posterus on 2008-04-17
> **Zames007 said:**
> Hi
I don't know if this helps, but I was getting the very same thing as you, ERROR: SQLITE3: (5) database is locked. I found that if I hit Ctrl + C it closes mediatomb and then can be restarted again with no errors. It worked for me...

I'm getting the same error and the Ctrl+C fix did not work for me :-\.  It's 1a.m. here and I don't intend to go to sleep until this problem is resolved! I will definetly post a fix if I find one.

--EDIT--

A reboot of my system seems to have worked for me. =] hope that solves future problems for anyone coming across this issue.

--**EDIT#2**--

All is going well except through the Web UI, I am unable to add the hard drive which contains all of my media (.avi's, .mp3's, etc...).  It will not let me click on the folder to which this drive is mounted to, I'm guessing that's telling me that mediatomb does not see any media there.  Is there something my tired brain is missing?

--Posterus

---

### Post by nihshs on 2008-06-07
> **Literati said:**
> Guys,

I'm getting this error when entering 'sudo mediatomb'
I didn't get it the first few times, but since I tried to make it start automatically, I'm getting it. 

2008-04-06 15:19:47   ERROR: SQLITE3: (5) database is locked
Query:UPDATE "mt_autoscan" SET "touched"=0 WHERE "persistent"=1 AND "scan_mode"='timed'
error: database is locked

I'll try a reinstall...
EDIT: Reinstall didn't fix it :(

to solve this problem just start your mediatomb without *sudo*
or if you already have it open your /home/usr/.mediatomb directory as root and change permission in properties of .db to usr


now the REAL problem
no matter I try my PS3 doesn't want to find any mediaservers (I've try different of them). 
Here what I have: PC with ubuntu hardy on it, PS3 with 2.35 firmware connected to PC straight into eth1, eth0 on PC for internet to my PS3 and PC.
Internet on PS3 works fine, mediatomb on computer works fine, but PS3 can't find any mediaserver (ms starting on eth1 (192.168.1.4) with port 49154 and I can see it through webinterface, but PS3 can't).
Maybe there is some trouble with network settings?

---

### Post by nuclearj on 2008-06-24
> **knowitman said:**
> I can not get the second command in the instructions to work for me.  What can I possibly be doing wrong?

I am having the same problem and then added it manually to the sources.list

---

### Post by luxor on 2008-06-27
> **Lonergan said:**
> I have had much luck with mediatomb and the various versions of ubuntu.  My PS3 is running the latest firmware and at present I am running HH beta.  

Under XP, running Tversity, I have FLAC to PCM working (though Tversity is flaky as hell at the moment and I hate being in Windows anyway) and Twonkmedia can't seem to operate well with transcoding.  

Given that I know the PS3 can accept a PCM/WAV file from a transcoded FLAC, and Mediatomb is purported to do this, I was wondering if anyone has had success getting a successful stream from Ubuntu/mediatomb to the PS3?

Do I need to run some ffmpeg command or add some line in the config.xml? Or should the oggflac2raw command work?  So far I have nothing...so I'm assuming the latter is not sufficient.

You can use either the oggflac2raw section of your config.xml file which calls ogg123 and outputs the data to raw pcm or you can use something like this:

[535] ranju@optimus:/ (03:31:02 PM)
-=>> cat /usr/bin/mediatomb-transcode-audio
#!/bin/bash

INPUT="$1"
OUTPUT="$2"
AUDIO_CODEC="pcm_s16le"
AUDIO_BITRATE="192k"
AUDIO_SAMPLERATE="44100"
AUDIO_CHANNELS="2"
#FORMAT="s16le"
FORMAT="s16le"

exec /usr/local/bin/ffmpeg -i "${INPUT}" -acodec ${AUDIO_CODEC} -ab ${AUDIO_BITRATE} -me zero -ar ${AUDIO_SAMPLERATE} -ac ${AUDIO_CHANNELS} -f ${FORMAT} - > "${OUTPUT}" # 2>/dev/null

I've tried this, and I know that my server is transcoding the flac files, however the PS3 does not seem to like the data it is receiving.

---

### Post by Lonergan on 2008-07-09
> **luxor said:**
> 

I've tried this, and I know that my server is transcoding the flac files, however the PS3 does not seem to like the data it is receiving.

Are you having problems with all files or merely the first one or two files in a folder?  The word length calculation is finicky.  8/10 I have "data not supported" for the first track of a playlist or folder I'm streaming, after that I could play 200 tracks in a row without problems. The key is that as the file is being transcoded to PCM the system has to know the word length.  Since the data hasn't been entirely cached into memory yet, the word length is unidentifiable and as such, the system figures it's a faulty file.  Just go to the next track and it should queue up fine.

---

### Post by Jeeevs2001 on 2008-07-11
Hi, sorry if this is hijacking the thread but I have been able to get MediaTomb to work almost perfectly with my Photo's Music and Video streamed from my Ubuntu 7.10 box to my (now 2.40) PS3. 

However, I can not get ffmpegthumbnailer to install. I have re installed both ffmpeg and ffmpegthumbnailer (latest versions of both compiled from source) and every time i try and install ffmpegthumbnailer it says ffmpeg is not found? 

Anyone else experiencing this issue? Or know of an alternative method to display thumbnail pictures for movies? 

thanks in advance, 
Jeeves

---

### Post by Fletch273 on 2008-07-24
> **grammatonklaric said:**
> 

BTW, here were the two locations of my config files:

/home/<user>/.meditatomb/config.xml
**/etc/mediatomb/config.xml**

Sorry if I'm being an idiot but I can't save the changes to this config file.  I can change the one in my own directory but not in the /etc directory.  How do I change this?

---

