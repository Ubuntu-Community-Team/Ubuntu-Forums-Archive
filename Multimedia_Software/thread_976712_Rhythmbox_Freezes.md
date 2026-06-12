---
title: "Rhythmbox Freezes"
date: 2008-11-09
forum: Multimedia Software
---

### Post by bockman on 2008-11-09
Hello all,

Notwithstanding the issues in [this link]("http://ubuntuforums.org/showthread.php?t=976646"), rhythmbox will completely lock up for me, but only occasionally. Personally I can reproduce this in several ways, but not everyone can.

[LIST=1]
[*]Stopping and starting an internet radio stream several times
[*]Transferring large amounts of data over a CIFS mount (not the GNOME way, with the mount command)
[*]Leaving it open too long
[/LIST]

So, I know these are nebulous and vague, but I can't reproduce them with any reliability. Sometimes it will lock up for no apparent reason. Once in awhile it'll jump to 100% CPU usage and just stay like that. This is all, of course, running 8.10. None of these issues occured in the same way in 8.04. I would file a bug report, but I don't even know if I can be specific enough to do so.

Has anyone experienced the same kinds of issues?

---

### Post by rotwang888 on 2008-11-09
Yeah, I have.  Wasn't a problem in Hardy.  I don't play music in Rhythmbox much, but I use it to download podcasts, and after the change to Intrepid it usually will freeze up after each download.

---

### Post by bockman on 2008-11-10
Does anyone have any suggestions of how to nail these down and submit a bug for them? I'm at a loss, because it doesn't happen every time, but enough to be annoying.

In the mean time I installed rhythmbox-dbg and enabled coredumps. Maybe I'll SIGABRT it to dump core and upload it to launchpad.

---

### Post by bockman on 2008-11-11
I found an Ubuntu brainstorm idea that supports the removal of Rhythmbox as the default. Hopefully this will catch on.

[http://brainstorm.ubuntu.com/idea/15509/](http://brainstorm.ubuntu.com/idea/15509/)

---

### Post by m0m0m0m on 2008-11-18
I do have a similar problem with a freezing rhythmbox, but that doesn't only affect it, but also exaile (which is gtk as well). Basically what happens is if I start the players, they freeze. Sometimes (after many minutes) they work again. But this isn't since intrepid only since a few days.

---

### Post by ranran on 2008-11-18
I'll add my 2C - Rhythmbox freezes with internet streaming as well.

Dell Inspiron 8600, Ubuntu 8.10 (fresh install)

---

### Post by gare on 2008-11-30
Ever since my Ibek upgrade, Rhythmbox has begun freezing as it tries to scan my library (admittedly I have large music library).  

I hate to leave Rhythmbox but do not seem to have choice. :(:(

---

### Post by tylerious on 2009-06-06
I don't really like dredging up an old thread, but this is what Google brought up first.

I'm having this problem (running Intrepid). Rhythmbox freezes without reason, sometimes just a couple minutes into playing a song.

Has anybody found a good fix for this or established what exactly is the problem? Has this issue been resolved for anybody by upgrading to Jaunty?

Thanks!

---

### Post by quill3033 on 2009-12-29
ok finally I am listening to my music w Rhythmbox.

Here is what I did - I have no idea whether this is what made it work but I thought I'd share it just in case. I am still on Hardy. I was just mucking around as I had done search after search and found no solution. 
First I moved the folder that Rhythmbox was scanning so it couldn't scan it anymore. It has some 600 songs. I moved its contents to the desktop and saved in another folder. I only moved something like 10 songs back into the folder that Rhythmbox scans. (I did this because when I had tried to completely uninstall and then reinstall Rhythmbox it would still go back to this folder on reinstall - and get all stuck because there were so many songs in different formats to catalogue/import or whatever it does). 

Then I changed my sound preferences to ALSA instead of PulseAudio. 

Then I right-clicked on a music file and went to Properties --> Open with and changed permission from VLC to Rhythmbox. (I did this because I had been  mucking around on the terminal and trying to open music files from the command line with Rhythmbox and instead of Rhythmbox,  VLC would open (and play) them despite the command only including Rhythmbox... 
Oh and in the plugins I also got rid of most of them just in case - because the error I used to get was that there was no radio device radio0 (don't have the exact output at the moment, sorry). 
I kept the following plugins - Coverart, Power Manager, Portable Players Ipod. 
I plan to add all my songs back into the folder that Rhythmbox scans maybe 10 at a time. In the meantime if I want to play them I can always use another player. 
Hope this helps someone. 
The reason I mucked around so much is that I really love Rhythmbox and that I logged out and tried logging in as another username and used it  without any problems so I thought the problem had to be fixable. 
Btw - this could just be coincidence but I installed the following plugin from Synaptic also around the time I was mucking around looking for a solution.
gstreamer0.10-fluendo-mp3 -Fluendo mp3 decoder GStreamer plugin

One last thing that might be relevant is that I have medibuntu enabled and installed w32codecs and libdvdcss2.  I haven't used their 'updates' for Amarok and Amarok-xine as I remember vaguely that in the past they haven't worked the best for me - ie. Amarok crashes when I install the medibuntu updates for it so... I now keep  it in its original form. I use Amarok mostly for radio streams - it has so many the mind boggles. But I like Rhythmbox for organising my music collection.

I suspect what happened was that (and this is my totally NON TECHNICAL EXPLANATION) 1. I tried importing a whole lot of songs at once which taxed Rhythmbox's capacity, 2. I didn't have codecs installed at that time and a lot of these songs were MP3 and other non-linux formats and Rhythmbox would try to find codecs unsuccessfully, 3. Something to do with PulseAudio 4. Something to do with VLC being the default player for those files (??) :confused:
Anyway, I even downloaded a couple of podcasts today. I'll see if it will automatically update them or not. 
For  now I'm really happy. Sorry I only have intuitive gibberish to contribute but thought I'd share my experience as I am soooo pleased that Rhythmbox is working again - :-):P

---

