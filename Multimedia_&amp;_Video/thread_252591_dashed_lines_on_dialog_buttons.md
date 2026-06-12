---
title: "dashed lines on dialog buttons"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by thom314 on 2006-09-07
I have installed ubuntu on an hp pavilion ze5300 laptop. I find that on pop-up dialogs, most of the buttons (like OK, CANCEL) have dashed lines on top of them. The lines disappear once my mouse hovers over each button.

I ran through the dpkg-reconfigure xserver-xorg X server configuration with no improvements (although there are an awful lot of choices there). Is this something I can fix or do I have to live with it?

---

### Post by mike078 on 2006-09-19
For what it is worth. I have the same problem. In my case it is rather ramdom dashed lines on the widgets.  

This is the first time I've managed to find mention of the problem (rather difficult error to search for). Like you I think it is something to do with Xorg. The other possibility though I can't imagine why (because it would probably relate to Xorg anyway) is something wrong with GTK. Unfortunately I'm not that knowledable of Xorg. 

It should be said that this started when I installed Dapper. 

Are you running a Radeon 7500 Mobility? :P

---

### Post by thoffland on 2006-10-03
> **mike078 said:**
> Are you running a Radeon 7500 Mobility? :P

I also have the same problem and I'm pretty sure I'm running the 7500 Mobility. The reason why I say pretty sure, is that if I look at xorg.conf it says Radeon mobility 9000 M7... but in Windows under Hardware manager it says 7500. 

Either way, I'm downloading the 7500 driver right now. The 9000 supposedly installed, but beryl doesn't work still... so this is my next thing to try. I could not get a new driver installed under Windows, so I'm hoping this works.

---

### Post by kalath on 2006-10-12
Was there any resolution of this? I'm running on a mobility 7500 on my laptop. Where did you find the drivers?

Thanks!

---

### Post by klato on 2006-10-14
I also see these lines with an ATI Radeon Moblity 7500

---

### Post by NetworkGuy on 2006-10-14
For what it is worth, I have a Radeon 9000.  I made these changes to my /etc /X11/xorg.conf file and now the dotted lines I used to have to longer appear.

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "AGPMode" "4"
        Option          "AGPSize" "64" # default: 8
        Option          "RingSize" "8"
        Option          "BufferSize" "2"
        Option          "EnablePageFlip" "True"
        Option          "EnableDepthMoves" "True"
        Option          "RenderAccel" "true"
EndSection

```

---

