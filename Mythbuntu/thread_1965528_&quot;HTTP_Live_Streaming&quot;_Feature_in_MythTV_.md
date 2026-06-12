---
title: "&quot;HTTP Live Streaming&quot; Feature in MythTV 0.25"
date: 2012-04-25
forum: Mythbuntu
---

### Post by bfrancom on 2012-04-25
Myth 0.25 has many new features including a backend web service called "HTTP Live Streaming," which allows 3rd party frontends (iPad, Android, etc) amongst other things.
See:
[http://code.mythtv.org/trac/changeset/7e1a77063e3f002c118149c91d2e5e86b3bb2c5a/mythtv]("http://code.mythtv.org/trac/changeset/7e1a77063e3f002c118149c91d2e5e86b3bb2c5a/mythtv")

It doesn't seem to be compiled into the Mythbuntu version of Mythtv.  Or did I miss something in the configuration?

(I just upgraded from 0.24 to 0.25)

---

### Post by superm1 on 2012-04-26
It's included, but if you don't already have a "Streaming" storage group, I don't believe it's created in the DB on the upgrade.  There is a directory created for it, but it's not hooked up to the DB.  Go into mythtv-setup and double check your storage groups.

---

### Post by iamlindoro on 2012-04-26
It's included, and everything works by default.  You don't even need to create a Steaming SG.  By default, Myth will create the streams in ~/.mythtv/streaming for the backend users.  You only need to create a streaming SG if you want the stream files to go elsewhere.

I set up a fresh Mythbuntu 12.04 VM and tested it against the forthcoming Torc for iOS iPad/iPhone app and it needed no modifications/additional setup.  Well done.

---

### Post by azmyth on 2012-05-17
I have this working but I have a couple of questions.

1) I can search the file names but my filenames are numbers so I don't have any easy way of correlating the file number to the title of the show thus I don't know what I'm playing. Is there a script to change the file name to a title.

2) The quality is really poor even at the best res and bit rates. I noticed there's a patch but then I'll have to compile. 

[http://www.gossamer-threads.com/lists/mythtv/users/517240](http://www.gossamer-threads.com/lists/mythtv/users/517240)

Anyone else seeing poor quality?

---

### Post by superm1 on 2012-05-17
Just so you know, building packages doesn't have to be a daunting task.  You should be able to use the package build scripts at:

[https://github.com/mythtv/packaging](https://github.com/mythtv/packaging)

Check out the branch you want to build (probably fixes/0.25).

There is a deb directory with both a source package and binary package build script.  You can either build a source package and then put it on a personal PPA (avoiding build dependencies on your system), or a binary package set directly (which will cause a lot of build dependencies to be installed).

The scripts do support building with additional patches (assuming they are properly formatted).

---

