---
title: "Problems with DVDs in Totem"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by ghindo on 2007-09-01
I'm running Feisty 7.04 on a Dell Inspiron 1420n.  When running DVDs in Totem, I have a few issues:[LIST]
[*]Lack of subtitles.
[*]Inability to access DVD menus.
[/LIST]I've searched Synaptic and Google to no avail.  Anyone have any hints?

---

### Post by RomeReactor on 2007-09-02
Hi. That happens while using the Gstreamer backend--that's the default on Ubuntu, and doesn't have that functionality. So you need to install **totem-xine** instead:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```
after that, totem should be able to access the menus and display subtitles.

---

### Post by ghindo on 2007-09-02
> **RomeReactor said:**
> Hi. That happens while using the Gstreamer backend--that's the default on Ubuntu, and doesn't have that functionality. So you need to install **totem-xine** instead:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```
after that, totem should be able to access the menus and display subtitles.Now I'm not able to play DVDs at all.  :(

---

### Post by RomeReactor on 2007-09-02
Make sure every needed package is installed:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```

If you were able to play DVDs previously, then all the packages will already be installed.

---

### Post by ghindo on 2007-09-03
> **RomeReactor said:**
> Make sure every needed package is installed:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```

If you were able to play DVDs previously, then all the packages will already be installed.Doesn't help too much.  Now whenever I open a video file, it closes after a few seconds.  I just keep having to revert back to gstreamer.

---

### Post by RomeReactor on 2007-09-03
Try opening totem from the terminal:
```
totem
```
then open a video file from its menu; if it crashes again (using the xine backend), it should leave error messages in the terminal, so please post those here.

---

### Post by ghindo on 2007-09-03
> **RomeReactor said:**
> Try opening totem from the terminal:
```
totem
```
then open a video file from its menu; if it crashes again (using the xine backend), it should leave error messages in the terminal, so please post those here.I receive this error message:```
[mpeg4 @ 0xb5cee8b4]looks like this file was encoded with (divx4/(old)xvid/opendivx) -> forcing low_delay flag
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 77 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by RomeReactor on 2007-09-04
Do you have desktop effects (Compiz/Beryl/Compiz Fusion) running while trying to play the videos? Do you have an Intel video card? If so, this might be related to [this bug]("https://bugs.launchpad.net/xorg-server/+bug/111257"). Try [this workaround]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback") from UbuntuGuide and see if it fixes your problem.

If you're using the **i810** driver, you can try adding an option to xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
scroll down to **Section  "Device"** and add the following line below the one specifying the driver:
```
Option "LinearAlloc" "8160"
```
save the file, close the text editor and restart the X server (press CTRL+ALT+BACKSPACE). if it still crashes, you can try increasing the value of LinearAlloc to **16000**. As you can [see here]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=badalloc&search=Search+Bug+Reports&field.scope=all&field.scope.target="), there are many bug reports referring to this issue.

---

### Post by ghindo on 2007-09-11
How do I tell which driver I have?

---

### Post by RomeReactor on 2007-09-11
Enter the following in the terminal:
```
cat /etc/X11/xorg.conf | grep Driver
```
the last driver entry is for your video card. Are you using any desktop effects? how much RAM does your system have?

---

