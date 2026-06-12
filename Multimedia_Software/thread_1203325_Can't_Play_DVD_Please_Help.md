---
title: "Can't Play DVD Please Help"
date: 2009-07-03
forum: Multimedia Software
---

### Post by vimod.c.nair on 2009-07-03
Hi,

I had installed Ubuntu 9.0.4 LTS and updated it. I am pretty impressed but 'am bit dissapointed when  an error prompted I can't play my DVD because the codecs were not available, I didn't tried playing any other formats so I don't know whether those would play in my Ubuntu PC. I am pretty new to linux and I am not sure what to do. Please help me. I had installed Ubunt on my hp dx2255 Business PC, which has AMD Athlon 64 3500+ as processor, I GB RAM, 80 GB samsung harddisk, and VIA  chipset, and has VIA Crome 9 for graphics.

By-the-by I want to from where can I get some good 3D Games such as NFS, GTA ... etc, which I can play on linux.

---

### Post by khelben1979 on 2009-07-03
You need [Medibuntu]("http://en.wikipedia.org/wiki/Medibuntu").

[Adding the repositories to Ubuntu]("https://help.ubuntu.com/community/Medibuntu#Adding the Repositories").

Other than this, make sure that you have [libdvdcss]("http://en.wikipedia.org/wiki/Libdvdcss") installed in your system.

---

### Post by khelben1979 on 2009-07-03
> **vimod.c.nair said:**
> By-the-by I want to from where can I get some good 3D Games such as NFS, GTA ... etc, which I can play on linux.

You can find demo versions of a lot of Windows games from several sources, but here is one: [GamersHell.com]("http://www.gamershell.com/").

---

### Post by jasonsjunk on 2009-07-03
Read this post  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

That should solve your problems.

---

### Post by Kainwolf on 2009-07-04
Installed the codecs including the medibuntu repository, didn't help.
Dragonplayer: spins up DVD drive momentarily, then sits there
Kaffeine: gives "This DVD Video is encrypted..." message
Mplayer & VLC: Spins up DVD then immediately closes
Totem: "Could not play DVD. No reason."

Tried on 3 different machines with Intrepid, same results on all 3.  Any further suggestions?

---

### Post by HappyFeet on 2009-07-04
Did you do
```
sudo apt-get install libdvdcss2
```?

---

### Post by Kainwolf on 2009-07-04
"libdvdcss2 is already the newest version."

---

### Post by mc4man on 2009-07-04
Not to keen on kubuntu but...

kaffeine - ck and see if libxine1-ffmpeg is installed

vlc - open vlc from the konsole, then media -> open disc and see what the konsole output says (vlc tends to close immediately (crash) when there is an issue with the audio and or video output.

---

### Post by Kainwolf on 2009-07-04
I'm the opposite, I've never liked gnome.

Thanks for the advice; installed libxine1-ffmpeg; now dragonplayer & kaffeine play a 25-second blue screen, no matter what DVD I insert, or what title/chapter on that DVD I select.

vlc reports errors wtih QPainter (?):

```
QPainter::setClipRegion: Painter not active
QPainter::setClipping: Painter not active, state will be reset by begin
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86
Cannot find libdbus-1 in your system to resolve symbol 'dbus_connection_close'.
Aborted
```

---

### Post by mc4man on 2009-07-04
Open vlc -> tools -> preferences, highlight the video icon and change the 'output' dropdown from 'default' to something specific (try X11 )
click save, try

What's your video adapter, do you have restricted drivers enabled? (if available

For kaffeine in the settings ->  xine parameters -. video there are some options other than auto (but no X11

Xv is preferred over X11, though using Xv may depend on your video drivers, some setups can use opengl, sdl is another option to try

(on my nvidia I use Xv for all, sdl also works in vlc, mplayer, though kaffeine will only allow Xv

edit 
for kaffeine if Xv doesn't work try xshm (i think that's X11

---

### Post by npm1 on 2009-07-04
install wine then install the desired dvd player i.e. power cinema
then play dvds through their

---

