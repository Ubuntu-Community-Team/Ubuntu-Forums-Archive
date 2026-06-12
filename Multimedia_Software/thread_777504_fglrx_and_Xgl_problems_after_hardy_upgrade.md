---
title: "fglrx and Xgl problems after hardy upgrade"
date: 2008-05-01
forum: Multimedia Software
---

### Post by mstreibe on 2008-05-01
Hi all,

before the upgrade I ran gutsy for a long time and everything worked fine, 3D acceleration, desktop effects etc.

Since the upgrade to hardy I have various problems:

1) fglrx
In general the driver works with full 3D acceleration, but the display freezes when I log out of my session. First, the display becomes black, then, a second or 2 later, the mouse pointer disappears, and then the only way out is to push the power button on my laptop to initiate a shutdown.

Or when doing

  /etc/init.d/kdm stop

it says kdm didn't respond to the signal. Then the Xserver consumes high cpu load and cannot be killed, not even with SIGKILL, and kdm cannot be restarted. Again, the only way out is to reboot.

A long time ago (ubuntu 6.x or so) I had similar problems, and at that time it was the fault of fglrx, and an upgrade that became available after some time fixed it.

Hardy ships with fglrx 8.473. On the ATI website there is 8.476 available, and the release notes of the latest driver mention a problem like this, so I followed the ATI installation instructions and also the ones at

[http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts](http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts)

to install that version.

The installation seemed to work, but afterwards the ATI catalyst control center still said it was version 8.473, and the logout problem remained.

I also tried envyng which didn't give any errors, but the driver version is still 8.473 and the logout display freeze is still there.

Does anyone have the same problem? Or even better a solution to this?

2)
Xgl/compiz doesn't work anymore.

With xserver-xgl installed, my kde session doesn't start. .xsession-errors shows

Xsession: X session started for testuser at Do 1. Mai 18:02:30 CEST 2008
Checking for nVidia: not present. 
Starting Xgl with options:  -accel xv:pbuffer -accel glx:pbuffer -nolisten tcp -fullscreen -br 
Waiting 10 more seconds for Xgl to start...
xmodmap:  unable to open display ':1'
Segmentation fault
^^^^^^^^^^^^^^^^^^
rm: Entfernen von &#8222;/tmp/.X11-unix/X1&#8220; nicht möglich: No such file or directory
xset:  unable to open display ":1"
xset:  unable to open display ":1"
xsetroot:  unable to open display ':1'
startkde: Starting up...
xprop:  unable to open display ':1'
   :

Looks like Xgl crashed. See the marked line. Interestingly, I can start Xgl out of an xterm during my session, and also a compiz and various X clients within it, and there it works. But it doesn't when starting the Xsession.

Without Xgl, compiz doesn't work because I disabled the composite extension in xorg.conf. When enabling it, compiz starts without Xgl, but the display is terribly slow and unusable, and I think I have read somewhere that fglrx doesn't support the composite extension.

Logging on as a different (virgin) user, I end up with a completely white screen plus mouse pointer. Apparently compiz started despite Xgl not running. I need to run "kwin --replace" from the ascii console to get the KDE desktop back.

Can anyone help out?

---

### Post by mstreibe on 2008-05-02
BTW, I have an HP nc6400 notebook with ATI Radeon Mobility X1300 graphics.

---

### Post by jocko on 2008-05-02
With the version of fglrx in hardy you do NOT need Xgl. The driver supports aiglx and composite. Just make sure you have NOT disabled aiglx or composite in xorg.conf and uninstall xserver-xgl.

---

### Post by mstreibe on 2008-05-02
Indeed, Xgl is not needed. I stumbled over this post:

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

Setting up xorg.conf accordingly made compiz work, although it is slower than under gutsy with Xgl. And fgl_glxgears and other OpenGL apps e.g. torcs shows a lot of flickering, and no window frame. The flickering makes these apps unusable.

Should I change any of the driver options given in the above post:

        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Option          "XaaNoOffscreenPixmaps" "true"
#       Option          "AddARGBGLXVisuals"     "true"
#       Option          "AllowGLXWithComposite" "true"
#       Option          "EnablePageFlip"        "true"
#       Option          "AccelMethod"           "EXA"
#       Option          "MigrationHeuristic"    "greedy"
        Option          "DRI"                   "true"
        Option          "TexturedVideo"         "on"
        Option          "UseFastTLS"            "0"
        Option          "BlockSignalsOnLock"    "on"
        Option          "KernelModuleParm"      "locked-userpages=0"
        Option          "ForceGenericCPU"       "off"

The ones I commented out were mentioned in /var/log/xorg.0.log as not being used.

And also, the display freeze on logout is still there.

---

### Post by mstreibe on 2008-05-14
I've disabled the composite extension and AIGLX now, although I really like many of compiz's features. For me it made graphics output slow, with flickering etc.

But at least it seems the latest fglrx update for hardy solved the display freeze on logout.

---

