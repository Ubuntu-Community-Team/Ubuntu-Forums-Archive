---
title: "Can't rip DVDs"
date: 2011-02-05
forum: Mythbuntu
---

### Post by NautiusMaximus on 2011-02-05
I don't seem to be able to rip DVDs any more. I have successfully done so in the past, but today I can't. I think I may not have tried since upgrading to 10.04, so perhaps something in that version is different to previous versions?

I've tried with a couple of different DVDs and tried rebooting the computer, to no avail. If I choose the "Rip DVD" menu item, I get a screen saying only "No jobs. Checking and/or waiting for DVD". I know that the DVD must have mounted, because if I exit to the Ubuntu desktop I can see it sitting there and can browse the contents with no difficulty.

Here is what my mythfrontend log file was saying at the time I was trying:

```
2011-02-05 10:20:00.251 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-02-05 10:20:00.414 Loading menu theme from /usr/share/mythtv/themes/classic//mainmenu.xml
2011-02-05 10:20:00.426 Found mainmenu.xml for theme 'Mythbuntu'
2011-02-05 10:20:02.133 MythContext: Connecting to backend server: 172.16.100.20:6543 (try 1 of 1)
2011-02-05 10:20:02.133 Using protocol version 56
2011-02-05 10:20:02.316 'nice /usr/share/mythtv/mythweather/scripts/no_yrno/yrnoxml.pl -u SI -d /home/adam/.mythtv/MythWeather/yrno-XML United_Kingdom/England/Mitcham' has exited
2011-02-05 10:20:19.573 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/menu-ui.xml
2011-02-05 10:20:19.620 Loading menu theme from /usr/share/mythtv/videomenu.xml
mount: can't find /dev/sdc in /etc/fstab or /etc/mtab
2011-02-05 10:20:30.289 Failed to mount /dev/sdc.
2011-02-05 10:20:42.424 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/dvd-ui.xml
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
2011-02-05 10:21:00.322 Failed to mount /dev/sdd.
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
2011-02-05 10:21:30.362 Failed to mount /dev/sde.
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab
2011-02-05 10:22:00.402 Failed to mount /dev/sdf.
2011-02-05 10:22:22.912 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2011-02-05 10:22:23.140 MythVideo::ScanVideoDirectory Scanning (/media/disk2/mythtv/videos)
2011-02-05 10:24:05.339 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/dvd-ui.xml
mount: block device /dev/sr0 is write-protected, mounting read-only
2011-02-05 10:24:11.922 Detected MediaType MEDIATYPE_DVD
2011-02-05 10:26:16.595 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit

```

Any ideas what the problem is? Could it be a permissions thing? And if so, what do I need to give extra permissions to?

Many thanks
NM

---

### Post by nickrout on 2011-02-07
Which version are you using, this functionality has been removed from mythtv.

---

### Post by NautiusMaximus on 2011-02-12
Thanks for the reply. I'm using 10.04.

Are you really telling me you can't rip DVDs any more? Wasn't that, like, part of the core functionality of MythTV?

Is there any workaround?

Seems odd that there should still be an option in the menus that says "Rip DVD" if there was never any chance of it working.

---

### Post by thatguruguy on 2011-02-12
> **NautiusMaximus said:**
> Thanks for the reply. I'm using 10.04.

He wasn't asking which version of mythbuntu you are using.  He was asking which version of mythtv you are using. .23? .23.1? .24?

> **NautiusMaximus said:**
> Are you really telling me you can't rip DVDs any more?

Yep.  This has been written about extensively and repeatedly in this forum.

> **NautiusMaximus said:**
> Wasn't that, like, part of the core functionality of MythTV?

Nope. The core functionality of MythTV is as a pvr.  DVD ripping is an add-on.

> **NautiusMaximus said:**
> Is there any workaround?

Again, this has been discussed repeatedly.  Personally, I use handbrake.

> **NautiusMaximus said:**
> Seems odd that there should still be an option in the menus that says "Rip DVD" if there was never any chance of it working.

True.  That option has been removed from mythtv .24.

---

### Post by NautiusMaximus on 2011-02-13
As far as I know, I'm using MythTV 0.23. That's the version that comes with Mythbuntu 10.04, right? I haven't knowingly upgraded MythTV since installing Mythbuntu 10.04.

I do regularly run updates via the update manager, but that wouldn't upgrade to a new version, would it?

Also, if I choose system status from the frontend menus, it tells me that I'm running Mythfrontend 0.23.

So, in that case, presumably ripping DVDs ought to work, right?

Any idea why it doesn't?

---

