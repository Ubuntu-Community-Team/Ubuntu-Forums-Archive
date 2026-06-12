---
title: "mythtv mplayer won't play videos"
date: 2009-10-22
forum: Mythbuntu
---

### Post by GoMad on 2009-10-22
Please help ! I am new to mythtv, I have created a trial setup in VMPlayer and now am setting it up on real boxes. I am creating a backend first with local front end but all is configured to use 192.168.1.98 instead of local host. sql is configured to listen on this IP. I intend to have remote frontends once this is working.
 
I had issues with 9.0.4 due to the intel video driver bugs, upgrading to 9.10 fixed this and then reinstalling gnome-console resolved the repeat login screen issue.
 
So, now the problem is playing avi's. I have copied the mythtv **mplayer** command line to a command prompt replacing %s with an avi - it all plays just fine.
 
Selecting the avi via mythtv and clicking play results in nothing happening. The log shows there is no stream from **myth://videos@192.168.1.98:mymovie.avi**
 
Now, I have read that 0.23 of mythtv will stream all media to frontends (awesome - I was wondering why it couldn't) and this behaviour is triggered if you create groups. I have ensured there are no groups, which should force mythtv 0.22 to default to the previous method - looking in /var/lib/mythtv/videos ! So, the problem looks to be mythtv interpretting the %s and converting it in to a stream string fed to **mplayer**, rather than a local directory / file.
 
Does %s auto convert to streamed format 0.23 will use, or should it pass in the avi 'as is' ? ie is there a different perameter type instead of %s ?
 
Please help and I am dumbfounded :confused: and this is clearly something internal to mythtv (as it works from command line), and I think this could well be a bug. I have not tried changing the default player to xine etc as really mplayer should do just fine (which, from a command line. it does).
 
Thanks,
 
Jason

---

### Post by dsauter on 2009-10-22
Same problem here with iso's, and I'm sure you are right about it being involved with the changes associated with storage groups.

From the  MythVideo .22 Transition Guide, [http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide]("http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide") one of the disadvantages to the current changes are:

>  * External Video Players (mplayer, xine, VLC) will not work with videos hosted on an SG. (Fix planned for .23) 

I *think* that I've disable storage groups, but my symptoms are all the same as yours, I can play it fine from a command line, but it inserts the "myth://videos@192.168.1.98:" (or something similar) which prevents the file from playing in the external player.

My only workaround so far is to use the internal player.

If you happen into a better solution, could you post your solution?  I'm sure others are scratching their head too.

---

### Post by GoMad on 2009-10-22
I most certainly will, in the mean time how have you got the internal player to work ?  I tried that and it did not fix the issue.  What command line did you type, or was it just "internal" ?
 
Many Thanks.

---

### Post by GoMad on 2009-10-22
Mind you I'd be happy for the streaming mechanism to work instead, however it does not seem to know what myth://IP:video.avi is !?  Any ideas on that also welcome as happy for either solution to work !

---

### Post by jwbrown77 on 2009-10-22
What I did was change the storage group for Videos in the backend setup dialog to a different directory like /var/lib/mythtv/videosg/

Then I went into the MythVideo setup in the frontend and set the videos directory to /var/lib/mythtv/videos

That allowed me to use the external player (mplayer).

Second post is right: the storage groups are incompatible with external video players.  Using the internal player did work for me in 9.10 Beta for a few videos I tried, but there were some things I couldn't figure out (like VDPAU decoding, mkv subtitles, etc) so I just stuck with mplayer.

---

### Post by GoMad on 2009-10-22
Well, that did not work either. I no longer get the myth://videos@ error but I don't see any movie either, just keep pressing play to no effect.
 
Going to try and reinstall mythvideo.
 
Thanks.

---

### Post by GoMad on 2009-10-22
actually I do still get the myth:// stream error, this is just ridiculous !  I know it's beta, but this is basic functionality !

---

### Post by jwbrown77 on 2009-10-22
If you changed the storage group directory for Videos in the *backend* setup (have to close mythfrontend and launch the backend setup from the taskbar), it should work.

Please post details on the Storage Group setup as well as the MythVideo directory setup in mythfrontend as well as a full log excerpt when playback doesn't work from mythfrontend.log.

---

### Post by GoMad on 2009-10-22
wowzers. Uninstalled mythtv-frontend (which removes related packages) and then reinstalled mythtv-frontend, mythvideo and mythmusic.
 
It now works, so something on the distro I downloaded (upgrade fromn 9.0.4 to 9.10 RC1) was dodgy, as was the gnome gui which I also had to re-install after the upgrade.
 
Conclusion: upgrade is very dodgy, until these issues are resolved do a fresh installation from scratch of 9.10.

---

### Post by GoMad on 2009-10-22
jwbrown - thanks, I changed all backend dir's to be dirname-stream so they are very different, still got same issues. A reinstall has resolved most of it, movie comes up now just doesn't play unless I hold down the arrow key :-).  Another issue of which i am sure there are plenty of other threads :-)  Thanks again.

