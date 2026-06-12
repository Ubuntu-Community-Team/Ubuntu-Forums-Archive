---
title: "no microphone..."
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by kpm on 2006-09-02
Hello,
I can't seem to get any sound input working on my freshly installed and updated Ubuntu Dapper 6.06.  I am runing it on an IBM Thinkpad and the multimedia system selector shows the 'Default Output Plugin' as
Output: Autodetect
Pileline: autoaudiosink.
The 'Default Input Plugin' is
Input: ALSA - Advanced Linux Sound Architecture
Pipeline: alsasrc

I would like to be able to communicate with Ekiga or Skype or any other voip, but can't until I get this microphone working.  The microphone is not defective as I have tested it on another computer and this computer use to have Windows on it and the microphone worked then as well, so I guess that tells me that the problem is software related not hardware.

Does anyone have any suggestions??

Thanks.

---

### Post by ispmarin on 2006-09-02
Open some mixer software (kmix for kde, or the sound icon on the tray) and try to see if the mic is muted, or if your board has a mic boost.

---

### Post by kpm on 2006-09-02
thanks!  that was embarrasingly easy...
i tried fixing it using the alsamixer earlier and really messed things up...
all I had to do was double click on the sound icon in the tray and enable the dang microphone...

---

### Post by ispmarin on 2006-09-03
Yeah, I had done this myself some times... ;-)

---

### Post by Flavian on 2006-09-05
Hi guys!
I don't know if I am too dumb, but I tried to get skype running on Dapper, now I updated to the latest alsa driver, which works flawlessly, but I thought it might as well change something in the sound panel - but it did not.

My problem is that I don't see the microphone under "capture" and if I start sound "Sound Recorder" it says:
"Your audio capture settings are invalid. Please correct them in the Multimedia settings."

My system is a Laptop and has a built in microphone!
If it doesn't work another way, I would have an external mic to plug in as well.

Here are two screenshots of my sound mixer

---

### Post by Flavian on 2006-09-05
Can noone help me??
This is really urgent!
Thanks
Flo

---

### Post by kpm on 2006-09-08
On the panel, go to Applications > Accesories > Alacarte Menu Editor 
then in the left hand side of the Alacarte Editor, go to 'System' then 'Preferences' (its near the bottom) and then in the right hand side of the editor, make sure that 'Multimedia Systems Selector' has a check mark in the box.
Next, on the panel, go to System > Preferences > Multimedia System Selector then in the Audio tab, try setting the Default Output and Input plugin to ALSA...
That is how I got my microphone recognized... but I still can't get skype to work so have switched to Ekiga and am tyring to convince friend to switch to Gizmoproject rather than use Skype... it seems to be more linux friendly...
good luck.

---

### Post by Flavian on 2006-09-08
Thanks!
It was already set to Alsa! - But if I hit Test on the "input device" it says:
> 
ALSA - Advanced Linux Sound Architecture: Could not open resource for reading.


If I set it to OSS, and start the sound Recorder, the sound recoder starts without any error, but if I want to RECORD something, I don't hear it.

Does anyone know a solution for that?

---

### Post by stairwayoflight on 2006-09-13
hi,

i have the same problem, opening sound recorder:
```
Your audio capture settings are invalid. Please correct them in the Multimedia settings.
```
when i open "multimedia system selector" (i think it is a gstreamer config app?) and try switching input plugin to OSS, i get:
```
OSS - Open Sound System: Unable to open device /dev/dsp for recording: Device or resource busy
```
when i try to switch to alsa, i get:
```
ALSA - Advanced Linux Sound Architecture: Resource busy or not available.
```
i am running an "up to date" ubuntu 6.06 dapper with backports, and i used automatix, i don't know if that changes gstreamer or anything else though it does grab codecs.
lspci gives:
```
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
```
lsmod gives:
```
snd_via82xx            28824  5
```
so i am sure i have the right driver... even in the sound dialog from the tray icon i have clicked preferences, then enabled just about everything that wasn't visibly controlled, and fiddled with unmuting/selecting different things and the results are the same.

---

### Post by stairwayoflight on 2006-09-13
come to think of it.. it was windows so it was some time ago, but i remember having a win app 'silent bob' give me problems. it had worked for me on other machines, it records a 2 min or so 'buffer' of sound to the hard drive in the back ground while you surf, listen to internet radio, etc, then you can hear something, decide you want it, and click 'record' and you have all the audio after you pressed record + the 2 min before. well on this particular box, for some reason the saved files had no audio in them on playback.

which makes me believe maybe there is a problem with my sound card. this was a returned emachines pc :-) is this possible? or should i try another route to a fix?

---

