---
title: "Transcoding error"
date: 2012-12-02
forum: Mythbuntu
---

### Post by thegodfaza on 2012-12-02
When I attempt to transcode a video, it fails. My system is Ubuntu Server 12.10 and mythtv v0.26-pre-1367-gf831b99. The error is error 139 and log reads:
```
2012-12-02 17:19:43.900520 C  mythtranscode version: master [v0.26-pre-1367-gf831b99] www.mythtv.org
2012-12-02 17:19:43.900533 C  Qt version: compile: 4.8.3, runtime: 4.8.3
2012-12-02 17:19:43.917014 E  Error Loading en_us translation for module mythfrontend
2012-12-02 17:19:43.919906 E  Filter dir '/usr/lib/mythtv/filters' doesn't exist?
2012-12-02 17:19:43.925235 E  Filter dir '/usr/lib/mythtv/filters' doesn't exist?
2012-12-02 17:19:44.047745 E  SampleRate: Attempted to add a rate 32000 Hz, which is not in the list of allowed rates.
2012-12-02 17:19:44.277131 E  FilterManager: Failed to load filter 'onefield', no such filter exists
Transcoding failed for 1071_20121202032700.mpg with error 139
```

---

### Post by nickrout on 2012-12-02
That seems a very odd version of mythtv you are running. How about updating?

---

### Post by thegodfaza on 2012-12-02
I'm using the [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu) quantal main repository since the main ubuntu repo is broken.

---

### Post by nickrout on 2012-12-02
> **thegodfaza said:**
> I'm using the [http://ppa.launchpad.net/mythbuntu/0.27/ubuntu](http://ppa.launchpad.net/mythbuntu/0.27/ubuntu) quantal main repository since the main ubuntu repo is broken.More fool you. That is the master or development code, expect breakages.

---

### Post by thegodfaza on 2012-12-03
So other than compiling from source, where can I get a working mythtv install for ubuntu? The main repo for 12.10 is broken and wont even install and this repo apparently can't transcode.

---

### Post by nickrout on 2012-12-03
> **thegodfaza said:**
> So other than compiling from source, where can I get a working mythtv install for ubuntu? The main repo for 12.10 is broken and wont even install and this repo apparently can't transcode.I haven't used 12.10 so what is broke about their repo? (Personally for a mythtv box I would use 12.04 as it an LTS version)

You can use [http://ppa.launchpad.net/mythbuntu/0.26/ubuntu](http://ppa.launchpad.net/mythbuntu/0.26/ubuntu) to get the latest updates to 0.26-fixes - ie the current release (0.26) with fixes that have been applied after release.

However I am still surprised you say the 12.10 repo is broken, given quote a number of people are using it!

---

### Post by thegodfaza on 2012-12-03
> **nickrout said:**
> I haven't used 12.10 so what is broke about their repo? (Personally for a mythtv box I would use 12.04 as it an LTS version)

You can use [http://ppa.launchpad.net/mythbuntu/0.26/ubuntu](http://ppa.launchpad.net/mythbuntu/0.26/ubuntu) to get the latest updates to 0.26-fixes - ie the current release (0.26) with fixes that have been applied after release.

However I am still surprised you say the 12.10 repo is broken, given quote a number of people are using it!

Lots of people are having a variety of issues with the 12.10 repo version of mythtv. There are missing dependency problems (libmyth-0.25-0), issues with mythweb not working with the latest version of php, and different versions of different mythtv components installing. Anyway I seem to have fixed my issue. I installed mythbuntu-control-center and installed xfce and tightvncserver so I could get a GUI then I set the mythtv repo to the 0.26 repo. After a purge and reinstall everything appears to be working now. Though on mythweb for some reason all my thumbnail previews are 4:3 instead of 16:9.

---

