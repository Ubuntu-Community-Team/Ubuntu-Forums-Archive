---
title: "Choppy video and high Xorg CPU% in Lucid"
date: 2010-06-16
forum: Multimedia Software
---

### Post by Joe Eye on 2010-06-16
I have been experiencing issues with choppy video playback since upgrading from Karmic to Lucid. If I play an .flv or .avi using VLC it may look fine at native resolution but as I enlarge the playback window the the video gets increasingly choppy and may freeze for seconds at a time if I go full screen. It seems even worse if I do the same using Movie Player. Going fullscreen with the same files was a cinch before the upgrade. Playback of streaming video online also seems affected.

I tried running "top" in the terminal and played a few videos with VLC and as I enlarged the playback window saw the CPU% for Xorg shot up dramatically. When a low res (320 x 240) file was played at native resolution Xorg was at about 35% and shot up to about 75-80% when it reached the point playback became noticeably choppy. It stays around that level as I expand the window further still but of course the video gets worse as I go. 

lspci | grep VGA gives me:
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

There is no /etc/X11/xorg.conf :confused: and I have xserver-xorg-video-openchrome, which I understand is there by default.

Any thoughts?

---

### Post by Joe Eye on 2010-07-28
Just to update (and bump) I was able to create /etc/X11/xorg.conf but I'm still living with this.

---

### Post by abelta on 2010-08-10
I'm having a similar problem since I upgraded to Lucid too (I think). Playing a Matrioshka video is unbearable now and I'm worried because the CPU temperature rises above 100 Cª which can't be good either.

---

### Post by mikewhatever on 2010-08-10
I've never used VIA products, and so apologies if the info is wrong. A quick [google search]("http://lmgtfy.com/?q=ubutnu+via+unichrome") revealed that there is a presumably proprietary driver for Unichrome cards that might provide better graphical performance.
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)

---

### Post by infamous-online on 2010-08-15
I'm experiencing this issue as well, but with playing video on my box. I'm using Ubuntu 64 bit Lucid, and I have 8 gigs of mem, and AMD Quad core processor @ 1.8 GHZ, and built ATI 3200 HD graphics card of course on Win 7 I don't experience this at all, just on Ubuntu, why? I know it's has to be a setting(s) on mplayer that's causing this. Watching vids on Ubuntu apparently gets the CPU hot because it will shut down Mplayer, so something has to be up, any ideas?

---

### Post by no2498 on 2010-08-15
this comes from the cheese help file faq's

*

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.
    
5.2.&#8195;I have a Mac with iSight and a ATI graphics card, and the colors are weird.


      This is a problem with the ATI graphics card, though there is a work around.
      Change the video-output to custom and insert the following: "ffmpegcolorspace !
      video/x-raw-yuv,format=(fourcc)YV12 ! ffmpegcolorspace ! xvimagesink".
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and select custom from the drop down menu.
    
5.3.&#8195;My webcam works with gstreamer, but does not work with Cheese. What's wrong?


      Using "gstreamer-properties" mentioned in the above question, try changing from
      xvimagesink to ximagesink or vice-versa. If this still does not work run "cheese --verbose" on
      the command line and copy the logging into a bug report in our 
      
      bug tracker.
    
5.4.&#8195;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?


      See if your webcam works when testing it in "gstreamer-properties". If it works
      there, but not in Cheese, please file a bug report in our 
      
      bug tracker.
    
5.5.&#8195;Where does Cheese store my photos?


      Your photos are stored in ~/.gnome2/cheese/media. You can also save
      them to an alternate location from within Cheese. Please see the help
      topic titled "Saving photos and videos to an alternate location" for
      information on this.
    
5.6.&#8195;My Quickcam Express doesn't work with Cheese...


      or gstreamer, and I see errors like "Not enough buffers. We got 1, we
      want at least 2" in the Cheese output. With driver "qc-usb".
    


      Try running "qcset /dev/video0 compat=dblbuf" to enable double buffer
      compatibility mode, then restart Cheese
    
5.7.&#8195;Which cameras are supported


      Cheese uses gstreamer for video grabbing. So in principle Cheese supports 
      any camera that works with GStreamer. In principle that should be any camera
      which support video4linux or video4linux2.

---

### Post by Joe Eye on 2010-08-16
> **infamous-online said:**
> I'm experiencing this issue as well, but with playing video on my box. I'm using Ubuntu 64 bit Lucid, and I have 8 gigs of mem, and AMD Quad core processor @ 1.8 GHZ, and built ATI 3200 HD graphics card of course on Win 7 I don't experience this at all, just on Ubuntu, why? I know it's has to be a setting(s) on mplayer that's causing this. Watching vids on Ubuntu apparently gets the CPU hot because it will shut down Mplayer, so something has to be up, any ideas?

I didn't mention it before because I'm using VLC, but if I try to play a video in MPlayer it shuts down right away. I don't know if the same thing you're experiencing but it got me thinking it might be related to the problem at hand. I'm thinking I might try the Unichrome driver suggestion. I'll let you all know how it works out.

---

### Post by infamous-online on 2010-08-17
> **Joe Eye said:**
> I didn't mention it before because I'm using VLC, but if I try to play a video in MPlayer it shuts down right away. I don't know if the same thing you're experiencing but it got me thinking it might be related to the problem at hand. I'm thinking I might try the Unichrome driver suggestion. I'll let you all know how it works out.

Well lucky me it doesn't shutdown right away, but let's I'm watching a DVD and before the movie is complete, it shuts down. What's strange is before it never did this, then out the blue it just started this. So I checked my system monitor to see what the load on the system is and funny enough my memory is through the roof. I know using 64 bit uses more mem but whenever 40% ram is used I think that's too high and there has to be a cause for it. Right now I am using SMplayer and the mem usage is low and it plays my DVD's without shutting the program down, however I do want to find out the cause though.

---

