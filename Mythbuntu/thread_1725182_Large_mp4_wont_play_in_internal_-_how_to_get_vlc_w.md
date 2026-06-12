---
title: "Large mp4 wont play in internal - how to get vlc working"
date: 2011-04-09
forum: Mythbuntu
---

### Post by geekyhawkes on 2011-04-09
Hi, 

I have a few HD mp4 files that dont really play very well in the internal player but play absolutely fine in VLC so in my simple head i thought i would just use vlc for those files.

I went into media lib. and selected to edit the properites of the flies in question and under unique player command i added VLC.

When i select play vlc is launched but i get the following error message:

VLC is unable to open MRL
myth://Videos@127.0.0.1:6543/filename.mp4 Check the log.

I then tried VLC %s but get the same error (as i think the %s is being passed as the url anyway).

Can someone help please, low waf having to exit myth, reach for the keyboard and browse to files to watch them in vlc.

Thanks for the help.

---

### Post by nickrout on 2011-04-11
you cannot use external players with storage groups.

However if the fuke is local, you can write a script to convert the myth:// url to a full path and filename and pass that to vlc.

But I am surprised that Internal will not play it, what is the frntend log output?

---

### Post by geekyhawkes on 2011-04-16
Which frontendoutput file are you after?  I was suprised the internal player was having problems, but a few of my larger, HD files are not great under internal player but fine with VLC. 

Thanks for your help

---

### Post by ian dobson on 2011-04-16
Hi,

Maybe have a look here [http://ubuntuforums.org/showthread.php?t=1729767](http://ubuntuforums.org/showthread.php?t=1729767) I'm still trying to get everything working 100% but I'm almost there.

Regards
Ian Dobson

---

### Post by LowSky on 2011-04-16
First try changing the playback group. I'm betting that will fix the issue you are having.

---

### Post by geekyhawkes on 2011-04-16
Which playback group?  As in the same as for livetv cpu++ cpu+ VDPAU etc?  Is there a way i can just change it for these specific files?  The rest of my system works nicely in CPU++ (i get artifacts in vdpau something to do with the cache i think but havent got round to looking in detail).

Thanks

---

### Post by nickrout on 2011-04-16
> **geekyhawkes said:**
> Which frontendoutput file are you after?  I was suprised the internal player was having problems, but a few of my larger, HD files are not great under internal player but fine with VLC. 

Thanks for your help

The normal mythfrontend log.

---

### Post by ian dobson on 2011-04-17
Hi,

What I've seen, is that if you use vdpau (mplayer or internal player) some mkv's don't play very well (Motion artifacts, crystalizing etc). As vlc on ubuntu doesn't use vdpau it doesn't suffer from the problem.

mplayer and the internal player only use about 10-15% CPU and vlc uses about 50-70% (Core2Duo 2500MHz) but vlc can play everything I throw at it.

Regards
Ian Dobson

---

### Post by geekyhawkes on 2011-04-17
Thanks.  I am not using vdpau for any play back as i got artifacts on live tv so figured HD mkv etc was never going to work.  I have no idea why some work and some dont with the internal player but everything works with vlc.  I will post the frontend log shortly, shame there is not an easy way to get vlc to run for the odd files (dont really want to put scripts running to convert file names, just doesnt seem that elegant a solution).

Thanks for the help, logfile en route later.

---

### Post by geekyhawkes on 2011-04-17
So the logfile said:

AFD opened codec 0x7f026254d3c0, id(h264) type (Video)
AFD codec AAC has 6 channels
Opened codec 0x7f026254d3c0, id(AAC) tpye (audio)
opening audio device default .ch2(@) sr48000
opening ALSA audio device default


No audio came out during playback and the frame count loked pretty low to me.  With VLC it all works fine.  

I then tried to play a file that had previously worked fine and got the following;

sh internal: not found

sh internal: not found came up everytime i tried to play any video file.  I have clearly messed about with something in myth trying to get vlc working as an alterante player and broken the normal player.  can someone help please, very low WAF without being able to watch dvds etc.

Thanks

---

### Post by nickrout on 2011-04-17
> **geekyhawkes said:**
> So the logfile said:

AFD opened codec 0x7f026254d3c0, id(h264) type (Video)
AFD codec AAC has 6 channels
Opened codec 0x7f026254d3c0, id(AAC) tpye (audio)
opening audio device default .ch2(@) sr48000
opening ALSA audio device default


No audio came out during playback and the frame count loked pretty low to me.  With VLC it all works fine.  

I then tried to play a file that had previously worked fine and got the following;

sh internal: not found

sh internal: not found came up everytime i tried to play any video file.  I have clearly messed about with something in myth trying to get vlc working as an alterante player and broken the normal player.  can someone help please, very low WAF without being able to watch dvds etc.

Thanks

the internal player is spelled with an upper case I, ie Internal not internal.

---

### Post by geekyhawkes on 2011-04-20
Thanks, just need to get the large files working now.  Looking around it seems several people are having problems with the internal player and the mkv / larger files of late.  Must be something going on for all of us..

---

### Post by nickrout on 2011-04-20
Your questions are very imprecise. What do you mean "larger files" - do you mean that the length of the file presents a problem? Or the bitrate? or is it codec related (mkv is NOT a codec).

Also your log report > So the logfile said:

AFD opened codec 0x7f026254d3c0, id(h264) type (Video)
AFD codec AAC has 6 channels
Opened codec 0x7f026254d3c0, id(AAC) tpye (audio)
opening audio device default .ch2(@) sr48000
opening ALSA audio device default

is pretty incomplete.

Try ```
DISPLAY=:0 mythavtest filename.mkv
``` and post the complete output.

---

### Post by geekyhawkes on 2011-04-21
Will do, i will post the output tomorrow.  Thanks for the help

---

