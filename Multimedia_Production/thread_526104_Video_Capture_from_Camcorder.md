---
title: "Video Capture from Camcorder"
date: 2007-08-15
forum: Multimedia Production
---

### Post by OsakaWilson on 2007-08-15
Is anyone capturing video from a camcorder and editing it? I'm beginning to believe that video capture is not practical in Ubuntu. It doesn't recognize my camera or my capture card. Following direction intended to make it work have been a dead end. Is this not worth pursuing? 

My camera is a Panasonic AG-DVC30 and my Capture Card is an ADVC110. I'm using Feisty 64. 

I have Kino installed. I also supposedly have dvgrab installed, but see no evidence of it.

---

### Post by dad311 on 2007-08-15
Im using a Hitachi camera with a ADVC110.  Works great, could not be happier.

What exact issues are you having?

---

### Post by OsakaWilson on 2007-08-15
As far as I can tell, the system doesn't recognize it at all. Does your system give some indication that it is connected when you power it up? If so, what kind of indication do you get?

Also, what applications do you use it with?

---

### Post by OsakaWilson on 2007-08-15
I tested it on a Windows machine and it works fine. However, when I plugged another firewire device into the plugs on my Ubuntu machine, it didn't work, so it appears that Ubuntu is not acknowledging my firwire plugs. That is an entirely different problem.

---

### Post by OsakaWilson on 2007-08-15
I installed a new firewire plug and it shows up on the Device Manager, but still nothing happens.

---

### Post by dad311 on 2007-08-15
Its strange, but I dont see any messages in "/var/log/messsages" file when I power on the camera or the ADC box.  

However, when I start Kino and press play on the camera, the image shows up in Kino.

Have you tested your firewire card with any other devices?  Maybe its not supported by Ubuntu.

---

### Post by OsakaWilson on 2007-08-15
I just installed a new firewire card with three plugs, because the others weren't working. I tested them and they work with another device. I ran the TV into ADVC and got no indication of Ubuntu or Kino acknowledging the signal. Grasping at straws, I plugged my camera directly into the new firewire plug in the computer. 

Suddenly my camera starts playing the signal that is coming from the TV!

So, the ADVC is working and sending a signal into the computer, which is then being sent out of the computer to my camera.

It seems the only thing not working is Ubuntu and Kino.

(I tried the video tutorial for capturing video with Kino, but midway through the video, he says to "set a rule" without explaining how, which rendered the rest of the tutorial useless to me.)

---

### Post by dad311 on 2007-08-15
> **OsakaWilson said:**
> I just installed a new firewire card with three plugs, because the others weren't working. I tested them and they work with another device. I ran the TV into ADVC and got no indication of Ubuntu or Kino acknowledging the signal. Grasping at straws, I plugged my camera directly into the new firewire plug in the computer. 

Suddenly my camera starts playing the signal that is coming from the TV!

So, the ADVC is working and sending a signal into the computer, which is then being sent out of the computer to my camera.

It seems the only thing not working is Ubuntu and Kino.

(I tried the video tutorial for capturing video with Kino, but midway through the video, he says to "set a rule" without explaining how, which rendered the rest of the tutorial useless to me.)

I think is normal not to recieve any indication that the firewire is active.  I dont see any messages and mine works fine.

Im assuming that your camera is not in play back mode because your recieving video from the tv.  Forgive me for asking, but have you tried your camera in play back mode.  I believe the signal is what enables the ADVC box.

---

### Post by OsakaWilson on 2007-08-16
Yeah. I've had it in playback mode. I was just messing around trying anything which is why it was able to recieve the TV signal. 

I guess Ubuntu is just not ready for editing video yet. Thanks for trying to help.

---

### Post by Statik on 2007-10-20
osaka, I'm editing video in Ubuntu presently, captured over firewire into Kino.

If you want to see if dvgrab is installed, just open a terminal window and type:
```
dvgrab --version
```
that should tell you if it is working.

Second, make sure your camera is connected to the computer using a Firewire cable, and turned onto the PLAYBACK function.

Now, fire up Kino and go to the capture tab. If the buttons are greyed out, try going to the setup screens and clicking on the IEE1394 tab. You should see your camera there in the dropdown. If its not selected, select it. I think there's an option around there for preview while capturing as well. You'll probably want that too.

Now click the rewind button and see what happens. If you have control of the camera, you are well on your way. Then hit capture when you are back far enough and you should start seeing video captured.

Statik

---

### Post by theacoustician on 2007-10-20
I do a ton of firewire capture and video editing in Ubuntu.  I can tell you the #1 problem is that permissions aren't set up properly on the firewire port.  Open a terminal and with video being fed to the firewire port, type "dvgrab" and it should just start capping files in raw DV encapsulated in .avi in the folder where you launched the command.  If you get an error, its probably because the permissions on your firewire port aren't properly set.  Go to /dev/ and type "sudo chmod 777 ____" with the blank being every entry in the /dev/ folder that says 1394.  Most people have video1394, dv1394, and raw1394.  Go back to your /home/ directory and run the dvgrab command again.  Should work brilliantly now.  Once you know dvgrab is working, try going back and using Kino again.  I tihnk you'll find it works now.

---

### Post by maruhana on 2007-10-28
I need help I trying to capture video from HD Camera Sony HDR fx 1e
I'm using Ubuntu Studio 7.10 does not recognize camera. Can ubuntu capture HD videos?

---