---

### Post by jwbrown77 on 2009-10-22
> **GoMad said:**
> jwbrown - thanks, I changed all backend dir's to be dirname-stream so they are very different, still got same issues.

Just curious: Are you storing your video files anywhere in the directory that's defined as the Storage Group in the backend?

e.g. if the backend setup for the Videos storage group is /var/lib/mythtv/videos, is that where you're dropping your files, or are you putting them in a completely different path?

The arrow key thing is really weird.  MythVideo/mplayer/VDPAU work flawlessly for me.  VDPAU is the best thing since sliced bread.

---

### Post by GoMad on 2009-10-23
OK, so here is what I have;
 
Backend - set up as groups in the backend (currently all empty).
/var/lib/mythtv/videos-stream
/var/lib/mythtv/banners-stream
/var/lib/mythtv/posters-stream
/var/lib/mythtv/coverart-stream
 
etc...
 
Front end (I have aci's in videos and dvd covers in posters).
/var/lib/mythtv/videos
/var/lib/mythtv/banners
/var/lib/mythtv/posters
/var/lib/mythtv/coverart
 
etc.
 
The VDPAU thing -0 I have just seen posts on that, will look in to it, any pointers most appreciated. with mplayer any key ont he keyboard will cause it to play 1-2s of the movie and then it pauses again :-( Can't believe all this hassle really as the PC, all be it 6 years old, is all branded stuff (sis / msi / intel graphics) so I am a bit surprised at these issues. i also do not understand why the streaming aspect for videos doesn't work, it does not understand what myth://IP@videos:movie.avi is or how to interpret it. I tried to down load a fresh 9.10 ios last night (to do a complete fresh install rather than upgrade) and it *seems* they have retracted the beta release. I guess because the official release is supposed to be on the 29th Oct.
 
Any pointers on the VDPAU thing most appreciated (my wife would like me back !!).
 
Best Regards.

---

### Post by GoMad on 2009-10-23
jwbrown - The arrow key thing is really weird
 
Just a thought, it is almost like the playback is on permanent pause and hitting keys causes it to jump / skip forwards or backwards.
 
I don't have a remote right now, just using the keyboard to get things going before I purchase a frontend (prob the msi media live unit).
 
When it first starts to play it starts off paused, I iwll look at the key mappings and see if P causes it to play continuously.
 
It is weirt though.  Failing that I will get the 9.10 RC1 full download and do a complete fresh re-install.

---

### Post by dsauter on 2009-10-23
> **GoMad said:**
> how have you got the internal player to work ?  I tried that and it did not fix the issue.  What command line did you type, or was it just "internal" ?
 
Many Thanks.

Close, but it's Internal with a Capital "I".  ("Internal" not "internal").  That's what worked for me.  I've seen many postings saying it is case sensitive.

I'm glad you've gotten so many responses to the external player.  I'm going to have to get to playing again and try out some of these ideas.

---

### Post by GoMad on 2009-10-23
Yes, I realised that when I did it and changed to a Capital I but that did not work either. I also tried to specify it in the command for file extensions with no joy.
 
Just burning RC1 iso from scratch and will try a fresh install !
 
I did use a custom partition setup but that should not affect things.  Had a few issues with Reiser FS mind so will go for ext4 all round.

---

### Post by jwbrown77 on 2009-10-23
> **GoMad said:**
> i also do not understand why the streaming aspect for videos doesn't work, it does not understand what myth://IP@videos:movie.avi is or how to interpret it.

As described in the MythTV wiki, video streaming does not currently work with any external player, such as mplayer or xine.  It only works with the internal (ffmpeg driven IIRC) player.  Why the internal player doesn't work for you I have no idea.  It worked good for me but since I had some other requirements I decided to stick with mplayer.

My 9.10 Beta install came with pretty much video extension pre-configured, all going to the internal player.  The internal player worked right off the bat.  All I did was change the extensions I wanted to play with mplayer to "use default player," which I defined as mplayer.

Regarding VDPAU: You mentioned your machine is fairly old.  It requires an NVIDIA 8400GS or newer.  My 8400GS is able to decode 1080p Matroska/x264 rips with no stuttering while mplayer takes 1-2% CPU usage.  Without it, mplayer took 100% CPU and struggled with high bitrate scenes.

---

### Post by GoMad on 2009-10-23
yes, read the notes in detail and have these issues, internal player did not work. just finished a fresh install wiping all old volumes and it already looks better.
 
Don't recommend doing an upgrade from 9.04 from what I have seen so far :-)  Blitz and resinstall.

---

### Post by lgiordano on 2009-11-17
> **GoMad said:**
> A reinstall has resolved most of it, movie comes up now just doesn't play unless I hold down the arrow key :-).  Another issue of which i am sure there are plenty of other threads :-)  Thanks again.

I was having this same issue where movies wouldn't play and appeared to be paused unless I held down the arrow key. I was able to fix it by adding ontop="1" to my mplayer config file (/home/user/.mplayer/config). Alternatively, you could have Mythtv call mplayer with -ontop specified.

---

### Post by NTolerance on 2009-11-28
> **lgiordano said:**
> I was having this same issue where movies wouldn't play and appeared to be paused unless I held down the arrow key. I was able to fix it by adding ontop="1" to my mplayer config file (/home/user/.mplayer/config). Alternatively, you could have Mythtv call mplayer with -ontop specified.

I wish this worked for me but it gives the same result.  Still can't use mplayer with Mythbuntu 9.10.

---

### Post by littlejon on 2010-01-16
I think I may have found a solution to this problem. It is an audio driver issue. I noticed I was having problems with pulse so I added "-ao alsa" to the mplayer setting in mythtv and it works.

More details can be found here:
[http://www.thelazysysadmin.net/2010/01/mythtv-mplayer-playback-issue-with-ubuntu-karmic-koala/](http://www.thelazysysadmin.net/2010/01/mythtv-mplayer-playback-issue-with-ubuntu-karmic-koala/)

Hope that helps.

---

### Post by joachimp on 2010-05-29
I was able to fix this by changing the audio preferences in mythfrontend Utilities/Setup > Setup > General  
to: 
Audio output device: pulseaudio:default
[also, but not sure if necessary] uncheck internal audio controls  
*nothing else worked for me* I tried everything else suggested on this thread, and many others.. This system was originally 8.10, 9.04, 9.10, 10.04, I think myth stopped working somewhere around 9.04....

---

### Post by maniaq on 2010-10-01
I can confirm I too was suffering from this problem and changing my external player command from:

mplayer -ao pulse ...

to:

mplayer -ao alsa ...

totally fixed it!

Shame, because I actually get better performance using Pulse from the command line, on large (720p) files, but if it (MythTV) wont' work with Pulse, I'll just have to wait until they get it right

---

