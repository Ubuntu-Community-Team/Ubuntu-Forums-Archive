---
title: "Amarok global hotkeys not working"
date: 2007-03-30
forum: Multimedia &amp; Video
---

### Post by gannina on 2007-03-30
Hi, I just recently started using Amarok music player, and it is nice, but the global hot keys don't seem to work very well in Ubuntu. If I change the global hot keys they only seem to work if Amarok has focus... which kind of defeats the purpose of hot keys. Strangely, the volume up and down hot keys I selected work, but those are the only ones. I also tried setting the keyboard shortcuts in System -> Preferences, but I could only get the key to launch Amarok to work, which required some strange command to change a symlink... 

Has anyone had any success at setting global hot keys for amarok in ubuntu?

---

### Post by ronocdh on 2007-03-31
I've always used the default global hotkeys and they've never given me trouble. (This is in Ubuntu, too.) It might sound odd, but have you tried a different keyboard? I had an MS USB one whose F-keys just gave me trouble. Sometimes if I were in a terminal they would respond, otherwise they were useless. Turns out even in XP they weren't on; the stupid drivers that shipped on CD with the keyboard were needed. Yuck.

So try hooking up an old PS/2 keyboard, or just another one, if that's what you're using, and see whether that helps.

---

### Post by Shmifty on 2007-03-31
It is possible the keys you assigned have some hidden task elsewhere and are conflicting that other program. I suggest sticking to the defaults as they are fairly easy to remember.

---

### Post by gannina on 2007-03-31
Sweet! I just got it working. I was just farting around in the keyboard setting, and I noticed that U.S english was unchecked under the layout tab, so I checked it. I then went back to Amarok and defaulted all the keys back to their default values, and hit ok. Then I went back into the global shortcut keys in Amarok and changed them to the ones I wanted. I also noticed that the shortcut key value changed. For example the key for number pad 5 use to be Kp_5, it changed to XF86AudioPlay

Summary of what I did:

1. System -> Preferences -> Keyboard
2. Click on layout tab
3. Make sure U.S English box is checked
4. Load up Amarok and go to settings -> Configure global Shortcuts
5. For the keys that are NOT working, set them back to their default value, and hit OK
6. Go back into "Configure global shortcuts in Amarok" and change the keys to whatever you want

These steps worked for me, I'm hoping they work for other people as well.

---

### Post by rainwalker on 2007-04-01
That happened to me when I first started using Amarok; I could only use the play/pause, stop, next, and previous multimedia buttons on my laptop when the Amarok window was focused. 
Installing KeyTouch worked for me:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=keytouch&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=keytouch&searchon=name&subword=1&version=all&release=all)

---

### Post by pwrinxs on 2007-04-21
> **gannina said:**
> Sweet! I just got it working. I was just farting around in the keyboard setting, and I noticed that U.S english was unchecked under the layout tab, so I checked it. I then went back to Amarok and defaulted all the keys back to their default values, and hit ok. Then I went back into the global shortcut keys in Amarok and changed them to the ones I wanted. I also noticed that the shortcut key value changed. For example the key for number pad 5 use to be Kp_5, it changed to XF86AudioPlay

Summary of what I did:

1. System -> Preferences -> Keyboard
2. Click on layout tab
3. Make sure U.S English box is checked
4. Load up Amarok and go to settings -> Configure global Shortcuts
5. For the keys that are NOT working, set them back to their default value, and hit OK
6. Go back into "Configure global shortcuts in Amarok" and change the keys to whatever you want

These steps worked for me, I'm hoping they work for other people as well.

I followed these directions but I still can't get this to work. The keys are detected but seem to have no effect when pressed. Anyone have any ideas?

---

### Post by pwrinxs on 2007-04-21
> **pwrinxs said:**
> I followed these directions but I still can't get this to work. The keys are detected but seem to have no effect when pressed. Anyone have any ideas?

Wow I just figured it out. I'll post it in case it helps someone in the future:

