---
title: "Joining mp3 files"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by NutMonkey on 2007-01-29
What is the best way to join two mp3's together?  If I remove the ID3 tags, can I just cat them?

---

### Post by kidders on 2007-01-29
Hi there,

Without having tried it myself, you *should* (in theory) be able to "cat" two MP3s together, provided:

[LIST=1]
[*]Like you mentioned, you chop the last 128 bytes off the file that's not going to wind up last. Extensions to the ID tagging schema might cause trouble though.
[*]Both files have exactly the same sample & bit rates. Although sudden changes are technically allowable, not all players are well-enough written!
[/LIST]

Give it a shot and see what happens! Assuming it works for you, you might be able to iron out any kinks by passing the result through an MP3 encoder.

**Edit:** I wonder if, to be safe, you should also scrap any of the appended MP3 preceding the first "0xFF 0xFB".

---

### Post by gamerteck on 2007-01-29
I suggest **Audacity **for all your music editing needs.  You can apt-get for it or search the repos with your package manager.

---

### Post by punx45 on 2007-01-29
i second the audacity plug.  i think i have it on every computer i use at work and home!
audacity will also need the LAME library in order to export files as mp3. details on how to do this are included with audacity.
do also keep in mind that exporting mp3 will compress the file again. you may find the quality degrading.

---

### Post by NutMonkey on 2007-01-29
I used id3v2 command line tool to remove the tags, and cat to join them, and that seems to work without having to re-encode.  At least, Amarok shows the correct time and plays the joined file, which is good enough for me..

---

### Post by kidders on 2007-01-29
Excellent. :-)

---

