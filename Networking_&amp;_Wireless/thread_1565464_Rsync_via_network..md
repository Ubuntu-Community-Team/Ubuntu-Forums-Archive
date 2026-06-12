---
title: "Rsync via network."
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-08-31
I've used rsync extensively, but only with local drives. My parents computer used to run Windows and used Syncback SE to auto-sync their data to an Ubuntu box in the house with samba running as a means of backing up the data. They have since began using Ubuntu full time, so I need to find a way to rsync their data within Ubuntu to the backup box. Same deal as before, it's just their client OS is now Ubuntu instead of Windows.

Any thoughts? Are there any GUI apps to do this? I'd like to learn how to do it via GUI and terminal if possible... just for my sake of learning.

---

### Post by BkkBonanza on 2010-09-01
I can't speak for gui apps but using rsync from the terminal is easy.

It works the same across a netowrk as for local drives except you prefix the network user and hostname. eg.

rsync /path/to/src/files user@other-machine-or-ip:/path/to/dest

All the same options can be used for compress, perms etc. 

It also works across the internet and it will use ssh to secure the data during transit.

---

### Post by Roasted on 2010-09-01
> **BkkBonaza said:**
> I can't speak for gui apps but using rsync from the terminal is easy.

It works the same across a netowrk as for local drives except you prefix the network user and hostname. eg.

rsync /path/to/src/files user@other-machine-or-ip:/path/to/dest

All the same options can be used for compress, perms etc. 

It also works across the internet and it will use ssh to secure the data during transit.

What about authentication to the share on the destination machine? Do I just have to connect and hit "remember password forever" so it auto-connects each time? The key is, the destination share won't already be mounted via network. I want to make sure I can do this pretty flawlessly...

---

### Post by BkkBonanza on 2010-09-01
Ideally for this you would use key authentication not passwords.

As far as mounting the share you would have to ssh in to mount it. That also would use key auth and need only be a single command depending on how you mount. In the end you would likely have a short script if you want it to work reliably.

eg. 

ssh user@machine smbmount share /mnt
rsync localfiles user@machine:/mnt
ssh user@machine umount /mnt

With key auth no prompts would occur for this. Key auth is easy to setup and much more secure than passwords. See **man ssh-copy-id**.

---

### Post by Roasted on 2010-09-01
Hate to sound like a weenie, but this is *exactly* what I was afraid of. With Windows doing this, I log in to server, check remember password, and add the paths to dest/src to sync the data. Bingo bango. Done. 

With my parents moving to Linux I was hoping I wouldn't have to set up any scripts beyond the basic rsync bash script I already have (and tweaking it of course to cross the network).

Would the saving password thing work? Or no? If it will, that's what I'll use.

---

### Post by BkkBonanza on 2010-09-01
Saving a password won't work for ssh. Using keys is easier and better anyway.

If you have a script that is working now then simply copying the key file will allow it to continue working without any password mods, by just tweaking the paths, and making sure the correct users/systems are there.

If scripting is not what you wanted then don't use the command line rsync tool. Use a gui backup tool. There are many - but I'm not the one to ask about those.

Windows is also Bingo Bango, hacked.

---

### Post by Roasted on 2010-09-08
I looked into two different utilities, and I'm hoping somebody can chime in here with my concerns about them.

Back In Time - can you back up over the network? When I tried to fire it up all I could find were local paths - I had no network options.

Simple Backup Tool from the Software Center - Seems to authenticate through SSH just fine. Awesome. Problem is it does zipped backups, like it zips up all of the files into a package and saves it as a date stamp. That's all well and good, but I'd also like the option to save the data as just raw format, just like it does when you use rsync without compression. If there's 10 folders 30 files in the source, I want that in its entirety in the destination as well.

Any input?

---

### Post by BkkBonanza on 2010-09-08
Maybe have a look at pyBackPack. I saw an article about it that indicated it supports remote backup using ssh. It's a GUI app and has backup file sets and restore from the sets by timestamp. It's in the repos apparently (I haven't used it). I don't know if it tars the files or not.

---

### Post by Roasted on 2010-09-12
It looks like gadmin-rsync does what I need it to. I can get it to successfully work, however I can't get the scheduler working. I get this error when I set the scheduler and hit "save":

Error: The time schedule server "cron(d)" does not seem to be running.

Anybody have any ideas?

---

### Post by BkkBonanza on 2010-09-13
Usually cron would be installed and running by default. It's very strange if it's not and could only happen if at some point it was removed/disabled.

Just check in synaptic that the "cron" package is installed. And if not then install.
If installed then somehow it must have been stopped. So at the command line,

**sudo service cron start**

---

### Post by Roasted on 2010-09-13
It certainly should be running, because I'm testing this on my desktop, which already has an rsync script I set up to run via cron every 12 hours.

I'm not at this machine now, but I'll check it later. Though I'm pretty positive it's running fine...

---

