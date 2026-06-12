---
title: "Hauppauge Nova-T 500 problems with MythTV"
date: 2009-03-11
forum: Mythbuntu
---

### Post by avoa on 2009-03-11
I can watch TV on Kaffeine without any problems, but on MythTV I can see only some channels, picture and sound is fragmented. 

Some channels on MythTV give message:* You should have gotten a channel lock by now. You can continue to wait for a signal*... Some channels show video, but picture is weak and sound is fragmented.
It seems, that TV signal is weak (or too strong?) on MythTV. When I unplug TV antenna cable when MythTV is on, then poor video continues to play. I'm living about 2 kilometers from TV mast.
If MythTV cannot play TV correctly, then how all channels are displayed well on Kaffeine and Me TV? 
I'm using Hauppauge WinTV Nova-T 500 dual tuner card (DVB-T) on Ubuntu Rel. 8.10 Kernel 2.6.27.
What might be the difference between Kaffeine and MythTV? Can it be MythTV setup problem? What and where should be changed to get MythTV working?
BTW. MythTV finds all possible channels by channels scan.

Any help or hint is appreciated.

Avo

---

### Post by freak42 on 2009-03-12
not exactly your card (rather an usb stick) however this might help:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29)

please feedback if it does or doesn't help .., maybe something else on that page might help aswell..

hth

---

### Post by avoa on 2009-03-12
Thanks freak42, but this option is already set. If I can see Kaffeine without problems, I guess, something is wrong with MythTV setup. Any ideas?

Avo

---

### Post by utar on 2009-03-12
> **avoa said:**
> I can watch TV on Kaffeine without any problems, but on MythTV I can see only some channels, picture and sound is fragmented. 

Some channels on MythTV give message:* You should have gotten a channel lock by now. You can continue to wait for a signal*... Some channels show video, but picture is weak and sound is fragmented.
It seems, that TV signal is weak (or too strong?) on MythTV. When I unplug TV antenna cable when MythTV is on, then poor video continues to play. I'm living about 2 kilometers from TV mast.
If MythTV cannot play TV correctly, then how all channels are displayed well on Kaffeine and Me TV? 
I'm using Hauppauge WinTV Nova-T 500 dual tuner card (DVB-T) on Ubuntu Rel. 8.10 Kernel 2.6.27.
What might be the difference between Kaffeine and MythTV? Can it be MythTV setup problem? What and where should be changed to get MythTV working?
BTW. MythTV finds all possible channels by channels scan.

Any help or hint is appreciated.

Avo


I'm confused about how the video can carry on playing (for more then the few seconds which are buffered) when you pull out the aerial?  What signal strength does Myth report on the channels that do work?

Freka42's suggestion about checking you have the LNA enabled is a good one, although this doesn't explain why Kaffine works.  Basically if the card is working under Kaffine with no issues it should work under Myth.

I would delete the cards completely from mythbackend and re run the scan in case something went wrong the first time round.

Edit: I would also check you have the right frequency table set for your location in mythbackend (US, Europe etc) and the right TV format.

---

### Post by avoa on 2009-03-12
I'm also confused, how TV continues playing without antenna, this is true with MythTV, however signal level drops after some 5-10 seconds and then picture slowly disappears. With Kaffeine picture stops immediately after unplugging antenna.
I deleted all DVB cards and then run scan again. MythTV founds all possible channels.
On MythTV picture is still dirty and sound is fragmented like with weak signal. So, the situation have not changed.
About signal strenght MythTV says: Signal 71% | BE 0 | (LAM) Lock

How to clear all MythTV configurations? Should I uninstall MythTV completely and install again?

Thanks in advance.

---

### Post by utar on 2009-03-12
Did you check the frequency table / tv format setting in mythbackend to ensure these are set up right?

---

### Post by avoa on 2009-03-12
Yes, I have checked frequency table / tv format setting. I'm using PAL and europa-east. Our broadcast is coming in MPEG4 format, but this shouldn't be a problem, this is question about codec translating TV stream. May-be I'm using wrong codec? I don't know, how to check it, I'm quite new in Linux world.

---

### Post by utar on 2009-03-12
You could check your myth logs to see if those give any clues.

---

### Post by JoeFlennigan on 2009-04-01
Hello, did you find a solution? I've got the same problem. Until last night, everything worked fine. I dind't change anything. Now  I get this message "You should have gotten a channel lock by now. You can continue to wait for a signal, or you can change the cannels with up or down, change video source (y), inputs (s) etc."

I tried to search one more time for channels - MythTV found the same channels as I had before but they still don't work.


P.S.: The only thing I can remeber is that I have activated the option to optimize MythTV automatically. Could this be a reason?

---

### Post by nickrout on 2009-04-01
> **avoa said:**
> I'm also confused, how TV continues playing without antenna, this is true with MythTV, however signal level drops after some 5-10 seconds and then picture slowly disappears. With Kaffeine picture stops immediately after unplugging antenna.


I suspect mythtv is buffering a lot more than kaffeine. mythtbackend records even livetv to disk and then mythfrontend plays it back, there is often quite a few seconds of buffered data there.

---

### Post by nickrout on 2009-04-01
> **JoeFlennigan said:**
> Hello, did you find a solution? I've got the same problem. Until last night, everything worked fine. I dind't change anything. Now  I get this message "You should have gotten a channel lock by now. You can continue to wait for a signal, or you can change the cannels with up or down, change video source (y), inputs (s) etc."

I tried to search one more time for channels - MythTV found the same channels as I had before but they still don't work.


P.S.: The only thing I can remeber is that I have activated the option to optimize MythTV automatically. Could this be a reason?

Could be that your channel definitions were slightly screwed and "fixing" the database wrecked them completely? I am just guessing of course.

Have you tried rebooting? The drivers may have crashed in some subtle way.

Are you sure the amplifier is activated?

---

