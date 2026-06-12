---
title: "Multiple monitors, custom resolutions, twinview, xinerama, nothing works."
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by naptastic on 2007-04-22
More precisely: I can't find a solution that does *everything* I want it to do.

I want 3D acceleration on the desktop, so I installed restricted NVIDIA binaries. This was a challenge, make no mistake, but it worked eventually, and now I have 3D acceleration on both desktops.

One monitor is a Dell 17" LCD, which is almost universally detected correctly. (The one exception was the Feisty installer, which I had to run in "safe video" mode to use. Better than a poke in the eye with a sharp stick...) The other monitor is a Sharp 37" LCD TV, with a native resolution of 1366x768. Now, I have *no* hope of getting that resolution to work; Windows won't even do that. But, I've had 1280x768 working on Fedora Core and Windows before.

So I thought, I'll just copy my old xorg.conf file over and use it, right?

I don't know whose bug this is, but **if I use Xinerama on these two screens, it becomes impossible for some apps to open**. (most notably gnome-terminal - VERY annoying.) I click the icon, the wheel spins for a minute, and then the app disappears. Here is the output from .xsession-errors from one attempted instance:

> The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 100 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

So I switched to Twinview.

Now... I don't know if I've exhausted all resources on my own yet, trying to get a custom resolution out of Twinview. The only tool I can find to adjust it is nvidia-settings, and it has no provision for custom resolutions that I can find. Thumbing through the xorg.conf file to find modelines was fruitless.

I don't really like Twinview as much as Xinerama anyway; Gedit has this annoying habit of maximizing across both monitors under Twinview, which is VERY annoying.

So... is there a trick to getting custom resolutions through Twinview / nvidia-settings? Is there a fix for the bug with Xinerama? Is there an open-source driver I can try that will do everything I want?

---

### Post by mwshook on 2007-04-22
I'm having the same problem. It took me a lot of hassle to get my dual monitors to work. And yes, xinerama is a much better solution than twinview. 

With twinview, I didn't like how stuff maximized across 2 screens. Also, doing the fullscreen slideshow on the default image viewer would center it between the two screens.

But I'm having the exact same problem with gnome-terminal and xinerama. I'm using xterm instead. Are there other apps I haven't found yet, that don't work with xinerama?

---

### Post by mwshook on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Searching the forums, I found a workaround
[http://ubuntuforums.org/showthread.php?t=276354&highlight=gnome+terminal](http://ubuntuforums.org/showthread.php?t=276354&highlight=gnome+terminal)

The last post on the thread has some code to add to xorg.conf
After adding it, gnome-terminal works fine for me. 

This is apparently a known bug since August, and is "High Priority." I don't know why it wasn't fixed before feisty. Maybe because it involves the proprietary nvidia drivers.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)

---

### Post by naptastic on 2007-05-04
Disabling NVidia's composite extension fixed the issue.

> Section "Extensions"
Option "Composite" "false"
EndSection

I added that to my xorg.conf file and everything is groovy. Except that I can't use the nifty 3D window managers (beryl, compiz) since the composite extension is necessary for those to work. But that's OK--I can live without them.

It also looks like this problem will be permanently fixed with the next release of the NV binary drivers; disabling composite extensions will not be necessary.

Best of luck to anyone else having this problem!

---

