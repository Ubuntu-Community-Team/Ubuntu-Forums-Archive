---
title: "mythbuntu output to 32&quot; lcd 1080p"
date: 2009-05-12
forum: Mythbuntu
---

### Post by clickwir on 2009-05-12
Got a mythbox with an nvidia 5200 video card using RGB out to a Visio 32" LCD that supports 1080P.

I boot up mythbuntu and it autodetects and displays 640x480. Using the nvidia-settings I'm able to manually set 1920x1080 and apply it. However, the desktop is now 1920x1080 but what's getting output to the LCD is still only 640x480.

So I have to move the mouse around to the edge of the screen and it scrolls the desktop. Everything is there, it's just not displaying it all at once. It's mythbuntu, jaunty, just made sure all updates were done 10 mins ago and rebooted a couple times, even after changes. Still only outputs 640x480 and the desktop is 1920x1080.

How can I force it to output 1920x1080?

---

### Post by clickwir on 2009-05-12
Ok, so I found out that it was panning because I had written in 1920x1080 in the nvidia-settings in the "panning" field. Duh. 

So, I figured out how to change the panning resolution, but not the actual output resolution.

---

### Post by clickwir on 2009-05-12
OK. VGA output doesn't work. But I found a DVI to HDMI converter and tried that. I had to reboot, enable output to the 2nd screen. Apply that. It had the full resolution!

So then I disabled the output to the primary VGA output and am just using the DVI/HDMI output. I found an audio input for that HDMI input and have sound now too. 

I'd prefer to be using the VGA. Since I have other machines that don't have DVI or HDMI, I'd really like to actually have the VGA input on the LCD working right. I'll have to try a laptop tomorrow.

---

