---
title: "pod, sooperlooper, audacity"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by capsid on 2006-09-17
I was messing around and used Ubuntu to make this:
[http://applecoremedia.org/capsid/guitarloops.ogg]("http://applecoremedia.org/capsid/guitarloops.ogg")
I'm not expecting you to care about the content, I mainly just wanted to talk about the workflow.  I dialed in a sound on the POD, which is a great device if you want to ditch your amps and cut down the size of your workspace.  By using it with subwoofers, you can get a much fuller range than a normal guitar amp gets.  Anyway, I used sooperlooper to record a loop, then used the multiply function to extend the loop eight times, then added a few tracks of overdubbing.  Then you can add or remove your tracks by pressing undo/redo.     

I ran the output of one computer to another which recorded the line input in Audacity.  By sending it with a crappy cable, i got a bad hiss, but Audacity's noise reduction worked very well (although it's always preferrable to just get a clean recording).  I also applied a default phaser sound and used the default fade in/fade outs...      

Live looping tools are my favorite!!! You can do some fun stuff by sending Seq24's MIDI clock to sooperlooper, and clicking "sync" and "psync", and quantizing to the "cycle". That way you can guarantee your loops will be on beat.    

So I had to record on a separate computer again because Audacity doesnt like to be opened after Jack Control.  Anybody know a way around this??

---

### Post by huwshimi on 2006-09-17
You should be able to record on the same computer but not with Audacity (I haven't used Sooperlooper but I'm assuming it uses jack). I hope I get this right...

First make sure you have Qjackctl and Ardour installed. Then open Ardour and make a new track. Next go to Qjackctl and go to connect. Disconnect the outputs of Sooperlooper and reconnect them to the inputs of Ardour. Then start recording in Ardour and press play in Sooperlooper. Then hopefully you should be recording the track to a .wav file.

I hope that works (I'm on a different computer so I had to write that from memory).

Cheers.

---

### Post by dolson on 2006-09-18
You can optionally compile the development version of Audacity, which supports JACK via PortAudio, or use ReZound, or some other JACK-supporting editor.

ardour is the best there is though, so it's worth learning.

---

