---
title: "Help: Anyone using a Samsung ML-1740 printer?"
date: 2011-02-04
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-04
Mythbuntu 10.10 (32bit)
xfce 4.6.2

I've been trying to get this Samsung ML-1740 printer to work which is connected via USB.

My goal is to print a pdf file.

I've installed CUPS v1.4.4 and SANE. No errors.
Using Cups in browser: [http://localhost:631/admin](http://localhost:631/admin) works fine.
1. CUPS sees Samsung ML-1740 and identifies it.
2. ML-1740 not in Samsung list nor is (SPL II) so I tried ML-1650, 1250, 1750 (gunshot approach). Nothing worked - no printing of pfd.
3.installed Adobe Reader 9.4.1 for linux via user and then uninstalled it and installed it under root. Didn't change anything. No joy.
4. installed xpdf as root. But it needed lpr.
5. installed lpr as root. no joy
6. installed splix  as root. Now Samsung ML-1740, ML-1710 appear as choices in CUPS. still no joy.
7. downloaded linux driver from Samsung and installed it as root. (This driver requires CUPS and SANE.) Choices for Samsung ML-1740 (SPL II) appear. no joy.
8. changed permissions on: chown root:root  ..../cups/filter/rastertosamsungspl and all files from Samsung driver install. no joy


I give up. What's the secret to getting this printer to work?

---

### Post by nickrout on 2011-02-04
I dunno, but it has nothing to do with mythbuntu!

What do your cups logs say?

When you say you installed acrobat reader and splix as root, did you use the ubuntu packages? If not, why not?

---

### Post by nhtrader on 2011-02-04
I was under the impression that this forum covered all things using mythbuntu. If it is strictly MythTV why didn't the powers that be create a MythTV forum?

I'll look for xfce forum for future posts. Sorry.

---

### Post by nickrout on 2011-02-04
Well it should work the same on any *buntu.

Anyway, we have started here, it doesn't matter that we might be on slightly the wrong forum. Anyway, let us know the answer to the things I posted and we'll work on it!

---

### Post by nhtrader on 2011-02-07
I got my Samsung ML-1740 to print pdf files using Adobe Reader 9.4.1 for linux.

After playing with this for hours, It turns out the problem was unique to printing pdf files using Adobe Reader.

CUPS  worked fine. I could print text files fine using "Geany".

I had to install one more package "cups-bsd"
used command: sudo apt-get install cups-bsd

Then opened adobe reader.
Opened pdf
Printed pdf - successful.

Apparently, Adobe reader uses "lpr" which is unavailable in Mythbuntu 10.10 (32bit)
Installing package CUPS is not enough.
Also required package cups-bsd so that adobe reader could access printers installed by CUPS.

Problem solved.

---

### Post by nhtrader on 2011-02-07
> **nickrout said:**
> I dunno, but it has nothing to do with mythbuntu!

What do your cups logs say?

When you say you installed acrobat reader and splix as root, did you use the ubuntu packages? If not, why not?

Here's the answer to your questions...


First, I had to make changes to CUPS log:

command: sudo pico /etc/cups/cupsd.conf...
changed line to: LogLevel debug
changed line to: MaxLogSize 5m

saved changes|exited file

command: service cups restart

No errors found in log.


As for Adobe Reader, I used Synaptic to search for:
adobe reader (only bleachbit package appeared. This deletes junk adobe reader files)
adobe (no reader found)
reader (no adobe found)

End result no adobe reader package found.

So I went to adobe.com to fetch adobe reader for linux...
AdbeRdr9.4-1_i486linux_enu.bin
(followed instructions with regards to installing *.bin)

I installed it as user. Then uninstalled it. Then installed it as root. 
I did this just to rule out possible permission problems.

As for splix, I used this command:
sudo apt-get install splix
(I don't remember why I chose this method)

---

### Post by nickrout on 2011-02-07
acrobat reader is available from ubuntu repos, but you have to enable the partner repository. Here is what my system says:

> nick@dell:~$ apt-cache policy acroread
acroread:
  Installed: 9.4.1-1lucid1
  Candidate: 9.4.1-1lucid1
  Version table:
 *** 9.4.1-1lucid1 0
        500 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages
        100 /var/lib/dpkg/status


---

### Post by nhtrader on 2011-02-09
> **nickrout said:**
> acrobat reader is available from ubuntu repos, but you have to enable the partner repository. Here is what my system says:

Here's what my system returns...

3:~$ apt-cache policy acroread
N: Unable to locate package acroread

(this of course doesn't recognize my manual install of adobe reader b/c I didn't use a repository package)

Thanks for providing me with a clue to enhance my understanding of using/customizing ubuntu - enabling a partner repository. 

This is new for me. Now I'll go and learn more about it.
 
PS - today's lesson for me is to upgrade MythTV  from 0.23-fixes to 0.24 Plus I want to learn how to use backup/restore MythTV database. Goal is to 1. Backup database 2. Upgrade 3. Restore (if necessary)

---

### Post by nickrout on 2011-02-09
1. Use the provided backup script, or run sudo /etc/cron.weekly/mythtv-database

2. sudo /etc/init.d/mythtv-backend stop

3. Install mythbuntu-repos. You will be asked to chose between 0.24 and 0.25. Choose 0.24. You will ba asked to chose a repo (ie a server location) - I usually go for ppa.

4. sudo aptitude update && sudo aptitude safe-upgrade

5. sudo /etc/init.d/mythtv-backend start

You should not need to restore the database.

---

