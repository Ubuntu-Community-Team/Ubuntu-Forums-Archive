---
title: "x11vnc crashes xorg on key press"
date: 2008-12-29
forum: Mythbuntu
---

### Post by maxim99 on 2008-12-29
I'm using the new Jaunty Alpha2 mythbuntu and am having an issue with x11vnc.

I have x11vnc running on the system and am able to log in, view the desktop, click around and interact with it using the mouse.

When I press a key on the keyboard, the X server crashes. Here is the log for that:```
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4ef056]
1: /usr/bin/X(xf86SigHandler+0x41) [0x483a51]
2: /lib/libc.so.6 [0x7f607b5cc030]
3: /usr/bin/X(CopyKeyClass+0x38) [0x53d118]
4: /usr/bin/X(mieqProcessInputEvents+0x2d3) [0x4cfa93]
5: /usr/bin/X(ProcessInputEvents+0x9) [0x484669]
6: /usr/bin/X(Dispatch+0x29e) [0x44d7be]
7: /usr/bin/X(main+0x3bd) [0x4332bd]
8: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f607b5b7586]
9: /usr/bin/X [0x432749]
Saw signal 11.  Server aborting.
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Ideazon Zboard Gaming Keyboard: Close
(II) UnloadModule: "evdev"
(II) Ideazon Zboard Gaming Keyboard: Close
(II) UnloadModule: "evdev"
(II) Razer Razer Diamonback Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
 ddxSigGiveUp: Closing log
```

x11vnc log also has something:```

caught XIO error:
29/12/2008 09:07:48 deleted 45 tile_row polling images.
```

I have a feeling that it's something to do with the new X server, and x11vnc not being up to date. Anyone else in the same boat as me?

On a side note I have yet to have a successful configuration using the Myth Control Center to setup VNC with the password. It has never allowed me to log in. Not sure what's up with that.

---

### Post by maxim99 on 2008-12-29
Using a newly compiled x11vnc (0.9.7) it still crashes.

---

### Post by maxim99 on 2008-12-29
I have tried running X using the command line "X" which started a server no problems. I then ran x11vnc with the command "x11vnc" and that attached to the server no problems. The same thing resulted. I am at a loss as to what to do.

---

### Post by krunge on 2008-12-29
> **maxim99 said:**
> I'm using the new Jaunty Alpha2 mythbuntu and am having an issue with x11vnc.

I have x11vnc running on the system and am able to log in, view the desktop, click around and interact with it using the mouse.

When I press a key on the keyboard, the X server crashes. Here is the log for that:
...

I have a feeling that it's something to do with the new X server, and x11vnc not being up to date. Anyone else in the same boat as me?


x11vnc is simply an X client app (i.e. a fancy, continous screenshoting program), and so it should **never** cause a crash of the X server.

So it is likely a fairly serious X server bug or X server misconfiguration.

Do you have weird hardware and/or device driver configured?

I'm not sure it is related but have a look at this thread:

