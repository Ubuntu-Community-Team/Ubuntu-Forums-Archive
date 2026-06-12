---
title: "Ubuntu 14.04 can't stop flash from playing automatically in chrome"
date: 2014-04-21
forum: Multimedia Software
---

### Post by I.Bun.Tu on 2014-04-21
I've been having non-stop issues on this system:

[COLOR=#000000][COLOR=#000000][FONT=Ubuntubeta]Corsair Vengeance Pro (2x4GB) ddr3 1600mhz cl9 dimms[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntubeta]AMD X6 FX-6300 (6 core, 3.5ghz, 8mb cache)[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntubeta]Gigabyte GA-970A-D3P AM3 socket mobo[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Ubuntubeta]Sapphire Radeon R7 260X OC 2gb, 1150mhz clock, 6600mhz memory


[/FONT][/COLOR][/COLOR]I'm starting to wonder if I should start a thread specifically for my system and maybe get some advice on replacing some of the hardware or try to figure out if there is a more general issue. I'm really thinking the motherboard is my issue here but am not experienced enough to say. I will briefly mention (off topic) that I have an IOMMU controller issue, my wireless mouse and keyboard give laggy input at unreasonably short distances, my removable media keeps auto-mounting after safe removal, just to name a few issues off the top of my head, now another weird one.

So I wanted to make it so flash videos don't play automatically and require user approval (e.g., click to play -chrome, ask to activate - firefox). I went ahead and enable these options, both on the above mentioned tower and on my ASUS RoG G55VW laptop. These settings work fine on my G55VW (also none of the above mentioned off topic issues occur on my laptop) and I have to click on the flash video before it starts playing. 

On the tower however the videos play on their own in chrome unless I block all plugins in which case I can't play flash videos at all. I've tried disabling every extension in chrome and even removed the pepflashplayer.so and libflashplayer.so and the flash videos still play. At this point I'm extremely confused as to how flash is working at all. The only thing I surmise is that there is a new package responsible for handling flash in Ubuntu 14.04?

I'm not sure how to trouble-shoot the issue any further. For now I'm just using Firefox instead of chrome but I would like to get this sorted. I also tried using pipelight to enable windows flash but that didn't help either.

Thank you for reading and for any suggestions.

---

### Post by monkeybrain20122 on 2014-04-21
I don't think it works the same way with chrome and firefox. In FF the option is clear, that you will have to activate flash explicitly. In Chrome it is more ambiguous, unchecking 'always allowed' is not logically equivalent to 'always ask to activate'. It seems that on some sites (e.g Youtube) flash always loads automatically, on other sites users will be asked to allow. I don't know how Chrome decides which sites to autoload flash and which one to ask . Maybe you can get something like flashblock for Chrome.

---

### Post by I.Bun.Tu on 2014-04-22
> **monkeybrain20122 said:**
> I don't think it works the same way with chrome and firefox. In FF the option is clear, that you will have to activate flash explicitly. In Chrome it is more ambiguous, unchecking 'always allowed' is not logically equivalent to 'always ask to activate'. It seems that on some sites (e.g Youtube) flash always loads automatically, on other sites users will be asked to allow. I don't know how Chrome decides which sites to autoload flash and which one to ask . Maybe you can get something like flashblock for Chrome.

For Google Chrome you need to go into content settings (after selecting show advanced settings) and under plugins you can select always allow, click to play, or block all. On my G55VW when I select click to play and go to youtube the videos do not play automatically, I have to click to play. This is the feature I'm trying to get working on the tower.

On my tower I did not uncheck 'always allowed' I actually disabled every single plugin under chrome://plugins

At that point, flash should not work at all... but it still does unless I select the option to block all plugins in the content settings. So the flash plugin is disabled for chrome according to chrome://plugins and I can't understand how flash could still be working.

Furthermore I located the pepperflash and flashplayer packages and removed them. So it should truly be absolutely impossible for flash to work on the tower. This is what leads me to believe that there is another package for handling flash in Ubuntu 14.04 and flash works in both chrome and firefox, but ask to activate works fine in firefox on the tower and click to play in chrome does not work. On the G55VW laptop both ask to activate in firefox and click to play in chrome work perfectly fine.

---

### Post by monkeybrain20122 on 2014-04-22
> Furthermore I located the pepperflash and flashplayer packages and  removed them. So it should truly be absolutely impossible for flash to  work on the tower. This is what leads me to believe that there is  another package for handling flash in Ubuntu 14.04 and flash works in  both chrome and firefox, but ask to activate works fine in firefox on  the tower and click to play in chrome does not work. On the G55VW laptop  both ask to activate in firefox and click to play in chrome work  perfectly fine.

Are you sure it is flash? Which sites did you check? Many Youtube videos are actually in html5. Now for Firefox if flash is not disabled (i.e always activate or ask to activate) they will play in flash,-ask you to allow flash if 'always ask',--they play in html5 only if flash is disabled completely, but in Chrome they always default to html5 if the option exists. That sounds like what happened.

---

### Post by I.Bun.Tu on 2014-04-22
> **monkeybrain20122 said:**
> Are you sure it is flash? Which sites did you check? Many Youtube videos are actually in html5. Now for Firefox if flash is not disabled (i.e always activate or ask to activate) they will play in flash,-ask you to allow flash if 'always ask',--they play in html5 only if flash is disabled completely, but in Chrome they always default to html5 if the option exists. That sounds like what happened.

AHH! Of Course. I forgot that most of the videos on youtube are HTML5. So that explains how the videos are working without the flash players.

I'm still not sure why the click to play setting in chrome doesn't work on the tower machine. I have the same settings for my laptop and click to play works fine for the same videos. I've also tried some of the chrome add-ons that are supposed to help stop youtube autoplay but to no avail. The problem (like a dozen other problems I'm having) are only specific to this tower system. I'm going to try a fresh installation to see if it helps with any of the other issues and post back to see if this is resolved. At this point I'm most likely going to buy a new motherboard because this one has been causing me so many issues.

---

### Post by Yellow Pasque on 2014-04-22
You did try booting with iommu=soft option? Lots of Gigabyte AMD 9xx chipset boards have that problem. My Biostar 890 chipset board also has IOMMU issues, and I've heard other people with Asus/MSI mobos with those chipsets complaining (though at least those mnaufacturers offer BIOS fixes).

AMD's IOMMU may not be the best design (or mobo manufacturers couldn't figure out how to implement it correctly). I hope it's improved in recent chipsets...

---

### Post by I.Bun.Tu on 2014-04-23
Yeah, I have to use iommu=soft in order for my USB2 and ethernet ports to work. I've been having nothing but problems with the controller on this board so I'm going to have to buy a new one. Are you suggesting I try to find a board without IOMMU?

---

### Post by I.Bun.Tu on 2014-12-05
[INDENT] 					This issue along with a bunch of others was caused by a controller  (at least iommu) issue with the AMD 970 chipset on the north bridge of  certain motherboards, most notably gigabyte models. I have upgraded to a  motherboard with an AMD 990FX chipset and it has solved all of my  issues. 				[/INDENT]

---

