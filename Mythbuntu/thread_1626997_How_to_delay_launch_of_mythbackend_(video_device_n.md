---
title: "How to delay launch of mythbackend?? (video device not found)"
date: 2010-11-20
forum: Mythbuntu
---

### Post by kyphos on 2010-11-20
I'm migrating from an old MythTV config running on Gentoo to Mythbuntu 10.04.

I have a Hauppauge PVR-150 tuner card. About half the time when I boot the system, the front-end's Information Center reports that the tuner card has an error.  A reboot usually  fixes it.

The mythbackend log reports:
```
2010-11-20 17:18:40.498 Channel(/dev/videoPVR)::Open(): Can't open video device, error "No such file or directory"
```

My present hypothesis is that the mythbackend process is trying to open the device before the PVR-150 card is "ready".  I don't know why it wouldn't be "ready" (and I never had any such probems when using the Gentoo system).  Perhaps adding a short delay to the initiation of the mythbackend process will work around the problem.

Upon booting a Mythbuntu system, all sorts of magic happens. The myth user gets logged in, the mythfrontend process gets launched, as does the mythbackend process. **Who or what is responsible for launching mythbackend? ** How might I introduce a small delay?

Any other suggestions on why the PVR-150 device can't be opened and/or how to fix the root cause will be gratefully received.

Thanks.

---

### Post by ian dobson on 2010-11-21
Hi,

I'm not 100% sure with 10.04, but I think upstart is responsible for starting myth-backend. Have a look in the /etc/init directory for a file names mythbackend.conf.

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

pre-start script
        sleep 5;
end script

exec /bin/su -c "/usr/bin/mythbackend --noupnp --logfile /var/log/mythtv/mythbackend.log --user mythtv -v eit" mythtv
```

The prestart script waits 5 seconds before continuing.

If your system doesn't use upstart then the script will be in /etc/init.d and be called something like mythbackend.

Regards
Ian Dobson

---

### Post by dsd_inc123 on 2010-11-21
Good discussion is going on 
________________________


[fas software](http://www.dsdinc.com/products/sage-fas-fixed-asset-mgmt/index.html)

[saleslogix](http://www.dsdinc.com/products/sage-mas-90-200-add-ons.html)

[Sagecrm](http://www.dsdinc.com/products/crm-solutions/index.html)

[sage software](http://www.dsdinc.com/products/sage-abra/index.html)

[erp software](http://www.dsdinc.com/products/sage-accpac-erp/index.html)

[deltek](http://www.dsdinc.com/products/sage-software-a-z/index.html)

[crm software](http://www.dsdinc.com/mas200/index.html?category_one=products&amp;category_two=mas200&amp;page=index)

---

### Post by kyphos on 2010-11-21
> **ian dobson said:**
> Hi,

I'm not 100% sure with 10.04, but I think upstart is responsible for starting myth-backend. Have a look in the /etc/init directory for a file names mythbackend.conf.



@Ian,
I've never heard of "upstart" (shows how little I know about Ubuntu), but I did find the mythbackend file you referred to.

```
myth@myth-box:/etc/init$ cat mythtv-backend.conf 
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script
```It's a little bit different than the one on your system; notably, there's no 5 second delay. Perhaps I'll try adding the pre-start script to my .conf file and see if that helps with my problem. 

In fact, looking at your version of the .conf file may shed some light on my issue. I note that your version doesn't initiate mythbackend until udev is finished its work.  (that's how I interpret the **...and started udev-finish** code).  I've found it necessary to use udev rules to create symlinks for my two tuner cards in order to get unambiguous device names. As a result, mythbackend isn't trying to open /dev/video0 or /dev/video1.  It's trying to open /dev/videoPVR (a symlink to whichever video device happens to be my PVR-150).  Is it possible that my symlink hasn't yet been defined by udev when mythbackend is trying to open it?  That could explain the error I'm seeing.

Thanks,
-kyphos

---

### Post by Senkoboy on 2010-11-21
Read this thread also, I had the same problem.  Fixed it with the  information shown.

[http://ubuntuforums.org/showthread.php?t=1414630]("http://ubuntuforums.org/showthread.php?t=1414630")

---

### Post by kyphos on 2010-11-21
@Senkoboy,

Thanks for the link.

This thread also has similar information, indicating this bug has already been fixed (by tgm4833):
[http://ubuntuforums.org/showthread.php?t=1511342](http://ubuntuforums.org/showthread.php?t=1511342)


I think I'm on the right track. But I don't understand how to get "auto-builds".  After installing  from a 10.04 Mythbuntu LiveCD, I ran Update Manager, and have done so a couple of times since. Hundreds of packages and over 100MB of updates were downloaded and installed. I would have expected that fixes to mythtv modules would have been part of these updates, but apparently not.

What's the best practice for updating/maintaining a Mythbuntu installation?

---

### Post by kyphos on 2010-11-21
@Ian,
I want to thank you for your helpful reply at the top of this thread. Your pointer to /etc/init mythtv-backend.conf eventually led me to a solution.


For others having similar problems with tuner cards not being found, here's the explanation.
In the version of mythtv-backend.conf that Ian posted above, there was a fragment of code that did not exist in my version (**..and started udev-finish**).  My installation came from a 10.04 Mythbuntu LiveCD. As a result, mythbackend could launch on my system before udev had finished its tasks, one of which is to define symlinks for my tuner cards. These symlinks are needed due to the non-deterministic behavior of Ubuntu when it boots up.

After a bunch of googling, and helpful posts from others, I found that a patched version of mythtv-backend.conf had been released by the author (supermario) subsequent to the release of 10.04 Mythbuntu. This new version (see CODE below) contains the same 'started udev-finish' constraint which somehow got dropped from the 10.04 Mythbuntu build. Note that it doesn't have the 5 second delay present in the version that Ian posted. 

```
myth@myth-box:/etc/init$ cat mythtv-backend.conf 
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script
```I surmise that by waiting for udev to finish, mythbackend can proceed to launch knowing that all required symlinks have been created.

I had run Update Manager a few times after installing from the 10.04 Mythbuntu LiveCD. I naively assumed that would update my system. Little did I know that out of the box, Update Manager doesn't bother to update the mythtv components. That seems like a fairly serious omission in a Mythbuntu package, but that's the way it is, at least on the 10.04 Mythbuntu CD.

Once I figured out how to obtain bug fixes  (something formerly known as 'AutoBuilds';  another painful experience for a newcomer), I ran Update Manager again. This installed a new-and-improved version of mythbackend.conf, and it contains, once again, the '**started udev-finish**' constraint. I won't know for a while if this is a solid fix for the problem I was having at boot time. Time will tell.

Alas, today's Update Manager (updating 0.23.0 mythtv) broke other things, which I now have to troubleshoot.

---

### Post by tgm4883 on 2010-11-21
MythTV updates are available by installing the mythbuntu-repos package from here [www.mythbuntu.org/repos](www.mythbuntu.org/repos)

That is where you will find the updated package which includes the udev-finish line. This portion which was guessed correctly previously in this thread, makes mythbackend wait until udev has completely finished starting before it tries starting. That is likely the issue that you were running into there.

---

### Post by kyphos on 2010-11-21
> **tgm4883 said:**
> MythTV updates are available by installing the mythbuntu-repos package from here [www.mythbuntu.org/repos]("http://www.mythbuntu.org/repos")


@TGM,
Please forgive this really basic question. Is there any difference between what's found at [www.mythbuntu.org/repos](www.mythbuntu.org/repos) (which entails downloading the .deb file) versus opening the Mythbuntu Control Centre, selecting Repositories, and enabling the two checkboxes for mythtv and mythbuntu updates?

Thanks a lot.

---

### Post by tgm4883 on 2010-11-21
> **kyphos said:**
> @TGM,
Please forgive this really basic question. Is there any difference between what's found at [www.mythbuntu.org/repos](www.mythbuntu.org/repos) (which entails downloading the .deb file) versus opening the Mythbuntu Control Centre, selecting Repositories, and enabling the two checkboxes for mythtv and mythbuntu updates?

Thanks a lot.

Nope, if you have that availability in Mythbuntu control centre, then you already have the mythbuntu-repos package installed :)

---

### Post by kyphos on 2010-11-22
@TGM,
Thanks. All seems to be working now, having used Update Manager to update 0.23.0 and thus obtained the patched /etc/init/mythtv-backend.conf

I tried moving to 0.23.1 but it broke all sorts of things so I returned to 0.23.0.

---