So I found that there was probably a conflict with the assignments. In System --> Pref --> Keyboard Shortcuts, I had to scroll down to sound and click on the play/pause, previous song, next song, and stop and then hit DELETE on the keyboard to remove and disable the shortcuts assigned in Keyboard Shortcuts. Then I followed the instructions given above by gannina. I had to restart Amarok once or twice in between but it now works.

---

### Post by bignickel on 2007-04-22
These instructions didn't work for me on Feisty.  It worked fine in Edgy, but maybe something changed with the KDE key mapping?  Maybe I don't understand these things properly, but I don't see how changing the Gnome key mapping would have any effect on amarok.

I'm running a Dell Inspiron 8600, and the multimedia keys work fine in Gnome, but they're not recognized at all in amarok.

---

### Post by bignickel on 2007-04-22
I found a solution that solves the problem.  It's a bit of a workaround though.  I put the details in [another thread]("http://ubuntuforums.org/showthread.php?p=2507060#post2507060").

---

### Post by hagar_am on 2007-04-23
Had that problem. Have just fixed it. Remove all shortcuts that you are going to use in Amarok ( for me play/pause & stop) from System->Preferences->Key Shortcuts. Open Amarok set global keys as default press ok then quit amarok(ctrl+q). Open again and set you global shortcuts and enjoy :D.

---

### Post by finer recliner on 2007-05-23
> **pwrinxs said:**
> Wow I just figured it out. I'll post it in case it helps someone in the future:

So I found that there was probably a conflict with the assignments. In System --> Pref --> Keyboard Shortcuts, I had to scroll down to sound and click on the play/pause, previous song, next song, and stop and then hit DELETE on the keyboard to remove and disable the shortcuts assigned in Keyboard Shortcuts. Then I followed the instructions given above by gannina. I had to restart Amarok once or twice in between but it now works.

this worked for me.
dell inspiron 6000 feisty


thanks guys

---

### Post by BrowneR on 2007-06-22
I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

---

### Post by AstarothCY on 2007-07-31
Excellent fix! Someone should compile this stuff into a HowTo, it was pretty difficult to piece everything together from different threads.

---

### Post by aysiu on 2007-07-31
> **BrowneR said:**
> I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)
or install it directly from the Amarok script manager - its called "gnome multimedia keys".

this should be the fastest way to get it working.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.
There's a bug filed on this:
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/94272](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/94272)

Could your script be a patch the developers could use to fix it?

---

### Post by BrowneR on 2007-08-01
> **aysiu said:**
> There's a bug filed on this:
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/94272](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/94272)

Could your script be a patch the developers could use to fix it?

No im afraid not. I haven't modified the Amarok code in any way to fix the issue and so my script is just a work around. Besides I dont think the Amarok developers are too fussed by this issue which is totally confined to gnome users. What could be done would be to include my script by default in the ubuntu amarok package so that all users of ubuntu would have a copy. I'm not sure how to go about that though - i have tried posting on the launchpad bug page (that link you gave was a duplicate of it and i have marked it as such).

---

### Post by gigabz666 on 2007-10-24
I'm having a similar problem. I'm using a Dell Inspiron 9400 which has multimedia keys on the front. Now all of them work in Amarok under global shortcuts apart from play. The play and pause button are the same and so I figured I could assign this to the play/pause option. However, when I press it, nothing happens.

If Amarok is currently playing and then I press that button, it does pause, however it cannot play again. I'm not really sure what to do to sort it out. I checked the shortcuts being used in KDE and can't see anything else using it (XF86AudioPlay).

Currently in the shortcuts XF86AudioPause is assigned to pause and XF86AudioPlay is assigned to play. It's really weird and I'm not sure what to do.

Thanks

---

### Post by Mithrilhall on 2007-10-26
I'm having a similar problem. What's actually happening is when I push my 'volume up', 'volume down' and 'mute' buttons on my keyboard (this is a desktop not a laptop) it's actually changing the volume for the headphones in kmix. This appears to be a system wide problem. It changes the headphone's volume regardless if Amarok is open or not.

---