### Post by tgm4883 on 2011-02-13
> **NautiusMaximus said:**
> As far as I know, I'm using MythTV 0.23. That's the version that comes with Mythbuntu 10.04, right? I haven't knowingly upgraded MythTV since installing Mythbuntu 10.04.

I do regularly run updates via the update manager, but that wouldn't upgrade to a new version, would it?

Also, if I choose system status from the frontend menus, it tells me that I'm running Mythfrontend 0.23.

So, in that case, presumably ripping DVDs ought to work, right?

Any idea why it doesn't?

Upgrade to the latest 0.23.0 version using [http://mythbuntu.org/repos](http://mythbuntu.org/repos)  then try again.

---

### Post by nickrout on 2011-02-13
> **NautiusMaximus said:**
> As far as I know, I'm using MythTV 0.23. That's the version that comes with Mythbuntu 10.04, right? I haven't knowingly upgraded MythTV since installing Mythbuntu 10.04.



That is a beta version of 0.23, use mythbuntu repos to upgrade to the latest 0.23.1 (you will need to do that on all your machines as there is a schema change between 0.23 and 0.23.1)

---

### Post by NautiusMaximus on 2011-02-19
Thanks for the replies.

So, if I've understood correctly:

By using an unmodified (apart from automatic updates installed via the update manager) version of Mythbuntu 10.04, I have MythTV 0.23.0, which is a beta version, and therefore potentially buggy. Correct?

If I update to MythTV 0.23.1, I will have a stable version, and one which still allows ripping of DVDs, correct?

---

### Post by tgm4883 on 2011-02-19
> **NautiusMaximus said:**
> Thanks for the replies.

So, if I've understood correctly:

By using an unmodified (apart from automatic updates installed via the update manager) version of Mythbuntu 10.04, I have MythTV 0.23.0, which is a beta version, and therefore potentially buggy. Correct?

If I update to MythTV 0.23.1, I will have a stable version, and one which still allows ripping of DVDs, correct?

No, well, not exactly.

The version of MythTV in the repos is a beta build of 0.23.0. (the actual version number is 0.23.0+fixes24158-0ubuntu2). Using the Mythbuntu repos you can update to the latest build of 0.23.0 (0.23.0++fixes25362-0ubuntu0++mythbuntu2), which is the released version + fixes. 

You also have the option of upgrading to 0.23.1 or 0.24 on 10.04 using the mythbuntu repos.

Your issue is likely fixed in a newer build (although your specific issue wouldn't be resolved in 0.24 since it doesn't exist anymore). If I were in your shoes I'd upgrade all my machines to 0.23.1 (or 0.24 and find another way of ripping dvd's)

---

### Post by NautiusMaximus on 2011-02-26
Many thanks for clearing that up.

So, I upgraded to MythTV 0.23.1, but sadly we're no further forward. I still can't rip DVDs, and the behaviour is the same as before. I still see the on-screen message "No jobs. Checking and/or waiting for DVD" when I try.

Here is what's in the MythFrontend log file at the time when I try:

```
2011-02-26 11:49:44.370 Loading menu theme from /usr/share/mythtv/videomenu.xml
2011-02-26 11:49:49.844 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/dvd-ui.xml
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
2011-02-26 11:50:07.458 Failed to mount /dev/sdd.
2011-02-26 11:50:28.672 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/dvd-ui.xml
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
2011-02-26 11:50:37.498 Failed to mount /dev/sde.
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab
2011-02-26 11:51:07.539 Failed to mount /dev/sdf.
2011-02-26 11:51:14.635 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

```

I'm a bit puzzled by the "failed to mount" messages, as I can play the DVD, I just can't rip it. My guess is that there are some permissions that haven't been set correctly, although I'm not sure what it could be. This is what the permissions for my videos directory look like:

```
drwxrwxrwx 2 mythtv mythtv 4096 2010-12-05 22:13 videos
```

Is that what it should look like? Are there other parts of the file system that need specific permissions that I should check? Or am I barking up the wrong tree and this is nothing to do with permissions at all?

NM

---

### Post by tgm4883 on 2011-02-26
> **NautiusMaximus said:**
> Many thanks for clearing that up.

So, I upgraded to MythTV 0.23.1, but sadly we're no further forward. I still can't rip DVDs, and the behaviour is the same as before. I still see the on-screen message "No jobs. Checking and/or waiting for DVD" when I try.

Here is what's in the MythFrontend log file at the time when I try:

