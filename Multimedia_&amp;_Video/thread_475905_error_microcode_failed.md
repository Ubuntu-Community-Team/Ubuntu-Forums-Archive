---
title: "error: microcode failed"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by ballison on 2007-06-16
Im sorry, Im very new to linux, so I dont have much of an understanding of what happens to my pc.

I'm basicly trying to install graphics drivers for my nvidia 6800, simply because there a no widescreen resolutions on a generic ubuntu install. 
I have managed to do this flawlessly only once, and I had to delete that partition unforutnatly to reogranise some space. 

Since then I have tried about 7 times, every one failing. The error it comes up with is;

&#8216;failed to start x server&#8217;
&#8216;error: Microcode bcm43xx_microcode5.fw not availble or load failed&#8217;

Now I believe Xserver is the graphical interface that ubuntu uses, and terminal is the text one. So I think when I get this error, it forces me onto terminal.

Previously I have tried both 'add remove programs' and 'synaptic package manager', on both the 64bit and 32bit versions of Fiesty, and the 'bleeding edge guide' and 'ENVY' script.

all have ended in some sort of error, but mostly end in this error I am explaining.

I've followed the HOW TO to the bets of my ablilty, and have tried all the remove commands from the wiki page.
[link](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

I am truly stuck, any help would be apreciated so I don't have to format my partitions again.

---

### Post by PaulFr on 2007-06-16
Perhaps you need to check wireless: bcm34xx is the wirelan LAN adapter, AFAIK. See **[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)** for some instructions.

---

