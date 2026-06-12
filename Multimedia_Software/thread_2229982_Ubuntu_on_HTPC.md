---
title: "Ubuntu on HTPC"
date: 2014-06-16
forum: Multimedia Software
---

### Post by buisteric on 2014-06-16
Hi,

I have been using XBMC for a year or two on Ubuntu 12.04. After upgrade to 14.04, playback of MKV files is broken. I am getting correct video (at least as far as I can see), correct sound effects, but voices are almost inaudible. They output faintly only on the left channel. I read all sorts of threads about people having audio problems, even somebody on a forum suggesting to hire actors to recreate the voices rather than fiddling around with the issue! I pretty lost hope of any simple solution after I read that.

VLC is playing back the MKV files fine, with correct audio. However, selection of a movie cannot be fully done with the keyboard like in XBMC. The best I can do is to type the movie name on the command-line, but the right shift on my wireless keyboard is wrongly placed, always confused with arrow keys, causing typing issues as soon as I need a / in the command line. Moreover, I found no shortcut keys to put VLC in full screen, set aspect ratio to 16:9, switch language, disable subtitles and even activate the menu bar. Alt, that used to so since years, now displays a search box similar to the Dashboard and thus seems a mapping to the Windows key. Probably reconfigurable, but I guess I would have to hack into xorg.conf and xmodmap, and that will break the next update.

I tried to upgrade to latest XBMC because maybe that will fix my audio issue for free. No avail. Now the XBMC PPA does not work anymore. After a few seconds, add-apt-repository responds with an error saying there is no such PPA and to check the name. I checked multiple times, I copy/pastes the name from XBMC's site, to no avail. Maybe the PPA is not available in 14.04.

So I would like to get a player similar to XBMC that would offer full keyboard navigation and be available from main repositories, not from PPAs which get out of sync. I could have waited a few weeks for the XBMC repo to be updated to 14.04, I should have checked this more carefully before dist-upgrading, but I am not ready to refrain from updating for months because of a PPA.

Before XBMC, I tried many different other players. MPlayer gave me good results, but I had to type the file names on the command line and sometimes, fast-forward or backward didn't work; was crashing the player or moving at start or end of file. Totem is a bit random. Sometimes it plays well, sometimes not, if I remember well no AC-3 passthrough. VLC is good, a bit more stable than MPlayer against the files I have, but the ncessity to use the command line and key functionalities not accessible with the keyboard annoy me. I gave a shot at MythTV: this is too heavy weight, the backend is accessing the hard drive CONSTANTLY and is incapable of any connection with the fronted.

Yes, I know about Mythbuntu and XBMCbuntu, but I would like to avoid a clean install for different reasons. First, my HTPC is hooked up to a 1080p HDTV and I need some larger fonts to operate the Linux box. These fonts are not set up by default when starting a live CD so reinstalling from scratch will be a real hassle for me. Moreover, I now have several hard drives in the machine and will have to set up their mount points one by one during installation. With the too small font, that will be hard, and sometimes, the installer crashes for one reason or another, and I usually have to do the mountpoint setup multiple times. Doing it post-install requires manual editing of /etc/fstab and copy/pasting of device UUIDs, which is tedious. Yes, everything is doable and if I am sure that will fix my HTPC, I will try it, but I would like to avoid time consuming guess work consisting of trying many Ubuntu variants or other Linux distributions.

Maybe I should try my luck with recompiling XBMC from source, but I really hate doing this because this takes too much time, usually this requires fixing dependencies issues and I even had, sometimes, to fix the build process and some souce files! And that completely bypasses the APT packaging system. If, later on, XBMC PPA becomes available again, I will be stuck with out-of-APT compiled files and probably won't be able to install any XBMC updates without clean reinstalling Ubuntu or recompiling again from source.

Any idea? Thanks in advance.

---

### Post by TheFu on 2014-06-16
I'm still on Ubuntu Server 12.04 + xbmc + Plex Server.  Thanks for reporting that there are issues.  Unfortunately, their isn't much troubleshooting information in your post.  No log data, no error messages, etc.

I don't have a keyboard connected to my xbmc system.  Do everything through ssh from a different machine and the remote control. When it is working well, I don't patch more than quarterly. WAF is extremely important.

In August, I'll consider migrating to 14.04 server, if others report it is working good.  At this point, Plex maintains the media data and XBMC is just a playback device. I like that plex is a great DLNA server and can serve pretty much every device in the house cleanly.

At this point if I were you, I'd reload 12.04 from a backup.

---

### Post by SuperFreak on 2014-06-16
I have XBMC installed on my HTPC (Gotham 13) and no audio problems with MKV files
Try

```
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt-get update
sudo apt-get install xbmc
```

---

### Post by buisteric on 2014-06-19
I tried

sudo add-apt-repository ppa:team-xbmc/ppa

