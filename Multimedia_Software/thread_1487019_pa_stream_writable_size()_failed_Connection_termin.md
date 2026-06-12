---
title: "pa_stream_writable_size() failed: Connection terminated"
date: 2010-05-18
forum: Multimedia Software
---

### Post by dreamquartz on 2010-05-18
After updating my EeePC 1000H from 9.10 to 10.04, I experienced 2 problems:
1. Not able to connect to network via WPA2. This was solved.
2. Most times my sound is not played via Totem if I play video files.
If I play a DVD, I get: **pa_stream_writable_size() failed: Connection terminated**
I I play a MPEG or an MPG-file, or a VOB-file directly from a DVD, I mostly get:
**pa_stream_writable_size() failed: Connection terminated**
There is, however one exception. I have one MPG-file, that does play with both Audio and Video.
I followed all the links available, to fix this issue, but to no avail.

What kind of a problem is this, and how to solve it?

---

### Post by lidex on 2010-05-20
Using a Terminal="Applications->Accessories->Terminal"
```
sudo pulseaudio --kill
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

### Post by StuartZ on 2010-05-21
I've tried this and it comes up with invalid file etc.
I also have very tinny sounding music.

---

### Post by mc4man on 2010-05-21
I have this on 1 of 3 installs.

Basically started only with ac3 5.1 audio in  beta or late alpha . recently became most any audio when playing a video file. ( and some audio only

Possibly a fresh install would resolve, but not inclined to do so. This system has 5.1 sound which is somehow a factor here.

Did 'fix' here by removing the gstreamer pulseaudio plugin, which has restored playback of all files inc. ac3 5.1

Without the plugin gstreamer apps will output 5.1 as 6 channel but not has 5.1 - matters not at all here as I have no use for gstreamer apps for such files anyway.

Filed a bug quite some time ago against this - has gone nowhere and I've lost interest..

---

### Post by dreamquartz on 2010-05-26
I waited a couple of days to see if there was a solution, and reinstalled 10.04. So far there is no solution to this problem. I noticed that other threads show a similar problem with no solution.

Anyone?

---

### Post by mc4man on 2010-05-26
As I may have mentioned in the other thread the error, "pa_stream_writable_size() failed: Connection terminated" (pulseaudio crashing),  may have various causes which would mean various solution, if any.

So here was resolved with
 ```