### Post by Flavian on 2006-09-13
I would be glad for any ideas as well... getting the mic to work would be important for me, since I am gonna go study at university and then I could phone home or my friends for free over the Inet :/

Thanks in advance for any suggestion or help!
Flo

---

### Post by kpm on 2006-09-13
Not sure if this will work for you, but besure all of the sound processes are stopped before you attempt to change multimedia settings, try the following at the command line:
sudo kill all esd
sudo kill all osd

---

### Post by kpm on 2006-09-13
> **stairwayoflight said:**
> come to think of it.. it was windows so it was some time ago, but i remember having a win app 'silent bob' give me problems. it had worked for me on other machines, it records a 2 min or so 'buffer' of sound to the hard drive in the back ground while you surf, listen to internet radio, etc, then you can hear something, decide you want it, and click 'record' and you have all the audio after you pressed record + the 2 min before. well on this particular box, for some reason the saved files had no audio in them on playback.

which makes me believe maybe there is a problem with my sound card. this was a returned emachines pc :-) is this possible? or should i try another route to a fix?

Not sure if this will work for you, but besure all of the sound processes are stopped before you attempt to change multimedia settings, try the following at the command line:
sudo kill all esd
sudo kill all osd

---

### Post by Flavian on 2006-09-19
Guys, seriously.
Can't someone help me? I don't think that noone in here knows a solution for my problem! - I am not as much as a pro on Linux as a lot of others here.

I am highly thinking about switching to MacOSX, why?
Well it is true Linux is opensource and therefore free a 100% but what does it help if I have to fiddle with everything (well it is fun, I aggree, and I liked to do things on my own just to explore the system and I have gained a lot of knowledge through that, BUT) LITTLE things like that just make me mad... if stupid little things like the microphone and skype telephony does not work on ubuntu, why should I not switch to OSX? - With OSX one thing is for sure, it JUST WORKS!
I do not talk about Windows because I don't at all consider it to be a good solution, in fact it is crap. And because it is crap I switched to Ubuntu.
It is a really great distro, but as I said when little things like that don't work it makes me wish I had a Mac!

Anyone got a solution though?!

---

### Post by motin on 2006-09-20
> **Flavian said:**
> Guys, seriously.
Can't someone help me? I don't think that noone in here knows a solution for my problem! - I am not as much as a pro on Linux as a lot of others here.

I am highly thinking about switching to MacOSX, why?
Well it is true Linux is opensource and therefore free a 100% but what does it help if I have to fiddle with everything (well it is fun, I aggree, and I liked to do things on my own just to explore the system and I have gained a lot of knowledge through that, BUT) LITTLE things like that just make me mad... if stupid little things like the microphone and skype telephony does not work on ubuntu, why should I not switch to OSX? - With OSX one thing is for sure, it JUST WORKS!
I do not talk about Windows because I don't at all consider it to be a good solution, in fact it is crap. And because it is crap I switched to Ubuntu.
It is a really great distro, but as I said when little things like that don't work it makes me wish I had a Mac!

Anyone got a solution though?!

You mean you want to switch to a system that comes pre-installed? I mean - otherwise go by a OS X cd rom and install it on your computer and get your microphone up. 

Or, keep free by buying from [http://system76.com](http://system76.com) or similar. Microphone will be gauranteed to work then.

---

### Post by kpm on 2006-09-20
> **Flavian said:**
> ...thinking about switching to MacOSX... wish I had a Mac!

If you do buy a Mac, I would warn you off the new macbooks, I bought one and it ran great for about a week... then it had boot up problems, then it had screen flicker problems, then the logic board was replaced, then the screen died, then the inverter board was replaced, then the sound died, then they put in the 'revised logic board and heat sink', then the dvd rom ceased to play dvd's, then the whole system refused to boot... And, after all that, Apples has finally caved in and is sending me a new one, though, from the sounds of the techs who worked on mine, they are not at all happy with the engineering of the new MacBooks (mine is/was a 13inch MacBook).  I bought the thing in June, and have only used it a few times, the rest of the time, it was waiting for parts.  Now I have to ship it off to Apple and they will replace it but they don't have anything to replace it with since they are not shipping any more of those lemon-apples... so now I hope in a couple weeks they will get one made that is not such a lemon and send it to me... then I can see what all the fuss is about with these supposed uber computers that 'just work'...  Thankfully my old thinkpad only needed a new harddrive, now it has been running like a champ with Ubuntu (recording issues aside) the whole time the crazy Mac was crapping, crashing, or in the shop...

---

### Post by xjgnsdof on 2007-11-23
Let's stay on track here. I have the same error message, though everything works fine except for Sound Recorder. When I open that app to record something, I get the invalid-multimedia-settings error message among all the other ones that Flavian also gets.

---

