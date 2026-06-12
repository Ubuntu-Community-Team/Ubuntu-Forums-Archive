---
title: "Errors installing mytbuntu-desktop package (16.04 LXC container)"
date: 2016-05-01
forum: Mythbuntu
---

### Post by mattlach on 2016-05-01
Hey all,

Since I run my mythbuntu backend in an LXC container managed by logging on using X2Go, I can't use the ISO to install mythbuntu, but rather have to start from the basic LXC template version of 16.04 (much like a base server install) and then install mythbuntu-desktop from there.

I've been running 0.27 in a 14.04LTS LXC container for a while this way now, and it works quite well.

Today I decided to start up a test container with 16.04LTS and 0.28 to see how it would work, but ran into problems during the install of packages as follows:

```
...
aspell-autobuildhash: processing: en [en-variant_0].
aspell-autobuildhash: processing: en [en-variant_1].
aspell-autobuildhash: processing: en [en-variant_2].
aspell-autobuildhash: processing: en [en-w_accents-only].
aspell-autobuildhash: processing: en [en-wo_accents-only].
aspell-autobuildhash: processing: en [en_CA-variant_0].
aspell-autobuildhash: processing: en [en_CA-variant_1].
aspell-autobuildhash: processing: en [en_CA-w_accents-only].
aspell-autobuildhash: processing: en [en_CA-wo_accents-only].
aspell-autobuildhash: processing: en [en_GB-ise-w_accents-only].
aspell-autobuildhash: processing: en [en_GB-ise-wo_accents-only].
aspell-autobuildhash: processing: en [en_GB-ize-w_accents-only].
aspell-autobuildhash: processing: en [en_GB-ize-wo_accents-only].
aspell-autobuildhash: processing: en [en_GB-variant_0].
aspell-autobuildhash: processing: en [en_GB-variant_1].
aspell-autobuildhash: processing: en [en_US-w_accents-only].
aspell-autobuildhash: processing: en [en_US-wo_accents-only].
Processing triggers for libapache2-mod-php7.0 (7.0.4-7ubuntu2) ...
Errors were encountered while processing:
 avahi-daemon
 avahi-utils
 libnss-mdns:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
myth@new-myth-test:~$
```

I wanted to post more detailed logs, but the two files in /var/log/apt/  (history.log and term.log) have no more detail than the console output above.

Rerunning the install shows 3 partially installed packages to be installed, and provides more detail as follows:

```
$ sudo apt-get install mythbuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mythbuntu-desktop is already the newest version (0.88).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up avahi-daemon (0.6.32~rc+dfsg-1ubuntu2) ...
Failed to add /run/systemd/ask-password to directory watch: No space left on device
Failed to add /run/systemd/ask-password to directory watch: No space left on device
Job for avahi-daemon.service failed because the control process exited with error code. See "systemctl status avahi-daemon.service" and "journalctl -xe" for details.
invoke-rc.d: initscript avahi-daemon, action "start" failed.
dpkg: error processing package avahi-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of avahi-utils:
 avahi-utils depends on avahi-daemon; however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package avahi-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnss-mdns:amd64:
 libnss-mdns:amd64 depends on avahi-daemon (>= 0.6.16-1); however:
  Package avahi-daemon is not configured yet.

dpkg: error processing package libnss-mdns:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 avahi-daemon
 avahi-utils
 libnss-mdns:amd64
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So, it errors out with a "no space left on device" when trying to set up some type of directory watch...

The thing is, none of the devices are full, I'm not sure where it is trying to write and failing:

```
$ df -h
Filesystem               Size  Used Avail Use% Mounted on
rpool/subvol-999-disk-1   16G  2.4G   14G  15% /
none                     100K     0  100K   0% /dev
cgroup                    12K     0   12K   0% /sys/fs/cgroup
tmpfs                     95G     0   95G   0% /sys/fs/cgroup/cgmanager
tmpfs                     95G     0   95G   0% /dev/shm
tmpfs                     95G  8.5M   95G   1% /run
tmpfs                    5.0M     0  5.0M   0% /run/lock
tmpfs                     19G     0   19G   0% /run/user/1000
```

Any idea what might be going on here?  Is it trying to write to some device that is a read only device in a LXC container situation?   Or maybe some of the permissions are set wrong in the LXC container template?   I never had any of these problems with 14.04/0.27.

Much obliged,
Matt

---

### Post by mattlach on 2016-05-02
I came across [this](https://lists.linuxcontainers.org/pipermail/lxc-users/2016-January/010791.html) which might be a solution.

---