```
2011-02-26 11:49:44.370 Loading menu theme from /usr/share/mythtv/videomenu.xml
2011-02-26 11:49:49.844 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/dvd-ui.xml
mount: can't find /dev/sdd in /etc/fstab or /etc/mtab
2011-02-26 11:50:07.458 Failed to mount /dev/sdd.
2011-02-26 11:50:28.672 XMLParseBase: Loading window theme from /usr/share/mythtv/themes/Mythbuntu/dvd-ui.xml
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
2011-02-26 11:50:37.498 Failed to mount /dev/sde.
mount: can't find /dev/sdf in /etc/fstab or /etc/mtab
2011-02-26 11:51:07.539 Failed to mount /dev/sdf.
2011-02-26 11:51:14.635 Deleting UPnP client...
Error in my_thread_global_end(): 1 threads didn't exit

```

I'm a bit puzzled by the "failed to mount" messages, as I can play the DVD, I just can't rip it. My guess is that there are some permissions that haven't been set correctly, although I'm not sure what it could be. This is what the permissions for my videos directory look like:

```
drwxrwxrwx 2 mythtv mythtv 4096 2010-12-05 22:13 videos
```

Is that what it should look like? Are there other parts of the file system that need specific permissions that I should check? Or am I barking up the wrong tree and this is nothing to do with permissions at all?

NM

Your barking up the wrong tree. The failed to mount messages are because you have a media reader without any media in it (like a SD card, CF card, etc)

---

### Post by NautiusMaximus on 2011-02-26
Yes, indeed I do: there is a card reader in the machine, which didn't have any media in it at the time I was trying.

Although it's a bit odd that that message should appear while I'm trying to rip a DVD, isn't it?

Anyway, if I am barking up the wrong tree, any idea what the right tree might be?

---

### Post by NautiusMaximus on 2011-03-05
Bump?

---

### Post by tgm4883 on 2011-03-05
> **NautiusMaximus said:**
> Bump?

Is mtd started? Can you start it from the terminal?

---

### Post by NautiusMaximus on 2011-03-12
> **tgm4883 said:**
> Is mtd started? Can you start it from the terminal?

I hadn't heard of mtd before, but after a brief Google search I assume you mean [this]("http://www.mythtv.org/wiki/MTD"), right?

Well, I'm not sure if it's started. This is all rather unfamiliar to me, but I tried the first step of the instructions of that page on mtd by typing 
```
mtd -n
```
at the command line as it suggested. That gave the following output: 

```
2011-03-12 10:21:40.121 Using runtime prefix = /usr
2011-03-12 10:21:40.121 Using configuration directory = /home/adam/.mythtv
2011-03-12 10:21:40.131 Empty LocalHostName.
2011-03-12 10:21:40.131 Using localhost value of htpc
2011-03-12 10:21:40.181 New DB connection, total: 1
2011-03-12 10:21:40.186 Connected to database 'mythconverg' at host: localhost
2011-03-12 10:21:40.186 Closing DB connection named 'DBManager0'
2011-03-12 10:21:40.187 Connected to database 'mythconverg' at host: localhost
2011-03-12 10:21:40.193 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1032
2011-03-12 10:21:40.242 Cannot load language en_us for module mythdvd
2011-03-12 10:21:40.245 MTD, Error: Can't bind to server port 2442
			There is probably copy of mtd already running.
			You can verify this by running 'ps ax | grep mtd'.
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.

```

I note that it says there is probably a copy already running, so I guess that means that mtd probably is started. I also note that it says I can verify this by running 'ps ax | grep mtd'. I'm afraid I'm not a Linux expert, so this seems a bit like a magic incantation to me, but anyway, I dutifully typed it at the command line. This was the result:

>  1736 ?        SNsl   0:35 /usr/bin/mtd -d
18629 pts/0    S+     0:00 grep --color=auto mtd


I have absolutely no idea what that means. So, could someone who understands this stuff better than I do tell me whether mtd is started?

If it is, what should I try next to fix my DVD ripping problem? And if it isn't, what should I try next to fix my DVD ripping problem?

Many thanks
NM

---

### Post by nickrout on 2011-03-12
ps ax lists all processes on your system. grep mtd searches for lines from the output of ps ax that contain the string 'mtd'.

so yes it is running, process number 1736.

---

### Post by NautiusMaximus on 2011-03-13
Great, thanks for explaining that. Little by little, the mysteries of Ubuntu are being revealed!

OK, so we've established that mtd is running. That presumably rules out one possible reason for my being unable to rip DVDs, right? Any ideas for any other problems that could be causing it?

Thanks
NM

---

### Post by NautiusMaximus on 2011-03-19
Bump?

---

