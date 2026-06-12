---
title: "Grab uk movie times in myth?"
date: 2009-08-10
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-08-10
Has anyone had any success grabbing uk movie times in myth?  Google has only given me this link but sadly the script doesnt actually work;


[http://www.gossamer-threads.com/lists/mythtv/users/316916](http://www.gossamer-threads.com/lists/mythtv/users/316916)

Thanks.

---

### Post by roundhay on 2009-08-10
I use xmltv, this page has a useful guide for UK Freeview but you can set up for other TV providers in a  similar way

[http://parker1.co.uk/mythtv_id.php]("http://parker1.co.uk/mythtv_id.php")

---

### Post by ian dobson on 2009-08-10
Hi,

I use the feed from [http://www.bleb.org/](http://www.bleb.org/) and a small script to grab several BBC channels. The EIT I get from my cable provider is only this/next.

If you want I can dump the script here.

Regards
Ian Dobson

---

### Post by SiHa on 2009-08-10
I think the OP is talking about movie times, not channel listings.

I use the one from [ [COLOR="Blue"]_this thread_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1090793), it seems to need the postcode hardcoded in, eg:```
#!/usr/bin/perl

use HTML::Entities;
use LWP::UserAgent;
use HTML::TreeBuilder;
use strict;

# Google Movieshow Times URL
my $googleurl = "http://www.google.com/movies?near=[COLOR="Red"]S0150DJ[/COLOR]";

my $url = $googleurl;
.
.
.
```

I copied the googlemovies.pl script to /usr/local/bin and made executable by all:```
chmod a+x googlemovies.pl
```Then just entered the full path to this file in the 'Grabber' section of the Setup > Info Center Settings > Movie Centre Settings page.

It's not the prettiest, but it does the job.

Beware that older versions (like mine, in 8.04) of the Mythmovies plugin don't handle errors well (or at all). So the chances are that if there's a problem, you'll just get dumped to the desktop. I think this is fixed now, so you'll probably be OK if you're using something more recent.

HTH,

Simon

BTW, if you hadn't already figured it out, the Zipcode & Radius fields don't do anything with this script. I think I tried passsing the postcode as a parameter, but gave up at the first hurdle and hardcoded it.

---

### Post by geekyhawkes on 2009-08-10
Thanks I will give this a try, heres hoping i can get movie times with the script!  Cheers.


LEGEND!  Works perfectly!  Myth just keeps on getting better!

---

### Post by beerguzzler on 2009-09-26
I too have hardcoded my postcode into the script file, but still cannot get it to work in mythmovies.

Script runs perfectly via terminal but when trying to run in in mythmovies all I see is this:

[IMG]http://www.jadrallypix.me.uk/forum_pics/mythmoviesScreenshot.png[/IMG]

I've checked my setup page and it has the correct postcode and radius and then the path to the grabber - /usr/local/bin/googlemovies.pl

I've tried it with both the Zip code and radius fields blank in the setup screen, but all I get when I run mythmovies is the setup screen, so I figure these have to be populated.

At a loss as to why it isn't working.

---

### Post by beerguzzler on 2009-09-28
well, left it for a couple of days and tried it again this evening and it's now working!

Does anyone know if there's some kind of time related db update that the system needs in order for the movie data to be populated the first time?

---

### Post by jontywareing on 2009-10-18
Just thought you'd like to know that I've been maintaining/rewriting this script for some time now, it used to have new versions posted into mythtv trac but I've now put it up on github so it's easy to find and fork.

[http://github.com/Jonty/Googlemovies/blob/master/googlemovies.pl](http://github.com/Jonty/Googlemovies/blob/master/googlemovies.pl)

Feel free to push changes back to me, I'll endeavour to merge them as quickly as possible.

Hope that helps someone,
--jonty

---

