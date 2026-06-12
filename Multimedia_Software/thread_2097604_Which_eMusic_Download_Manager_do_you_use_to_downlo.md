---
title: "Which eMusic Download Manager do you use to download music?"
date: 2012-12-23
forum: Multimedia Software
---

### Post by oscarivera9 on 2012-12-23
Hi everyone,
I'm wondering which download manager eMusic subscribers are using to download their eMusic purchases?   The two options that I've found so far are:[INDENT]
[LIST=1]
[*]The official eMusic Download Manager that you can get from their website.  However, that download manager is as old as the 2.2.14 linux kernel.
[*]The other option is emusicj, which is a java-based emusic download manager and it can be found here:  [http://www.kallisti.net.nz/EMusicJ/Download](http://www.kallisti.net.nz/EMusicJ/Download)  However, this download manager is also pretty old, the newest version is from 2010.
[/LIST]
[/INDENT]I've used both in the past and I haven't decided which one to use with my semi-fresh Ubuntu 12.04LTS install on a semi-new PC.
The emusicj has been a bit more reliable for me, but I'm wondering if anyone else has any fresh perspective on the issue or a good valid reason why they like to use the official download manager instead of the emusicj version.
This is perhaps the only other thread that I found that had any information on this issue and it's from 2009, or so it seems:  [http://ubuntuforums.org/showthread.php?p=12417519#post12417519](http://ubuntuforums.org/showthread.php?p=12417519#post12417519)

---

### Post by IsaacJGL on 2012-12-23
I just use google play and google music manager. It works for ubuntu :P

---

### Post by oscarivera9 on 2012-12-24
> **IsaacJGL said:**
> I just use google play and google music manager. It works for ubuntu :P

My question was specifically for eMusic subscribers, but I'm glad you answered and informed me about Google Play because I have Google Play on my Android and in my Windows, but last time I checked there wasn't a linux version available yet.  I have just installed it and will be using it from now on.

Thanks again.

---

### Post by Life On Mars on 2013-06-21
I previously used Banshee Media Player's eMusic plugin for downloading, but had some problems with it where it would skip or miss tracks for some reason.

I contacted eMusic support who helpfully suggested I install the new eMusic Download Manager for Linux. It's been 'available' since February 2013, although I don't think it's officially released yet. See [this post's comments]("https://plus.google.com/100263450914757358041/posts/iSHUacL5Y2F") for confirmation of details below:

1) Download from here:

32 bit: [http://www.emusic.com/apps/dlm/emusic-dlm-linux32-6.0.3.tar.bz2]("http://www.emusic.com/apps/dlm/emusic-dlm-linux32-6.0.3.tar.bz2")
64 bit: [http://www.emusic.com/apps/dlm/emusic-dlm-linux64-6.0.3.tar.bz2]("http://www.emusic.com/apps/dlm/emusic-dlm-linux64-6.0.3.tar.bz2")

2) Open the file with something like Archive Manager. This will extract the emusic-dlm executable.

3) Visit [http://www.emusic.com/dlm/install/](http://www.emusic.com/dlm/install/) to set the DLM5 cookie 

4) Buy a track or album. When the "Your Music Is Now Downloading" screen appears, the browser will prompt a download for "0.emx". When you open it, the OS should prompt you to choose an application to handle it... choose the emusic-dlm executable you extracted in Step 2. It should start downloading.&#65279;

Works well for me.

---

### Post by oscarivera9 on 2014-05-05
> **Life On Mars said:**
> I previously used Banshee Media Player's eMusic plugin for downloading, but had some problems with it where it would skip or miss tracks for some reason.

I contacted eMusic support who helpfully suggested I install the new eMusic Download Manager for Linux. It's been 'available' since February 2013, although I don't think it's officially released yet. See [this post's comments]("https://plus.google.com/100263450914757358041/posts/iSHUacL5Y2F") for confirmation of details below:

1) Download from here:

32 bit: [http://www.emusic.com/apps/dlm/emusic-dlm-linux32-6.0.3.tar.bz2](http://www.emusic.com/apps/dlm/emusic-dlm-linux32-6.0.3.tar.bz2)
64 bit: [http://www.emusic.com/apps/dlm/emusic-dlm-linux64-6.0.3.tar.bz2](http://www.emusic.com/apps/dlm/emusic-dlm-linux64-6.0.3.tar.bz2)

2) Open the file with something like Archive Manager. This will extract the emusic-dlm executable.

3) Visit [http://www.emusic.com/dlm/install/](http://www.emusic.com/dlm/install/) to set the DLM5 cookie 

4) Buy a track or album. When the "Your Music Is Now Downloading" screen appears, the browser will prompt a download for "0.emx". When you open it, the OS should prompt you to choose an application to handle it... choose the emusic-dlm executable you extracted in Step 2. It should start downloading.&#65279;

Works well for me.

Thanks for you input.  I had marked the thread as solved after a couple of months of no one discussing anything about it and just today while I was trying to install emusic manager again (I just recently upgraded to Ubuntu 14.04 from 12.04) I saw you reply.  I didn't know that there was a newer version but I'm installing it as we speak.
Thanks

:guitar:

---

### Post by Wolfsblood on 2014-06-26
Did you actually get those instructions to work? I've been struggling to get it installed for a while now but have had no success. I've followed the steps precisely, but I still get an error when I try to download tracks or albums because Ubuntu doensn't know what program to use to open the .emx file from Emusic. I've tried using the context menu to set the application, but the emusic_dlm doesn't appear in the list.  If it works well for you two, can you please let me know what I'm doing wrong? I'm using firefox and or chrome on Ubuntu 14.04.

---

### Post by dave_sisley on 2014-08-16
Sorry for the late response, but I was just wrestling with this today...

It may be that you need to associate the eMusic Download Manager with .emx files outside the browser -- this was true of chromium, where you can't set it in the browser.

After the .emx file downloads, just go to it via a file browser and right-click the file.  Whatever the file browser (I actually use Thunar which comes with XFCE, but this should work for Nautilus / Gnome and others as well...), you should be given a menu option of 'open with'.  Select that and have it point to the eMusic Download manager.  There should also be a checkbox or somesuch where you can say 'Always open files of this type with this app'.

Hope that helps.

-d.

---

