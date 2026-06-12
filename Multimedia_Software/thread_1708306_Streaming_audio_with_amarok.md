---
title: "Streaming audio with amarok"
date: 2011-03-16
forum: Multimedia Software
---

### Post by pwabrahams on 2011-03-16
I'm trying to play the content of a streaming audio website with amarok.  (I can actually get it to work with Firefox and Flash, but that's not my preferred Linux-y solution.)  The website is:[http://www.earlymusicradio.co.uk/10.html]("http://www.earlymusicradio.co.uk/10.html").  It has a "play now" button which invokes Flash (and doesn't seem to work with Konqueror), plus choices for "RealPlayer". "Winamp and Itunes", and "Other players".  The URL for "Other Players" is [http://public.wavepanel.net/DZRMW4UMOE2OX733/listen/m3u]("http://public.wavepanel.net/DZRMW4UMOE2OX733/listen/m3u"). I copied that URL into amarok's Playlist / Add Stream URL box, but nothing happened when I tried to play it. (Same for the other players.)  How can I get Amarok to play this stream?

Two other related questions: once I have it playing, is there a way to capture it?  And where in Amarok can I keep a list of streams I'm interested in?

---

### Post by SeijiSensei on 2011-03-16
I'm using [Clementine]("http://code.google.com/p/clementine-player/"), the rebuild of Amarok 1.4 for KDE4.  There I went to Playlist > Add Stream and entered the URL you gave.  It immediately started playing.  Maybe the procedure is similar in Amarok 2?

I didn't like the new Amarok much, nor did a lot of other users.  I was happy to see someone continue to maintain the 1.x code under the new name Clementine.  It's in the repositories: "sudo apt-get install clementine".

---

### Post by pwabrahams on 2011-03-16
I'd really prefer to solve the problem with Amarok, but I decided to try Clementine anyway.  But here's what I got:```
pwa@pwa-K60IJ:~/Downloads/mpg123-0.59q$ clementine
Clementine(20355)/ KSharedDataCache::Private::mapSharedMemory: Opening cache "/var/tmp/kdecache-pwaQgiuQP/icon-cache.kcache" page size is 4096
Clementine(20355)/ KSharedDataCache::Private::mapSharedMemory: Attached to cache, determining if it must be initialized
Clementine(20355)/ KSharedDataCache::Private::mapSharedMemory: Cache fully initialized -- attached to memory mapping
Clementine(20355)/ KSharedDataCache::Private::mapSharedMemory: 4317184 bytes available out of 10485760
Clementine(20355)/ KIconCache::Private::themeDirsChanged: Theme directory has been modified
Couldn't load icon "clementine-panel" 
Couldn't load icon "clementine-panel-grey" 
virtual bool QxtGlobalShortcutBackend::DoRegister() 
QxtGlobalShortcut failed to register: "Media Next" 
QxtGlobalShortcut failed to register: "Media Play" 
QxtGlobalShortcut failed to register: "Media Previous" 
QxtGlobalShortcut failed to register: "Media Stop" 
Updating "songs" for %allsongstables 
Updating "magnatune_songs" for %allsongstables 
Updating "songs" for %allsongstables 
Updating "magnatune_songs" for %allsongstables 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/pwa/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
Loading remote file  QUrl( "http://public.wavepanel.net/DZRMW4UMOE2OX733/listen/m3u" )  
Segmentation fault

```

Stymied!

---

### Post by pwabrahams on 2011-03-16
Installing clementine had a very unwelcome side effect: amarok now produces no sound.  Uninstalling clemeintine and reinstalling amarok didn't help.  Nor did rebooting.  Perhaps the cause lies elsewhere, but I don't know.  I also get a message to the effect that hda-intel sound isn't working, but sound does work in applications other than amarok.

---

### Post by johntaylor1887 on 2011-03-17
> **SeijiSensei said:**
> I'm using [Clementine]("http://code.google.com/p/clementine-player/"), the rebuild of Amarok 1.4 for KDE4.  There I went to Playlist > Add Stream and entered the URL you gave.  It immediately started playing.  

I like Clementine. The original Amarok was pretty good.

---

### Post by SeijiSensei on 2011-03-17
Did you install clementine from the repositories?  It shouldn't be segfaulting.

You've got something funky going on with your sound system settings I think.  I just retested both Amarok and Clementine side-by-side, and they both play correctly on my system which also has Intel HDA audio.  I'm using a pretty vanilla Kubuntu 10.10 except for upgrading to KDE 4.6 via the backports repository.

Try looking in System Settings > Multimedia > Phonon and check to make sure you've got the right settings.  If that doesn't fix the problem, I'd try uninstalling and reinstalling pulseaudio.

---

### Post by HannuMR on 2011-03-17
Clementine

sudo add-apt-repository ppa:me-davidsansome/clementine

sudo apt-get update

sudo apt-get install clementine

---

### Post by SeijiSensei on 2011-03-17
I didn't need a PPA.  The version of Clementine in the standard Ubuntu repositories works fine here.

---

### Post by pwabrahams on 2011-03-17
I installed clementine from this repository:[http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu]("http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu") and it segfaults on the stream URL  **[http://lush.wavestreamer.com:9171/](http://lush.wavestreamer.com:9171/)**.  If I provide that URL to amarok, it just does nothing with it.  But if I provide the playlist file containing that URL to mplayer, it plays correctly.  For some reason that's not clear to me, amarok and clementine both want a URL, not the location of an m3u file containing that URL.  Dragon Player also does nothing with the URL.

I've reinstalled pulseaudio and added myself to the audio group.  It makes no difference.

I cannot make sense of this, but the fact that mplayer can play the playlist file proves that the necessary componentry for playing mp3 streams is alive and well.

---

### Post by mc4man on 2011-03-17
Well I have amarock 2 installed on 11.04 to test, generally prefer amarok 1.4 for use. (find amarok 2 very frustrating app.

Anyway no real issue with your stream - 2 ways
If entering the url just used the actual - 
[http://lush.wavestreamer.com:9171/](http://lush.wavestreamer.com:9171/)
amarok played it fine.

A bit more useful was to download the listen.m3u, and add the folder it was in the folders for amarok to scan
(in this case Downloads, normally would just create a folder to keep .m3u's in
After re-scanning amarok was able to find and use the .m3u (listen.m3u) in "Playlist Files on Disk"
(media sources -> saved playlist -> Playlist Files on Disk
see screen

---

### Post by pwabrahams on 2011-03-17
I installed clementine from this repository:[http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu]("http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu") and it segfaults on the stream URL  **[http://lush.wavestreamer.com:9171/](http://lush.wavestreamer.com:9171/)**.  If I provide that URL to amarok, it just does nothing with it.  But if I provide the playlist file containing that URL to mplayer, it plays correctly.  For some reason that's not clear to me, amarok and clementine both want a URL, not the location of an m3u file containing that URL.  Dragon Player also does nothing with the URL.

I've reinstalled pulseaudio and added myself to the audio group.  It makes no difference.

I cannot make sense of this, but the fact that mplayer can play the playlist file proves that the necessary componentry for playing mp3 streams is alive and well.

---

### Post by pwabrahams on 2011-03-18
I tried running a couple of the streams preset into amarok.  The first one was Afterhours under Cool Streams.  Same result: the time counter is stuck at zero even when I click on "play".  I get that whether I use an m3u file or the actual URL stored in it.  So streams don't work no matter how I access them, it seems.

I wondered if perhaps there was some problem playing mp3s under amarok, but I was able to play one that was stored in a file.  So that's not the difficulty.  I wonder if for some reason amarok has trouble accessing the Net, even though the rest ot my system doesn't.  This also might be specific to my Kubuntu version (10.10) and amarok version (2.3.2).

It's very puzzling why I have so much trouble with this when it works so smoothly for you.

Another useful bit of information: I tried running Amarok in Natty via Virtual Box.  Streams work fine for me there.  So the problmm has something to do with versions, it seems.

---

