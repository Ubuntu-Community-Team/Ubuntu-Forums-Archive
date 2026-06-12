---
title: "VLC is unable to open the MRL"
date: 2022-03-13
forum: Multimedia Software
---

### Post by JamButty on 2022-03-13
Something has changed recently with VLC and DVD playback. Codecs are good, been doing the
```
sudo apt-get install libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg
```
bit for years after each new re-install. But now, DVDs I played without problem just a month or two ago pull this error as a popup
```
Your input can't be opened:
VLC is unable to open the MRL 
```
and the VLC log reads:
```
&#65279;-- logger module started --
main: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
filesystem error: read error: Input/output error
cache_read error: cannot pre fill buffer
mjpeg error: cannot peek
```

every online reference to this I find is concerned with VLC playing streaming media (youtube etc.), but these are standard commercial DVDs playing from the main CD/DVD tray. The log output is the same whether auto-opening the DVD on mount or trying to play initial files in VIDEO-TS directly, but the pop-up only appears when trying to play the VIDEO_TS files directly.
I am stumped.

---

### Post by #&amp;thj^% on 2022-03-13
What shows here:
```
apt policy libdvdcss2
```
Or
```
dpkg -l *libdvdcss* | grep ii
```
Also with DVD playing run:
```
DVDCSS_VERBOSE=2

```
may give more information.
Other Steps to take:
Reset your preferences. (you would be suprised how often this fixes problems)
If that dose not solve the issue.>>>Use a script:
first download this script: [https://github.com/videolan/vlc/blob/master/share/lua/playlist/youtube.lua](https://github.com/videolan/vlc/blob/master/share/lua/playlist/youtube.lua)
Lets find our file with:
```
locate youtube.luac
```
Mine was here:
```
/usr/lib/x86_64-linux-gnu/vlc/lua/playlist/youtube.luac
/usr/share/doc/vlc/lua/playlist/youtube.lua.gz ###Don't worry about this line

```
copy and paste it to a text file, named example "youtube.luac"
now replace this with the new youtube.luac file.
```
sudo cp ~/Downloads/youtube.lua /usr/lib/x86_64-linux-gnu/vlc/lua/playlist/youtube.luac
```
Should be Good to Go.

---

### Post by JamButty on 2022-03-14
```
$ apt policy libdvdcss2
libdvdcss2:
  Installed: 1.4.2-1~local
  Candidate: 1.4.2-1~local
  Version table:
 *** 1.4.2-1~local 100
        100 /var/lib/dpkg/status
$ dpkg -l *libdvdcss* | grep ii
ii  libdvdcss-dev:amd64 1.4.2-1~local amd64        library for accessing encrypted DVDs - development files
ii  libdvdcss2:amd64    1.4.2-1~local amd64        library for accessing encrypted DVDs
$ DVDCSS_VERBOSE=2
$ 

```

I could not run "DVDCSS_VERBOSE=2" while DVD is running as no DVD file will run at all, so I ran it immediately after attempting a VLC play. I did reset the VLC preferences. All that did was make my log file disappear. I went through a song and dance about a year ago just to force VLC to even produce a logfile I could easily find, so I need to research again to see/remember how I did that.
I am still trying to process what the script is about.
Thanks.

---

### Post by JamButty on 2022-03-14
Also tried removing snap-VLC and installing non-snap version - no change.

---

### Post by #&amp;thj^% on 2022-03-14
> **JamButty said:**
> 
I am still trying to process what the script is about.
Thanks.
Simply "youtube.lua", was preventing videos with copyright-claimed material from being played. (This changes more often than one would expect)
Back-up your old one first then, add the New one and enjoy.
If not then there is something else wrong.
Side Note Snap Version of VLC just not an option for me. (Snaps just leave a bad taste in my usage).

---

### Post by JamButty on 2022-03-14
sooooo...since the "youtube.lua" file at that address is text and VLC is expecting a binary LUAC file, I assume I would need to compile it, which I have no idea how to do, me being a basic user, not a programmer. Also unclear why a module designed to mediate streaming online data would mediate commercial DVDs. 
I got the logfile going again, changed the output level to "debug" and got reams of output, most of which I understood nothing of, but it seemed clear that even when it found files it needed (e.g. meta fetcher module, art finder module, access_demux module, meta fetcher module etc.) it either did not find the portions  inside each it needed or was entirely unable to open them.
Since some of the online solutions aimed at Windows users mentioned file ownership issues as a possible problem, I had a hunch that running VLC from the command line (as root if needed) might help. Hey presto! Tested several DVDs and all work running from the command line (even without root privs). Further the logfile now shows VLC happily finding files it could not find before and even autostarting VLC on mount now works for some DVDs, not all. Can't say I understand it, but it works.

TL;  DR- running VLC from the command line eliminated problem.

---

### Post by #&amp;thj^% on 2022-03-14
> **JamButty said:**
> sooooo...since the "youtube.lua" file at that address is text and VLC is expecting a binary LUAC file, I assume I would need to compile it, which I have no idea how to do, me being a basic user, not a programmer. Also unclear why a module designed to mediate streaming online data would mediate commercial DVDs. 

As I said **any** It's preventing videos with copyright-claimed material. (DVD's fall in here)
Not sure why running from the terminal would make a difference though, unless left-over stuff from Snap version is lingering.
And no you don't have to compile anything, the changed script should be enough.

---

### Post by JamButty on 2022-03-15
I am baffled too - why it suddenly became inoperable and then why a command line start without root privs helps. But it works. Thanks for your input.

---

### Post by JamButty on 2022-03-15
I am baffled too - why it suddenly became inoperable and then why a command line start without root privs helps. But it works. Thanks for your input.

---

