---
title: "DeVeDe Sound Problems in Finished DVD's"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by Jesterday on 2007-01-16
Hey Guys and Girls,

I have been creating DVD's with DeVeDe for a while now, I have used many file types from xvid, divx, etc... and it has always worked to make basic DVD's with no menus. But recently, I believe after I upgraded to Edgy, when I create the iso with DeVeDe everything seems to work fine, but when it is burnt to the DVD the video is perfect but the sound is all messed up, and completely incomprehensible. 

I know DeVeDe uses Mplayer, Mencoder for conversions, but I can't understand why it can't convert my AVI's without an issue anymore. Has anyone else run into this problem or similar problem with DeVeDe or Mplayer or Mencoder?

Thanks in advance for the help!

Darren

---

### Post by casfindad on 2007-02-21
I have the same problem. After I burn the iso, the playback is choppy on my computer. If I play the DVD on my standalone player, the video is fine but there is no audio. :-( The mpeg file made by DeVeDe is ok, however.

Follow-up: Interestingly, the choppy DVD playback (on a DVD produced by DeVeDe and burned with K3b) on my computer is limited to Kaffeine. If I play the same DVD with Noatun or VLC, both audio and video are fine.

---

### Post by wxnker on 2007-02-22
I just installed DeVeDe in Feisty a couple of hours ago and I get the same problem. Weird because I have never had any issues with DeVeDe before but now the audio is VERY distorted.

I'm trying to solve this right now. I'll get back here if I get it to work
[COLOR="Red"]
EDIT: Well, my problem with DeVeDe sound is only in "Feisty". If I log into "Edgy" everything is fine. I'm not sure why, but since Feisty is not the final version I'm just going to use DeVeDe with Edgy until this is solved.[/COLOR]

---

### Post by wxnker on 2007-02-24
The problem might be Mplayer. It was in my case. Since I don't use Mplayer I never did the settings. 
After choosing the proper codec family in Mplayer, sound in DeVeDe works great.

See this thread:
[http://www.ubuntuforums.org/showthread.php?t=369585](http://www.ubuntuforums.org/showthread.php?t=369585)

---

### Post by disturbedite on 2007-02-24
could you guys be a little more descriptive?  are you using lpcm, mp2, or ac3 audio?

---

### Post by wxnker on 2007-02-25
Since I had the same distorted sound in Mplayer I thought the solution was to do the settings in Mplayer. Now Mplayer plays MP3's with no problems so I thought DeVeDe would work to. I was wrong, DeVeDe is still just creating noise when converting _AVi files (divx/xvid with MP3 vbr sound)_ to DVD.

I have set Mplayer to use:

Video: FFmpeg's libavcodec codec family (driver gl2)
Audio: FFmpeg/libavcodec audio decoders (driver alsa)

My settings are the same as in Edgy but when running DeVeDe in Feisty the sound, when converted to DVD (or when previewing), is terrible = 95% noise.

---

### Post by Yeuclid on 2007-04-01
I have had exactly the same problem. When I first installed it on 7.04 Devede worked fine, created DVD structure files perfectly, and sound was OK.

Then, after I took some 7.04 upgrades this past week, it stopped working, converted video had thin blue lines across it, and sound was just like very loud static.

I guess some bad codecs have been downloaded as part of the upgrade, so I'll just wait until maybe another cycle perhaps cures it.

I can't be bothered to go back to 6.10 now so I'll hope that the 7.04 team restores Devede to a usable state.

---

### Post by regomodo on 2007-04-24
Is this sorted?

I've just tried it and all i get with my sound is loud static, like someone previously said. I upgraded to Feisty last week.

I've used ffmpeg+transcode combo before in Edgy with much better results, although not as good as it can be.

---

### Post by ljpp on 2007-04-24
It seems that DeVeDe and Mplayer/encoder should be updated to Feisty repos rather urgently. Newer versions contain important fixes.

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

> When the original video has 24 fps and the destination is a NTSC DVD, DeVeDe will use 24000/1001 fps instead of 30000/1001.
...
Note for Ubuntu Feisty users: currently (as April 20, 2007), the Mplayer/Mencoder version in Ubuntu Feisty is buggy and produces noisy sound when used with DeVeDe. While the maintainer doesn't fix it, you can use the .deb package created by from the CVS sources (it's available in the Download section)


---

### Post by erissiva on 2007-04-27
My only problem is that now I cannot use k9copy or Devede. After installing the mplayer-cvs package from that site, it removes mencoder, mplayer, devede, and k9copy. After installing it, I try to install Devede and k9copy, but they want to uninstall the mplayer-cvs package and go back to the broken ones! :( 

What do I do?

---

### Post by plainjane on 2007-04-28
"My only problem is that now I cannot use k9copy or Devede. After installing the mplayer-cvs package from that site, it removes mencoder, mplayer, devede, and k9copy. After installing it, I try to install Devede and k9copy, but they want to uninstall the mplayer-cvs package and go back to the broken ones!"

Exact same thing happens to me!  I would love to know how to fix please.:)

---

### Post by kelvin spratt on 2007-04-28
I had the same problem down loaded latest version from [http://www.getdeb.net/](http://www.getdeb.net/) all is well now hope this helps

---

### Post by erissiva on 2007-04-28
kelvin - Actually, I've tried the same thing. The .deb from that site tries to remove the CVS file and install the old broken one. Is there any possible way to fix this?

---

### Post by plainjane on 2007-04-28
So, being totally new to linux, when a program breaks like this will a fix be released?  How does that work?  Do we keep checking with the DeVeDe website?  Sorry to ask such stupid questions, just really want this program to work, especially after reading that ToVid takes hours and hours to work. 
                    Thanks!

---

### Post by russell.h on 2007-04-30
At some point a fix may be released into the repositories, at which point the next time you do an update you will get the newer version.

The way updates are worked in Ubuntu (as I understand it) within a given version of Ubuntu (Feisty, Edgy, Dapper, etc) an update to software will not contain new features, they only do security and bug fixes, etc.

If a few people report this on launchpad then it will probably be fixed.

---

### Post by erissiva on 2007-04-30
As far as I can tell, this is the Launchpad bug that this is associated with:

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751)

---

### Post by Yeuclid on 2007-05-02
I've been following this problem now for a while and there are a few duplicates of it in Launchpad, as it seems to have been isolated to a fault in the 7.04 version of Mencoder.

Some people have worked around it by replacing the 7.04 version by the one from 6.10.

I don't know enough about Ubuntu to be able to do that just yet, and would be concerned about affecting other dependencies.

Can anyone tell me how to do that easily and safely?

---

### Post by ERam123 on 2007-05-07
The problem lays with mencoder's mp3 decoding (also related to mplayer).

As a workaround, in DeVeDe when you add a file, select "Advanced options" then "Misc" and in the "Extra parameters for Mencoder" box, enter "-afm ffmpeg".

You can double check to make sure this workaround works by previewing 10 seconds or so of the movie.

---

### Post by julie_lebou on 2007-05-08
I did that -afm ffmpeg... not working, and even tovid is not working for me. so i have like 10 movies to burn... grrr

---

### Post by TOOOL on 2007-05-08
also tryed adding -afm ffmpeg to devede and it didn't work, blue lines on screen and bad sound, new to linux and can see lots of potential but frustrating when you can't do what you want
is there alist of top apps to use with ubuntu

---

### Post by chalimac on 2007-05-16
I've found a workaround to fix audio problems:

1. Download .deb from the bottom of this page: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

2. Extract the files mplayer and mencoder from the package (don't install it, just extract it).

3 backup the files mplayer and mencoder from you /usr/bin directory.

4. Copy the files you extracted from the package (mplayer and mencoder) to /usr/bin

---

### Post by TOOOL on 2007-05-17
how do you make it write accesss to the usr/bin folder?

---

### Post by PilotJLR on 2007-05-18
> **chalimac said:**
> I've found a workaround to fix audio problems:

1. Download .deb from the bottom of this page: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

2. Extract the files mplayer and mencoder from the package (don't install it, just extract it).

3 backup the files mplayer and mencoder from you /usr/bin directory.

4. Copy the files you extracted from the package (mplayer and mencoder) to /usr/bin

THanks! This worked perfectly!

---

### Post by TOOOL on 2007-05-18
this worked but just had to work out how to shift files into usr/bin folder, still not sure how to do it, ended up booting up cough cough win xp, which has a ext2 reader writer program running and shifting the files, is there some way of getting round the access issues in ubuntu so you can shift files easily

note also had to pick the deinterlace ffmpg option in advanced settings to get rid of blue lines

---

### Post by PilotJLR on 2007-05-18
> **TOOOL said:**
> this worked but just had to work out how to shift files into usr/bin folder, still not sure how to do it, ended up booting up cough cough win xp, which has a ext2 reader writer program running and shifting the files, is there some way of getting round the access issues in ubuntu so you can shift files easily


Yikes! That's the Rube Goldberg way. Add "sudo" in front of the move command. So:
```

sudo mv thenewfilename /usr/bin/

```

---

### Post by TOOOL on 2007-05-19
is there a way of graphically moving files to this folder as i don't know all the commands

---

### Post by tommcd on 2007-05-19
Hit ALT+F2 and type in the box that comes up "gksudo nautilus". This will open up a nautilus window as root where you can do things through the GUI.
I've been following this thread with interest. Hope the fix works.

---

### Post by TOOOL on 2007-05-19
thanks thats a good command to know, slowly getting a few commands that are solving some issues i have, be good if there was a list of all the main ones for doing the common things
cheers

---

### Post by tommcd on 2007-05-20
> **TOOOL said:**
> thanks thats a good command to know, slowly getting a few commands that are solving some issues i have, be good if there was a list of all the main ones for doing the common things
cheers

Here is one:
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
and another:
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
If you really want to learn linux you should try to learn basic command line stuff. It helps a lot if you ever want to try other distros.

---

### Post by wrongo on 2007-05-23
> **ERam123 said:**
> The problem lays with mencoder's mp3 decoding (also related to mplayer).

As a workaround, in DeVeDe when you add a file, select "Advanced options" then "Misc" and in the "Extra parameters for Mencoder" box, enter "-afm ffmpeg".

You can double check to make sure this workaround works by previewing 10 seconds or so of the movie.

No, no. When I did a 10-second preview, **using the "-afm ffmpeg" fix (see QUOTE above)**, the audio was OK.

I'd bet $5 it works now. (I'll be back if it didn't...)

Meanwhile, thanks for the (apparent) fix!

---

### Post by hyfalcon on 2007-05-25
> **ERam123 said:**
> The problem lays with mencoder's mp3 decoding (also related to mplayer).

As a workaround, in DeVeDe when you add a file, select "Advanced options" then "Misc" and in the "Extra parameters for Mencoder" box, enter "-afm ffmpeg".

You can double check to make sure this workaround works by previewing 10 seconds or so of the movie.


This seems to have worded for me also.  I'm encoding an .avi file at this moment to test it.  At least I was able to watch the preview without jumping out of my chair from the audio playback.:popcorn:

---

### Post by hob4bit on 2007-05-26
Hi Folks,

Hello, this bug has effected me as well. There is a very simple workaround
and that is to get the "Mencoder-0.99" from Ubutntu 6.10:

wget [http://uk.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_0.99+1.0pre8-0ubuntu8_i386.deb](http://uk.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_0.99+1.0pre8-0ubuntu8_i386.deb)
dpkg -i mencoder_0.99+1.0pre8-0ubuntu8_i386.deb

There are no dependencies issues for me. Don't downgrade mplayer.

This is the fourth serious Ubuntu-7.04 bug that has effected me.

1) Low screen refresh rate 
2) Gnome screen saver activating during games like ET (Use "xset s 60")
3) PTP camera problem (downgrade to libgphoto and gthumb)
4) Mencoder produces corrupt sound (downgrade Mencoder)

