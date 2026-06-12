---
title: "No Preferences in Sonata"
date: 2009-04-28
forum: Multimedia Software
---

### Post by Kizsde on 2009-04-28
Hi!

I have a really weird issue in Ubuntu 9.04 lately. I was looking for a simple clean media player and found out about MPD+Sonata. I'm not really an ubuntu guru, so I tried to figure out the settings and configurations to use as Sonata doesn't work 'out-of-the-box' as other players do. I tried to follow some guides on the web, but none were really for my skills (although I think I managed to configure MPD correctly by the end). The main problem is that in Sonata, I tried to set the path for my music files (which are on an NTFS drive) and it didn't seem to import anything. So i deleted the default profile and tried to create a new one, but Sonata crashed on me. After that, whenever I went to Sonata I could not open the preferences anymor, I clicked on it but nothing happened. The 'Connections' sections only contained 'Disconnected' and there was no way I could bring up the preferences menu (not with F5 either). Now I tried to uninstall/re-install Sonata through the default Add/Remove function and also through Synaptic, but it didn't fix the issue. I don't really know how to do a clean install of Sonata, with the default settings, so I could access preferences again:confused: Also if anyone knows a good, simple, straight to the point guide on how I can set up MPD+Sonata so it can import my music from a Windows drive, I would greatly appreciate it!

I hope this wasn't too confusing and sorry for being lame :lolflag:

Thanks in advance for any suggestions!

Kizsde

---

### Post by mcduck on 2009-04-28
First, try removing Sonata's configuration fiels from your home directory to reset its settings (reinstalling the program doesn't do that). You'll find the files in ~/.config/sonata.

Then, you should set the music directory in MPD's settings (/etc/mpd.conf) instead of Sonata. In the end it's MPD that's playing your music and handlng the music library, not Sonata.

---

### Post by Kizsde on 2009-04-28
Thanks for the advice, I'll check the config file when I get near my home computer again. Also, does that mean that if I edit the mpd.conf file, I won't have to change anything in the preferences of Sonata (just leave it as it is)?

Thanks!

Kizsde

---

### Post by andrewabc on 2009-04-28
Getting sonata and mpd working on ubuntu is damn near impossible. I went to sonata IRC for several hours and someone was nice enough to help me out.

I had to write down the steps to get them working:



To get sonata/mpd running need to install
paprefs

Enable network access to local sound devices
	Don't require authentication

Make sure music_directory in mpd.conf is pointing to where music located.
music_directory		"/media/disk/Music"

In sonata:
Music directory point to /media/disk/Music (same as where music is located)

Then create your database
sudo mpd --create-db

In mpd.conf you need to change audio settings to:
audio_output {
type	"pulse"
name	"My MPD Pulseaudio Output
}

And that should help you out some.

---

### Post by Kizsde on 2009-04-28
Hi andrewabc!

Thanks for your reply, I'm gonna check what you suggested also, when I get home. 
By the way, I'm sure this was asked a thousand times before, but I wonder if there is a music player in Ubuntu which has the functionality of foobar2000. What I would really need is to see my music library in the player as a tree structure (like the same layout as it is on the drive). I have a lot of custom song compilations, from various artists in specific folders and when they get imported into e.g.: Rhythmbox or Banshee, then the player just sorts the songs by album, artist etc. This way I need to search for the songs separately or create a specific playlist for them (which is kind of time consuming). There may be a view/browser in some players which shows the songs/folders as they are on the drive that I'm not aware of, so any suggestions would be helpful!!


Thanks again,


Kizsde

---

### Post by mcduck on 2009-04-28
> **Kizsde said:**
> Thanks for the advice, I'll check the config file when I get near my home computer again. Also, does that mean that if I edit the mpd.conf file, I won't have to change anything in the preferences of Sonata (just leave it as it is)?

Thanks!

Kizsde

Exactly. I've never done anything for Sonata's settings, and haven't really even changed much in mpd.conf either. I've found the easiest way to be to just link my music directory into MPD's defalt music directory. Pretty much wors out-of-the-box unless you need to change the audio output settings.

---

### Post by Kizsde on 2009-04-28
I just checked for the config file of Sonata, but can't really find it....I must admint I can't really find a .config folder either. Any suggestions?

---

### Post by mcduck on 2009-04-29
It's a hidden directory (inside your home), press Ctrl-h to show it in the file manager.

---

### Post by Kizsde on 2009-04-29
Ahh, ok, I told you I was an amateur :) I found the config file and managed to delete it and the preferences came back, woooo! Now I also changed the path in mpd.conf so that is pointing to my main music folder, but after I start Sonata still nothing is imported. I really just changed the 'music_directory' path. Sorry to be a pain :) Also in andrewabc's guide, what does he mean by "enable network access to local sound devices"?

