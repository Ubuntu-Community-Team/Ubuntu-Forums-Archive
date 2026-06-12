---
title: "Can't get PulseAudio to work in Ubuntu Minimal"
date: 2009-07-15
forum: Multimedia Software
---

### Post by Buce on 2009-07-15
I previously had ALSA working, and now I'm trying to get PulseAudio to work in an installation of Ubuntu done from the Minimal CD. I want to use pavucontrol so that I can mute all Flash sounds coming from firefox while still listening to music using Amarok, Songbird, or mpg123.

I was using [this tutorial]("https://wiki.ubuntu.com/PulseAudio"), using the addgroup command instead of the GUI version it told me to, and now I'm stuck at this part:

> **Configuring PulseAudio**

Now, go into Applications -> Sound and Video -> click on PulseAudio Preferences.

    * Checkmark all three options under Network Access. This will allow other computers on your LAN with PulseAudio to access this computer's sound devices.
    * Checkmark Enable Multicast/RTP Receiver. This allows receiving multicast streams from other systems on your LAN.
    * Checkmark Enable Multicast/RTP Sender. This allows sending multicast streams (One source sends packets, all others may receive them simultaneously) 

Leave the other options alone for now, unless you want to loop outgoing streams through the local speakers.

Next go into System -> Preferences -> Sound and make sure that Enable Software Sound Mixing is checked. Also, under the Sounds Tab, I set devices to Autodetect.

    * Restart the current session with Ctrl + Alt + Backspace to enable pulseaudio (Save any work 1st)

Do I need to do this? I don't need to send sound to other computers on my LAN, so I'm pretty sure I can skip the first three bullets. As far as the last bullet point goes, I'm not sure what Software Sound Mixing is, but I'm guessing I at least need the autodetection, since, at this point in the tutorial, I'm not getting any sound at all.

If this is something I need to do, can I do it by editing a config file, or running a command? If not, I need to know the command to run to pull up the GUI they're referencing (System -> Preferences -> Sound)? I'm running a very lightweight, fluxbox-based desktop, and don't have access to the GNOME menus.

I hope this tutorial will work once I'm finished, or at least give me a few good leads on how to continue. Right now, I've got no sound, and starting pavucontrol from a command line gives me a segfault error. For now, I'm gonna browse through padevchooser and see if I can't find something promising, but if anyone could answer my questions above, I'd be very appreciative.

---

### Post by Buce on 2009-07-15
Odd thing: When I launch the PulseAudio Manager from padevchooser, it lists the 'User Name' as \u. And the title of the window is 'PulseAudio Manager [/tmp/pulse-\u/native]'. Hm.

---

### Post by Buce on 2009-07-15
Okay, I got it working in a reasonable way. First, I went to padevchooser -> Configure Local Sound Server -> Simultaneous Output and checked "Add virtual output device for simultaneous output on all local sound cards". This had no noticeable effect. Then, I removed the /etc/asound.conf file I created as part of the tutorial. After a reboot, sounds play normally, and pavucontrol loads up fine, but nothing shows up on the Playback tab. Maybe this is where "Software Sound Mixing" would come in handy? Looks like I still need to figure out how to launch the System -> Preferences -> Sound GUI from the command line. If anyone has any info on this, I'd appreciate the hint.

---

### Post by Buce on 2009-07-28
Alright, I figured it out. In order for pavucontrol to load properly, I need to run 'pulseaudio -D'. I added this to my .fluxbox/startup script.

For firefox/flash sounds to show up in the Playback tab of pavucontrol, I just needed to install libflashsupport.

---

### Post by igorzwx on 2009-07-28
Have you tried Skype with Pulse?
What is the sound quality?

---

### Post by Buce on 2009-07-29
> **Buce said:**
> For firefox/flash sounds to show up in the Playback tab of pavucontrol, I just needed to install libflashsupport.

I take that back. libflashsupport causes firefox to crash with a segfault any time a site has flash in it. Once again, it would be nice to know how to launch System/Preferences/Sound from the command line. I could load the LiveCD and look at the menu, but my LiveCD is at home, and I won't have access to it until Sunday or Monday.

igorzwx, I'm no audiophile, but the sound quality of pulse + skype seems fine to me. Why do you ask?

---

### Post by Buce on 2009-07-29
I tried following the directions at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578), and now flash doesn't work at all. When I try to install flashplugin-nonfree, I get this checksum error:

