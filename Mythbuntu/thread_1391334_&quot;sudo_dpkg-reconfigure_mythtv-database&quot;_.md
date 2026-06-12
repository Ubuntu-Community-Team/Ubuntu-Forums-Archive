---
title: "&quot;sudo dpkg-reconfigure mythtv-database&quot; fails"
date: 2010-01-26
forum: Mythbuntu
---

### Post by florin on 2010-01-26
Ubuntu 9.04 64 bit, plain version (not Mythbuntu). Installed a while ago, I just want to put mythtv-backend on it today. So I installed the mythbuntu-repos package.

I did "sudo apt-get install mythtv-backend mythweb mythtv-database" and it went well, except this:

```
Setting up mythtv-database (0.22.0+fixes23298-0ubuntu0+mythbuntu2) ...
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database
```

Okay, I did the command manually, only to receive the same error. I changed the MySQL root account to no password (blank password), because /var/cache/debconf/passwords.dat lists a blank password for . Didn't help.

I did "sudo dpkg-reconfigure mysql-server-5.0" and changed the MySQL root password, but that didn't help either.

/etc/mysql/debian.cnf says something about the user "debian-sys-maint", and there's a password noted in that file. I tried to login with the mysql text client using those credentials, and it worked. But I have no idea whether that's the account used by dpkg-reconfigure or not.

I tried to change "debian-sys-maint" to no password, and then dpkg-reconfigure mythtv-database asks me about the host MySQL is running on, the admin user and password (so it's a different behavior), and I tried a few different things for user/pass, but in the end it fails just the same.

If I knew what happens when I do "sudo dpkg-reconfigure mythtv-database" maybe I could just run that stuff manually, instead of relying on these obscure admin commands. :( It's probably something simple, like creating / populating a database and maybe editing some config files.

Any suggestions? I'm stumped.

EDIT: The machine where I'm installing MythTV is headless, no X display. I am working on it over ssh from my laptop which is running Ubuntu 9.10.

---

### Post by florin on 2010-01-26
I tried to do a "sudo mythtv-setup" anyway, but I get this bizarre error (sorry for the image, copy/paste didn't work with plain xterm):

[IMG]http://imgur.com/i4Dzo.png[/IMG]

How can there be a protocol mismatch? I installed the packages from the same source (mythbuntu repos). Maybe this is because I failed to run dpkg-reconfigure?

---

### Post by superm1 on 2010-01-27
> **florin said:**
> Ubuntu 9.04 64 bit, plain version (not Mythbuntu). Installed a while ago, I just want to put mythtv-backend on it today. So I installed the mythbuntu-repos package.

I did "sudo apt-get install mythtv-backend mythweb mythtv-database" and it went well, except this:

```
Setting up mythtv-database (0.22.0+fixes23298-0ubuntu0+mythbuntu2) ...
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database
```

Okay, I did the command manually, only to receive the same error. I changed the MySQL root account to no password (blank password), because /var/cache/debconf/passwords.dat lists a blank password for . Didn't help.

I did "sudo dpkg-reconfigure mysql-server-5.0" and changed the MySQL root password, but that didn't help either.

/etc/mysql/debian.cnf says something about the user "debian-sys-maint", and there's a password noted in that file. I tried to login with the mysql text client using those credentials, and it worked. But I have no idea whether that's the account used by dpkg-reconfigure or not.

I tried to change "debian-sys-maint" to no password, and then dpkg-reconfigure mythtv-database asks me about the host MySQL is running on, the admin user and password (so it's a different behavior), and I tried a few different things for user/pass, but in the end it fails just the same.

If I knew what happens when I do "sudo dpkg-reconfigure mythtv-database" maybe I could just run that stuff manually, instead of relying on these obscure admin commands. :( It's probably something simple, like creating / populating a database and maybe editing some config files.

Any suggestions? I'm stumped.

EDIT: The machine where I'm installing MythTV is headless, no X display. I am working on it over ssh from my laptop which is running Ubuntu 9.10.
If things are working, the message is harmless.  If they aren't however, that's a different story :)

---

### Post by SiHa on 2010-01-27
> **florin said:**
> ... copy/paste didn't work with plain xterm



In xterm, you add a 'shift':

CTRL+SHIFT+C = Copy
CTRL+SHIFT+X = Cut
CTRL+SHIFT+V = Paste

---

### Post by florin on 2010-01-27
> **superm1 said:**
> If things are working, the message is harmless.  If they aren't however, that's a different story :)

Well, uh, mythtv-setup doesn't work either, due to the protocol mismatch. So, no, things are definitely not working.

Meanwhile, I removed all myth-related packages, disabled the Mythbuntu repos, and just pulled the mythtv 0.21 packages from the regular Ubuntu repos. Guess what - I had exactly zero problems with them. Everything went without a hitch.

Now I have a working MythTV 0.21 setup, the backend on the 9.04 server, the frontend on a desktop running an even older Ubuntu version, it detected my HDHomeRun tuner, I can watch TV, record shows, I'm happy.

Not the latest version, but at least this one works. :)

Something is definitely wrong with the 0.22 packages that come with Mythbuntu.

---

### Post by diskmaster23 on 2010-02-01
Did anyone ever figure out what to do about this protocol mismatch?

(Solved) Once I upgraded from .21 to .22, I just had to reboot the machine and the protocol mismatch went away.

---

