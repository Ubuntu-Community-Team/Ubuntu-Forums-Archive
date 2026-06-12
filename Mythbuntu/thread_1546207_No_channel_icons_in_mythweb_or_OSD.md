---
title: "No channel icons in mythweb or OSD"
date: 2010-08-04
forum: Mythbuntu
---

### Post by bcg30506 on 2010-08-04
I have the channel icons now downloaded and mapped for most all of my channels.  They show up perfectly in the Program Guide on the frontend.  However, they do not show up in the Playback OSD regardless of the theme nor in the Listings screen of mythweb.  The option is checked in the mythweb default settings.

Anyone have this working in 0.23?

---

### Post by bcg30506 on 2010-08-05
An update:  I now have the OSD showing channel icons while watching TV.  I simply had to exit the frontend and run it again after getting the icons setup in the database.

Still no icons on mythweb's listing page and nothing I've tried has worked.  So any suggestions or fixes would be appreciated.

---

### Post by bcg30506 on 2010-08-06
Been debugging this with my limited PHP knowledge, but have figured out enough to know the line that is causing me problems.

Under /var/www/mythweb in the modules/tv/classes/Channel.php file, line 49 is:

[PHP]if (file_exists($channel_data['icon'])) {[/PHP]

which is supposed to see if the icon file is local and copy it to the data/tv_icons location.  However it always returns false on my setup causing it to then try to ask the backend which fails since this directory is not under a web folder.

The problem is the file IS there as shown below:

```

$ ls -l /home/user/.mythtv/channels/wsb_atlanta.jpg
-rw-r--r-- 1 user user 11420 2010-08-04 23:23 /home/user/.mythtv/channels/wsb_atlanta.jpg

```

So now I'm stuck.  I do not know why php says the file does not exist when bash says it does.

---

### Post by bcg30506 on 2010-08-07
Getting much closer now to having channel icons in mythweb.  From my previous message in this thread, I commented out the check for file_exists so it would always try and copy as a local file.  After doing this, I got a new error message on the listings page which may help for real:

```

Warning at /usr/share/mythtv/mythweb/modules/tv/classes/Channel.php, line 51:
copy(/home/user/.mythtv/channels/espn.jpg): failed to open stream: Permission denied

```

So it's a permissions issue.  Now the question is what should permissions be and how do I do that when it's under my home directory without opening up the entire home private area to the world?

EDIT:  I did a poor man solution which works, but maybe not ideally.  I just went ahead and manually copied the icon files directly to the mythweb location with:
```
sudo cp ~/.mythtv/channels/*.jpg /var/www/mythweb/data/tv_icons/
```

---

