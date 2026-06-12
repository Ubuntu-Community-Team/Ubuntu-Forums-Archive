---
title: "Missing MP4 option in Handbrake"
date: 2014-07-07
forum: Multimedia Software
---

### Post by andrea b on 2014-07-07
I'm a newbie (learning on my excellent mistakes) and running Trusty on several older ThinkPads.  Handbrake has long been my go-to video transcoder ... and I was really surprised to see that there is no MP4 option in the release I installed via Software Center (MP4 is an option in the drop down list in the 'Video' tab, but not the Destination tab; all roads seem to lead to mkv files.)

I've read the posts [here]("http://ubuntuforums.org/showthread.php?t=2076246&p=12319446&viewfull=1#post12319446") and [here]("http://ubuntuforums.org/showthread.php?t=2221790").  I'm just beginning to get the hang of repositories, ppas, and all that.  But I'm not savvy enough to pull off SeijiSensei's fix which was to:

Rename the file /etc/apt/sources.list.d/stebbins-handbrake-releases.trusty.list to stebbins-handbrake-releases-raring.list, and then to edit that file to read:

```
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu raring main
```

Can someone help me with performing this task (using sudo in the command line)?  ... I've  added the ppa  (stebbins-handbrake-releases-trusty.list.)  

As a total noob, I tried renaming it (to raring') and editing the gedit (to 'raring') via the GUI (I know, I know...you can't do it that way!)

---

### Post by coldcritter64 on 2014-07-08
> **andrea b said:**
> ...MP4 is an option in the drop down list in the 'Video' tab, but not the Destination tab; all roads seem to lead to mkv files....
Have you installed the ubuntu-restricted-extras package to your install ? Doing so may give you better codec support for the MP4 file type.

If you already haven't added the restricted extras package, I'd suggest installing it and see if you can write to MP4 in handbrake before trying the ppa version of handbrake, you may not necessarily need the ppa version if you only have a codec issue.

If you need to add it, copy/paste the next code to a terminal  ...
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SeijiSensei on 2014-07-08
> **andrea b said:**
> But I'm not savvy enough to pull off SeijiSensei's fix

Sorry I wasn't sufficiently clear, Andrea!  Let's take it step-by-step.  Open a terminal, then

1. Rename the file:
```

cd /etc/apt/sources.list.d
sudo mv stebbins-handbrake-snapshots.trusty.list stebbins-handbrake-releases-raring.list

```
The "mv" or "move" command will rename a file if a new directory path is not specified for the move.

2.  Edit that file:
```

sudo nano stebbins-handbrake-releases-raring.list

```
This will open the "nano" editor.  It's a convenient choice for many users because it includes a menu of command at the bottom of the screen.  Nano uses a variety of Ctrl-key sequences for commands.  In the menus they are designated like "^X" which means hold down Ctrl and hit the "X" key.  So, using nano, edit the "deb" entry in that file so it reads:
```
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu raring main
```
then save the file with Ctrl-X to exit and typing "Y" to save when prompted.

3.  Update your repositories and install
```

sudo apt-get update
sudo apt-get install handbrake-gtk

```

Before you do this, I would purge any existing versions of Handbrake with
```

sudo apt-get purge handbrake handbrake-*

```

Let me know if this works for you.

Just adding the restricted-extras repositories doesn't work for Handbrake.  [It does not use any external encoders]("http://ubuntuforums.org/showthread.php?t=2221790&p=13013059&viewfull=1#post13013059"), so adding the various libavcodec and gstreamer items in restricted-extras won't affect how Handbrake operates.

---

### Post by andrea b on 2014-07-08
> Have you installed the ubuntu-restricted-extras package to your install ? Doing so may give you better codec support for the MP4 file type.

Thanks, coldcritter - yes, I did that among the other 20-odd tasks after installation.

---

### Post by andrea b on 2014-07-08
Thanks, Sensei!  This is just a quick, initial thank-you -- I'll try it later this evening.  And - you were plenty clear for anyone versed in command line basics!  I'm  ... getting versed, but couldn't get the mv command just right. And ... you really don't want to get that *wrong!*

A deep bow and an offering to the mononoke.

---

### Post by andrea b on 2014-07-09
> Let me know if this works for you.

Thanks, SeijiSensei - seems to have worked.  

Another bow, and offerings to the mononoke.  

So grateful to this community as I learn the mysteries of Ubuntu.

---

### Post by Bucky Ball on 2014-07-09
*Thread moved to **Multimedia & Video**.*

---

