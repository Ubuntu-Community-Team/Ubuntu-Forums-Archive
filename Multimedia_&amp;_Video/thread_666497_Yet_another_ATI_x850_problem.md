---
title: "Yet another ATI x850 problem"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by ihatethatguy on 2008-01-13
Ive spent the last few days or so browsing the forums, trying various things, and yelling at my computer, which has only served to give me a headache, and not fix the problems ive had getting this stupid card to work properly.

Ive tried both methods described here:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

This method:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


I've also tried a manual re-detection 

dpkg-reconfigure xserver-xorg

I tried that envy program as well.  I have a lan party coming up in a few weeks and it would be nice to be able to actually participate.


I see people that have stuff like this:

"Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
"

in their xorg.conf file, after almost all of m attmepts at installing the proper drivers, the module sections is either empty or only conatins "fglrx"

at the moment, this is what mine looks like, and im not really sure how i got it that way.

"Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection"

It seems like the more i browse the forums here, the more i get the impression that ATI cards are really unfriendly towards linux and that Nvidia is the way to go.  Im not pleased with ATI already since i cannot use the DVI connection for my Sceptre LCD or it will never wake up and they think that they dont have to come up with any support for that, or even respond to my emails.  

Id rather not spend the money, but if it would save me a greater headache, i might be tempted to buy an Nvidia card.

Do those tend to work better, or are those just as big of a headache as ATI cards?

---

