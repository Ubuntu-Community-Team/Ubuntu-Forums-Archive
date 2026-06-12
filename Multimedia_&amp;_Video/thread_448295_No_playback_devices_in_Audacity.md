---
title: "No playback devices in Audacity"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by thoughts on 2007-05-19
I just opened Audacity for the first time in a while, and it's giving me an error about not being able to play audio.  I go to Edit > Preferences, and I see that there are no devices in the menu under "Playback".  Strangely, there are devices in the menu under "Recording", an OSS one and a bunch of ALSA ones.

The last time I used Audacity was back when I was running Edgy, and the sound worked fine then.  I guess this is the first time I've tried to use it since upgrading to Feisty.  But the sound on the rest of my system is fine (Amarok, XMMS, gxine/mplayer/VLC, and browser plugins).

I've removed and reinstalled Audacity a couple of times now (via apt-get) to no avail.  I've also deleted my ~/.audacity file.

I've disabled the sound server in System > Prefs > Sound, and I killed the esd process.

I'm running on a pretty new Core 2 Duo system.  Here's my kernel and sound card info:

```
Linux soma 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

Any ideas?

(I can launch Audacity as "aoss /usr/bin/audacity" and then I get an OSS playback device, but the sound skips and Audacity eventually crashes.)

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by sclough on 2007-05-21
I've got the exact same problem.  Did anyone find a solution for this one?

---

### Post by Daniel15 on 2007-06-05
Me too - I'm encountering this same problem :(.

---

### Post by sclough on 2007-06-05
Ok, here's what I've discovered so far.  This seems to be the pattern.  If I open Audacity and there are no sound output devices, I then open up some sound file that opens in an audio player like Real Player, Totem, etc.  That audio file will play fine.  Close that player.  Then, re-open Audacity and the output devices seems to be there.  

The only twist is that the output devices won't show if you get an error that a device has the sound card locked when you open real player, totem, or whatever.  I think there is a bug in the flash player or one of the Firefox plugins that may be holding onto the soundcard device, because I found the other day that when I tried to do the above steps and Real Player refused to play saying that something else has the audio output locked, I closed down firefox and after that Real Player could play the sound and then I re-started Audacity and voila, the output devices appeared.  It appears that something is not getting initialized correctly or Audacity doesn't deal with other applications getting a lock on the soundcard.  

Either way I'm a little confused on if there is any way to prevent the sound card from being blocked.  I've fooled with my main sound settings and I don't know what the best sound system is to use (alsa/oss/esd).  I've got it currently set to esd, but that hasn't helped with any of this.

What's almost as annoying is when I output mp3s out of Audacity and choose the genre, the list that comes up doesn't have the text populated, so I have to keep clicking around on a blank list until I select the one I want.  This was fine in dapper, so I don't know if this is a feisty/studio bug or an Audacity bug.

BTW, somebody posted this same missing output devices error on the Audacity forums, but at the time I saw it there was no response.

---

### Post by Big_J on 2007-06-21
> **thoughts said:**
> I just opened Audacity for the first time in a while, and it's giving me an error about not being able to play audio.  I go to Edit > Preferences, and I see that there are no devices in the menu under "Playback".  Strangely, there are devices in the menu under "Recording", an OSS one and a bunch of ALSA ones.

The last time I used Audacity was back when I was running Edgy, and the sound worked fine then.  I guess this is the first time I've tried to use it since upgrading to Feisty.  But the sound on the rest of my system is fine (Amarok, XMMS, gxine/mplayer/VLC, and browser plugins).

I've removed and reinstalled Audacity a couple of times now (via apt-get) to no avail.  I've also deleted my ~/.audacity file.

I've disabled the sound server in System > Prefs > Sound, and I killed the esd process.

I'm running on a pretty new Core 2 Duo system.  Here's my kernel and sound card info:

```
Linux soma 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

Any ideas?

(I can launch Audacity as "aoss /usr/bin/audacity" and then I get an OSS playback device, but the sound skips and Audacity eventually crashes.)

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)


I was in your same exact situation, haven't used audacity for a while and now it doesn't detect my card after I upgraded Ubuntu. And I also have a core2duo

