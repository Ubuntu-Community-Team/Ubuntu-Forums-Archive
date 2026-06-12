---
title: "Just a few problem i have already found in Maverick Meerkat"
date: 2010-06-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-05
The biggest problem i found is that it doesn't always recognize one of my partitions i noticed it from the start.
For some reason he have a problem mounting my sdb2 partition i tried using palimpsest to mount it and i get:

"Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, none is already mounted on none
mount failed"

But for some reason it did worked for a short time before and i need that partition to work properly. 

That was problem number 1 number 2 is that fglrx is not working but i'm sure you are aware of that i'm sure it want take long for a new fglrx to be 
release assuming that Maverick Meerkat is using x.server 1.75 and that there is support for 1.75 in the latest ati 10.05 driver.

Problem number 3 is with network manager i have two network cards one is on the mother board i use it for my home network and i manually set there manual ip 
192.168.137.1 and that is fine but my other card Realtek i can't use auto eth1 there and the dsl dialer meaing i can either connect to my Netvision isp or i can connect 
to auto eth1 and connect to my modem by using 10.0.0.138 and that is a big problem that i didn't had before.

Problem number 4 is very old and the problem is that in RTL environment it still doesn't auto arrange icons on desktop i'm hopping that you would fix it this time.

Problem number 5 i have a lot of problems with this command that i made does anybody know why?
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo aptitude install ubuntu-restricted-extras avidemux wireshark axel axel-kapt gnome-alsamixer amule p7zip-full p7zip-rar gparted startupmanager acpi gnome-device-manager apt-p2p mplayer smplayer gnome-mplayer wine human-theme x264 python python-gtk2 intltool gettext nfoview assogiate fusion-icon simple-ccsm emerald vlc cheese compiz subversion compiz-fusion-plugins-extra gmountiso rar apache2.2-bin libapache2-mod-dnssd git-core gimp w32codecs alsa-oss shutter faac gnome-themes-more faad flashplugin-nonfree gstreamer0.10-ffmpeg samba gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse git-core wine gstreamer0.10-plugins-ugly gshare gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs unrar && sudo aptitude install xfonts-terminus compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev x11proto-scrnsaver-dev libxss-dev libxslt1-dev libtool libgl1-mesa-dev and libglu1-mesa-dev 

