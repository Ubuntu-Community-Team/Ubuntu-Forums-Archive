---
title: "Installer crash on flashplugin-installer"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by trasigt on 2011-04-02
I get this error with daily snapshots from 0331 and 0402 and beta 1 image..
Unity installer crashes on flashplugin-installer and says my installer is maybe old and need to be upgraded and then fails to resume

Im running from a USB key and tried both options Try ubuntu and Install ubuntu,.. both gives me same error.

Apr  2 16:53:34 ubuntu ubiquity: Errors were encountered while processing:
Apr  2 16:53:34 ubuntu ubiquity:  flashplugin-installer
Apr  2 16:53:34 ubuntu plugininstall.py: Traceback (most recent call last):
Apr  2 16:53:34 ubuntu plugininstall.py:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 739, in do_install
Apr  2 16:53:34 ubuntu plugininstall.py:     if not cache.commit(fetchprogress, installprogress):
Apr  2 16:53:34 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/deprecation.py", line 98, in deprecated_function
Apr  2 16:53:34 ubuntu plugininstall.py:     return func(*args, **kwds)
Apr  2 16:53:34 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 427, in commit
Apr  2 16:53:34 ubuntu plugininstall.py:     res = self.install_archives(pm, install_progress)
Apr  2 16:53:34 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/deprecation.py", line 98, in deprecated_function
Apr  2 16:53:34 ubuntu plugininstall.py:     return func(*args, **kwds)
Apr  2 16:53:34 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 390, in install_archives
Apr  2 16:53:34 ubuntu plugininstall.py:     res = install_progress.run(pm)
Apr  2 16:53:34 ubuntu plugininstall.py:   File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 381, in run
Apr  2 16:53:34 ubuntu plugininstall.py:     res = pm.do_install(self.write_stream.fileno())
Apr  2 16:53:34 ubuntu plugininstall.py: SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Apr  2 16:53:34 ubuntu plugininstall.py: 
Apr  2 16:53:34 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /sys
Apr  2 16:53:34 ubuntu ubiquity: umount: /proc: device is busy.
Apr  2 16:53:34 ubuntu ubiquity:         (In some cases useful info about processes that use
Apr  2 16:53:34 ubuntu ubiquity:          the device is found by lsof(8) or fuser(1))
Apr  2 16:53:34 ubuntu plugininstall.py: log-output -t ubiquity chroot /target umount /proc
Apr  2 16:53:34 ubuntu plugininstall.py: log-output -t ubiquity umount /target/dev
Apr  2 16:53:35 ubuntu plugininstall.py: broken packages after installation: 
Apr  2 16:53:58 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Apr  2 16:53:58 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /proc /target/proc
Apr  2 16:53:58 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /sys /target/sys
Apr  2 16:53:58 ubuntu plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
Apr  2 16:53:59 ubuntu ubiquity: umount: /target/proc/sys/fs/binfmt_misc: not mounted
Apr  2 16:53:59 ubuntu ubiquity: 
Apr  2 16:53:59 ubuntu ubiquity[3515]: debconffilter_done: ubi-partman (current: ubi-partman)
Apr  2 16:54:03 ubuntu ubiquity[3515]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^keyboard-configuration/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Apr  2 16:54:04 ubuntu ubiquity: WARNING:root:Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
Apr  2 16:54:04 ubuntu ubiquity[3515]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Apr  2 16:54:04 ubuntu ubiquity: WARNING:root:modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
Apr  2 16:54:04 ubuntu ubiquity: 
Apr  2 16:54:04 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
Apr  2 16:54:04 ubuntu ubiquity: 
Apr  2 16:54:04 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
Apr  2 16:54:04 ubuntu ubiquity: 
Apr  2 16:54:04 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
Apr  2 16:54:04 ubuntu ubiquity: 
Apr  2 16:54:04 ubuntu ubiquity: WARNING:root:modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
Apr  2 16:54:04 ubuntu ubiquity: 
Apr  2 16:54:04 ubuntu ubiquity: WARNING:root:modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
Apr  2 16:54:04 ubuntu ubiquity: 
Apr  2 16:54:05 ubuntu ubiquity: WARNING:root:modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
Apr  2 16:54:05 ubuntu ubiquity: 
Apr  2 16:54:05 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
Apr  2 16:54:05 ubuntu ubiquity: 
Apr  2 16:54:05 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
Apr  2 16:54:05 ubuntu ubiquity: 
Apr  2 16:54:05 ubuntu ubiquity: WARNING:root:modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
Apr  2 16:54:05 ubuntu ubiquity: 
Apr  2 16:54:05 ubuntu ubiquity: WARNING:root:modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
Apr  2 16:54:05 ubuntu ubiquity: 
Apr  2 16:54:05 ubuntu ubiquity: WARNING:root:modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
Apr  2 16:54:05 ubuntu ubiquity: 
Apr  2 16:54:05 ubuntu ubiquity: There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.
Apr  2 16:54:05 ubuntu plugininstall.py: log-output -t ubiquity umount -f /target/proc
Apr  2 16:54:05 ubuntu ubiquity: umount2: Invalid argument
Apr  2 16:54:05 ubuntu ubiquity: umount: /target/sys: not mounted
Apr  2 16:54:05 ubuntu ubiquity: 
Apr  2 16:54:05 ubuntu plugininstall.py: log-output -t ubiquity umount -f /target/sys
Apr  2 16:54:05 ubuntu plugininstall.py: log-output -t ubiquity umount -f /target/dev
Apr  2 16:54:05 ubuntu ubiquity[3515]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^oem-config/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Apr  2 16:54:05 ubuntu ubiquity[3515]: log-output -t ubiquity umount /target/proc/sys/fs/binfmt_misc
Apr  2 16:54:05 ubuntu ubiquity[3515]: log-output -t ubiquity umount /target/proc
Apr  2 16:54:05 ubuntu ubiquity[3515]: log-output -t ubiquity umount /target/home
Apr  2 16:54:05 ubuntu ubiquity[3515]: log-output -t ubiquity umount /target/cdrom
Apr  2 16:54:07 ubuntu ubiquity[3515]: log-output -t ubiquity umount /target
Apr  2 16:54:07 ubuntu ubiquity: umount: /target/cdrom: not found
Apr  2 16:54:07 ubuntu ubiquity: 
Apr  2 16:54:07 ubuntu plugininstall.py: log-output -t ubiquity umount /target/cdrom
Apr  2 16:54:07 ubuntu ubiquity: grep: /target/etc/apt/sources.list
Apr  2 16:54:07 ubuntu ubiquity: : No such file or directory
Apr  2 16:54:07 ubuntu plugininstall.py: Exception during installation:
Apr  2 16:54:07 ubuntu plugininstall.py: Traceback (most recent call last):
Apr  2 16:54:07 ubuntu plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 1525, in <module>
Apr  2 16:54:07 ubuntu plugininstall.py:     install.run()
Apr  2 16:54:07 ubuntu plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 55, in wrapper
Apr  2 16:54:07 ubuntu plugininstall.py:     func(self)
Apr  2 16:54:07 ubuntu plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 192, in run
Apr  2 16:54:07 ubuntu plugininstall.py:     self.install_extras()
Apr  2 16:54:07 ubuntu plugininstall.py:   File "/usr/share/ubiquity/plugininstall.py", line 1090, in install_extras
Apr  2 16:54:07 ubuntu plugininstall.py:     if self.db.get('oem-config/enable') == 'true':
Apr  2 16:54:07 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/debconf.py", line 65, in <lambda>
Apr  2 16:54:07 ubuntu plugininstall.py:     lambda *args, **kw: self.command(command, *args, **kw))
Apr  2 16:54:07 ubuntu plugininstall.py:   File "/usr/lib/python2.7/dist-packages/debconf.py", line 86, in command
Apr  2 16:54:07 ubuntu plugininstall.py:     status = int(status)
Apr  2 16:54:07 ubuntu plugininstall.py: ValueError: invalid literal for int() with base 10: ''
Apr  2 16:54:07 ubuntu plugininstall.py:

---

### Post by 5149.5 on 2011-04-02
Try[ flashaid]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/").

---

### Post by teachop on 2011-04-02
I got a similar error on my first two attempts to install from live CD as well.  For me the key was to not check the boxes that download updates and install 3rd party software.  Then it worked, and I installed the updates etc later.

---

### Post by einheitlix on 2011-04-08
Yes, I got the same error when trying to install Ubuntu 11.04 beta1 64-bit.

No need to uncheck the "Download updates while installing" box, I only unchecked the "Install third party software" box. The problem is the flashplugin-installer as mentioned above. You can install it after Ubuntu installation is complete. When I wanted to do this, I first got another error message from Synaptic as it tried to install flashplugin-installer, but then it automatically installed some back-up ".orig" package instead and now Flash works flawlessly here.

---

