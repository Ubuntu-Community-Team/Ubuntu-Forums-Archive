---
title: "Headphone Jack Problems"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by ChrisMP1 on 2008-02-23
I have a Compaq/HP Presario C751 laptop, and I'm using the snd_hda_intel module for my sound. My problem is that the sound always comes out the speakers, even with headphones plugged in. Every other computer I've ever had has had a sound channel called "PCM" that controlled the headphones; that doesn't even exist on this one. I couldn't find any problem exactly like mine, and solutions for similar problems didn't help. This being a laptop, I really need to be able to use headphones. Any ideas?

---

### Post by Lizzy on 2008-02-23
Hi, the absolute same problem here and i don't know how to fix it..... did i miss something here? I had quiet a lots of problems getting Linux installed on this Laptop, this laptop came with Vista Home Premium preinstalled :-( and died after 3 days due to 4 viruses... I got the integrated webcam working+wireless :-), But yesterday i wanted to listen to some music on my headphones, and that simply doesn't work..... i checked some of the solutions in the forum but none of them work.... Specs in signature ;-)   Any help would be apreciated :-)) ... No more Vista on that Laptop

---

### Post by fredfjr on 2008-02-23
> **ChrisMP1 said:**
> I have a Compaq/HP Presario C751 laptop, and I'm using the snd_hda_intel module for my sound. My problem is that the sound always comes out the speakers, even with headphones plugged in. Every other computer I've ever had has had a sound channel called "PCM" that controlled the headphones; that doesn't even exist on this one. I couldn't find any problem exactly like mine, and solutions for similar problems didn't help. This being a laptop, I really need to be able to use headphones. Any ideas?

Well, no guarantees that this will help you (I have a HP Pavilion zv5320), but here's the process that got things working right for me:

1.  Double-click on the speaker icon.  You should see the Volume Control window open now.
2.  Click Edit-->Preferences in the Volume Control window.  The Volume Control Preferences window should be open with various check boxes that will display tracks to be visible when they're clicked.
3.  There should be a check box there named Headphone Jack Sense.  If it's there, click it to put a check there.  A tab named Switches should be open now in your first Volume Control window.  Close the Volume Control Preferences window to get back to the first Volume Control window.
4.  Click on the Switches tab to display it.  Click the check box for Headphone Jack Sense.

This is the point at which things worked well.  The speaker would work until I plugged in headphones, at which time the headphones took over and the laptop speakers went silent.

My laptop has a NVidia NForce3 motherboard inside it so I can't be sure things will be the same for you.  I hope this helps.

Have a good day.

---

### Post by Lizzy on 2008-02-24
Well, the thing is that there is no Headphones option in the preferences tab. I had an old Toshiba Satellite until recently and everything was detected out of the box. It seems that all Intel-drivers for Compack and HP-Laptops aren't working as they should (no compiz/ due to blacklisted Intel graphics card, wireless was a hack, integrated webcam was a hack, and now the headphones :-( ), which is a shame really. I hope this gets fixed with the next kernel upgrade,I need the headphones to work for video/voice-chatting

Thx for trying to help, really apreciate it :-)


Anyone else with a solution.... please :confused:

---

### Post by Ekin on 2008-02-26
Unfortunately, i have the same problem as you and waiting for solution. (i had your kind of wifi problem too).

But i can help you with compiz and blacklisted card. The way to work around it is here:
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

But if you enable that option, your video playback wont work. To fix this, i used mplayer patched for compiz by David Raveman (i dont remember link sry). And then enable video playback plugin in "advanced desktop settings".

---

### Post by Bungo Pony on 2008-02-26
> My problem is that the sound always comes out the speakers, even with headphones plugged in.

It's most likely a hardware issue.

Many headphone jacks have a switch in them to turn the speakers off when you insert your headphones plug. In your case, the headphone jack on your speakers doesn't have a switch built in. You could modify it to do so if you have a soldering iron, and a replacement jack that has the switch.

---

### Post by ChrisMP1 on 2008-02-27
Why would I want to modify my computer's hardware?? It worked in Windows, so it's obviously not a hardware problem...

---

### Post by ChrisMP1 on 2008-03-01
Hello anyone?

---

### Post by IrishPidge on 2008-03-01
Maybe this is a bit obvious, but have you tried the following?

1. Double click the speaker icon and go Edit -> Preferences
2. Make sure every box is ticked.
3. Leave preferences and mute the channel marked "Speaker".

I have full control over whether I want speakers muted when the headphone goes in. It's quite handy.

---

### Post by ChrisMP1 on 2008-03-02
I tried that. In every other computer I've ever put Ubuntu on, the PCM control was for the headphone jack. Nothing there controlled it. Though, yes, I'd be happy to be able to turn off the main speakers myself. It doesn't need to be automatic; I just need to be able to do it.

---

### Post by ChrisMP1 on 2008-03-08
If nobody has any ideas, can you please tell me that? I'm kinda in the dark here...

---

### Post by dibryn on 2008-03-09
I am using a Toshiba A135-S4677 laptop and for months now I haven't had any success with getting headphones to work until today. I stumbled upon this link: [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA135](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA135). From that link I found a post to add this statement to the end of your alsa-base file: options snd-had-intel model=lenovo. Once I added that and rebooted, I had the switches tab in my volume control. Then I muted the PCM and voila! sound is coming from my new Sennheiser HD280 headphones. I am currently using Hardy Alpha 6, this problem ha dogged me in Gutsy and Feisty. I hope this will help you and anyone else who has had the headphone issue. It may not work for everyone but it did help me as a Linux Noob.

---

