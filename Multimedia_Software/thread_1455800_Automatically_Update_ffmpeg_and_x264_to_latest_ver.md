---
title: "Automatically Update ffmpeg and x264 to latest versions with FakeOutdoorsman's How To"
date: 2010-04-16
forum: Multimedia Software
---

### Post by prupert on 2010-04-16
Hi All

I have written a script, with his permission, to automate FakeOutdoorsman's excellent [how tos]("http://ubuntuforums.org/showthread.php?t=786095") for updating to the latest versions of ffmpeg and x264 from source.

I have written up about the script on my personal blog here: 

[http://www.prupert.co.uk/2010/04/16/automatically-update-ffmpeg-and-x264-from-source-svn-in-ubuntu/](http://www.prupert.co.uk/2010/04/16/automatically-update-ffmpeg-and-x264-from-source-svn-in-ubuntu/)

And the scripts themselves are hosted on Google Code here:

[http://code.google.com/p/x264-ffmpeg-up-to-date/](http://code.google.com/p/x264-ffmpeg-up-to-date/)

As stated on both sites, this is BETA code, and these scripts do some powerful things to your system, like installing and removing packages and making and deleting files. I would only recommend using them if you know what you are doing. Also, the completelyclean.sh script can really cause a few problems if you are aren't careful, I wouldn't use it.

That being said, the scripts seem to work well and I find them useful. Please feel free to try them out, but if you have any problems or questions, please post them on this thread, on my blog or, better still, on the Google Code page. Cheers.

---

### Post by mc4man on 2010-04-16
While haven't tested your scripts, did take a look at them, (always something to be learned).

In the update one it *appears* the new x264 will be 1:0, if so, that's probably not a good idea for lucid.

(for sometime I've been using 2:0 for x264 and 5:0 for ffmpeg, whether static or shared packages.
The reason's are/were for something else, though there is no issue doing so for karmic and eariler

---

### Post by prupert on 2010-04-16
Ahh, good catch, I didn't see that. I add distro checking to the update script so it is version 2 for Lucid and version 1 for the others. Also, it seems that the versions for ffmpeg also change, so I'll fix that as well.

Cheers for taking the time to look into this.

EDIT:

I've now updated ffmpegup.sh to update via Distro, to keep the pkg versions correct.

---

### Post by FakeOutdoorsman on 2010-04-16
I added your script to the Additional Resources section of [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095).

I have yet to test it though, but I did look through it quickly and it looks good to me, but my bash scripts are very simple in comparison.

You should check the guide occasionally to see if there are any major changes or updates.  Or perhaps you can subscribe to the thread and I can start new replies when changes are made.

---

### Post by prupert on 2010-04-16
Coolio, cheers. Yeah, I'll defo be subscribing to the post so I can then integrate any updates. If you could post a reply to the thread when you update it, that would be the easiest thing.

Killer, as they say in Oz.

---

### Post by mc4man on 2010-04-16
As a small aside. a 'good' thing that's in the update script is the removal of the the previous ffmpeg build before updating the x264 one.

That will eliminate the possible core version error when the new x264 core # is higher than the one an existing ffmpeg was built off of.

(if that potential 'merry-go-round ' is still a possibility - havent ck.'ed recently

---

### Post by Bonster on 2010-04-16
good timing, gonna try this on lucid

---

### Post by prupert on 2010-05-14
Just a quick update to the scripts, so that ffmpegupv1.4.sh can now be run using a config file (that it creates the first time you run it). This allows the script to be run with no user interaction, so it can be called via cron.

You can also copy the .debs created by checkinstall to a folder of your choice, so you can install the packages on other systems running the same distro.

Updates are here:


[http://code.google.com/p/x264-ffmpeg-up-to-date/](http://code.google.com/p/x264-ffmpeg-up-to-date/)

---

### Post by scar1 on 2011-04-01
Hi,

Thanks very much for these scripts. It has indeed helped me keep up to date with the latest releases of FFmpeg. I have recently come across a bug in FFmpeg which is fixed in a newer version. 
My version of FFmpeg is "SVN-r26402" and not sure if your scripts will look at the new git repositories as they have moved and soon to be removing the SVN repository. 

I could remove and manually obtain the newest version on git repo however your script has worked so well for me (and others) thought it might be a good idea to update the script so we can continue using.

Apologies in advance if this is already looking at git repo's and I have missed when looking at the script.

Many thanks
Scar1

---

### Post by prupert on 2011-04-01
Hi

I have been a bit slack on this front, what with a new job, potential redundancy and a 12 month old baby girl (excuses excuses) so you are right, I haven't updated the scripts to accommodate the git changes.

However, I shall update these scripts this weekend, as, for once, I haven't got that much on. I think there were also a few bugs that could be squashed and some other clearing up.

So, should be done by Sunday evening, I'll post here to let you know.

---

### Post by scar1 on 2011-04-01
Hi,

Once again thanks very much!
I appreciate that you are a busy and your efforts are much appreciated. 

If you can update at your next convenience is good enough for me :-) 

Cheers
Scar1

---

### Post by prupert on 2011-04-02
Hi

I've update the scripts, I just have to check them on a couple of virtual machines (I'll just check Maverick and Lucid) to make sure they are both working ok.

They should be available later on this evening (UK time).

Rgds

---

### Post by prupert on 2011-04-02
Hmm, bash isn't behaving itself at the moment, so running into some problems.

In the meantime, I have released a temporary script that works for Maverick ONLY.

This is the initial install script:

[http://x264-ffmpeg-up-to-date.googlecode.com/files/ffmpeginv2mav.sh](http://x264-ffmpeg-up-to-date.googlecode.com/files/ffmpeginv2mav.sh)

And this is the subsequent update script:

[http://x264-ffmpeg-up-to-date.googlecode.com/files/ffmpegupv2mav.sh](http://x264-ffmpeg-up-to-date.googlecode.com/files/ffmpegupv2mav.sh)

Because FFmpeg has moved over to git, you need to run both, you can't simply use the update script over an old SVN install of FFmpeg. I haven't been able to try the scripts on a pre-existing FFmpeg build using SVN, so I am not sure if any issues may occur with the existing /usr/local/src/ffmpeg folder being SVN and not git.If it isn't an issue, everything should install fine then.

---

### Post by scar1 on 2011-04-03
Hi,

Many thanks for your help here. I understand your very busy and appreciate the time you have taken to update this. 
I am currently running Lucid so will hang on till a later. May even be worth while totally removing and starting with a fresh install using the new script looking at the git server.

Many thanks again....
scar1

---

### Post by prupert on 2011-04-04
Hi

If you use this version, it supports Lucid:

[http://x264-ffmpeg-up-to-date.googlecode.com/files/ffmpeginv2.sh](http://x264-ffmpeg-up-to-date.googlecode.com/files/ffmpeginv2.sh)

This is the initial install script, rather than the update script, but since FFmpeg is now updated via git, I think you'll need to start from scratch anyway.

I'll update the update script later on this week, but in the meantime, this will get you the latest version of FFmpeg and x264 on lucid ;)

---

### Post by searler on 2011-04-13
Thanks for the efforts. I tried the script on a Lucid install and I get the same problem as when I manually followed the HOWTO :

/usr/bin/installwatch: line 322: /var/tmp/tmp.1DPryeBSQQ/installscript.sh: Permission denied

occurs at the checkinstall point of the instructions.

My permissions on /var/tmp are normal (I think) :

drwxrwxrwt  3 root root    80 2011-04-14 11:36 tmp

Any hints greatly appreciated.

---

### Post by searler on 2011-04-13
Finally tracked down the problem : /var/tmp is mounted as tmpfs with noexec flags in /etc/fstab.
I am temporarily changing the mount permissions until I have everything in place. I tried setting TMPDIR in my environment but that didn't help

---

### Post by scar1 on 2011-04-25
Thanks [prupert]("http://ubuntuforums.org/member.php?u=312245") - much appreciated!

---

