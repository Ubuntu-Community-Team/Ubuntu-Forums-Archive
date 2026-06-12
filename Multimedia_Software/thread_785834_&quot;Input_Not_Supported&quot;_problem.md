---
title: "&quot;Input Not Supported&quot; problem"
date: 2008-05-07
forum: Multimedia Software
---

### Post by Gru001 on 2008-05-07
I have tried all the steps from: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

but nothing has worked. 

Running Ubuntu Hardy Heron, fresh install.
**Video Card:** Nvidia GeForce 8800GT 512mb - made by Palit

**Monitor 1:** Rosewill R912E 19" LCD
[http://www.newegg.com/product/product.aspx?Item=N82E16824021019&ATT=24-021-019](http://www.newegg.com/product/product.aspx?Item=N82E16824021019&ATT=24-021-019)
Horizontal Refresh Rate 30KHz - 83KHz
Vertical Refresh Rate 55 Hz - 75 Hz
***this Rosewill monitor has the problem***


**Monitor 2:** 37" NEC LCD HDTV, works fine, but resolution is 1280x1024, instead of 1360x768, so it is stretched, but that is another problem.

Here is the whole story, I'll try to make it short. I used to have Ati Radeon x1950pro, and didn't have this problem. I replaced the card with Nvidia card mentioned above and since that point I have "Input Not Supported" box bouncing around at all times.

I did a fresh install, with formatting as I wanted to make sure that it is not swapped hardware that messed something up.

After the fresh install my screen resolution was 1280x1024 which what it is supposed to be, with available refresh rates of 60 and 75. Both of those refresh rates caused a bouncing box. I found this strange, since in Windows both 60hz and 75hz refresh rates work fine.

At that point, in the top right corner I saw a notice that "restricted hardware" drivers are available for my Nvidia card. I proceeded to install them and Enable them.

This didn't help at all, as the only refresh rates that were available under Screen Resolution window were 50,51 & 52, and all of them cause "Input Not Supported" problem. The good thing is that I was able to enable the Desktop effects and that they worked great.

I have then tried all the suggestions from the Ubuntu support page mentioned at the start, and then I added:

     HorizSync          30-83
     VertRefresh        55-75

under "Monitor" section. I still had the bouncing box, however the available refresh rates were again 60 & 75 which is correct, and what my LCD monitor supports.

So I am totally clueless on why this is happening, and what I can do. If you have any ideas, please share them with me and I will try them out.

Thanks!!!

---

### Post by andyrue304 on 2008-05-07
Hiya,

I managed to fix this by installing teh nVidia settings manager available from the synaptic.

Neat little tool, no I'm showing 78Hz refresh rate plus image is a lot more vibrant!

Zwing!

---

### Post by showgun22 on 2008-05-07
So if I understand this is a problem that is cause by the video card and not the monitor?

I am running Hardy Heron my Video card is the ATI Radeon 8500LE or R200

what can I do to fix this annoying little floating box..?
Thanks

---

### Post by Gru001 on 2008-05-08
The problem is caused by Ubuntu, monitor and graphic cards are fine.

Ubuntu is not reading the correct monitor specs and it is setting up rates that monitor doesn't support. 

I even tried Envy NG and still have the bouncing box. After prolly 5 hours and a dozens of different "fixes", I am giving up.

I even tried some Modelines and trying to edit other ppls xorg.config files, or whatever they are called and nothing has worked.

---

### Post by showgun22 on 2008-05-08
Does any one knows if a bug report has been log with Hardy Heron/Ubuntu team for a fix if the problem is Ubuntu?

If so any link to the bug report?

I was about to test Envyng but the program is crashing waiting for the repository to be updated with the new version of envyng....

Thanks

---

### Post by Gru001 on 2008-05-08
It was crashing for me as well when I was trying to install 169.12 (I think that is the number) drivers.. I had to install one of the other 2 offered.. 

something is messed up big time, I had problems with update as well, it was just failing when trying to get some files, but later that night it says all is up to date.

I'll wait few months for them to fix the problems, and then try again.

One good think I noticed is that my back button on my mouse is working!!! This is the first version that did this, woohoo for technological leap.

---

### Post by showgun22 on 2008-05-08
The version of envyng that wa have with ubuntu is envyng-core 1.1.1ubuntu14
and the next versio n that should fix it is apparently ready but not yet posted
IT will be envyng-core 1.1.1ubuntu15
[https://launchpad.net/ubuntu/hardy/+source/envyng-core/1.1.1ubuntu15](https://launchpad.net/ubuntu/hardy/+source/envyng-core/1.1.1ubuntu15)

I hope to see it tomorrow <G>

---

