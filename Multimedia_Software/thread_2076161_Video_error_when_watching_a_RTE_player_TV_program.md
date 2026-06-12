---
title: "Video error when watching a RTE player TV program"
date: 2012-10-25
forum: Multimedia Software
---

### Post by Rytron on 2012-10-25
Hi.

A relative was going to watch this TV program in Firefox (sorry but I am not sure if someone else can watch it outside Ireland) [http://www.rte.ie/player/ie/show/10067440/](http://www.rte.ie/player/ie/show/10067440/). He got the error "**(UNCAUGHT) Error #2203**" as seen in the attached image.

He can watch YouTube videos without any problems. I tried another browser (Chromium) but had the same issue.

I disabled the adblock addons on both browsers and the video played the adverts but when it eventually got to the main TV program - the same error appeared.

He is using Ubuntu 12.04 with all updates applied. I also ran bleachbit.

Please help. Thanks.

---

### Post by TokyoCrusaders92 on 2012-10-26
Hi,
   Your getting this error because the video is encrypted / DRM'd.  To play this video the flash player downloads the required library into ~/adobe/Flash_Player/NativeCache/.... The problem is this downloaded library requires libhal which is not installed by default in a new install anymore.  The following steps will fix the issue (they may not all be necessary but it does work)

Close all browser windows

1)      remove the adobe cache   -  rm ~/.adobe -rf
2)      install hal & hal-info  -  sudo apt-get install hal hal-info

3)       reinstall adobe player   - sudo apt-get install flashplugin-installer --reinstall

Open your browser and you should be good to go !! 

Ruairi

---

### Post by Rytron on 2012-10-26
> **TokyoCrusaders92 said:**
> Hi,
   Your getting this error because the video is encrypted / DRM'd.  To play this video the flash player downloads the required library into ~/adobe/Flash_Player/NativeCache/.... The problem is this downloaded library requires libhal which is not installed by default in a new install anymore.  The following steps will fix the issue (they may not all be necessary but it does work)

Close all browser windows

1)      remove the adobe cache   -  rm ~/.adobe -rf
2)      install hal & hal-info  -  sudo apt-get install hal hal-info

3)       reinstall adobe player   - sudo apt-get install flashplugin-installer --reinstall

Open your browser and you should be good to go !! 

Ruairi

Cheers Ruairi. I will give it a go and tell you how it goes.
...

---

### Post by limcearna on 2012-10-28
I had the same problem and the the suggested solution worked

Thanks folks

---

### Post by Rytron on 2012-10-29
> **limcearna said:**
> I had the same problem and the the suggested solution worked

Thanks folks

Ditto. Just tried the solution last night, worked a charm. Thanks again TokyoCrusaders92 (Ruairi). :)

---

### Post by zaarina on 2012-11-07
Thanks, the fix worked perfectly.

---

### Post by geraldkelly on 2012-11-29
> **TokyoCrusaders92 said:**
> Hi,
   Your getting this error because the video is encrypted / DRM'd.  To play this video the flash player downloads the required library into ~/adobe/Flash_Player/NativeCache/.... The problem is this downloaded library requires libhal which is not installed by default in a new install anymore.  The following steps will fix the issue (they may not all be necessary but it does work)

Close all browser windows

1)      remove the adobe cache   -  rm ~/.adobe -rf
2)      install hal & hal-info  -  sudo apt-get install hal hal-info

3)       reinstall adobe player   - sudo apt-get install flashplugin-installer --reinstall

Open your browser and you should be good to go !! 

Ruairi

I have Ubuntu 12.10 with Gnome 3 and this fix worked perfectly me. Thanks! Now I won't need to miss a single episode of Home and Away! :)

---

### Post by entryubu on 2012-11-29
So the same fix can be applied to any other browser installed in Ubuntu?.  Hope so.

---

### Post by Rytron on 2012-12-23
I've just checked my laptop (Xubuntu 12.04) and got the same error. The above fix worked a charm.

However my main PC (Linux Mint 13) will no longer play any RTE Player TV programs since about 3 days ago. I get no error message, just this [image attached]. I tried the above fix and even rebooted but no joy.

Update: This alt site works fine, [http://www.rte.ie/playerxl/](http://www.rte.ie/playerxl/)

---

### Post by Gabe13 on 2013-04-16
> **TokyoCrusaders92 said:**
> 

Close all browser windows

1)      remove the adobe cache   -  rm ~/.adobe -rf
2)      install hal & hal-info  -  sudo apt-get install hal hal-info

3)       reinstall adobe player   - sudo apt-get install flashplugin-installer --reinstall

Open your browser and you should be good to go !! 

Ruairi


Thanks Ruairi,  I've been meaning to try and fix this for a while and your instructions worked perfectly.  (Using Linux Mint Maya - KDE)

---

