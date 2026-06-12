---
title: "no sound in headphone output karmic"
date: 2009-12-27
forum: Multimedia Software
---

### Post by Franbugallo on 2009-12-27
Hi, I have just installed karmic koala after almost 2 years with hardy heron and everything works fine except for the sound! There's no sound coming out from the headphone jack! I've tried everything...I have an ALC268 sound card.

Thank you for your help

---

### Post by Nearl86 on 2009-12-27
what computer model are you using?

---

### Post by Nearl86 on 2009-12-27
well at any rate if you type the command below into terminal it will give you access to alsa-base.conf.

gksudo gedit /etc/modprobe.d/alsa-base.conf

after that you need to type the following command at the very bottom of the page on its own line, the part thats says "xxxxxx" needs to be replaced with a command that corasponds to your sound card which you should be able to locate in one of the bottom two links.

options snd-hda-intel model="xxxxxx"

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

hope this helps, if it doesn't try typing the command "alsamixer" and use your arrow keys to navigate and see if the volume is up on your headphones or to see if they are not muted.

---

### Post by Franbugallo on 2009-12-27
I have a toshiba a200 1kz laptop.

I've already done what you said, but nothing happens...

Thank you for your help

---

### Post by Chris Edgell on 2009-12-27
I have just completed a synopsis of how I solved my sound problems. 

THE FIRST STEPS

For me this was really all beside the point - this was about making sure I had all the necessary programs installed.  Acrobat, Java, and probably etc, etc. If you need to see about those there are easier descriptions than MY thread about it:
[http://ubuntuforums.org/showthread.php?t=1285131](http://ubuntuforums.org/showthread.php?t=1285131) 

                 ............................**** 

[B]The real secret is to check the 3 following places to see if it is just something that is muted, turned off, not activated.
[/B]


THE FIRST PLACE TO CHECK
Applications > Multimedia > **Mixer**

I slid the volume slide to quite high...still no sound.   Then  someone pointed out those little red X's at the bottom of each slide (in the AlsaMixer) -- indicated muted -- click red x to unmute.)  You will also notice in the bottom left-hand corner, click that button marked "Select Controls" and inside you will see about 20 places that can be activated for sound (or at least says, "Select which controls should be visible".  Be sure to click master.  See the first screenshot.
				....................................

THE SECOND PLACE TO CHECK
Applications > Accessories > Terminal

This is the second screenshot.  I'm showing the Mixer too.  You can see that the mixer **causes** the changes in the terminal.  If the terminal is showing red, the mixer volume slide can be adjusted then and there -- and you'll see it reflected in the terminal.  Also notice that when you mute in the Mixer, you will see a fated "mm" at the bottom of the slide in the terminal.  Again you see how the changes made in the mixer are shown in the terminal.  

				..................................

THIS IS THE THIRD PLACE
This is the third screenshot.

Applications > Multimedia > aumix

"What the heck is it?" I asked. It looked like sound and volume, there was a word unmute, I clicked it... various little "O" position markers all reset to ZEROs at the starting point.

I was quite sure I could click on the word "Mute" (that the unmute had changed to), and that it would change back to how it had been. But NO...The word changed back to unmute but all the zeros stayed at first position (instead of all the various positions on that horizontal scale). I went to the AlsaMixer and the mute was not marked with the red X.....but there was now NO SOUND.  I could press mute on the aumix and all the zeroes  popped to the starting point, and the little red X showed up at the base of all the slides in the mixer.

Can you believe, I went to examine aumix again and on the odd chance, I clicked far along that  horizontal, turquoise line...and the Zeros positioned where I clicked...and now I have sound again, although in the between time I happened to have made sure that the mixer had no red x, because now as I'm defining for YOU, I discover that if I had not happened to have removed those red mutes, even when I moved those zeroes up the scale, I still would NOT have gotten sound, because of having reimposed the mutes into the mixer.

Also this aumix is a TERMINAL that has been arrived at NOT by clicking "Terminal", I don't really know how it got to the multimedia position-it had to have come there when I installed something...but now I see it can be gotten by means of the regular terminal click.  So we could skip the convoluted way I got to "aumix".   But tell me about it, is it a third way that people could have lost their sound?  I have never seen it mentioned as a possible "cure" for sound problems.  I have never seen it mentioned at all...maybe because I wasn't looking to notice a word I had never heard.


...................................

---

