---
title: "Would like to have MPD+Sonata.."
date: 2011-01-05
forum: Multimedia Software
---

### Post by Smile88 on 2011-01-05
I'm a new Xubuntu user (new to Linux) and am looking for a nice audio player. Tried a lot out, but none of them really suited me. Music Player Daemon with Sonata seemed like a nice combination, but I'm have troubles installing it.

I think I managed to install both programs, but can't seem to find music through Sonata. 

I found the guide on this site..
[https://help.ubuntu.com/community/MPD#Music](https://help.ubuntu.com/community/MPD#Music) Player Daemon (MPD)

> 
Configuring MPD to run as a system service
In Ubuntu, much of the work is done for you with regard to setting up the proper directories and permissions. However, there is still some customization to be done.

Editing /etc/mpd.conf
Almost all of the default /etc/mpd.conf can be left untouched, but there are some things that you may want to change. First of all, it is always a good idea to make a backup of the file in case things go south.

$ sudo cp /etc/mpd.conf /etc/mpd.conf.bak

But when I put the above command into the Terminal, nothing happens. Does that mean it's working or not?

Then I tried the next command to edit the files.. 

> 
And now the editing begins.

$ sudo gedit /etc/mpd.conf

And it gives:

sudo: gedit: command not found

Any ideas?

---

### Post by Version Dependency on 2011-01-05
> **Smile88 said:**
> 
I found the guide on this site..
[https://help.ubuntu.com/community/MPD#Music](https://help.ubuntu.com/community/MPD#Music) Player Daemon (MPD)

That guide is seriously lacking.  Because you will have to change a few things in the mpd.conf file to get things to work properly.  The following three lines I remember needing to edit to get mpd to work on my PC.

```
music_directory        "/home/USERNAME/Music"
``````
user                "root"
``````
bind_to_address        "127.0.0.1"
```> **Smile88 said:**
> 
But when I put the above command into the Terminal, nothing happens. Does that mean it's working or not?


Don't worry.  It worked.

> **Smile88 said:**
> 
Then I tried the next command to edit the files...

And it gives:

sudo: gedit: command not found

I'm not a Xubuntu user but is Gedit installed by default in Xubuntu?  If not replace "gedit" with the command for whatever the XFCE text editor is (mousepad or leafpad possibly???). 

Best of luck!

---

### Post by snapback77 on 2011-01-09
This will work to get you to mpd.conf.
nano ~/.mpdconf  Copy and paste in terminal and you are in.

---

### Post by snapback77 on 2011-01-09
This will work to get you to mpd.conf.
nano ~/.mpdconf    Copy in Terminal and you are in

---

### Post by Smile88 on 2011-01-11
Thanks for the responses. I've edited the file exactly as Version Dependancy explained. But when I open Sonata, I'm still not seeing my music files. Is it because of wrong settings in Sonata, or because I still need to set up things regarding MPD, after editing the file?

---

### Post by aeiah on 2011-01-11
you may need to restart the music playing daemon and tell it to update its self first

---

### Post by Smile88 on 2011-01-11
Maybe a silly question but how do I start the MPD?

---

### Post by snapback77 on 2011-02-14
I have Sonata and MPD running.  I hope to help you.
1. If you see "not connected" when you open Sonata, 
you need to start MPD.
Open terminal and paste: sudo /etc/init.d/mpd restart
That should start it up.  

2. If you do not see your songs in Sonata library tab, you need to make a symbolic link between MPD database and your Music folder.  To do this paste in terminal:  sudo ln -s /home/yourusername/Music /var/lib/mpd/music/yourusername  

Where you see yourusername if it is smile88 then that is what you write.
 
You should see in Sonata all the song you have store in your Music folder.

3. If you clik play and it starts without sound, then you need to follow the instructions I discovered here. [http://ubuntuforums.org/showthread.php?t=1298789](http://ubuntuforums.org/showthread.php?t=1298789)


[I][I]How to get MPD working with pulseaudio in Karmic Koala (Ubuntu 9.10)

   1. Install pulseaudio prefs (paprefs) from synaptic or open a terminal and enter...

      Code:

      sudo apt-get install paprefs

   2. Open PulseAudio prefrences from the menu System->Prefrences->PulseAudio Preferences
   3. Click the Network Server tab
   4. Check the box "Enable network access to local sound devices"
   5. Check the box "Don't require authentication"
   6. Next enable pulse in your mpd.conf file,in a terminal enter...
      Code:

      gksudo gedit /etc/mpd.conf

   7. In the audio output section add these lines...

      Code:

      audio_output {
          type "pulse"
          name "My Pulse Device"
      }

   8. Finally restart mpd,in the terminal enter...
      Code:

      sudo /etc/init.d/mpd restart

   9. Open up your favourite client -- sonata, ncmpc, mpc -- & enjoy.

That should get you enjoying your music with Sonata and MPD.  If you need more clues you can search in the forum for mpd gmpc working but no sound.
That is my thread marked solve with how I finally got it going.

Kenneth

---

### Post by Smile88 on 2011-03-09
> **snapback77 said:**
> I have Sonata and MPD running.  I hope to help you.
1. If you see "not connected" when you open Sonata, 
you need to start MPD.
Open terminal and paste: sudo /etc/init.d/mpd restart
That should start it up.  


Thanks for your help.

But when I paste this I get:

"failed to stat music directory "/home/james/music": No such file or directory"

---

### Post by Version Dependency on 2011-03-09
> **Smile88 said:**
> Thanks for your help.

But when I paste this I get:

"failed to stat music directory "/home/james/music": No such file or directory"

In the default Ubuntu installation, I believe that the Music folder is capitalized.  May make a difference, so try "/home/james/Music"

---

### Post by Chronon on 2011-03-11
It does make a difference.  The file system is case sensitive.

---

### Post by Smile88 on 2011-03-14
Ah! How stupid of me. 

Ok, well I edited the file again to replace the m with a capital letter. :P And now Terminal gave me:

Usage: /etc/init.d/mpd {start|start-create-db|stop|restart}

I suppose this means that it started.

However, I still can't see any music files in Sonata, so I pasted:
sudo ln -s /home/james/Music /var/lib/mpd/music/james

But it seems like nothing really happened. Still can't see any files in Sonata.

---

### Post by Chronon on 2011-03-14
When a program prints usage info, it usually means that you didn't provide expected input.  If this is your first time running it, I would try this one:
```
sudo /etc/init.d/mpd start-create-db
```

---

