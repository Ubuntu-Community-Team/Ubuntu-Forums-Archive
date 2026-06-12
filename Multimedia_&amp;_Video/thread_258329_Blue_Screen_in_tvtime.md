---
title: "Blue Screen in tvtime"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by scratched on 2006-09-15
For some unknown reason, tvtime is not displaying the picture on my tv tuner. All I see is a blue screen (sometimes it's black). Sound works totally fine, it's only video that gives me a problem. 

Any ideas on how I might be able to go about fixing this? 


I've tried searching the forums and although a similar problem was posted, the solution (a simple restart) did not work for me. I've even googled the problem and haven't found a solution that will work for me (all of the solutions on google have to do with resolving driver issues that don't affect me)](*,) 



I just got my tuner this week and tvtime worked great the first time I ran it:D  (even better than the windows software that came with the card:cool: ), until I closed the program. The next time I opened it, I got a screen of blue.:frown: 

I've tried xawtv and the picture works, but it is small and not as nice looking as tvtime, and I can't seem to make the screen much bigger.

---

### Post by scratched on 2006-09-16
I just had a thought...

I had to add module options to the driver saa7134 for the card to be recognized. Before I added the options tvtime displayed the same blue screen. Is it possible that modprobe.d is somehow ignoring these options?

Does anyone know how I might be able to investigate this?

I'm using a shell script I found in the forums to get sound to work. I never really took the time to figure out exactly what it does (I just copy and pasted the code) but what it does is it allows the sound for the tvtuner to work in tvtime. The way I understand how it works, is it bypasses the saa7134 driver's sound output (or something like that) and just sends the sound directly to the sound card when tvtime is running. I'm guessing this could be why only sound is working.


I'm a relative newbie when it comes to this stuff so I'm completely clueless as to what the problem is:-\"

---

### Post by bigfatgeek on 2007-02-18
I'm having the exact same issue - I see no one ever replied, but did you ever get it figured out?

---

### Post by bigfatgeek on 2007-02-21
I can uninstall, delete all traces, re-install, and it works perfect. Log out and then back in... blue screen. Perfect sound. All the channels are receiving great 'audio only', but no video. Only that damn blue screen. Installed with Synaptic, apt-get, aptitude, all same results. I can unload - reload the modules.. no avail. I hate to say this, it doesn't really make any sense how this can be, but it only happened since I went back to XFCE with version 4.4. Hmmm,  idea. I'll pop Fluxbox or something back on and try that. Don't know what else to do. I am baffled. Never never ever ever again will I invest before checking Linux compatibility.

---

### Post by bigfatgeek on 2007-02-21
Well - no joy on that experiment... Window manager macht nix. 
Tried Fluxbox, Ice, Wmaker... all same results. 
On the plus side it takes only a couple mionutes to remove and reinstall, but it just ain't right to have to do that. If the card worked before, it should work now. 
In case anyone is interested...
ATI TV Wonder 200 (TV Wonder Pro is printed on card)
Conexant decoder - CX23883-19
Using "options cx88xx card=4 tuner=44" in /etc/modprobe.d/cx88xx 
US Cable / NTSC

---

