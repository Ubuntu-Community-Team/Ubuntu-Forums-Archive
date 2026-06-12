---
title: "Remote in mythtv makeses playback jerky"
date: 2008-12-17
forum: Mythbuntu
---

### Post by ederopaa on 2008-12-17
Using remote in mythtv to adjust volume raises CPU load and makes the videos jerky.

I have been having troubles with volume control inside myhtv with both an USB and serial port ir-receivers. When watching programs if I adjust the volume (and scroll the menu) the CPU load jumps up very high making the video jerky for a moment. I’ve tried using the remote in a shell with irw and it has no effect on the CPU load.

I have mythbuntu 8.10 on an AMD Athlon 64 X2 5200+, Asus M2N-SLI Deluxe AM2 motherboard, GeForce 7600 GS computer.

Any ideas on how to proceed?

Thanks!

---

### Post by JSkimming on 2008-12-17
We've discussed this before, on the MythTV Users mailing list, but we never got to the bottom of it (we'll, I've not really had the time to dig much deeper).

Here's the [discussion]("http://www.gossamer-threads.com/lists/mythtv/users/348760?page=last") to see if it helps you at all.

---

### Post by IntuitiveNipple on 2008-12-27
I've just analysed the call-path for LIRC events and discovered the cause of the delay. It is the result of *poking* gnome-screensaver for each key-press on the remote.

In summary, the difference between a regular key-press and a remote-control key-press handled by LIRC, is that LIRC creates a custom event. In the Myth front-end the method customEvent() handles the LIRC events. For ***every*** event the screensaver's count-down timer is reset. This involves the execution of an external system command each time:
```

gnome-screensaver-command --poke

```
The time it takes the system to run that command is what causes the delay. On some systems the delay will not be as noticeable as on others.

It should be possible to use the DBUS API instead to remove this delay. I'll put together a patch to test this out later, but first I need to check this isn't already being addressed upstream.

Here's the call-path analysis:
```

libs/libmyth/lirc.cpp::LircClient::Process(void)
 QApplication::postEvent(mainWindow, new LircKeycodeEvent(code, keycode, true));

 libs/libmythui/mythmainwindow.cpp::MythMainWindow::customEvent(QCustomEvent *ce)
 {
 #if defined(USE_LIRC) || defined(USING_APPLEREMOTE)
    else if (ce->type() == kLircKeycodeEventType && !d->ignore_lirc_keys) 
    {
        LircKeycodeEvent *lke = (LircKeycodeEvent *)ce;
        int keycode = lke->getKeycode();

        if (keycode) 
        {
            gContext->ResetScreensaver();
            if (gContext->GetScreenIsAsleep())
                return;
 // ...
 
            QKeyEvent key(lke->isKeyDown() ? QEvent::KeyPress :
                          QEvent::KeyRelease, k, ascii, mod, text);

            QObject *key_target = getTarget(key);
            if (!key_target)
                QApplication::sendEvent(this, &key);
            else
                QApplication::sendEvent(key_target, &key);

 }

 libs/libmythui/mythmainwindow.cpp::MythMainWindow::eventFilter(QObject *, QEvent *e)
 {
      switch (e->type())
    {
        case QEvent::KeyPress:
        {
            QKeyEvent *ke = dynamic_cast<QKeyEvent*>(e);
 }


libs/libmythui/mythmainwindow.cpp::MythMainWindow::customEvent(QCustomEvent *ce)
 libs/libmythui/mythmainwindow.cpp:1515: gContext->DoResetScreensaver();
 libs/libmyth/mythcontext.cpp::MythContext::DoResetScreensaver(void)
  libs/libmyth/mythcontext.cpp::d->screensaver->Reset();
  libs/libmyth/screensaver-x11.cpp::ScreenSaverX11::Reset(void)
   XResetScreenSaver(qt_xdisplay());
   if (d->IsScreenSaverRunning()) resetSlot();
    libs/libmyth/screensaver-x11.cpp::ScreenSaverX11::resetSlot()
     d->ResetScreenSaver();
     libs/libmyth/screensaver-x11.cpp::ScreenSaverX11Private::ResetScreenSaver()
	 {
	    if (m_xscreensaverRunning)
	        myth_system("xscreensaver-command -deactivate >&- 2>&- &");
	    else
	        myth_system("gnome-screensaver-command --poke >&- 2>&- &");
	}


```

---

### Post by IntuitiveNipple on 2008-12-27
I've opened a [launchpad bug report](https://bugs.edge.launchpad.net/mythbuntu/+bug/311772) to track this issue.

---

### Post by IntuitiveNipple on 2008-12-28
I've implemented DBus support via the QT3 library. Initial observations seem to show that mythtv isn't affected by the jitter, but that the gnome-screensaver process still eats a fair amount of CPU time when a series of remote key-presses occur quickly.

This CPU usage can exceed 30% which will indirectly slow down mythtv responses slightly, or cause a sudden rush of responses when gnome-screensaver CPU load returns to idle.

As there is no need to poke the screensaver for every key-press/event I'm going to try an alternative approach whereby mythtv will send a maximum of one poke per minute.

I'll make the current version available in my PPA as version ~ppa4i (which includes provisional native PulseAudio support too). It may be superseded by further package builds later as I experiment with the one-poke-per-minute variation.

---

### Post by IntuitiveNipple on 2008-12-28
My earlier searches upstream didn't find any details about this issue but earlier I searched for something related and discovered upstream [ticket #5893](http://svn.mythtv.org/trac/ticket/5893) that has a patch that has been accepted into the trunk and 0.21+fixes branch.

I've packaged this and put it in my PPA for testing as:

mythtv (0.21.0+fixes18722-0ubuntu2+5893~tj~ppa1i)

---

### Post by EasyRiderOnTheStorm on 2008-12-28
Please pardon me if I'm saying something stupid, but aren't we going the wrong way about this? This happens during video playback, right? Why is any screen saver active at all...? I mean, one of the first things one sees when for instance mplayer starts is something like:

```

xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[...]
GNOME screensaver enabled
Exiting... (Quit)

```
Wouldn't the purpose be better served by having the internal player do the same...?

---

### Post by IntuitiveNipple on 2008-12-29
From what I can understand of the code the reasoning is this:

If keyboard or mouse is used the system directly **pokes** the screen-saver, so mythtv doesn't need to deal with that scenario.

However, when a remote-control key-press occurs MYthTV generates a CustomEvent. CustomEvents are not just for remote-control key-presses but they usually indicate some form of interaction with the user.

Therefore the CustomEvent needs to **poke** the screen-saver to reset its idle timer.

If the user does all their interaction with the system via remote control then the system interaction with the screen-saver will be minimal.

Myth might not be playing video for long periods especially where used in a Home Theatre configuration; therefore it would not be a good idea to disable the screen-saver completely.

mplayer can assume that when loaded the user intends to watch video immediately.

The accepted upstream patch addresses the issue by only sending one poke every 30-seconds from the CustomEvent logic. My own patch set the minimum to 1 minute (the same as the internal mythtv timer when playback is active).

---

### Post by ederopaa on 2008-12-29
Great IntuitiveNipple that you found a reason for the behavior!

I found this work around for the time being to disable the screensaver:

[http://ubuntuforums.org/showpost.php?p=1630034&postcount=5](http://ubuntuforums.org/showpost.php?p=1630034&postcount=5)

---

