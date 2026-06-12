---
title: "Bypass MTP: wireless android syncing with banshee and SSHFS"
date: 2012-12-04
forum: Multimedia Software
---

### Post by HibyPrime on 2012-12-04
**How to use SSHFS to wirelessly sync an android phone with banshee on ubuntu, bypassing all that MTP mess that just doesn't work properly.**

I recently decided to full switch to ubuntu, dropping my dual-boot setup with windows.  Of the few things I was worried about, syncing my Galaxy Nexus was one of the biggest problems.  MTP support in linux is just terrible, and the nexus doesn't have USB mass storage support.

I managed to get Banshee to sync with my galaxy nexus, wirelessly!  It's one hell of a work around, but once up and running it's reasonably simple to use.  The first step is to install SSHDroid on your phone (doesn't require root). On your PC, use SSHFS (included in the main ubuntu repos) to mount your phone to a folder:

```
person@coolcomputer:$ sshfs root@192.168.*.*:/sdcard/music -p (port) ~/nexus
```

I wasn't able to get /sdcard to mount, you might need root on your phone for that, I'm not sure.  /sdcard/anything works fine though.  Once that's done you need to install banshee and an extension called foldersync:

[http://packages.ubuntu.com/precise/banshee-extension-foldersync](http://packages.ubuntu.com/precise/banshee-extension-foldersync)

Open up banshee and create a playlist you want to sync.  Note that foldersync doesn't work with smart playlists (which sucks), but you can use a smart playlist and when ready to sync simply ctrl-a the smart playlist and drag into a normal one. 

Go to tools -> Syncronize to folder.  

Here's the tricky part thats kind of hard to figure out without someone telling you.  This screenshot shows a column that is hidden by default:

[https://dl.dropbox.com/u/14469783/foldersync.png](https://dl.dropbox.com/u/14469783/foldersync.png)

You need to drag it out from the vertical spacer, I had to turn on cover art (view -> show cover art) and drag near the bottom before it would show up.  Once that's done, select the playlist you want to sync, select the destination, and voila!

Once it's complete, there are 3 downsides to this:
1. It's slow, I can't get a speed off of it, but it takes ~10 seconds per song.  Definitely an over-night thing
2. Can't sync smart playlists directly
3. It won't delete old music that is no longer in the sync playlist.

But it syncs wirelessly over SSH!  That has to be worth something right?!

---

### Post by Abdi110 on 2013-02-07
Hi there, this is a one line rsync that I scraped together to sync up content from a m3u playlist (which Banshee can spit out if you right click on a playlist) to my Android over an SSHFS mount...

```
rsync -vhrlptoD --delete --delete-excluded --prune-empty-dirs --modify-window=1 --progress --stats --include-from=<(</home/rubin110/music/library/z-fill.m3u sed -e 's/[*?\[]/\\&/g') --include='*/' --exclude='*' /home/rubin110/music/library/ /media/flamboyantssh/extSdCard/Music/
```

It should update the music content on your device, by deleting music which isn't in the playlist anymore, adding new tracks it doesn't have, and retaining anything else that hasn't changed. I would recommend checking out what all those options I have listed do through rsync's man page before running first. Also --dry-run is a really handy option when you're testing out this stuff.

---

### Post by Fran on 2013-04-06
Thanks for the very helpful one-liner.  I found that [SSHelper]("https://play.google.com/store/apps/details?id=com.arachnoid.sshelper") makes this even simpler to use: you can rsync directly to the android device.

---Fran

---