I posted workaround for three. It looks increasingly like Ybutntu-7.04 
wasn't tested properly. Its more cutting edge than 6.10 where every
thing works for me.

I hope Ubuntu 7.10 is a good stable version otherwise I may be
forced to switch distros.

At present I will live with these workarounds.:(

---

### Post by plainjane on 2007-05-26
> **ERam123 said:**
> The problem lays with mencoder's mp3 decoding (also related to mplayer).

As a workaround, in DeVeDe when you add a file, select "Advanced options" then "Misc" and in the "Extra parameters for Mencoder" box, enter "-afm ffmpeg".

You can double check to make sure this workaround works by previewing 10 seconds or so of the movie.

This worked for the sound for me, but I have lines running across the screen now through the movie.  Any ideas on that?  Good thing I have Todisc!  It just takes a lllooonnnnggg time to run!

---

### Post by erissiva on 2007-06-02
> **plainjane said:**
> This worked for the sound for me, but** I have lines running across the screen now through the movie**.  Any ideas on that?  Good thing I have Todisc!  It just takes a lllooonnnnggg time to run!

I have this same problem. Please tell me there's a fix.
This is really making me regret upgrading to 7.04. All I do is surf the net and make DVDs. The fact that I can't now is regretful. :(

---

### Post by Jason Weiss on 2007-06-03
> **hob4bit said:**
> Hi Folks,

Hello, this bug has effected me as well. There is a very simple workaround
and that is to get the "Mencoder-0.99" from Ubutntu 6.10:

wget [http://uk.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_0.99+1.0pre8-0ubuntu8_i386.deb](http://uk.archive.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mencoder_0.99+1.0pre8-0ubuntu8_i386.deb)
dpkg -i mencoder_0.99+1.0pre8-0ubuntu8_i386.deb

There are no dependencies issues for me. Don't downgrade mplayer.

This is the fourth serious Ubuntu-7.04 bug that has effected me.

1) Low screen refresh rate 
2) Gnome screen saver activating during games like ET (Use "xset s 60")
3) PTP camera problem (downgrade to libgphoto and gthumb)
4) Mencoder produces corrupt sound (downgrade Mencoder)

