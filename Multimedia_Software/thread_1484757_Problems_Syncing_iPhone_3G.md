---
title: "Problems Syncing iPhone 3G"
date: 2010-05-16
forum: Multimedia Software
---

### Post by Sumo74 on 2010-05-16
Ok I just got an iPhone 3G with Firmware version 3.1.3, and I running Ubuntu Lucid. The machine mounts and reads the phone, but in RhythmBox it will show the phone, but not allow me to add music to it. It just does nothing. I have not seen any error outputs, so I don't know what could be going on.

Then if I go into Nautilus and right click on a file and send it to the iPhone that way, it just sends it to the root of the iPhone and does not show up on the iPhone itself. (I have tried moving the files to different folders, and it was useless also).

---

### Post by Sumo74 on 2010-05-16
Sorry for the bump, but I have tried everything (Even downloading music from iTunes on the phone and seeing where it went, which unfortunately doesn't help much) I am leaving to go on the road to work tomorrow and I am in kind of a bind with my radio not working and only my iPhone for music.


Also Rhythmbox does not show the song I purchased on the iPhone, so I am not for sure what can be the issue.

---

### Post by vkcaspervk on 2010-05-16
Ive got the same issue, iPhone 3g 3.1.3. I can access it via Nautilus. Even play withthe new iphone tools. Nothing in rhythmbox. 


This is the debug output from rhythmbox when I plugin the iphone.

```

(14:44:16) [0xce3040] [uevent_cb] rb-removable-media-manager.c:591: add event for /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2.4 (bd8a)
(14:44:16) [0xce3040] [create_source_device_cb] rb-mtp-plugin.c:385: device 2-2.4 is supported through AFC, ignore
(14:44:16) [0xce3040] [uevent_cb] rb-removable-media-manager.c:591: add event for /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2.4/2-2.4:1.0 (0)
(14:44:16) [0xce3040] [create_source_device_cb] rb-mtp-plugin.c:391: can't get udev device number for device 2-2.4:1.0
(14:44:16) [0xce3040] [uevent_cb] rb-removable-media-manager.c:591: add event for /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2.4/2-2.4:4.0 (0)
(14:44:16) [0xce3040] [create_source_device_cb] rb-mtp-plugin.c:391: can't get udev device number for device 2-2.4:4.0
(14:44:16) [0xce3040] [uevent_cb] rb-removable-media-manager.c:591: remove event for /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2.4/2-2.4:1.0 (0)
(14:44:16) [0xce3040] [uevent_cb] rb-removable-media-manager.c:591: add event for /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2.4/2-2.4:4.2 (0)
(14:44:16) [0xce3040] [create_source_device_cb] rb-mtp-plugin.c:391: can't get udev device number for device 2-2.4:4.2
(14:44:16) [0xce3040] [uevent_cb] rb-removable-media-manager.c:591: add event for /sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2.4/2-2.4:4.1 (0)
(14:44:16) [0xce3040] [create_source_device_cb] rb-mtp-plugin.c:391: can't get udev device number for device 2-2.4:4.1
(14:44:19) [0xce3040] [dump_volume_identifiers] rb-removable-media-manager.c:664: uuid = 00000000000000000000000000000000000000
(14:44:19) [0xce3040] [rb_removable_media_manager_add_volume] rb-removable-media-manager.c:709: Unhandled media
(14:44:21) [0xce3040] [rhythmdb_mount_added_cb] rhythmdb-monitor.c:465: volume afc://00000000000000000000000000000000000000/ mounted
(14:44:21) [0xce3040] [rb_removable_media_manager_add_mount] rb-removable-media-manager.c:751: Unhandled media, no volume for mount
(14:44:21) [0xce3040] [rhythmdb_mount_added_cb] rhythmdb-monitor.c:465: volume afc://00000000000000000000000000000000000000/ mounted
(14:44:21) [0xce3040] [dump_volume_identifiers] rb-removable-media-manager.c:664: uuid = 00000000000000000000000000000000000000
(14:44:21) [0xce3040] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/ipod/ipod-init.ui' when searching for file 'ipod-init.ui' for plugin 'ipod'
(14:44:21) [0xce3040] [rb_removable_media_manager_add_mount] rb-removable-media-manager.c:785: Unhandled media

```

I changed the uuid just in case its traceable...

---

### Post by nj1n on 2010-05-16
Hy
Im not an iPhone - iPod suer.
I've read on ubuntu-it sopport forum that the problem was solved downloading the new version of some packages from SID's repository.
The packages are:
ifuse_1.0.0-1
libimobiledevice1_1.0.0.1
libimobiledevice-utils_1.0.0.1
libusbmuxd1_1.0.3-1
usbmuxd_1.0.3-1
i'll repeat , i'm not an user of this phones so i can't test this.
Hope helpfull, send report if OK
NJ1n

---

### Post by Sumo74 on 2010-05-16
> **nj1n said:**
> Hy
Im not an iPhone - iPod suer.
I've read on ubuntu-it sopport forum that the problem was solved downloading the new version of some packages from SID's repository.
The packages are:
ifuse_1.0.0-1
libimobiledevice1_1.0.0.1
libimobiledevice-utils_1.0.0.1
libusbmuxd1_1.0.3-1
usbmuxd_1.0.3-1
i'll repeat , i'm not an user of this phones so i can't test this.
Hope helpfull, send report if OK
NJ1n


Do you have the repository address? I will try to look it up myself, but I figured I would ask. Reason being, the Lucid Repository does not show those versions, and I have tried to compile the source myself, but I run into error after error

Ok I found the SID repository, updated all the packages, and still a no go.  So I am not for sure what happened.

---

### Post by Sumo74 on 2010-05-16
Bump for a solution

---

### Post by vkcaspervk on 2010-05-16
The thing is, its suppose to work "outta the box..."

Here is what I have installed, all up to date as per Synaptic.

ifuse - 0.9.7-1
libimobiledevice0 - 0.9.7-1ubuntu1
libimobiledevice-utils - 0.9.7-1ubuntu1
libusbmuxd1 - 1.0.2-1ubuntu2
usbmuxd - 1.0.2-1ubuntu2

---

### Post by Sumo74 on 2010-05-17
> **vkcaspervk said:**
> The thing is, its suppose to work "outta the box..."

Here is what I have installed, all up to date as per Synaptic.

ifuse - 0.9.7-1
libimobiledevice0 - 0.9.7-1ubuntu1
libimobiledevice-utils - 0.9.7-1ubuntu1
libusbmuxd1 - 1.0.2-1ubuntu2
usbmuxd - 1.0.2-1ubuntu2

I know, I don't know what could be going wrong with this

---

### Post by vkcaspervk on 2010-05-17
I love I can access the iphones drive now. Now if rhythmbox can join the show, it would be a party.
 
I fought the long nightmare of syncing the iphone with virtual box, finally getting the rules just right so it would do an OS update. Now if only I can get gtkpod or rhythmbox to see the dang thing... =\ 

i tried pointing gtkpod to the afc://blah/ and it didnt work either.

---

### Post by Zorael on 2010-05-17
When my iPhone just flat out refused to save the database and any songs I uploaded into it, I solved it by manually setting the Firewire GUID as described over on the (now sort of outdated) [wiki page](https://help.ubuntu.com/community/PortableDevices/iPhone#Retrieving%20and%20setting%20the%20Firewire%20GUID%20%28FirewireGuid%29).

Basically;
[list=1][*]Attach iPhone
[*]Mount to a directory using **ifuse**
[*]Move into the **iPod_Control/Device** directory of your mount
[*]Write Firewire GUID to the **SysInfo** file in there, retrievable by the following command.
```
sudo lsusb -v -d 05ac: | grep iSerial | awk '{print $3}' | cut -b1-16 | xargs printf "FirewireGuid: 0x%s\n"
```
[*]Unmount and reboot iPhone[/list]

So, basically;
```
$ mkdir iphone
$ ifuse iphone
$ sudo lsusb -v -d 05ac: | grep iSerial | awk '{print $3}' | cut -b1-16 | xargs printf "FirewireGuid: 0x%s\n" > iphone/iPod_Control/Device/SysInfo
$ fusermount -u iphone
```
And reboot the phone.

---

### Post by Sumo74 on 2010-05-17
Nope didn't work either. gtkPod can read the phone being present, but can't load it. It comes up with these errors:

Extended Info will not be used.
iPod Database Import Failed.

The extended info part sounds like the Sysinfoextended file, located in iTunes_Control/Device. So I don't know if that may help, or if it just leads to another problem.

---

### Post by vkcaspervk on 2010-05-17
After trying that code, 

```
sudo lsusb -v -d 05ac: | grep iSerial | awk '{print $3}' | cut -b1-16 | xargs printf "FirewireGuid: 0x%s\n" > iphone/iPod_Control/Device/SysInfo
bash: iphone/iPod_Control/Device/SysInfo: No such file or directory

```
iPod_Control folder doesnt even exist on my iphone. 

I am a little sceptical of randomly creating files or deleting files on the phone...

I think we are still missing something, its suppose to work out of the box, I can access all these files without ifuse and by using afc://6...3/ I just cant I figure out why other apps dont see it.

---

### Post by Flash858 on 2010-05-18
I can tell you my experience, and it is with iPod Touches, not iPhones. One has firmware 3.12, jail-broken, and firmware spoofed to 3.13. It mounts fine, I can ssh into it, copy files all day long, even upload an entire theme, and it shows up and works fine in Winterboard. It also mounts in Rhythmbox, and I can drag files to it, but they only show in Rhythmbox, or the file manager.

The other is running 3.13, is not jail-broken, and does indeed work entirely "out of the box" in Rhythmbox. It copies artwork automatically, and even puts podcasts WITH artwork (something iTunes only does occasionally... ;) in the podcast directory. I haven't tried an audiobook yet, but my guess is that it will work.

What I have noticed is that after the files are copied, it can take up to a minute, but then you will see the standard "sync in progress" on the device, and when it is finished, it is just as if you used iTunes (except that you don't feel dirty...).

Hope this helps someone...

---

### Post by vkcaspervk on 2010-05-18
Ya Ive tried on a fresh install, since I have 4 computers in here... All the same thing, i can access it with Nautilus, but rhythmbox doesnt see it, nor does banshee. =\ Dunno, maybe its the phone?

---

### Post by Sumo74 on 2010-05-18
Well that is weird thing. Rhythmbox sees it. The machine mounts it. Nautilus can navigate through it. It can even send files to it (Just not in the correct spot so the iPod app does not recognize the songs being there). But I cannot transfer songs to the iPhone through Rhythmbox or Amarok. Nothing seems to work, I am about to just to upgrade everything from the SID repository and hopes that can help. I am just glad I am on the road, and can use someone else's free Wifi to do it lol

---

### Post by Sumo74 on 2010-05-23
Anyone think of anything else? I have tried everything, even faking a .plist file to see if the phone would fall for it, and it didn't. I have tried everything from every source, search google til my eyes started bleeding, and nothing works.

---

### Post by bctechnzl on 2010-05-25
Where did you find the SID repository? Can you post the link?

---

### Post by Sumo74 on 2010-05-27
> **bctechnzl said:**
> Where did you find the SID repository? Can you post the link?


For the SID repo: [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian)

Well I got a new iPhone (wanted to the 3gs for the firmware update with the multitasking). And it seems to want to work, but nothing can Initialize it. Also Rythmbox now does not "see" the phone. I am at a lost now, even more than before.

---

### Post by asuastrophysics on 2011-01-12
I'm still having this problem. Anyone know of what to do? Everything worked fine with iOS 3.2, but now that I've upgraded to iOS 4.2.1, Rhythmbox will detect the iPhone, show that it's transferring tracks, but I can never find any of them in iPod.app.

---

