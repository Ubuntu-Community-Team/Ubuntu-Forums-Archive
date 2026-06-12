---
title: "Alsa mixer doesn't install"
date: 2006-06-18
forum: Multimedia &amp; Video
---

### Post by matjaz_pirnovar on 2006-06-18
I have Dapper for a week now, but yesterday sound suddenly stopped working. When I turn on the computer, default sound setting is MUTE.

So I wanted to install Gnome alsa mixer to change the "defaul MUTE". But it doesn't want to run after installation. I get the icon in Applications/ Sound&Video but when I open it, window is empty with File and Help tollboxes at the top.

When I try to open it in File -> Preferences it reports an error (The device quitted unexpectedly. Please report the bug to the developers...) and the following bug report is:

Backtrace was generated from '/usr/bin/gnome-alsamixer'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1223436064 (LWP 734]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0 0xffffe410 in __kernel_vsyscall ()
#1 0xb74bd463 in __waitpid_nocancel ()
from /lib/tls/i686/cmov/libpthread.so.0
#2 0xb7f728e6 in libgnomeui_module_info_get ()
from /usr/lib/libgnomeui-2.so.0
#3 <signal handler called>
#4 0x0804cae1 in ?? ()
#5 0x080a0d20 in ?? ()
#6 0x082965ac in ?? ()
#7 0xbf9c8428 in ?? ()
#8 0x08051366 in ?? ()
#9 0x00000000 in ?? ()

Thread 1 (Thread -1223436064 (LWP 734):
#0 0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1 0xb74bd463 in __waitpid_nocancel ()
from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2 0xb7f728e6 in libgnomeui_module_info_get ()
from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3 <signal handler called>
No symbol table info available.
#4 0x0804cae1 in ?? ()
No symbol table info available.
#5 0x080a0d20 in ?? ()
No symbol table info available.
#6 0x082965ac in ?? ()
No symbol table info available.
#7 0xbf9c8428 in ?? ()
No symbol table info available.
#8 0x08051366 in ?? ()
No symbol table info available.
#9 0x00000000 in ?? ()
No symbol table info available.
#0 0xffffe410 in __kernel_vsyscall ()

The Bug Buddy opens and suggests to report the 'bug'. Have a funny feeling that content of the mixer is somehow empty...
Sound and video devices run, but there is no sound. And when I run Mplayer it says 'no sound. It 'couldn't be initiated'

Any clues?  The repository has no broken packages.

Appreciate help.

Thanks.

M

---

### Post by matjaz_pirnovar on 2006-06-20
Hi,

I'm really getting fed up (sorry).

Any ideas why Alsa mixer would have crashed? Any similar experiences? I'm trying to report it as a crash-bug (but is it related?)

Sound is set on MUTE by default when I turn on the computer. I would need alsa to untick the MUTE.

ANY direction REALLY appreciated.

:confused:  :) 

Matjaz

---

### Post by matjaz_pirnovar on 2006-06-20
I typed "ALSAMIXER" in terminal and it came out with this:

matjaz@cpc5-cbly1-0-0-cust771Matjaz:~$ alsamixer
ALSA lib conf.c:1592:(snd_config_load1) _toplevel_:29:1:Unexpected char
ALSA lib conf.c:2837:(snd_config_hook_load) /etc/asound.conf may be old or corru pted: consider to remove or fix it
ALSA lib conf.c:2700:(snd_config_hooks_call) function snd_config_hook_load retur ned error: Invalid argument
ALSA lib conf.c:3066:(snd_config_update_r) hooks failed, removing configuration

alsamixer: function snd_ctl_open failed for default: Invalid argument
matjaz@cpc5-cbly1-0-0-cust771Matjaz:~$

I did remove Alsa mixer - which btw didn't want to open (see previous posting). But I get the result above (currupt?).

What am I suppose to do?? Could it be that there is some leftover of the file or similar? (help)

Please hackers I need your coments, have been without the sound almost a week now!! Really appreciate.

Thanks

---

### Post by dixonstalbert on 2006-06-20
hi matjaz

I am wondering if there is a way you can rule out a hardware failure. 

do you have another OS loaded that you can test your sound system?

