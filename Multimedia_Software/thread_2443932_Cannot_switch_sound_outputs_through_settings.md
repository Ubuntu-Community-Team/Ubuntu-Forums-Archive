---
title: "Cannot switch sound outputs through settings"
date: 2020-05-22
forum: Multimedia Software
---

### Post by DuckHook on 2020-05-22
I have just network upgraded one of my partitions from vanilla Ubuntu Bionic to Focal. Since upgrading, all sound output is redirected to my USB headphones if it is plugged in. I've worked around this by installing pavucontrol and turning off the USB device under Configuration. This then allows me to choose my other outputs, but I miss the old convenience of just switching between outputs using Settings.

Curiously, on a separate partition in which I installed a virgin Focal from scratch, sound can be switched at will using only *Settings*.

Clearly, some configuration was changed on the upgrade, but for the life of me, I can't find it.

I'm curious if anyone else has experienced this and would greatly appreciate any insights that might help me fix it.

Update:

Stranger and stranger… I can switch between sound sinks in Rhythmbox, but not in any of my browsers, Totem or VLC. So it varies from app to app. First time I've run into something like this. I thought sound was handled at a more basic layer than apps, but apparently not.

---

### Post by CatKiller on 2020-05-22
> **DuckHook said:**
> Since upgrading, all sound output is redirected to my USB headphones if it is plugged in.

That sounds very much like your USB headphones are set as the *fallback device*.

Setting device priorities in KDE is trivial, but I understand from reports here that it's harder in Gnome; I last used Gnome with Xenial so I can't help with the specifics.

---

### Post by Yellow Pasque on 2020-05-22
Is there any way you can create another user and see if the problem exists when logging in as the new user?

I'm not sure if this is related in any way: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1877194](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1877194)

---

### Post by DuckHook on 2020-05-22
> **CatKiller said:**
> That sounds very much like your USB headphones are set as the *fallback device*.

Setting device priorities in KDE is trivial, but I understand from reports here that it's harder in Gnome; I last used Gnome with Xenial so I can't help with the specifics.
Thanks for the pointer. I did try setting my main speakers as fallback, but no joy. Setting fallback can be accessed through pavucontrol &#8594; Output Devices. In one sense, it isn't difficult, but one has to download pavucontrol first, which does obscure the location of this control.
> **Yellow Pasque said:**
> Is there any way you can create another user and see if the problem exists when logging in as the new user?
Good suggestion. Will try that next.
> I'm not sure if this is related in any way: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1877194](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1877194)
Thanks for the link. I tried editing /etc/pulse/default.pa as per suggested fix, but no go.

Will reset to default config file and try creating new user to test.

---

### Post by DuckHook on 2020-05-22
New user works perfectly. So the problem is in my local user settings. I've a rather complex setup, mainly because I have a bunch of LXD containers with Unix sockets linked into pulseaudio. However, I don't believe that's the issue since they are subservient to my base install and copy their settings from the main installation and not the other way around.

I've also checked ~/.config/pulse/xxxx&#8230;xxxx-default-sink

As CatKiller suspected, it was pointed to the USB dongle even though, in pavucontrol, it was set to main speakers. That in itself is frustrating. It means that pavucontrol does not, in fact, make the needed changes. So I manually edited the file to point to the analogue speakers and rebooted. No joy. The settings survive a reboot, but does not change the forced redirection behaviour.

Stepping out for a couple of hours and will look into it some more upon my return.

Thanks for the pointers.

---

### Post by CatKiller on 2020-05-22
> **DuckHook said:**
> As CatKiller suspected, it was pointed to the USB dongle even though, in pavucontrol, it was set to main speakers. That in itself is frustrating. It means that pavucontrol does not, in fact, make the needed changes. So I manually edited the file to point to the analogue speakers and rebooted. No joy. The settings survive a reboot, but does not change the forced redirection behaviour. 

Just as a heads-up, you can have more than one fallback device configured.

---

### Post by DuckHook on 2020-05-22
> **CatKiller said:**
> Just as a heads-up, you can have more than one fallback device configured.
Would you know where those other config files/settings might be hiding? I had only the one device in my ~/.config/pulse/xxxx…xxxx-default-sink

---

### Post by DuckHook on 2020-05-22
Thanks to the road laid out for me by both CatKiller and Yellow Pasque, the issue is finally resolved. I ended up resorting to the brute force method of nuking the contents in my entire *.config/pulse* directory and replacing it with the pristine contents from that of the new user. For posterity, the details follow:

[list=1]
[*]In addition to *~/.config/pulse/xxxx…xxxx-default-sink* and *~/.config/pulse/xxxx…xxxx-default-source*, the contents of *.config/pulse* include three databases: ```
~/.config/pulse/xxxx…xxxx-card-database.tdb
~/.config/pulse/xxxx…xxxx-device-volumes.tdb
~/.config/pulse/xxxx…xxxx-stream-volumes.tdb
```
[*]The contents of these databases were pristine in the new user databases but choked with oddball settings in my old user.
[*]I renamed the old files and copied the new user's files into *.config/pulse*
[*]Rebooted, and everything now works as it should.
[*]Deleted the old files.
[/list]
I surmise that my pulseaudio databases have been corrupted through years of use and network upgrades. The small changes in pulseaudio between Focal and Bionic were enough to finally push things over the edge. The new pulseaudio could not cope with the accumulated cruft in the inherited *.config/pulse* directory and responded by going on strike.

Lessons learned:

[list=1]
[*]If do-release-upgrade(ing), be prepared for subtle breakages and wonky post-upgrade behaviour.
[*]More often than not, such breakage is not due to bugs but to accumulated cruft and non-default settings that were tinkered with at some point and then forgotten about.
[*]Creating a new user and comparing configs is a great diagnostic strategy,
[/list]
Many thanks to CatKiller and Yellow Pasque.

---

