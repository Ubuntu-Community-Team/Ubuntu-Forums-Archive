---
title: "2 graphic programs won't start"
date: 2017-02-25
forum: Multimedia Software
---

### Post by Hankbonk on 2017-02-25
Dear forum members,

I have Lubuntu 16.04 LTS installed on my Desktop. Yesterday I found that (at least) 2 graphic programs do not start any more
when I click them from the Graphics menu : GIMP Image Editor and ImageMagick . How do I fix this ?

Henk Vanneste,
Belgium.

---

### Post by vasa1 on 2017-02-25
How exactly did you install Lubuntu on your computer? I'm asking because you had [another issue with "less"]("https://ubuntuforums.org/showthread.php?t=2352669") and most of the software on your system in that thread seemed to have ```
[installed,local]
``` which seems odd.

Only software not installed from standard repos should appear as "[installed,local]" when listed using```
apt list --installed | grep -E ',local\]$'
```

---

### Post by Hankbonk on 2017-02-25
Hello vasa1, 

thanks for your reply.

I installed Lubuntu 16.04 LTS from a usb-stick that I loaded under Lubuntu 14.04

And I did this again
```
henk@~$ apt list --installed | grep -E ',local\]$'

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


abiword/now 3.0.1-6ubuntu0.16.04.1 i386 [installed,local]
abiword-common/now 3.0.1-6ubuntu0.16.04.1 all [installed,local]
accountsservice/now 0.6.40-2ubuntu11.2 i386 [installed,local]
adwaita-icon-theme/now 3.18.0-2ubuntu3.1 all [installed,local]
adwaita-icon-theme-full/now 3.18.0-2ubuntu3.1 all [installed,local]
apparmor/now 2.10.95-0ubuntu2.2 i386 [installed,local]
audacious-plugins/now 3.6.2-2ubuntu1 i386 [installed,local]
audacious-plugins-data/now 3.6.2-2ubuntu1 all [installed,local]
base-files/now 9.4ubuntu4.2 i386 [installed,local]
bash/now 4.3-14ubuntu1.1 i386 [installed,local]
bash-completion/now 1:2.1-4.2ubuntu1.1 all [installed,local]
bsdutils/now 1:2.27.1-6ubuntu3.1 i386 [installed,local]
command-not-found/now 0.3ubuntu16.04.2 all [installed,local]
command-not-found-data/now 0.3ubuntu16.04.2 i386 [installed,local]
console-setup/now 1.108ubuntu15.2 all [installed,local]
console-setup-linux/now 1.108ubuntu15.2 all [installed,local]
dh-python/now 2.20151103ubuntu1.1 all [installed,local]
dmidecode/now 3.0-2ubuntu0.1 i386 [installed,local]
dpkg/now 1.18.4ubuntu1.1 i386 [installed,local]
fonts-noto-cjk/now 1:1.004+repack2-1~ubuntu1 all [installed,local]
fuse/now 2.9.4-1ubuntu3.1 i386 [installed,local]
gir1.2-gtk-3.0/now 3.18.9-1ubuntu3.1 i386 [installed,local]
gir1.2-packagekitglib-1.0/now 0.8.17-4ubuntu6~gcc5.4ubuntu1.1 i386 [installed,local]
gir1.2-unity-5.0/now 7.1.4+16.04.20160701-0ubuntu1 i386 [installed,local]
glib-networking/now 2.48.2-1~ubuntu16.04.1 i386 [installed,local]
glib-networking-common/now 2.48.2-1~ubuntu16.04.1 all [installed,local]
glib-networking-services/now 2.48.2-1~ubuntu16.04.1 i386 [installed,local]
grep/now 2.25-1~16.04.1 i386 [installed,local]
grub-common/now 2.02~beta2-36ubuntu3.2 i386 [installed,local]
grub-pc/now 2.02~beta2-36ubuntu3.2 i386 [installed,local]
grub-pc-bin/now 2.02~beta2-36ubuntu3.2 i386 [installed,local]
grub2-common/now 2.02~beta2-36ubuntu3.2 i386 [installed,local]
gstreamer1.0-libav/now 1.8.2-1~ubuntu1 i386 [installed,local]
gstreamer1.0-plugins-ugly/now 1.8.2-1ubuntu0.1 i386 [installed,local]
gstreamer1.0-plugins-ugly-amr/now 1.8.2-1ubuntu0.1 i386 [installed,local]
gtk2-engines-murrine/now 0.98.2-0ubuntu2.2 i386 [installed,local]
gvfs/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
gvfs-backends/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
gvfs-common/now 1.28.2-1ubuntu1~16.04.1 all [installed,local]
gvfs-daemons/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
gvfs-fuse/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
gvfs-libs/now 1.28.2-1ubuntu1~16.04.1 i386 [installed,local]
hunspell-en-au/now 1:5.1.0-1ubuntu2.2 all [installed,local]
hunspell-en-ca/now 1:5.1.0-1ubuntu2.2 all [installed,local]
hunspell-en-gb/now 1:5.1.0-1ubuntu2.2 all [installed,local]
hunspell-en-za/now 1:5.1.0-1ubuntu2.2 all [installed,local]
hunspell-nl/now 1:5.1.0-1ubuntu2.2 all [installed,local]
init/now 1.29ubuntu2 i386 [installed,local]
init-system-helpers/now 1.29ubuntu2 all [installed,local]
initramfs-tools/now 0.122ubuntu8.1 all [installed,local]
initramfs-tools-bin/now 0.122ubuntu8.1 i386 [installed,local]
initramfs-tools-core/now 0.122ubuntu8.1 all [installed,local]
isc-dhcp-client/now 4.3.3-5ubuntu12.1 i386 [installed,local]
isc-dhcp-common/now 4.3.3-5ubuntu12.1 i386 [installed,local]
keyboard-configuration/now 1.108ubuntu15.2 all [installed,local]
klibc-utils/now 2.0.4-8ubuntu1.16.04.1 i386 [installed,local]
language-pack-de/now 1:16.04+20160627 all [installed,local]
language-pack-de-base/now 1:16.04+20160627 all [installed,local]
language-pack-en/now 1:16.04+20160627 all [installed,local]
language-pack-en-base/now 1:16.04+20160627 all [installed,local]
language-pack-fr/now 1:16.04+20160627 all [installed,local]
language-pack-fr-base/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-de/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-de-base/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-en/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-en-base/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-fr/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-fr-base/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-nl/now 1:16.04+20160627 all [installed,local]
language-pack-gnome-nl-base/now 1:16.04+20160627 all [installed,local]
language-pack-nl/now 1:16.04+20160627 all [installed,local]
language-pack-nl-base/now 1:16.04+20160627 all [installed,local]
language-selector-common/now 0.165.4 all [installed,local]
language-selector-gnome/now 0.165.4 all [installed,local]
less/now 481-2.1ubuntu0.1 i386 [installed,local]
libabiword-3.0/now 3.0.1-6ubuntu0.16.04.1 i386 [installed,local]
libaccountsservice0/now 0.6.40-2ubuntu11.2 i386 [installed,local]
libapparmor-perl/now 2.10.95-0ubuntu2.2 i386 [installed,local]
libapparmor1/now 2.10.95-0ubuntu2.2 i386 [installed,local]
libblkid1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libboost-filesystem1.58.0/now 1.58.0+dfsg-5ubuntu3.1 i386 [installed,local]
libboost-system1.58.0/now 1.58.0+dfsg-5ubuntu3.1 i386 [installed,local]
libcupsfilters1/now 1.8.3-2ubuntu3.1 i386 [installed,local]
libdrm-amdgpu1/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdrm-intel1/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdrm-nouveau2/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdrm-radeon1/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdrm2/now 2.4.67-1ubuntu0.16.04.2 i386 [installed,local]
libdvdcss-dev/now 1.4.0-1~local i386 [installed,local]
libdvdcss2/now 1.4.0-1~local i386 [installed,local]
libegl1-mesa/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libfdisk1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libfm-data/now 1.2.4-1ubuntu1.1 all [installed,local]
libfm-extra4/now 1.2.4-1ubuntu1.1 i386 [installed,local]
libfm-gtk-data/now 1.2.4-1ubuntu1.1 all [installed,local]
libfm-gtk4/now 1.2.4-1ubuntu1.1 i386 [installed,local]
libfm-modules/now 1.2.4-1ubuntu1.1 i386 [installed,local]
libfm4/now 1.2.4-1ubuntu1.1 i386 [installed,local]
libfuse2/now 2.9.4-1ubuntu3.1 i386 [installed,local]
libgbm1/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libgif7/now 5.1.4-0.3~16.04 i386 [installed,local]
libgl1-mesa-dri/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libgl1-mesa-glx/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libglapi-mesa/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libglib2.0-0/now 2.48.1-1~ubuntu16.04.1 i386 [installed,local]
libglib2.0-bin/now 2.48.1-1~ubuntu16.04.1 i386 [installed,local]
libglib2.0-data/now 2.48.1-1~ubuntu16.04.1 all [installed,local]
libgstreamer1.0-0/now 1.8.2-1~ubuntu1 i386 [installed,local]
libgtk-3-0/now 3.18.9-1ubuntu3.1 i386 [installed,local]
libgtk-3-bin/now 3.18.9-1ubuntu3.1 i386 [installed,local]
libgtk-3-common/now 3.18.9-1ubuntu3.1 all [installed,local]
libklibc/now 2.0.4-8ubuntu1.16.04.1 i386 [installed,local]
libldap-2.4-2/now 2.4.42+dfsg-2ubuntu3.1 i386 [installed,local]
liblightdm-gobject-1-0/now 1.18.2-0ubuntu2 i386 [installed,local]
libllvm3.8/now 1:3.8-2ubuntu4 i386 [installed,local]
libmount1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libnautilus-extension1a/now 1:3.18.4.is.3.14.3-0ubuntu5 i386 [installed,local]
libnm0/now 1.2.0-0ubuntu0.16.04.3 i386 [installed,local]
libnma-common/now 1.2.0-0ubuntu0.16.04.4 all [installed,local]
libnma0/now 1.2.0-0ubuntu0.16.04.4 i386 [installed,local]
libosmesa6/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libp11-kit0/now 0.23.2-5~ubuntu16.04.1 i386 [installed,local]
libpackagekit-glib2-16/now 0.8.17-4ubuntu6~gcc5.4ubuntu1.1 i386 [installed,local]
libplymouth4/now 0.9.2-3ubuntu13.1 i386 [installed,local]
libpoppler-glib8/now 0.41.0-0ubuntu1.1 i386 [installed,local]
libpoppler58/now 0.41.0-0ubuntu1.1 i386 [installed,local]
libsmartcols1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libunity-protocol-private0/now 7.1.4+16.04.20160701-0ubuntu1 i386 [installed,local]
libunity-scopes-json-def-desktop/now 7.1.4+16.04.20160701-0ubuntu1 all [installed,local]
libunity9/now 7.1.4+16.04.20160701-0ubuntu1 i386 [installed,local]
libupower-glib3/now 0.99.4-2ubuntu0.3 i386 [installed,local]
libuuid1/now 2.27.1-6ubuntu3.1 i386 [installed,local]
libwayland-egl1-mesa/now 11.2.0-1ubuntu2.2 i386 [installed,local]
libwhoopsie0/now 0.2.52.1 i386 [installed,local]
libwnck-common/now 1:2.30.7-5ubuntu1.1 all [installed,local]
libwnck22/now 1:2.30.7-5ubuntu1.1 i386 [installed,local]
libxatracker2/now 11.2.0-1ubuntu2.2 i386 [installed,local]
lightdm/now 1.18.2-0ubuntu2 i386 [installed,local]
lsb-base/now 9.20160110ubuntu0.2 all [installed,local]
lsb-release/now 9.20160110ubuntu0.2 all [installed,local]
lshw/now 02.17-1.1ubuntu3.2 i386 [installed,local]
lubuntu-artwork/now 0.61.1 all [installed,local]
lubuntu-artwork-16-04/now 0.61.1 all [installed,local]
lubuntu-core/now 0.65.1 i386 [installed,local]
lubuntu-icon-theme/now 0.61.1 all [installed,local]
lubuntu-lxpanel-icons/now 0.61.1 all [installed,local]
lxshortcut/now 1.2.4-1ubuntu1.1 i386 [installed,local]
mount/now 2.27.1-6ubuntu3.1 i386 [installed,local]
mplayer/now 2:1.2.1-1ubuntu1 i386 [installed,local]
mtools/now 4.0.18-2ubuntu0.16.04 i386 [installed,local]
mtr-tiny/now 0.86-1ubuntu0.1 i386 [installed,local]
network-manager/now 1.2.0-0ubuntu0.16.04.3 i386 [installed,local]
network-manager-gnome/now 1.2.0-0ubuntu0.16.04.4 i386 [installed,local]
p11-kit/now 0.23.2-5~ubuntu16.04.1 i386 [installed,local]
p11-kit-modules/now 0.23.2-5~ubuntu16.04.1 i386 [installed,local]
plymouth/now 0.9.2-3ubuntu13.1 i386 [installed,local]
plymouth-label/now 0.9.2-3ubuntu13.1 i386 [installed,local]
plymouth-theme-lubuntu-logo/now 0.61.1 all [installed,local]
plymouth-theme-lubuntu-text/now 0.61.1 all [installed,local]
plymouth-theme-ubuntu-text/now 0.9.2-3ubuntu13.1 i386 [installed,local]
python3-commandnotfound/now 0.3ubuntu16.04.2 all [installed,local]
python3-distupgrade/now 1:16.04.16 all [installed,local]
python3-software-properties/now 0.96.20.4 all [installed,local]
python3-urllib3/now 1.13.1-2ubuntu0.16.04.1 all [installed,local]
shared-mime-info/now 1.5-2ubuntu0.1 i386 [installed,local]
software-properties-common/now 0.96.20.4 all [installed,local]
software-properties-gtk/now 0.96.20.4 all [installed,local]
sudo/now 1.8.16-0ubuntu1.2 i386 [installed,local]
ubuntu-drivers-common/now 1:0.4.17.1 i386 [installed,local]
ubuntu-mono/now 14.04+16.04.20160804-0ubuntu1 all [installed,local]
ubuntu-release-upgrader-core/now 1:16.04.16 all [installed,local]
ubuntu-release-upgrader-gtk/now 1:16.04.16 all [installed,local]
update-notifier/now 3.168.1 i386 [installed,local]
update-notifier-common/now 3.168.1 all [installed,local]
upower/now 0.99.4-2ubuntu0.3 i386 [installed,local]
util-linux/now 2.27.1-6ubuntu3.1 i386 [installed,local]
uuid-runtime/now 2.27.1-6ubuntu3.1 i386 [installed,local]
whoopsie/now 0.2.52.1 i386 [installed,local]
xinit/now 1.3.4-3ubuntu0.1 i386 [installed,local]
xserver-common/now 2:1.18.3-1ubuntu2.3 all [installed,local]
xserver-xorg-core/now 2:1.18.3-1ubuntu2.3 i386 [installed,local]
xserver-xorg-video-intel/now 2:2.99.917+git20160325-1ubuntu1.1 i386 [installed,local]



