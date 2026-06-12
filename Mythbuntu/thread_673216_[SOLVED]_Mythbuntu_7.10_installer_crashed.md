---
title: "[SOLVED] Mythbuntu 7.10 installer crashed"
date: 2008-01-20
forum: Mythbuntu
---

### Post by aussiedude on 2008-01-20
Hi

I am having trouble getting Mythbuntu installed.
I have read the other threads that discuss a similar error but none of them have any specific details about how they overcame the problem.

> Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
    install.run()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
    self.configure_mythbuntu()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
    raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
InstallStepError: MythbuntuApply Debconf Xfer failed with code 1


This happens about 85% of the way through the install.
I have tried advanced also, it gets further but crashes while setting up the remote (windows media center) about 95% into the install. I tried the advanced again, without setting up the remote and it failed at 85% too.

Any help would be appreciated.
Thanks in advance.

---

### Post by superm1 on 2008-01-20
Most common cause is a password using invalid characters for MySQL or mythweb.  Try avoiding non alpha-numeric (including spaces) characters.

If that wasn't it, then post all the options you chose during install.

---

### Post by aussiedude on 2008-01-20
My password for mysql contained only alpha-numeric characters.

I have tried de-selecting all options including all the modules and themes, with the exception of SSH and SMB and it still crashes.

---

