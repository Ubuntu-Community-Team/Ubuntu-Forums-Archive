---
title: "Configuring mythtv through mythweb"
date: 2010-07-29
forum: Mythbuntu
---

### Post by BadPenny on 2010-07-29
I have finally set up my first mythtv installation (so please be gentle. :) ). It is a standalone backend using mythbuntu 10.04. Since this box will eventually go in my basement for recording, I will eventually set up frontends on my TVs and PCs on the main level.

So in the meantime, I am just mainly doing recordings on the backend, then convert-and-copy to my N900 and my wife's N810. But I have run into some configuration problems.

1) Transcoding doesn't work. In mythweb, if I go to Recorded Programs, then click on the Recording Details banner for a show, I have the option to Queue a job -> Transcode. When I do this, it fails. Here is an excerpt from the logs:

```

2010-07-29 09:50:03.471 Using runtime prefix = /usr
2010-07-29 09:50:03.478 Using configuration directory = /home/mythtv/.mythtv
2010-07-29 09:50:03.487 Empty LocalHostName.
2010-07-29 09:50:03.495 Using localhost value of stargazer
2010-07-29 09:50:03.513 New DB connection, total: 1
2010-07-29 09:50:03.524 Connected to database 'mythconverg' at host: localhost
2010-07-29 09:50:03.529 Closing DB connection named 'DBManager0'
2010-07-29 09:50:03.538 Connected to database 'mythconverg' at host: localhost
2010-07-29 09:50:03.547 Enabled verbose msgs: important
...
2010-07-29 09:50:03.567 Transcoding from /data/1048_20100727220100.mpg to /data/1048_20100727220100.mpg.tmp
2010-07-29 09:50:03.638 AFD: Opened codec 0x82ce910, id(MPEG2VIDEO) type(Video)
2010-07-29 09:50:03.646 AFD: codec MP2 has 2 channels
2010-07-29 09:50:03.654 AFD: Opened codec 0x82cf370, id(MP2) type(Audio)
...
2010-07-29 09:50:03.836 Transcode: Using autodetect profile: MPEG2
2010-07-29 09:50:03.838 No video information found!
2010-07-29 09:50:03.846 Please ensure that recording profiles for the transcoder are set
2010-07-29 09:50:03.858 Transcoding /data/1048_20100727220100.mpg failed
2010-07-29 09:50:03.865 Deleting /data/1048_20100727220100.mpg.tmp

```

A friend suggested setting the record profiles, but I don't see how to do that from mythweb. I go into settings, and don't find anyhwere to set record profiles.

2) I also have a similar problem with mythweather. I enabled it in mythbuntu-control-center, however, when I go to the weather page in the mythweb settings, I end up with a single tab. At the top it says

```

Inactive Screens

Warning!! No types were found in weathersourcesettings for hostname ()

```

And under active screens, I have buttons for up, down, edit and delete, but none of them seem to do anything. (The page reloads, but thats it...)

Is there a way to get these items working under mythweb? Or do I need to install mythtv-frontend?

I tried doing this on one of my Debian workstations, but this failed as well. The mythbuntu version is 0.23.0+fixes24158-0ubuntu2, while Debian is 0.23.1-0.1. My backend logs show

```

MainServer::HandleVersion - Client speaks protocol version 23056 but we speak 56!

```

It seems that I have painted myself into a corner. Is there a way to fix these problems? Any advice would be deeply appreciated.

--bp

---

### Post by nickrout on 2010-08-01
> **BadPenny said:**
> 
I tried doing this on one of my Debian workstations, but this failed as well. The mythbuntu version is 0.23.0+fixes24158-0ubuntu2, while Debian is 0.23.1-0.1. My backend logs show

```

MainServer::HandleVersion - Client speaks protocol version 23056 but we speak 56!

```

It seems that I have painted myself into a corner. Is there a way to fix these problems? Any advice would be deeply appreciated.

--bp

Upgrade both front and backends using the mythbuntu daily builds and the protocol version problem will go away.

---

