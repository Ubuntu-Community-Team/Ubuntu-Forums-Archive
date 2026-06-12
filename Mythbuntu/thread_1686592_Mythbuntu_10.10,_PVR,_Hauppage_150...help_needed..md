---
title: "Mythbuntu 10.10, PVR, Hauppage 150...help needed."
date: 2011-02-12
forum: Mythbuntu
---

### Post by MrMosier on 2011-02-12
I just installed Mythbuntu on my HP a1113w (3.0ghz single core, 1.5gb ram, 1tb hd, intel 915 graphics), and I cannot get the tv tuner to work in Myth. I have the coaxial connection coming from my DirecTV receiver (and I change channels on it), the only channel I set up was 3 (for the receiver), and I can then go into VLC and choose PVR and get a not so pretty picture and clear sound. I did set up the tuner as a MPEG card (ivtv) and install the ivtv driver and software. In Myth frontend, I choose Live TV, and it goes back to the menu. I have looked through everything I can find, and I cannot find a solution to this issue. I had everything set up with an Asus My Cinema 3100, but I could not get the sound to work at all (the picture was gorgeous, though). Any help would be appreciated. I am not at the machine right now, but I will post the frontend and backend logs if that will help once I get back home.

---

### Post by MrMosier on 2011-02-12
[http://mythbuntu.pastebin.com/RqxXWMrW](http://mythbuntu.pastebin.com/RqxXWMrW)
These are all of the logs from this system. Any ideas?

---

### Post by nickrout on 2011-02-13
> **MrMosier said:**
> [http://mythbuntu.pastebin.com/RqxXWMrW](http://mythbuntu.pastebin.com/RqxXWMrW)
These are all of the logs from this system. Any ideas?

There is too much there to read.

Have you been through every step of the setup in mythtv-setup?  ie did you setup a capture card, then a video source, then connect the capture card to a video source, then set up channels?

Did you choose the pvr to be a v4l card of an mpeg2 ivtv card? It should be the latter.

---

### Post by MrMosier on 2011-02-15
I thought so...I setup the card as a mpeg card (using the ivtv drivers), set up a video source (the coax connection), then I manually added channel 3 (it would not detect). I really am at a loss...and to top it all off, as I booted it up last night, vlc shows a crystal clear picture (so everything should work). REALLY irritating...

---

### Post by nickrout on 2011-02-15
> **MrMosier said:**
> I thought so...I setup the card as a mpeg card (using the ivtv drivers), set up a video source (the coax connection), then I manually added channel 3 (it would not detect). I really am at a loss...and to top it all off, as I booted it up last night, vlc shows a crystal clear picture (so everything should work). REALLY irritating...

When you say the coax connection what exactly do you mean? Is it the composite connection? The s-video connection? Or the aerial (RF) connection?

---

### Post by MrMosier on 2011-02-15
Aerial (rf) connection.

---

### Post by nickrout on 2011-02-15
That will give the worst possible result, and be hardest to set up. The preference in terms of quality are s-video then composite then RF.

Does your STB offer any other options?

---

### Post by MrMosier on 2011-02-16
Unfortunately, that is what I have to use.

---

### Post by nickrout on 2011-02-16
> **MrMosier said:**
> Unfortunately, that is what I have to use.

I have never used RF in on a pvr card before. Perhaps you need to set the frequency in the tuning section.

---

### Post by wirepuller134 on 2011-02-17
Giving a little info on our setup, just to clarify it works, and is not that hard to setup on rf.  This set up has been running now for 5 years. It sounds like you aren't using a defined frequency table (IE: schedules direct or some other service) and need to setup the frequency table by hand as already stated in an earlier post.

OK we use Mythdora.....but our set up is has follows.

Incoming cable to our myth server:

69 directv tuners: each set to one channel. 
6 combiners bringing all channels down to one cable.
The one cable supplies 12 buildings through amplifiers so fourth with all channels.  Yes we manage the media center for a large apartment complex. 

Our myth server setup:

Our set up for our televisions is one backend/front-end with 9 tuners connected through a splitter to this one cable.  We only use the RF connection.  These cards are 4 pvr500 and 1 pvr150 for the remote.   We then have 2 other front-ends in house.  The only issue we had with going to 12.24 was IRQ assignment.  The OS kept changing the order of the cards on bootup messing with settings.

Capture cards are set up as mpeg ivtv, video source is set up from schedules direct. input connections are all set to tuner 1.

---

