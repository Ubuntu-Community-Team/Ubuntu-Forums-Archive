---
title: "getting my PC to contect to my SAmsung LCD TV"
date: 2009-02-09
forum: Multimedia Software
---

### Post by aboatwri on 2009-02-09
PC = Dell Latitude 610
TV = Samsung LCD 40" LE40556 etc
Ubuntu 8.10

I am trying to get my PC to link to my TV using a male to male vga cable. Note I will only use the TV as my monitor from time to time

The Samsung manual on page 46 lists a whole bunch of resolutions that include horizontal freq, vertical freq, etc...I have looked at System|administration|screen resolution and have only a very minimum number of basic options.

Further investigation revealed that I need to probably work my xconf.org which is VERY basic at the moment..... bascially says "default device" everywhere. 

I tried to use the following command: 
sudo dpkg-reconfigure -phigh xserver-xorg

But I cannot get into the tool. I just get that a warning and nothing else

This looked like the right tool but no look. 

Investigations

_Item 1: tried to get more info on my graphics card_
Have run lspci to try to information on my graphics card and all I get is: 
----
*00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)*
-----
 I also have gone into System|Administration|Hardware Drivers but this is empty

_Item 2_
I tried to find a GUI that would help me configure the xconf.org but no luck. I did read the manual, but as a relative newbee (to linux not IT) I felt it was a bit risky

So basically any guidance on where I can go from here would be appreciated. I have spent 2 whole days google-ing without any luck other than somehow the xconf needs changing. 

Thank you very much in advance for your ideas and support

---

### Post by bmitov on 2009-02-19
I'm having a similar problem as well--

I'm connecting the computer to the Samsung LCDTV using a VGA cable and I went to "PC" in the source menu, yet it seems that the TV doesn't recognize my computer cause it just keeps searching for signals.

I have no idea what to do. Help? :D

---

### Post by bmitov on 2009-02-19
oK I was being really stupid. I just went to into "screen resolution" under preferences and set the tv and laptop as mirror images operating under 1024x768 resolution.

Now for my next problem: when I play a movie file in the vlc player, it is playing fine on the laptop (ie I can see the movie), but when I look at the TV it shows a blank dark blue screen with no movie where the movie is supposed to be.

I'm connecting my laptop to the TV using VGA. Is there something that I have to configure in Linux?

I'm gonna check whether it works fine with windows just to make sure the TV ain't at fault here.

edit: when I play a movie in media player in windows the tv switches off and gives me "mode not supported" .... hmmm

---

### Post by aboatwri on 2009-08-02
I just wanted to say that the resolution was a bad cable. I aparently bought a cheap cable. As soon as I got a decent cable all worked well again.

---

