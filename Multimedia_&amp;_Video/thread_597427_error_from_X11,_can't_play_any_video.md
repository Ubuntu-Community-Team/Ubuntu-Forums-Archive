---
title: "error from X11, can't play any video"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by zlochko on 2007-10-30
Hallo everybody. I've installed 7.10 and so far I am very satisfied... there is only one problem thou.
I can't play any video files (except flash).

Every peace of software I start gives me some strange errors which are somehow cosed by X11.
This is what Totem is throwing:

[FONT="Courier New"]The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 92 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/FONT]

mplayer or any other video player also refuses to play giving me the same strange error:
[FONT="Courier New"]The error was 'BadAlloc (insufficient resources for operation)'.[/FONT]

Can anyone please help me? I really am quite baffled on what to do next. :confused:
Thank you very much.

Gjoko.

---

### Post by zlochko on 2007-10-30
Even VLC is crushing down. :mad:
This is the log:
[FONT="Courier New"]
VLC media player 0.8.6c Janus

** (.:24010): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
main warning: can't store message (Invalid or incomplete multibyte or wide character): found Chunk fourcc:22b083c8 (
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  86
  Current serial number in output stream:  87[/FONT]

This is not fair... (whine)

Gjoko.

---

### Post by DeadToad on 2007-10-30
try reinstalling vlc VideoLAN Media Player for Linux Ubuntu Gutsy Gibbon v7.10

To install/reinstall VLC Media Player:
Open Synaptic (System -> Administration -> Synaptic Package Manager).
Type your password.
Click Settings -> Repositories.
Under "Ubuntu Software" check the first four items, making sure you have the "universe" repository checked.
Do NOT check "source code".
Under "Third-Party Software" check all items.
Under "Updated/Ubuntu Updates" check the first two items.
Click "Close", twice if necessary.
Now back at the Synaptic Package Manager main window:
Click "Search".
Type "vlc".
Click "Search" button.
"vlc" will be shown in the left window.  left-click it once to highlight it.
In the right window, click on these additional files: vlc-plugin-esd and mozilla-plugin-vlc, then click "Mark for installation" for each file.
(libdvdcss2 which will be installed later, as it is NOT in a repository).
Click "Apply".
Click "Apply" again, if necessary to begin download.
After "Changes applied", click "Close".
Close "Synaptic Package Manager" window.

Now, you just need to REINSTALL livdvdcss2 to get VLC and Totem MPlayer to play DVDs:
"libdvdcss2_1.2.9-1_i386.deb" is here: 
[http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html](http://files.filefront.com/libdvdcss2+129+1+i386deb/;6575747;/fileinfo.html)
(This is the version that works).
If not found, google "libdvdcss2_1.2.9-1_i386.deb" for an active link.

Just click the link, then "open" it with the default selection (do NOT save it).
Then click "Install Package", and let it finish.
After that, VLC Media Player and Totem MPlayer will play your DVDs.

Reboot computer, then run Update Manager again for additional updates (libdvdread3):
System/Administration/Update Manager.

You may need these two additional CODECS to play DVDs:
libdvdread3 and libxine1-ffmpeg (in the Ubuntu repository).
To install them through the command line, type the following:
sudo apt-get install libdvdread3 libxine1-ffmpeg
===

Good luck.
DeadToad

---

### Post by zlochko on 2007-10-30
I don't think the problem is there....
Anyway... I've got at least VLC working. I only changed the Video Output Module from 'default' to 'X11 video output' in Preferences > Video > Output modules 
But this is only a VLC only fix. Yet... it's movie time! :popcorn:
It seems that the problem might be connected with my Compiz.

Any gurus out there to tell me how to change the output module on a system wide level?

Thanks.
Gjoko.

---

### Post by wouterommeslag on 2007-10-30
I have the same problem. 

When I turn compiz off, everything runs fine. With Compiz turned on, I get the 

The error was 'BadAlloc (insufficient resources for operation)'.

error. Setting my gstreamer video output to "no Xv" "solves" the issue, but my CPU rate goes through the roof and high res video plays with hick ups...

Is a better solution available?

---

### Post by defrex on 2007-11-02
I'm also having the same issue. Ironically, it only started after I moved from feisty upgraded to gutsy, to a fresh gutsy install (same /home).

I'll use the vlc fix for now. But a real solution would be awesome.

Oh, and interestingly, I'm using one of the blacklisted intel video cards. Playing video with this problem, plus the aforementioned vlc fix gets rid of the video-playback bug that's all the fuss in the first place.

---

### Post by arthur_kalm on 2007-11-05
The "real" solution that I found is to install xserver-xgl. It seems AIGLX really sucks a lot, so I highly recommend XGL.

> sudo aptitude install xserver-xgl

XGL works on all video cards, Intel, nVidia and ATi.

---

### Post by Seq on 2007-11-05
What kind of Video Card do you have? This sounds like the issue with the Intel X3100 when using compiz (xv stops working when not using EXA).

---

### Post by zlochko on 2007-11-07
> **Seq said:**
> What kind of Video Card do you have? This sounds like the issue with the Intel X3100 when using compiz (xv stops working when not using EXA).

Yes, you are right. That's what I have, a HP laptop with a Intel X3100 graphic card.
Is there a solution for this problem?

Regards,
Gjoko Pargo.

---

### Post by Seq on 2007-11-07
> **zlochko said:**
> Yes, you are right. That's what I have, a HP laptop with a Intel X3100 graphic card.
Is there a solution for this problem?

Regards,
Gjoko Pargo.

I _just _got a new macbook with an x3100 _yesterday night_. Hopefully I'll be able to answer that from experience for you soon.

From what I understand, the solutions are:
1. Don't use Compiz. This should allow xv to work.
2. Switch to EXA instead of XAA. This may have speed-related issues.

---

### Post by zlochko on 2007-11-07
> **Seq said:**
> I _just _got a new macbook with an x3100 _yesterday night_. Hopefully I'll be able to answer that from experience for you soon.

From what I understand, the solutions are:
1. Don't use Compiz. This should allow xv to work.
2. Switch to EXA instead of XAA. This may have speed-related issues.

Thank you very much for your effort in addressing this issue. I will be awaiting your reply.

Thanks again,
Gjoko Pargo.

---

### Post by Seq on 2007-12-03
> **zlochko said:**
> Thank you very much for your effort in addressing this issue. I will be awaiting your reply.

Thanks again,
Gjoko Pargo.

Sorry for not getting back to you. I have been unable to get 3D to be stable at all on my system, at it seems to be a common issue. Sorry I can not be of help.

---

### Post by zlochko on 2007-12-04
> **Seq said:**
> Sorry for not getting back to you. I have been unable to get 3D to be stable at all on my system, at it seems to be a common issue. Sorry I can not be of help.

Never mind Seq. Your effort is appreciated. 
I guess will have to wait for an official package update or something.
:-k

Regards,
Gjoko Pargo.

---