### Post by david_2001 on 2007-02-22
Just passing.  Does the information [COLOR="SandyBrown"][here]("http://icculus.org/~jcspray/wintv_cx88.html")[/COLOR] help (scroll down to "Configuring tvtime)?

---

### Post by bigfatgeek on 2007-02-22
Thanks David_2001...  I thought I had good Google foo, but I didn't think of Googling CX88. 
I did check it out. The driver (CX8800) is already installed, but I followed all the other instructions as if I had just installed the driver fresh. There are a couple modules I don't even know if I need, but I tried it anyway. Lo and behold... TVTime came back on without the uninstall/install routine that I had to do before. Too good to be true? I logged out and back in, it was still working. Wow. I did a reboot, still works. That is a definite improvement. A reboot in the past always meant TVTime would give me the blue screen. 

I don't know if it will last - we'll see. I must admit my hardware is also suspect. I just got sudo authority to purchase a new desktop in the next few weeks, so I'll probably ditch this card anyway and turn this old PC into a backup/storage box. Check out the screen shot to see why I think the hardware is suspect. Ever seen that? Comes and goes every few minutes. Line noise? I dunno. The distortion I can tune out - the letter garbling is what I mean. Gives me an idea... would be cool to run a terminal over a TV image. Useless but cool. 

Anyway - a big thanks for a big step forward.

jj

---

### Post by david_2001 on 2007-02-23
> **bigfatgeek said:**
> I don't know if it will last - we'll see. I must admit my hardware is also suspect. I just got sudo authority to purchase a new desktop in the next few weeks, so I'll probably ditch this card anyway and turn this old PC into a backup/storage box. Check out the screen shot to see why I think the hardware is suspect. Ever seen that? Comes and goes every few minutes. Line noise? I dunno. The distortion I can tune out - the letter garbling is what I mean. Gives me an idea... would be cool to run a terminal over a TV image. Useless but cool. 

If tvtime works following a reboot then my guess would be that the blue screen problem is fixed :cool:.  As to the letter garble in the screenshot, I've never seen anything like that before and wouldn't know where to start diagnosing the problem.

---

### Post by bigfatgeek on 2007-02-23
Blue screen is back now. It worked last night. It worked after reboot. It worked this morning. I leave my PC on. Came home form work and it's a blue screen again. This is not the "No Signal" blue screen, the signal is there, sound anyway, and I can change stations. Maybe it's weak - I don't know. I have a signal booster somewhere in the garage - I may try that. Maybe the card is overheating. Maybe I'll take it out and pound it with a hammer. Yeah - that might make me feel the best. Getting a new PC anyway - may as well get a new TV card too.
Thanks - consider this thread finished. I have never ever given up on a problem on my PC before - but it's illogical to continue. Thanks for the help - Live long and prosper.

---

### Post by Ergo on 2007-02-23
I had the exact same problem with Xawtv years ago with SuSE linux.  The answer back then was to edit the configuration file in the hidden /home/user/.xawtv directory.  For whatever reason, xawtv worked the first time, but after logging out and back in, the program had a black screen with audio.  The few times I managed to accidentally get it working, it was in PAL instead of NTSC so it was garbbled.  Without having studied this program and card more closely, I would have to say "Look at a config file!"  If it were drivers, the silly thing would not work from the start.  Once the program runs one time, it writes a config file to reference back to when it runs again.  Hope this helps and good luck.

---

### Post by bigfatgeek on 2007-02-23
I thought of the config file first too. There's really not much there. I think it's hardware. 

I pulled every card out of my 3.5 year old motherboard, cleaned the clogged fins on my Athlon 2200. Blew out the fans, powersupply, slots, reseated the memory, reseated all the cards, changed the order of the cards to maximize open space for the TV card. And of course it works again. I'm thinking it's hardware. On again, off again. For what it's worth, here's the cfg file.  Pretty benign. 

<?xml version="1.0"?>
<!DOCTYPE tvtime PUBLIC "-//tvtime//DTD tvtime 1.0//EN" "http://tvtime.sourceforge.net/DTD/tvtime1.dtd">
<tvtime xmlns="http://tvtime.sourceforge.net/DTD/">
  <option name="Channel" value="4"/>
  <option name="NTSCCableMode" value="Nominal"/>
  <option name="DefaultBrightness" value="40"/>
  <option name="DefaultContrast" value="37"/>
  <option name="DefaultSaturation" value="45"/>
  <option name="DefaultHue" value="49"/>
  <option name="PrevChannel" value="5"/>
  <option name="FramerateMode" value="0"/>
  <option name="OverScan" value="2.0"/>
  <option name="CheckForSignal" value="1"/>
  <option name="AudioBoost" value="-1"/>
  <option name="AlwaysOnTop" value="0"/>
  <option name="QuietScreenshots" value="0"/>
  <option name="UnmuteVolume" value="17219"/>
  <option name="Muted" value="0"/>
  <option name="V4LInput" value="0"/>
  <option name="AudioMode" value="stereo"/>
  <option name="PalDKMode" value="0"/>
<option name="WideScreen" value="0"/><option name="ShowCC" value="1"/><option name="FullScreen" value="0"/></tvtime>

------end file----------------

Note: 
V4LInput line - 0=Television 1=Composite 2=S-Video 
I use Television input (cable) I have not tried the other two methods. Next time it goes blue I'll pop a GameCube on the composite and see if it's blue too. That will at least tell me whether it's just cable or all inputs.

---

