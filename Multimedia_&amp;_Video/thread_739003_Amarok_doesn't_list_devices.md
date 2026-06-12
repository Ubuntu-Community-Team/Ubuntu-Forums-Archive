---
title: "Amarok doesn't list devices"
date: 2008-03-29
forum: Multimedia &amp; Video
---

### Post by Elphizo on 2008-03-29
Hi all. I'm having a little problem with Amarok and my new Creative ZEN 8GB. In gutsy I wasn't able to detect this MP3 player, but I recently upgraded to hardy and now I can connect it even with Amarok, thanks to libmtp7(I suppose). Amarok works correctly and I can transfer everything from my music library, the problem is that, when I restart the program, the old devices are not listed anymore in the media device configuration window, but when I try to add a new one, if I use the same name of old devices, the program says that I can't name two devices in the same way. I belive that this means that, somewere, they are still listed, but amarok doesn't see them. I know that I could simply rename the device with ZenWHATEVER, but I was looking for a better solution. 
I hope it's clear, i cant't speak english very well, sorry. Thanks for reading!

---

### Post by insineratehymn on 2008-03-29
Have you tried checking to see if the device has been properly unmounted after you remove it?

---

### Post by Elphizo on 2008-03-29
No i don't. How can I check that? In the mount directory I can't find it.
I think that the problem is about Amarok. If i add a device , close and restart the program, the device is gone and I can't use the same name anymore, and this happens even if I don't connect the ZEN to the PC. One workaround is to delete the device from the list before closing the program, but sometimes I forget to do it.

---

### Post by insineratehymn on 2008-03-31
Yeah, I think the problem is that it isn't getting unmounted properly.

You said it is a Zen?

Google showed me this little info site about Zen + Linux:
[http://tiagoboldt.net/blog/creative-zen-linux/](http://tiagoboldt.net/blog/creative-zen-linux/)

Try that out, make sure to especially note the part about fusermount.

---

### Post by wyth on 2008-04-01
I was having a similar problem on 8.04 beta with Amarok 1.4.8 and a generic ums device iRiver T10.  After poking around, here's what worked for me:[LIST]
[*] I closed Amarok;
[*]I went into ~/.kde/share/config/amarokrc and removed every instance of any configured device;
[*]I opened Amarok back up and manually added a generic device;
[*]I plugged in my device, made sure it mounted, connected via Amarok, and voila, I'm connected again.[/LIST]Hope that helps someone.

---

### Post by Elphizo on 2008-04-03
> **wyth said:**
> I was having a similar problem on 8.04 beta with Amarok 1.4.8 and a generic ums device iRiver T10.  After poking around, here's what worked for me:[LIST]
[*] I closed Amarok;
[*]I went into ~/.kde/share/config/amarokrc and removed every instance of any configured device;
[*]I opened Amarok back up and manually added a generic device;
[*]I plugged in my device, made sure it mounted, connected via Amarok, and voila, I'm connected again.[/LIST]Hope that helps someone.
This doesn't solved the problem, but at least I found the list of precedently added devices and I deleted it. Thanks for helping!

---

### Post by warp99 on 2008-04-03
Did you check to see if you added the devices in your system wide amarokrc file?

```
cat /etc/kde3/amarokrc && cat /usr/share/kubuntu-default-settings/kde-profile/default/share/config/amarokrc

```

If so you need to edit and delete those entries in the these files. Also check if you added the entry as root by accident:

```
sudo cat /root/.kde/share/config/amarokrc
```

If so you need to delete this file.

---

### Post by Elphizo on 2008-04-03
> **warp99 said:**
> Did you check to see if you added the devices in your system wide amarokrc file?

```
cat /etc/kde3/amarokrc && cat /usr/share/kubuntu-default-settings/kde-profile/default/share/config/amarokrc

```

If so you need to edit and delete those entries in the these files. Also check if you added the entry as root by accident:

```
sudo cat /root/.kde/share/config/amarokrc
```

If so you need to delete this file.

I can't find the second file, I have the ubuntu distro with ubuntu studio, and the only similar folder that I found in usr/share is ubuntustudio-default-settings, wich doesn't contain any amarokrc file. If I search amarokrc with gnome I can't find nothing but the file in etc/kde3, and I don't know why it doesn't find the one in home/user/.kde/share/config.
Anyway, if I try to manually add the device in the kde3 file, it disappears from the other file, and the problem still remains: amarok doesn't display any device, and if I try to add another one with the same name I get an error message, telling me that I can't use the same name on more than one device...

---

### Post by warp99 on 2008-04-03
Well it's looks like you are not the only one in Hardy:

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/207704](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/207704)

I would also confirm the bug with the maintainers.

---

### Post by mattman on 2008-04-04
> **wyth said:**
> I was having a similar problem on 8.04 beta with Amarok 1.4.8 and a generic ums device iRiver T10.  After poking around, here's what worked for me:[LIST]
[*] I closed Amarok;
[*]I went into ~/.kde/share/config/amarokrc and removed every instance of any configured device;
[*]I opened Amarok back up and manually added a generic device;
[*]I plugged in my device, made sure it mounted, connected via Amarok, and voila, I'm connected again.[/LIST]Hope that helps someone.

This worked for me. I had started trying out other media players because of this bug but could not find one that handled podcasts and media devices as well as Amarok. Glad I can use it again. Thanks a bunch.

---