[http://ubuntuforums.org/showpost.php?p=6132263&postcount=13](http://ubuntuforums.org/showpost.php?p=6132263&postcount=13)

---

### Post by maxim99 on 2008-12-29
Nothing weird as far as I know. I just installed mythbuntu, did myth control center setup to install x11vnc. The driver in use is "intel" from the intellinuxgraphics folks. The latest intel driver was the whole reason for using the alpha. I have no monitor on this machine and with the old driver X would exit because of no connected monitors. Now x11vnc isn't working out with this new software. :/

Thank you for your reply.

I did indeed try with noxfixes earlier and it seems it is something else cause the segmentation fault, as it still happens with this option in use.

A peculiar thing about this is that the very first time I ran x11vnc is it worked. I was able to use the keyboard without issue. I opened up a terminal and typed some lines.```
maxim@mythbuntu:~$ history
    1  sudo su -
    2  type type type
    3  nice
    4  n-n-n-nice!
```

These were typed in a terminal window, in X, through a VNC client.

---

### Post by krunge on 2008-12-29
> **maxim99 said:**
> 
A peculiar thing about this is that the very first time I ran x11vnc is it worked. I was able to use the keyboard without issue. I opened up a terminal and typed some lines.

First time since a reboot or first time since the OS is installed?

I am wondering if this patch 154_force-copykeyclass-for-key-events.patch
is what broke you:

[http://lists.debian.org/debian-x/2008/12/msg00198.html](http://lists.debian.org/debian-x/2008/12/msg00198.html)

You may want to submit a formal bug with all of your details.  That patch may be broken for XTEST insertion of keystrokes (that is how x11vnc inserts keystrokes.)  So be sure to mention XTEST keystroke insertion.  I will send a quick email to the patch submitter, but I don't have all of the details you have about your setup, etc.

---

### Post by maxim99 on 2008-12-29
Man, i'm glad you know what you're talking about. I'll try and do a clean install and such to try and make sure the issue is reproducible. I'll try and get some hardware specs too. I'll wipe it clean and start over again and see if I can isolate what in the sequence breaks it.

Thank you for your input on this matter. I didn't know where to start with this issue, I've never had the X server crash like that before. Especially over just a keyboard.

---

### Post by maxim99 on 2008-12-30
I opened a bug thing for x11vnc on ubuntu's bug thing yesterday before I received your advice and someone has posted a reply stating that they are also experiencing the same issue.

Yay, i'm not alone.

[https://bugs.launchpad.net/ubuntu/+bug/312168](https://bugs.launchpad.net/ubuntu/+bug/312168)

---

### Post by krunge on 2008-12-30
> **maxim99 said:**
> I opened a bug thing for x11vnc on ubuntu's bug thing yesterday before I received your advice and someone has posted a reply stating that they are also experiencing the same issue.


Try compiling and running this test program on the machine:
```

/*
 * xkeytest.c: use XTEST extension to inject a few keystrokes. 
 * compile:    cc -o xkeytest xkeytest.c -L /usr/X11R6/lib -lX11 -lXtst
 * run:        ./xkeytest
 */

#include <stdio.h>
#include <unistd.h>
#include <X11/Xlib.h>
#include <X11/extensions/XTest.h>
#include <X11/keysym.h>

int main(void) {
        KeySym syms[16];
        Display *dpy = XOpenDisplay(NULL);
        int i, n = 0;

        if (dpy == NULL) {
                fprintf(stderr, "XOpenDisplay failed.\n");
                return 1;
        }

        fprintf(stderr, "In 2 secs we inject 'hi mom' ...\n");
        sleep(2);

        syms[n++] = XK_h;
        syms[n++] = XK_i;
        syms[n++] = XK_space;
        syms[n++] = XK_m;
        syms[n++] = XK_o;
        syms[n++] = XK_m;
        syms[n++] = XK_Return;

        for (i = 0; i < n; i++) {
                KeyCode key = XKeysymToKeycode(dpy, syms[i]);
                XTestFakeKeyEvent(dpy, key, True,  CurrentTime); 
                XTestFakeKeyEvent(dpy, key, False, CurrentTime);
        }
        XCloseDisplay(dpy);
        return 0;
}

```

It will try to inject the keystrokes 'hi mom' exactly the same way x11vnc does.

If this crashes Xorg, it is pretty clear the problem is in the X server's XTEST support.

---

### Post by maxim99 on 2008-12-30
Should this be done from within the X server? Can it be done from a tty instead? Again, i'm glad you know what's going on. I'll try and compile this up when I get home. Do I have to be a special directory to make this? Actually now that I think about it, I have no idea have to compile that. Hopefully it's a simple command line.

---

### Post by krunge on 2008-12-30
> **maxim99 said:**
> Should this be done from within the X server? Can it be done from a tty instead? Again, i'm glad you know what's going on.

I think it is best to run it from a terminal running inside the X server. That way you will see if it injects the keystrokes into your terminal (or a 2nd terminal if you move the mouse focus to it within the first 2 seconds)

You can run it from a console tty or ssh login if you want.  You will need to make sure the env. vars. DISPLAY and possibly XAUTHORITY are set correctly. If Xorg crashes you'll know that was it (otherwise you should try to verify the keystrokes were injected successfully.)
> 
I'll try and compile this up when I get home. Do I have to be a special directory to make this? Actually now that I think about it, I have no idea have to compile that. Hopefully it's a simple command line.

At the top of the file it says how to compile it.  Just save the text to a file "xkeytest.c" and follow the instructions at the top.

You will need gcc and dev packages of course, which your distro will likely send you on a scavenger hunt for.

---

### Post by maxim99 on 2008-12-30
Snap. Sorry, i didn't read the comments at the top of the file. I see what to do now.

Unfortunately I haven't been able to get mythbuntu to fully install again. It keeps crashing at the very end of the install. Kinda weird. I'll have to fool around with it after the new year. I'll be out of town for the next couple of days.

---

### Post by krunge on 2008-12-30
> **maxim99 said:**
> 
Unfortunately I haven't been able to get mythbuntu to fully install again. It keeps crashing at the very end of the install. Kinda weird.

Be sure to check carefully that bad hardware isn't causing the "bug".

---

### Post by maxim99 on 2009-01-01
> **krunge said:**
> Be sure to check carefully that bad hardware isn't causing the "bug".

It was a BIOS setting that was causing it. It's a totally new system so I'm not sure what setting it was since I'm not totally familiar with it. I F9ed it and restored everything to the Defaults and it installed without an issue.

Also there has been an update by someone at the bug report that I opened here:

[https://bugs.launchpad.net/bugs/312168](https://bugs.launchpad.net/bugs/312168)

They have apparently found the cause. It appears to be related to this patch here:

[http://lists.debian.org/debian-x/2008/12/msg00198.html](http://lists.debian.org/debian-x/2008/12/msg00198.html)

They say "missing null check in 154_force-copykeyclass-for-key-events.patch"

This is also posted in there. I haven't tested this yet, but I just got mythbuntu installed again and will be testing it momentarily.

```
safe binary patch to fix it without waiting for new packages:
$ sudo sed -ibak /usr/bin/Xorg -e 's/\x8b\x55\xdc\x89\x7c\x24\x04\x89\x14\x24\xe8\x59\x10\x07\x00\x85\xff\x0f\x85\x74\xfe\xff\xff\x85\xf6/\x85\xff\x74\x13\x8b\x55\xdc\x57\x52\x90\xe8\x59\x10\x07\x00\x83\xC4\x08\xe9\x74\xfe\xff\xff\x85\xf6/'
$ md5sum /usr/bin/Xorg*
c0ebe565e608f4175253d6f77f89a229 /usr/bin/Xorg
f10c2687c8bc69ee1cbf37d362cd0f7e /usr/bin/Xorg.bak

===============
patch:
--- ./154_force-copykeyclass-for-key-events.patch 2008-12-31 23:01:53.000000000 -0500
+++ ./154_force-copykeyclass-for-key-events.patch.fixed 2008-12-31 23:04:45.000000000 -0500
@@ -49,7 +49,7 @@
 + is transferred. */
 + if (event->u.u.type == DeviceKeyPress ||
 + event->u.u.type == DeviceKeyRelease)
-+ CopyKeyClass(dev, master);
++ if (master) CopyKeyClass(dev, master);
 +
              if (master)
                  CopyGetMasterEvent(master, event,
```

---

### Post by maxim99 on 2009-01-01
haha, it appears to be fixed already. I just did a test and updated everything just like before and it works perfect. Awesome. The open source community never ceases to amaze me. Thanks for your input on this whole matter krunge!

---

### Post by maxim99 on 2009-01-01
Nevermind, jumped the gun. Oddly enough, it worked after a reboot, and then after I had x11vnc start up with GDM, it started crashing the X server. Oh well. It works before the updates, and since it's alpha software anyway, i'm sure it'll get fixed eventually.

---

### Post by maxim99 on 2009-01-01
I was able to get it working by loading x11vnc through the autostart apps in xfce4 using just the x11vnc command without any options. So in short, alpha2, no updates, x11vnc through xfce4 autostarted apps. I will humbly await a new version of xorg to be released which addresses this issue.

Nevermind again, spoke too soon. I rebooted three times this time each time testing x11vnc functionality and it worked all but the last time. I made no changes except to the grub menu.lst file to add vga=791, and remove splash and quiet.

---

### Post by maxim99 on 2009-01-02
I found out why it was working sometimes and not others.

Given the scenario where x11vnc would start with GDM, X would crash when connected and keyboard was pressed through x11vnc.

Given the scenario where x11vnc was started after X was started manually through a terminal window on the machine, X would not crash.

The difference between the two is input from the keyboard in the second scenario. After input is recieved from a physical keyboard x11vnc does not crash X. It only crashes when there is no input received from a keyboard input before an attempt to use the keyboard through x11vnc.

---

### Post by krunge on 2009-01-02
> **maxim99 said:**
> 
The difference between the two is input from the keyboard in the second scenario. After input is recieved from a physical keyboard x11vnc does not crash X. It only crashes when there is no input received from a keyboard input before an attempt to use the keyboard through x11vnc.
Oh, I think I see.  From the patch for the fix you showed above:
```

- CopyKeyClass(dev, master);
+ if (master) CopyKeyClass(dev, master);

```
I guess when you first type at the physical keyboard "master" gets set properly (to something non null.)  Then even when you type through x11vnc master is still valid and so no crashes.

Only when you first type through x11vnc, then master is null and causes the crash.  However with the above fix, the crash is avoided by checking if master is OK  before making the function call.

---

### Post by maxim99 on 2009-01-30
This has been fixed in the latest Alpha3 release with all updates.

---

