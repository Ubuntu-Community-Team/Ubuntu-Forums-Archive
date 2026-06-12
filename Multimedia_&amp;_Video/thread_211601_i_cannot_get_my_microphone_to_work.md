---
title: "i cannot get my microphone to work"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by Polygon on 2006-07-08
for some reason my microphone is not working and i cannot figure out how to configure it.

when i go to applications>sound/video>sound recorder, it says "your audio capture settings are invalid, please correct them in your multimedia settings." Well that is specific... now where ARE my multimedia settings

after reading some other posts, they said to run alsamixer in terminal and make sure that microphone and capture are not muted. I made sure capture is not muted, but i do not seem to have "microphone", the only thing i have is line/mic in, and currently thats set to 'mic in"

any suggestions?

---

### Post by Polygon on 2006-07-10
bump!

---

### Post by Alpha1Dash1 on 2006-07-10
Hi Polygon, I had this exact same problem over the weekend & the following solution worked for me. (However, I'm *very* new to Linux:oops: , so there may well be lots of subtle things going on that I don't know about...)

The **Multimedia Systems Selector** thing is already there, but by default you can't see it! Use the Alacart menu editor (Applications|Accessories) to make it visible (it lives in the "preferences" section). Then when you run it (System|Preferences), set the input & output plugins to ALSA.

The **Volume Control** config is done from the Edit|Preferences option of Volume Control itself. Make sure you have the microphone & +20dB boost (if available) ticked, along with the defaults. Then, back in the main pannel, set the mic volume to 100% (Playback tab) & make sure the +20dB switch is ticked (Switches tab).

Two bits of "weirdness" that I've noticed (but that don't seem to cause any probs):
1) Sound Recorder won't let me select anything in the "Record from input box" - it appears to be an un-populated dropdown menu! However, it you hit record, chat into the mic for a bit & then hit stop, then playback, all seems to be working fine.
2) The mic seems to be live 100% of the time and plays back (quite quietly) through the system. This sounds (no pun intended!) as if it would be really annoying, but when using Skype for instance, its really not a problem. 

Hope this is of some help

---

### Post by Polygon on 2006-07-10
i cannot find this "alacart menu editor", so i went to "applications menu editor' under system tools and i looked around and i could not find this "multimedia systems selector".

---

### Post by Alpha1Dash1 on 2006-07-10
Hi again Polygon. Its probably my spelling thats causing the problem here. Sorry (never was any good at French!).

I'm assuming that you are using DD 6.06. I'm not trying to be "smart" in the following, just walking through what I see step by step. If you don't see what I describe, then you'll have to wait for some Guru who knows what's going on to sort you out.

From the Desktop, on my system at least, the following happens:
1) if you click on the "Applications" menu option (top left of screen), you should get a drop down who's first entry is "Accessories".
2) highlighting "Accessories" causes a sub-menu to appear who's first entry is "Alacarte Menu Editor". 

Do you see this?

---

### Post by Polygon on 2006-07-10
i dont, this is what i see (i took a ss of applications editor cause it does not let me take an ss while i have the menu open)

[[IMG]http://img135.imageshack.us/img135/2058/screenshot5vf.th.png[/IMG]](http://img135.imageshack.us/my.php?image=screenshot5vf.png)

are you using kde or kubuntu? if so that would most likely be why, as im using Gnome

---

### Post by Alpha1Dash1 on 2006-07-10
Hi Polygon. Unfortunatley here's where my ignorance comes into play...](*,) 

"are you using kde or kubuntu?"

Gnome (I think).

My install is fresh off a DD6.06 liveCD (i386) and its had one automatic kernal update. I only put it on last Friday after abandoning the AMD64 version I had been running before. It's installed on the 2nd HDD and was reformatted before use (to avoid any hangovers). The main reason for swapping was to get Skype up & running, so the first thing I did was to make sure the  hw was woking... and by the above steps, it did.

Sorry friend, sounds like you need help from someone who actually knows what they are talking about. 

George

<edit>

  What happens it you open a teminal anf type "alacarte"? (no quotes obviously)

</edit>

---

### Post by Polygon on 2006-07-10
i upgraded from breezy so a lot of stuff (like GUI and the application menu) are still the same from breezy unless i changed them myself, so i think it is most likely there in a fresh install but not for an upgrade

thanks for all your help though, ill try and find the command line to open that program you are talking about

---

### Post by fatalGlory on 2006-09-08
Thanks very much Alpha1Dash1,
I followed your instructions and was able to (finally!) get both gnome sound recorder and Audacity to record and playback by changing my output plugin to ALSA and my input plugin to OSS in the Multimedia Systems Selector.  Hope that helps someone else.

---

### Post by serban on 2006-10-07
Hi guys,
I had the same problem - twice !!! I managed to fix it somehow from the Volume Control playing withnthe constrols, etc and it worked. About a week ago it stopped working - i have no idea why (in the mean time I tried eLive with Enlightment - probably that's it) so today I started to play again with the controls. Now it works again. 
I find it strange that in the Capture tab (Applications/Sound & Video/ Volume Control/Capture *tab*)  my Microphone has the microphone off and the Capture is at the minimum level ... and it works.
Anyway, it was about an hour of trial and error and I still can't understand but it works. I think it should be better documented as it happened twice to me and probably it happened to most.
Cheers,
Serban

---

### Post by ulugeyik on 2006-10-14
Hello,

I can do all this in GNOME (Ubuntu Dapper) but not on Xubuntu (Xfce). What is the proper way of doing a "multimedia systems selector" for Xubuntu? I can hear sounds well but no microphone.

---

