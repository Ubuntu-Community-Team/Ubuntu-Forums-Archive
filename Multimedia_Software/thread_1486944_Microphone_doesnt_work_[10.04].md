---
title: "Microphone doesnt work [10.04]"
date: 2010-05-18
forum: Multimedia Software
---

### Post by Wandang on 2010-05-18
Hello folks.

as header says my microphone doesnt work at all.
after reading several threads it still wont work.

i would appreciate if any1 could help me out.

```
lspci:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
06:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 9500M GS] (rev a1)

```
```
sudo lshw -C sound:
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:30 memory:f8ef8000-f8efbfff

```

and the alsa-info script:
[http://www.alsa-project.org/db/?f=3897aecbff8cb0f7e4ae66a5dcf0aa6b6a29f973](http://www.alsa-project.org/db/?f=3897aecbff8cb0f7e4ae66a5dcf0aa6b6a29f973)

[IMG]http://www.ubuntu-forum.de/index.php?page=Attachment&attachmentID=5279&h=36f5ba35123704ff5ad53723a086e9f80f9b2ab0[/IMG]

[IMG]http://www.ubuntu-forum.de/index.php?page=Attachment&attachmentID=5280&h=fa9eb366e5119124a92ebfa6f0ddb545d82a688a[/IMG]

[IMG]http://www.ubuntu-forum.de/index.php?page=Attachment&attachmentID=5281&h=baf2999218cbd7ce858c60654bb183e3c07ab94a[/IMG]

[IMG]http://www.ubuntu-forum.de/index.php?page=Attachment&attachmentID=5278&h=e9f2422269d7eadeb618e19bacd3d0d5e0f76af4[/IMG]


greetz Wandang

---

### Post by lidex on 2010-05-20
I see you've done some tweaking. Remove the custom entry from alsa-base.conf:
```
options snd-hda-intel model=targa-2ch-dig
```
Replace with:
```
options snd-hda-intel model=targa-dig
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1

```
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Save. Close. Reboot. Check your levels in alsamixer.

---

### Post by Wandang on 2010-05-20
i didnt change alsa-base.config

instead i created the new file hda_intel.conf

ill delete that file and put ur suggestions into the alsa-base.conf.

if that wont work i put ur code into hda_intel.conf (then recreated)?

ill try.

/€: didnt work. maybe i messed with the alsamixer?
cannot find the error :/
added a actual picture as attachment

---

### Post by lidex on 2010-05-20
Stay away from 'hda_intel.conf' for now. Update your alsa to 1.0.23 via the link in my sig. After check 'Edit>SoundCard Properties' in gnome-alsamixer to make sure elements are enabled.

---

### Post by Wandang on 2010-05-20
> **lidex said:**
> Stay away from 'hda_intel.conf' for now. Update your alsa to 1.0.23 via the link in my sig. After check 'Edit>SoundCard Properties' in gnome-alsamixer to make sure elements are enabled.

i will (this will be the third time... first 2 caused me more trouble then fixes)
hopefully this time the upgrade wont kill my sound again^^

/&#8364;: update done... now i dont have any sounds in ts3. rythmsound still works.
all elements under SoundCard Properties are enabled....

greetz

---

### Post by lidex on 2010-05-20
What is ts3? You removed file hda_intel.conf, correct? And added lines to alsa-base.conf?
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by Wandang on 2010-05-21
sure. ts3 = teamspeak3 , an mumble alternative (voice over ip program)

```
wandang@wandang:~$ uname -a
Linux wandang 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
wandang@wandang:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC1200 Analog [ALC1200 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC1200 Digital [ALC1200 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
wandang@wandang:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on May 18 2010 for kernel 2.6.32-22-generic (SMP).
wandang@wandang:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC1200

```oh i see that the update went wrong.:(
ill try it again.

/&#8364;: again the update went wrong. still having 1.0.22.1 :/ (thats the first time it didnt go well)

---

### Post by lidex on 2010-05-21
If you have alsa backports installed, uninstall it and try the update again. For some reason backports overrides it.

---

### Post by Wandang on 2010-05-21
i'm not aware of having any backports.
there is no entry in my software sources containing backport in it.

greetz
thank you very much for taking ur time to help me:)

if it helps, here is my sources.list:
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://de.archive.ubuntu.com/ubuntu/ lucid main restricted universe
deb-src http://de.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe
deb-src http://de.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://de.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://orniere-du-globe.net/debian ./
deb http://ppa.launchpad.net/jcfp/ppa/ubuntu lucid main
```

---

### Post by lidex on 2010-05-21
Look in synaptic for this:
```
linux-backports-modules-alsa-lucid-generic
``` which is the metapackage. There would be one more package with an actual kernel version number. If there remove them both.

---

### Post by Wandang on 2010-05-21
checked it, nothing containing backport installed.

now my firefox freezes after 2 sec when opening flashvideos.
after that no sound works. nor firefox nor rythm player....
only restart fixes this until i try to see a flashvideo again...

/&#8364;: update: firefox doesnt freeze anymore. if rythm is used playing music flashstreams wont play music and viseversa.
instead flashstream-sound is lowered to 0 (the streamcontroller is on mute)
/&#8364;: the program who uses sound first has sound. any other program trying to use it while its alrdy used doesnt have sound.
like pidgin, teamspeak, firefox, rythm, etc...

/&#8364;: i would appreciate if i wont be left behind in the middle of the process.:)

greetz wandang

---

### Post by Wandang on 2010-05-25
im not sure if pushes are allowed cuz their is no info in the forumrules.

bump^^"

---

### Post by lidex on 2010-05-25
Can you run the alsa-info script again please?

---

### Post by Wandang on 2010-05-26
sure thx for ur help again
[http://www.alsa-project.org/db/?f=031ab962c7f4884eb6c615d823b3a8b72ee44126](http://www.alsa-project.org/db/?f=031ab962c7f4884eb6c615d823b3a8b72ee44126)

---

### Post by lidex on 2010-05-26
If you have installed alsa backports, uninstall it. Now use the alsa-upgrade link in my sig to update your alsa driver.

---

### Post by Wandang on 2010-05-26
> **lidex said:**
> If you have alsa backports installed, uninstall it  and try the update again. For some reason backports overrides  it.


u posted that alrdy^^"
i dont have any backports installed nor did an update help me out....:P

---

### Post by lidex on 2010-05-26
> **Wandang said:**
> u posted that alrdy^^"
i dont have any backports installed nor did an update help me out....:P

It still hasn't updated properly. 
> i didnt change alsa-base.config

instead i created the new file hda_intel.conf

The one thing that jumps out at me is that file you created (above). Did you remove it?

---

### Post by Wandang on 2010-05-27
> **lidex said:**
> It still hasn't updated properly. 

The one thing that jumps out at me is that file you created (above). Did you remove it?

y i did...
is there a way to remove alsa,(reinstall it) and the do the update?

i did follow this instructions: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

but it still isnt updated... :(

/&#8364;: if i follow #17 of the above link i get 1.0.23 with the cat command. but then all my sound is killed as posted in #28 :/
ive undone the changes and now im back at the start (cannot upgrade)

---