```

---

### Post by vasa1 on 2017-02-25
Please post the complete output of```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by Hankbonk on 2017-02-25
```
henk@~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb http://be.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://be.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://be.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list:deb http://be.archive.ubuntu.com/ubuntu/ xenial-backports main restricted multiverse universe
/etc/apt/sources.list.d/fkrull-ubuntu-deadsnakes-xenial.list:deb http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu xenial main
/etc/apt/sources.list.d/fkrull-ubuntu-deadsnakes-xenial.list.save:deb http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu xenial main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main



```

---

### Post by ajgreeny on 2017-02-25
Interesting!
Go to **software-sources ->update** tab and look to see if the middle of the three tick boxes, ie xenial-updates, is selected as you appear to have no xenial-updates repositories showing in your list.

---

### Post by Hankbonk on 2017-02-25
my DISTRO is [COLOR=#000000]Lubuntu 16.04-32bit,
but I found the xenial-updates unticked, so I ticked it (had to enter my password)
and closed that .

I also did an
```
apt-get update
```

Was that enough  ?
[/COLOR]:confused:

---

### Post by cariboo on 2017-02-26
Open a terminal and type:

```
gimp
```

and post the error messages you see.

---

### Post by Hankbonk on 2017-02-26
Hi cariboo,

gimp gives nothing of output at all in a terminal.

---

### Post by vasa1 on 2017-02-26
> **Hankbonk said:**
> Dear forum members,

I have Lubuntu 16.04 LTS installed on my Desktop. Yesterday I found that (at least) 2 graphic programs do not start any more
when I click them from the Graphics menu : GIMP Image Editor and ImageMagick . How do I fix this ?

Henk Vanneste,
Belgium.Why do you say "(at least) 2 graphic programs"? Which are the others?

Please post the complete output, including the actual commands, of```
sudo apt-get update
``` and ```
sudo apt-get upgrade
```

---

### Post by Hankbonk on 2017-02-26
```
henk@~$ sudo apt-get update[sudo] password for henk: 
Hit:1 http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu xenial InRelease
Hit:2 http://be.archive.ubuntu.com/ubuntu xenial InRelease                                        
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease                                        
Hit:4 http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial InRelease                           
Get:5 http://be.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                     
Get:6 http://be.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                       
Get:7 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]          
Fetched 306 kB in 1s (214 kB/s)                              
Reading package lists... Done



```

the output of ```
sudo apt-get upgrade
```
was so extensive, that I could not copy it all, it asked me to continue
on which I answered yes. Then I rebooted the system to see if anything was changed,
but it was still the same : No GIMP nor ImageMagick that works.

---

### Post by vasa1 on 2017-02-26
Re. Imagemagick, please open a terminal and run```
/usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/display
```and let us know what happens.

---

### Post by vasa1 on 2017-02-26
Re. gimp, please post the output of ```
apt-cache policy gimp
```and```
apt list --installed | grep -i gimp
```

---

### Post by Hankbonk on 2017-02-26
I managed to reinstall GIMP from Synaptic Package Manager !

I tried it for ImageMagick, but that did not work, it still doesn't start.

---

### Post by Hankbonk on 2017-08-28
ImageMagick still does not work, but I forgot to do this :

```
henk@:~$ /usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/display
bash: /usr/lib/x86_64-linux-gnu/ImageMagick-6.8.9/bin-Q16/display: No such file or directory

```

---

### Post by Hankbonk on 2017-08-28
I am fed up with this Imagemagick that doesn't start...

I removed it from my system and my applications menu !

Now I will mark this thread as solved .

:)    ):P

---

### Post by QIII on 2017-08-28
Hello!

Marking this thread as "Solved" will confuse those looking for a solution here and finding none.  I've changed it back.

Cheers!

---

### Post by mc4man on 2017-08-29
It would seem the OP was on an i386 install so that imagemagick command wouldn't work. Probably better to just use the bin file
```
display-im6
```

---

