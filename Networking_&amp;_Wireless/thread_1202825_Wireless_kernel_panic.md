---
title: "Wireless kernel panic"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by sdlynx on 2009-07-02
Hi everyone,

I have the Intel Wifi Link 5100 AGN and when it is in use a lot my Ubuntu 9.04 system has a kernel panic and freezes.  I'm sure its the wireless as when it is off there is never a kernel panic.  I've waited it out and nothing happens, I also tried downgrading my driver, which seems to have made it better (less crashes but they are still there).  Any suggestions?

Thanks

P.S. I've seen two other threads involving the same problem but with no solution...

---

### Post by sdlynx on 2009-07-03
bumpp

---

### Post by sdlynx on 2009-07-05
bump again.  maybe someone will actually find this lol....

---

### Post by ibuclaw on 2009-07-05
> **sdlynx said:**
> bump again.  maybe someone will actually find this lol....

Can you go to "System->Administration->Log File Viewer" and post the output of the logs from 30 minutes before the kernel panic to the time when the kernel panic actually occurs?

Viable log files are:
[LIST]
[*]debug
[*]dmesg
[*]kern.log
[*]syslog
[/LIST]

You can post either in [NOPARSE]```

```[/NOPARSE] tags or on [Ubuntu Paste]("http://paste.ubuntu.com/").


Regards
Iain

---

### Post by sdlynx on 2009-07-05
Thanks a lot for a response! I'll try to cause another kernel panic (the files were too recent to include the last one) and do what you said.

---

### Post by sdlynx on 2009-07-07
debug:

