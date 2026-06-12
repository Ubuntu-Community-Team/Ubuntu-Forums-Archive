---
title: "TV recordings - naming convention"
date: 2008-11-09
forum: Mythbuntu
---

### Post by alexeix on 2008-11-09
Hi,

Is there any way to set the naming convention for TV recordings in Mythbuntu?

I aim to stream them to my Xbox 360, so I would like the file names to be automatically saved as something meaningful, for example, an episode of Heroes to be named Heroes-channel-date - Heroes-BBC2-05112008.

Is this, or something similar, possible?

Thanks.

---

### Post by newlinux on 2008-11-10
[http://www.mythtv.org/wiki/index.php/Mythrename.pl](http://www.mythtv.org/wiki/index.php/Mythrename.pl)

you can run it periodically as a cron, as a job to be run with each recording in myth.

---

### Post by SiHa on 2008-11-10
I've been meaning to ask the myself, you've saved me the trouble, thanks.
I guess you just run it as **user job #n** to run with each recording?

---

### Post by newlinux on 2008-11-10
> **SiHa said:**
> I've been meaning to ask the myself, you've saved me the trouble, thanks.
I guess you just run it as **user job #n** to run with each recording?

Yep, I think that should work.

---

### Post by anonymousdog on 2008-11-10
Just make really sure you understand what that script does.  Newer versions rename your actual recording files and fix the db to reflect the changes.  Command line switches are necessary to get the "old" behavior of creating a directory full of sensibly-named symlinks to untouched recording files.  I'm a little leery of that script's doing so much renaming and db fixing...seems like inviting trouble; so, I use it with the --link switch to create symlinks.  Besides, if you do that, you can create several different directories with different naming conventions: I do one that naturally sorts by original episode air date, another by recording date, etc...all with no heavy lifting or db mods.  You can set the naming convention by editing the script or, IIRC, via command line arguments.

In case you run it without arguments and want your default naming convention back on your recordings files, I can supply a script already coded for the default naming convention.

I really like the idea of running it as a user job; that obviates unnecessary runs as would happen with (a) cron job(s).  I just wish there were more user jobs available; all mine are taken by transcoding and commercial removal jobs.

---

### Post by alexeix on 2008-11-10
Is there a step-by-step guide for this somewhere?  I can see how to rename the files (i.e. the format), and I understand what you're saying about using --link, but I tried running my script (/usr/share/mythtv/contrib/mythrename.pl --link --verbose --format "%T %S %d%m%Y%H%i") from the terminal and got "command not found".

I'm still a MythTV/Linux newb and this is my first encounter with scripts, so go easy on me!

:)

Thanks.

---

### Post by newlinux on 2008-11-10
The ubuntu location of the script is:

/usr/share/doc/mythtv-backend/contrib/mythrename.pl.gz

you will need to unzip it and make it executable:

```

sudo gunzip /usr/share/doc/mythtv-backend/contrib/mythrename.pl.gz

sudo chmod +x /usr/share/doc/mythtv-backend/contrib/mythrename.pl

```
Then you can run it from there or copy the script somewhere in your executable path.

---

