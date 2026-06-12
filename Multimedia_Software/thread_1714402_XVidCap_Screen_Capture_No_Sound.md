---
title: "XVidCap Screen Capture No Sound"
date: 2011-03-25
forum: Multimedia Software
---

### Post by baumtopf on 2011-03-25
Hello Ubuntu Users,

I have installed XVidCap Screen Capture. If I record my screen with XVid Cap Screen Capture there is no sound. But if I record with Desktop Recorder there is sound. What is wrong?

Please visit the pictures in the attachment

Regards, Juergen

---

### Post by baumtopf on 2011-03-27
no ideas?
please reply!
Why are there no answers?
What is the prblem?

Regards, Juergen

---

### Post by baumtopf on 2011-03-27
no ideas?
please reply!
Why are there no answers?
What is the problem for answers?

---

### Post by vezolmi on 2011-03-27
Hello: I've just found a solution:
[http://ubuntuforums.org/showpost.php?p=10607591](http://ubuntuforums.org/showpost.php?p=10607591)

---

### Post by baumtopf on 2011-03-31
Hello Ubuntu Users,

There is a new problem now,
after I installed XVidcap again, the play button of XVidCap doesn't function anymore.
I would like to play my records.
If I press the start button, nothing starts
And I don't know why? 
Perhaps my preferences are wrong?
I attached pictures of my preferences again and a video,
which show you the new problem.
Please check these.

[http://www.youtube.com/watch?v=E6uUi5Ko8iE](http://www.youtube.com/watch?v=E6uUi5Ko8iE)

Regards, Juergen

---

### Post by baumtopf on 2011-04-02
Thank you very much vezolmi!

The recording works,

but the play button still not function!

So I have to use XVidCap without the play button.

To fix the play button I have deinstalled XVidCap and reinstalled it again and I deleted the data files of XVidCap. But these tryings resulted in failure.

I press the play button again and again, but nothing happens, no error warning or video play.

So please if you have good ideas, share your ideas with me.

Regards, Juergen

---

### Post by vezolmi on 2011-04-14
Hi, baumtopf:

In Ubuntu 10.04 I have the same problem.

In Linux Mint 10 (based on Ubuntu 10.10) I don't have that problem.

I hadn't notice the problem because I open the video from its location, using Nautilus. If you open Nautilus you'll see the video you have just recorded, with a name like test-0000.mpeg. It's in the home directory ( ~ or /home/username).

To try to get help to solve the problem, I would create a thread for it. I would title it something like:
> xvidcap's play button doesn't work

Regards

---

### Post by vezolmi on 2011-04-15
I have the solution!!

2 options:

a) Install mplayer from Synaptic.

b) Go to preferences (right clicking on the name of the file, for example test-0000.mpeg, and then cliking on Preferences), then to the Commands tab, and then in the "Multi-Frame Capture Commands"' "Playback Command" replace mplayer with totem and click on OK. Then right click again on the name of the file and click on "Save preferences".

---

### Post by baumtopf on 2011-04-16
Hello vezolmi,

thanks for answer.

Please watch my video clip and check it.

this is my current solution for ubuntu 10.10:

[http://www.youtube.com/watch?v=CUJXQ9WJFc4&feature=player_embedded](http://www.youtube.com/watch?v=CUJXQ9WJFc4&feature=player_embedded)

I will test your new solution!

Regards, Juergen

---

### Post by baumtopf on 2011-04-17
Hello ubuntuusers,

vezolmi's solution works:

the start button and the audio recording functions.

Watch the solutions:

[http://www.youtube.com/watch?v=vJC5HArL8QY](http://www.youtube.com/watch?v=vJC5HArL8QY)

best thanks to vezolmi

Regards, Juergen

---

### Post by vezolmi on 2011-04-20
Hello, baumtopf:

I'm glad for you having solved the problem. Thanks for your videos.

Regards

---

### Post by baumtopf on 2011-05-08
Hello again,

here is a new solution video clip:

[URL="http://www.youtube.com/watch?v=UKkTj5xR8nE&feature=related"]
[/URL][http://www.youtube.com/watch?v=kqKZ8wyP9ow]("http://www.youtube.com/watch?v=ZCSJEIkniF8")

---

### Post by baumtopf on 2011-05-10
Hi Ubuntu users,

here another update of my solution xvidcap video:

[http://www.youtube.com/watch?v=kqKZ8wyP9ow]("http://www.youtube.com/watch?v=ZCSJEIkniF8")

---

### Post by knightowl626 on 2011-08-21
Thanks @baumtopf. Great video tutorial.

---

### Post by kesten on 2011-12-30
I tried following the instructions by vezolmi but ran into problems on ubuntu 11.10 with the mods for x86-64 architecture (original was 32 bit solution).  Anybody had luck with it?  I'm not sure if getlibs is compatible with software center.

when i try to install the default xvidcap player
  	 	 	 	 	 	   Software Center:
 In order to install GNome Mplayer these items must be removed
 

 libavcodec-dev
 libav codec library
 libavutil51
 mp3 encoding libmp3lame0:i386
 libopenjpeg2:i386
 libvo-amrwbenc0:i386
 libx264-116:i386
 libxvidcore4:i386
 xvidcap:i386
  
I also don't seem to have vlc player working anymore.

Can anybody who has got it working in 11.10 give an update?

kesten

---

### Post by Tim Legg on 2012-01-05
> **vezolmi said:**
> Hello: I've just found a solution:
[http://ubuntuforums.org/showpost.php?p=10607591](http://ubuntuforums.org/showpost.php?p=10607591)


I have run into this problem as well.  The problem I see is that xvidcap is searching for sound input from /dev/dsp and that device doesn't exist.  I spent an hour or so trying to find the device for the microphone.  Surely this must be documented somewhere, but I can't find it.  I can't squeeze the device name from the gnome audio applet, I suppose they don't want to bore us with the under-the-hood stuff.  Once that device name is set up correctly, I don't think these gyrations that have to be done each time xvidcap is started would need to be done anymore.

I haven't tried a USB microphone yet, like the Shure x2u/Shure 5700.  It worked for me as a solution when I had a weird built-in mic issue a couple years ago.

(The sound device needs much better documentation, Ubuntu seems to use /dev/snd/ but there is a vacuum of knowledge for this topic since I spotted a few unanswered threads asking about /dev/snd)

---

