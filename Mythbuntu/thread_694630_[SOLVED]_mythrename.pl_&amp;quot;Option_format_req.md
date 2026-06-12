---
title: "[SOLVED] mythrename.pl &amp;quot;Option format requires an argument&amp;quot;"
date: 2008-02-12
forum: Mythbuntu
---

### Post by a_posse_ad_esse on 2008-02-12
I have a cron job set up to create human-readable symlinks for my recordings, and is as such:

```

*/10 * * * * /scripts/tim/mythrename.pl /var/lib/mythtv/recordings --format %T/%S /var/lib/mythtv/recordings --link /recordings

```

However, this format is not working, and I am receiving mail stating

```

Subject: Cron <tim@server> /scripts/tim/mythrename.pl /var/lib/mythtv/recordings --format
Option format requires an argument

```

I don't understand why I would be receiving this...  The --format arguments are there and the command works properly when run through the command line.

Any suggestions would be appreciated.  Thanks

---

### Post by a_posse_ad_esse on 2008-02-18
bump

---

### Post by dannyboy79 on 2008-02-20
I use mythrename.pl myself but don't mess around with using the --format at all. I just settle for the default. BUT when I look at the code of mythrename.pl you can see towards the top what the default names are set to be. maybe try editing the following line to only include the format you want.
My links come out like this:
CSI- Miami - 2008-02-04, 9-00 PM - Bang, Bang, Your Debt.mpg

so if you only wanted the %T and the %S
something like this maybe?

# Default filename format
    $dformat = '%T %- %S';

which should result in 
CSI- Miami - Bang, Bang, Your Debt.mpg

---

### Post by a_posse_ad_esse on 2008-02-20
The format that I selected creates directories for each show, then has the episodes within.  I am doing the symlinking option, and it just turns out nicer over the samba share.

What I'm not sure about is why it doesn't see the other half of the command.  What has me wondering is that the same command works just fine through the normal command line...

---

### Post by dannyboy79 on 2008-02-20
i do the symlink command as well. it may not be working thru the script because of the way the script is written, just try to change the default like I suggested and see what happens. here;s my crontab for mythrename.pl
0 * * * * /usr/local/bin/mythrename.pl --link /media/400gb/mythtv/readable-recordings

---

### Post by a_posse_ad_esse on 2008-02-21
It does appear to the the --format option that is at fault for whatever reason.  I can do without for the time being.

Thanks for your help.

---

### Post by dannyboy79 on 2008-02-21
why do without? i said, just change the mythrename.pl script where it says default and the linked human readable recordings will be the way you want them.

---

### Post by ronkinoz on 2008-03-05
Personally, I find this works well for me.

Shows categorized by title, but no dodgy file names for shows without a subtitle.  Also sortable by date recorded.

```
*/10 * * * * mythtv nice -n 19 /usr/bin/mythrename.pl --format "\%T/\%Y-\%m-\%d \%H\%i \%- \%T \%-\%S" --link /mythtv/readable-recordings
```

Cheers.

---