sudo apt-get remove gstreamer0.10-pulseaudio
```

You could try, if not then 
```
sudo apt-get install gstreamer0.10-pulseaudio
```

---

### Post by dreamquartz on 2010-06-16
[SIZE=3][SIZE=1]After a long search and many trials, this is what did the trick with my EeePC 1000H.
I did an update from 9.10 to 10.04 and entered the following in Terminal:
[/SIZE][/SIZE] 
[LIST=1]
[*][SIZE=1]sudo apt-get remove gstreamer0.10-pulseaudio[/SIZE]
[*][SIZE=1]sudo apt-get install gnome-alsamixer[/SIZE]
[/LIST]
Tx everyone for helping me fix this. I started to think I had to wait much longer to get this realized.
:popcorn:

---

### Post by ferrell.charles on 2010-06-23
OK, after 3 months of this bug being a @#$$%!#$%... I found another post that mentioned PERMISSIONS as the culprit:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/189060](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/189060)

Do 

[COLOR=Red][B]sudo chown -R yourusernamehere ~/*
[/B][/COLOR]
Then log out and back in again.

And btw... if you uninstall gstreamer, it will uninstall ubuntu-desktop and thoroughly screw up your entire system.  Update manager will crash and be completely non-functional, you will lose all volume control, and you won't be able to install any new software ever again... and there's no way out of it but to reinstall the whole system.  I had this stoopid bug after reinstalling fresh EVERY time consistently.  Such a simple problem can cause all that heartburn!

---

### Post by ferrell.charles on 2010-06-23
Well, that didn't work for me either.  It only made it play a little longer before crashing (5 mins instead of 10 seconds).  

So I tried adding myself to the pulse and pulse-access groups, still doesn't work.  Pulseaudio crashes when I try to play a DVD.  I end up with no sound and three dashes ( --- ) right after the volume control icon in the panel applet.

---

### Post by mc4man on 2010-06-23
> And btw... if you uninstall gstreamer, it will uninstall ubuntu-desktop and thoroughly screw up your entire system. ......

Actually the suggestion is if nothing else works and this bug isn't fixed (no sign yet) to remove the gstreamer0.10-pulseaudio plugin, not gstreamer itself.

If will remove ubuntu-desktop - no big loss, just a metapackage. (can be re-installed down the road if need be

There is no "thoroughly screw up" whatsoever going on there.

(it doesn't hurt to read previous posts a bit more carefully...

---

### Post by Nabo00o on 2010-07-03
So why is this tread market as solved?
Come on, at least somebody should admit that something changed from the previous version that bugged totem.

I am also suffering from this bug, but only once in a while for every song...

---

### Post by mc4man on 2010-07-03
> So why is this tread market as solved?

Because it's just that, a thread, not a bug report. The Op's issue was resolved to his satisfaction.
There are several bug reports about this - the error isn't the bug, it just means pulse crashed.

So there could and are many scenarios and or causes.

For instance I've seen it since lucid BUT just on a 5.1 system when playing ac3 audio. (though it did migrate eventually to mostall audio.

Now on maverick the same thing, ac3 playback crashes pulse on a 5.1 system with analog 5.1 output. Everything else is fine.

Others have it occur in different ways.

Here's one bug report, I wouldn't doubt there's half a dozen different scenarios.
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/496616](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/496616)

Here's my orig. on lucid that's the same as seen now on maverick
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good0.10/+bug/554002](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good0.10/+bug/554002)

The odds of this being fixed directly are slim to none, though it may be in an inadvertant manner or someday as part of a 'let's fix most open pulse bugs' deal like happened in lucid 
(or so they say..

> pulseaudio (1:0.9.22~0.9.21+341-g62bf-0ubuntu1) lucid; urgency=low

  * New snapshot based on stable-queue git branch (testing requested
    specifically by upstream)
    - LP: #164745, #173212, #201391, #204536, #207796, #210016, #221038,
    - LP: #226342, #230408, #236423, #237443, #250059, #269585, #274304,
    - LP: #274577, #275474, #277532, #277566, #277932, #278025, #280534,
    - LP: #283049, #286816, #287036, #292732, #298011, #298301, #300290,
    - LP: #302038, #311497, #311853, #324062, #339448, #344057, #348979,
    - LP: #350829, #356206, #367379, #367544, #369822, #371897, #374846,
    - LP: #375570, #381801, #399515, #402950, #403786, #408169, #409322,
    - LP: #409723, #410326, #410446, #417695, #417976, #419271, #421072,
    - LP: #422774, #423979, #424655, #425028, #427016, #431072, #432660,
    - LP: #437640, #437996, #442191, #443306, #443389, #446719, #449762,
    - LP: #455417, #461532, #464652, #483191, #497537, #503780
  * debian/patches/:
    + add: 0099-change-configure-git-version-tag.patch: Match released
           upstream 0.9.21 for shlibs and LIBPULSE_VERSION_INFO
    - drop: 0004-set-tsched0.patch (no longer relevant)
            0050-revert-pacmd-poll-argv.patch (no longer relevant)
            0056-dont-bail-on-sound-class-modem.patch (merged)
            0056-ignore-sound-class-modem.patch (merged)
            0058-Backport-4c793.patch (merged)
            0059-Backport-978d3.patch (merged)
            0060-fix-implicit-func-decl-cpu-arm.patch (merged)
            0061-Backport-c5fdb.patch (merged)
            0070-dont-bail-on-sound-class-modem-devs.patch (merged)
    + refresh: 0001-change-resample-and-buffering.patch
               0090-disable-flat-volumes.patch
               0091-dont-load-cork-music-on-phone.patch
               0057-load-module-x11-bell.patch

 -- Daniel T Chen <crimsun@ubuntu.com>  Thu, 14 Jan 2010 20:33:05 -0500

---

### Post by dreamquartz on 2010-07-04
> **Nabo00o said:**
> So why is this tread market as solved?
Come on, at least somebody should admit that something changed from the previous version that bugged totem.

I am also suffering from this bug, but only once in a while for every song...

Indeed I did that because it was my thread, and it was solved for me.

---

### Post by zeroseven0183 on 2010-07-23
I didn't have this problem before my last update. However, I don't remember which packages where updated.
Video and audio worked fine back then.

---

### Post by John Baptist on 2010-07-26
zeroseven0183: You can see exactly which packages were updated by looking at /var/log/apt/history.log

---

### Post by JoeMac42 on 2010-08-05
This worked for me on the Lucid PowerPC port:
```
aptitude reinstall gstreamer0.10-pulseaudio

