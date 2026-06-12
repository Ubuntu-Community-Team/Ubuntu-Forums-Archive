---
title: "No real-time voice changers!!?"
date: 2010-09-17
forum: Multimedia Software
---

### Post by ubutu on 2010-09-17
Anyone care to explain why Linux doesn't have real-time voice changers? Or why the Windows version don't even works with wine?

---

### Post by Joe of loath on 2010-09-17
There is most probably one out there. I'm pretty sure you could work one out using JACK and some effects in BEAST.

---

### Post by ubutu on 2010-09-17
There isn't, I've checked. 

What does it take to motivate Linux coders to actually write applications that people want. We'll even pay for it just to avoid going back to Windows.

LOL....I was half-expecting someone to say I don't need one and to get rid of "The Windows Mind Set".

---

### Post by dv3500ea on 2010-09-17
There are several reasons why certain types of program don't have a linux alternative:
[LIST=1]
[*]Too few people want/need the features provided (this makes it less likely that programmers want/need the functionality and Linux programmers tend to program things that they use).
[*]It is a difficult thing to program.
[*]No one has paid for a Linux version to be created.
[*]The task is too specific and perhaps there is a more general program that can do what the specific program would do with the enough skill.
[/LIST]

---

### Post by cchhrriiss121212 on 2010-09-17
> **ubutu said:**
> There isn't, I've checked. 
There are plenty of realtime effects available, and as mentioned above they will work with jack, which is the sound server designed for realtime audio work. 
You don't mention what you actually want to change, but these programs should have you covered:
Jack rack
Calf plugins
Rakarrack

---

### Post by tgalati4 on 2010-09-17
You would have to play around a bit, but sox can probably do it.

sudo apt-get install sox

sox pitch -100 inputfile.wav outputfile.wav

This will reduce pitch by one semitone and preserve tempo.  You can use linux piping tools to try this in realtime.

Although I don't have it working yet, it seems possible:

from man sox:


       -p, --sox-pipe
              This can be used in place of an output filename to specify that the SoX command should be used  as  in  input  pipe  to
              another SoX command.  For example, the command:
                play "|sox -n -p synth 2" "|sox -n -p synth 2 tremolo 10" stat
              plays two &#8216;files&#8217; in succession, each with different effects.

              -p is in fact an alias for &#8216;-t sox -&#8217;.

       -d, --default-device
              This  can  be  used  in  place of an input or output filename to specify that the default audio device (if one has been
              built into SoX) is to be used.  This is akin to invoking rec or play (as described above).

       -n, --null
              This can be used in place of an input or output filename to specify that a &#8216;null file&#8217; is to be used.  Note that  here,
              &#8216;null  file&#8217;  refers  to  a  SoX-specific mechanism and is not related to any operating-system mechanism with a similar
              name.

              Using a null file to input audio is equivalent to using a normal  audio  file  that  contains  an  infinite  amount  of
              silence,  and  as  such is not generally useful unless used with an effect that specifies a finite time length (such as
              trim or synth).

              Using a null file to output audio amounts to discarding the audio and  is  useful  mainly  with  effects  that  produce
              information about the audio instead of affecting it (such as noiseprof or stat).

              The  sampling rate associated with a null file is by default 48 kHz, but, as with a normal file, this can be overridden
              if desired using command-line format options (see below).

Edit:

This works!  Although there is a slight delay.  You might want to use headphones:

play "|rec -d pitch -200"

---

### Post by transmogrifox on 2010-09-18
What do you really mean by "voice changer"?

I know the great wealth of plugins (LADSPA, DSSI...) have all the possible signal processing covered even though it may not be all packaged together as a "voice changer" program.

Do you mean something that does pitch bending, gender bending, vocoding?  Do you mean something that makes you sound like a monster?

Explain what ways, specifically, you want to change the voice and maybe somebody can help suggest a combination of tools that will do the job.

Adding to what is mentioned above, people who program applications for Linux usually aren't idealists who have made it their life work to create an "equal" to every Windows or Mac program.  Usually it is somebody who has a personal interest in the program and chooses to share it...or a corporation who has a use for the software, and chooses to share it. 

It's a bit rude when invited to a person's house if you made a comment like, "What? You don't keep soda in the fridge for guests?  Jeez, go get me some soda!  I can't believe you don't have a soda for me."  Likewise here :D  

How much money do you have?  Will you pay me $85USD an hour to code a voice changer for you?  I think I could probably give you a beta version in a few weeks with several thousand dollars ;)

---

### Post by checoimg on 2011-02-23
I would like t o have all kind of voice effects including sounding like a monmster. LOL and u r right transmogrifox

---

### Post by colinnashonline on 2011-07-15
I'm interested to find out what's available in the gender bending type voice changers - I use secondlife a lot and sometimes it would be cool to change the voice as well as the avatar....

---

### Post by xxxlam on 2011-10-26
Real time voice changing software is interesting. I've been searching this for a while in W1nd0wZ and I came up with AV Voice Changer (proprietary) and MorphVOX Junior (free). Sadly, both has no versions for Linux.

I hope to create one using java(?) by converting the voice input to a DataInputStream then manipulate the bits (put some bits then shift left or right, according to frequency). After it, get the DataOutputStream then make it a sound once again. Theoretically, I think it is possible. Practically, I do not know how to do it.

Any ideas?

---

### Post by patryk77 on 2012-01-27
Sorry about the necroposting, I just wanted to point out there is in fact a pitch changer available for Linux, as there has been since 2008:

[http://distrho.sourceforge.net/ports.html](http://distrho.sourceforge.net/ports.html)

Check out Juce Pitcher.

As for going and making your own, you should look into the SoundTouch library:
[http://www.surina.net/soundtouch/](http://www.surina.net/soundtouch/)

Hope this helps anyone, as Google led me here.

---

### Post by starfyredragon on 2013-02-25
> **patryk77 said:**
> Sorry about the necroposting, I just wanted to point out there is in fact a pitch changer available for Linux, as there has been since 2008:

[http://distrho.sourceforge.net/ports.html](http://distrho.sourceforge.net/ports.html)

Check out Juce Pitcher.

As for going and making your own, you should look into the SoundTouch library:
[http://www.surina.net/soundtouch/](http://www.surina.net/soundtouch/)

Hope this helps anyone, as Google led me here.

Let's make a tradition of this thread being necroposted! YAY! Anyway, FYI, your link no longer works, and I can't find the pitch changer under that name.

---

### Post by ubuntu27 on 2013-02-26
[http://distrho.sourceforge.net/ports.**php**]("http://distrho.sourceforge.net/ports.php")

[http://www.surina.net/soundtouch/](http://www.surina.net/soundtouch/)

---

### Post by codemaniac on 2013-02-26
Old thread closed.

---

