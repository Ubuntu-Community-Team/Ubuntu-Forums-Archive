---
title: "Songs just won't START playing!"
date: 2008-06-16
forum: Multimedia Software
---

### Post by oomar on 2008-06-16
I'll boot up my computer and say, "HEY! lets listen to some music!" Ill start up my Rythmbox or Listen Player and ill hit play. Nothing happens... sound works fine with everything but the song stays at 0:00. nothing happens..... ill fast forward to a part into the song and it still just sits there doing nothing. This happens with ALL of my music players.. sometimes ill even be on youtube and the video will play but there is no sound! WHATS WRONG??!?!?!?!?

help me....

---

### Post by cozmicharlie on 2008-06-16
Lets start from the beginning.  Did you install all the necessary codecs?  See this post [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683).

If so, provide more info.  What types of files are these (mp3, flac, ??).  What are you using (Hardy, gutsy, ???).

---

### Post by oomar on 2008-06-16
sometimes they all work fine! its weird... so its just that seemingly at random they dont work.

---

### Post by oomar on 2008-06-16
many are mp3 but also many are m4a's from itunes... i just backed up a lot of them off my ipod...

---

### Post by jjmatt on 2008-06-16
I'm having the same problem. I'm using hardy, it happens with all audio types, with all players. Actually, this causes Amarok to crash about 70% of the time. I installed all the necessary codecs. I'm running 2.6.24-19-generic but I was running -18 earlier with the same issue.

Also, I think its worth mentioning (since I think it might be worth mentioning) I think there's some correlation to different audio players/video players playing. For example, if I open up Amarok first, it will play (for a little while before crashing), but then if I open up mplayer, it'll play video REALLY slow. So I close mplayer, and open up vlc, the same video will run normal speed, but then it will freeze when the first video is up. But if I open up mplayer or vlc first (upon reboot) the opposite will happen. I haven't tried any other players really, but its annoying enough as is.

any thoughts?

---

### Post by oomar on 2008-06-16
yea occasionaly ill boot up and it will play but usually it just doesnt...

---

### Post by cozmicharlie on 2008-06-16
> **oomar said:**
> many are mp3 but also many are m4a's from itunes... i just backed up a lot of them off my ipod...

So does this happen with all the files or just the m4a?  
So you boot and the files play fine then the next time you boot up and try and play the same files in the same player they don't play?  Is that correct?  
Are you sure it is not a problem with the files? I ask because music you buy on itunes does not transfer (it has copyright protection).  When you buy from itunes you buy a license and that license allows you to play on that device (your ipod for instance).  The license is not for playing on multiple devices.  
Does the same thing happen with music that you did not buy from itunes?  
FYI - m4a are a bit tricky - m4a is actually a container (it is an mpeg4 without the video).  It usually contains a file in aac format (if it is from itunes) so you need the faac encoder to play (available in Synaptic).

---

### Post by Daedal Dementia on 2008-06-16
m4a's ey?

i suggest getting soundconverter (sorry dont know code)

and searching "m4a" in your music folder and just converting them all to something else (i picked mp3)

---

### Post by oomar on 2008-06-17
the problem may be with the file but yes you are correct ill boot up and they will be working and ill boot again and they wont or even ill pause it and they wont start again! Im pretty sure they right codec is installed to play tem cause i didnt use to have this problem and they still occasionaly play.and i DO have music i bought from itunes and i do have problems with that but im not stupid.... some are locked and im too lazy to unlock them. this is completely different from Apples stupid proprietory laws... most of my songs are backed up from the ipod but are in an unlocked format

---

### Post by paulnn on 2008-06-17
I'd just like to add that I've been having this problem too intermittently for the past 8 weeks, it is solved by a reboot but keeps recurring sporadically. I am sure I have all the necessary codecs installed, and it's not a sound problem as flash sound works fine. Below is console output from mplayer. VLC just crashes with no output.

