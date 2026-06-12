---
title: "map script to keyboard button (actually remote)"
date: 2010-12-01
forum: Mythbuntu
---

### Post by davidstoll on 2010-12-01
I have a remote that is actually detected as a keyboard.  It has extra colored buttons that I would like to assign to a shell script (.sh or even a perl .pl script) to be executed.

The upgrade to 10.10 really screwed up LIRC and I am beat down to using a remote that acts like a keyboard to get things to basically work.  The last thing I need to do is be able to assign a script to a button (or key on a keyboard).

Here is the remote I have.
[http://www.amazon.com/Windows-Control-Infrared-Receiver-Ultimate/dp/B00224ZDFY/ref=sr_1_1?ie=UTF8&qid=1291045314&sr=8-1](http://www.amazon.com/Windows-Control-Infrared-Receiver-Ultimate/dp/B00224ZDFY/ref=sr_1_1?ie=UTF8&qid=1291045314&sr=8-1)

Thanks!

---

### Post by kyphos on 2010-12-01
Will Xmacro help?
[http://ubuntuforums.org/showthread.php?t=299524](http://ubuntuforums.org/showthread.php?t=299524)

---

### Post by davidstoll on 2010-12-01
> **kyphos said:**
> Will Xmacro help?
[http://ubuntuforums.org/showthread.php?t=299524](http://ubuntuforums.org/showthread.php?t=299524)

That looks like it records a combination of keystrokes.  However, I want to be able to assign a program/script execution to a particular button/key.

---

### Post by tgm4883 on 2010-12-01
> **davidstoll said:**
> That looks like it records a combination of keystrokes.  However, I want to be able to assign a program/script execution to a particular button/key.

You want to use irexec

---

### Post by davidstoll on 2010-12-01
> **tgm4883 said:**
> You want to use irexec


This remote is not an IR remote.  I had to switch to one that acts like a keyboard because of the significant changes (bugs?) in 10.10...and I can't go back.

I forgot to mention that this is a continuation of another couple of different threads....
[http://ubuntuforums.org/showthread.php?t=1595018](http://ubuntuforums.org/showthread.php?t=1595018)
and
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651?comments=all](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651?comments=all)

I have previously used irexec, but with the introduction of 10.10, LIRC is so changed that it does not appear to be an option any longer.  To use irexec and assign scripts to buttons on an IR remote...
[http://ubuntuforums.org/showthread.php?t=1628976](http://ubuntuforums.org/showthread.php?t=1628976)

---

### Post by tgm4883 on 2010-12-01
> **davidstoll said:**
> This remote is not an IR remote.  I had to switch to one that acts like a keyboard because of the significant changes (bugs?) in 10.10...and I can't go back.

I forgot to mention that this is a continuation of another couple of different threads....
[http://ubuntuforums.org/showthread.php?t=1595018](http://ubuntuforums.org/showthread.php?t=1595018)
and
[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651?comments=all](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651?comments=all)

I have previously used irexec, but with the introduction of 10.10, LIRC is so changed that it does not appear to be an option any longer.  To use irexec and assign scripts to buttons on an IR remote...
[http://ubuntuforums.org/showthread.php?t=1628976](http://ubuntuforums.org/showthread.php?t=1628976)

Sorry about that, I missed the part where you said it was acting like a keyboard.

Gnome has a program called gnome-keybinding-properties, I'd check and see if xfce has something similar.

---

### Post by davidstoll on 2010-12-01
Found it.  In MythBuntu, click the program launcher button (start button ;), then click Settings and then click Keyboard.

Click the Add button, type in the path to a script, program or whatever and then it waits for you to click a button on a keyboard (or remote that acts like a keyboard).

;)

---

### Post by kyphos on 2010-12-03
@davidstoll,

Thanks for figuring this out. I will find it useful to customize my 'looks-like-a-keyboard' remote control.

A clarification for others who find this thread wanting to add keyboard commands to their Myth remotes. On my Mythbuntu system, the "Start" button on my keyboard has no effect. I found it necessary to click on **Applications**, then **Settings/Keyboard** to open the Keyboard control panel. Then click on **Application Shortcuts** to reveal the list of currently mapped keyboard shortcuts. And finally, **Add** to add a new command.

Clicking **Add** opens up a **Shortcut Command** window. First, you type in the name of the command or script that you want to map.  Then **OK**. A **Command Shortcut** window then opens.  It's not at all obvious that Ubuntu is now waiting for you to enter the desired keyboard shortcut (alt-F4, ctrl-delete, or whatever you want to map from your remote control). But it is.

---

### Post by davidstoll on 2010-12-06
Small problem/update:

The remote can now fully navigate the MythTV menu system, but when I play a video, the remote does not work.

I'm not sure how to train the remote at this point...with play/pause/FF/REW/etc...

:(

---

### Post by kyphos on 2010-12-06
@davidstoll,
My  remote-that-looks-like-a-USB-keyboard works just fine to drive the mythbox when playing a recorded TV show (play, pause, stop, rewind, etc).  Is that what you're trying to do? (or are you playing a video file from Media Library/Watch Videos...)?

---

### Post by davidstoll on 2010-12-07
> **kyphos said:**
> @davidstoll,
My  remote-that-looks-like-a-USB-keyboard works just fine to drive the mythbox when playing a recorded TV show (play, pause, stop, rewind, etc).  Is that what you're trying to do? (or are you playing a video file from Media Library/Watch Videos...)?

Playing a recorded video.  I don't use the library, so I'm not sure about that.

This is strange, I rebooted the pc and now play and pause work.  However, stop, fast forward, skip forward, back, info...still don't work.

---

### Post by kyphos on 2010-12-07
I was able to program my remote's buttons to work during playback of a recorded show using the various Actions in **Edit Keys**, under the "TV Playback" context.  It took some experimentation, but my remote has full control of play, pause, skip back, skip forward, rewind, ffwd, jump ahead, jump back, and commercial skip.

The **TV Playback** list is below **TV Editing** and **TV Frontend** in the list of Contexts. You might have to scroll down the list to see it.

---

### Post by davidstoll on 2010-12-07
> **kyphos said:**
> I was able to program my remote's buttons to work during playback of a recorded show using the various Actions in **Edit Keys**, under the "TV Playback" context.  It took some experimentation, but my remote has full control of play, pause, skip back, skip forward, rewind, ffwd, jump ahead, jump back, and commercial skip.

The **TV Playback** list is below **TV Editing** and **TV Frontend** in the list of Contexts. You might have to scroll down the list to see it.

I do see this, but a few are missing.  For instance...

I have no "stop" option.  The only thing close is "exitnoprompt", which is ok, but I like it to ask me if I want to save the position.  This function is more like the "exit" function that the little lonely left arrow button on most MCE remotes does.

I can't figure out which one is the normal fastforward/rewind.  i've tried everything that seemed logical.

---

### Post by kyphos on 2010-12-07
I don't have "stop" either. Doesn't seem to exist in mythland. The closest is Pause, which stops playback but freezes the image on the screen. If I want to save the position so I can return to it later, I just remember to hit the Select command (or spacebar on a keyboard) to bookmark the position, and then the 'exit' key. Playback resumes from the bookmarked location the next time you play that recording.  

I think I remember seeing some option or setting that would 'auto-bookmark' when exiting a show, but I don't know where it was. Maybe in the many pages of TV Playback settings.

---

### Post by davidstoll on 2010-12-07
> **kyphos said:**
> I don't have "stop" either. Doesn't seem to exist in mythland. The closest is Pause, which stops playback but freezes the image on the screen. If I want to save the position so I can return to it later, I just remember to hit the Select command (or spacebar on a keyboard) to bookmark the position, and then the 'exit' key. Playback resumes from the bookmarked location the next time you play that recording.  

I think I remember seeing some option or setting that would 'auto-bookmark' when exiting a show, but I don't know where it was. Maybe in the many pages of TV Playback settings.

That is strange because normally when you hit the stop button, it asks.  So, there is a function, but I don't see it in the list.

Also, I still don't see the normal fastforward and rewind functions.

---

### Post by kyphos on 2010-12-07
When a recorded show reaches the end, I get a pop-up asking if I want to delete it, save it to watch again, or delete and re-record. I've never seen a pop-up after I clicked 'back' asking me if I wanted to bookmark the current location.

I have:
-rewind: plays back the 'tape' in reverse at 3x or 10x, just like an old VCR
-f-forward: ditto, the other way
-skip back (typically by 5 seconds)
-skip forward (typically by 30 seconds)
-jump back (10 minutes)
-jump fwd (10 minutes)
-skip commercials (skip to end of commercial break, assuming that the CommFlagging process has run)

I found all of the keymaps for the above in the TV Playback key settings.

If you're using myth 0.24, you might have different options/features than what I have on 0.23.

---

### Post by davidstoll on 2010-12-08
> **kyphos said:**
> When a recorded show reaches the end, I get a pop-up asking if I want to delete it, save it to watch again, or delete and re-record. I've never seen a pop-up after I clicked 'back' asking me if I wanted to bookmark the current location.

I have:
-rewind: plays back the 'tape' in reverse at 3x or 10x, just like an old VCR
-f-forward: ditto, the other way
-skip back (typically by 5 seconds)
-skip forward (typically by 30 seconds)
-jump back (10 minutes)
-jump fwd (10 minutes)
-skip commercials (skip to end of commercial break, assuming that the CommFlagging process has run)

I found all of the keymaps for the above in the TV Playback key settings.

If you're using myth 0.24, you might have different options/features than what I have on 0.23.

I suppose it is possible there is a difference between .24 and .23 (You are lucky you are on .23...for several reasons, in this case LIRC is really messed up).  This is the first time things seem to have gone really bad on an update (and the changes seem to be intentional...so, it's not a "bug" that can be fixed).

However, in my TV settings, I have ffwdsticky, jumpffwd, seekffwd, seekrew, jumprew and rewsticky, but they don't seem to do anything.

---

### Post by davidstoll on 2010-12-11
Does anyone have any further suggestions on how to assign functions to those keys that seem to be missing...at least as far as I can tell?

---

