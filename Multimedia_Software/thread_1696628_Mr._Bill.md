---
title: "Mr. Bill"
date: 2011-02-27
forum: Multimedia Software
---

### Post by William Cary on 2011-02-27
Greetings, I am kind of new to ubuntu. I love it! 
I am wondering if there is some one I can let in to my PC via the net, to help me with 2 program problems. 
1) A movie player that actually can stream the movies without stopping every 12 seconds to reload?
2) I have a soundblaster Xfi sound card that I cannot get to work on Ubuntu 10.4. It has my midi ins and outs on it so my key board and recording suite is shot. HELP!

If you can help: [EMAIL="billcaree3@yahoo.com"]billcaree3@yahoo.com[/EMAIL]       put at your service in the subject line please.

Thank you
Bill

---

### Post by jeremyjjbrown on 2011-02-27
> **William Cary said:**
> 
1) A movie player that actually can stream the movies without stopping every 12 seconds to reload?


VLC should fit your needs.

search VLC player in the software center or
"sudo apt-get install vlc" in a terminal.

Have fun!

---

### Post by Rasa1111 on 2011-02-27
How about VLC player?
That streams video flawlessly for me.

---

### Post by pafufta503 on 2011-02-27
#1; when you are watching online videos, and it pauses to load, this is called buffering.  whether or not you experience pauses in playback depends entirely on the speed of your internet and the websites server.  youtube, for example, has to meet a very large serverload demand for it's users and is therefore slow even on very fast internet connections.  what i do, is i press play, and then pause the video for a minute or two to allow it to buffer enough video that i do not experience pauses.

#2; any soundcard with MIDI is supported by ALSA.  what is ALSA?  it is the software written to talk to your soundcard.  to get your midi working, please do the following:

a) connect your keyboard to the soundcard and turn it on.
b) go to the ubuntu software center, under the applications menu.
c) search for aconnectgui and install it
d) open aconnect gui (applications -> sound & video) and click on the instrument cable icon.  

you can now connect the midi in/out/thru for your keyboard to any ALSA/midi compatible software (such as rosegarden or AMS).  hope this helps.

---

