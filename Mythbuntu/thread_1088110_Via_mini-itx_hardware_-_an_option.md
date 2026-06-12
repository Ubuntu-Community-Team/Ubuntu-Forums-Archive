---
title: "Via mini-itx hardware - an option?"
date: 2009-03-05
forum: Mythbuntu
---

### Post by brianeh on 2009-03-05
I own a Epia motherboard with spdif and s-video inbuilt, one of the M series. The processor is a Via C3, which is a 586 processor - not supported by mythtv 0.21. 

I want an easy life here, so don't want to recompile so looked to buy another board. The only one I could see with inbuilt spdif/s-video was the EX range, however the mpeg2/4 acceleration on the cx700m2 chip isn't supported in linux by openchrome - so guess Mythbuntu out of the box doesn't support?

I really liked the small via thing of having everything on the same motherboard, low power and small case - can anyone suggest an option where I can replace my existing motherboard? Or do I have to get a new motherboard (c7 based?) and buy a nvidia video card with it? Or any other ideas...?
Cheers.

---

### Post by Flecko on 2009-03-05
I'm glad I found your post.

I just built a mini-itx High Def Myth setup that works like a charm. I went with a Zotac 8200 motherboard (no expansion slots FYI) Athlon X2 4850, 2 gigs of G. Skill DDR, a 500gb laptop HD, and an HDHomerun. My remote is a Wiimote using a bluetooth dongle and a wminput script. 

So far I am liking it much better than my old tweaky Via mini-itx setup. (Very tempermental.)

Hope this helped!

---

### Post by mpsii on 2009-03-05
@brianeh -- what model is your motherboard?

---

### Post by brianeh on 2009-03-06
Hi - thanks for the replies. 

mpsii - haven't got infront of me now but think it's the M6000, /proc/cpuinfo reports as the Samuel C3 - definitely used i586-pc-linux-gnu as CHOST in its Gentoo days. 

Flecko - like the sound of that box, a lot. Can't see that it's available for purchase in the UK? Also, reading this review

[http://www.tweaktown.com/reviews/1726/9/zotac_geforce_8200_itx_wifi_am2_motherboard/index.html](http://www.tweaktown.com/reviews/1726/9/zotac_geforce_8200_itx_wifi_am2_motherboard/index.html)

It doesn't have an spdif out - I direct all sound straight to my amp, so this is essential..not sure what would be involved to get this working. Also what box have you got and does it just fit in your VIA box (I've got the Morex 2699B)?

Nice one, cheers.

---

### Post by Flecko on 2009-03-07
brianh: Hadn't thought about the SPDIF out. According to the article you sent (and my motherboard manual for that fact) the board has a motherboard header with SPDIF output on it. Worst case scenario, you would have to buy a connector for it. So that should solve your issues with SPDIF.

At the moment, I'm using the VGA out and not the DVI->HDMI option because I've read that under 8.10 you have to do some serious mucking around to get audio working over HDMI. Also, I'm only using the stereo out to connect it to my receiver...works fine until the next update to 9.04 I suppose.

As for UK availability, I could have sworn that when I was looking to purchase my board that I found a UK shop that had it, but I can't seem to find it now. I ended up getting it from newegg, not sure if that helps though.

Great board though, I hope you can get your hands on one.

EDIT: I forgot your question about the case. At the moment, I'm not using a case, but I'm in the hunt for one. With the stock heatsink and fan, the CPU I have needs a smidge more clearance than a normal mini-itx case provides, so I'm in the hunt for one. I like the looks of the one you're using, but its a smidge large for my setup. I need to find the smallest possible case that still has room for the fan in it. I'll post back if/when I find one.

---

### Post by brianeh on 2009-03-13
Still looking into this - all really want now is small (mini-itx) solution to run mythbuntu frontend on. 

See Via have released the Epia M700-10E ([http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=670](http://www.via.com.tw/en/products/mainboards/motherboards.jsp?motherboard_id=670)) - looks really good, but without drivers to take advantage of the hardware acceleration, what's the point? (from a linux point of view) VX800 chipset is not supported...
[http://www.openchrome.org/trac/wiki/SupportedHardware](http://www.openchrome.org/trac/wiki/SupportedHardware)

Basic question is for a mini-itx solution that has spdif and s-video outputs...and works out of the box...

---

### Post by movieman on 2009-03-14
Intel Atom D945GCLF2 board has both, though I don't know whether they work; I know the S/Video wasn't working in Linux but I believe that Intel recently released a new driver that fixed it.

Plays SD fine, but single-threaded HD codecs are too much work for the CPU to handle; you really need to load it up with multiple threads to get the best performance.

---

