---
title: "VLC player stopped playing DVDs. What's wrong?"
date: 2013-10-05
forum: Multimedia Software
---

### Post by MagisterDixit on 2013-10-05
I run Ubuntu 12.04 LTS and have had no trouble with using my VLC media player until recently. I used to just plug in the DVD and play would begin automatically just like it is supposed to. But now VLC starts up and gives me the organge cone. Nothing else happens. What went wrong? Do I need to update something?

Edit: I just tried the update VLC PPA and it says I have the latest version already? I used synaptic package manager to upgrade everything that had an upgrade available. Seriously, what gives?

---

### Post by varunendra on 2013-10-06
Make sure you have libdvdread4 and ubuntu-restricted-extras installed -
```
sudo apt-get install libdvdread4 ubuntu-restricted-extras
```

If it still can't play DVDs, post back the output of -
```
dpkg -l | egrep 'libdvd|restricted|gstreamer'
```

---

### Post by MagisterDixit on 2013-10-07
GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio                     0.10.31-1ubuntu1.2                               GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                          0.10.36-1ubuntu1                                 Tools for use with GStreamer
ii  gstreamer0.10-x                              0.10.36-1ubuntu0.1                               GStreamer plugins for X11 and Pango
ii  libdvdnav4                                   4.2.0-1                                          DVD navigation library
ii  libdvdread4                                  4.2.0-1ubuntu3                                   library for reading DVDs
ii  libgstreamer-plugins-bad0.10-0               0.10.22.3-2ubuntu2.2                             GStreamer shared libraries from the "bad" set
ii  libgstreamer-plugins-base0.10-0              0.10.36-1ubuntu0.1                               GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                           0.10.36-1ubuntu1                                 Core GStreamer libraries and elements
ii  phonon-backend-gstreamer                     4:4.7.0really4.6.2-0ubuntu0.1                    Phonon GStreamer 0.10.x backend
ii  ubuntu-restricted-addons                     12                                               Commonly used restricted packages for Ubuntu
ii  ubuntu-restricted-extras                     57                                               Commonly used restricted packages for Ubuntu

---

### Post by mc4man on 2013-10-07
Put a dvd in the drive, close out anything that pops up or opens,  inc. vlc.
Once the drive settles open a terminal & go - 
vlc
Once vlc is open go > ctrl+d to open the "open media > disc" menu, click on 'play'.

Post the complete terminal output.

