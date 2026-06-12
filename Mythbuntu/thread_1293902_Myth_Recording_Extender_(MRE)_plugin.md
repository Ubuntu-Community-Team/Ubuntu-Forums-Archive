---
title: "Myth Recording Extender (MRE) plugin"
date: 2009-10-17
forum: Mythbuntu
---

### Post by jrockinl on 2009-10-17
I realize Myth Recording Extender isn't a supported plugin.  I would like to be able to record sports without having to add 60 minutes on to the end of the scheduled time.  I think that wastes too much hard drive space.

It seems to me that this would be a commonly desired feature.

I tried installing instructions from the following page:
[http://www.mythtv.org/wiki/Myth_recording_extender](http://www.mythtv.org/wiki/Myth_recording_extender)

I also realize this is pretty old information as it talks about MythTV 0.19+.  It also doesn't say which linux is used.  I have a feeling ubuntu places things in different areas than this page shows.

The steps I did:
> sudo apt-get update
> sudo apt-get install php5 php5-cli php5-mysql php5-pear php-db
> sudo ./configure
> sudo make install
   this failed on a "if [[ -f ... ]]" so I changed it to "if [ -f ... ]" and then it looked like it ran fine
> mre.php
  this give me "Fatal error: Unable to read conf file! in /usr/local/lib/mre/class/SysConf.php on line 177"

At this point, I am all out of ideas.  I am too new to linux.

---

### Post by blackoper on 2009-10-18
I had this working back in .19 I believe. I wouldn't mind finding out info on this myself. I would recommend you shoot off an email to the mythtv-users list with myth recording extender in the title and ask about it. I think i ran into problems trying to get it working last winter for college basketball season. The original developer of it was pretty active in the mailing lists. If you don't want to do the mailing list thing let me know and I'll send a question off

---

### Post by azmyth on 2009-10-19
I have it working in trunk. At least it starts but I haven't tested extending a recording.

You need to manually move the mre.conf to /etc so you have /etc/mre.conf.

You also need to edit some code to get it to work past 0.20. You also need to edit code to get the check to work. I'm not in front of my computer so I can't look.

---

### Post by blackoper on 2009-10-19
When you get a chance, let me know what changes need to be made to it. I plan on trying to use it during college basketball season coming up. (have a month until then so no rush)

---

### Post by jrockinl on 2009-10-21
I will try the idea of moving the mre.conf file to /etc.  I know nothing of bash, perl, or python so I would have no clue on editing those type files to get them to work with 0.22.

Thanks for the response.

---

### Post by azmyth on 2009-10-23
For some reason, the daemon switch set to true in the mre.conf caused problems so I set it to false and just used nohup mre.php & to start in the rc.local.

Also, needed to create a directory for the log files to be written and gave the user running mre permissions to use this.

On line 115 of the MythClient.php, you need to fix the spacing issues with the Library API version. You can get the correct spacing by doing a mythbackend --version

In the mre.php you need to define change the min version to something higher than 0.19.

---

### Post by blackoper on 2009-10-30
> **azmyth said:**
> 
On line 115 of the MythClient.php, you need to fix the spacing issues with the Library API version. You can get the correct spacing by doing a mythbackend --version
.

working on this now. I don't understand what you mean by getting correct spacing.

line 115 for me states:
         if(preg_match('/^Library API version: (.*)$/', $line, $matches))

and doing a mythbackend --version gives me

Please include all output in bug reports.
MythTV Version   : 22594
MythTV Branch    : branches/release-0-22-fixes
Network Protocol : 50
Library API      : 0.22.20091023-1
QT Version       : 4.5.2

So what should I change that line to read? Oh and I am going to update the wiki once I get this working

---

### Post by azmyth on 2009-10-30
It's hard to show this on these forums since it removes the spacing.

If you look at the code in the mre file. It's searching for a match of Library : and then after this it grabs the version. The spacing is off so when it searches for the Library: it doesn't come back with a match so it fails.

```

File in mre.php
Library          :

mythbackend --version
Library     :

```

View it and you'll see what I'm talking about with how the spacing is off.

---

### Post by blackoper on 2009-11-06
I figured out the spacing, after counting the spaces it appears to be 6 spaces needed.

Now onto hopefully the final problem:
what's your line read in mre.php line 27?

define('MIN_MYTH_VER', 22);

is what I have in there but logs indicate:
FATAL ERROR: Unable to contact Myth master backend or invalid MythTV version detected [0]! in /usr/local/bin/mre.php on line 70

---

### Post by azmyth on 2009-11-06
define('MIN_MYTH_VER', 19);

Change to above. My bad, I forgot you didn't need to change this because any version higher than 19 will work thus 22 will work.

---

### Post by azmyth on 2009-11-14
The parsers don't work. Looks like they search for the complete name like Chicago Bulls and espn now uses a <logo> Bulls.

---

### Post by blackoper on 2009-11-15
darn it was a really usefull script when it worked

---

