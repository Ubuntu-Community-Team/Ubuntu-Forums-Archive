---
title: "Freecom DVB-T v4 RTL2831U"
date: 2010-05-01
forum: Multimedia Software
---

### Post by regstraton on 2010-05-01
I had a real pain trying to find a concise solution to getting my Freecom v4 DVB-T USB dongle to work on my system:

[INDENT][COLOR="Gray"]Ubuntu 9.04 (Jaunty Jackalope) - Desktop (on Asus Eee PC 901)
uname -r: 2.6.28-18-generic
lsusb: Bus 001 Device 013: ID **14aa:0160** AVerMedia (again) or C&E 
[/COLOR][/INDENT]
It appears I needed the device driver, and after hours of trawling through outdated chatty forums and web searching I found this:

[COLOR="Blue"][http://linuxtv.org/wiki/index.php/Realtek_RTL2831U](http://linuxtv.org/wiki/index.php/Realtek_RTL2831U)[/COLOR]

[I]NOTES:
- use the latest mecurial repository mentioned, which is currently: [http://linuxtv.org/hg/~anttip/rtl2831u/](http://linuxtv.org/hg/~anttip/rtl2831u/)
- The CLI command should be:[/I]
[INDENT][COLOR="gray"]hg clone [http://linuxtv.org/hg/.../rtl2831u](http://linuxtv.org/hg/.../rtl2831u)
cd rtl2831u
make
sudo make install
cd ..
rm -rf rtl2831u
[/COLOR][/INDENT]
Got it running straight off with Kaffiene [COLOR="Gray"]sudo apt-get install kaffeine[/COLOR]
though it will also run with many others like MythTv, VLC, etc.

I hope this helps !!

Further reading:
[INDENT][https://help.ubuntu.com/community/DVB-T_(USB](https://help.ubuntu.com/community/DVB-T_(USB))
[https://help.ubuntu.com/community/Converting%20DVB-T%20streams%20to%20AVI%20files](https://help.ubuntu.com/community/Converting%20DVB-T%20streams%20to%20AVI%20files)[/INDENT]

This device driver apparently supports the following device IDs:
[COLOR="DimGray"][INDENT][FONT="Courier New"]0bda:2831    
2304:022b    
13d3:3216    
13d3:3220    
13d3:3236    
13d3:3238    
13d3:3244    
08dd:2103    
185b:0100    
185b:0150    
1a46:1601    
14aa:0160    
14ff:0225[/FONT][/INDENT][/COLOR]

---