Here's how I fixed it:
1. Search for audacity in Synaptic, and check "Mark for complete removal"
2. Go to home, press ctrl+h to view hidden files, and delete .audacity
3. install audacity again. 
Start audacity, select a language, and it should work!

---

### Post by thoughts on 2007-06-21
> **Big_J said:**
> I was in your same exact situation, haven't used audacity for a while and now it doesn't detect my card after I upgraded Ubuntu. And I also have a core2duo

Here's how I fixed it:
1. Search for audacity in Synaptic, and check "Mark for complete removal"
2. Go to home, press ctrl+h to view hidden files, and delete .audacity
3. install audacity again. 
Start audacity, select a language, and it should work!

Awesome, that fixed it.  Thanks!

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by deadcabbit on 2007-06-22
does not work here :(

---

### Post by deadcabbit on 2007-06-22
Damn, had to close the video player... the windows version worked fine though...

---

### Post by gefenm11 on 2007-07-09
worked flawlessly

---

### Post by sclough on 2007-07-10
Trying to remove Audacity would remove some other stuff for me for some reason (I'm on ubuntu-studio), so I just wiped out the ~/.audacity directory which would force Audacity to re-configure itself on next launch and should accomplish the same as a re-install unless some files had been corrupted or overlaid.  It seems to have worked so far...

---

### Post by sseebart on 2007-07-21
I had the same issue, but removal didn't help. Instead, I edited the ~/.audacity file, changing

PlaybackDevice=

to:

PlaybackDevice=/dev/dsp

When I started audacity again, the device showed up and played fine.

---

### Post by rpglover64 on 2007-08-19
Same problem.  Reinstalling (and removing configuration) didn't work.  Neither did editing the .audacity file.

---

### Post by Ardrias on 2007-08-30
Installing alsa-oss and running "aoss audacity" seems to work for me, granted all I do is some simple editing.

---

### Post by luvcash75 on 2007-08-31
Slough......Your the man, thanks very much for this:)  For once I found the answer to a problem straight away thanks to you.  Nice one....:guitar:

---

### Post by OutsideEdge on 2007-09-21
Had the same issue. 

Tried reinstall and manual edit of .audacity file without success.

 Audacity worked fine after changing sound preferences in System->Preferences->Sound Devices tab to all ALSA devices.

---

### Post by 4ebees on 2007-09-29
Hi all,

Another option is to open a terminal, type:

ps aux

which will then show everything that is running.

Look through the list for anything that may be using the sound device.

Once you've found what it may be, look for the process number, which will be on the far left of the line showing you the name of the application you wish to terminate. Again, in the terminal, type:

kill

followed by a space and then the process number. This will kill the application.

I recently had a similar problem - which had not happened for a long time.

I found that I had instances of gmplayer running (from last night!).

After following this process, I was able to use audacity again.

HTH

Regards,

Patrick

---

### Post by lbyrd1984 on 2007-10-16
I did not try uninstalling, I did try editing the .audacity file and putting /dev/dsp into the Playback= line. Still did not see a playback dev. Did a sudo su and became super user and then was able to run audacity from the command line and had play back? I have seen the same problem on an upgraded fedora core system. Do I need to change the permissions on something? Any suggestions most welcome. 

Thanks

---

### Post by chemisus on 2007-10-17
i installed audacity via aptitude and was encountering the same problem: no playback device was recognized by audacity.

after reading the previous post by Big_J i tried the following:

sudo aptitude remove audacity
sudo aptitude autoclean
sudo aptitude install audacity

i tried that probably 2 or 3 times with no luck.

then i realized that i was listening to music on amarok also and that might have something to do with it. (was playing bass to music... kind of got in the mood to record... hence the installing audacity)

once i closed amarok and ran the code above, audacity recognized the playback device.

i just recently (like 4 days ago) recieved my new motherboard that has a core 2 duo (previous was p4).

just wanted to point out that having music playing could be a cause of problem.

---

### Post by 4ebees on 2007-10-18
> **chemisus said:**
>  just wanted to point out that having music playing could be a cause of problem.

My experiences is the same; Audacity appears generally unhappy if something else is using the soundcard.

---

