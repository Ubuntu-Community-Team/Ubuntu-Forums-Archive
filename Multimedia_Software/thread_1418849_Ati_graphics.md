---
title: "Ati graphics"
date: 2010-03-01
forum: Multimedia Software
---

### Post by Flaffen on 2010-03-01
I have the open source drivers for my ATI card, but when I try to run WoW in wine I get a error message that reads:

X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 135 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 228
Current serial number in output stream: 228

I've tried to find something about this and it seems its a common problem with Karmic. Problem is that I'm still a n00b with Ubuntu and I have no idea what to do.
I cant install the proprietary fglrx drivers as they dont support my card.
My ATI card is Radeon 9200 PRO, and I'm running Ubuntu 9.10.

And when I write:

glxinfo | grep rendering or
glxinfo | grep
in terminal, I get this error too:
X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 135 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 16
Current serial number in output stream: 16

I have no idea what this is, but I'm guessing that my X or graphics drivers are not functioning properly.

Does anyone have any idea?

---

### Post by darolu on 2010-03-01
You need to install mesa-utils to run glxinfo:
```
$ sudo apt-get install mesa-utils
```

---

### Post by Flaffen on 2010-03-01
ok thanx, will try that

---

### Post by Yellow Pasque on 2010-03-01
More specifically: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by Flaffen on 2010-03-01
Well, I did the sudo apt get thing and then terminal said this:
mesa-utils is already the newest version
he following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 fakeroot libwxgtk2.8-0 dkms libwxbase2.8-0
  fglrx-kernel-source xorg-driver-fglrx python-wxversion imagemagick patch
  python-wxgtk2.8 linux-headers-2.6.31-14-generic

that means there's something screwy going on right?
my mesa utils are not working properly?

---

### Post by Yellow Pasque on 2010-03-01
Some of the files in various mesa packages were overwritten by ATI's proprietary files when you tried to install Catalyst/fglrx. It means you need to do this:
```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
Log out to restart the X server.

---

### Post by Flaffen on 2010-03-01
Ok, so I did all those commands. Diddent help.
I have not tried to install the propietary drivers since my last install of Ubuntu 9.10 anyway.

Still get same error:
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  228
  Current serial number in output stream:  228

and when I try: glxinfo | grep rendering or glxinfo | grep I still get that same error message.

The mesa and ati drivers should atleast be correctly installed now.
Anyone got any other ideas of what I can do?

---

### Post by Flaffen on 2010-03-01
Ok, so now I've installed a game called Boson for linux, and I get error messages there too.
Even with Starcraft I get this message:
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  1059
  Current serial number in output stream:  1059

Now, starcraft is a low graphics game, so I guess there is something wrong with the drivers or X.org.


How can I install another version of X.org? Or do anything at all so that games with graphics work?

This was the error code with Boson:
[int main(int, char**)] Boson 0.13 is starting...
[int main(int, char**)] resolving GL, GLX and GLU symbols
cannot enter directory /lib/i486-linux-gnu
ERROR: [bool BoGL::initialize()] GL methods have not yet been resolved.
ERROR: [bool BoGL::initialize()] GL methods have not yet been resolved.
cannot enter directory /lib/i486-linux-gnu
Resolved GL symbols from file /usr/lib/libGL.so.1
Resolved GLU symbols from file /usr/lib/libGLU.so.1
[int main(int, char**)] GL, GLX and GLU symbols successfully resolved
kbuildsycoca running...
Reusing existing ksycoca
Boson Sound: [BosonAudioInterface::BosonAudioInterface()] 
Boson Sound: [BosonAudioInterface::BosonAudioInterface()] construct BosonAudio object
boson: [BosonAudioAL::BosonAudioAL()] initializing OpenAL
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
boson: [BosonAudioAL::BosonAudioAL()] OpenAL initialized
Boson Sound: ERROR: [BosonMusic::BosonMusic(BosonAudioAL*)] oops - should be invalid
Boson Sound: [BosonAudioInterface::BosonAudioInterface()] BosonAudio object constructed
Boson Sound: [void BosonAudioAL::executeCommand(BoAudioCommand*, BosonMusic*, BosonSound*)] music object is created on startup. nothing to do
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  135
  Minor opcode:  19
  Resource id:  0x3c00008
boson: ../../src/xcb_io.c:542: _XRead: Assertion `dpy->xcb->reply_data != ((void *)0)' failed.
KCrash: Application 'boson' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

Now to mee it seems that some file or something is missing in my X.org or drivers, tho I'm a noob so I dont really know.
I just know that everything requiring graphics doesent work wich is annoying.
Am I wrong in thinking that there is some malfunction with my X.org?

Any ideas?

---

### Post by Flaffen on 2010-03-01
Ok, so I was just looking through my /ect/x11/ folder and I cant seem to find any xorg.conf file.
Shouldent there be one there? And if so, how do I get it there with the right info in it? Like Section (someinfo) Endsection?

Is that the problem? That i'm missing my xorg.conf file?

---

