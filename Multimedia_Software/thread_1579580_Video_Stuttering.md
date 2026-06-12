---
title: "Video Stuttering"
date: 2010-09-22
forum: Multimedia Software
---

### Post by Pnev on 2010-09-22
Hello,

I am new to Ubuntu (like, installed it today for the first time, new) and just installed it on an old computer. I'm not positive on the computer specs, but I'm pretty sure it's a Pentium 4, 512 MB of RAM and an ATI Radeon 9400.

My problem is that video playback stutters. Not too badly, but constantly and too much to comfortably watch it. I'm using VLC, and I disabled a few things that I could find (desktop effects) and lowered the resolution, and it got better, but still not watchable. Is the computer just not powerful enough to play basic avi's on 10.4? Or does this sound like something I can fix? Any help would be appreciated!

-Pnev

---

### Post by nikosm on 2010-09-22
Hi Pnev,

same problem here on an Acer Aspire 5610Z. When calling vlc from the command line, the following is reported when the stuttering beggins (not always but usually, and always with big stuttering):

```
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x81668fc] main libvlc: VLC wird mit dem Standard-Interface ausgeführt. Benutzen Sie 'cvlc', um VLC ohne Interface zu verwenden.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb75c00d4, 0xb75c0048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1285291074)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:1974): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
[COLOR="Red"][0x821f824] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)[/COLOR]
warning: first frame is no keyframe

```

(Pnev, can you check if this error message appears for you too when running vlc from the command line?)

This appeared after a fresh install of Lucid, and remained after an upgrade to Maverick.

Also, in Lucid, after a while the computer would shut down completely during playback (haven't tested under Maverick) and irrespective of video playback, it refused to suspend (brought up a login screen).

All the above problems didn't appear with the previous OS which was quite old ubuntu, I think 08.04 .

Any help is greatly appreciated.

Nikos

P.S. Problem also appears with totem, no error is reported in the console.

---

### Post by Pnev on 2010-09-22
How do I run VLC from the command line?

---

### Post by nikosm on 2010-09-22
Hi Pnev,

I think the easiest is to copy a video file that you know is problematic to the Videos folder in your home directory. After doing that go to Applications > Accessories > Terminal
A black window will open with a cursor. type the following two lines and press enter after each of them:
```
cd Videos
vlc <videofilename>

```
where videofilename is the filename of the video you have copied. Remember than filenames are case-sensitive. You can start typing the filename and then press the TAB button to complete.

hope this helps,
Nikos

---

### Post by TBABill on 2010-09-22
Have you installed the proprietary driver for your video card? If you are running open source drivers you may be experiencing lesser performance than you would with the ATI driver. Also, have you installed the ubuntu-restricted-extras from the Ubuntu Software Center (under applications in the menus)? That will pull in all the codecs that don't get installed on the standard install.

---

