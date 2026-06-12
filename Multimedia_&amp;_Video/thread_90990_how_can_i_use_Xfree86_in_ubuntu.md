---
title: "how can i use Xfree86 in ubuntu"
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by kakashi on 2005-11-16
i have found the dirver for my my built in video card 
which is according to lspci
[QUOTE][/Q0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
UOTE]
i found them at via arena. here's the exact [page]("http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2580&SubCatID=112") 

here is also the page that descirbes my [COLOR="Red"][motherboard.]("http://www.msi.com.tw/program/products/mainboard/mbd/pro_mbd_detail.php?UID=611")[/COLOR] please look at it if you can to see if any info can be found there that would help

but they are meant for xfree68. i tried to run the install script and the confidure script but none work. bnut if i install xfree86 i can't use X anymore cuz no driver i select at installation time works. can anyone help. 
thank you for your help.
i ahve provided aas much info as i could think of but if anymore is reuired i will give that too.

---

### Post by tseliot on 2005-11-16
Well, xfree86 doesn't seem to be your only problem as (according to the website with the drivers "This package contains Linux Display Driver Source Code for [COLOR="Red"]2.4.x kernel[/COLOR] in VIA ProSavage/ProSavageDDR Family Chips"

Ubuntu uses kernel 2.6.12-9 (kernel 2.4.x are quite old). This means you can't use (unless you recompile your kernel) the drivers. However I wouldn't know how to use xfree86. Perhaps you should install Debian 3.1 Sarge stable which uses xfree86 (but there are also other distros).

BTW can you tell me why you need the drivers for your integrated graphic card? I don't think you could use it for 3D applications.

If you have a real problem (e.g. your monitor doesn't display anything in Ubuntu, etc.), please tell me

---

### Post by kakashi on 2005-11-16
thank you for replying. 
sorry i just realised i wrongly named the thread. i was gathering the info at the time so  made that mistake. could you please make it 
'how can i use drivers for Xfree86 in ubuntu'
also thanks for the tip on the kernel i did not notice/know that.
also while my screen is ok and stuff but everytime i try to play a movie in mplayer my processor usage goes through the roof. my processor is not that weak (amd sempron 2400+) and even when i use firefox or any graphical application in gnome or xfce4 my proceesor usage maxes out and the whole computer becomes sluggish and (sometimes) crashes.

also please tell me how i can install a 2.4.x kernel or can i recompile this kernel  to support it. also if you could point me to some guides on kernel compiling that would be great.

---

### Post by tseliot on 2005-11-16
About kernel compilation: try my guide (it's for newbies)

[http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")

[COLOR="Red"]BTW I think your problem might not be related to your graphic card.[/COLOR]

1) Can you open System Monitor (without any other applications running) and tell me the percentage of use of your CPU?

2) Do you use Ubuntu 32bit (i386,etc.) or Ubuntu 64bit (AMD64)?

---

### Post by kakashi on 2005-11-16
oh thanks your guide is good.
in system monitor my cpu usage is about 25 % when i am running azureus (downloading the 13 debain 3.1 cds in the backgorund) and firefox.

i use ubuntu i386 although i did install the k7 kernel and use that.

---

### Post by tseliot on 2005-11-17
[QUOTE=kakashi]oh thanks your guide is good.
in system monitor my cpu usage is about 25 % when i am running azureus (downloading the 13 debain 3.1 cds in the backgorund) and firefox.

i use ubuntu i386 although i did install the k7 kernel and use that.[/QUOTE]

I just wanted to make sure you are not affected by the double clock speed bug.

---