[http://paste.ubuntu.com/212204/](http://paste.ubuntu.com/212204/)

dmesg:

[http://paste.ubuntu.com/212205/](http://paste.ubuntu.com/212205/)

kern.log:

[http://paste.ubuntu.com/212208/](http://paste.ubuntu.com/212208/)

syslog:

[http://paste.ubuntu.com/212207/](http://paste.ubuntu.com/212207/)

Wow that was a lot... hope you can piece that apart...

---

### Post by sdlynx on 2009-07-08
bump

now that I've got the system files up I hope some1 will take a look

---

### Post by sdlynx on 2009-07-09
bump help guys?

---

### Post by sdlynx on 2009-07-11
bump.

---

### Post by Crafty Kisses on 2009-07-11
It's really hard to tell what's causing the kernel panic. It's probably marginal hardware that's causing it. Have you tried compiling a different kernel? I'd say go with an older version, or try the latest version. Infact I'd love to know what kernel you're running now, post the results of:
```
uname -r
```
You can grab the latest and older kernels from [**The Linux Kernel Archives.**]("http://www.kernel.org/") So grab the kernel you want and compile it. In order for the initial compile to go through, you're going to need a couple of packages, so copy and paste this command into the Terminal:
```
sudo apt-get install build-essential && fakeroot
```
You also need these packages to my knowledge:
```
apt-get build-dep linux-source
apt-get source linux-source
```
Then you need to navigate to:
```
cd /usr/src
```
Then fetch the kernel you want, by using wget or downloading it off the [**kernel index.**]("http://www.kernel.org/pub/linux/kernel/v2.6/") Once you have downloaded the proper kernel, you need to extract it, so run:
```
tar xjf linux-(kernel version)
```
Now go into the kernel directory and run:
```
make menuconfig
```
Now in essence next, we are going to test the kernel compile and see if any errors occur:
```
make-kpkg clean
fakeroot make-kpkg --initrd --revision=(kernel image)
```
If something happens like a compilation error, then you need to run:
```
make clean
```
Then you need to once again try **make menuconfig**. Then depending on what kernel you chose to compile, you would run:
```
dpkg -i kernel-image-(your kernel)
```
Then you can see if you're running your kernel you compiled. This is a brief rundown on how to compile a kernel. There is a way better guide over at the official Ubuntu documentation. Check it out right **[here.]("https://help.ubuntu.com/community/Kernel/Compile")** I'm aware this may be a bit extreme, but it's worth a shot and may solve the problem, I had a similar hardware issue that was causing kernel panics and I compiled a new kernel, and it worked like a charm.

---

### Post by sdlynx on 2009-07-11
I'm running 2.6.28-13 but I'll give that a shot.

Hmm it seems to give me an error when I run make menuconfig:

```
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:105: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:307: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
 *** Unable to find the ncurses libraries or the
 *** required header files.
 *** 'make menuconfig' requires the ncurses libraries.
 *** 
 *** Install ncurses (ncurses-devel) and try again.
 *** 
make[1]: *** [scripts/kconfig/dochecklxdialog] Error 1
make: *** [menuconfig] Error 2

```

ncurses-devel doesn't exist in the repositories

---

### Post by Crafty Kisses on 2009-07-11
Yeah 2.6.28-13-generic is the kernel you get if you ran the update. I'd suggest downgrading your kernel. As stated before it's a bit extreme, but it's worth a shot.

---

### Post by sdlynx on 2009-07-11
Actually I checked on kernel.org and the latest stable kernel is 2.8.30.1 so I'm compiling that.

---

### Post by Crafty Kisses on 2009-07-11
> ncurses-devel doesn't exist in the repositories
I think the package name for ncurses is:
```
libncursesw5-dev
```
So install the ncurses package, then try running:
```
make modules
make modules_install
```
That will probably most likely solve your makemenu problem by installing the ncurses dev package then running the module commands.

---

### Post by sdlynx on 2009-07-11
yes, I did that (the main article you linked to told me so).  Thanks a lot.  Back to seeing if this works now lol

---

### Post by sdlynx on 2009-07-11
hmm this is taking too much work, and I'm having too many errors to make this work right lol.  I even downloaded the 2.6.30 deb package from ubuntu but it gives me an error when I try to install, so I just figure I'll wait til karmic comes out, but even so does anybody have an idea what else I can do wireless?

---

### Post by Crafty Kisses on 2009-07-12
Take a look at this post, and see if this doesn't help. [http://ubuntuforums.org/showpost.php?p=5710211&postcount=4](http://ubuntuforums.org/showpost.php?p=5710211&postcount=4)

---

### Post by sdlynx on 2009-07-12
I tried this earlier and yes the wireless is much more stable, gone from like 10-15 crashes to 0-1 per day.

---

### Post by Crafty Kisses on 2009-07-12
Hmm, out of curiosity what are the results of the following?
```
lsmod
```

---

### Post by sdlynx on 2009-07-13
lsmod:```
Module                  Size  Used by
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
vboxnetadp            109228  0 
vboxnetflt            116844  0 
vboxdrv              1721356  1 vboxnetflt
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557492  3 
snd_pcm_oss            52352  0 
arc4                   10240  2 
snd_mixer_oss          24960  1 snd_pcm_oss
ecb                    11392  2 
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
iwlagn                114820  0 
iwlcore               106496  1 iwlagn
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
leds_hp_disk           11400  0 
uvcvideo               69512  0 
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
led_class              13064  2 iwlcore,leds_hp_disk
mac80211              251528  2 iwlagn,iwlcore
video                  29204  4 
iTCO_wdt               21712  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
joydev                 20864  0 
psmouse                64028  0 
intel_agp              39408  0 
output                 11648  1 video
iTCO_vendor_support    12420  1 iTCO_wdt
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
v4l1_compat            23940  2 uvcvideo,videodev
sdhci_pci              16896  0 
sdhci                  27396  1 sdhci_pci
pcspkr                 11136  0 
serio_raw              14468  0 
cfg80211               43552  3 iwlagn,iwlcore,mac80211
lis3lv02d              19408  0 
nvidia               8123768  39 
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
r8169                  46596  0 
mii                    14464  1 r8169
vesafb                 15240  1 
fbcon                  49792  72 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

edit:the update for the 2.6.28.14 kernel came out and I installed that, dunno if it fixed it yet but I haven't had a crash so far.

---

### Post by mirko_3 on 2009-08-19
hey did that kernel update fix it? I'm having random kernel panics and i'm pretty sure it's my wireless driver iwlagn too... so i'd just like to know how things are going there!

---

### Post by sdlynx on 2009-08-20
I haven't had a problem in a long time.  I think the kernel update to 2.6.28-14 has fixed any problems.  Good luck!

---

