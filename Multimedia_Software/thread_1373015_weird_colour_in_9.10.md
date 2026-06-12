---
title: "weird colour in 9.10"
date: 2010-01-05
forum: Multimedia Software
---

### Post by strangequarks on 2010-01-05
Hello all, I'll try to describe the problem as best I can:

In brief: colours are screwed up in 9.10.

In detail:

I switched from windows to ubuntu 7.04 a few years ago, and (after some messing around with the wireless) got everything working fine. I never bothered upgrading, and it's been smooth running the whole time, but I just decided to switch to 9.10 and installed it from DVD. But something has clearly gone wrong.

Mostly, the display is fine - the resolution, for example, looks perfect - and the icons and everything are roughly okay. But I get some odd things, like right now there is horizontal yellow banding across the screen. It's not enough to affect what I can do, as it just tints the colours of the window and pictures. Other symptoms are: the login screen, rather than the classy dark black-brown it should be, is an oddly psychadelic blue and black pattern; and the default desktop background has purple stripes across it, like a zebra. The headers of windows are also an eye-watering purple-black-yellow mess instead of nice smooth dark brown. There are similar problems with large pictures on the internet. 

Now, I wondered if this was just a bad installation, so I reinstalled - the problem remained. I've got the Linux Format magazine DVD, and ran the live openSUSE just to see what happened with that - and it had the same problem with images. So then I thought maybe something's gone wrong with my computer itself, so I dug out the old Ubuntu 7.04 DVD, and ran that live - and it was perfect. No problem on that. So I could go back to that, but I really don't want to go back to an unsupported distro. 

My laptop is an Acer Aspire 3000, which claims to have "SiS M760GX integrated 3D graphics". 

I've been searching the forums for anyone with similar problems, but have found nothing that sounds like this - possibly it's a problem that was found with earlier releases, and I've just missed the solution as I left it so long before upgrading. 

Does anyone know of anything that's changed between 7.04 and 9.10 that could have caused this problem? And does anyone have any advice for how I can solve it? Or recommendations for other places to look?

If there's any info you need about my computer etc, I shall look it up. Or if you want to see a photo of the desktop, I can do that.

Cheers
Ax

---

### Post by pmlxuser on 2010-01-05
have you tried to check whether the graphics driver is installed correct.

i think you go > system > administration > hardware drivers.

some drivers that used to work in the older version seem to be not in recent version without installing extra closed drivers.. just check

---

### Post by strangequarks on 2010-01-05
Solved!

After posting the above I found another thread about the same problem:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1224660](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1224660)

I only followed the first part of the advice there offered:

1) Press Alt-F2 and run the following command (without quotes):
"gksu gedit /etc/modules"
2) The editor will open. Add the following line to the bottom (without quotes):
"sisfb"

I then saved the modules file and restarted the computer, and everything is fine. I didn't do anything to xorg.conf. But it's all fine now!

I shall anyway leave this here in the hope it will help others.

---

