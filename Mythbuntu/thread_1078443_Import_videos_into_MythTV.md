---
title: "Import videos into MythTV"
date: 2009-02-23
forum: Mythbuntu
---

### Post by davidstoll on 2009-02-23
I have shows that were recorded on another mythtv box (that died) and I would like to import them to my new box.  I've seen methods for importing them using a mysql command and password, but it doesn't seem to work for me.  What is the best way to import videos (any type...even videos not recorded from myth...like avi) into my mythtv recorded shows list?

Thanks!

---

### Post by blackoper on 2009-02-23
myth.rebuilddatabase.pl script is what I use to import old recordings. It's kind of a pain to use though. I think it has a wiki entry:
yep found it: [http://mythtv.org/wiki/Myth.rebuilddatabase.pl]("http://mythtv.org/wiki/Myth.rebuilddatabase.pl")

---

### Post by davidstoll on 2009-02-23
> **blackoper said:**
> myth.rebuilddatabase.pl script is what I use to import old recordings. It's kind of a pain to use though. I think it has a wiki entry:
yep found it: [http://mythtv.org/wiki/Myth.rebuilddatabase.pl]("http://mythtv.org/wiki/Myth.rebuilddatabase.pl")

I ran
sudo find / -name myth.rebuilddatabase.pl
and it didn't find the script.

---

### Post by davidstoll on 2009-02-23
> **davidstoll said:**
> I ran
sudo find / -name myth.rebuilddatabase.pl
and it didn't find the script.

I found...
/local/mythtv-src/mythtv-0.20/contrib/myth.rebuilddatabase.pl.gz
so I unzipped it and now I get an error when I run this...

$ sudo /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl --dbhost localhost --file z.mpg

Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl line 55.
david@MythBuntu:/recordings/Default$ /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl --dbhost localhost --file z.mpg
Can't locate Time/Format.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl line 55.
BEGIN failed--compilation aborted at /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl line 55.

---

### Post by dannyboy79 on 2009-02-23
I am guessing that you have to install some perl dependencies. Did you read the README file that was in the gzipped file?

I always thought using the find_orphans.pl perl script was better? I could be wrong here though.

---

### Post by davidstoll on 2009-02-23
> **dannyboy79 said:**
> I am guessing that you have to install some perl dependencies. Did you read the README file that was in the gzipped file?

I always thought using the find_orphans.pl perl script was better? I could be wrong here though.

There was no readme in the gz file.  I looked inside it with...
gzip -l myth.rebuilddatabase.pl.gz

Only the .pl script.

---

### Post by vcallaway on 2009-02-25
sudo aptitude install libyaml-perl
sudo perl -MCPAN -e 'install Time::Format'

Should be able to press enter for the default answers.

---

### Post by davidstoll on 2009-02-25
> **vcallaway said:**
> sudo aptitude install libyaml-perl
sudo perl -MCPAN -e 'install Time::Format'

Should be able to press enter for the default answers.

I guess pearl is installed, but I still don't seem to be able to run (or even have?) myth.rebuilddatabase.py script.

---

### Post by dannyboy79 on 2009-02-25
i did this
```
sudo aptitude search perl > perl_modules.txt
```
then I opened that file and did a find for cpan and found this:
libtime-format-perl
so you may have to perform this command:
```
sudo aptitude install libtime-format-perl
```
other than that, I am not sure what to tell you.

---

### Post by davidstoll on 2009-02-25
> **dannyboy79 said:**
> i did this
```
sudo aptitude search perl > perl_modules.txt
```
then I opened that file and did a find for cpan and found this:
libtime-format-perl
so you may have to perform this command:
```
sudo aptitude install libtime-format-perl
```
other than that, I am not sure what to tell you.

The first command found nothing.
I ran the second command it it installed.

$ myth.rebuilddatabase.py
bash: myth.rebuilddatabase.py: command not found

---

### Post by dannyboy79 on 2009-02-25
the first command is going to put the standard output into a file called perl_modules.txt into whatever directory you're currently in. You didn't even need to do that. I did that work for you. Also, you're not running the correct command anymore, it suppose to be
```
sudo /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl --dbhost localhost --file z.mpg
```
at least that's what you ran earlier. Notice the .pl (perl) versus .py (python).

---

### Post by davidstoll on 2009-02-25
> **dannyboy79 said:**
> the first command is going to put the standard output into a file called perl_modules.txt into whatever directory you're currently in. You didn't even need to do that. I did that work for you. Also, you're not running the correct command anymore, it suppose to be
```
sudo /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl --dbhost localhost --file z.mpg
```
at least that's what you ran earlier. Notice the .pl (perl) versus .py (python).

I had to use the mysql password and the --dir option.

/usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl --dbhost localhost --pass XXXXXXXX --dir /recordings/Default/ --file z.mpg

Where XXXXXXXX is the mysql password found in Utilities/Setup->Setup->General
and also where /recordings/Default/ is the path to the default folder where all the mpg files are recorded, and as far as I can tell, you need to put the new file in this same folder too.

Lastly, the myth.rebuilddatabase.pl was gz zipped, so I had to unzip it.  I have no idea why it isn't already unzipped and ready to go.
/usr/share/doc/mythtv-backend/contrib/
gunzip myth.rebuilddatabase.pl.gz
did the trick.

Thank you for your help!  I really appreciate it.

Now, how do I mark this thread as "solved"?

---

### Post by dannyboy79 on 2009-02-25
> **davidstoll said:**
> I had to use the mysql password and the --dir option.

/usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl --dbhost localhost --pass XXXXXXXX --dir /recordings/Default/ --file z.mpg

Where XXXXXXXX is the mysql password found in Utilities/Setup->Setup->General
and also where /recordings/Default/ is the path to the default folder where all the mpg files are recorded, and as far as I can tell, you need to put the new file in this same folder too.

Lastly, the myth.rebuilddatabase.pl was gz zipped, so I had to unzip it.  I have no idea why it isn't already unzipped and ready to go.
/usr/share/doc/mythtv-backend/contrib/
gunzip myth.rebuilddatabase.pl.gz
did the trick.

Thank you for your help!  I really appreciate it.

Now, how do I mark this thread as "solved"?
most stuff comes zipped up to save space, remember all this stuff is crammed onto a cd (700mb) so where ever they can save space they are going to. Did you notice the difference in size between the gzipped one and the one that was extracted?
I think it's under "Thread Tools"

---

### Post by davidstoll on 2009-02-25
> **dannyboy79 said:**
> most stuff comes zipped up to save space, remember all this stuff is crammed onto a cd (700mb) so where ever they can save space they are going to. Did you notice the difference in size between the gzipped one and the one that was extracted?
I think it's under "Thread Tools"

There is a 3:1 compression rate on that particular file, but I wonder why they don't just uncompress it after installation.  Seems like many people use it, but all the "how to"'s seem to assume it is uncompressed and they also assume you know where it is...which a newbie like me doesn't.  Heck, I hardly know how to effectively use the find function....but I'm getting better thanks to all you guys.

The thread tools only have these options:
Show Printable Version
Email this Page
Subscribe to this Thred
Add a Poll to this Thread

I know people like it when you make something as solved.
I changed the title when I replied.  Maybe that will do it.

Thanks again

---

