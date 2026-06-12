---
title: "Record Seq24 song"
date: 2008-02-21
forum: Multimedia Production
---

### Post by Roanoke on 2008-02-21
So, after overcoming some obstacles, I now have a small song in seq24. But I have a strange problem: I don't know how to record it. Yes, the answer is probably simpler than I can imagine, but I still don't know.

---

### Post by darsu on 2008-02-22
Seq24 does not produce sound, it merely sends MIDI note data to other programs, such as a synthesizer, which then generate the sounds. It's the synth you should record.

---

### Post by Roanoke on 2008-02-22
Hmm... This is sort of a problem. You see, I have a loop that plays on hydrogen, and about 5 other loops that play on zynaddsubfx. How should I go about doing this?

---

### Post by darsu on 2008-02-23
Here's how I would do it, using JACK.

1. Open QJackCtl and start JACK.
2. Open Ardour, create a new session and make two stereo tracks (via Session -> Add track/bus)
3. In QJackCtl: open the connections window, patch Hydrogen's two output channels to Ardour's Audio1/in1 and Audio1/in2, and ZynAddSubFX's outputs to Audio2/in1 and Audio2/in2 resp.
4. In Ardour: Click the 'r' button in the button group to the left of each track to enable the tracks for recording.
5. In Ardour, hit record and play; in Seq24, hit play.
6. (After recording) in Ardour: open the mixer window and route all tracks to "Master out"; create a mixdown through Session -> Export -> Export session to audiofile.

---

### Post by Roanoke on 2008-02-23
Doesn't work for me. Here are my settings:

---

### Post by darsu on 2008-02-24
This works:
[img]http://img441.imageshack.us/img441/9360/qjackctlnt0.jpg[/img]

---

### Post by nlz on 2008-02-24
if you want to learn more about professional recording/mixing/editing, do this short but comprehensive tutorial on Ardour 2.. I also includes Jack stuff..
[http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/)

---

### Post by Roanoke on 2008-02-24
I don't have an 'audio1/in2' port.

---

### Post by darsu on 2008-02-24
Looks like you created a mono track. There should be a stereo option in the track creation dialog.

---

### Post by Roanoke on 2008-02-24
Not that I can see.

---

### Post by darsu on 2008-02-25
It seems Ubuntu 7.04 is stuck with Ardour version 0.99, and since 7.10 has version 2.05 with a differing interface which I've never seen, I'm afraid I can't advise you with it. Sorry.

---

### Post by Roanoke on 2008-02-25
Anyone else?

---

### Post by Roanoke on 2008-03-01
Wait, I managed to get it working, but it still doesn't record.

---

### Post by darsu on 2008-03-02
That record button to the right of the "Audio 2" text field - is it on or off? If it's off, the track isn't activated for recording.

---

### Post by Roanoke on 2008-03-02
I'm pretty sure it was on, and the green bar was recorded.

---

### Post by nlz on 2008-03-03
a few posts ago i advised you to look into the ardour tutorial, did you do that?

If you did it, you've probably read that you have to select the input of the track in the track fader bar (activate with SHIFT + E ), press input and select seq24 output.

---

### Post by Roanoke on 2008-03-03
Seq24 doesn't even show.

---

### Post by nlz on 2008-03-04
did you set Jack as  audio driver in Seq ? Can you play a song when Jack is fired up?

---

### Post by Roanoke on 2008-03-15
How do I set audio drivers in seq24?
If by "playing" you mean send midi data to zasfx and have it emit sound, yes.

---

### Post by nlz on 2008-03-17
there is transport for seq24 as i can read here

[http://www.filter24.org/seq24/road.html](http://www.filter24.org/seq24/road.html)

you can find some answers or post a question about it here

[https://lists.sourceforge.net/lists/listinfo/seq24-users](https://lists.sourceforge.net/lists/listinfo/seq24-users)

here is also some other documentation

[http://www.filter24.org/seq24/doc.html](http://www.filter24.org/seq24/doc.html)

this is a nice walkthrough

[http://www.linuxjournal.com/article/8304](http://www.linuxjournal.com/article/8304)

good luck

PS I haven't used seq24 but there is a lot of info obtainable through google as you can see above. Maybe give it a try if you can't find the answer in the above links.

---

### Post by nlz on 2008-03-17
i just installed seq24 and it's really to easy! Fire up JACK with qjackctl and start the engine, fire up seq24.

go to file > options > JACK Sync and select 'JACK transport'.

There you go! everything working with jack.

---

### Post by Roanoke on 2008-03-18
> **nlz said:**
> a few posts ago i advised you to look into the ardour tutorial, did you do that?

If you did it, you've probably read that you have to select the input of the track in the track fader bar (activate with SHIFT + E ), press input and select seq24 output.
I only see in 1+2, and no seq24 in the edit window.

---

