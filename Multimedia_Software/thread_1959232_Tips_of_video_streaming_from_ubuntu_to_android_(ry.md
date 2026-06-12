---
title: "Tips of video streaming from ubuntu to android (rygel + upnplay + mx player)"
date: 2012-04-15
forum: Multimedia Software
---

### Post by meowmeowsama on 2012-04-15
Today I tried to figure out how to play the videos from my ubuntu desktop on my android phone. I ended up simple enough solution, and I hope this would help anyone trying to solve the same problem.

AFAIK, this solution:
* Does not need any paid apps.
* Does not require transcoding.
* Should work with zero customized script/config file.

Step 1. Install rygel on ubuntu
 ```
sudo apt-get install rygel
```

Step 2. Install upnplay on andorid.

Step 3. Install MX player on andorid (or whatever player you like, to play local video on your android)

Step 4. If your videos locate in ~/Videos then you can skip this step. Otherwise, you can edit /etc/rygel.conf, change the "uris" field to the folders with your media files.

Step 5. Run rygel in command line (no sudo). It might have some heavy IO if you have huge media library (I simply disabled the mp3 files discovery in the config, since I do not want to play those)

Step 6. Open upnplay on your andorid, you should see your ubuntu media library. Locate and click the video file, choose the video player you want to use (MX player in my case). And it plays ;)

I don't want to mess up with ufw, so I simply disabled it when I tried this, not sure if it is necessary~


Tested on:
Ubuntu 12.04
Galaxy Nexus
with some divx music videos.

---

### Post by dnns on 2012-06-02
That's exactly what I did.

If you have an extensive library, indexing might take days! This is due to the fact that Rygel is configured to extract metadata by default. Disable the extract-metadata in rygel.conf to speed up initial and subqequent crawling. For details see the manpage:

[http://manpages.ubuntu.com/manpages/natty/man5/rygel.conf.5.html](http://manpages.ubuntu.com/manpages/natty/man5/rygel.conf.5.html)

PS look for the rygel.conf file in your HOME/.config folder. The copy in the ETC/ folder is not used if there is one set up in HOME.

---

### Post by jensgeorg on 2012-06-20
> **dnns said:**
> That's exactly what I did.

If you have an extensive library, indexing might take days! This is due to the fact that Rygel is configured to extract metadata by default. Disable the extract-metadata in rygel.conf to speed up initial and subqequent crawling. For details see the manpage:

[http://manpages.ubuntu.com/manpages/natty/man5/rygel.conf.5.html](http://manpages.ubuntu.com/manpages/natty/man5/rygel.conf.5.html)

PS look for the rygel.conf file in your HOME/.config folder. The copy in the ETC/ folder is not used if there is one set up in HOME.

If you have _lots_ of videos, the meta-data extraction slows down for some reason I couldn't pinpoint yet; Restarting rygel every odd-hundred videos helps.

---

### Post by em wai zee on 2012-08-04
> **meowmeowsama said:**
> Today I tried to figure out how to play the videos from my ubuntu desktop on my android phone. I ended up simple enough solution, and I hope this would help anyone trying to solve the same problem.

AFAIK, this solution:
* Does not need any paid apps.
* Does not require transcoding.
* Should work with zero customized script/config file.

Step 1. Install rygel on ubuntu
 ```
sudo apt-get install rygel
```

Step 2. Install upnplay on andorid.

Step 3. Install MX player on andorid (or whatever player you like, to play local video on your android)

Step 4. If your videos locate in ~/Videos then you can skip this step. Otherwise, you can edit /etc/rygel.conf, change the "uris" field to the folders with your media files.

Step 5. Run rygel in command line (no sudo). It might have some heavy IO if you have huge media library (I simply disabled the mp3 files discovery in the config, since I do not want to play those)

Step 6. Open upnplay on your andorid, you should see your ubuntu media library. Locate and click the video file, choose the video player you want to use (MX player in my case). And it plays ;)

I don't want to mess up with ufw, so I simply disabled it when I tried this, not sure if it is necessary~


Tested on:
Ubuntu 12.04
Galaxy Nexus
with some divx music videos.

TQ a million ... Now, I'd stream video from Ubuntu to my Android Tab!

---

### Post by AN@S on 2012-09-12
When I run rygel I get this error message:


```
Rygel-Message: New plugin 'MediaExport' available
MediaExport-Message: 'file:///home/anas/Music' harvested
MediaExport-Message: 'file:///home/anas/Pictures' harvested
MediaExport-Message: 'file:///home/anas/Videos' harvested

** (rygel:9183): WARNING **: Failed to get SCPD: Connection terminated unexpectedly
The initial event message will not be sent.

** (rygel:9183): WARNING **: Failed to get SCPD: Connection terminated unexpectedly
The initial event message will not be sent.

** (rygel:9183): WARNING **: Failed to get SCPD: Connection terminated unexpectedly
The initial event message will not be sent.
```

On UPnPlay screen I can only see files stored on my Galaxy Nexus (Local Media).

What does that error mean?

---

### Post by jensgeorg on 2012-11-22
> **AN@S said:**
> When I run rygel I get this error message:


```
Rygel-Message: New plugin 'MediaExport' available
MediaExport-Message: 'file:///home/anas/Music' harvested
MediaExport-Message: 'file:///home/anas/Pictures' harvested
MediaExport-Message: 'file:///home/anas/Videos' harvested

** (rygel:9183): WARNING **: Failed to get SCPD: Connection terminated unexpectedly
The initial event message will not be sent.

** (rygel:9183): WARNING **: Failed to get SCPD: Connection terminated unexpectedly
The initial event message will not be sent.

** (rygel:9183): WARNING **: Failed to get SCPD: Connection terminated unexpectedly
The initial event message will not be sent.
```

On UPnPlay screen I can only see files stored on my Galaxy Nexus (Local Media).

What does that error mean?

Try another client.

---

