---
title: "S-video"
date: 2008-11-17
forum: Multimedia Software
---

### Post by johnlundy on 2008-11-17
I was wondering if anyone knows a good way to get an S-VIDEO cord to work through Ubuntu. I recently wiped my harddrive and am now running 100% Ubuntu on my computer, and I'd really like to be able to watch movies on the TV through the S-VIDEO.

I've also only been on Ubuntu for a couple of days, so please consider me an extreme linux-noob. Descriptive help is much appreciated.

I'm running Intrepid on a Compaq Presario V2000, with an ATI Radion Xpress 200M graphics card, and I don't know what other system specs you even need from me.

Thanks in advance.

---

### Post by cotcot on 2008-11-17
I can connect with S-video to my hauppauge PVR 150. 
Here is an extract of my file where I make notes of how I install things. It is a collage of instruction I have found on the net.
> Install VLC (synaptic). Use "File>Open Capture Device" and then click the "PVR" tab to get to your PVR settings.* Set "Norm" to "NTSC" (if you're in the USA, or "PAL" if Europe), and if you're using Channel 3 for the VCR output, then set the frequency to 61250.* Then click the "Advanced" button to open the rest of the needed settings.
What video input is my PVR150 currently using
As you probably already know, the PVR150 can capture off it's build in TV tuner (input 0), a SVIDEO source (input 1), or a COMPOSITE video source (input 2). You can always see what video input the PVR-150 is currently using by running the command:
v4l2-ctl -I
In which case you will probably see an output like this:
Video input : 0 (Tuner 1)
Step 2:Changing the capture input
To switch your PVR-150 to use the SVIDEO input run the command:
v4l2-ctl -i 1
If you are using the composite video input on your PVR-150 you will want to run:
v4l2-ctl -i 2
There are more inputs you can use. To get a listing of all of them and what number they correspond to run:
v4l2-ctl -n
If this sort of thing excites you you can find many more detail about v4l2-ctl at: [http://www.ivtvdriver.org/index.php/V4l2-ctl](http://www.ivtvdriver.org/index.php/V4l2-ctl)



---

### Post by johnlundy on 2008-11-17
/etc/environmentvlc does not exist on my filesystem.

---

### Post by cotcot on 2008-11-18
Sorry. The sentence with /etc/environmentvlc was not necessary. I have edited my previous post. Just install VLC (it is in synaptic) if you do not have it and go on with "Use "File>Open Capture Device" and then ...".

---

