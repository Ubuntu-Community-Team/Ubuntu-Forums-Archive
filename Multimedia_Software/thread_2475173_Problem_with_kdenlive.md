---
title: "Problem with kdenlive"
date: 2022-05-18
forum: Multimedia Software
---

### Post by gale85 on 2022-05-18
I have a problem with kdenlive in Ubuntu 22.04 today I did a restore system but kdenlive after update and upgrade the system I get the error "Kdenlive crashed on last startup.
Do you want to reset the configuration files? "Yes or No But it doesn't matter what I click the program won't and won't. That's how the system restored before and now. I'm going crazy and I need the program urgently, I worked and reinstalled everything and deleted file yes yes and he did it himself when I click yes and again nothing. Does anyone know how to solve this?

---

### Post by Yellow Pasque on 2022-05-19
What happens when you start it from the command line?

---

### Post by gale85 on 2022-05-19
Now by some miracle it works kdenlive but I can't see nicely all parts of the program there is no maximize button in the upper right corner. In the beginning, when he didn't want to work, he sent me a message in the terminal that he deleted the settings files, and that's it, after that it breaks and won't start. After that I did everything that is written on this site [https://www.linuxcapable.com/how-to-install-kdenlive-on-ubuntu-22-04-lts/](https://www.linuxcapable.com/how-to-install-kdenlive-on-ubuntu-22-04-lts/) After the restart it now works kdenlive but as I already said there is no maximize button below I can't see that zoom scale so I do it a little differently. By the way, here is the message I get in the terminal
```
Qt: Session management error: Could not open network socket=== /// CANNOT ACCESS SPEECH DICTIONARIES FOLDER
profilePath from $MLT_PROFILES_PATH:  "/snap/kdenlive/48/usr/share/mlt-7/profiles/"
meltPath from KdenliveSetting::rendererPath:  "/snap/kdenlive/48/usr/share/mlt-7/profiles/"
Invalid metadata for  "avcolour_space"
Failed to parse "avcolour_space"
Invalid metadata for  "avcolor_space"
Failed to parse "avcolor_space"
Invalid metadata for  "avdeinterlace"
Failed to parse "avdeinterlace"
Invalid metadata for  "swscale"
Failed to parse "swscale"
Invalid metadata for  "swresample"
Failed to parse "swresample"
Invalid metadata for  "audiochannels"
Failed to parse "audiochannels"
Invalid metadata for  "audioconvert"
Failed to parse "audioconvert"
Invalid metadata for  "imageconvert"
Failed to parse "imageconvert"
Invalid metadata for  "jack"
Failed to parse "jack"
Invalid metadata for  "glsl.manager"
Failed to parse "glsl.manager"
Invalid metadata for  "movit.convert"
Failed to parse "movit.convert"
Invalid metadata for  "movit.crop"
Failed to parse "movit.crop"
Invalid metadata for  "movit.resample"
Failed to parse "movit.resample"
Invalid metadata for  "movit.resize"
Failed to parse "movit.resize"
Invalid metadata for  "telecide"
Failed to parse "telecide"
Invalid metadata for  "deinterlace"
Failed to parse "deinterlace"
plugin not available: "avfilter.acompressor"
plugin not available: "avfilter.aecho"
plugin not available: "avfilter.agate"
plugin not available: "audiolevelgraph"
plugin not available: "avfilter.atadenoise"
plugin not available: "avfilter.bwdif"
plugin not available: "avfilter.deblock"
plugin not available: "avfilter.dedot"
plugin not available: "avfilter.deflate"
plugin not available: "avfilter.derain"
plugin not available: "avfilter.doubleweave"
plugin not available: "avfilter.field"
plugin not available: "avfilter.framestep"
plugin not available: "avfilter.fspp"
plugin not available: "avfilter.graphmonitor"
plugin not available: "avfilter.hqdn3d"
plugin not available: "avfilter.inflate"
plugin not available: "avfilter.lagfun"
plugin not available: "avfilter.loudnorm"
plugin not available: "avfilter.random"
plugin not available: "avfilter.removegrain"
plugin not available: "avfilter.separatefields"
plugin not available: "avfilter.shuffleplanes"
plugin not available: "avfilter.sr"
plugin not available: "avfilter.tmix"
plugin not available: "avfilter.w3fdif"
plugin not available: "avfilter.weave"
plugin not available: "avfilter.yadif"
plugin not available: "frei0r.baltan"
plugin not available: "frei0r.bgsubtract0r"
plugin not available: "frei0r.bigsh0t_eq_mask"
plugin not available: "frei0r.bigsh0t_eq_to_rect"
plugin not available: "frei0r.bigsh0t_hemi_to_eq"
plugin not available: "frei0r.bigsh0t_rect_to_eq"
plugin not available: "frei0r.bigsh0t_stabilize_360"
plugin not available: "frei0r.bigsh0t_transform_360"
plugin not available: "frei0r.delay0r"
plugin not available: "frei0r.delaygrab"
plugin not available: "frei0r.facebl0r"
plugin not available: "frei0r.facedetect"
plugin not available: "frei0r.lightgraffiti"
plugin not available: "frei0r.lightgraffiti"
plugin not available: "frei0r.tehRoxx0r"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa.9354877"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "movit.unsharp_mask"
plugin not available: "region"
plugin not available: "timewarp"
plugin not available: "region"
ALSA lib conf.c:4120:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
QObject::connect: No such signal QDBusAbstractInterface::DeviceAdded(QString)
QObject::connect: No such signal QDBusAbstractInterface::DeviceRemoved(QString)
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.308\" (uid=1000 pid=25338 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=731 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.308\" (uid=1000 pid=25338 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=731 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.308\" (uid=1000 pid=25338 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=731 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.308\" (uid=1000 pid=25338 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=731 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.308\" (uid=1000 pid=25338 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=731 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.308\" (uid=1000 pid=25338 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=731 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.308\" (uid=1000 pid=25338 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=731 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.308\" (uid=1000 pid=25338 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=731 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
QObject::disconnect: Unexpected nullptr parameter
QObject::disconnect: Unexpected nullptr parameter
QObject::disconnect: Unexpected nullptr parameter
qrc:/qml/timeline.qml:2021:5: QML Connections: Implicitly defined onFoo properties in Connections are deprecated. Use this syntax instead: function onFoo(<arguments>) { ... }
=== REG FOCUS:  false

```
Let me just mention that I now have two icons for kdenlive, one works and the other does not

---

### Post by Yellow Pasque on 2022-05-20
Looks like the snap version is not working. I don't use snaps, so maybe there is a  way around it, but if it was me, I would just use the apt/deb version and call it a day.

---

### Post by mIk3_08 on 2022-05-21
> **gale85 said:**
> I have a problem with kdenlive in Ubuntu 22.04 today I did a restore system but kdenlive after update and upgrade the system I get the error "Kdenlive crashed on last startup.
Do you want to reset the configuration files? "Yes or No But it doesn't matter what I click the program won't and won't. That's how the system restored before and now. I'm going crazy and I need the program urgently, I worked and reinstalled everything and deleted file yes yes and he did it himself when I click yes and again nothing. Does anyone know how to solve this? I prefer to the old kdenlive than using the new version of it. I always encounter problem with the new version of Kdenlive but it will be okay then after I perform a restart. But compared to the old Kdenlive I always prefer to use the old version than the new version of Kdenlive release.  Regards and cheers

---

### Post by gale85 on 2022-05-22
I installed it over the snap because I couldn't install it properly the classic way. I tried everything, I deleted it, I reinstalled it through the terminal and through Ubuntu Software, nothing helped, so with the help of that link above, I somehow miraculously installed it, but I already said that there is no maximize button. Can I somehow delete everything that has to do with kdenlive and then install it normally again or if I install an older version

---

### Post by Yellow Pasque on 2022-05-22
The no maximize button sounds like a problem with CSD (Client Side Decorations). Does it still occur if you login with an X(server) session instead of Wayland?

---

### Post by gale85 on 2022-05-22
I haven't tried it but I'll let you know when I try

---

### Post by gale85 on 2022-05-26
Today I tried to log on to Wayland as I only have two default options Ubuntu and Ubuntu Wayland and then on kdnelive showed me the option to maximize but it doesn't seem to work at all and still lacks part of the bottom row so it gives me a little problem when some short I need to cut the frame in the clip. Just to mention when I log on to Wayland the system works much slower

---

### Post by SeijiSensei on 2022-05-26
Have you considered installing Kubuntu or KDE Neon so you have a native KDE desktop to work with?  I just installed kdenlive to my Neon 5.24 machine (built on Ubuntu 20.04), and it works just like it did on previous versions of Kubuntu.

---

### Post by gale85 on 2022-05-26
I haven't thought about it because I've been using Ubuntu for 12 years and I have another problem with my computer and what I avoid is reinstalling the system because my computer is quite old. The last time I did the reinstallation, I could hardly find a DVD-Rom to start the ubuntu installation from disk, because my computer either doesn't have the ability to boot from a flash drive or something doesn't work, and this boot over disk was barely done.

---

### Post by Yellow Pasque on 2022-05-26
> **gale85 said:**
> After that I did everything that is written on that site 

You did everything written on that site? Which version of kdenlive are we troubleshooting? Did you install a PPA, Snap, or Flatpak? I'm confused..

---

### Post by gale85 on 2022-05-26
I don't know, I tried all the ways until it suddenly started working, but as far as I can see, when I start it from the console, it seems to be running via a snap. Here's the command exit
> 
Qt: Session management error: Could not open network socket
=== /// CANNOT ACCESS SPEECH DICTIONARIES FOLDER
profilePath from $MLT_PROFILES_PATH:  "/snap/kdenlive/48/usr/share/mlt-7/profiles/"
meltPath from KdenliveSetting::rendererPath:  "/snap/kdenlive/48/usr/share/mlt-7/profiles/"
Invalid metadata for  "avcolour_space"
Failed to parse "avcolour_space"
Invalid metadata for  "avcolor_space"
Failed to parse "avcolor_space"
Invalid metadata for  "avdeinterlace"
Failed to parse "avdeinterlace"
Invalid metadata for  "swscale"
Failed to parse "swscale"
Invalid metadata for  "swresample"
Failed to parse "swresample"
Invalid metadata for  "audiochannels"
Failed to parse "audiochannels"
Invalid metadata for  "audioconvert"
Failed to parse "audioconvert"
Invalid metadata for  "imageconvert"
Failed to parse "imageconvert"
Invalid metadata for  "jack"
Failed to parse "jack"
Invalid metadata for  "glsl.manager"
Failed to parse "glsl.manager"
Invalid metadata for  "movit.convert"
Failed to parse "movit.convert"
Invalid metadata for  "movit.crop"
Failed to parse "movit.crop"
Invalid metadata for  "movit.resample"
Failed to parse "movit.resample"
Invalid metadata for  "movit.resize"
Failed to parse "movit.resize"
Invalid metadata for  "telecide"
Failed to parse "telecide"
Invalid metadata for  "deinterlace"
Failed to parse "deinterlace"
plugin not available: "avfilter.acompressor"
plugin not available: "avfilter.aecho"
plugin not available: "avfilter.agate"
plugin not available: "audiolevelgraph"
plugin not available: "avfilter.atadenoise"
plugin not available: "avfilter.bwdif"
plugin not available: "avfilter.deblock"
plugin not available: "avfilter.dedot"
plugin not available: "avfilter.deflate"
plugin not available: "avfilter.derain"
plugin not available: "avfilter.doubleweave"
plugin not available: "avfilter.field"
plugin not available: "avfilter.framestep"
plugin not available: "avfilter.fspp"
plugin not available: "avfilter.graphmonitor"
plugin not available: "avfilter.hqdn3d"
plugin not available: "avfilter.inflate"
plugin not available: "avfilter.lagfun"
plugin not available: "avfilter.loudnorm"
plugin not available: "avfilter.random"
plugin not available: "avfilter.removegrain"
plugin not available: "avfilter.separatefields"
plugin not available: "avfilter.shuffleplanes"
plugin not available: "avfilter.sr"
plugin not available: "avfilter.tmix"
plugin not available: "avfilter.w3fdif"
plugin not available: "avfilter.weave"
plugin not available: "avfilter.yadif"
plugin not available: "frei0r.baltan"
plugin not available: "frei0r.bgsubtract0r"
plugin not available: "frei0r.bigsh0t_eq_mask"
plugin not available: "frei0r.bigsh0t_eq_to_rect"
plugin not available: "frei0r.bigsh0t_hemi_to_eq"
plugin not available: "frei0r.bigsh0t_rect_to_eq"
plugin not available: "frei0r.bigsh0t_stabilize_360"
plugin not available: "frei0r.bigsh0t_transform_360"
plugin not available: "frei0r.delay0r"
plugin not available: "frei0r.delaygrab"
plugin not available: "frei0r.facebl0r"
plugin not available: "frei0r.facedetect"
plugin not available: "frei0r.lightgraffiti"
plugin not available: "frei0r.lightgraffiti"
plugin not available: "frei0r.tehRoxx0r"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa.9354877"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "ladspa"
plugin not available: "movit.unsharp_mask"
plugin not available: "region"
plugin not available: "timewarp"
plugin not available: "region"
ALSA lib conf.c:4120:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
QObject::connect: No such signal QDBusAbstractInterface::DeviceAdded(QString)
QObject::connect: No such signal QDBusAbstractInterface::DeviceRemoved(QString)
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.438\" (uid=1000 pid=52425 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1279 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.438\" (uid=1000 pid=52425 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1279 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.438\" (uid=1000 pid=52425 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1279 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.438\" (uid=1000 pid=52425 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1279 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.438\" (uid=1000 pid=52425 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1279 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.438\" (uid=1000 pid=52425 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1279 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.438\" (uid=1000 pid=52425 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1279 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
kf.solid.backends.udisks2: Failed enumerating UDisks2 objects: "org.freedesktop.DBus.Error.AccessDenied" 
 "An AppArmor policy prevents this sender from sending this message to this recipient; type=\"method_call\", sender=\":1.438\" (uid=1000 pid=52425 comm=\"/snap/kdenlive/48/usr/bin/kdenlive \" label=\"snap.kdenlive.kdenlive (enforce)\") interface=\"org.freedesktop.DBus.Introspectable\" member=\"Introspect\" error name=\"(unset)\" requested_reply=\"0\" destination=\"org.freedesktop.UDisks2\" (uid=0 pid=1279 comm=\"/usr/libexec/udisks2/udisksd \" label=\"unconfined\")"
QObject::disconnect: Unexpected nullptr parameter
QObject::disconnect: Unexpected nullptr parameter
QObject::disconnect: Unexpected nullptr parameter
qrc:/qml/timeline.qml:2021:5: QML Connections: Implicitly defined onFoo properties in Connections are deprecated. Use this syntax instead: function onFoo(<arguments>) { ... }
=== REG FOCUS:  false


---

### Post by Yellow Pasque on 2022-05-26
My suggestion would be to get rid of everything except the the native apt/deb from the Ubuntu repository. I am not well-versed in snaps or Flatpacks, but I know others can you walk you through it.

---

### Post by gale85 on 2022-05-26
It's not a problem, I'll do anything just to make this work properly, the only thing I've already said is reinstalling the system, not because, as I've already mentioned, a bad computer

---

### Post by mIk3_08 on 2022-05-27
> **gale85 said:**
> It's not a problem, I'll do anything just to make this work properly, the only thing I've already said is reinstalling the system, not because, as I've already mentioned, a bad computer As I have mentioned to you in my previous reply to this thread. I prefer to use the previous version of kdenlive 21.12 But later than kdenlive version 4. I think its version 10 maybe. I forgot since I haven't use kdenlive for a quite a while now. But if you are not in a hurry there's a lot of solution that can fix your issue of Kdenlive its just that, we have just to wait to other here in the community that also encounter or have some idea about this kdenlive issue of yours. Or you maybe you need some other Best Linux video editor.  Just [Click Here]("https://www.lifewire.com/best-linux-video-editors-4176979"). Regards and Cheers

---

### Post by gale85 on 2022-05-28
I would prefer if the kdenlive can somehow be fixed because I'm used to it.

---

### Post by mIk3_08 on 2022-05-30
> **gale85 said:**
> I would prefer if the kdenlive can somehow be fixed because I'm used to it. 
I get your point. How about the ppa? Have you tested the Kdenive ppa in launchpad? Try it maybe it will help solve your issue.  Regards and Cheers.

---

### Post by gale85 on 2022-06-03
How do I check if it's a proper ppa so I don't delete kdenlive because I'm afraid it might accidentally fail again when reinstalling?

---

### Post by mIk3_08 on 2022-06-04
> **gale85 said:**
> How do I check if it's a proper ppa so I don't delete kdenlive because I'm afraid it might accidentally fail again when reinstalling? I can't guaranty you since I don't use kdenlive anymore but if you hesitate to try some of the ppa try any package manager. Regards and Cheers.

---

### Post by gale85 on 2022-06-05
I'm trying to install kdenlive myself, but nothing made me miss it again until I installed it via snap. Maybe let's try to install that older version just to work properly, I don't use this one again via snap where I can't use the maximize button

---

### Post by mIk3_08 on 2022-06-06
> **gale85 said:**
> I'm trying to install kdenlive myself, but nothing made me miss it again until I installed it via snap. Maybe let's try to install that older version just to work properly, I don't use this one again via snap where I can't use the maximize button
I don't know what is always to be an issue with snap just try another package manager like Flatpack. Don't worry everything has always a solution its just that it can't be found that easily. Just don't lose any hope. Regards and Cheers.

---

### Post by gale85 on 2022-06-06
How to install kdenlive via flatpack, I seem to have tried it via terminal but failed

---

### Post by deadflowr on 2022-06-06
> **gale85 said:**
> How to install kdenlive via flatpack, I seem to have tried it via terminal but failed

Follow the flatpak setup guide here: [https://flatpak.org/setup/Ubuntu]("https://flatpak.org/setup/Ubuntu")

And then run the commands at the bottom of the page shown here: [https://flathub.org/apps/details/org.kde.kdenlive]("https://flathub.org/apps/details/org.kde.kdenlive")

---

### Post by gale85 on 2022-06-07
I did that and downloaded the kdenlive flatpak file, the kdenlive window opened, I clicked open but nothing starts

---

### Post by gale85 on 2022-06-17
Just to let you know that kdenlive has suddenly started working normally with the fact that when I type in the kdenlive terminal it can be seen running via snap and then I still have the problem I already talked about (no maximize button) and when I click on the corresponding icon in the dockbar then opens normally. I don't know how this has improved, but it's important that it works, only if I could set it to open this one in the terminal when I type kdenlive, which works normally and not a snap

---

