---
title: "Tablet Issue"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by ~/Chromekaldra/~ on 2007-12-12
Installed my Wacom tablet (aparrently surpported by the Wacom Linux Distrubution as it's a bamboo, but i found nothing usful on their site.)

Basically, i used Wine to install the Tabet and that worked nice and dandy. However, when i go to App > Wine > Programs > Tablet > Pen Tablet properties, the display box for it appears on my base panel, and i get the 'busy' cursor, but then after about 10 seconds, it dissapears, closes, w/o anything opeing or anything. I need to run this app in order to use the tablet...

I've scoured a few sites that attempt to help but i'm a n00b to Linux (ubuntu) so i got lost real quick...

Please help, this tablet was expensive and i'd like to use it very much. :(

---

### Post by em es on 2007-12-25
Hi, I'm trying to get my bamboo working too. I wouldn't try and get it to work with wine, since it would probably be much faster if you use a native driver, that is without wine.

If you are using Gutsy Gibbon you might try this thread:
[http://ubuntuforums.org/showthread.php?t=631881&highlight=wacom+bamboo]("http://ubuntuforums.org/showthread.php?t=631881&highlight=wacom+bamboo") and if you are using Feisty Fawn this Thread [http://ubuntuforums.org/showthread.php?t=488013&highlight=wacom+bamboo]("http://ubuntuforums.org/showthread.php?t=488013&highlight=wacom+bamboo").

It's a bit tricky and if you are unsure you might want to wait until the next release of the Ubuntu Kernel (2.6.23) - native wacom support will be included, so you don't need to play around. (I'm still having problems with my bamboo)

---

### Post by the dsc on 2008-06-18
The problem is that without the installation of the windows driver, we're not able to use all the tablet's resources in programs running under wine.

The mentioned "tablet pen properties" option in the menu links to "PenTablet.cpl", somewhere under that fake windows directory, but not directly, the "command line" is that:

wine "C:\windows\command\start.exe" "C:\windows\system32\PenTablet.cpl"

Which "start.exe" is not able to run. It says:

```

fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: Success

```

There are a couple of tablet-related files, one is an .exe, I've executed it with wine, and after some time it just says that the driver isn't loaded. Looking a bit on google, I've found this:

> 7.3.6. Wine drivers

Wine will not allow running native Windows drivers under Unix. This comes mainly because (look at the generic architecture schemas) Wine doesn't implement the kernel features of Windows (kernel here really means the kernel, not the KERNEL32 DLL), but rather sets up a proxy layer on top of the Unix kernel to provide the NTDLL and KERNEL32 features. This means that Wine doesn't provide the inner infrastructure to run native drivers, either from the Win9x family or from the NT family.

In other words, Wine will only be able to provide access to a specific device, if and only if, 1/ this device is supported in Unix (there is Unix-driver to talk to it), 2/ Wine has implemented the proxy code to make the glue between the API of a Windows driver, and the Unix interface of the Unix driver.

Wine, however, tries to implement in the various DLLs needing to access devices to do it through the standard Windows APIs for device drivers in user space. This is for example the case for the multimedia drivers, where Wine loads Wine builtin DLLs to talk to the OSS interface, or the ALSA interface. Those DLLs implement the same interface as any user space audio driver in Windows. 

[http://www.winehq.org/site/docs/winedev-guide/x2584](http://www.winehq.org/site/docs/winedev-guide/x2584)



In the other hand, I've seen in some forums people saying that pressure sensivity worked better under wine than in native linux support... so either it's "outdated" (regarding the inability to run specifically this driver), or they were just fantasizing...

I notice now that this topic itself is a bit old. Which version of wine do you ubuntuers are running now, and how does it handle pressure sensivity in applications running under wine? I'm in debian lenny, wine is 1.0-rc2, and I couldn't manage to have pressure sensivity yet (under wine).

---

### Post by the dsc on 2008-06-19
Something related I've found in another forum (vector linux):

> 6.Tablet support in wine
 (artrage,open canvas,photoshop cs1,2...and so on)-
Your pressure sensitivity should work fine for you in those applications and that makes wine really great,because they are trully awesome drawing apps.If it doesnt,then something must be wrong with the version of wine you are using. In my case,pressure sensitivity did not work,because of the curent version of the wacom driver and wine.In order to get it to work again,i had to apply a patch (read here: [http://www.vectorlinux.com/forum2/index.php?topic=5046.30](http://www.vectorlinux.com/forum2/index.php?topic=5046.30)  ). If you dont know how to apply a patch,and you are running vl-5.9 (or 6),i have a package of the patched version of wine that i use curently:
[http://blurymind.googlepages.com/wine-0.9.61-i386-1.tlz](http://blurymind.googlepages.com/wine-0.9.61-i386-1.tlz)

[http://www.vectorlinux.com/forum2/index.php?topic=6458.0](http://www.vectorlinux.com/forum2/index.php?topic=6458.0)

Disclaimer: I don't know how version/distribution-specific these things are. By the way, anyone knows? (That's not a rethorical question)

---