### Post by aussiedude on 2008-01-20
Here is my syslog for my latest attempt;
> Jan 20 13:43:25 ubuntu ubiquity[27420]: Ubiquity 1.6.8+mythbuntu4
Jan 20 13:43:27 ubuntu ubiquity[27420]: log-output -t ubiquity umount /target/home
Jan 20 13:43:27 ubuntu ubiquity[27420]: log-output -t ubiquity umount /target
Jan 20 13:43:32 ubuntu ubiquity[27420]: log-output -t ubiquity laptop-detect
Jan 20 13:43:38 ubuntu ubiquity[27420]: switched to page stepLanguage
Jan 20 13:43:39 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Jan 20 13:43:39 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
Jan 20 13:43:39 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
Jan 20 13:43:39 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jan 20 13:43:39 ubuntu ubiquity[27420]: switched to page stepLanguage
Jan 20 13:43:42 ubuntu localechooser: info: LANGNAME=English
Jan 20 13:43:42 ubuntu localechooser: info: line=English;0;en;US;en_US.UTF-8;UTF-8;;kbd=lat0-sun16(utf8)
Jan 20 13:43:42 ubuntu localechooser: info: Set debian-installer/language = 'en'
Jan 20 13:43:42 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jan 20 13:43:42 ubuntu localechooser: info: Set debian-installer/fallbacklocale = 'en_US.UTF-8'
Jan 20 13:43:42 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jan 20 13:43:42 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'kbd=lat0-sun16(utf8)'
Jan 20 13:43:42 ubuntu localechooser: info: Set debconf/language = 'en'
Jan 20 13:43:42 ubuntu localechooser: info: Set countrychooser/country-name = 'United States'
Jan 20 13:43:42 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jan 20 13:43:42 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jan 20 13:43:42 ubuntu ubiquity[27420]: debconffilter_done: Language (current: Language)
Jan 20 13:43:42 ubuntu ubiquity[27420]: Step_before = stepLanguage
Jan 20 13:43:44 ubuntu ubiquity[27420]: switched to page stepLocation
Jan 20 13:43:51 ubuntu localechooser: info: Locale has been preseeded to en_US.UTF-8
Jan 20 13:43:51 ubuntu localechooser: info: Set languagechooser/language-name = 'English'
Jan 20 13:43:51 ubuntu localechooser: info: Set countrychooser/shortlist-en = 'US'
Jan 20 13:43:51 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jan 20 13:43:51 ubuntu localechooser: info: Set debconf/language = ''
Jan 20 13:43:51 ubuntu localechooser: info: Set countrychooser/country-name = 'United States'
Jan 20 13:43:51 ubuntu localechooser: info: Set debian-installer/country = 'US'
Jan 20 13:43:51 ubuntu localechooser: info: Set debian-installer/locale = 'en_US.UTF-8'
Jan 20 13:43:51 ubuntu ubiquity[27420]: debconffilter_done: Timezone (current: Timezone)
Jan 20 13:43:51 ubuntu ubiquity[27420]: Step_before = stepLocation
Jan 20 13:43:53 ubuntu ubiquity[27420]: log-output -t ubiquity setxkbmap -model pc105 -layout us
Jan 20 13:43:53 ubuntu ubiquity[27420]: switched to page stepKeyboardConf
Jan 20 13:43:57 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Jan 20 13:43:57 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Jan 20 13:43:57 ubuntu ubiquity[27420]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Jan 20 13:43:57 ubuntu ubiquity[27420]: debconffilter_done: ConsoleSetup (current: ConsoleSetup)
Jan 20 13:43:57 ubuntu ubiquity[27420]: Step_before = stepKeyboardConf
Jan 20 13:43:58 ubuntu kernel: [ 6543.890326] cdrom: sr0: mrw address space DMA selected
Jan 20 13:43:58 ubuntu kernel: [ 6543.915275] program parted_devices is using a deprecated SCSI ioctl, please convert it to SG_IO
Jan 20 13:44:01 ubuntu ubiquity[27420]: switched to page stepPartAuto
Jan 20 13:44:08 ubuntu ubiquity[27420]: switched to page stepPartAdvanced
Jan 20 13:44:29 ubuntu last message repeated 3 times
Jan 20 13:44:37 ubuntu ubiquity[27420]: debconffilter_done: Partman (current: Partman)
Jan 20 13:44:37 ubuntu ubiquity[27420]: Step_before = stepPartAdvanced
Jan 20 13:44:38 ubuntu ubiquity[27420]: switched to page stepUserInfo
Jan 20 13:44:58 ubuntu ubiquity[27420]: debconffilter_done: UserSetup (current: UserSetup)
Jan 20 13:44:58 ubuntu ubiquity[27420]: Step_before = stepUserInfo
Jan 20 13:44:59 ubuntu ubiquity[27420]: switched to page mythbuntu_stepInstallType
Jan 20 13:45:02 ubuntu ubiquity[27420]: debconffilter_done: MythbuntuAdvancedType (current: MythbuntuAdvancedType)
Jan 20 13:45:02 ubuntu ubiquity[27420]: Step_before = mythbuntu_stepInstallType
Jan 20 13:45:03 ubuntu ubiquity[27420]: switched to page mythbuntu_stepCustomInstallType
Jan 20 13:45:16 ubuntu ubiquity[27420]: debconffilter_done: MythbuntuInstallType (current: MythbuntuInstallType)
Jan 20 13:45:16 ubuntu ubiquity[27420]: Step_before = mythbuntu_stepCustomInstallType
Jan 20 13:45:16 ubuntu ubiquity[27420]: switched to page mythbuntu_stepPlugins
Jan 20 13:45:26 ubuntu ubiquity[27420]: debconffilter_done: MythbuntuPlugins (current: MythbuntuPlugins)
Jan 20 13:45:26 ubuntu ubiquity[27420]: Step_before = mythbuntu_stepPlugins
Jan 20 13:45:26 ubuntu ubiquity[27420]: switched to page mythbuntu_stepThemes
Jan 20 13:45:27 ubuntu ubiquity[27420]: debconffilter_done: MythbuntuThemes (current: MythbuntuThemes)
Jan 20 13:45:27 ubuntu ubiquity[27420]: Step_before = mythbuntu_stepThemes
Jan 20 13:45:28 ubuntu ubiquity[27420]: switched to page mythbuntu_stepServices
Jan 20 13:45:53 ubuntu ubiquity[27420]: debconffilter_done: MythbuntuServices (current: MythbuntuServices)
Jan 20 13:45:53 ubuntu ubiquity[27420]: Step_before = mythbuntu_stepServices
Jan 20 13:45:54 ubuntu ubiquity[27420]: switched to page mythbuntu_stepPasswords
Jan 20 13:46:33 ubuntu ubiquity[27420]: debconffilter_done: MythbuntuPasswords (current: MythbuntuPasswords)
Jan 20 13:46:33 ubuntu ubiquity[27420]: Step_before = mythbuntu_stepPasswords
Jan 20 13:46:34 ubuntu ubiquity[27420]: switched to page mythbuntu_stepLirc
Jan 20 13:46:43 ubuntu ubiquity[27420]: debconffilter_done: MythbuntuRemote (current: MythbuntuRemote)
Jan 20 13:46:43 ubuntu ubiquity[27420]: Step_before = mythbuntu_stepLirc
Jan 20 13:46:44 ubuntu ubiquity[27420]: switched to page mythbuntu_stepDrivers
Jan 20 13:46:49 ubuntu ubiquity[27420]: debconffilter_done: MythbuntuDrivers (current: MythbuntuDrivers)
Jan 20 13:46:49 ubuntu ubiquity[27420]: Step_before = mythbuntu_stepDrivers
Jan 20 13:46:50 ubuntu ubiquity[27420]: switched to page stepReady
Jan 20 13:46:51 ubuntu ubiquity[27420]: debconffilter_done: Summary (current: Summary)
Jan 20 13:46:51 ubuntu ubiquity[27420]: Step_before = stepReady
Jan 20 13:46:51 ubuntu ubiquity[27420]: progress_loop()
Jan 20 13:46:59 ubuntu kernel: [ 6724.371909] intel_rng: FWH not detected
Jan 20 13:47:00 ubuntu kernel: [ 6725.645304] Adding 1461872k swap on /dev/sda5.  Priority:-7 extents:1 across:1461872k
Jan 20 13:47:01 ubuntu partman: mke2fs 1.40.2 (12-Jul-2007)
Jan 20 13:47:06 ubuntu kernel: [ 6731.326742] kjournald starting.  Commit interval 5 seconds
Jan 20 13:47:06 ubuntu kernel: [ 6731.333278] EXT3 FS on sda1, internal journal
Jan 20 13:47:06 ubuntu kernel: [ 6731.333288] EXT3-fs: mounted filesystem with ordered data mode.
Jan 20 13:47:06 ubuntu kernel: [ 6731.428315] XFS mounting filesystem sda6
Jan 20 13:47:06 ubuntu kernel: [ 6731.562272] Ending clean XFS mount for filesystem: sda6
Jan 20 13:47:08 ubuntu ubiquity[27420]: debconffilter_done: PartmanCommit (current: None)
Jan 20 13:47:09 ubuntu ubiquity: /usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
Jan 20 13:47:09 ubuntu ubiquity:   warnings.warn("apt API not stable yet", FutureWarning)
Jan 20 13:50:03 ubuntu localechooser: Generating locales...
Jan 20 13:50:03 ubuntu localechooser:   en_US.UTF-8... 
Jan 20 13:50:05 ubuntu localechooser: done
Jan 20 13:50:05 ubuntu localechooser: Generation complete.
Jan 20 13:50:05 ubuntu localechooser: Generating locales...
Jan 20 13:50:05 ubuntu localechooser:   en_US.UTF-8... 
Jan 20 13:50:05 ubuntu localechooser: up-to-date
Jan 20 13:50:05 ubuntu localechooser: Generation complete.
Jan 20 13:50:06 ubuntu python: log-output -t ubiquity chroot /target fontconfig-voodoo --auto --quiet
Jan 20 13:50:07 ubuntu user-setup: Shadow passwords are now on.
Jan 20 13:50:08 ubuntu user-setup: Adding user `graham' ...
Jan 20 13:50:08 ubuntu user-setup: Adding new group `graham' (1000) ...
Jan 20 13:50:08 ubuntu user-setup: Adding new user `graham' (1000) with group `graham' ...
Jan 20 13:50:08 ubuntu user-setup: The home directory `/home/graham' already exists.  Not copying from `/etc/skel'.
Jan 20 13:50:08 ubuntu user-setup: Adding group `lpadmin' (GID 117) ...
Jan 20 13:50:08 ubuntu user-setup: Done.
Jan 20 13:50:08 ubuntu user-setup: addgroup: 
Jan 20 13:50:08 ubuntu user-setup: The group `scanner' already exists as a system group. Exiting.
Jan 20 13:50:08 ubuntu user-setup: Adding user `graham' to group `adm' ...
Jan 20 13:50:08 ubuntu user-setup: Done.
Jan 20 13:50:08 ubuntu user-setup: Adding user `graham' to group `audio' ...
Jan 20 13:50:08 ubuntu user-setup: Done.
Jan 20 13:50:08 ubuntu user-setup: Adding user `graham' to group `cdrom' ...
Jan 20 13:50:08 ubuntu user-setup: Done.
Jan 20 13:50:08 ubuntu user-setup: Adding user `graham' to group `dialout' ...
Jan 20 13:50:08 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: Adding user `graham' to group `floppy' ...
Jan 20 13:50:09 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: Adding user `graham' to group `video' ...
Jan 20 13:50:09 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: Adding user `graham' to group `plugdev' ...
Jan 20 13:50:09 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: Adding user `graham' to group `dip' ...
Jan 20 13:50:09 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: adduser: The group `netdev' does not exist.
Jan 20 13:50:09 ubuntu user-setup: Adding user `graham' to group `powerdev' ...
Jan 20 13:50:09 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: Adding user `graham' to group `lpadmin' ...
Jan 20 13:50:09 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: Adding user `graham' to group `scanner' ...
Jan 20 13:50:09 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: addgroup: 
Jan 20 13:50:09 ubuntu user-setup: The group `admin' already exists as a system group. Exiting.
Jan 20 13:50:09 ubuntu user-setup: Adding user `graham' to group `admin' ...
Jan 20 13:50:09 ubuntu user-setup: Done.
Jan 20 13:50:09 ubuntu user-setup: Using `/usr/share/libgksu/debian/gconf-defaults.libgksu-sudo' to provide `libgksu-gconf-defaults'.
Jan 20 13:50:12 ubuntu ubiquity: /usr/bin/casper-reconfigure: package 'gnome-power-manager' is not installed
Jan 20 13:50:12 ubuntu ubiquity: umount: /target/cdrom: not mounted
Jan 20 13:50:12 ubuntu python: log-output -t ubiquity umount /target/cdrom
Jan 20 13:50:12 ubuntu python: log-output -t ubiquity mount --bind /cdrom /target/cdrom
Jan 20 13:50:12 ubuntu mythbuntu: Adding user `graham' to group `mythtv' ...
Jan 20 13:50:12 ubuntu mythbuntu: Done.
Jan 20 13:50:12 ubuntu mythbuntu:  Adding system startup for /etc/init.d/ntp ...
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc0.d/K20ntp -> ../init.d/ntp
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc1.d/K20ntp -> ../init.d/ntp
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc6.d/K20ntp -> ../init.d/ntp
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc2.d/S20ntp -> ../init.d/ntp
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc3.d/S20ntp -> ../init.d/ntp
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc4.d/S20ntp -> ../init.d/ntp
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc5.d/S20ntp -> ../init.d/ntp
Jan 20 13:50:12 ubuntu mythbuntu:  Adding system startup for /etc/init.d/mysql ...
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc0.d/K20mysql -> ../init.d/mysql
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc1.d/K20mysql -> ../init.d/mysql
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc6.d/K20mysql -> ../init.d/mysql
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc2.d/S20mysql -> ../init.d/mysql
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc3.d/S20mysql -> ../init.d/mysql
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc4.d/S20mysql -> ../init.d/mysql
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc5.d/S20mysql -> ../init.d/mysql
Jan 20 13:50:12 ubuntu mythbuntu:  Adding system startup for /etc/init.d/samba ...
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc0.d/K20samba -> ../init.d/samba
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc1.d/K20samba -> ../init.d/samba
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc6.d/K20samba -> ../init.d/samba
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc2.d/S20samba -> ../init.d/samba
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc3.d/S20samba -> ../init.d/samba
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc4.d/S20samba -> ../init.d/samba
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc5.d/S20samba -> ../init.d/samba
Jan 20 13:50:12 ubuntu mythbuntu:  Adding system startup for /etc/init.d/apache2 ...
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc0.d/K20apache2 -> ../init.d/apache2
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc1.d/K20apache2 -> ../init.d/apache2
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc6.d/K20apache2 -> ../init.d/apache2
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc2.d/S20apache2 -> ../init.d/apache2
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc3.d/S20apache2 -> ../init.d/apache2
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc4.d/S20apache2 -> ../init.d/apache2
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc5.d/S20apache2 -> ../init.d/apache2
Jan 20 13:50:12 ubuntu mythbuntu:  Adding system startup for /etc/init.d/mythtv-backend ...
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc0.d/K20mythtv-backend -> ../init.d/mythtv-backend
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc1.d/K20mythtv-backend -> ../init.d/mythtv-backend
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc6.d/K20mythtv-backend -> ../init.d/mythtv-backend
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc2.d/S20mythtv-backend -> ../init.d/mythtv-backend
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc3.d/S20mythtv-backend -> ../init.d/mythtv-backend
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc4.d/S20mythtv-backend -> ../init.d/mythtv-backend
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc5.d/S20mythtv-backend -> ../init.d/mythtv-backend
Jan 20 13:50:12 ubuntu mythbuntu:  Adding system startup for /etc/init.d/ssh ...
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc0.d/K20ssh -> ../init.d/ssh
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc1.d/K20ssh -> ../init.d/ssh
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc6.d/K20ssh -> ../init.d/ssh
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc2.d/S20ssh -> ../init.d/ssh
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc3.d/S20ssh -> ../init.d/ssh
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc4.d/S20ssh -> ../init.d/ssh
Jan 20 13:50:12 ubuntu mythbuntu:    /etc/rc5.d/S20ssh -> ../init.d/ssh
Jan 20 13:50:13 ubuntu mythbuntu: df: Warning: cannot read table of mounted file systems: No such file or directory
Jan 20 13:50:13 ubuntu mythbuntu:  * Starting MySQL database server mysqld
Jan 20 13:50:15 ubuntu mythbuntu:    ...done.
Jan 20 13:50:15 ubuntu mythbuntu:  * Checking for corrupt, not cleanly closed and upgrade needing tables.
Jan 20 13:50:16 ubuntu mythbuntu:  * Stopping MySQL database server mysqld
Jan 20 13:50:19 ubuntu mythbuntu:    ...done.
Jan 20 13:50:20 ubuntu mythbuntu: Module auth_digest installed; run /etc/init.d/apache2 force-reload to enable.
Jan 20 13:50:21 ubuntu ubiquity: ln: creating symbolic link `/target/home/graham/.config/autostart/mythtv.desktop' to `/usr/share/applications/mythtv.desktop'
Jan 20 13:50:21 ubuntu ubiquity: : File exists
Jan 20 13:50:21 ubuntu python: log-output -t ubiquity umount /target/cdrom
Jan 20 13:50:21 ubuntu python: Exception during installation:
Jan 20 13:50:21 ubuntu python: Traceback (most recent call last):
Jan 20 13:50:21 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
Jan 20 13:50:21 ubuntu python:     install.run()
Jan 20 13:50:21 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
Jan 20 13:50:21 ubuntu python:     self.configure_mythbuntu()
Jan 20 13:50:21 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
Jan 20 13:50:21 ubuntu python:     raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
Jan 20 13:50:21 ubuntu python: InstallStepError: MythbuntuApply Debconf Xfer failed with code 1
Jan 20 13:50:21 ubuntu python: 
Jan 20 13:50:21 ubuntu ubiquity[27420]: debconffilter_done: Install (current: None)
Jan 20 13:50:21 ubuntu ubiquity[27420]: Exception in GTK frontend (invoking crash handler):
Jan 20 13:50:21 ubuntu ubiquity[27420]: Traceback (most recent call last):
Jan 20 13:50:21 ubuntu ubiquity[27420]:   File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
Jan 20 13:50:21 ubuntu ubiquity[27420]:     main()
Jan 20 13:50:21 ubuntu ubiquity[27420]:   File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
Jan 20 13:50:21 ubuntu ubiquity[27420]:     install(args[0])
Jan 20 13:50:21 ubuntu ubiquity[27420]:   File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
Jan 20 13:50:21 ubuntu ubiquity[27420]:     ret = wizard.run()
Jan 20 13:50:21 ubuntu ubiquity[27420]:   File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
Jan 20 13:50:21 ubuntu ubiquity[27420]:     self.progress_loop()
Jan 20 13:50:21 ubuntu ubiquity[27420]:   File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
Jan 20 13:50:21 ubuntu ubiquity[27420]:     (ret, realtb))
Jan 20 13:50:21 ubuntu ubiquity[27420]: RuntimeError: Install failed with exit code 1
Jan 20 13:50:21 ubuntu ubiquity[27420]: Traceback (most recent call last):
Jan 20 13:50:21 ubuntu ubiquity[27420]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
Jan 20 13:50:21 ubuntu ubiquity[27420]:     install.run()
Jan 20 13:50:21 ubuntu ubiquity[27420]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 100, in run
Jan 20 13:50:21 ubuntu ubiquity[27420]:     self.configure_mythbuntu()
Jan 20 13:50:21 ubuntu ubiquity[27420]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 179, in configure_mythbuntu
Jan 20 13:50:21 ubuntu ubiquity[27420]:     raise InstallStepError("MythbuntuApply Debconf Xfer failed with code %d" % ret)
Jan 20 13:50:21 ubuntu ubiquity[27420]: InstallStepError: MythbuntuApply Debconf Xfer failed with code 1
Jan 20 13:50:21 ubuntu ubiquity[27420]: 
Jan 20 13:50:21 ubuntu last message repeated 2 times


