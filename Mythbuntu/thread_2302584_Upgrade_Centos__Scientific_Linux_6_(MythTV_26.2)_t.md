---
title: "Upgrade Centos / Scientific Linux 6 (MythTV 26.2) to Mythbuntu 14.04 LTS (MythTV 27)"
date: 2015-11-11
forum: Mythbuntu
---

### Post by wpcprez on 2015-11-11
Hello,
I have a mythtv box that I've been using since 2003 and I've migrated the database and installed centos or scientific linux and I'm familiar with the process to upgrade that route but I've recently tried installing mythbuntu on a secondary box for testing and I love how it's all packaged and bundled together. It just works, as it should. Can someone give me any additional info I may need on what the process would be to upgrade my old centos box to mythbuntu? 

My original plan was to export the mysql database then install mythbuntu fresh and import the database. I believe the frontend or mythtv-setup knows about the schema differences and automatically upgrades the database? 

Any input would be appreciated. Thanks

-Johnny

---

### Post by blm-ubunet on 2015-11-13
Sounds like you have good handle on the process.
Good reading here:-
[https://www.mythtv.org/wiki/Category:Release_Notes](https://www.mythtv.org/wiki/Category:Release_Notes)
[https://www.mythtv.org/wiki/Release_Notes_-_0.27](https://www.mythtv.org/wiki/Release_Notes_-_0.27)

The upgrade from 0.26 - 0.27 seems fairly innocuous.
If you have macroblocking in recording playback seeking then consider rebuilding seektables on your recordings.

Basic Checklist:
dB backup/restore scripts
dB & xmltvids backups.
Qt4.8
UTC & mysql timezone support should already be sorted in your 0.26 install.
Logging options changed
tuner card record/livetv priority changes.

Note that mythbuntu uses wrapper scripts around the mythtv executables & could now be using systemd (was using upstart).

---

### Post by wpcprez on 2015-11-22
thanks, this worked perfectly. Installed fresh. Shut off mysql and mythbackend. Restored database. Just needed to make sure frontends all used that new auto generated password and I was good to go.

---