Thanks!

---

### Post by Kizsde on 2009-04-30
**BUMP**

Any suggestions??

---

### Post by mcduck on 2009-05-05
> **Kizsde said:**
> Ahh, ok, I told you I was an amateur :) I found the config file and managed to delete it and the preferences came back, woooo! Now I also changed the path in mpd.conf so that is pointing to my main music folder, but after I start Sonata still nothing is imported. I really just changed the 'music_directory' path. Sorry to be a pain :) Also in andrewabc's guide, what does he mean by "enable network access to local sound devices"?

Thanks!

Try using MPD's default directories and symlinking your music directory there instead of changing MPD to use your own directory directly.

Since MPD runs as it's own user file & directory permissions can become a problem (so if you have copied any of your music files from windows file systems make sure that all the files & directories have sane permissions). Using symlinks and the default directories makes things easier and also allows adding music from many user's accounts to MPD.

For example on my machine MPD's music directory is /var/lib/mpd/music, which is the default. To add my music to the library I simply ran a command "sudo ln -s /home/mcduck/Music /var/lib/mpd/music/mcduck" and then updated MPD's database.

I also decided to add music from my removable hard drive, with "sudo ln -s /media/Helios/mcduck/Music /var/lib/mpd/music/helios". Now those files are accessible as well when ever the drive is plugged in (alhough I need to remember to plug the removable drive in before updating MPD database)

If you only have one user, and one place where all your music is, you can of course link it directly to /var/lib/mpd/music instead of /var/lib/mpd/music/*somedir*.

I'm not sure what the "enable network access to local sound devices" means, during the years I've used MPD as my music player of choice I've never used that setting. I'd suspect it has something to do with using MPD together with some audio streaming service to allow playing the music on a remote machine (instead of just remote controlling the MPD machine). I also have never even heard of the "paprefs" package he suggested. I don't know what it is, but MPD & Sonata definitely work fine without. ;)

I've been using MPD for years now, and every time I install it I seem to do less and less configurations. These days I just install MPD, ncmpc and Sonata packages, link the music directories I want, change the mixer setting in /etc/mpd.conf, restart MPD and update the library. Takes less than 5 minutes to get MPD working. :D

---

### Post by Kizsde on 2009-05-07
> **mcduck said:**
> Try using MPD's default directories and symlinking your music directory there instead of changing MPD to use your own directory directly.

Since MPD runs as it's own user file & directory permissions can become a problem (so if you have copied any of your music files from windows file systems make sure that all the files & directories have sane permissions). Using symlinks and the default directories makes things easier and also allows adding music from many user's accounts to MPD.

For example on my machine MPD's music directory is /var/lib/mpd/music, which is the default. To add my music to the library I simply ran a command "sudo ln -s /home/mcduck/Music /var/lib/mpd/music/mcduck" and then updated MPD's database.

I also decided to add music from my removable hard drive, with "sudo ln -s /media/Helios/mcduck/Music /var/lib/mpd/music/helios". Now those files are accessible as well when ever the drive is plugged in (alhough I need to remember to plug the removable drive in before updating MPD database)

If you only have one user, and one place where all your music is, you can of course link it directly to /var/lib/mpd/music instead of /var/lib/mpd/music/*somedir*.

I'm not sure what the "enable network access to local sound devices" means, during the years I've used MPD as my music player of choice I've never used that setting. I'd suspect it has something to do with using MPD together with some audio streaming service to allow playing the music on a remote machine (instead of just remote controlling the MPD machine). I also have never even heard of the "paprefs" package he suggested. I don't know what it is, but MPD & Sonata definitely work fine without. ;)

I've been using MPD for years now, and every time I install it I seem to do less and less configurations. These days I just install MPD, ncmpc and Sonata packages, link the music directories I want, change the mixer setting in /etc/mpd.conf, restart MPD and update the library. Takes less than 5 minutes to get MPD working. :D
Hi mcduck!

I appreciate all your help, it's really nice to see that there are such helpful ppl here. Unfortunately I'm hitting my head against the keyboard now :D I think I messed up MPD conf pretty good, so what I'm thinking is to uninstall mpd, sonata, ncmpc, then reinstall them and start from scratch.

Also can you elaborate on how you do it on your own system...like the whole procedure from start to finish (like what you type?, where?, when?) I wish I could see the procedure as a whole and not just tidbits....I'm sorry I really am a loser when it comes to this whole linking and changing conf settings...guess windows sucked my brain out!!!

Thanks in advance...again..

K

UPDATE: WOOOOOOOOOO! I actually managed to get Sonata working :D. I just scrapped the whole mpd.conf and started from scratch and managed to configure it the proper way.....although I'm not sure what was wrong before.

Thanks for the help everyone!!!!!

---