``` Completely fixed.

---

### Post by zeroseven0183 on 2010-08-21
Even after reinstalling or removing gstreamer pulseaudio, I still encounter this ugly problem

---

### Post by lidex on 2010-08-22
> **zeroseven0183 said:**
> Even after reinstalling or removing gstreamer pulseaudio, I still encounter this ugly problem

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by zeroseven0183 on 2010-08-27
I think I got it. The audio crashes everytime I have a USB device (mouse, mobile broadband) plugged. This is an ugly bug, indeed.

---

### Post by steej on 2010-10-19
oh my god! It's true!
Without my usb mouse the audio works well!

---

### Post by BSD_dad on 2010-10-24
figures, I get it trying to play dvd through ext usb drive :(

---

### Post by in0giro on 2010-10-24
i seem to only get this on an RT (real time) kernel, whether a USB device is connected or not.  sorry i do not have more to add, but still happening with Gentoo kernel 2.6.34.

peace

---

### Post by BSD_dad on 2010-10-25
Update:
Got dvd playing.

Removed gstream pulseaudio plugin and resolved crash, however dvd playback was choppy (Movie Player). After trying to check if it was a hardware issue by booting back to Vista :( and *it* crashed on boot with the ext usb drive plugged in, had to restore (another reason to not boot Win!), lost Grub loader, had to build 10.10 flash drive to restore Grub2 (hours later...) then found [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Troubleshooting") in community help. Deleted ~/.dvdcss/ folder, installed VLC Media Player (which worked great) and Movie Player worked but still with a slight jitter in video. Reinstalled gstream pulseaudio plugin and VLC still works fine, no crash.

Ought to put VLC as default player in distribution.

---

### Post by Cripton on 2010-11-01
> **JoeMac42 said:**
> This worked for me on the Lucid PowerPC port:
```
aptitude reinstall gstreamer0.10-pulseaudio

``` Completely fixed.

this works for me on maverik, i used
sudo apt-get remove gstreamer0.10-pulseaudio --purge
sudo apt-get install gstreamer0.10-pulseaudio

on maverik this appears to be an installation bug, or upgrade bug, i have it on a fresh install and a fully upgraded one, and the reinstall with the purge option do the trick..

i hope this help

---

### Post by snowmath on 2010-11-06
> **dreamquartz said:**
> I waited a couple of days to see if there was a solution, and reinstalled 10.04. So far there is no solution to this problem. I noticed that other threads show a similar problem with no solution.

Anyone?
Thanks for your hard work dreamquartz,I followed your lead for the very same problem and it worked perfectly on my Eee pc1005ha under Ubuntu LTs ! I just wish someone would explain to me why it worked!BTW this is my first post so if I am not doing this right please forgive.

---

### Post by GrandpaLeaman on 2010-11-14
OK, I had the same problem and the solutions I was seeing on the net and in the forums gave me no joy. So I went to Preferences-->Sound and opened the Output Tab to see how I had the output configured. Since I am running PulseAudio-Equalizer I show two output options:

Option 1 - Internal Audio Analog Stereo
Option 2 - LADSPA Plugin Multiband EQ on Internal Audio Analog Stereo

The LADSPA option is selected because it is required by the equalizer. When I select option one and restarted Totem, movies played fine. When I switched back to Option 2 and restarted Totem, again it would crash. So my problem looked like it was in LADSPA.

I then went to Synaptic and did a search on LADSPA and reinstalled the following packages:

 - ladspa-sdk
 - pulseaudio-equalizer
 - sox
 - swh-plugins

I then verified I had sound output switched to Option 2, restarted Totem, and everything is working fine.

I hope this helps someone else.

---

### Post by JCyberinux on 2010-11-18
sudo apt-get remove gstreamer0.10-pulseaudio --purge
sudo apt-get install gstreamer0.10-pulseaudio

this command helps me a lot on resolving the issues on sound card....
thank you all guys!!!

---

### Post by patman0623 on 2010-11-25
> **JCyberinux said:**
> sudo apt-get remove gstreamer0.10-pulseaudio --purgeThis worked great for me:```
The following packages will be REMOVED:
  gstreamer0.10-pulseaudio* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 270kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 248070 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gstreamer0.10-pulseaudio ...

