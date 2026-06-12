---
title: "Poor performance with fullscreen web content"
date: 2011-02-08
forum: Mythbuntu
---

### Post by ill_switch on 2011-02-08
I know this isn't strictly a mythbuntu problem but I'm posting here anyways as the machine in question is running mythbuntu and I figure this forum has people knowledgeable about video. If people think this thread would be better served in a different forum please feel free to suggest.

Machine in question is a new-ish install using 10.10 on this hardware:

Foxconn M61PMP-K AM3 NVIDIA MCP61P Micro ATX AMD Motherboard
AMD Athlon II X2 240 Regor 2.8GHz Socket AM3 65W Dual-Core Processor ADX240OCGQBOX
Patriot 2GB 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) Desktop Memory Model PSD32G13332
HITACHI Deskstar 7K1000.C HDS721010CLA332 (0F10383) 1TB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive

The PC is connected to a TV via the VGA port on the motherboard.

Mythbuntu itself performs fine. However, when watching web content in firefox or chromium in a web browser (i.e. watching TV show episodes on pbs.org or hulu.com) there are some weird performance issues.

If I watch the content in a "normal" browser window things are totally fine. However, if I use the player's "full screen" mode it all goes to crap. The video playback starts dropping frames to the point that it's not watchable; it probably drops to only 1 or 2 fps. The strange thing is, I can zoom or expand the "normal" browser window until the media nearly fills the screen and performance is totally fine. The problem only occurs when using the "full screen" button presented in the player.

Any thoughts? Is there something I can adjust in software? Is this a case of the poor quality video card on the mobo causing issues? If so, can someone suggest a cheap and compatible video card?

---

### Post by nhtrader on 2011-02-10
I'll take a shot at this one only b/c I experienced a similar problem.  Video dropped down to 3 fps but my situation interestingly didn't  involve Mythbuntu nor did it involve streaming video using a webbrowser. I  can also add that my hardware was different too.

My guess for you is that the wrong video decoder is being implemented or a necessary video decoder/codec is missing.

However, I will acknowledge that buying a new piece of hardware is often times the path of least resistance.

---

### Post by LowSky on 2011-02-10
That motherboard you have uses a Nvidia 6150... which isn't made to run VDPAU or HD video. I have no idea why Foxconn would even make that motherboard, the 6xxx series chipset was dead way before AM3 cameout.

Just go out and buy a Nvidia GT 2xx series video card and your problems will go away.
this one is one sale if you are in the US
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814121385](http://www.newegg.com/Product/Product.aspx?Item=N82E16814121385)

---

### Post by ill_switch on 2011-03-02
Well, I went ahead and put a new video card in it (a Galaxy-brand GeForce 210; thanks to a rebate it was cheaper than the one you suggested). No difference. This is the card:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814162041](http://www.newegg.com/Product/Product.aspx?Item=N82E16814162041)

All I did was put it in the PC, plug in an HDMI cable, and boot the machine. Clearly the card "works" in the sense that I'm getting video output, but:

a) it didn't fix this problem,
b) there's no sound.

I would at least be happy if I could get sound through the HDMI cable. Any pointers on that? Thoughts on fixing the original problem would be welcome, too. Do I need to do any install or setup to get the video card working correctly?

This whole issue just strikes me as really strange. Take this video on Hulu for example:

[http://www.hulu.com/watch/217308/the-office-todd-packer](http://www.hulu.com/watch/217308/the-office-todd-packer)

If I hit the icon to pop the viewer into a new window, and then maximize that window, it's essentially showing the video at full screen, with 100% perfect quality. BUT, if I hit the little "full screen" icon to actually put it in full screen mode, quality plummets and I get like 1 frame per second.

---

