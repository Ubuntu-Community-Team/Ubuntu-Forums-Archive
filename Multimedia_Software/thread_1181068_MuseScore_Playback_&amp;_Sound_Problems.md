---
title: "MuseScore Playback &amp; Sound Problems"
date: 2009-06-07
forum: Multimedia Software
---

### Post by Alan Jordan on 2009-06-07
I installed the Application 'MuseScore' via Add/Remove Applications in Ubuntu Linux 9.04 (Jaunty), but am unable to playback the Sample Score provided with the Application; in particular although the Start Sequencer Play Button works, there is **NO** advancing cursor to show what is being played. I have started the Application from a Terminal Window and discovered that:-

1. With the standard I/O configuration (Internal Synthesizer & default Alsa Audio), the initialisation of the Alsa Driver, Audio Driver and Sequencer fail, because the ALSA Audio Driver doesn't support mmap-based access.

2. Selecting the alternative Midi Output I/O configuration, Permission is denied to set the ticks in /dev/rtc, and hence the I/O cannot start, and the Sequencer initialisation fails. If I start the Application with Root privileges, the Application starts without errors, and there is now an advancing cursor to show what is being played, but there is **NO** sound, which ever Midi Port I select.

I was very surprised to find these problems with a standard Ubuntu Application, but as a virtual Linux novice I have no idea what to try now; does anyone have any ideas?

---

### Post by SolRebel on 2009-06-07
I too am expiericing similar difficulties with MuseScore. Any help the community can provide would be greatly appreciated!

---

### Post by SolRebel on 2009-06-09
[http://www.musescore.org/en/handbook/installation](http://www.musescore.org/en/handbook/installation)

After doing a workaround with JACK server(I used OSS, ALSA still doesn't work for me), I've found MuseScore to be working wonderfully. Hope this helps you!

---

### Post by u3000 on 2009-11-25
all i had to do was change alsa-driver from default to hw:0... hope that helps for you too.

---

### Post by johngreth on 2010-04-03
I solved this problem on my [blog]("http://johngreth.com/blog/?p=332#332.2"). This is the important part:

1. Open MuseScore and go to Edit->Preferences…->I/O
2. Select “Port Audio” and click Ok.
3. Restart MuseScore and go back to Edit->Preferences…->I/O
4. Select “ALSA” and “Default” under “Port Audio”
5. Click Ok and restart MuseScore one more time. The sounds should work now.

Hope this helps.

---

