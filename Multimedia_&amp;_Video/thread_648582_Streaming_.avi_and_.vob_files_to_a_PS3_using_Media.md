---
title: "Streaming .avi and .vob files to a PS3 using MediaTomb working"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by IMOC on 2007-12-23
After trying for hours I have finally managed to stream both .avi and .vob files to my PS3 using MediaTomb.  The .vob files even managed to keep their 5.1 surround sound!

To get this working I had to do the following over and above what is normally required to get MediaTomb to stream to a PS3.

(1) Edit the MediaTomb configuration file (/etc/mediatomb/config.xml) to set a suitable mime types for .avi and .vob file types.  My section of this file now looks like this:

    <mappings>
      <extension-mimetype ignore-unknown="no">
        <map from="avi" to="video/x-divx"/>
        <map from="vob" to="video/mpeg"/>
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

(2) Delete MediaTomb's database file (/var/lib/mediatomb/sqlite3.db) or the changes to the config file above wont do anything.  You will have to re-add you files to MediaTomb later.

(3) Restart MediaTomb.  I reboot my PC to achieve this.

(4) Re-add your media files files to MediaTomb in the usual way with the HTML interface.

(5) Ensure your PS3 has at least version 2.10 of the firmware installed.

(6) Re-boot your PS3 (or just select 'search for media servers') to ensure it has not cached the details of you media files.

That is it, your PS3 should be able to play streamed .avi files and .vob files.  

Please note that I don't condone piracy, but I do want to stream the DVDs I have bought from my PC to my living room.

Hopefully this will be of use to some.

--
Chris

---

### Post by Prisoner_97p904 on 2008-01-06
This only works for DivX, or also XviD?
I tried with some XviD's, and no luck.

---

### Post by cooljoe on 2008-01-08
It should be noted that In order to get this to work with ps3, one must add the following line:

<protocolInfo extend="yes"/> 

under the <server> line.  

Also, this particular file that you're editing did not work for me.  I had to change the lines in the

/home/user/.mediatomb/config.xml   file because I do not run mediatomb as root?

Otherwise, I did everything you said, just with the new file, and it fixed the "unsupported media" problem that I was having.

---

### Post by thanos3636 on 2008-02-09
I followed the above and still had trouble accessing *.vob files on my PS3.  After reading the Mediatomb help, I noticed that some file types may be case sensitive.  In the event your *.vob's are actually *.VOB, you will need to add this extension in all caps as well.  Great post & thanks for the help!

---

### Post by HeavyMetaler on 2008-02-10
/etc/mediatomb/config.xml is the config file used when it's running as a daemon using the init script.  It does not run as root, it runs as the "mediatomb" user that get's added if you installed using the deb from the repo.

---