```
woody@bender:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  firefox konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/19.2kB of archives.
After this operation, 168kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  flashplugin-nonfree
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 82016 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.12.36ubuntu1~pp
a1_i386.deb) ...
Setting up flashplugin-nonfree (10.0.12.36ubuntu1~ppa1) ...
Downloading...
--02:19:55--  http://fpdownload.macromedia.com/get/flashplayer/current/install_f
lash_player_10_linux.tar.gz
           => `./install_flash_player_10_linux.tar.gz'
Resolving fpdownload.macromedia.com... 69.192.130.70
Connecting to fpdownload.macromedia.com|69.192.130.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,994,294 (3.8M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  189.78 KB/s
   50K .......... .......... .......... .......... ..........  2%  450.63 KB/s
  100K .......... .......... .......... .......... ..........  3%  602.76 KB/s
  150K .......... .......... .......... .......... ..........  5%  649.69 KB/s
  200K .......... .......... .......... .......... ..........  6%  652.84 KB/s
  250K .......... .......... .......... .......... ..........  7%  643.20 KB/s
  300K .......... .......... .......... .......... ..........  8%  627.01 KB/s
  350K .......... .......... .......... .......... .......... 10%  657.71 KB/s
  400K .......... .......... .......... .......... .......... 11%  657.11 KB/s
  450K .......... .......... .......... .......... .......... 12%  636.32 KB/s
  500K .......... .......... .......... ....>..... .......... 14%  648.18 KB/s
  550K .......... .......... .......... .......... .......... 15%  639.00 KB/s
  600K .......... .......... .......... .......... .......... 16%  653.06 KB/s
  650K .......... .......... .......... .......... .......... 17%  648.70 KB/s
  700K .......... .......... .......... .......... .......... 19%  637.79 KB/s
  750K .......... .......... .......... .......... .......... 20%  646.23 KB/s
  800K .......... .......... .......... .......... .......... 21%  651.72 KB/s
  850K .......... .......... .......... .......... .......... 23%  649.90 KB/s
  900K .......... .......... .......... .......... .......... 24%  637.58 KB/s
  950K .......... .......... .......... .......... .......... 25%  650.96 KB/s
 1000K .......... .......... .......... .......... .......... 26%  644.19 KB/s
 1050K .......... .......... .......... .......... .......... 28%  634.53 KB/s
 1100K .......... .......... .......... .......... .......... 29%  655.64 KB/s
 1150K .......... .......... .......... .......... .......... 30%  636.93 KB/s
 1200K .......... .......... .......... .......... .......... 32%  644.42 KB/s
 1250K .......... .......... .......... .......... .......... 33%  655.76 KB/s
 1300K .......... .......... .......... .......... .......... 34%  634.43 KB/s
 1350K .......... .......... .......... .......... .......... 35%  653.16 KB/s
 1400K .......... .......... .......... .......... .......... 37%  654.66 KB/s
 1450K .......... .......... .......... .......... .......... 38%  633.51 KB/s
 1500K .......... .......... .......... .......... .......... 39%  650.83 KB/s
 1550K .......... .......... .......... .......... .......... 41%  655.95 KB/s
 1600K .......... .......... .......... .......... .......... 42%  635.33 KB/s
 1650K .......... .......... .......... .......... .......... 43%  650.92 KB/s
 1700K .......... .......... .......... .......... .......... 44%  654.20 KB/s
 1750K .......... .......... .......... .......... .......... 46%  630.20 KB/s
 1800K .......... .......... .......... .......... .......... 47%  656.91 KB/s
 1850K .......... .......... .......... .......... .......... 48%  651.15 KB/s
 1900K .......... .......... .......... .......... .......... 49%  622.91 KB/s
 1950K .......... .......... .......... .......... .......... 51%  668.57 KB/s
 2000K .......... .......... .......... .......... .......... 52%  634.73 KB/s
 2050K .......... .......... .......... .......... .......... 53%  642.25 KB/s
 2100K .......... .......... .......... .......... .......... 55%  660.99 KB/s
 2150K .......... .......... .......... .......... .......... 56%  634.98 KB/s
 2200K .......... .......... .......... .......... .......... 57%  653.73 KB/s
 2250K .......... .......... .......... .......... .......... 58%  653.56 KB/s
 2300K .......... .......... .......... .......... .......... 60%  627.16 KB/s
 2350K .......... .......... .......... .......... .......... 61%  652.58 KB/s
 2400K .......... .......... .......... .......... .......... 62%  652.06 KB/s
 2450K .......... .......... .......... .......... .......... 64%  636.14 KB/s
 2500K .......... .......... .......... .......... .......... 65%  648.76 KB/s
 2550K .......... .......... .......... .......... .......... 66%  656.92 KB/s
 2600K .......... .......... .......... .......... .......... 67%  628.99 KB/s
 2650K .......... .......... .......... .......... .......... 69%  658.14 KB/s
 2700K .......... .......... .......... .......... .......... 70%  346.55 KB/s
 2750K .......... .......... .......... .......... .......... 71%    4.42 MB/s
 2800K .......... .......... .......... .......... .......... 73%  653.47 KB/s
 2850K .......... .......... .......... .......... .......... 74%  631.55 KB/s
 2900K .......... .......... .......... .......... .......... 75%  654.26 KB/s
 2950K .......... .......... .......... .......... .......... 76%  651.37 KB/s
 3000K .......... .......... .......... .......... .......... 78%  633.24 KB/s
 3050K .......... .......... .......... .......... .......... 79%  655.22 KB/s
 3100K .......... .......... .......... .......... .......... 80%  655.50 KB/s
 3150K .......... .......... .......... .......... .......... 82%  631.68 KB/s
 3200K .......... .......... .......... .......... .......... 83%  648.29 KB/s
 3250K .......... .......... .......... .......... .......... 84%  641.55 KB/s
 3300K .......... .......... .......... .......... .......... 85%  647.49 KB/s
 3350K .......... .......... .......... .......... .......... 87%  657.04 KB/s
 3400K .......... .......... .......... .......... .......... 88%  633.72 KB/s
 3450K .......... .......... .......... .......... .......... 89%  651.33 KB/s
 3500K .......... .......... .......... .......... .......... 91%  656.09 KB/s
 3550K .......... .......... .......... .......... .......... 92%  635.04 KB/s
 3600K .......... .......... .......... .......... .......... 93%  640.46 KB/s
 3650K .......... .......... .......... .......... .......... 94%  657.56 KB/s
 3700K .......... .......... .......... .......... .......... 96%  634.24 KB/s
 3750K .......... .......... .......... .......... .......... 97%  653.52 KB/s
 3800K .......... .......... .......... .......... .......... 98%  632.49 KB/s
 3850K .......... .......... .......... .......... .......... 99%  656.07 KB/s
 3900K                                                       100% 1292.68 GB/s

02:20:02 (622.75 KB/s) - `./install_flash_player_10_linux.tar.gz' saved [3994294
/3994294]

Download done.
md5sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is NOT installed.

```

---

### Post by Buce on 2009-07-29
Seems like everywhere I look, it says that hardy + flash + pulse is nearly impossible. I'm gonna come back to this thread tomorrow, see if there's any new suggestions, maybe try the tutorial I posted in my last post once more, and then, if all else fails, cut my losses and give Jaunty a try.

---

### Post by igorzwx on 2009-07-29
QUOTE:
"igorzwx, I'm no audiophile, but the sound quality of pulse + skype seems fine to me. Why do you ask? "

There is a reason, of course.
More precisely: Do you have noise, delay, latency with Skype?
Do you have a quadro core or something else?
We can make test calls with Skype and Ekiga.

---

### Post by kostkon on 2009-07-29
You could install Flash 10, that works OK with PulseAudio.

Canonical offers Flash 10 in their Partner repo, thus you can easily install it in Hardy. If you don't have the Partner repo in your sources.list, then here is its url:
```
deb http://archive.canonical.com/ubuntu hardy partner
```
Add the repo and then install the *adobe-flashplugin* package
Obviously, you then need to *remove* the *libflashsupport package*.

Afterwards, put a flash video playing in Firefox (obviously with sound) and then open *pavucontrol* and select the *Playback* tab. You should see the audio stream of Flash listed there. Right click on it and select *Move Stream...* and in the list that will appear select the audio device you want. PulseAudio will remember you choice from now on (I think only if you have followed [this how-to]("http://ubuntuforums.org/showthread.php?t=789578") in full and you already have the *.pulse* folder and the necessary files in it).

Hope that helps.

---

### Post by Buce on 2009-07-31
igorzwx: I don't have my webcam on hand at the moment, so I can't say for sure, but when I call echo123 on skype, I can hear it fine. There's no noise, at least. In reference to your last question, I have an intel duo core, not a quadro core.

kostkon: Thanks! Worked beautifully.

---