That hung for a few seconds, then displayed it could not find the PPA and to check the name. I then tried to enable back the Team-XBMC source by editing APT's sources.list.d directory and that worked. So it seems add-apt-repository had an issue, but the repo was there.
Unfortunately, I don't have a 12.04 backup. I don't have any reliable tools to make such backups. All I tried take more than one hour to operate, requires an external disk that I don't have, and create an unusable image when trying to recover.

At least XBMC is now updated to 13.1.

But the machine became too slow so I tried to replace Unity with something lighter, but all lightweight alternatives I know of lack keyboard shortcuts even for launching the start menu.

---

### Post by TheFu on 2014-06-19
Don't have reliable tools to make backups?  Seriously??????????!   There are 20 great tools in the repos just for backups - if you can't get those working, ask.  I use rdiff-backup, but suspect you'd be happier with fsarchive which makes an image.  Of course, you'll need storage to put the image. It is impossible to compress 20G down to 5KB, sorry. That storage does NOT need to be external, but it would be foolish NOT to have it external or at least inside a different machine.  Backups on the same physical HDD are foolish for too many reasons to list, of course, you can still put backups there, if you like. :(

An hour backup is long?  There is at least 6 hours every 24 hrs when the PC isn't doing anything, right? That is a poor excuse for not doing backups. The 2nd-500+ths backup takes less than 4 minutes with rdiff-backup. It is just that 1st one that takes more time. I'm using rdiff-backup over a LAN to Linux storage.

13.10 support ends in July ... that is 2 weeks.  12.04 has support until 2017 and 14.04 until 2019.

Keyboard shortcuts are controlled completely BY YOUR SETTINGS!  ALT-F2 works on every Linux distro that I know, so opening a terminal and running things is easy ... I run LXDE and there is a config file in ~/.config/openbox/lxde-rc.xml where you can setup any keyboard accel that you wish.  XFCE uses something similar, I'm positive.  Of course, knowing what tools you'd like to run is important.

Sorry - rereading your last post makes me believe that Linux isn't a good choice for you.

---

### Post by SuperFreak on 2014-06-19
```

sudo add-apt-repository ppa:team-xbmc/ppa
```

I tried the command on my 14.04 machine and it worked with no issue. Did you use the copy command to enter it into terminal or type it manually. Typing manually will lead to errors frequently. As far as I can see there are no issues with the PPA as I have it on my own HTPC and has worked flawlessly.
You will be prompted when you enter the command into terminal to press the ENTER key to proceed and then add the other two commands one at a time

---

### Post by buisteric on 2014-06-19
Why are you telling Linux is not the right choice for me? Because I am not able to efficiently copy/paste command lines from web sites? NO, I am not efficient at this, because when I select the beginning of the command line, I miss one character or two, I have to redo it, redo it, miss the end, then finally get it, but that is just completely inefficient, and there should be better ways, like shorter, easier to remember command lines or GUIs. I have terrabytes of movies on Ext4 partitions, so it is too late now to roll back to a non-Linux solution. Correct, I will stop posting and looking at forums since I only get flames because I am not efficient at copy/pasting command lines, I don't spend my weekends doing backups and monitoring if they work or fail, etc. But I would have liked to know in 2009, before assembling my HTPC, that it would be a dead end and only loss of time.

---

### Post by SuperFreak on 2014-06-19
Take it easy. Just suggesting that you copy the command instead of typing manually so you don't make any mistakes. enter each of the 3 commands i gave you separately

---

### Post by buisteric on 2014-06-20
Hi,

XBMC is now updated to 13.1. I just enabled back the APT source pointing at team-xbmc repo and made sure it was pointing to trusty. However, AC-3 passthrough does not work anymore. I made sure it is enabled in pavucontrol, but despite of this, I get no passthrough: sound is downmixed to stereo. Trying with MPlayer or VLC, AC-3 is correct since they go through ALSA directly. Trying with Totem or XBMC, which go through PulseAudio, I get no AC-3. Trying to force XBMC into ALSA using AE_SINK=ALSA xbmc resulted in cracky distorted sound and still no AC-3. So seems there are bugs with XBMC and PulseAudio. I cannot uninstall PulseAudio since I sometimes use the machine for YouTube video playback.
I am not tied to XBMC. Anything that would work under Ubuntu and be controllable from the keyboard and not requiring long and error prone command lines would be great.

TheFu, thanks for the references to backup tools. SuperFreak, my last reply was not meant at you but rather at TheFu proposing me to give up on Linux, without any clear solution for my HTPC.

---

### Post by buisteric on 2014-06-20
Hi again, now it seems to work. Installed libasound2-plugins-extra and going into pavucontrol to enable AC-3 and DTS. After another freaking crack sound, AC-3 suddenly started working. I shut down and restarted XBMC and still working. Will have to see if that remains stable.

---

