---
title: "not a question just an observation"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by mrdaze0 on 2007-10-06
i have a hp laptop with a nvidia geforce go 7150m video card.
i started out installing ubuntu 7.04 on the laptop and the nvidia restricted driver did not work X crashed continuously

so i upgraded to ubuntu 7.10 didnt think it would make a difference but thought hey why not.  so installed and installed nvidia restricted driver.  it works...everything i read online said the 7150m video card was not supported for linux.

so 7150 does work (with alittle bit of work not 100% xorg.conf edit free)  with the next release of ubuntu.  anyone with this card might consider upgrading now.

---

### Post by SpiritIsReality on 2007-10-06
howdy
good one for the archive, way to go
buds

howdy again
only trouble is, unless you start a new thread with the name of your graphics card in the title, no one is going to find it.
I mean if I type into the search box , 7150 I ...oh, yours will still show up if I don't choose search only titles. sorry about that.
buds

---

### Post by dsorensen on 2007-10-09
I have the same card as you on a HP laptop and I can't get the video to work, could you please share how you managed to get it working?


Thanks!

---

### Post by Dark_Stang on 2007-10-09
I'm looking to buy a new hp6636nr laptop that has this card in it. I'd like to know every detail you can give me on it. And I want to know how well it works.

Thanks.

---

### Post by mrdaze0 on 2007-10-09
all i had to do was install the latest version of ubuntu then start in bad graphics mode.  once desktop was loaded went to system>admin>restricted drivers installed and rebooted

then go to terminal enter > sudo nvidia-settings 

nvidia control panel opens.  go to XServer Display Configuration it will have options on the right select resolution or set to auto

then click save to x configuration file and your xorg.conf file will be rewritten 

now restart X ctrl-alt-backspace you should now have nvidia card working properly. if not reboot system and it should work.


It works great no problems yet. still looking for an easier way to enable second monitor without having to restart X everytime but if that is all i have to do I am happy.  Btw on anohter note Compiz--Fusion works very well.  if you have any questions or problems i will try to help you.

---

### Post by Dark_Stang on 2007-10-10
So you're using the Gusty Beta? Also, what's the exact model of your hp? Since I've been shopping around I've become intimately familiar with most of the HP laptop lineup. I PM'd you a much more detailed list of questions, but try to answer them all here just in case somebody else has problems.

If I'm sure I can get this working I'll be bringing the laptop home, and will create a full and very detailed guide on how I did everything. And I'll create a web page for it and start posting the link around.

Thanks.

---

### Post by mrdaze0 on 2007-10-10
Ok here are the specs on my laptop
Model: HP dv6500t
Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-60
Memory: 2GB ddr2
Video Card Nvidia Geforce go 7150m
Wireless card: Broadcom BCM4328 
Hard Drive 160GB 5400rpm Sata Drive

Ubuntu version Gusty beta.
[INDENT]- fiesty would not work installed this first and nvidia restricted drivers caused X to crash[/INDENT]
Wireless was a little bit of a pain to get going but that was because I tried to not follow guides online and did it on my own.  HINT follow the guide here [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
  do not try and use wireless drivers provided by HP with ndiswrapper.  after starting over and using the guide above had wireless running in about 10 minutes.

As far as noapi or nolspci not an issue didn't need them.

Ok now for installing software the live cd works in safe graphics mode very very very low resolution.  The install screen does not fit on the laptop screen.
I was still able to run install from the live cd.  When you go through the install on pages where you select language and the click able items double click on the last option you will advance to the next page. There will come a page (i think partitioning) where you will have to tab a couple times and then enter (will need to guess how many tabs and hit enter till you get it).  After install you can  start using nvidia driver.  You will still have low resolution you will have to click on Applications and use the arrow keys to navigate to the restricted drivers.



[SIZE="5"][B]
DISCLAIMER:::::I IN NO WAY ADVISE PURCHASING A HP LAPTOP![/B][/SIZE]
For the story behind why ask and i will tell to long to post here.

---

### Post by SpiritIsReality on 2007-10-10
ask

---

### Post by Dark_Stang on 2007-10-10
Hm... But, the dv6500t uses Intel processors and either the intel chip or an nvidia 8400, and uses intels wireless cards. Did you mean dv6500z? The dv6500z uses AMD processors, either an nvidia 7150 or 8400, and broadcom wireless cards. Or is there something different about your laptop than most of the others?

And if you don't advise getting an hp, you don't have to post your long story. This is the only question I ask on that. Did you have problems with HP the company, or the hardware in this laptop?

I know I'm asking a lot of questions. But I'll be spending around $900 on this laptop and if I get it wrong I'm screwed.

---

### Post by dsorensen on 2007-10-10
Thanks for all your help mrdaze0, I have almost the exact same laptop as you and your answers were very helpful in getting the video and wireless working.


Thanks again!

---

### Post by mrdaze0 on 2007-10-10
Problems with the hardware.  I cannot gurantee the accuracy of the model number given.  The laptop i have is a replacement for a defective laptop from hp.  The support told me it was the dv6500t but iagree the specs do not match that model.

This laptop replaced a 1 month old laptop that had hardware failures.  New laptop is already having hardware problems.  I have decided i dont feel like spending 16 hrs on the phone with there support for this so i am using it till it dies and buying a new laptop not made by hp.

---

### Post by Dark_Stang on 2007-10-13
Ubuntu 7.10 RC is up and running wonderfully on my HP dv6636nr. The one last thing I have to configure is the built in webcam. Everything has gone pretty smoothly so far. I will be posting a full and detailed writeup of everything I had to do to get it working soon.

Thank you, mrdaze0, for all your information.

Edit: So, to my pleasant surprise, the built in webcam works "out of the box".

---

### Post by mdshann on 2007-10-17
Crap. I just saw this thread after ordering a very similar laptop, the dv6640us. It has the same specs except with an Athlon X2. My brother has an HP and had no problems but it is 2 years old so maybe the quality has gone down. Anyways I am very glad to hear that the card works with 3d and that the wireless works as well.

---

### Post by mrdaze0 on 2007-10-18
webcam hmmm.....

oh yeah my replacement didnt come with the webcam.

---

### Post by bossie7079 on 2008-01-23
Hi everybody...

Looking for INFO about some Installation issues I found this Forum. I had my Ubuntu Account, but I didn't think it could be helpful. If some one can help me I'd really appreciatte it.

SPECS
I have the UBUNTU 7.10 Installadion CD. 
I have an HP Pavillio Notebook  ZD9620
2 DDR RAm
AMD Turion 64 x2 Mobile Tech
NVIDIA GeForce Go 7150M Graphics w/ 559MB

When I start I tells me that it will run in LOW GRAPHICS MODE or CONFIGURATION (the GRAPHIC CARD)
I tried both:
1-  the first one sent me to a Black Screen Like programming screen and I am not able to leave. I had to turn it off.
20 The second one gives the choice to look for the Graphic Card Manufacturer and Model but I couldn;t find my CARD.

CAN ANY ONE HEL ME??? PLEASE...

THANKS

---

