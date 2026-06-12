---
title: "MythTV and ATI All-In-Wonder Radeon"
date: 2008-08-21
forum: Multimedia Software
---

### Post by TrashmanL on 2008-08-21
A brief history: 
The first few flavors of Linux I tried, I could not get to recognize my all-in-wonder as a TV tuner card. I had all but given up on it until I used a Dapper LiveCD. On it, it had XawTV which just worked.

I later installed Fiesty, and have since upgraded to Gutsy.

The problem... the XawTV UI is terrible, and doesn't have many options. I've been searching for a better program. I can't get Zapping, TVtime or MythTV to work. But XawTV still JUST WORKS. I want to use MythTV, but it didn't work right from the install and I have no clue what drivers to use in the setup. There are no /dev/video# devices at all on my computer.

I've searched these forums multiple times and this thread is the only one I found that seems at all relevant to my problem: [http://ubuntuforums.org/archive/index.php/t-220027.html]("http://ubuntuforums.org/archive/index.php/t-220027.html")

That is for a TV-Wonder tuner card, which I think uses the same tuner, but I'm concerned that running the modprobe commands might possibly screw up my XAWtv and leave me with no working Tuner programs at all.

Has anyone else got a working MythTV/All-In-Wonder setup? How did you you do it? 

Alternately, if no one else has that setup, where can I find what drivers XawTV is using? I did a search for Xaw* on my computer and the only config files I found were frequency tables, and install scripts, nothing pointing out drivers.

---

### Post by TrashmanL on 2008-08-21
I tried the modprobe commands from the forum I linked to. They didn't break my system, but they didn't work, either.

I found the command:

```
xawtv -hwscan
```

which gave:

> 
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-15-generic)
looking for available devices
port 73-73                              [ -xvport 73 ]
    type : Xvideo, video overlay
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay


If I understand this right, it seems XAW TV can access the "ATI Radeon Video Overlay" directly but MythTV and others need a /dev/something to look for, and there is none on my system. Is there some way I can create a device that points to this?

---

### Post by gcodner on 2008-11-06
To answer your question directly, MoTV has a a slightly better user interface (UI) than raw xawtv and since it uses xawtv, it should work without /dev/video0, etc.  MoTV conveniently uses your existing .xawtv file.

I was even able to use the RF remote control without a problem, although I needed to edit the /etc/X11/app-defaults/MoTV file in order to be able to use the digit keys.  I also defined vol up/down, etc.  

Apparently, xawtv is using Xvideo for the ATI A-i-W Radeon instead of /dev/video0.  As a result, video recording is not available.  I am trying to determine whether this is a hardware or software limitation. I am happy that I can watch TV, but I would love to record also.  And I would like to be able to see closed-captions.  I should also mention that scantv does not work.

I too, found that tvtime, MythTV and scantv did not work because there is no /dev/video0.  Xawtv (and motv) works only with Xvideo.  Commands such as:

```
motv -noxv
```

produce:

> 
This is motv-3.95, running on Linux/i686 (2.6.24-21-generic)
Warning: Actions not found: Remote
Warning: Actions not found: Remote
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available.


The command:

```
xawtv -noxv 
```

produces similar results.

Perhaps we should start a new thread on the subject of /dev/v* since your original question was specifically about the UI.

Threads on this subject seem to do die a slow and agonizing death, sometimes with lot's of, "Gosh my Hauppage card works fine." and "Did you plug the card in?" posts.  The card is there and obviously recognized.

---

