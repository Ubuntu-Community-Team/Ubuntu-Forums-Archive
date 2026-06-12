---
title: "[SOLVED] audio input connector doesn't work"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by maxhoward on 2008-02-02
I can't seem to get any input through the audio input connector (the blue one on the back of the PC).  I have a Dell Dimension XPS 400 and am running Ubuntu 7.10. I am sending the output of my stereo amp through an RCA cable to Y-cable to the blue input connector.  The Device Manager shows a STAC 92xx Analog ALSA Capture Device present.  Do I have to configure this?  Can I send the input directly to the Speakers  so I can hear what's going on?  Is there any other way to test this input?

This seems kind of fundamental but I need some help please.

---

### Post by maxhoward on 2008-02-02
More info and questions.  

I opened "alsamixer" in the terminal and think I have the correct settings: ie line-in is selected and the volume is all the way up for the speakers (a CD comes through loud and clear).

I then tried to use Audacity since everybody seems to recommend it but when I press the record button, I get the message "error opening sound device".

So how do I find that device and set its preferences or whatever?

I read part of Brian's Sunshine Club Tutorial about copying LPs to CDs but his screen shots of  Audacity do not match what I have.

So I am really stuck.  Thanks for any help.

---

### Post by maxhoward on 2008-02-02
Problem solved.  I found a tutorial on Audacity in one of the Ubuntu references and got everything working.

---

### Post by pmac0001 on 2008-02-03
maxhoward, can you post a link to the tutorial?

---

### Post by maxhoward on 2008-02-03
I'll try to put the link here.

[http://audacityteam.org/wiki/index.php?title=Transferring_tapes_and_records_to_computer_or_CD]("http://audacityteam.org/wiki/index.php?title=Transferring_tapes_and_records_to_computer_or_CD")

This link seems to work.

I realized I had to Open Audacity, then Edit > Preferences then set both Record and Playback  devices to my sound card.  That solved my whole problem.

---