(vlc doesn't use gstreamer or any gstreamer plugins..

---

### Post by MagisterDixit on 2013-10-08
> **mc4man said:**
> Put a dvd in the drive, close out anything that pops up or opens,  inc. vlc.
Once the drive settles open a terminal & go - 
vlc
Once vlc is open go > ctrl+d to open the "open media > disc" menu, click on 'play'.

Post the complete terminal output.

(vlc doesn't use gstreamer or any gstreamer plugins..

After entering "vlc" in terminal, it opens VLC. From there I'm lost. I pasted "> ctrl+d" and nada. The name@nameUbuntu12 doesn't come back up for me to actually use the command- or any other. Did I do something wrong?

---

### Post by mc4man on 2013-10-08
> **FpCrPnW said:**
> After entering "vlc" in terminal, it opens VLC. From there I'm lost. I pasted "> ctrl+d" and nada. The name@nameUbuntu12 doesn't come back up for me to actually use the command- or any other. Did I do something wrong?

That would have been ctrl+d on keyboard (just a shortcut to menu
Try again & after vlc opens either  ctrl+d or go Media > Open disc (scr. 1), then play from that menu (scr. 2
Post all of the terminal output

---

### Post by MagisterDixit on 2013-10-08
Sorry. I had a duh moment. Here are the terminal results:

VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x9660908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: SERENITY
libdvdnav: DVD Serial Number: 3337a695
libdvdnav: DVD Title (Alternative): FULLFRAME_R0
libdvdnav: Unable to find map file '/home/travis/.dvdnav/SERENITY.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
[0xb5400618] main input error: ES_OUT_RESET_PCR called
[0xb5400618] main input error: ES_OUT_RESET_PCR called
[0xb5400618] main input error: ES_OUT_RESET_PCR called
[0xb5400618] main input error: ES_OUT_RESET_PCR called

---

### Post by MagisterDixit on 2013-10-08
Thanks, mc4man! With that error message I was able to google the solution that you posted for another person way back in the day. I put 
sudo /usr/share/doc/libdvdread4/install-css.sh

in the terminal and now I can watch movies again! I'm still confused about how I lost this ability though. I haven't done anything with the terminal or added anything to my computer in a long time. Any idea about what happened?

---

### Post by mc4man on 2013-10-09
> **FpCrPnW said:**
> /I'm still confused about how I lost this ability though. I haven't done anything with the terminal or added anything to my computer in a long time. Any idea about what happened?

It would seem libdvdcss2 was uninstalled somehow..

Another way to ck. for vlc warnings & or errors is right in the gui. Just open vlc as normal  & go ctrl+m or tools > messages. Leave the message window open & go about using vlc.
There are 3 verbosity levels in the message window, start with the default of 0  which is errors only. (you can't change v while playing
Output can be saved to file when useful.

---

### Post by euanbuntu2 on 2013-10-10
How are you guys getting dvds to play at all? Apparently mediabuntu repositories are now gone and any other instructions I have received on getting my dvd's to work are quite complicated, involving somethig called git (that I've never heard of) and I'd love it if someone could help me out with a walk through of what to do please as I'm really confused? I'm on 13.04

---

### Post by varunendra on 2013-10-10
I never added medibuntu repositories to my default ones (the default "Ubuntu" repositories) and I never needed to add 'anything' except installing VLC and restricted extras to be able to play DVDs.

Did you follow the suggestions in this thread? Just install these and try playing again -
```
sudo apt-get install ubuntu-restricted-extras libdvdread4
```
If you still can't play DVDs, run the player (I'd recommend VLC) from terminal and post back the messages it leaves in the terminal.

---

### Post by mc4man on 2013-10-10
> **euanbuntu2 said:**
> How are you guys getting dvds to play at all? Apparently mediabuntu repositories are now gone and any other instructions I have received on getting my dvd's to work are quite complicated, involving somethig called git (that I've never heard of) and I'd love it if someone could help me out with a walk through of what to do please as I'm really confused? I'm on 13.04
You can take a look here as how to install the new libdvdread4 & then run this in a terminal to install libdvdcss2

```
sudo /usr/share/doc/libdvdread4/install-css.sh

```

[http://ubuntuforums.org/showthread.php?t=2179777&p=12812210&viewfull=1#post12812210](http://ubuntuforums.org/showthread.php?t=2179777&p=12812210&viewfull=1#post12812210)

---

### Post by Dean28 on 2013-10-10
@ euanbuntu2
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by euanbuntu2 on 2013-10-10
hi everyone, thanks for all the support :)

@Varunendra - thank you, I got thie following response:

```

christmaspudding@Christmas:~$ vlc
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x1029108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

```

I'm still having problems and have followed the terminal commands you've given...

first I did this:

```
christmaspudding@Christmas:~$ sudo apt-get install libdvdread4 ubuntu-restricted-extras
[sudo] password for christmaspudding: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

...which I take to mean that's all up to date. Then, when I went onto give the terminal the next one I get this:

```

christmaspudding@Christmas:~$ sudo /usr/doc/libdvdread4/install-css.sh
sudo: /usr/doc/libdvdread4/install-css.sh: command not found

```

I've already got the regionset package installed and set to my region, that was ok. Popped in a dvd...but nada...not a squeak.

So, I've run the following as was hinted earlier in the thread and hope it might spread a bit of light on the situation for us?? Here goes:

```

christmaspudding@Christmas:~$ dpkg -l | egrep 'libdvd|restricted|gstreamer'
ii  bluez-gstreamer                           4.101-0ubuntu8b1                       amd64        Bluetooth GStreamer support
ii  gir1.2-gstreamer-0.10                     0.10.36-1ubuntu2                       amd64        Description: GObject introspection data for the GStreamer library
ii  gir1.2-gstreamer-1.0                      1.0.6-1                                amd64        Description: GObject introspection data for the GStreamer library
ii  gstreamer0.10-alsa:amd64                  0.10.36-1.1ubuntu1                     amd64        GStreamer plugin for ALSA
ii  gstreamer0.10-ffmpeg:amd64                0.10.13-5                              amd64        FFmpeg plugin for GStreamer
ii  gstreamer0.10-fluendo-mp3:amd64           0.10.15.debian-1ubuntu1                amd64        Fluendo mp3 decoder GStreamer plugin
ii  gstreamer0.10-gconf:amd64                 0.10.31-3+nmu1ubuntu2                  amd64        GStreamer plugin for getting the sink/source information from GConf
ii  gstreamer0.10-nice:amd64                  0.1.3-1                                amd64        ICE library (GStreamer plugin)
ii  gstreamer0.10-plugins-bad:amd64           0.10.23-7ubuntu2                       amd64        GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-multiverse      0.10.21-1ubuntu1                       amd64        GStreamer plugins from the "bad" set (Multiverse Variant)
ii  gstreamer0.10-plugins-base:amd64          0.10.36-1.1ubuntu1                     amd64        GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps           0.10.36-1.1ubuntu1                     amd64        GStreamer helper programs from the "base" set
ii  gstreamer0.10-plugins-good:amd64          0.10.31-3+nmu1ubuntu2                  amd64        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly:amd64          0.10.19-2                              amd64        GStreamer plugins from the "ugly" set
ii  gstreamer0.10-pulseaudio:amd64            0.10.31-3+nmu1ubuntu2                  amd64        GStreamer plugin for PulseAudio
ii  gstreamer0.10-tools                       0.10.36-1ubuntu2                       amd64        Tools for use with GStreamer
ii  gstreamer0.10-x:amd64                     0.10.36-1.1ubuntu1                     amd64        GStreamer plugins for X11 and Pango
ii  gstreamer1.0-alsa:amd64                   1.0.6-1                                amd64        GStreamer plugin for ALSA
ii  gstreamer1.0-clutter                      2.0.2-0ubuntu1                         amd64        Clutter PLugin for GStreamer 1.0
ii  gstreamer1.0-libav:amd64                  1.0.6-1                                amd64        FFmpeg plugin for GStreamer
ii  gstreamer1.0-nice:amd64                   0.1.3-1                                amd64        ICE library (GStreamer plugin)
ii  gstreamer1.0-plugins-bad:amd64            1.0.6-1ubuntu1                         amd64        GStreamer plugins from the "bad" set
ii  gstreamer1.0-plugins-base:amd64           1.0.6-1                                amd64        GStreamer plugins from the "base" set
ii  gstreamer1.0-plugins-base-apps            1.0.6-1                                amd64        GStreamer helper programs from the "base" set
ii  gstreamer1.0-plugins-good:amd64           1.0.6-1ubuntu1                         amd64        GStreamer plugins from the "good" set
ii  gstreamer1.0-plugins-ugly:amd64           1.0.6-1                                amd64        GStreamer plugins from the "ugly" set
ii  gstreamer1.0-pulseaudio:amd64             1.0.6-1ubuntu1                         amd64        GStreamer plugin for PulseAudio
ii  gstreamer1.0-tools                        1.0.6-1                                amd64        Tools for use with GStreamer
ii  gstreamer1.0-x:amd64                      1.0.6-1                                amd64        GStreamer plugins for X11 and Pango
ii  libdvdnav-dbg                             4.2.0+20130225-1ubuntu0.1              amd64        DVD navigation library (debug)
ii  libdvdnav-dev                             4.2.0+20130225-1ubuntu0.1              amd64        DVD navigation library (development)
ii  libdvdnav4:amd64                          4.2.0+20130225-1ubuntu0.1              amd64        DVD navigation library
ii  libdvdread-dbg                            4.2.0+20121016-1ubuntu1                amd64        library for reading DVDs (debug)
ii  libdvdread-dev                            4.2.0+20121016-1ubuntu1                amd64        library for reading DVDs (development)
ii  libdvdread4                               4.2.0+20121016-1ubuntu1                amd64        library for reading DVDs
ii  libgstreamer-plugins-bad0.10-0:amd64      0.10.23-7ubuntu2                       amd64        GStreamer shared libraries from the "bad" set
ii  libgstreamer-plugins-bad1.0-0:amd64       1.0.6-1ubuntu1                         amd64        GStreamer development files for libraries from the "bad" set
ii  libgstreamer-plugins-base0.10-0:amd64     0.10.36-1.1ubuntu1                     amd64        GStreamer libraries from the "base" set
ii  libgstreamer-plugins-base0.10-0:i386      0.10.36-1.1ubuntu1                     i386         GStreamer libraries from the "base" set
ii  libgstreamer-plugins-base1.0-0:amd64      1.0.6-1                                amd64        GStreamer libraries from the "base" set
ii  libgstreamer-plugins-good1.0-0:amd64      1.0.6-1ubuntu1                         amd64        GStreamer development files for libraries from the "good" set
ii  libgstreamer0.10-0:amd64                  0.10.36-1ubuntu2                       amd64        Core GStreamer libraries and elements
ii  libgstreamer0.10-0:i386                   0.10.36-1ubuntu2                       i386         Core GStreamer libraries and elements
ii  libgstreamer1.0-0:amd64                   1.0.6-1                                amd64        Core GStreamer libraries and elements
ii  lubuntu-restricted-addons                 14                                     amd64        Commonly used restricted packages for Lubuntu
ii  phonon-backend-gstreamer:amd64            4:4.7.0really4.6.3-0ubuntu1            amd64        Phonon GStreamer 0.10.x backend
ii  ubuntu-restricted-addons                  14                                     amd64        Commonly used restricted packages for Ubuntu
ii  ubuntu-restricted-extras                  57                                     amd64        Commonly used restricted packages for Ubuntu

```

Does that make any sense to anyone?

Thanks again for all the support, I hope you can still help?

Edit: just found out that mediabuntu repositories are now closed, maybe this helps??

---

### Post by varunendra on 2013-10-10
> **euanbuntu2 said:**
> ```

christmaspudding@Christmas:~$ vlc
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x1029108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

```
That's from when only opening vlc. Try playing the DVD (see post #6) and see what other messages appear in the terminal.

..And..
```

christmaspudding@Christmas:~$ sudo **[COLOR="#FF0000"]/usr/doc/[/COLOR]**libdvdread4/install-css.sh
sudo: /usr/doc/libdvdread4/install-css.sh: command not found

```
Oops !! That has to be "**/usr/[COLOR="#FF0000"]share[/COLOR]/doc....**" not "**/usr/doc**", ....... all blame goes to *mc4man*, I take none.. :P

---

### Post by euanbuntu2 on 2013-10-11
Ok, so after running the correct command I got:

```
christmaspudding@Christmas:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2013-10-11 13:27:45--  [http://packages.medibuntu.org/dists/raring/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/raring/free/binary-amd64/Packages)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-10-11 13:27:45 ERROR 404: Not Found.

Dynamic fetch failed; Falling back to static fetch
--2013-10-11 13:27:45--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-10-11 13:27:51 ERROR 404: Not Found.

```

And after trying to run a dvd, selecting crtl-d and trying to play the dvd I got:

```
christmaspudding@Christmas:~$ vlc
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x2128108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Could not open input: No medium found
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: failed to open/read the DVD
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.css     **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Could not open input: No medium found
libdvdread: Can't open /dev/dvd for reading
[0x7f4934001168] dvdread demux error: DVDRead cannot open source: /dev/dvd
[0x7f4958000b78] main input error: open of `dvd:///dev/dvd' failed
```

Please let me know what you think my next steps should be - I'm on 13.04 raring if that makes a difference?

Thanks again for the continued support :)

---

### Post by varunendra on 2013-10-11
Well-well... now I can see what the sudden fuss about DVDs is all about. That script (the older version that most of us have) tries to pull the packages from the same medibuntu repo that is now closed. So even though *I* didn't add medibuntu repos, the packages eventually came from there.

Fortunately, there is a fix that mc4man already pointed to. You need to follow the instructions in his post he linked to in post #12 : [http://ubuntuforums.org/showthread.php?t=2179777&p=12812210&viewfull=1#post12812210](http://ubuntuforums.org/showthread.php?t=2179777&p=12812210&viewfull=1#post12812210)

In short,
Enable "**Proposed**" repos > Install/Upgrade "**libdvdread4**" to upgrade the script > disable the "Proposed" repos > run the script again -
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

..and come back to say thanks to mc4man (all credit goes to mc4man, I get none :()!

---

### Post by Yellow Pasque on 2013-10-12
@euanbuntu: You're making it overly difficult... 
```
cd ~/
wget http://download.videolan.org/pub/ubuntu/raring/libdvdcss2_1.2.13-0_amd64.deb
sudo dpkg -i libdvdcss2_1.2.13-0_amd64.deb
```

---

### Post by zer010 on 2013-10-12
Thanks, Temujin!  That's a LOT easier.  I just reinstalled Lubuntu 13.04 and have been going about changing what I want and then I ran into the DVD issue.  Perhaps you should volunteer your solution to the Documentation.  I'm sure it would be much appreciated.  Once again, thanks.

Edit: I have submitted Temujin's fix with credit due as a Document bug report.  Hopefully, it will be updated soon.

---

### Post by Yellow Pasque on 2013-10-12
@zer010: You're welcome. Those exact instructions only work for raring 64-bit, so I hope you noted that.

> Perhaps you should volunteer your solution to the Documentation.
I'm hoping that the updated dvdread packages go from proposed to main repos any time now and make workarounds unnecessary...

---

### Post by Yellow Pasque on 2013-10-12
A more generalized solution:

```
cd ~/
wget http://download.videolan.org/pub/ubuntu/`lsb_release -c -s`/libdvdcss2_1.2.13-0_`dpkg --print-architecture`.deb
sudo dpkg -i libdvdcss2*
```

---

### Post by mc4man on 2013-10-12
Updated libdvdread4 packages were released today for 12.04,12.10 & 13.04 so the script will again work fine.

---

### Post by euanbuntu2 on 2013-10-13
> **Temüjin said:**
> @euanbuntu: You're making it overly difficult... 
```
cd ~/
wget http://download.videolan.org/pub/ubuntu/raring/libdvdcss2_1.2.13-0_amd64.deb
sudo dpkg -i libdvdcss2_1.2.13-0_amd64.deb
```

Thanks for this. 

To be honest, I haven't the first idea of what I am or am not doing - I'm simply asking for help :)

---

### Post by euanbuntu2 on 2013-10-13
> **varunendra said:**
> Well-well... now I can see what the sudden fuss about DVDs is all about. That script (the older version that most of us have) tries to pull the packages from the same medibuntu repo that is now closed. So even though *I* didn't add medibuntu repos, the packages eventually came from there.

Fortunately, there is a fix that mc4man already pointed to. You need to follow the instructions in his post he linked to in post #12 : [http://ubuntuforums.org/showthread.php?t=2179777&p=12812210&viewfull=1#post12812210](http://ubuntuforums.org/showthread.php?t=2179777&p=12812210&viewfull=1#post12812210)

In short,
Enable "**Proposed**" repos > Install/Upgrade "**libdvdread4**" to upgrade the script > disable the "Proposed" repos > run the script again -
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

..and come back to say thanks to mc4man (all credit goes to mc4man, I get none :()!


Hello and thank you to everyone - can't remember if I said so before, but I'm fairly new to ubuntu and getting one's head around the commands is quite a thing and so to thave the support here is fantastic. Now I'm going to find a ubuntu guide and learn exactly what both of you mc4man and temujin have just walked me through!

---

### Post by varunendra on 2013-10-13
> **euanbuntu2 said:**
> Now I'm going to find a ubuntu guide and learn exactly what both of you mc4man and temujin have just walked me through!

Like mc4man mentioned in his last post (and I just verified from [here]("http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/")), the updated package has been added to the "universe" repository. So just do an update/upgrade with the following commands -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
..then run the script again (which would be a fixed version now) -
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

This time, the script will use videolan site, not medibuntu, for downloading the required packages.

---

### Post by 8Qnf0bne on 2013-10-20
Varun thank you I'm totally new to this whole Ubuntu universe (less than a week) dvd's are now playing but still no luck with blue ray's

---

