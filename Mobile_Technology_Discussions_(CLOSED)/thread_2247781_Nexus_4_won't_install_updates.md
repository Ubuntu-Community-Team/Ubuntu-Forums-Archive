---
title: "Nexus 4 won't install updates"
date: 2014-10-10
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Teoclaid on 2014-10-10
Hi.  I am fairly new to Ubuntu and Linux in general (so please be gentle with me!)

I have been running Ubuntu Touch on a Nexus 4 for around a month and a half, and updated on 30/9 to 14.10 (r243).  I am experiencing a few glitches and I'm not sure where the correct place to report them is (so I guess that is my first question),  but more urgently the phone has stopped installing updates in the past 3-4 days.  It tells me that there are updates, and if I hit 'install' it changes to the installation progress bar and 'pause' button but nothing happens.  I now have 9 updates waiting.

Possibly related - the battery ran flat last Friday and I was eventually forced to reset the phone because once it finally came back to life it refused to recognise the sim.  I didn't have problems with updates until a few days after that though.

I have 14.04 on a VM on my macbook, but for about 2 weeks now (before the big update) it has been recognising the device but no longer allowing me to access its contents.  Again, not sure if relevant.

Grateful for any suggestions and help.  Thanks!

---

### Post by cariboo on 2014-10-11
For Touch problems, this may be a better place, than New to Ubuntu.

---

### Post by grahammechanical on 2014-10-11
I have absolutely no experience of running Ubuntu Touch (now called Ubuntu for Devices) on a phone. So, the best I can offer is this link with the suggestion to check out sections Upgrading Ubuntu and Next Steps.

[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

You might be interested in this page about Channels.

[http://developer.ubuntu.com/start/ubuntu-for-devices/image-channels/](http://developer.ubuntu.com/start/ubuntu-for-devices/image-channels/)

It is my understanding that Ubuntu for Devices now gets Image Updates. Note this comment:

> [COLOR=#333333][FONT=Ubuntu]Ubuntu images are generated daily (often multiple images per day) and are thoroughly tested with automated and manual tests to ensure they comply with Ubuntu&#8217;s QA standard. These daily images are distributed on the &#8216;devel-proposed&#8217; channel and are only promoted to the &#8216;devel&#8217; channel once they comply with a set of quality criteria.[/FONT][/COLOR]

What channel is this device set to update/upgrade from? If it is the devel channel, then those 9 updates might be 9 images and 8 of them will have been replaced by the latest image. Incidently, Ubuntu 14.10 has not yet been released. Although Ubuntu Touch is being built on the 14.10 development code what you should have is image 14.09.

Regards.

---

### Post by Teoclaid on 2014-10-11
thanks :)

---

### Post by Teoclaid on 2014-10-11
Thanks for the reply graham.  Didn't know about a name change from Ubuntu Touch - interesting!

Yes, it receives images automatically, and I'm on the Utopic 14.10 Daily Build channel - [http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/) - as this was the only one I could get to work when I initially flashed my device.  That page on channels was a little out of date even back then, as the 'devel' channel name had been changed to 'utopic'...

I now have 16 updates, and they are all for apps, not system.  

Perhaps of use for those in the know, here is the info from my 'about this phone' pages:
[INDENT]OS: Ubuntu 14.10 (r243)
Last updated: 30/09/14
Ubuntu image part: 20140916
Ubuntu build description:  Ubuntu Utopic Unicorn (development branch) - armhf (20140916-020205)
Device image part: 20140903.1
Device build description: aosp_mako-userdebug 4.4.2 KOT49H 20140902-2009-0ubuntu1 test-keys
[/INDENT]

Thanks

---

### Post by Teoclaid on 2014-10-17
Hi.  I found out what was stopping the downloads (though it's a bug beyond my control!).  I had deleted some of the default apps (eg Amazon), but discovered the Ubuntu store was still showing them as installed.  Sure enough, as soon as there were updates for any of the apps I had deleted the whole update system stopped working.  I had re-set the phone and had it happen again before I worked it out.  I've re-set now and am not deleting any apps!

Is there somewhere to quickly report bugs like this?  (and things like the phone locking during calls, orientation lock not working, etc)

Thanks!  :)

---