I should note I am using the XFS filesystem for my home partition. I mentioned this as I noted this warning;
Jan 20 13:50:13 ubuntu mythbuntu: df: Warning: cannot read table of mounted file systems: No such file or directory
Not sure if that is significant or not.

---

### Post by superm1 on 2008-01-20
Looks like the home partition was not wiped out before hand.  Remove ~/.config and ~/.mythtv in that partition before starting.  Also, please file a bug regarding this so that those files can be checked for in the future.

---

### Post by aussiedude on 2008-01-21
> **superm1 said:**
> Looks like the home partition was not wiped out before hand.  Remove ~/.config and ~/.mythtv in that partition before starting.  Also, please file a bug regarding this so that those files can be checked for in the future.
Removed offending directories, install got past the 83% but crashed again setting up my remote.
Error details:
> Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 212, in <module>
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 207, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 65, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 252, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 330, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/mythbuntu_install.py", line 288, in <module>
    install.run()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 144, in run
    self.configure_remote()
  File "/usr/share/ubiquity/mythbuntu_install.py", line 229, in configure_remote
    raise InstallStepError("Remote Control Configuration failed with code %d" % ret)
InstallStepError: Remote Control Configuration failed with code 1




I notice in my syslog the following lines;
> Jan 21 01:39:53 ubuntu ubiquity: cp: cannot create regular file `/target/home/graham/.lircrc'
Jan 21 01:39:53 ubuntu ubiquity: : No such file or directory

Going to remove the offending file and the above-mentioned directories and try again.

Thanks for your help.

---

### Post by aussiedude on 2008-01-21
Removing the config files worked. Mythbuntu is now up and running.

---

