---
title: "Vlc won't open, problems with qt4"
date: 2011-04-18
forum: Multimedia Software
---

### Post by kennedn on 2011-04-18
Whenever I try to open vlc it wont even start. When i try to open it in Terminal I get this output:

```
kennedn@MUSHROOMS:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8bfc914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x8c94304] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x8c94304] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x8bfc914] main libvlc error: interface "default" initialization failed

```and when i tried a command i found on a forum with a similar problem 'vlc -v --reset-config --reset-plugins-cache -l | grep wx' I got this output:

```
[0x8e65914] main libvlc warning: cannot load module `/usr/lib/vlc/plugins/gui/libqt4_plugin.so' (/usr/lib/vlc/plugins/gui/libqt4_plugin.so: undefined symbol: _ZN9QListData6detachEi)
```I know its something to do with qt4 but I'm not sure how to go about resolving it, any help would be much appreciated

---

### Post by varunendra on 2011-04-19
Try "completely remove" vlc from synaptic. Then-

```
sudo apt-get clean
```
(will remove all downloaded packages from download cache)

```
sudo apt-get autoremove
```
(will remove modules that are no longer needed)

then reinstall VLC from synaptic. Should fix dependencies.

---

### Post by kennedn on 2011-04-19
I tried your advice but the problem still remains, i don't think it is a problem with vlc itself but qt4, but maybe I'm wrong.

Has anyone got any other suggestions??

---

### Post by varunendra on 2011-04-19
> **kennedn said:**
> i don't think it is a problem with vlc itself but qt4
Seems weird to me. The modules "libqtcore" and  "libqtgui4" are parts of vlc dependencies, so they should have been reinstalled with vlc if it was completely removed and the suggested two commands were run afterwards.

One more possibility maybe that libqtgui4 is perhaps used by some other application as well such as compiz effects or something and as such it is not removed by apt-get autoremove while the existing one might be broken or incompatible with vlc. In that case completely removing and reinstalling it (only libqtgui4) should work, but that's a long shot.

The only thing you can check easily is to see after removing vlc (completely) and performing apt-get autoremove, whether or not libqtgui4 is removed. If it still is there, then you may wish to remove it manually.

Also, while reinstalling vlc, have you checked what dependencies are going to install along with it? If libqtgui4 is not in that list, then it certainly is being used by some other app, hence not autoremoved, and at the same time - is broken or incompatible.

---

### Post by mc4man on 2011-04-19
Have you installed some app recently that could have installed some qt4 libs, whether from a ppa or else wise (maya from Autodesk does this sometimes

What's this show
```
ldconfig -p |grep libQt
```
or more specifically
ldconfig -p |grep libQtC or ldconfig -p |grep libQtG

---

### Post by kennedn on 2011-04-19
Thank you very much mc4man I found out that it was Google Earth that was causing the problems which i had recently installed but rarely use, as soon as i removed it vlc started working again :P thank you too varunendra for your help :)

---

### Post by varunendra on 2011-04-19
Ah!

Thanx to you for the good news early in the morning.
(well.. I guess 8:58 isn't that early though..! :) )

How about certifying this to be a good one by marking it as [solved]? (pl refer to my sign.. :) )

---

### Post by apurvtwr on 2011-05-14
Hi,
I have a similar problem like yours where VLC is not opening due to qt4. However, in my case, I want to keep both the applications.
What do you suggest for that?
Following are the logs:

VLC media player 1.1.4 The Luggage (revision exported)
[0x9445914] main libvlc warning: cannot load module `/usr/lib/vlc/plugins/gui/libqt4_plugin.so' (/usr/lib/vlc/plugins/gui/libqt4_plugin.so: undefined symbol: _ZN9QListData6detachEi)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x94f0534] main interface error: no suitable interface module
[0x9445914] main libvlc error: interface "default" initialization failed

---

### Post by varunendra on 2011-05-14
> **apurvtwr said:**
> Hi,
I have a similar problem like yours where VLC is not opening due to qt4. However, in my case, I want to keep both the applications.
What do you suggest for that?
Following are the logs:

VLC media player 1.1.4 The Luggage (revision exported)
[0x9445914] main libvlc warning: cannot load module `/usr/lib/vlc/plugins/gui/libqt4_plugin.so' (/usr/lib/vlc/plugins/gui/libqt4_plugin.so: undefined symbol: _ZN9QListData6detachEi)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x94f0534] main interface error: no suitable interface module
[0x9445914] main libvlc error: interface "default" initialization failed

Hmm.. I think I posted a reply in [that thread]("http://ubuntuforums.org/showthread.php?t=1757173") of yours almost 15hrs ago. Did you check it? And by the way, posting here may not bring you much help as the potential helpers would not consider looking at it since it is already marked as [SOLVED].

So I suggest to post in your own ongoing thread instead. And also include the above qt4 error in your new post (or edit the first one) since you didn't mention it before.

---

