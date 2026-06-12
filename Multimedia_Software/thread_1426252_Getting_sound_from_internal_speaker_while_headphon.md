---
title: "Getting sound from internal speaker while headphones are plugged in"
date: 2010-03-10
forum: Multimedia Software
---

### Post by charlescarroll1 on 2010-03-10
I recently bought a Compaq Presario CQ60 from my work. The Ubuntu install surprisingly went very smoothly. The only problem is that when I am playing an kind of audio, I will still get sound from the internal speakers even after I've plugged in a pair of headphones into the audio jack. I get sound from both the headphones and internal speakers. I tried playing around with the sound preferences but it didn't get me anywhere and google isn't being of any help.

Does anyone have any suggestions?

---

### Post by agnes on 2010-03-10
This once did it for me:
Putting the line
*options snd-hda-intel model=hp*
in the file /etc/modprobe.d/alsa-base.conf.
Perhaps you should replace* hp* with *compaq*, also see  [this thread]("http://ubuntuforums.org/showthread.php?t=314383")

---

### Post by sloty on 2010-03-10
Install GNOME Alsa Mixer from the software centre. There you will be able to select "jack sense" to fix this.

---

### Post by Cooter2543 on 2010-03-22
I have the same problem on the same model.
There is no "jack sense" option that I can see anywhere in Gnome Alsa Mixer, and I've tried adding many different lines to the alsa-base.conf file with no luck. If I find a solution I will post it here.

---

### Post by wilsontp on 2010-03-28
I have the same problem with my computer.
 
But if I restart with the headphones plugged in, then it only outputs to the headphone plugs.  If I want my internal speakers to work again, I have to unplug my headphones, and then restart.
 
I have ubuntu 9.10 on an hp tx2525nr.
 
This is aggrivating, I would think JackSense would be integrated into most ubuntu sound drivers (alsa and oss).

---

### Post by lidex on 2010-03-28
Have you tried - in gnome alsamixer - checking "edit>soundcard properties"? Jack sense may need to be enabled there.

---

### Post by wilsontp on 2010-03-28
no i dont even have an alsamixer in gnome.
how do i get that?

---

### Post by lidex on 2010-03-28
In a terminal:
```
sudo apt-get install gnome-alsamixer
```

"Applications>Accessories>Terminal"
Copy and paste command, press enter. 
Enter your user password when prompted.

---

### Post by wilsontp on 2010-03-28
actually i got my sound to work right (headphone sor speakers, not both) but now banshee won't run.
 
what the hell is going on?

---

### Post by lidex on 2010-03-28
That sounds like another issue. Try uninstalling then reinstalling it.

---

### Post by wilsontp on 2010-03-28
tried that, and it won't work.
really strange, it literally just STOPPED WORKING.
 
im having issues getting gnome to do what i need it to, should i consider switching to KDE?

---

### Post by lidex on 2010-03-28
What exactly is going on? Does it startup at all or not have sound? Try running it from a terminal and post the error messages. I don't use it but I assume the command is:
```
banshee
```

---

### Post by wilsontp on 2010-03-28
it doesnt do anything even from the terminal
what does that mean, and why is it all of a sudden like this?

---

### Post by lidex on 2010-03-28
That may not be the right command. Go to the banshee entry in your menu, right-click on it and select "add this launcher to desktop". Right-click on that launcher and select properties. Copy and paste the entry in the "command" field into the terminal and press enter.

---

### Post by wilsontp on 2010-03-28
It just sits there.  doesn't hang (freeze) but doesn't do anything.

---

### Post by Speakstofei on 2010-05-03
[LEFT]I'm in the same boat as Cooper & Charles: Operating on a Compaq CQ60.  Just upgraded to 10.04 hoping the new release would have a fix.  Sadly, it does not.  I've checked several other threads for an answer, yet to no avail, I've found none. ALSA mixers, alsabase.conf "Jack Sense" adaptations have all failed. Has anyone found an answer for this laptop?
[/LEFT]

---

### Post by the-rosbif on 2010-05-03
I think this is kinda common with HP/Compaq machines. I had the same thing on my laptop for a while in Windows and it seemed to go away by itself. I fear it was a hardware issue that will probably return when the thing is out of warranty!

For some people, it appears to be software. Check these out.

[http://ubuntuforums.org/showthread.php?t=1381413](http://ubuntuforums.org/showthread.php?t=1381413)

[http://www.pchelpforum.com/sound-etc/87653-headphones-do-not-stop-onboard-sound.html](http://www.pchelpforum.com/sound-etc/87653-headphones-do-not-stop-onboard-sound.html)

[http://h30434.www3.hp.com/t5/Notebook-PC-Sound-and-Audio/headphone-plugged-does-not-silent-laptop-speakers/m-p/16231](http://h30434.www3.hp.com/t5/Notebook-PC-Sound-and-Audio/headphone-plugged-does-not-silent-laptop-speakers/m-p/16231)

---

### Post by Speakstofei on 2010-05-03
It seems to be that the Codec: Conexant 5067 isn't supported with Alsa.  I've updated to the snapshot drivers and still cannot find the proper setting to work in the alsa-base.conf file.  This is going to be extremely annoying if I try to use this on a plane or anywhere else in public for that matter.

---

