---
title: "Easy install MYTHTV on 23.04 Lunar lobster"
date: 2023-05-27
forum: Multimedia Software
---

### Post by vidtek on 2023-05-27
I did an easy install with gotchas for earlier flavours the last was Focal so here is one for Lunar:

Add mythtv repository of your choice replace the XX with 33 for latest stable version:
```
sudo add-apt-repository ppa:mythbuntu/XX

sudo update

sudo apt install mythtv
```

A dialogue box asks if other computers will run mythytv

once you answer that the install commences.

It will automatically create the mythtv group and add mythtv to it and video and audio
Adding user mythtv to group video
Adding user mythtv to group audio
Adding user mythtv to group cdrom
Adding user mythtv to group dialout

Ensure your user and any other user also is added to these groups. (not quite sure why the dialout group?)

Now edit the sudoers file with this command with this if you want acpi shutdown and wakeup
:```
sudo visudo
``` 
 ```
%mythtv ALL=NOPASSWD: /sbin/shutdown, /usr/bin/mythshutdown, /usr/sbin/checklogin.sh, /usr/sbin/setwakeup.sh, /usr/sbin/rtcwake

```
Create the trailers, banners, screenshots, coverart, fanart directories in /home/mythtv (or wherever you want)  and ensure the permissions are usable by mythtv.

I always reboot at this point to enable the groups added.

Now is the time to test the install.  I always do it in a windowed terminal in case something is amiss.  It makes it much easier to adjust things.:```
mythtv-setup -w
```

You should now have the setup screens.  Do your normal mythtv setups, adding tuners, setting directories etc.

Once that's done, do ```
mythfrontend -w
``` and see if you can login.

If all is well, you should have a working mythtv installation.

If you can't login, check these 4 locations for the config.xml files to ensure they are identical: /etc/mythtv/config.xml   /home/youruser/.mythtv/config.xml  /home/mythtv/.mythtv/config.xml /root/.mythtv/config.xml

I usually keep one copy of the file in /etc/mythtv and symlink all the others.

Cheers Tony.

---

### Post by TheFu on 2023-05-27
I always thought that people deploying media centers didn't want to be forced into upgrading their OS every 6 months.  23.04 isn't an LTS, to anyone choosing it will need to move to 23.10, then 24.04 to stay patched.  There's no other choice.

The consideration of LTS or non-LTS is very important.


> I always reboot at this point to enable the groups added.
In theory, a reboot shouldn't be needed, but that problem appears to be another gift from the systemd team. For 40+ yrs, to see group changes, we could use newgrp or just logout, then login, but I've seen a bug a few times with systemd that does require a reboot to see group changes.  Don't know why and it isn't **always** required.  Rather than troubleshoot the issue, most people just reboot. Sigh.

I wish installing MythTV was this easy 15 yrs ago when I tried (and failed).  Thanks to HDHR tuners, using Jellyfin is relatively easy, though it is far from great.  Connecting to HDHR tuners that support DLNA is trivial. I don't think any client-side software beyond jellyfin is needed. No HDHR drivers required.

---

### Post by vidtek on 2023-05-28
> **TheFu said:**
> I always thought that people deploying media centers didn't want to be forced into upgrading their OS every 6 months.  23.04 isn't an LTS, to anyone choosing it will need to move to 23.10, then 24.04 to stay patched.  There's no other choice.

The consideration of LTS or non-LTS is very important.



In theory, a reboot shouldn't be needed, but that problem appears to be another gift from the systemd team. For 40+ yrs, to see group changes, we could use newgrp or just logout, then login, but I've seen a bug a few times with systemd that does require a reboot to see group changes.  Don't know why and it isn't **always** required.  Rather than troubleshoot the issue, most people just reboot. Sigh.

I wish installing MythTV was this easy 15 yrs ago when I tried (and failed).  Thanks to HDHR tuners, using Jellyfin is relatively easy, though it is far from great.  Connecting to HDHR tuners that support DLNA is trivial. I don't think any client-side software beyond jellyfin is needed. No HDHR drivers required.

Hi Fu,  Yes, you are right LTS and stability is crucial, but idiots like me like to fiddle and try out all the latest an greatest - I do it on a trial machine kept for just that purpose.

I know what you mean about the reboot thing, it's just easier and only takes a few seconds.   I too failed miserably with several mythtv installs in the early days, but have been using it since about the turn of the century.   It's much more stable now, although they keep messing about with mysql sodding about with different command structures.   You just get used to one thing and they change it.  Probably for good reasons, but it can be very frustrating. 

Cheers Tony.

---

