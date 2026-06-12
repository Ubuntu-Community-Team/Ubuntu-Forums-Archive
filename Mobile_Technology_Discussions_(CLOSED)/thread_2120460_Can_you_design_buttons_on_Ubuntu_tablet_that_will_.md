---
title: "Can you design buttons on Ubuntu tablet that will be a virtual keyboard for desktop?"
date: 2013-02-26
forum: Mobile Technology Discussions (CLOSED)
---

### Post by bboyjkang on 2013-02-26
**Running out of buttons**

  After using Autohotkey for remapping, I soon didn't have enough  keyboard buttons to attach macros or scripts to them, so I'd have to  make new scripts that use the same button. After more scripts, it can be  easy to forget which button does what.

  **Customizable, expensive, physical keyboards**

  There are companies that provide custom overlays for their own  massive, custom keyboards, such as The Enterpad, which is $300. There's  the E-inkey Keyboard concept. The Optimus Popularis keyboard, which has  customizable OLED screens, is $1000! 

  **Tablet as a customizable, virtual keyboard**

  With a touchscreen, you could pretty much design whatever virtual  keyboard you want, have multiple virtual keyboard layers, and design the  buttons to look however you want. Could you use an Ubuntu tablet as a  virtual keyboard for your desktop? 

  **VNC and remote control of desktop**

  There's remote control of Ubuntu with android-vnc-viewer ([http://www.youtube.com/watch?v=sTKX6QMBgck#t=0m30s](http://www.youtube.com/watch?v=sTKX6QMBgck#t=0m30s)),  but you're moving a mouse cursor with your fingers, and the interaction  is supposedly not as smooth. The newly announced Ubuntu for mobile  could make controlling an Ubuntu desktop more seamless. 

  **Design your own buttons**

  Aside from the scripting that could be behind the buttons (you would probably use something like AutoKey ([http://code.google.com/p/autokey/](http://code.google.com/p/autokey/)),  a desktop automation utility for Linux), I'm not sure what methods and  tools that are out there to design your own buttons. Does anyone know  anything that can help create your own keyboard and buttons?

  Thanks.

---

### Post by bboyjkang on 2013-03-29
This is not an answer for designing  custom-looking keyboard buttons, but if you're content with attaching  macros in scripts to the typical, regular buttons of a hard keyboard, I  asked a question on superuser.com: [How would you turn a tablet into a keyboard + easy-to-reach touchscreen (mirror the desktop) (not a touchpad) for a desktop PC?]("http://superuser.com/questions/564421/how-would-you-turn-a-tablet-into-a-keyboard-easy-to-reach-touchscreen-mirror"). You can do the following:

  **android-vnc-viewer to mirror the desktop PC screen, and control the desktop**

  I had another question on [android.stackexchange.com]("http://android.stackexchange.com/"):  (In using a VNC to control a computer, is it possible to have the  cursor go to where you touch? -  android[dot]stackexchange[dot]com/questions/34668/in-using-a-vnc-to-control-a-computer-is-it-possible-to-have-the-cursor-go-to-wh)
  In the question, I included a video: Remote control of Ubuntu with android-vnc-viewer - [www.youtube.com/watch?v=sTKX6QMBgck#t=0m30s]("http://www.youtube.com/watch?v=sTKX6QMBgck#t=0m30s")
  android-vnc-viewer[INDENT]   “See and control your computer's desktop from your phone, from   anywhere. androidVNC is the Open Source (GPL) remote desktop program   for Android devices. Connects to most VNC servers: incl TightVNC,   RealVNC on Win and Linux, x11vnc, and Apple Remote Desktop on OS/X.”.


 [/INDENT]
In the video, I don't know the input mode that is being demonstrated  at 0:30, but it looks like the mouse cursor goes to where he touches.
  [http://code.google.com/p/android-vnc-viewer/](http://code.google.com/p/android-vnc-viewer/)

  I'm guessing that the input mode in the video was either:
[INDENT]   Touch Mouse Pan and Zoom
  This is the default input mode and is   designed to work like the Android browser. You can both pan the   display and control the mouse using the touchscreen and gestures. You   pan by dragging or flicking on the touchscreen; you click the mouse by   tapping on it. You right-click by double-tapping (or by holding down   the camera button while tapping). You drag the mouse by doing a long   press on the display, and then dragging. In this mode the trackball or   DPad (if your phone has one) can also be used to control the mouse;   this may give you finer control. You can zoom the screen size with the   +/- buttons, or, if your device supports multi-touch and has Android 2.0+, you can pinch to zoom out and spread to zoom in.
 [/INDENT]
or:[INDENT]   Mouse Control Mode
  In this mode, use the touchscreen to control the   mouse. Touching the screen generates a mouse click at that point;   dragging on the screen creates a mouse drag. Keyboard events are sent   as normal. The trackball is used to send arrow-key events to the VNC   server. Pressing the trackball toggles between Mouse Pointer Control   and Desktop Panning modes.


 [/INDENT]
Port forwarding
[INDENT]   If the PC you're connecting to accesses the internet through a router,   this will be the WAN address assigned to the router by your ISP;   you'll also need to forward the VNC port (5900) from the router to   your PC (exactly how you do this depends on the details of your   router, so I can't give more explicit instructions here).


 [/INDENT]
**Hacker's Keyboard - use a full soft keyboard on Android**

  From what I've read, the stock android keyboard doesn't have buttons such as Ctrl, Alt, Esc, arrow keys, Home, End, and Delete.
  You can use the free, open source, app call Hacker's Keyboard to gain access to the buttons of a full keyboard:[INDENT]   “Are you missing the key layout you're used to from your computer?   This keyboard has separate number keys, punctuation in the usual   places, and arrow keys. It is based on the AOSP Gingerbread soft   keyboard, so it supports multitouch for the modifier keys.
      This keyboard is especially useful if you use ConnectBot for SSH   access. It provides working Tab/Ctrl/Esc keys, and the arrow keys are   essential for devices such as the Xoom tablet or Nexus S that don't   have a trackball or D-Pad.”
 [/INDENT]
[http://code](http://code)[dot]google[dot]com/p/hackerskeyboard/

  **A patch that allows android-vnc-viewer to recognize all the keys of Hacker's Keyboard**

  In “Frequently Asked Questions” of Hacker's Keyboard, there's a  section called “Android VNC Viewer doesn't recognize the extra keys”.
  It directs you to an issue called “Issue 238:   Support additional  keys, fix modifier handling”  (code.google.com/p/android-vnc-viewer/issues/detail?id=238). The patch  there will make it so that Android VNC Viewer recognizes buttons of a  full keyboard.

---

### Post by coffeecat on 2013-04-09
Note of action.

@bboyjkang, in case you were responding to it, I've removed a spam post that preceded your second post in this thread. It was not obvious spam - it purported to post a relevant reply but spammed a company by means of the username.

---