### Post by Arathon on 2008-04-17
> **gannina said:**
> Sweet! I just got it working. I was just farting around in the keyboard setting, and I noticed that U.S english was unchecked under the layout tab, so I checked it. I then went back to Amarok and defaulted all the keys back to their default values, and hit ok. Then I went back into the global shortcut keys in Amarok and changed them to the ones I wanted. I also noticed that the shortcut key value changed. For example the key for number pad 5 use to be Kp_5, it changed to XF86AudioPlay

Summary of what I did:

1. System -> Preferences -> Keyboard
2. Click on layout tab
3. Make sure U.S English box is checked
4. Load up Amarok and go to settings -> Configure global Shortcuts
5. For the keys that are NOT working, set them back to their default value, and hit OK
6. Go back into "Configure global shortcuts in Amarok" and change the keys to whatever you want

These steps worked for me, I'm hoping they work for other people as well.

Just wanted to say that this worked for me - principally, going into Keyboard and making sure the (radio button, in my case) is actually selected.  

This is in 8.04, for the record.

---

### Post by wired00 on 2008-04-17
> Sweet! I just got it working. I was just farting around in the keyboard setting, and I noticed that U.S english was unchecked under the layout tab, so I checked it. I then went back to Amarok and defaulted all the keys back to their default values, and hit ok. Then I went back into the global shortcut keys in Amarok and changed them to the ones I wanted. I also noticed that the shortcut key value changed. For example the key for number pad 5 use to be Kp_5, it changed to XF86AudioPlay

Summary of what I did:

1. System -> Preferences -> Keyboard
2. Click on layout tab
3. Make sure U.S English box is checked
4. Load up Amarok and go to settings -> Configure global Shortcuts
5. For the keys that are NOT working, set them back to their default value, and hit OK
6. Go back into "Configure global shortcuts in Amarok" and change the keys to whatever you want

worked for me using 8.04 with toshiba satellite A200. 

Messed around for 15 minutes but basically ...

1) went into System > Keyboard - Layouts tab. Checked "USA" = Default.
2) went into System > Keyboard Shortcuts. Disabled the following:
[LIST=1]
[*]Play (or play/pause)
[*]Pause playback
[*]Stop playback
[*]Previous track
[*]Next track
[/LIST]

*Do not re-assign them to your keys!

3) Load amarok. Settings > Configure Global Shortcuts...
4) change Play/Pause, Next Track, Stop and Previous Track back to Default by clicking each one then clicking "Default".

click OK then close amarok and reload. go back into Settings > Configure Global Shortcuts and they should all be assigned your buttons... ie, mine had gone back to play/pause = "XF86AudioPlay".

If it didn't auto assign then you could try just clicking each one to assign a new key then pressing your keyboard buttons. either way , you want it to say "XF86AUdioPlay" or something like this in the Play/pause, Next, Previous spots.

hope that helps?

---

### Post by Vajk on 2008-04-19
wired00 -> I've done your step by step guide but still only works if Amarok is focused. I'm using Ubuntu Gutsy now on an Inspiron 9300. The keys work working OK with Kubuntu and Amarok.

---

### Post by thebigham on 2008-04-21
Took me a while but i finally found the plugin for it. 

[http://www.kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://www.kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)

Just load the plugin in the amarok script manager, restart amarok, and click run on the script manager.

---

### Post by DarwinsTheory on 2008-07-17
> **gannina said:**
> 

Summary of what I did:

1. System -> Preferences -> Keyboard
2. Click on layout tab
3. Make sure U.S English box is checked
4. Load up Amarok and go to settings -> Configure global Shortcuts
5. For the keys that are NOT working, set them back to their default value, and hit OK
6. Go back into "Configure global shortcuts in Amarok" and change the keys to whatever you want

These steps worked for me, I'm hoping they work for other people as well.

Fantastic... this worked for me as well.   Lucky I found your post, no mucking around with other programs or scripts etc.  WELL DONE...!!!

Matt

---

### Post by MxGB on 2008-07-20
> **BrowneR said:**
> I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in
system-->preferences-->keyboard shortcuts

done.
Nice one for this script, works perfectly on my 8.04 desktop with an MS multimedia keyboard.

---

