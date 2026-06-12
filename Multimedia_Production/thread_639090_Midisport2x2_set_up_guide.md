---
title: "Midisport2x2 set up guide?"
date: 2007-12-12
forum: Multimedia Production
---

### Post by nixi on 2007-12-12
Hello!

I am looking for a good method for setting up my Midisport2x2 under Gutsy so that I can play QSynth, or the like, with my piano.  

Under Feisty I used to follow a guide at [http://ubuntuforums.org/showthread.php?t=96506](http://ubuntuforums.org/showthread.php?t=96506), but it seemed incomplete, or out-dated even, for I always ended up having to load the firmware manually through the terminal after each system start. 

Is there a better way? 

Thanks! 

Regards, N

---

### Post by deadgobby on 2007-12-13
If it is the nice USB one. Just have it plug in the USB and have the keyboard on at boot up. The midi sport should have a flashing LED showing that it is all go. Next is to install ZynSubbFX, and after that install Jack Control. Both can be found in Synaptic. This is to test the link and Zyn is best to do this with. 
  Right now I am in a middle of a move and my stuff is at the other place.  So bear with me. When Jack control is open click on the connect button. Then click on the midi tab. Now make a link.
See Screen shot and play away. Sorry so short, but  ice on the trees and the lights are flickering.
Gobby
PS the Midi should have the midisport name and link it up to the soft Synth

---

### Post by nixi on 2007-12-13
Thanks, but how can I get that lamp on my Midisport2x2 to start flashing? 

In Feisty I got it flashing by manually loading the firmware (i.e. by pasting the command into the terminal). But now when I use Gutsy I don't even get that far: for after checking the USB numbers assigned to the Midisport (now they are 002/003) I paste the following command (according to the previous guide) into the terminal: 

fxload -I /etc/firmware/ezusbmidi2x2.ihx -D /proc/bus/usb/002/003


But I get the following reply: "No such file or directory". There is nothing under   /proc/usb/usb anymore, and the lamp on my Midisport2x2 remains dead. 

Is there another way to load the firmware?

---

### Post by deadgobby on 2007-12-13
You should not need firmware any more with Gusty version of Ubie. Older versions, yes you do. It should detect it at the usb port. Did you boot up the computer with the midisport plugged in and into your midi device? Is any of the LEDs on the midi sport working? I wish I could be more hellp, but my midi sport is packed up....

---

### Post by deadgobby on 2007-12-14
I am going to go and dig out my midi sport and help you out. It may be a couple of days. Yet, you could DL the live CD version of Studio 64.
[http://www.64studio.com/](http://www.64studio.com/)
 It should detect it right off the bat.
 All so see this link. Oh crap I forgot I book marked that page. It is a really good how to how to set it up running what you are running.
[http://ubuntuforums.org/showthread.php?t=96506&highlight=midisport+uno](http://ubuntuforums.org/showthread.php?t=96506&highlight=midisport+uno)
Gobby

---

