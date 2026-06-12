---
title: "Restricted Formats DVDs not Playing"
date: 2017-03-12
forum: Multimedia Software
---

### Post by Priswell on 2017-03-12
I've been trying to get my Restricted DVDs to play on a new 16.04 install. I followed instructions on 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Made sure that the multiverse repository was installed, but when I tried to run the install-css.sh script, I got:

```
/usr/share/doc/libdvdread4/install-css.sh: command not found
```

Tried to

```
sudo dpkg-reconfigure libdvd-pkg
```

and run it again, still no success. I've read several responses here where trying to run the install processes again seemed to help, but no success. I've been going round and round the process several times. Tried rebooting.

Is there anything else I can try? Or is there something I'm missing?

---

### Post by deadflowr on 2017-03-12
Do you try the recommended command to install the libdvd-pkg package?
Not just try to reconfigure the package.
```
sudo apt-get install libdvd-pkg
```
there is no need to run the sh script anymore for newer versions of Ubuntu.
the libdvd-pkg does everything now.

---

### Post by Perfect Storm on 2017-03-12
/me ninja'd by deadflowr

Did you install libdvd-pkg before reconfigure it?

---

### Post by Priswell on 2017-03-12
*Did you install libdvd-pkg before reconfigure it?* 

Yes. I've gone through the full sequence as mentioned on the referred Ubuntu help page several times.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvd-pkg is already the newest version (1.4.0-1-1).

---

### Post by deadflowr on 2017-03-12
How fresh an install is it?
Is this a totally fresh install or do you have a separate home partition. (or some other method that might have restored a backup of home, maybe?)
If you have a separate home partition (or it was restored from a backup) that you use, maybe you have a legacy hidden folder ~/.dvdcss folder.
In that case try removing that folder.

---

### Post by Priswell on 2017-03-12
Thanks for your response(s).

*How fresh an install is it?*

Downloaded it last week, and I installed it last night. No special home partition. There is no ~/.dvdcss folder. I looked.

---

### Post by deadflowr on 2017-03-12
Ooh, what player are you trying?

(I ask because there is a funny thing about vlc on 16.04.
If you installed vlc through the software center on 16.04, it might have installed the snap version.
And the snap version cannot use the libdvdcss library, currently; if it ever will)
(More about snaps: [https://www.ubuntu.com/desktop/snappy]("https://www.ubuntu.com/desktop/snappy")

But installing the regular repository vlc version should work.
(Moot, though, if you already did this, or if something else is going on)

---

### Post by Priswell on 2017-03-12
*If you installed vlc through the software center on 16.04, it might have installed the snap version.*

I installed it from the command line: 

```
sudo apt-get install vlc
```

---

### Post by Priswell on 2017-03-12
OK, I reformatted and reinstalled Ubuntu 16.04. Immediately after installing updates, I 


```
sudo apt-get install vlc
```

then

```
sudo apt-get install libdvd-pkg
```


Tried a DVD, no response. Then did the reconfigure as follows:



```
sudo dpkg-reconfigure libdvd-pkg
libdvd-pkg: Downloading orig source...
I: libdvdcss_1.4.0
/usr/bin/wget --tries=3 --timeout=40 --read-timeout=40 --continue -O libdvdcss_1.4.0.orig.tar.bz2 \
          http://download.videolan.org/pub/libdvdcss/1.4.0/libdvdcss-1.4.0.tar.bz2 \
        || /usr/bin/uscan --noconf --verbose --rename --destdir=/usr/src/libdvd-pkg --check-dirname-level=0 --force-download --download-current-version /usr/share/libdvd-pkg/debian
--2017-03-12 16:25:06--  http://download.videolan.org/pub/libdvdcss/1.4.0/libdvdcss-1.4.0.tar.bz2
Resolving download.videolan.org (download.videolan.org)... 88.191.250.2, 2a01:e0d:1:3:58bf:fa02:c0de:5
Connecting to download.videolan.org (download.videolan.org)|88.191.250.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 364373 (356K) [application/octet-stream]
Saving to: ‘libdvdcss_1.4.0.orig.tar.bz2’

libdvdcss_1.4.0.ori 100%[===================>] 355.83K   423KB/s    in 0.8s    

2017-03-12 16:25:07 (423 KB/s) - ‘libdvdcss_1.4.0.orig.tar.bz2’ saved [364373/364373]

libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.0.orig.tar.bz2: OK
libdvd-pkg: Unpacking and configuring...
libdvd-pkg: Building the package... (it may take a while)
libdvd-pkg: Build log will be saved to /usr/src/libdvd-pkg/libdvdcss2_1.4.0-1~local_amd64.build
Current: = cap_chown,cap_dac_override,cap_dac_read_search,cap_fowner,cap_fsetid,cap_kill,cap_setgid,cap_setuid,cap_setpcap,cap_linux_immutable,cap_net_bind_service,cap_net_broadcast,cap_net_admin,cap_net_raw,cap_ipc_lock,cap_ipc_owner,cap_sys_module,cap_sys_rawio,cap_sys_chroot,cap_sys_ptrace,cap_sys_pacct,cap_sys_admin,cap_sys_boot,cap_sys_nice,cap_sys_resource,cap_sys_time,cap_sys_tty_config,cap_mknod,cap_lease,cap_audit_write,cap_audit_control,cap_setfcap,cap_mac_override,cap_mac_admin,cap_syslog,cap_wake_alarm,cap_block_suspend,37+ep
Bounding set =cap_chown,cap_dac_override,cap_fowner,cap_wake_alarm,cap_block_suspend,37
Securebits: 024/0x14/5'b10100
 secure-noroot: no (unlocked)
 secure-no-suid-fixup: yes (unlocked)
 secure-keep-caps: yes (unlocked)
uid=0(root)
gid=0(root)
groups=0(root)
libdvd-pkg: Installing...
Selecting previously unselected package libdvdcss-dev:amd64.
(Reading database ... 210720 files and directories currently installed.)
Preparing to unpack .../libdvdcss-dev_1.4.0-1~local_amd64.deb ...
Unpacking libdvdcss-dev:amd64 (1.4.0-1~local) ...
Selecting previously unselected package libdvdcss2:amd64.
Preparing to unpack .../libdvdcss2_1.4.0-1~local_amd64.deb ...
Unpacking libdvdcss2:amd64 (1.4.0-1~local) ...
Setting up libdvdcss2:amd64 (1.4.0-1~local) ...
Setting up libdvdcss-dev:amd64 (1.4.0-1~local) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
```

and tried the DVD again. Still no success.

---

### Post by Priswell on 2017-03-13
OK, I'm not really sure what happened, but it works now. I went through the motions of installing (reinstalling?) libdvdnav4, libdvdread4, gstreamer1.0-plugins-bad, gstreamer1.0-plugins-ugly and libdvd-pkg again. All reported that they had already been installed, no changes. Then I did the 

```
sudo dpkg-reconfigure libdvd-pkg
```

thing again, and it said, "Duh, you already did that, too." Then I popped a DVD movie in and it worked! Thanks for watching this space, and any contributions made.

---