```

> **JCyberinux said:**
> sudo apt-get install gstreamer0.10-pulseaudioThis didn't: ```
sudo apt-get install gstreamer0.10-pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-pulseaudio is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gstreamer0.10-pulseaudio' has no installation candidate

```
and
```
sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-desktop

```

Um, I'm scared, help!!! I don't even know what ubuntu-desktop is, but it sounds important, although my machine is working fine. Do I need it back?

On another note, this is really weird, but the videos and audio are now working with my USB sound card plugged in. Not sure why.

---

### Post by lidex on 2010-11-25
> **patman0623 said:**
> 
This didn't: ```
sudo apt-get install gstreamer0.10-pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gstreamer0.10-pulseaudio is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gstreamer0.10-pulseaudio' has no installation candidate

```
and
```
sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-desktop

```

Um, I'm scared, help!!! I don't even know what ubuntu-desktop is, but it sounds important, although my machine is working fine. Do I need it back?

On another note, this is really weird, but the videos and audio are now working with my USB sound card plugged in. Not sure why.

Open a terminal and run these commands:
```
sudo apt-get update
sudo apt-get upgrade
```
Post the output here.

---

### Post by patman0623 on 2010-11-25
> **lidex said:**
> Open a terminal and run these commands:
```
sudo apt-get update
sudo apt-get upgrade
```
Post the output here.

```
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Get:3 http://dl.google.com stable Release [1,347B]                             
Get:4 http://us.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Get:5 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ maverick/main Translation-en_US
Get:6 http://dl.google.com stable Release [1,338B]                             
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Get:7 http://security.ubuntu.com maverick-security Release [27.2kB]            
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://archive.canonical.com maverick Release                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Get:8 http://dl.google.com stable/main i386 Packages [1,094B]                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Hit http://ppa.launchpad.net maverick Release                                  
Get:9 http://us.archive.ubuntu.com maverick-updates Release [31.4kB]           
Hit http://ppa.launchpad.net maverick Release                                  
Get:10 http://dl.google.com stable/main i386 Packages [613B]                   
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://packages.medibuntu.org maverick Release.gpg                         
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US             
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://us.archive.ubuntu.com maverick Release                              
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_US         
Hit http://packages.medibuntu.org maverick Release                             
Get:11 http://security.ubuntu.com maverick-security/main Sources [13.8kB]      
Get:12 http://us.archive.ubuntu.com maverick-updates/main Sources [41.4kB]     
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Get:13 http://security.ubuntu.com maverick-security/restricted Sources [14B]   
Get:14 http://security.ubuntu.com maverick-security/universe Sources [4,365B]  
Get:15 http://security.ubuntu.com maverick-security/multiverse Sources [649B]  
Get:16 http://security.ubuntu.com maverick-security/main i386 Packages [39.8kB]
Hit http://packages.medibuntu.org maverick/free i386 Packages                  
Get:17 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:18 http://security.ubuntu.com maverick-security/universe i386 Packages [18.5kB]
Hit http://packages.medibuntu.org maverick/non-free i386 Packages              
Get:19 http://us.archive.ubuntu.com maverick-updates/restricted Sources [14B]  
Get:20 http://us.archive.ubuntu.com maverick-updates/universe Sources [13.5kB] 
Get:21 http://us.archive.ubuntu.com maverick-updates/multiverse Sources [649B] 
Get:22 http://us.archive.ubuntu.com maverick-updates/main i386 Packages [110kB]
Get:23 http://security.ubuntu.com maverick-security/multiverse i386 Packages [1,655B]
Get:24 http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:25 http://us.archive.ubuntu.com maverick-updates/universe i386 Packages [44.8kB]
Get:26 http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages [1,958B]
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Fetched 355kB in 1s (193kB/s)                             