I posted workaround for three. It looks increasingly like Ybutntu-7.04 
wasn't tested properly. Its more cutting edge than 6.10 where every
thing works for me.

I hope Ubuntu 7.10 is a good stable version otherwise I may be
forced to switch distros.

At present I will live with these workarounds.:(

I know i am very upset about the beta testing as well

I have a good mind to ask for my money back

---

### Post by fdrake on 2007-06-09
i followed the solution suggested before but it didn't work because of a permission and execution problem, so this is how i made it to work correctly:

as they said:

-click the link to download the archive [http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2](http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2) on your home folder
- extract the content 
-now on the terminal type :
sudo chmod 777 ~/mplayer_fixed/m* 
sudo cp ~/mplayer_fixed/m* /usr/bin/

that's it !! enjoy

---

### Post by ernstblaauw on 2007-06-20
I have Feisty 64-bit. How should I correct the audio problems? The 32-bit mplayer and mencoder from DeVeDe don't work in my system....

---

### Post by marklid on 2007-06-23
> **fdrake said:**
> i followed the solution suggested before but it didn't work because of a permission and execution problem, so this is how i made it to work correctly:

as they said:

-click the link to download the archive [http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2](http://www.rastersoft.com/descargas/mplayer_fixed.tar.bz2) on your home folder
- extract the content 
-now on the terminal type :
sudo chmod 777 ~/mplayer_fixed/m* 
sudo cp ~/mplayer_fixed/m* /usr/bin/

that's it !! enjoy

I downloaded the archive form the above link, extracted it and ran install.sh (as root) and job done - Devede back working a treat ! 
Thanks for the help.

---

### Post by ernstblaauw on 2007-06-23
The author has made available a 64-bit version of mencoder and mplayer - now my problems are fixed!

---

### Post by erissiva on 2007-06-25
Even with the new install.sh and new files, I am **still** having the problem of thick lines running through my encoded videos. I cannot seem to find anywhere that can help.

Is there anyone who might even have a hint at what I can do? Or at least where I can find help?

---

### Post by maxjivi05 on 2007-07-23
I've been having the same problem still... After downgrading, and trying those workarounds, then updating and trying them again... Both ways it will not produce sound through a entire movie.... It worked before all this crap but now its just being retarded.... and acting up... Any one have a better fix?

---

### Post by Hawk__0 on 2007-07-26
> 
Hi Folks,

Hello, this bug has effected me as well. There is a very simple workaround
and that is to get the "Mencoder-0.99" from Ubutntu 6.10:

wget [http://uk.archive.ubuntu.com/ubuntu/...untu8_i386.deb](http://uk.archive.ubuntu.com/ubuntu/...untu8_i386.deb)
dpkg -i mencoder_0.99+1.0pre8-0ubuntu8_i386.deb

There are no dependencies issues for me. Don't downgrade mplayer.


worked GREAT! thanks!!!

---

### Post by Julianz on 2007-10-28
.

---

### Post by Julianz on 2007-10-28
It worked for me as well. Many thanks!.
The link did not work so I downloaded from [http://download.thaigrid.or.th/pub/ubuntu/archives/pool/multiverse/m/mplayer/](http://download.thaigrid.or.th/pub/ubuntu/archives/pool/multiverse/m/mplayer/)
Anybody knows how to tell the update manager to ignore this file for upgrade?

---

### Post by erissiva on 2007-10-29
> **Julianz said:**
> It worked for me as well. Many thanks!.
The link did not work so I downloaded from [http://download.thaigrid.or.th/pub/ubuntu/archives/pool/multiverse/m/mplayer/](http://download.thaigrid.or.th/pub/ubuntu/archives/pool/multiverse/m/mplayer/)
Anybody knows how to tell the update manager to ignore this file for upgrade?

I'm not sure how to set it to ignore. But, after using the "downgrade" patch from the official DeVeDe website, it hasn't asked me to upgrade mencoder/mplayer.



Also, for anyone reading Launchpad, a fix to this issue is currently being tested and **should** be pushed in a few days. Finally we'll get that faulty MPlayer out of the stream. ^_^

---

### Post by fivesmellydragons on 2007-11-06
I've been following this problem as well for a little while now and while everything works fine on my computer here, i.e. devede movies and such have no problem with the audio when played on my computer, there is still an issue when playing on a normal dvd player through a tv. Audio is MP3, but I can't find a solution yet to this dillemma. Anyone have anything?

---

### Post by TOOOL on 2007-11-20
with the latest update of memcoder and mplayer now fixing the sound problem  all seems fixed :guitar:
what happens with posts that are fixed like this, should they be deleted or archived

---

### Post by Rhadamanthus on 2007-11-21
I hope you are right about Mencoder and Mplayer being fixed; I just re-downloaded DeVeDe and will try it again tomorrow.
I vote to keep the thread active for at least a few weeks so that people like myself can locate all the words of wisdom regarding this problem.
Question: If the problem is fixed should I still add that "-afm ffmpeg" line to the app?

PS: I use Gutsy

---

### Post by StevenHarper on 2008-01-01
I am on Gutsy 32bit and the sound problem in DeVeDe (scrambled sound buzzing) still exists.

To fix the problem I followed the instructions (higher up in this thread) - this fixed the problem for me.

*As a workaround, in DeVeDe when you add a file, select "Advanced options" then "Misc" and in the "Extra parameters for Mencoder" box, enter "-afm ffmpeg".*

---

### Post by Dannyblueyes on 2008-01-09
I just installed devede back in early December. At first all the dvd's I burned worked perfectly.Any DVD I've burned  In the last two weeks the audio has been horribly mismatched. However, when I watch the same movies on my laptop using totem or Mplayer they work fine. 

Can anyone tell me a probable cause for this?

On a side note, my AVI copy of "Barfly" no longer works on my system either even though it played absolutely fine a month ago. I wonder if this could be related.

---

### Post by jmfrey on 2008-04-20
I'm still having problems with the audio cutting out at intervals after converting avi to DVD.  I've tried the solutions here, but none have helped.

Here's what I'm running.

Ubuntu Gutsy (7.10)
MPlayer 1.0rc2-4.1.3
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1

When I tried the "-afm ffmpeg" in the miscellaneous options, the preview was fine, but the eventual disc was not.

---

