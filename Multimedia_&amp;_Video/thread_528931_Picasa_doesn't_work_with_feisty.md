---
title: "Picasa doesn't work with feisty"
date: 2007-08-18
forum: Multimedia &amp; Video
---

### Post by auradog on 2007-08-18
I've searched and searched, but I can't find a solution to make Picasa work for me.

I just upgraded from Edgy (where Picasa did work at first and then mysteriously stopped) and now Picasa doesn't work.

It installs fine. I've installed four different ways: Automatix, Synaptic Package manager, and downloading from google their .deb package as well as their .bin package.
When I start it, there are no errors or any other sign of distress and it seems to be running, because it is listed as a running process when I check  (ps -ef |grep picasa) to see it is running. 
it just doesn't show up on screen. 

What gives?

Can anyone help?

Thanks in advance.

---

### Post by kellemes on 2007-08-18
When started from the terminal.. do you get any interesting messages?

---

### Post by auradog on 2007-08-18
Nothing.

But, here's what I get when I, "ps -ef |grep picasa"

kturner  16311     1  0 16:10 ?        00:00:00 /bin/bash /opt/picasa/bin/picasa
kturner  16320 16311  0 16:10 ?        00:00:00 /bin/bash /opt/picasa/bin/wrapper regedit /E /tmp/picasa.mediacheck.reg.n16319 HKEY_USERS\S-1-5-4\Software\Google\Picasa\Picasa2\Preferences\

It sure looks like it's running, but I sure don't see it.

Thanks.

---

### Post by auradog on 2007-08-18
I guess I should have added:

When I click on the picasa icon, I get nothing, but if I, "ps -ef |grep picasa"
(see earlier post)

When I type picasa at the terminal it hangs but I still get (see earlier post)

(I hope I haven't confused you)

thanks

---

### Post by auradog on 2007-08-18
I can get it to run if I do it like:
~/.picasa/drive_c/Program Files/Picasa2
wine Picasa2.exe

but it runs very slowly.

and here's the output I get.
-----------------------------------------------------

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:ole:CoResumeClassObjects stub
fixme:urlmon:DllGetClassObject {79eac9e5-baf9-11ce-8c82-00aa004ba90b}: no class found.
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:create_server class {79eac9e5-baf9-11ce-8c82-00aa004ba90b} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {79eac9e5-baf9-11ce-8c82-00aa004ba90b} could be created for context 0x17
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:wininet:InternetGetConnectedState always returning LAN connection.
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:win:FlashWindowEx 0x33c244

------------------------------------------
It looks like it has something to do with my X setup and/or video card (an older nVidia), yes?

---

### Post by bramberg on 2007-10-07
I had the same problem as described above with Picasa. I have it now working with Wine and the windows version of Picasa. A description of how to install Picasa under Wine can be found in this tread: [http://ubuntuforums.org/showthread.php?t=528151&highlight=picasa](http://ubuntuforums.org/showthread.php?t=528151&highlight=picasa)

---

