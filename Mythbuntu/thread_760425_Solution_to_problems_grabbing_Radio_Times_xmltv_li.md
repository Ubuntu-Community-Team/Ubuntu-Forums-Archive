---
title: "Solution to problems grabbing Radio Times xmltv listings"
date: 2008-04-20
forum: Mythbuntu
---

### Post by oscarsfriend on 2008-04-20
I thought I'd post this here in case it helps anyone.

The problem: Since Christmas the Radio Times website that provides programme listings for UK viewers has been having problems.  Often when grabbing listings the RT website will start off working, then timeout for no particular reason, and the grabber will fail.  This means that there will be no listings until the next time the grabber runs -- and even then it may timeout again.  (This may only be a problem if you grab your listings during the evening.)

After having this happen repeatedly, and then several days in a row, I decided to come up with a fix.

[B]NOTE: Please be confident you know what you are doing before tinkering around under the hood.  You might mess up your mythtv box otherwise.  You have been warned.
[/B]
The solution: Configure MythTV to run the following script to grab your listings, instead of running mythfilldatabase:

```

#!/bin/sh

export USER=[COLOR="Red"]YOUR_USERNAME_HERE[/COLOR]
export HOME=/home/$USER

SOURCEID=[COLOR="Red"]YOUR_SOURCE_ID_HERE[/COLOR]

TIMES=[COLOR="Lime"]5[/COLOR]
WAIT=[COLOR="Lime"]30[/COLOR]

CACHE=/tmp/tv_grab_uk_rt.cache
XML=/tmp/tv_grab_uk_rt.xml

while [ $TIMES -gt 0 ]
do
  tv_grab_uk_rt --quiet --cache=$CACHE --output $XML
  if [ $? -eq 0 ]; then
    if [ -s $XML ]; then
      mythfilldatabase --no-delete --file $SOURCEID -1 $XML
      rm -f $CACHE $XML
      exit 0
    else
      rm -f $CACHE $XML
      exit 1
    fi
  fi

  rm -f $XML
  sleep $WAIT

  TIMES=$(($TIMES - 1))
done

rm -f $CACHE

exit 1

```

A quick explanation of what this does: it reads the listings data from the RT website into a cache file, and processes the data into an xml file.  Should the website timeout, the grabber will be run again, and continue grabbing from where it left off, reading the already downloaded data from the cache.  It will do this up to five times (by default) before failing (and if it does fail, it won't bother to run mythfilldatabase, as it would ordinarily).

In order to use this script you will need to configure it first.  The information highlighted above in red must be set, the information in green can be altered if you wish.

Replace YOUR_USERNAME_HERE with the user mythfilldatabase is normally run as.  This will most probably be either "mythtv", or the username you log in as.  This is needed as the grabber looks for the channel list to download in /home/USER/.xmltv/tv_grab_uk_rt.conf

Finding the value for YOUR_SOURCE_ID_HERE is slightly more complicated.  (If you only have one source it will most likely be "1", but it is safer to check.)  You will need to connect to your mythtv database to get this info:

```

[COLOR="Gray"]$[/COLOR] mysql -p -u mythtv mythconverg
[COLOR="Gray"]mysql>[/COLOR] select * from cardinput\G
[COLOR="Gray"]mysql>[/COLOR] quit

```

You will need to enter your database password, which you can find in /etc/mythtv/mysql.txt.  You will need to read off the sourceid for the tuner card(s) you are grabbing listings for.

Please note that if you have more than one source, you may find that they sometimes switch places when you run mythtv-setup -- so you may need to reconfigure the script after running mythtv-setup.  If you only have one source (like I do), then this shouldn't be a problem.

TIMES (default=5) is the total number of times to run the grabber before giving up.  I suggest you don't set this too large, as when the RT website has real problems (as it occasionally does), you may find your grabber running this many times before giving up.  I find five times is more than enough for me, as I only grab listings for around 30 channels.  If you are grabbing a lot more listings you may need to increase this number.

WAIT (default=30) is the number of second to wait before running the grabber again.  You could probably set this to 0, as it takes some time for the grabber to fail when it times out, and a fair bit more time to read from the cache.  But I put this in just to be on the safe side.

You will need to set this script to run in your frontend (you may also need to run it with sudo, and maybe run visudo to configure it to run without needing a password -- I'm not sure this is necessary, though).

I've been testing the script for a couple of weeks now, and it has worked without failing.  I know it is working as I originally had it set to e-mail me each time the grabber failed and was restarted, and the first time it run by itself, it had to call the grabber 3 times to get all the listings.

This script has only been tested with MythTV version 0.20.2 and xmltv version 0.5.49.

I hope this has been of use to someone.

EDIT: For MythTV 0.21 the options for mythfilldatabase have changed a little.  In order to run the above script, you will need to change the line in the above from:
```

mythfilldatabase --no-delete --file $SOURCEID [COLOR="Red"]-1[/COLOR] $XML

```
to:
```

mythfilldatabase --no-delete --file $SOURCEID $XML

```
See [this link]("http://mythtv.org/wiki/index.php/Mythfilldatabase#3._Run_mythfilldatabase_with_the_--file_flag") for more info.

---

