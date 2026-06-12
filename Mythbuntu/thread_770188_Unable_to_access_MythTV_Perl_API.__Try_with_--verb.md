---
title: "Unable to access MythTV Perl API.  Try with --verbose to find out why."
date: 2008-04-27
forum: Mythbuntu
---

### Post by dsbw on 2008-04-27
[I]Unable to access MythTV Perl API.  Try with --verbose to find out why.
[/I]
I logged in with PuTTY and got this message, after a bunch of MythTV status info. This appears to be a new feature for 8.04. (I don't recall ever getting status updates when telnetting in before.)

Actually, the full output is:

```
MythTV status for localhost
===========================
Status..........: Sun Apr 27 2008, 2:10 AM
Total Disk Space: Total space is 703,874 MB, with 37,665 MB used (5.4%)

Encoders:
castle (1) - Watching LiveTV

Recording Now:
Unknown (Unknown) Ends: 02:59:14

Schedule Conflicts:
Unable to access MythTV Perl API.  Try with --verbose to find out why.

```

So, my question is "Try WHAT with --verbose to find out why?" :popcorn:

---

### Post by uopjohnson on 2008-04-30
I did some digging around until I finally found mythtv-status in /usr/bin/ I still don't know how it is called on login, but that is where this is coming from.  It seems to be trying to load a perl class names Mythtv, which isn't there.  calling mythtv-status --verbose doesn't give any more information and I didn't want to dig any further into the script.

Does anyone know what this class is, or why it is being called in this script since it isn't present on a default install?

---

### Post by superm1 on 2008-05-01
There is a bug opened on this issue.  It appears to be boiling down to the fact that the root user doesn't have a .mythtv directory.  Try copying your directory ~/.mythtv to /root and wait 10 minutes to see if it refreshes properly.

---

### Post by whoisvince on 2008-05-01
There's a cron job called mythtv-status in /etc/cron.d that runs every ten minutes.  That cron job runs an init script called mythtv-status in /etc/init.d.  The init script updates the /etc/motd file with the latest mythtv status.

It seems a bit convoluted, but it does work.

Try```
$sudo cp ~/.mythtv/config.xml /root/.mythtv/
$sudo /etc/init.d/mythtv-status reload
```
That'll fix the error and update the motd without waiting

---

### Post by uopjohnson on 2008-05-01
Yup found it. finally did an slocate and found it there.
I copied the .mythtv directory over, thanks for the tip.

---

### Post by superm1 on 2008-05-01
So this being said, the only permanent, packaged solution I can think of would be running this as the mythtv daemon user instead, but that still even has it's own set of problems since a config.xml isn't provided for that user either.

Anyone think of other ideas?

---

### Post by uopjohnson on 2008-05-01
Is there a reason that the config.xml can't be copied to /etc/mythtv?  It would cause some problems if things changed, but that could probably be handled by the MCC.

---

### Post by Megatog615 on 2008-06-01
You can do this also:
```
sudo ln -s ~/.mythtv/config.xml /root/.mythtv/config.xml
```

This prevents copying it entirely, and updates with changes to the config if you decide to change the config.

---

### Post by t3chn0b0y on 2008-11-07
> **Megatog615 said:**
> You can do this also:
```
sudo ln -s ~/.mythtv/config.xml /root/.mythtv/config.xml
```

This prevents copying it entirely, and updates with changes to the config if you decide to change the config.


You might also do the same thing with the mythtv user account..
Seems I had the problem and it wouldn't go away with just the root
I had to add the config.xml over to mythtv also..

sudo ln -s ~/.mythtv/config.xml /home/mythtv/.mythtv/config.xml
sudo /etc/init.d/mythtv-status reload

---

### Post by MTDrifter on 2008-12-03
> **t3chn0b0y said:**
> You might also do the same thing with the mythtv user account..
Seems I had the problem and it wouldn't go away with just the root
I had to add the config.xml over to mythtv also..

sudo ln -s ~/.mythtv/config.xml /home/mythtv/.mythtv/config.xml
sudo /etc/init.d/mythtv-status reload


I copied and combined everything from my ~/.mythtv/ to /home/mythtv/.mythtv
I also had to copy ~/.lirc and ~/.lircrc to /home/mythtv/
From there I deleted the before mentioned directories and files and linked to them in my home directory and root directory.

Since I am the only one who uses this computer, it made sense to do this. So far I haven't had any issues with MythTV, plug-ins or my remote.

---

### Post by finlay648 on 2009-02-08
As noted this problems occurs because the cron job runs as root and the root user doesn't have a properly configured /root/.mythtv/config.xml file. An alternative fix to the problem is to add the following to the /etc/default/mythtv-status file:

MYTHCONFDIR=/home/mythtv/.mythtv
export MYTHCONFDIR

Replace the /home/mythtv/.mythtv path with the mythtv user config path on your system.

---

### Post by dannyboy79 on 2009-12-22
none of the solutions on this thread work for me. all my config.xml's are the same within the mythtv users directory, my user's home dir, and root's home dir. i still get 

Schedule Conflicts:
Unable to access MythTV Perl API.  Try with --verbose to find out why

when i run it with --verbose i get this:
One Liners
  Going to process: One Liners
Considering: Status
  Going to process: Status
Can't locate MythTV.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/bin/mythtv-status line 662.
i have read the perl bindings are messed up in .22 mythtv. i am running 0.22.0+fixes22994-0ubuntu0+mythbuntu3

i have tried to look into this, one suggestion was to download the latest Debian package number 0.9.2-3, that didn't do it. i ahve looked for the Mythtv.pm but I can't find it. any suggestions?

---

### Post by crisr on 2010-03-30
@dannyboy79:

sudo apt-get install mythtv-perl

---

