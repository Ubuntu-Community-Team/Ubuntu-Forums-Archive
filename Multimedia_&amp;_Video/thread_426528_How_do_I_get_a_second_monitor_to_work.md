---
title: "How do I get a second monitor to work?"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by damgaard on 2007-04-28
How do I get a second monitor to work? 

I need to run 1280x1024 on the other monitor. The resolution must be this because the second monitor is a TFT monitor that only runs this resolution. My normal monitor runs 1400x1050 (but I can accept another res. temporarily). 

I need the second monitor to work because I want to watch video on it.

I hope you can help me. 

Please let me know if you need more information about my setup.

My hardware:
My computer is a laptop -- IBM Thinkpad T42 with an ATI graphics card.
lspci says :  ATI Technologies Inc RV350 [MobilityRadeon 9600 M10]

Software:
I use kaffeine in Kubuntu 7.04.
I have installed the fglrx driver for my ATI card.

---

### Post by AR_Kozz on 2007-04-29
I use a radeon 9200 and I had this issue. 

I couldn't get fglrx configured right until I used envy, by alberto morales. It configured it perfectly to where I could use two res for different displays.


I'm not sure where the link is  on these forums but if you google "morales" and "envy" you'll find it. It worked for me. After it ran and I restarted, I had support for 2 displays, and I could give them different resolutions too. A nice bonus was a GUI control panel.

Unfortunately I still can't get video to run on my second display, the display works but video runs as black. But my second display is a TV so you may not have that problem.

If you've already used envy, you should post your xorg.conf, cause it oughtta work.
.

---

### Post by damgaard on 2007-04-29
I can't find the link to "envy". 
I have tried googling for morales+envy, alberto+morales+envy, morales+envy+linux, and so on.

I hope that I can use video on the second monitor because I need this for video.

---

### Post by dante.regis on 2007-05-06
That's because it is not morales, but milone. The URL is this one:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

Best,
Dante

---

### Post by tdn on 2007-05-17
Ok.

How is the right way to use the restricted drivers for my ATI card in Kubuntu Feisty Fawn?

In Ubuntu there is a Restricted Drivers Manager. But how do I do this in Kubuntu?

---