(same problem in this thread: [http://ubuntuforums.org/showthread.php?t=825439](http://ubuntuforums.org/showthread.php?t=825439))
and this thread: [http://ubuntuforums.org/showthread.php?t=823629](http://ubuntuforums.org/showthread.php?t=823629)

edit: In the second thread someone suggested to go to sys->pref->sound and change "Music and Movies" from "autodetect" to "alsa". This fixed the problem for me, for now.

> Playing 01. Astral Weeks.mp3.
Audio file file format detected.
Clip info:
 Title: Astral Weeks
 Artist: Van Morrison
 Album: Astral Weeks
 Year: 1968
 Comment: &#65533;berStandard - UberNet.org
 Track: 1
 Genre: Rock
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.4 (00.3) of 664.0 (11:04.0) ??,?% 


---

### Post by Mattevt on 2008-06-17
I had this problem when I started a youtube video while rhythmbox was playing.

This worked for me, it may or maynot work for you...just a suggestion.

open terminal and type

'killall pulseaudio' 

this reverts to ALSA. 

However, when you restart, pulseaudio will take over again. I just remember to kill pulse when I log on and things have been fine. Now, even if I accidently play a youtube video while rhythmbox is playing, sound isn't affected. It's worth a shot.

(I'd eventually like a permanent solution to this as well, aside from killing pulse everytime)

---

### Post by Stefanie on 2008-06-17
Same problem here.
edit: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) this page contains information on how to use alsa instead of pulseaudio - it's as simple as going to system -> preferences -> sound and select ALSA for all options (in hardy, at least). i just changed my settings, i'll let you know if this works.

---

### Post by cozmicharlie on 2008-06-17
> **oomar said:**
> the  but im not stupid.

oomar - please don't take this the wrong way when I ask questions.  When I help people on the forums I have no way of knowing how much knowledge you have so in order to help I have to ask a lot of questions.  They are not meant to imply you are stupid, they are intended to gather info so I can figure out what is going on and help.  You would be surprised how many people buy music from itunes not knowing what they are getting then blaming Ubuntu because they can't play the music. SOunds to me though that you know what you are doing and that is not the problem so lets try something else. 

What's baffling me is that they play at times and not other times.  I would say if they play you probably do have the codecs installed and that is not the problem.  You might try to uninstall all the codecs and the players make sure you delete the config files in the home folder - for example in /home/yourname/.mplayer/config (make sure and click "show hidden files" in the menu).  Then reinstall them systematically using this post: 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Lets see if that does it.  If not and no one else has any suggestions you may need to reinstall the OS.  Lets try this first though.

Also, are you using Hardy?  Are you confident your sound card etc are set up OK?  I ask because their are a number of posts with people having problems with the new Pulse Audio in Hardy.  As others have suggested the problem may be in your sound and not that you don't have the proper codecs.

---

### Post by oomar on 2008-06-17
haha im not going to take any offense. I do have a decent amount of experiance in Linux but with any system, sometimes you just don't know whats going on. I AM using hardy and as it turns out, paulnn's solution worked for me and i would suggest using that and see if it works. So my problem is solved! yay! 

Thanks guys, this is why I activly promote Ubuntu, even if the people on here have no idea what they're talking about (almost never true) there are just sooo many people willing to help that things will get fixed EVENTUALLY. lol 

For those about to rock, I salute you!

(AC/DC rocks!!!) lol thanks guys!

---

### Post by oomar on 2008-06-17
haha im not going to take any offense. I do have a decent amount of experiance in Linux but with any system, sometimes you just don't know whats going on. I AM using hardy and as it turns out, paulnn's solution worked for me and i would suggest using that and see if it works. So my problem is solved! yay! 

Thanks guys, this is why I activly promote Ubuntu, even if the people on here have no idea what they're talking about (almost never true) there are just sooo many people willing to help that things will get fixed EVENTUALLY. lol 

For those about to rock, I salute you!

(AC/DC rocks!!!) lol thanks guys!

EDIT: oh and by the way Mattevt you can make a script for that and set it to run on startup. just a thought.

---

### Post by markbuntu on 2008-06-17
This problem is caused by pulseaudio. I fixed it by stopping pulseaudio from loading at boot with Boot Up Manager (bum) and changing all the defaults to alsa. If you want to try to fix your pulseaudio setup you can go here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

or here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If you want to go back to a pure alsa setup you can do this which I wrote after having a few complete failures with the pulseaudio guides. Do not get me wrong, they have helped a lot of people. But of they don't work for you, you can try this:

Emergency Sound Repair Guide


1. Stop pulseaudio from loading at boot with Boot Up Manager (bum). 

2. Put etc/asoundrc in the trash.

3. Edit etc/libao.conf: default_driver=alsa

4. Make sure alsa-utils runs at boot (System/Admin../Services)

5. Check with Synaptic that these are all installed:

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

6. System/Preferences/Default Sound Card, choose the sound card. 

7. Sys../Pref.../Mutimedia Systems Selector/Audio, set plugin  to alsa and Device to Default for both input and output.

8. Sys../Pref.../Sound, set all to ALSA. Default mixer tracks to "your sound card" (i.e. ATI IXP) (Alsa )mixer).

9. Reboot. If you are having trouble changing settings in Multimedia Systems Selector or Sound, reboot and then make the changes.

10. alsamixer, alsamixergui, gnome-alsamixer,  configure. Turn stuff on and put up the sliders. check mix, capture, cd, mic, etc, unmute, mute, blah blah blah... If you have a usb mic or headphones turn them on and test them in the gnome-alsa mixer USB section.

11. Test with Rythmbox, vlc, totem, xine, gstreamer, etc. configure all preferences to alsa if available/possible.

12. Test Sound Recorder. set capture/mix level, enable record, turn on mic, unmute, mute etc, etc... fool with mixer until it works right

13.  jackd, set driver to alsa in jack control.

---

### Post by jjmatt on 2008-06-19
So the solutions generally seem to be, stop using pulseaudio... While that works and that's cool and all, does anyone know of a way to get everything to work WITH pulseaudio? 

Thanks

---

### Post by cozmicharlie on 2008-06-19
> **jjmatt said:**
> So the solutions generally seem to be, stop using pulseaudio... While that works and that's cool and all, does anyone know of a way to get everything to work WITH pulseaudio? 

Thanks

Something in this post might help [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by macpointman on 2008-12-17
> **Stefanie said:**
> Same problem here.
edit: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio) this page contains information on how to use alsa instead of pulseaudio - it's as simple as going to system -> preferences -> sound and select ALSA for all options (in hardy, at least). i just changed my settings, i'll let you know if this works.
Worked like a charm.  Will have to keep an Eye on it.  Thanks for your post.

MacPointMan

---

### Post by FAJALOU on 2009-01-13
> **paulnn said:**
> 
edit: In the second thread someone suggested to go to sys->pref->sound and change "Music and Movies" from "autodetect" to "alsa". This fixed the problem for me, for now.


Paul:  Thank you, this worked for me :)

It's weird because one day it *just stopped workin!*  It was really really weird!

---

### Post by FAJALOU on 2009-01-13
Has anyone put in a bug for this?  Because it was really weird! Just stopped working!

---

