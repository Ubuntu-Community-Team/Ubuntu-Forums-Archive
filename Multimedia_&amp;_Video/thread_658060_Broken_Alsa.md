---
title: "Broken Alsa"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by 4th guy on 2008-01-04
After having a couple of problems with Alsa, I decided to reinstall it, however something must have gone terribly wrong because i get these errors:
> me@my-desktop:~$ alsamixer
ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_V8237.so

alsamixer: function snd_ctl_open failed for default: No such file or directory
and
> me@my-desktop:~$ amixer -q set Master 100% unmute  
ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_V8237.so
amixer: Mixer attach default error: No such file or directory[
Any hints on this error?

---

### Post by NilsE on 2008-01-04
It sounds like something is not installed like the driver.  Make sure all of the packages in the attached screenshot are install in Synaptic.  If they are re-install them.

---

### Post by 4th guy on 2008-01-04
They're all there...oh dear.
> Reinstallation of libesd-alsa0 is not possible, it cannot be downloaded.
Reinstallation of libao2 is not possible, it cannot be downloaded.
Reinstallation of gstreamer0.10-alsa is not possible, it cannot be downloaded.
Reinstallation of linux-sound-base is not possible, it cannot be downloaded.
Reinstallation of libasound2 is not possible, it cannot be downloaded.
Reinstallation of libsdl1.2debian-alsa is not possible, it cannot be downloaded.
Reinstallation of libpt-plugins-alsa is not possible, it cannot be downloaded.

---

### Post by NilsE on 2008-01-04
Check your sources.list.  There may be a problem since it is saying they can't be downloaded.

It also looks like it is trying to access a Debian repository which may be your problem to start with.

Fix your list, remove all the packages in my list above and then install them via Synaptic.

---

### Post by 4th guy on 2008-01-04
If I try to remove those packages it tries to uninstall _everything_.

---

### Post by NilsE on 2008-01-04
> **4th guy said:**
> If I try to remove those packages it tries to uninstall _everything_.
OK, then just try to re-install them after checking your sources.list

---

### Post by 4th guy on 2008-01-04
Here it is. To me it looks like there's nothing out of the line:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

EDIT: On the second look via a gui editor, my list is screwed up.

EDIT2: Well, I reinstalled some things, and it still doesn't work

> 
## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse restricted universe main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe

---

### Post by NilsE on 2008-01-04
Not sure where to go with this.  It all points to something not being installed.

If you try alsamixer now do you get the same error re: the missing file?  

Have you checked that the file really does not exist? 

See if the missing file is somewhere else on the system by searching for it.

List what is in that folder the error is pointing to here.

---

### Post by 4th guy on 2008-01-04
I reinstalled the system, and now every time I open alsamixer, this error is given:
> alsamixer: function snd_ctl_open failed for default: No such device


---

### Post by Yellow Pasque on 2008-01-04
Try and get the ALSA working, but if things don't work out, you can always try OSSv4 (see link in my sig)

---

### Post by NilsE on 2008-01-04
Try this

In a terminal run: asoundconf list

This should return a list of cards. (If it does not show any then we have to start over.)

Replace   xxxxx  below with the name you found in list. I believe it is case sensitive.

In a terminal run: asoundconf set-default-card xxxxxx

Then again with sudo: sudo asoundconf set-default-card xxxxx

This will set the defaults for the card and create a config file. 

In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice

In the volume control turn on as many options as you can that show up on all of the tabs. Make sure none are muted.

---

### Post by 4th guy on 2008-01-04
The sound works at the logon screen, but not when I log on to my account.
I logged in the root account and the command alsamixer worked. What could be blocking my normal account?

---

### Post by NilsE on 2008-01-04
Add yourself to the audio group

you should add your username to the group file by doing

gksudo gedit  /etc/group

Now find the line that looks like

audio:x:29:root   #or something similar

and change it to

audio:x:29:root:username  #only replacing username with your real username (log in name) if your user name is not already there

Save it and reboot

---

### Post by 4th guy on 2008-01-05
I tried that, and it still does nothing. Then I found [this]("http://wiki.archlinux.org/index.php/ALSA_Setup#Setup_Permissions"):
> Alsamixer does not run

If running alsamixer does not work and you wind up with the following error

alsamixer: function snd_ctl_open failed for default: No such device

You might need to re-install your kernel. Run 'pacman -S kernel26' or whichever patchset you prefer to use. 
But I have absolutely no idea what to do. You'd think that something like the above quote would come up at the top of a search engine when you search for your error.

---

### Post by Yellow Pasque on 2008-01-05
Then I would definitely try installing OSSv4 (link in sig). Your sound chip is supported.

---

### Post by 4th guy on 2008-01-05
Does OSSv4 support surround sound?

---

### Post by Yellow Pasque on 2008-01-05
> **4th guy said:**
> Does OSSv4 support surround sound?
Yes.

---

### Post by 4th guy on 2008-01-05
I managed to reinstall the kernel. :) Of course, now I still have a problem with splitting the 2.0 sound across all 5.1 channels

UPDATE: So far I haven't made too much progress. I either get 4 speakers working at one go or two.

---

