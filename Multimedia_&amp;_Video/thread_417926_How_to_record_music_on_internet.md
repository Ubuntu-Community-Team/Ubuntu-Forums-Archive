---
title: "How to record music on internet?"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by paker on 2007-04-22
I asked this question in Absolute Beginner forum, but  no reply there.
I found a web site that has many mid files listed. I can hear the music well. But I want to record it and eventually burn a CD. The author allows non-commercial use with proper credit. Please help me. By the way, here is the site: [http://www.tc.umn.edu/~sorem002/misc_midi.html](http://www.tc.umn.edu/~sorem002/misc_midi.html)
Many thanks.

---

### Post by Spr0k3t on 2007-04-22
You should be able to right click and save the midi files you want to convert over to wave/compressed audio.  One of the best applications I can think of off the top my head is Audacity, but then I'm not sure if that will convert midi over to raw-aiff or not... been a while since I've used it.  Nevertheless, that should get you started on the right path to convert the audio.  Wether Audacity meets your needs, please make sure you post your findings.

---

### Post by firefly2442 on 2007-04-22
You might also want to look into a program called LAME.  I bet that has an option to convert .mid to MP3 or whatever you want to use.

---

### Post by Spr0k3t on 2007-04-22
> **firefly2442 said:**
> You might also want to look into a program called LAME.  I bet that has an option to convert .mid to MP3 or whatever you want to use.

Nods to that.  LAME is one of the best encoders you can find that's not proprietary format or for commercial use only.   There are LAME packages in the repos, so just search for them as needed.  Not sure if it has a conversion from MIDI or not, but if it does it will produce a very clean sound... make sure you use VBR if you do MP3 encoding.

---

### Post by paker on 2007-04-22
Thank you for the suggestions.
1) Right clicking on the file and "saving the link as" downloaded the mid file to Desktop. I opened Audacity,  imported the mid file, and exported as wav file (that's what the program recommends.). The mid file on Desktop is 33K, but the wav file is only 44 bytes. What's happening?

2) I could not play the mid file with Audacity. Some output thingy not setup correctly. So I iinstalled Kmid and Amarok. Neither could play the mid file. I mean no sound at all. I am completely lost.

3) I have lame already installed according to synaptic manager. I don't know what else to do.

My goal is to burn a music CD from the mid files I downloaded.
Thank you.

---

### Post by Spr0k3t on 2007-04-22
I just did a deep check through Audacity and could not find MIDI support.  I'll look further to see if there is a way to convert the MIDI to something else.

---

### Post by firefly2442 on 2007-04-23
Open up Audacity, then go to the Project menu

Then go down to Import Midi.

Maybe that will work?

---

### Post by paker on 2007-04-23
Thanks for replies. Problem solved.  Someone at Beginner's Forum gave me the answer: "timidity myfile.mid -Ow" outputs myfile.wav. Audacity imports midi file and outputs wav and mp3 files. Somehow Audacity did not make proper wav or mp3 files on my computer. It must have something to do with setting.

---

### Post by ubromtoo on 2007-05-28
Tried everything...... no luck.

  Audacity shows the file , but won't play it audibly, won't export it as wav or mp3.

  tried many solutions.... any more ideas?


   when I type "timidity" in the terminal, just get the EULA.

---

### Post by shen-an-doah on 2007-05-28
> **ubromtoo said:**
> Tried everything...... no luck.

  Audacity shows the file , but won't play it audibly, won't export it as wav or mp3.

  tried many solutions.... any more ideas?


   when I type "timidity" in the terminal, just get the EULA.

Did you try "Timidity myfile.mid -Ow" as the guy above you said?

---

