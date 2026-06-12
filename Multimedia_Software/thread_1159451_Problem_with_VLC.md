---
title: "Problem with VLC"
date: 2009-05-14
forum: Multimedia Software
---

### Post by 71CH on 2009-05-14
Hi all.  When I try to start VLC I get this:

```
VLC media player 0.9.0 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.0 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--disable-swscale'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc error: no memcpy module matched "any"
[00000008] main interface error: no interface module matched "hotkeys,none"
[00000008] main interface error: no suitable interface module
[00000001] main libvlc error: interface "hotkeys,none" initialization failed
[00000009] main interface error: no interface module matched "inhibit,none"
[00000009] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000010] main interface error: no interface module matched "screensaver,none"
[00000010] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000011] main interface error: no interface module matched "signals"
[00000011] main interface error: no suitable interface module
[00000001] main libvlc error: interface "signals" initialization failed
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000012] main interface error: no interface module matched "any"
[00000012] main interface error: no suitable interface module
[00000001] main libvlc error: interface "(null)" initialization failed
*** LibVLC Exception not handled: Interface initialization failed
Set a breakpoint in 'libvlc_exception_not_handled' to debug.

```

Anybody know how to fix this?  Thanks.

---

### Post by khelben1979 on 2009-05-14
This looks like you or someone else have tried to compile up VLC and failed with the installation. Is that the case here?

```
sudo apt-get install vlc
```
installs vlc the correct way.

---

### Post by 71CH on 2009-05-14
Thanks for your reply.  I already tried to install it that way but because of the failed compiling it won't work.  VLC shows up in the menu but when I click it nothing appears.  When I try to run it in terminal the above shows.  I tried to purge and remove but maybe it doesn't remove it completely?  Anybody know how to COMPLETELY remove it?  I tried sudo apt-get remove vlc --purge already.  Oh and when I do sudo apt-get install vlc it looks like it doesn't download any files but just reinstalls from previously downloaded deb files, if that makes any sense.

---

### Post by mc4man on 2009-05-14
> but because of the failed compiling it won't work

You may wish to describe this a bit more.
Where did you get 0.9.0 from? (I'd assume you built it yourself, though maybe someone had that version available as a .deb package set.

If you built it, do you still have the build/source folder?

---

### Post by 71CH on 2009-05-14
I don't have the source folder anymore.  I deleted it.  I guess I messed up big time.

---

### Post by mc4man on 2009-05-14
Yeah but it should be salvageable, hopefully  you installed to /usr/local/, which will make it easier to remove all the files.

There are 2 ways
The cleanest would be to dl the 0.9.0 source, extract, configure as you did before, make, sudo make install followed by sudo make uninstall.

Otherwise you can try to manually remove everything.

If you wish to do that then as starters first search vlc in synaptic and mark for complete removal anything with vlc in the name and apply.
Also go into home folder (show hidden files) and if there is a .vlc delete it. Also look in .config folder and if there is a vlc folder delete it as well.

(note none of the above is removing the vlc you built, but should be done anyway and will make a final search ck. easier.

Let me know and I'll give you a list of folders, and several files to delete.

Before anything open a terminal and start vlc just to confirm the the configure options. (post the complete terminal output, want to see the configure options you used

Edit; if it turns out you installed to /usr/ there may be a shortcut to the whole deal so let me know

---

### Post by 71CH on 2009-05-14
Ok I did all of the above and here is what I get

```
VLC media player 0.9.0 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.0 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--disable-swscale'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc error: no memcpy module matched "any"
[00000008] main interface error: no interface module matched "hotkeys,none"
[00000008] main interface error: no suitable interface module
[00000001] main libvlc error: interface "hotkeys,none" initialization failed
[00000009] main interface error: no interface module matched "inhibit,none"
[00000009] main interface error: no suitable interface module
[00000001] main libvlc error: interface "inhibit,none" initialization failed
[00000010] main interface error: no interface module matched "screensaver,none"
[00000010] main interface error: no suitable interface module
[00000001] main libvlc error: interface "screensaver,none" initialization failed
[00000011] main interface error: no interface module matched "signals"
[00000011] main interface error: no suitable interface module
[00000001] main libvlc error: interface "signals" initialization failed
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000012] main interface error: no interface module matched "any"
[00000012] main interface error: no suitable interface module
[00000001] main libvlc error: interface "(null)" initialization failed
*** LibVLC Exception not handled: Interface initialization failed
Set a breakpoint in 'libvlc_exception_not_handled' to debug.

```

And I don't think I installed to /usr.  Thanks for your help.

EDIT: I just did a search for "vlc" and I found some stuff that might be in /usr.  Don't know what that means.  Should I just delete all of that?

---

### Post by mc4man on 2009-05-14
I'd do what I first mentioned, search synaptic, uninstall any package with vlc, ect.

Then the places vlc installs to. (same directories whether installed to /usr or /usr/local

Start in /usr/local (much less to look thru, if not there go back to /usr/

the dir. are
share - a vlc folder - delete
include - a vlc folder - delete
lib - a vlc folder - delete
bin -  up to 4 files - cvlc, svlc, rvlc and vlc
the will also be a lib or two loose in the lib dir. , will edit the names in a moment

After that run a search again, ignore anything in root trash (unless you do a full delete then nothing will go to the root trash


Edit:
if vlc was installed to usr/local the loose libs in /usr/local/lib will be obvious

If installed to /usr/lib then not so

To find, go (while in the /usr/lib directory) edit -> "select items matching" -> and for the pattern use
```
libvlc*
```

There may be 6 or 7

---

### Post by 71CH on 2009-05-15
Thanks bud.  Worked like a charm.  BTW, would you happen to know how to install version 0.9 or higher on 8.04?  Thanks.

---

### Post by mc4man on 2009-05-15
Here's a ppa for vlc with a vlc 0.9.9a version

[https://edge.launchpad.net/~c-korn/+archive/vlc](https://edge.launchpad.net/~c-korn/+archive/vlc)

Just change the 'source list. entries' drop down to hardy, and copy the entries 1 at a time into your sources list.
(System -> Admin. -> Software sources -> Third Party -> add
After adding a line, click add source, after adding both then click close and then reload.

(there may be error about authenticate key, blah, blah, I don't bother adding one for ppa's, you can search how to, though it doesn't effect adding packages. (not having the key

Then go into synaptic, search vlc and you should see 0.9.9a available 
If you had re-installed the hardy 0.8.6 version I'd remove it completely first like before (vlc, vlc-nox, ect. Not 100% necessary, but better practice.

).9.9.a works pretty good, a few things are broken or regressed, you may never notice.

---

### Post by 71CH on 2009-05-17
Thanks bro.

---

