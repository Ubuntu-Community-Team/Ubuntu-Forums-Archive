---
title: "Video recording in Linux.  Suggestions?"
date: 2012-10-27
forum: Multimedia Software
---

### Post by Ifaistos on 2012-10-27
Hello everyone :-)

The need has appeared to record video in linux.
eg.  webinars that can be uploaded to a channel for all people who didn't make it on time.

I've never done this before.
People told me that camtasia for windows is one of the best for that operating system.

I have gotten rid of Win7 on both my machines, and I run on both of them Linux.

Can anyone propose a way to have the same functionality as camtasia?  I could run it on Wine if need be.

Are there any open source programs that I could use natively in Linux?

Thanks all

---

### Post by bbarcesaj125 on 2012-10-27
I'm not sure i understand your question but if screencasting is what you're trying to do, i suggest Kazam (screenrecording tool).
you can install it using this command:
```
sudo apt-get install kazam
```

---

### Post by cybrsaylr on 2012-10-27
I was wondering about this also and found this:

[http://www.webupd8.org/2012/01/kazam-screencaster-10-released.html](http://www.webupd8.org/2012/01/kazam-screencaster-10-released.html)

Kazam 1.0 is available in its stable PPA for Ubuntu 11.10 and 12.04. To add the PPA and install it (Ubuntu Oneiric and Precise only!), use the commands below:

Linux terminal:~$
> sudo add-apt-repository ppa:kazam-team/stable-series
sudo apt-get update
sudo apt-get install kazam

---

### Post by Ifaistos on 2012-10-27
yeap :-)

This is what I wanted to do.  Screen recording!
I am going to install it and give it a go...

I just upgraded to 12.10... is it available for the latest Ubuntu?

---

### Post by Ifaistos on 2012-10-28
It seems there is an error produced when I add the ppa.
I have been able to install the software, but now my "Software updater" is broken.

When I launch it, it tries to download from the ppas and it crashes with the error below.

I had to download a ppa manager, to delete the kazam ppa, for the software updater to work.

Is there a workaround for that?

Thanks


W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 199.47.217.170 80]
, W:Failed to fetch [http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://linux.dropbox.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 199.47.217.170 80]
, W:Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/kazam-team/stable-series/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Ifaistos on 2012-10-28
ok... the reason for this error was that the repositories didn't exist..

Back to kazam.
I don't think it works in 12.10.
I don't know why, but when I press stop recording it gets stuck.
Can anyone confirm that it actually works in 12.10?

I am using gtk-record my desktop, but it is slow, and with less options.

From what I saw, kazam is much better... but I need to get it to work on my machine.

Thanks for the help.

---

### Post by Abhinav Kumar on 2012-10-28
Go to
[http://www.screencast-o-matic.com/](http://www.screencast-o-matic.com/)
and do the screen recording by allowing the java applet to run:)

---

### Post by Ifaistos on 2012-10-28
ok thanks :)

I am installing java runtime from the Software Center, as we speak.

However I would still like to have Kazam on my computer.
Is there anyone who has made it run successfully on 12.10?

Thanks all...

---

### Post by Ifaistos on 2012-10-29
bump :-)

---

### Post by VanillaMozilla on 2012-10-29
Desktop Recorder.  You probably already have it.  Or get it through the Ubuntu Software Center.

---

### Post by Ifaistos on 2012-11-01
I find it very limiting.
Can anyone confirm that kazam runs on 12.10?

Thanks

---

### Post by Ifaistos on 2012-11-03
Bumpity bump :-)

---

### Post by cybrsaylr on 2012-11-03
> **VanillaMozilla said:**
> Desktop Recorder.  You probably already have it.  Or get it through the Ubuntu Software Center.

It is in Synaptic also.
Desktop Recorder is KDE. Will it work OK with Ubuntu, or does it have to be tweaked?

---

### Post by cybrsaylr on 2012-11-03
Was just playing around with all 3 apps and Kazam works the best and fastest on 64 bit 12.04 but the picture quality on copies isn't top grade and audio is acceptable.

Couldn't get RecordMyDesktop to work at all.

Recorditnow worked but takes a long time to encode and again picture quality isn't top grade, plus pic motion is jerky  and couldn't get any audio on my copy samples.

Found all 3 in Synaptic.

---

### Post by FakeOutdoorsman on 2012-11-03
Have you tried **ffmpeg**?
[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719)

---

### Post by cybrsaylr on 2012-11-03
> **FakeOutdoorsman said:**
> Have you tried **ffmpeg**?
[HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719)
I used FFmpeg solely to upload songs to YouTube with 11.04. It worked great. Since moving to 12.04, FFmpeg doesn't work and haven't tweaked it yet to get it working on 12.04 as yet. 

Didn't know you could use FFmpeg for that purpose. Will have to look into it when I get some time.

---

### Post by monkeybrain2012 on 2012-11-03
You added the wrong ppa. Kazam stabe is only offered for 12.04 and 11.10
[https://launchpad.net/~kazam-team/+archive/unstable-series](https://launchpad.net/~kazam-team/+archive/unstable-series) 
Check the drop down window "published in" and see for yourself.

You need the ppa for kazam unstable (I know, it sounds terrible but it works)

[https://launchpad.net/~kazam-team/+archive/unstable-series](https://launchpad.net/~kazam-team/+archive/unstable-series)

```
sudo add-apt-repository ppa:kazam-team/unstable-series
sudo apt-get update
sudo apt-get install kazam
```

EDITED: I am not sure what other capabilities do you need apart from recording your desktop and maybe adding audio (which kazam is very capable and much better than recordmydesktop) but there is also webcam studio
[http://www.ws4gl.org/](http://www.ws4gl.org/)
It sounds sophisticated and full of features but I have never used it. :)

---

### Post by cybrsaylr on 2012-11-03
Was playing around with Kazam. It works fine on 64 bit 12.04 but the picture quality on copies isn't top grade. The color is off, usually too green. Is there a way to correct color to make it more like the original? Audio copy is fine.

---

### Post by Ifaistos on 2012-11-04
@ monkeybrain

Thanks!  So you are saying that this version is for 12.10?
The one for 12.04 doesn't work for sure..

I will give it a try immediately.

---

### Post by resruta on 2012-11-04
If you also need to do some editing afterwards I would suggest using Cinelerra. There are plenty of options and - as I said you have the possibility to do some serious editing.
At least for the community-version there is a PPA maintained by Nicola Ferralis:
[https://launchpad.net/~cinelerra-ppa/+archive/ppa](https://launchpad.net/~cinelerra-ppa/+archive/ppa)
You could also compile it yourself, the code for the original non-cv Version can be found here:
[http://heroinewarrior.com/cinelerra.php](http://heroinewarrior.com/cinelerra.php)

There are also some tuturials how to do screencasting, e.g.
[https://www.youtube.com/watch?v=MhaOgNQ0Bbc](https://www.youtube.com/watch?v=MhaOgNQ0Bbc)

---

### Post by Ifaistos on 2012-11-05
I installed Kazam, and it works erratically at best with 12.10.
Window casting makes it hung up.
Area casting produces unwatchable video.

To record from microphone I need to check on speakers... go figure.  Sound is very nice, but intermittent.

I will try Cinelerra, I hope screencasting will work with it.

Thanks

---

### Post by cybrsaylr on 2012-11-05
I installed Kazam on 64 bit 12.04 and it works fairly well. The only problem is the color of copies is off, usually too green. Will  Cinelerra correct the color or is there a better solution to make color look as accurate as the original?

---

