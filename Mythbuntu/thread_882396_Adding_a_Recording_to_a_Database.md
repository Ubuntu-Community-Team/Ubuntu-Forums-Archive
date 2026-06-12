---
title: "Adding a Recording to a Database"
date: 2008-08-06
forum: Mythbuntu
---

### Post by nicom on 2008-08-06
I am considering migrating my myth box from Knoppmyth to Mythbuntu. I have 7.10 loaded on a USB hard drive for experimentation and can successfully boot to it and operate it. One of my reasons for considering the migration is because of freezing problems I am having particularly with HD. As a test I would like to try playing particularly troublesome recordings through the player in Mythbuntu. I have copied over one such recording and want to add it to the database so it appears on the Recordings list. Is this possible? I have searched this and other forums about this matter but most solutions involve backing up the origin database and merging with the new database. I do not want to copy over the entire Knoppmyth database and recordings because it is too big for my USB hard drive.

I suppose I could treat the recording as a video and change the settings to play .mpg files with internal player but I am not sure this would tell me what I want to know. Will it still do the commercial skipping? Any thoughts?

---

### Post by nickrout on 2008-08-06
yes you need to use mythrebuilddatabase which should be in your system (use locate to find it, its tucked away in a documentation directory).

[http://www.mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/index.php/Myth.rebuilddatabase.pl)

---

### Post by ian dobson on 2008-08-07
Hi,

You might need to Install the perl module Time::Format for this script to work.

Just go to the terminal.
start cpan
then install Time::Format
then quit

Regards
Ian Dobson

---

### Post by nicom on 2008-08-09
Thanks for the replies. I looked for myth.rebuilddatabase.pl on my MythBuntu drive but could not find it. I did find it on my KnoppMyth drive so I copied it across. I suspect there are some dependencies that are required but I carried on regardless. I tried to run the script and got the following```
richard@mythbuntu-portable:~$ /usr/local/bin/myth.rebuilddatabase.pl --try_default
Can't locate Date/Parse.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/local/bin/myth.rebuilddatabase.pl line 54.
BEGIN failed--compilation aborted at /usr/local/bin/myth.rebuilddatabase.pl line 54.

```I then tried to install the Time::Format module in the hope that that was causing it and got```
richard@mythbuntu-portable:~$ sudo start cpan
start: Unknown job: cpan
richard@mythbuntu-portable:~$ sudo start /usr/bin/cpan
start: Unknown job: /usr/bin/cpan

```It is probably painfully obvious I don't know what I am doing here so any further assistance would greatly appreciated.

---

### Post by nickrout on 2008-08-10
you can't have looked very hard. the file is in  compressed format, and is part of the mythtv-backend package.

/usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz

you need to copy it somewhere sensible, unzip  it and make it executable:
```

sudo cp /usr/share/doc/mythtv-backend/contrib/myth.rebuilddatabase.pl.gz /usr/local/bin
sudo gunzip /usr/local/bin/myth.rebuilddatabase.pl.gz
sudo chmod +x myth.rebuilddatabase.pl
```


as for Time::Format, simply

```
apt-get install libtime-format-perl
```

---

