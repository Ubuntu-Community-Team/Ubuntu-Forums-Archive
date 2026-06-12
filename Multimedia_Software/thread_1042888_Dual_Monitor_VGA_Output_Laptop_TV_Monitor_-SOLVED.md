---
title: "Dual Monitor VGA Output Laptop TV Monitor -SOLVED"
date: 2009-01-18
forum: Multimedia Software
---

### Post by russ5811 on 2009-01-18
I have been helped MANY times in the forums and I am finally able to offer help to others. I have a Toshiba laptop with an integrated Intel graphics card (not NVIDIA or ATI). I wanted to enable VGA output simultaneously with my LCD screen to enable Boxee to play on my TV.  Here's how to do it:

To edit xorg conf file, type the following into a terminal: sudo gedit /etc/X11/xorg.conf

Add this to END of xorg conf file to enable vga monitor out on laptop:


Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Option          "MonitorLayout" "CRT,LFP"
        Option          "Clone" "true"
EndSection

Once this is added and saved, plug in the cable connected to your monitor or TV, then press CTRL, ALT, Backspace.  And you will now have your LCD screen on your TV!  If you already knew this, then I'm sorry to have wasted your time. I just hope it helps someone!

---

### Post by _Jo_ on 2009-01-18
> **russ5811 said:**
> 
Once this is added and saved, plug in the cable connected to your monitor or TV, then press CTRL, ALT, Backspace.  And you will now have your LCD screen on your TV!  If you already knew this, then I'm sorry to have wasted your time. I just hope it helps someone!

Excellent, there is some Ghosting, but I've finally got an output on my Sony Vaio! I've got a good starting point, just need to tweak it until it's right. Thanks for the tip.

Jo

---

### Post by yadayada2 on 2009-01-18
Very nice.

But I have a follow-up question. Dual monitoring in clone mode works fine, but what about real dual monitoring?

I got it working with other TFT displays, but not with my TV. For whatever reason, it's only working in clone mode.

Do you have a clue?

---

### Post by russ5811 on 2009-01-18
It took me a couple hours to figure this out. My searches on real dual monitors have turned up with nothing useful. Sorry. To be honest, that isn't a capability I'm in need of so I probably will not be putting much time into figuring it out right now. Good luck though. Sorry I couldn't be of more help.

---

### Post by jocika on 2010-05-16
> **_Jo_ said:**
> Excellent, there is some Ghosting, but I've finally got an output on my Sony Vaio! I've got a good starting point, just need to tweak it until it's right. Thanks for the tip.

Jo

Can you tell me which tweaking exactly you applied? I have Sony Vaio with ATI Mobility Radeon x600 and cannot connect to TV.

---

### Post by jasquith on 2011-01-20
I have Ubuntu 10.10 and I don't have this file.How do I enable the vga on my Toshiba Satellite?

---

