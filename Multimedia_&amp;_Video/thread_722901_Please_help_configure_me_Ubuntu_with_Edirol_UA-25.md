---
title: "Please help configure me Ubuntu with Edirol UA-25"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by meaghers on 2008-03-12
Hello all, long time listener first time user :)

I am having lots of fun playing with my new Ubuntu install.  I've played with Mandrake a few years ago, but I'm still just getting my feet wet in Linux goo.

I have searched a lot and still cannot figure out how to fix my problem.  I have an Edirol UA-25 usb sound device that I'd like to use for everything audio related.  I don't even care if my onboard sound is recognised, in fact I've inserted an -ignore statement somewhere ... anyhow, I've tried a lot over the last 3 days and am such a beginner that I would really appreciate someone helping me out and walking me through a few steps.  

So far I've read and followed to the best of my abilities the info. on the following pages:

[http://alsa.opensrc.org/index.php/Edirol_UA-25](http://alsa.opensrc.org/index.php/Edirol_UA-25)
[http://meandubuntu.wordpress.com/2008/01/30/ubuntu-and-studio-work-pt-1-foundations/](http://meandubuntu.wordpress.com/2008/01/30/ubuntu-and-studio-work-pt-1-foundations/)
[http://ubuntuforums.org/showthread.php?t=451596](http://ubuntuforums.org/showthread.php?t=451596)
[http://www.backports.ubuntuforums.org/showthread.php?t=271897](http://www.backports.ubuntuforums.org/showthread.php?t=271897)

Nothing seems to address what I'm experiencing specifically.  I have no idea of what outputs of what commands or contents of files would be useful to someone to help, but I am ready to be helped when someone offers.  :)

---

### Post by daengbo on 2008-03-13
> Nothing seems to address what I'm experiencing specifically.
You don't really say what you are experiencing. Does the card work at all? Is it missing functionality? What's the issue?

---

### Post by meaghers on 2008-03-16
> **daengbo said:**
> You don't really say what you are experiencing. Does the card work at all? Is it missing functionality? What's the issue?

My apologies, I suppose my explanation was lacking.  Since this post I have reinstalled gutsy for an unrelated reason.  So now I have a chance to start fresh.

Upon entering 'sound preferences', selecting 'usb audio' and then clicking 'test', sound preferences would shut down.  I searched around and found this:

[http://sudan.ubuntuforums.com/showthread.php?t=653939&highlight=edirol](http://sudan.ubuntuforums.com/showthread.php?t=653939&highlight=edirol)

following these instructions to rollback alsa to 1.0.13 worked to resolve that issue.  Now I can get playback through my UA25 and for now I'm not concerned about recording.

However, playback is currently working with rhythmbox and movie player, but not mplayer, which is where I started running into trouble on my last try.  It seems to me that I am missing some connection between the sound card and alsa.  I don't fully understand what alsa is, what it does, and how it does it.  I will search this out.  I also would like to control main volume from the taskbar.

---

### Post by meaghers on 2008-03-16
Following this page;

[http://alsa.opensrc.org/index.php/Edirol_UA-25](http://alsa.opensrc.org/index.php/Edirol_UA-25)

I have created a .asoundrc file in my home directory as: > pcm.!default {
  type             plug
  slave.pcm       "softvol"
}
pcm.softvol {
  type            softvol
  slave {
      pcm         "pasymed"
  }
  control {
      name        "SoftMaster"
      card        1
  }
}
#This PCM combining the dmix and dsnoop slaves
pcm.asymed {
     type asym
     playback.pcm "dmix"
     capture.pcm "dsnoop"
}  
#This PCM should be able to convert recording rates automatically
pcm.pasymed {
     type plug
     slave.pcm "asymed"
}
pcm.record_left {
  type        dsnoop
  ipc_key 234884
  slave {
      pcm     "plughw:UA25"
      channels 2
  }
  bindings.0  0
}
pcm.record_right {
  type        dsnoop
  ipc_key 2241234
  slave {
      pcm     "plughw:UA25"
      channels 2
  }    
  bindings.0  1
} 

I should note that I believe my card is card 1 in my system because...

> meaghers@meaghers-media:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with ALC202 at irq 21
 1 [UA25           ]: USB-Audio - UA-25
                      EDIROL UA-25 at usb-0000:00:1d.1-1, full speed

so I changed my .asoundrc file to reflect this ... I think.

---

### Post by meaghers on 2008-03-16
Now I have UA-25 (alsa mixer) available in gnome.volume.control 2.20.1 on the taskbar, however I can not get any sound :(

No playback in rhythmbox or through the 'sound preferences' 'test' button.  In sound preferences, I have 'usb audio' selected for all options, but have tried 'ALSA mixer' also to no avail.

help?

---

### Post by daengbo on 2008-03-17
First of all, your basic sound was working before you edited .asoundrc, so delete that since it's obviously not working.

There are two parts to the sound (really three, but ...). ALSA handles moving sound to your sound card. ESD is a Gnome daemon which mixes multiple sources and then feeds tham to ALSA. In short, an application can send sound to ALSA directly or use ESD to do it. If one application is using ALSA, then other applications will need to wait until the first one is done, locking out sound.

Totem and Rhythmbox use ESD by default, so we know that ESD and ALSA are working correctly (for playback). MPlayer simply isn't sending the sound to the right place. It may be trying to use an older system called OSS, in which case the sound isn't going anywhere.

Try running mplayer from the command line (in a terminal) using the following options.
mplayer -ao esd testfile.avi
mplayer -ao alsa testfile.avi

See if those work. If they don't, look in the terminal for errors and post them here.

Also check sound recorder to see if you can record.

---

