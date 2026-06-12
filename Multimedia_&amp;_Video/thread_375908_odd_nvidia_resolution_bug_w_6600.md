---
title: "odd nvidia resolution bug w/ 6600"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by CC_machine on 2007-03-04
ok, recently installed the nvidia drivers from synaptic (searched for: nvidia glx) on xubuntu 6.06.1 LTS. Note: ever since I installed the default resolution for my screen has been 1280x1024.

after it finished, I noticed there were far fewer screen resolution options (aka the only 75hz option was 832x624, and all the others were at 85hz, which my monitor can't display. :(). I'm using a 15 inch Flatscreen(native res 1024x768 ), but after poking around in xorg.conf, it looks like it recognized my monitor as a 17 inch Flatscreen instead, which would explain all the odd options. I tried changing where it says 17 inch to 15, but no difference. The good news is that the game(aka [http://sauerbraten.org](http://sauerbraten.org)) i installed the drivers for is now working perfectly :), albeit at a low resultion.

thx in advance :)

Hardware: Inno3d brand geforce 6600, amd sempron 3400, ATI motherboard (could be the problem...), 1gb RAM.

---

### Post by mid_night gypsy on 2007-03-04
CC_machine,
 You could post your xorg file so we could better help you. Also you could run this command in a terminal.......gtf 1280 1024 75...and paste the output to your xorg file under the monitor secition.
                                                                                                                  hope this helps gypsy

---

### Post by CC_machine on 2007-03-04
oh, sorry i should have posted xorg before ^^' (btw: why the stupid restriction on file extensions?)

ok, did "gtf 1024 768 75", returns:
  # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

tried putting that into the xorg config, here:

Section "Monitor"
	Identifier	"15'' LCD"
	Option		"DPMS"
  # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
EndSection

...no luck.

---

### Post by mid_night gypsy on 2007-03-04
CC_machine,
 Sorry for the delay,To answer your question "why the stupid restriction on file extensions?"It's for
your system's protection. Your xorg looks fine to me,except for the name of the monitor it's more
right in your last post,you could rename it to something else.(e.g. "15LCD" )and get rid of the inch
marks. That's part I'em not liking.I could be wrong,but thats where I would start...Good Luck gypsy

---

### Post by CC_machine on 2007-03-05
Well i changed that to 15LCD and it didnt work but thanks anyway :)... I'll resend my Xorg.conf if anybody can help.

Is there some way to make xubuntu or the drivers attempt to redetect my monitor?

P.S. i recently tried installing Beryl which is why the file has been changed it a few times.

---

