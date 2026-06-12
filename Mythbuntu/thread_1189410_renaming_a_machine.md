---
title: "renaming a machine"
date: 2009-06-16
forum: Mythbuntu
---

### Post by zapstrap on 2009-06-16
I have mythbuntu 9.04 installed on a machine, and it seems when I did the install I didn't specify a host or domain name.  Since I'm behind a firewall, I'd like to give the machine a name, and even give it a static IP address.

I'm used to the old rh 2.4.xx kernel, and couldn't figure out how to do it initially.  After a little reading I discovered that I *should* be able to type:

  hostname <newname> 

...and all should be well.  I did this, and it seems to have made a total mess out of the install.  All of the video drivers reset to default modes, without properly rescaling images, changed the mythTV theme (wtf?) and now the frontend can't see the backend.  Previously the backend could wake the machine up to make recordings and put it back to sleep.  Now the wake-up part of the picture is broken.

Is there a straight-forward way out of this, other than deleting the host name?  I'd really like the other machines on the network to be able to see this machine, and it's not going to happen if it's called localhost-desktop, when everybody else has a different name.

---

### Post by uncle hammy on 2009-06-16
MANY tables in the mythtv database have a "hostname" field, which would be set to your old host name for those records....which no longer exists.  If your going to change the hostname of your machine, you need to update every record in the database that has a hostname field to the new value.

[https://www.fladenmuller.org/mythtv/mythtv-doc/mythtv-HOWTO-21.html#ss21.15](https://www.fladenmuller.org/mythtv/mythtv-doc/mythtv-HOWTO-21.html#ss21.15)

One of those tables is the "settings" table which stores all the settings for each host...including the theme ;)

Until you do this, I would suggest you simply change your hostname back to it's old value.

---

### Post by zapstrap on 2009-06-17
I tried the database modification, but I'm still unable to get the frontend to do much of anything.

I think there are other problems.  When I renamed the machine, mythTV seemed to reset itself, and changed virtually every setting.  It reset the display resolution, and started putting it into a very low-res format (<640x480) without prescaling everything to fit, so most of everything ended up off the screen and not viewable.  It also reset which input card it was working with.

---

### Post by stevanbt on 2009-06-19
Hi,
I changed the name of my combined frontend/backend a while back.  I didn't have as much trouble as you seem to be having.  There is a script that can do the required database changes (but it sounds like you've already done that, here it is anyway):-

[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Change_the_hostname_of_a_MythTV_frontend_or_backend](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Change_the_hostname_of_a_MythTV_frontend_or_backend)

Hope this helps.

Thanks, Steve.

---

### Post by zapstrap on 2009-06-19
Thanks for the link.  I think the database change went reasonably well.  A small editorial comment would be that this seems pretty technical to expect a typical user to tangle with.

In the end, because it had been a couple of days with no progress at all, I gave up last night and started again from scratch.  I believe that the problems were related to mythTV resetting all of its configuration options to a set of defaults.  This wasn't obvious until I re-installed and realized that the Hauppauge card had been changed.

Of course, now that I've been around in circles a couple of times, the installation went far more smoothly.  Now if I could just get mythTV to work with my DVD drive...

---

