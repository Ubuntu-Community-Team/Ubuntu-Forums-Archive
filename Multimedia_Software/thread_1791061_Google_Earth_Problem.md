---
title: "Google Earth Problem"
date: 2011-06-26
forum: Multimedia Software
---

### Post by Wobblewing on 2011-06-26
Hi,  please bear with me I'm new to ubuntu! (and this forum)
I installed GE6 on 11.04 Natty a while a go.
Initially I had to sort the fonts out, but found the fix and that work fine.
However recently Google Earth will not start.  I get the 'Earth' start tile picture, then that disappears and nothing happens.
I retried removing and reinstalling, but that doesn't work either..

Can anyone point me to a fix?  I did a search but nothing seemed to indicate the same problem as I'm having.

Thanks  
Andy

---

### Post by AKADAP on 2011-06-26
open a terminal and type "google-earth", hit return and tell us what happens.

---

### Post by Wobblewing on 2011-06-26
Hey thanks for your reply.  This is what I got:

"andy@andy-Aspire-5100:~$ google-earth
Google Earth has caught signal 11.



We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/andy/.googleearth/crashlogs/crashlog-4e078c01.txt

Please include this file if you submit a bug report to Google.
"

Here's what is says in the crashlog
"Major Version 6
Minor Version 0
Build Number 0003
Build Date May 17 2011
Build Time 00:40:40
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 38
OS Patch Version 0
Crash Signal 11
Crash Time 1309117441
Up Time 6.21633

Stacktrace from glibc:
./libgoogleearth_free.so(+0xab953)[0x747953]
./libgoogleearth_free.so(+0xabad3)[0x747ad3]
[0xcf0400]
/opt/google/earth/free/libmeasure.so(_ZN5earth7measure5state19MeasureStateContext10OnLoggedInERKNS_4evll11StatusEventE+0x22)[0x2d139e2]
/opt/google/earth/free/libevll.so(_ZN5earth7EmitterINS_4evll14StatusObserverENS1_11StatusEventENS_19EmitterDefaultTraitIS2_S3_EEE6notifyEMS2_FvRKS3_ES8_bPKc+0x1af)[0x26cb37f]
/opt/google/earth/free/libevll.so(_ZN5earth4evll21ConnectionContextImpl11FinishLoginEv+0x177)[0x26be777]
/opt/google/earth/free/libevll.so(_ZN5earth4evll7APIImpl17NotifyInitializedEv+0x16d)[0x23d2bdd]
/opt/google/earth/free/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x25c)[0x23643fc]
./librender.so(_ZN12RenderWidget6SetApiEPN5earth4evll3APIE+0x47)[0x2815ae7]
./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0x16a)[0x27fa38a]
./libgoogleearth_free.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x8d)[0x72244d]
./libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0x770)[0xe91a60]
./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xac)[0xe2e69c]
./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x484)[0xe396c4]
./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x78)[0x8e2ba8]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x145)[0xe936d5]
./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7d)[0xe933cd]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0xc5)[0xe934b5]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xe935f1]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xe93a2b]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xe93560]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xe935f1]
./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7d)[0xe933cd]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0xc5)[0xe934b5]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xe935f1]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xe93a2b]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xe93560]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xe935f1]
./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7d)[0xe933cd]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0xc5)[0xe934b5]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xe935f1]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xe93a2b]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xe93560]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xe935f1]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xe93a2b]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xe93560]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xe935f1]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xe93a2b]
./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x170)[0xe93560]
./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x61)[0xe935f1]
./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x1db)[0xe93a2b]
./libQtGui.so.4(_ZN7QWidget10showNormalEv+0x5c)[0xe8116c]
./libgoogleearth_free.so(_ZN10MainWindow18readScreensizeInfoEv+0xd2f)[0x714bbf]
./libgoogleearth_free.so(_ZN5earth6client11Application12SetupMainWinENS0_3Kvw7ProductEb+0x31c)[0x74e8cc]
./libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x50e)[0x751aae]
./libgoogleearth_free.so(+0xaa40b)[0x74640b]
./libgoogleearth_free.so(earthmain+0x247)[0x747587]
./googleearth-bin[0x804872b]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe7)[0x6923e37]
./googleearth-bin[0x8048671]"


I have no idea what this lot means :-)  I suppose I'd better email someone at google?

---

### Post by beew on 2011-06-26
How did you install GE?

Check if you have lsb-core installed, if not, install it and see what happens.

---

### Post by Wobblewing on 2011-06-27
Yeah I did that... installed via the software centre as normal.
 
still no luck... unfortunately

---

### Post by beew on 2011-06-27
> **Wobblewing said:**
> Yeah I did that... installed via the software centre as normal.
 
still no luck... unfortunately

Uninstall the version you have installed from the Software Centre and download the .deb from googleearth

[http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Just right click and install. I have not had a problem with the 32 bit, don't know about 64 bit.

I don't know which version of GE do you get through the Software Centre, but it could be outdated or broken in some way.

(For right click install you may want to install gdebi and set it as the default to open .deb files, otherwise right clicking a .deb file would bring up the Software Centre, which is bloated and slow IMO, by the time it is ready gdebi would have finished installing the .deb)

---

### Post by Wobblewing on 2011-06-27
Thanks for your help Beew, this is exactly what I did.

Anyway I did it again just to be sure.  As you say, download it directly from google, then right click and accept the option 'open with ubuntu software centre'.  This is the only option which makes sense.

What I do notice though it that the installation process seems a bit short lived.  What I mean is that I click 'install', the bar moves a bit, the stops and goes back to showing 'install' again.

anyway, I did what you said and installed gdebi, issuing the command:
sudo gdebi google-earth-stable_current_i386.deb

So it goes away and installs some stuff.

When 'finished' I type google-earth..
.. then I get the same error as posted above..

any ideas?

---

### Post by Wobblewing on 2011-06-27
incidentally I also posted on this google forum.

no response yet, although I see some others maybe seeing the same issue?

[http://www.google.com/support/forum/p/earth/thread?fid=386445256b8644630004a6a30756b903&hl=en](http://www.google.com/support/forum/p/earth/thread?fid=386445256b8644630004a6a30756b903&hl=en)

---

### Post by Wobblewing on 2011-06-27
PS how do I set gdebi as default installer?

---

### Post by beew on 2011-06-27
I am not sure what happened. Maybe the configuration is corrupted or something. Go to your home directory, click View > Show Hidden Files, then look for the folder .googleearth and delete it and see if it works. Beyond that I am afraid you would have to wait for someone more knowledgeable to help you.

The other question is easy, to make gdebi the default, just right click any .deb file, choose properties > Open With and pick gdebi.

---

### Post by Wobblewing on 2011-06-28
Thanks for the help beew, I tried deleting .googleearth directory but no luck unfortunately.
Looks like I'm stuck for a little while, but thanks for taking the time helping out.

Andy

---

