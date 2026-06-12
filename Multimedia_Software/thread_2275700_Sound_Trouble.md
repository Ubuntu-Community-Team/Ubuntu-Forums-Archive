---
title: "Sound Trouble"
date: 2015-04-27
forum: Multimedia Software
---

### Post by huff2 on 2015-04-27
Hey guys,

I recently used my tv as a dual-monitor but I want the sound to come out of the tv. Can anyone give me a walk through. I'm new so don't leave little bits out.. 

I set it up by going to system settings>display then I drug the laptop screen over top the tv screen till the alighnment read (0,0). 
Thanks!!

---

### Post by Rob Sayer on 2015-04-28
First, though I'm doubtful this is your problem, I'm wondering about your dual display config.  It sounds like you overlaid the 2nd over the 1st.  I see no reason to do this.  I think it'd work better with the displays side by side and aligned at the top.

Re your main question, are you talking about an hdmi connection?

Anyway, need more info.  What hardware?  To find out the video adapter, paste this into terminal, enter password, and post the results here (use ```
 tags so people can read it better)

[CODE]sudo lshw -C video
```

---

### Post by huff2 on 2015-04-28
[FONT=monospace][COLOR=#000000]brandon@brandon-NV57H:~$ sudo lshw -c video [/COLOR]
[sudo] password for brandon:  
  *-display                
       description: VGA compatible controller 
       product: 2nd Generation Core Processor Family Integrated Graphics Contro
ller 
       vendor: Intel Corporation 
       physical id: 2 
       bus info: pci@0000:00:02.0 
       version: 09 
       width: 64 bits 
       clock: 33MHz 
       capabilities: msi pm vga_controller bus_master cap_list rom 
       configuration: driver=i915 latency=0 
       resources: irq:25 memory:c0000000-c03fffff memory:b0000000-bfffffff iopo
rt:2000(size=64) 
brandon@brandon-NV57H:~$ 


Also, I was using an hdmi connection. I overloaded because my goal is to watch a movie on the tv but when the displays were side by side, I had to drag and drop the window from my computer screen to the tv screen. When I did this, the window would not "stick" onto the tv screen. 
[/FONT]

---

### Post by Bucky Ball on 2015-04-28
Maybe just mirror the displays rather than side by side. arandr (available in the repos) gives a GUI you can tweak your monitors with. I prefer it to the generic 'Display' app.

You should be routing audio with Pulseaudio Volume Control. Install it from Software Centre if you don't already have it installed. You need to set the 'Output' tab to 'HDMI - output' on the stream you are sending if you want sound through the TV and not the computer. You may need to make HDMI available in the 'Configuration' tab, though.

---

### Post by huff2 on 2015-04-28
Thanks! I got it to work!

---

### Post by Bucky Ball on 2015-04-29
Excellent news. Please share with the community how. ;)

Enjoy and good luck.

---

