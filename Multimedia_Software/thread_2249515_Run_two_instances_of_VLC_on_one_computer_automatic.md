---
title: "Run two instances of VLC on one computer automatically?"
date: 2014-10-22
forum: Multimedia Software
---

### Post by DeathAdder666 on 2014-10-22
Hello All. I've been trying to get a picture and video slideshow to appear on two (2) monitors with one (1) computer running Ubuntu 14.  I'm still a novice at Linux and thought maybe VLC would work.  Basically, I want:

1. Computer to boot up at a certain time (which I can do through the BIOS).

2. Login automatically to Ubuntu 14.04 (64-bit).

3. Start instance #1 of VLC with a specific playlist on monitor #1 

4. Start another instance, #2 on VLC on monitor #2.

5. Shutdown the computer at a certain time to wait for the next boot time.

All of this would be going through a single video card split between two identical monitors in the lobby of my office.  I prefer VLC because the video clips are in different formats and VLC will pretty much play everything.  I'm OK with using VLC on one monitor and another program on the other, if that's what it takes.  But I know you can open multiple instances of VLC on the same computer, just need to figure out how to get that to happen automatically and start up in full screen.

Remember, I'm a novice at this.  I've been a Windows (](*,)) admin forever and wanted to get more into Linux (\\:D/) now.  Please be gentle and thanks.

---

### Post by shantiq on 2014-10-23
Hi adder

let us give you a few pointers to get you started for 3 4 and 5


```
shutdown  --help
```   to shutdown reboot your machine should be of use

examples :

sudo shutdown -h 08:48
sudo shutdown -r 08:49 to reboot
sudo shutdown -h +15


or also **crontab**   for   timing:  

 [http://ubuntuforums.org/showthread.php?t=2112739&p=12496050#post12496050](http://ubuntuforums.org/showthread.php?t=2112739&p=12496050#post12496050)  
[http://www.scrounge.org/linux/cron.html](http://www.scrounge.org/linux/cron.html)

if a gui like vlc   use 

> 0 2 * * * env DISPLAY=:0 nameofguiprogram


as regards vlc

```
vlc -f --run-time=1200  NAMEOFPLAYLIST.m3u 



```    runtime is in seconds   this works with one instance;   multiple instances running is default in vlc


```
 Playlist These options define the behaviour of the playlist. Some of them can be overridden in the playlist dialogue box.
  -Z, --random, --no-random      Play files randomly forever (default disabled)
          VLC will randomly play files in the playlist until interrupted.
          (default disabled)
  -L, --loop, --no-loop          Repeat all (default enabled)
          VLC will keep playing the playlist indefinitely. (default enabled)
  -R, --repeat, --no-repeat      Repeat current item (default disabled)
          VLC will keep playing the current playlist item. (default disabled)
      --play-and-exit, --no-play-and-exit 
                                 Play and exit (default disabled)
          Exit if there are no more items in the playlist. (default disabled)
      --play-and-stop, --no-play-and-stop 
                                 Play and stop (default disabled)
          Stop the playlist after each played playlist item. (default disabled)
      --play-and-pause, --no-play-and-pause 
                                 Play and pause (default disabled)
          Pause each item in the playlist on the last frame. (default disabled)
      --playlist-autostart, --no-playlist-autostart 
                                 Auto start (default enabled)
          Automatically start playing the playlist content once it's loaded.
          (default enabled)
      --playlist-cork, --no-playlist-cork 
                                 Pause on audio communication (default enabled)
          If pending audio communication is detected, playback will be paused
          automatically. (default enabled)
      --one-instance, --no-one-instance 
                                 Allow only one running instance (default
                                 disabled)
          Allowing only one running instance of VLC can sometimes be useful,
          for example if you associated VLC with some media types and you don't
          want a new instance of VLC to be opened each time you open a file in
          your file manager. This option will allow you to play the file with
          the already running instance or enqueue it. This option requires the
          D-Bus session daemon to be active and the running instance of VLC to
          use D-Bus control interface. (default disabled)
      --started-from-file, --no-started-from-file 
                                 VLC is started from file association (default
                                 disabled)
          Tell VLC that it is being launched due to a file association in the
          OS (default disabled)
      --one-instance-when-started-from-file, --no-one-instance-when-started-from-file 
                                 Use only one instance when started from file
                                 manager (default disabled)
          Use only one instance when started from file manager (default
          disabled)
      --playlist-enqueue, --no-playlist-enqueue 
                                 Enqueue items into playlist in one instance
                                 mode (default enabled)
          When using the one instance only option, enqueue items to playlist
          and keep playing current item. (default enabled)
      --media-library, --no-media-library 
                                 Use media library (default disabled)
          The media library is automatically saved and reloaded each time you
          start VLC. (default disabled)
      --playlist-tree, --no-playlist-tree 
                                 Display playlist tree (default disabled)
          The playlist can use a tree to categorise some items, like the
          contents of a directory. (default disabled)
      --open <string>            Default stream
          This stream will always be opened at VLC startup.
      --auto-preparse, --no-auto-preparse 
                                 Automatically preparse files (default enabled)
          Automatically preparse files added to the playlist (to retrieve some
          metadata). (default enabled)
      --metadata-network-access, --no-metadata-network-access 
                                 Allow metadata network access (default
                                 disabled)
          Allow metadata network access (default disabled)
```


as i said just a few ideas to get going ...    good luck

---