```And it is possible that something in this command did something to my problem with the missing partition because when i installed 10.10 i didn't had this partition after updates i did and now after using this command i 
don't so maybe i removed something i shouldn't via this command or via ubuntu-tweak cleaner.

And that it for now i will continue updating this thread with more problems that i would found but at least this time i didn't had any problems with grub which is a major improvement for me.:)

---

### Post by luceerose on 2010-06-05
> **aviramof said:**
> The biggest problem i found is that it doesn't always recognize one of my partitions...

Just curious. Is the problem partition ext3/ext4/ntfs/... ?
& Extended or Primary ?

---

### Post by wojox on 2010-06-05
1. try running

```
sudo update-grub
```

5. See my site to install medibuntu. You need to use 10.04 for it to work

[Medibuntu]("http://wojox.homelinux.org/?p=12")

---

### Post by aviramof on 2010-06-05
> **larsenguitars said:**
> Just curious. Is the problem partition ext3/ext4/ntfs/... ?
& Extended or Primary ?

Ntfs primary partition.

[QUOTE=wojox;9413544]1. try running

```
sudo update-grub
```i don't understand what grub had something to do with the partition problem but one restart it's working fine and the other it's not.

---

### Post by ronacc on 2010-06-05
on your partition problem , When I did a fresh install of LUCID  to upgrade to Maverick when the repos opened I had the same thing . The install was to its own drive , that was the only install on it . It was formated using the installer partitioner this way , / ext4 , /home ext4 , swap . about every second boot it would stall saying /home was not ready or could not be found , a reboot usually would go normally although sometimes it took 2 or 3 reboots , and note that it did this both before and after the upgrade to maverick. After using that install for a couple of weeks I wiped that drive and formated it with a STAND ALONE GPARTED and installed a different distro there which has had no problem  since installed . I used the stand alone gparted to add 2 partitions ( primary ,ext4 ) to a different drive and installed Maverick there ( lucid then upgrade) and that install has no problems . I suspect that your "missing partition is the fault of the partitioner not maverick itself , over the years the partitioner in ubiquity has given me more grief during testing than anything else . Try redoing your maverick partitions with a stand alone gparted . It will mean a reinstall but this early on that should not cause too much pain .

edit: the "missing" partition was relly there , I could reliably mount it from a lucid or karmic install that are on a different drive every time I tried  .

---

### Post by taavikko on 2010-06-05
> **ronacc said:**
> Try redoing your maverick partitions with a stand alone gparted .

Just FYI, latest stable release has an bug that writes the partitions incorrectly in some cases.


Trying to seek the link... [http://gparted-forum.surf4.info/viewtopic.php?id=13777](http://gparted-forum.surf4.info/viewtopic.php?id=13777)

---

### Post by ronacc on 2010-06-05
@ taavikko  I normally use a stand alone gparted because I have had so many problems over the years with ubuntu's installer , I just got lazy that time . My stupid mistake .

---

### Post by taavikko on 2010-06-05
> **ronacc said:**
> @ taavikko  I normally use a stand alone gparted because I have had so many problems over the years with ubuntu's installer , I just got lazy that time . My stupid mistake .

I wasn't critisizing, just felt to notify about the bug in gparted which in return may cause ill effects.

One must use the tools that one needs and is best fitted in his/her demands.

He who isn't guilty of stupid mistakes, should cast the first stone...
(I was complaining one day about the errors in vdpau cause it didn't work... Forgot to install the libvdpau1 for it to work :) )

---

### Post by ronacc on 2010-06-05
I didn't think you were criticizing me , I was criticizing myself ,

---

### Post by aviramof on 2010-06-05
The partition in question is not the ubuntu partition the ubuntu partition is ext4 extended partition(i forgot to change it to primary when i created this partition)
the ntfs partition with the problem is an old one and is working very fine via windows 7 and also via ubuntu but in ubuntu one restart she's fine and the other she's
not there so it's something with ubuntu 10.10 not the partition itself.

---

### Post by cariboo on 2010-06-05
IF you are mounting your NTFS partion using the device label eg: /dev/sda1 try mounting it using UUID in fstab, I had a problem with device labels changing on each reboot until resorting to UUID to mount them. To find the UUID in a terinal type:

```
sudo blkid
```

the output should look something like this:

```
sudo blkid
[sudo] password for me: 
/dev/sda1: UUID="98407982-ed69-4691-b483-deecc3b342d1" TYPE="ext4" 
/dev/sda2: UUID="3a7058ef-fd9c-4d72-ad5d-6f169daf24a9" TYPE="swap" 
/dev/sda3: UUID="ffd3b758-e18a-4e1e-b9b3-6d8008a6672a" TYPE="ext4" 
/dev/sdb1: UUID="cbdde71e-13ce-4445-8dad-964c1443ebd1" TYPE="ext4" 
/dev/sdb3: UUID="178a305c-b7c5-4850-b4a4-0ef43ae6b92c" TYPE="ext4"
```

Then use the UUID in fstab:

```
# /home on Lucid
UUID=ffd3b758-e18a-4e1e-b9b3-6d8008a6672a /home/lucid	ext4	defaults	0  2
```

Change the mount point and partition type to suit your setup.

---

### Post by ronacc on 2010-06-05
that can be a pain because the way Ubuntu orders the drives is NOT the same as gparted orders the drives (eg what Ubuntu calls SDA is not the same drive that gparted calls SDA ) and neither is the same as the order shown in bios . When you have a complex system , mine is 6 drives and 7 installs spread across 18 partitions , the only way to keep track is to name the partitions ( eg lucid and lucidho(me) , mangy and mangyho(me) etc )

---

### Post by aviramof on 2010-06-05
This is what i have:
```
/dev/sda1: LABEL="Windows 7" UUID="DE047EA8047E8377" TYPE="ntfs" 
/dev/sda2: LABEL="M-WM-^SM-WM-^YM-WM-!M-WM-' M-WM-^^M-WM-'M-WM-^UM-WM-^^M-WM-^Y" UUID="58544AAE544A8F26" TYPE="ntfs" 
/dev/sda3: LABEL="M-WM-^SM-WM-^YM-WM-!M-WM-' M-WM-^^M-WM-'M-WM-^UM-WM-^^M-WM-^Y" UUID="EA9635979635656B" TYPE="ntfs" 
/dev/sdb1: LABEL="Windows Server 2008" UUID="54462E54462E36E0" TYPE="ntfs" 
/dev/sdb2: UUID="b9cc83b2-9fd5-40b7-bda7-6128ab25d1cd" TYPE="swap" 
/dev/sdb5: UUID="4c7c8708-222a-4f9e-9afb-41161aa7ba32" TYPE="ext4"
```

I also have another problem every restart the speaker icon is marked with red x meaning meaning mute and audio preference option doesn't work.

---

### Post by cariboo on 2010-06-05
Have a look [here]("http://ubuntuforums.org/showpost.php?p=9349048&postcount=10") to fix the sound problem.

---

### Post by aviramof on 2010-06-06
Well for now everything is looking fine i'v reinstalled ubuntu then i added compiz ppa and the fglrx ppa i found in another thread then coreavc ppa and mediabuntu ppa and all the non-free codecs and all the software from my command i just needed to shorten her to this
```
sudo apt-get install ubuntu-restricted-extras avidemux wireshark axel axel-kapt gnome-alsamixer amule p7zip-full p7zip-rar gparted startupmanager acpi gnome-device-manager apt-p2p mplayer smplayer gnome-mplayer wine human-theme x264 python python-gtk2 intltool gettext nfoview assogiate fusion-icon simple-ccsm emerald vlc cheese compiz subversion compiz-fusion-plugins-extra gmountiso rar apache2.2-bin libapache2-mod-dnssd git-core gimp w32codecs alsa-oss shutter faac gnome-themes-more faad flashplugin-nonfree git-core wine gstreamer0.10-plugins-ugly gshare gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs unrar xfonts-terminus 
```in order for her not to do any damages because for some reason 10.10 didn't liked the full command and always asked me to remove all sort of packages like pidgin and more.

And the sound problem is also solved now the only thing not working properly yet is the Plymouth logo meaning there is no Plymouth login but it's not a problem i'm sure that if it could be fix it would be fix in the future.:)

---

### Post by aviramof on 2010-06-06
So as far i can see for now all i need right now is a better file  manager with better desktop support a desktop support with auto arrange capability in an RTL Hebrew 
environment meaning that when i download files or create shortcuts on desktop they want pile up one  on top of the other.

[https://bugs.launchpad.net/nautilus/+bug/404363](https://bugs.launchpad.net/nautilus/+bug/404363)

And hopefully nautilus 3.0 would have more arranging files capabilities in the future.

And by the way why does the default option of the screen save is five minutes and locking the user automaticly? every time i install ubuntu i need to change it manually to 15 minutes and disable the 
auto lock option but in any case five minutes it's too short time for my taste and also it should be set at random screen save and not at empty screen because it could be a bit terrifying when you first 
see it and before you check because for several second you think that something happen to ubuntu and it's not making you feel very good to be honest.

> **cariboo907 said:**
> Have a look [here]("http://ubuntuforums.org/showpost.php?p=9349048&postcount=10") to fix the sound problem.

The problem was back so i tried it and i think it helped so thanks for the help but i would know better after the next restart.

---

