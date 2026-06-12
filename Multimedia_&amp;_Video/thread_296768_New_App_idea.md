---
title: "New App idea"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by Spenser_Gilliland on 2006-11-10
I have an idea for a new app.  

Create a visual representation  of I/O app interaction.

I made this image to represent the idea. Its far from a GUI but expresses my idea.  

This would set linux apart from every other piece of editing software.  Reason being is that you will never get the hundreds of companies who make the I/O software to conform to the rules of this project and yet they wont release there source to others so that they may fix it to work.  

Rules:
-Programs should set there in's and outs according to the config file with options for infinitive in's and outs.   
-Programs should be allowed to edit the config file.  
-The file should be user refreshable or auto-refreshable.  
-The program should have multiple places where you can zoom in order to better understand where data is going.  
-Anything should be allowed to become an input or an output.  Outputs direct to file.  
-Maybe a small viewer program that could be placed inline to see what is happening at that specific place.  
-It would almost be like a living CAD environment.

Purpose:
-Allows us to create general file format converters that are completely independent of there associated editors.  
-Make on screen diagnositics alot easier.
Makes it alot easier for the common analog guy to switch to digital.
-Iono add it. 

Future:
After finishing the basic core of this program
-Realtime: accomplished through client server
-Programs to adjust formats based on processsor usage and/or memory.
-Hardware devices(mixers) for altering the sound.  Start a DIY mixing board thing.  (I'm a first year EE right now prob be a senior before this is done)

---

### Post by ciscosurfer on 2006-11-10
Sounds good to me!

---

### Post by nalmeth on 2006-11-12
Can you explain what this would do that qjackctl does not? I don't think I quite grasp the concept. 

Is it a visualization of the hardware/software audio routing? For instance, you would see that a device is plugged into line-in, but you could use this program to actually control the software connection. 

I'm kind of intrigued with what you might mean by outputting directly to file, and by the CAD reference aswell.

All in all it sounds like some cool ideas, like making protocols unique to linux, setting it apart, and so on. Visualization is the bees-knees

---

### Post by Spenser_Gilliland on 2006-11-12
I actually looked at qjackctl after writing this and like it alot, but I'd like it to go a step further so that the whole system is easily viewable would help with quicker mixer engineer coordination?  What i mean is that a person could walk in look at this diagram say ok and start using the controllers without close to any orientation by the audio/video engineer.  Maybe even make the devices outside the computer manually inputable on the diagram.  This would help organization.    

The CAD refrence was related to how a electrical cad diagram shows relations.  I think my picture didnt make it thats why its alil confusing.  I reattached it.  

You could set this diagram as one of your desktop backgrounds so that you could just switch over too it in order to see what is goin where if you get confused.

when i used the word converters i meant to use the word transcoders.  

Also making this a client server program would allow multiple people to work on the same workplace at the same time.  Therby eliminating the one computer problem.

Another idea which is a ways away is being able to have two seperate keyboards and mice inputing to the same computer and being able to have two people on the same desktop so that you could lend a hand in a live production situation.  This would eliminate the need for multiple instances of a program across seperate computers to update each other while in heavy use.

---

### Post by std on 2006-11-13
Well, this does sound a lot like what qjackctl already does (based on JACK, indeed), but with a polished GUI and a few added features.

I do like the idea of making everything easier to view, understand and manipulate. Qjackctl has a rather awful interface right now. However, afaik, qjacktl is aimed at being a complete way to control the JACK server.

I would suggest you to consider submitting this batch of ideas (along with the diagram) to the qjackctl team -- although I know little about how they manage their program and what plans they have for future. Having yet another app which does a lot of what qjackctl does would be a considerable effort (only in order to achieve what qjackctl has already achieved).

Either way, good luck with your ideas ;)

---

### Post by dolson on 2006-11-13
What about getting together with the patchage guys and working on it if it doesn't do what you want?

[img]http://om-synth.nongnu.org/patchage_screenshot.png[/img]

---

### Post by Spenser_Gilliland on 2006-11-14
didnt know that exists but wow that does look better than qjackctl.  I'm definantly going to look into it.

---

### Post by VividHazE on 2006-11-16
While working for a technical documentation company I had to create a user manual for the BBC, who actually operate a very user friendly program that is similair to this to create their final rendered output image for our TV's. I wasn't allowed to take anything away with me or I would have shown you.  Good idea. :)

---