have you checked kernel.log for errors  (System > Administration > System Log)

maybe check lsmod to see if sound drivers loaded and if there is error message

---

### Post by matjaz_pirnovar on 2006-06-20
Hi dixonstalbert,

Firstly - thanks for help  :)

I don't use dual boot, I only use Ubuntu on my laptop. Sound did work properly till week ago.

When I type i nterminal lsmod I get info below. Can you see smth irregular about the sound?

matjaz@cpc5-cbly1-0-0-cust771Matjaz:~$ lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
i915                   20608  1
drm                    73236  2 i915
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ipv6                  265728  8
dm_mod                 58936  1
af_packet              22920  2
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
pcmcia                 40508  0
joydev                 10048  0
tsdev                   8000  0
via_rhine              23940  0
mii                     5888  1 via_rhine
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           33692  1
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
pcspkr                  2180  0
snd_pcm_oss            53664  0
snd_mixer_oss          18688  2 snd_pcm_oss
usbhid                 39904  0
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
psmouse                36100  0
serio_raw               7300  0
rtc                    13492  0
snd                    55268  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  4
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
matjaz@cpc5-cbly1-0-0-cust771Matjaz:~$

I checked kern.log. No errors signs. Can you advise me what eaxctly I should look for at kern.log?

The funny thing is: I read the thread on how to get the sound back. It's about installing ALSA mixer and unticking the MUTE. But the problem is that alsa is not working properly here.

I don't hink the hardware is damaged. It worked excellent till recently.

???

Regards,

Matjaz

---

### Post by dixonstalbert on 2006-06-20
I compared your lsmod to mine and could not find a problem. 

Have you tried going into synaptic package manager and selecting alsa-base and marking it for complete removal then reinstalling it?

also have you tried going into mplayer preferences > audio and tried different drivers to see if anything else works?

---

### Post by dixonstalbert on 2006-06-20
I was able to get gnome-mixer to crash on loading with 'inform developers message' by installing (with synaptic package manager) a bunch of stuff in the repositories that I found searching for 'alsa'. 

(I have been experimenting to see why my Realplayer10 has no sound but mplayer vlc, xmms work without a problem)

I found if I chose 'alsa-base'  and gnome-alsamixer in synaptic package manager and chose completely remove,  did this, then re-installed them plus 'ubuntu-minimal' (*** if you completely remove alsa-base, it also removes ubuntu-minimal which you probably need to have a bootable system- dont forget to reinstall it  #-o ), I got my alsa mixer up and running again.
 
see if this works for you

---

### Post by matjaz_pirnovar on 2006-06-21
Thanks  :)

But it still doesn't work. Completely removing and reinstalling didn't change anything unfortunatelly.

I have ALSA mixer version 9.3.6. or something, but I saw some poeple here posting about version 1.1.0.1. or similar - starting with 1.... 
I checked on Google and 9.3.6 (something like that) is the latest version.

I find really suspicious comments in the terminal about "corrupted..." after i type "alsamixer".

Do you think it's a hardware failure?

I'm tempted to completely reinstall Dapper again (although this may take some time to get CD via post). I wouldn't want to da that, I prefer to fix the problem.

Did anyone else had alsamixer crash?????

Appreciate further help.

Matjaz

---

### Post by matjaz_pirnovar on 2006-06-21
What did happen a few days ago is that I played with repositories a bit and accidentally deleted Ubuntu 5.10 and Ubuntu 5.04 repositories when I was trying to change repositories from "officially supported" to "universe". 

Since then I think I got a note or two about something not working properly, but it disappeared. Yes, I know....I am suspicious about that  ;) 

Now in the repositories I only have 4 default Ubuntu 6.06 (binary) files and nothing else. Now when I change to universe and multivere packages do downolad (hope they are all).

Is it possible that this could cause crashing the alsamixer (or some other problems perhaps)?

Thanks.

---

### Post by matjaz_pirnovar on 2006-06-22
Have no idea whay my alsa mixer was crashing.

I played with it quite a bit and could reconfigure it somehow.

Anyway I completely reinstalled Dapper (since I'm using it only two weeks now I could afford it) and sound and ALSA work like charm.

Hopefully it stays like that...

:) 
Matjaz

---