```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by patman0623 on 2010-11-25
I'm going to bump this thread as I'm rather anxious to get this fixed (I can't reboot after all, so time is of the essence).

---

### Post by lidex on 2010-11-26
> **patman0623 said:**
> I'm going to bump this thread as I'm rather anxious to get this fixed (I can't reboot after all, so time is of the essence).

The errors you referred to earlier would suggest an issue with connecting to repos. The output now shows you are connecting so try it again. Both those packages are there.

---

### Post by patman0623 on 2010-11-26
> **lidex said:**
> The errors you referred to earlier would suggest an issue with connecting to repos. The output now shows you are connecting so try it again. Both those packages are there.

Nope. I installed Ubuntu 10.10 from a CD, which I then had to remove from the repo list, so it's likely I'm missing an important one.

---

### Post by patman0623 on 2010-11-26
There, I figured it out! I fixed my sources.list, I added:

```
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
```

I'm still having issues again with my sources... I'll make my own post though.

---

### Post by tjma2001 on 2010-12-22
dpkg -r --force-all gstreamer0.10-pulseaudio 

to remove and not uninstall anything else.

---

### Post by JoeloRoss on 2010-12-25
I had the same problem with my **Exaile** in Maverick. This command solved my problem !!

```
sudo apt-get remove gstreamer0.10-pulseaudio
```

---

### Post by Sugi on 2011-01-01
I started this error out of nowhere, but it wasn't happening too often.  Then it got really bad, I couldn't even play 5 seconds of a song before this started happening again.  I did the below method and so far it fixed it right out of the box.  Though, I didn't reinstall pulseaudio-equalizer, because it wasn't available for me in the Synaptic manager.  I'll report back with how stable the new changes are.

Sugi

> **GrandpaLeaman said:**
> I then went to Synaptic and did a search on LADSPA and reinstalled the following packages:- ladspa-sdk - pulseaudio-equalizer - sox - swh-plugins

EDIT:
Since 11 hours ago, I have testing it out. It has greyed out once and "Disconnected: Connection Timeout" error.  Of course, my connection to the streaming of the music should be fine, though these output errors might explain something.  Not sure if they are still connected to the original problem.

> (totem:16494): Gtk-CRITICAL **: IA__gtk_tree_view_scroll_to_cell: assertion `tree_view->priv->tree != NULL' failed
** Message: Error: Disconnected: Connection terminated
pulsesink.c(290): gst_pulsering_is_dead (): /GstPlayBin2:play/GstPlaySink:playsink0/GstBin:abin/GstBin:audiosinkbin/GstGConfAudioSink:audio-sink/GstBin:bin40/GstAutoAudioSink:autoaudiosink19/GstPulseSink:autoaudiosink19-actual-sink-pulse

Memory pool destroyed but not all memory blocks freed! 1 remain.

---

### Post by lidex on 2011-01-02
@Sugi
Have you tried resetting your pulse configuration?
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

If you still have issues post the output of:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by nicksum4141 on 2011-01-13
I get this error randomly without any USB drives plugged in. The only thing I find that fixes it is to turn on crossfade, but I don't want that set on. I tried to reinstall gstreamer but that didn't do anything.

---

### Post by patman0623 on 2011-01-13
> **nicksum4141 said:**
> I get this error randomly without any USB drives plugged in. The only thing I find that fixes it is to turn on crossfade, but I don't want that set on. I tried to reinstall gstreamer but that didn't do anything.

Again the solution to this problem is to entirely remove pulseaudio and default back to ALSA, which has worked great for me.
```
sudo apt-get remove gstreamer0.10-pulseaudio ubuntu-desktop
```
As you can see in [this thread]("http://ubuntuforums.org/showthread.php?t=1664500"), ubuntu-desktop is just a wrapper package and no harm should come to your computer as a result.

---

### Post by coverup1128 on 2011-04-13
Instead of removing gstreamer0.10-pulseaudio, I installed VLC player. The error emerges, if I play my video using the default player (totem), but the file plays fine using VLC.

---

### Post by lidex on 2011-04-13
> **coverup1128 said:**
> Instead of removing gstreamer0.10-pulseaudio, I installed VLC player. The error emerges, if I play my video using the default player (totem), but the file plays fine using VLC.

Sounds about right - vlc does not use gstreamer backend and totem does.

---

### Post by Melotten on 2011-04-14
Me too, VLC seems working fine for me as well.

Seems that I need to dismiss totem from my system :(

---

