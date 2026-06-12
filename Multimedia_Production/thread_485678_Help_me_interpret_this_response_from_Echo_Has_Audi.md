---
title: "Help me interpret this response from Echo: Has Audiofire full linux support?"
date: 2007-06-27
forum: Multimedia Production
---

### Post by fsando on 2007-06-27
I'm in the market for an external audio card (usb or firewire or pcmcia)

I've been looking at EMU, Audiofire (Echo's firewire cards) and TC.Electronic (a pcmcia card called Konnekt), and I've mailed all three companies.
EMU/Creative didn't answer yet, The supporter at TC.Electronics said the company doesn't consider Linux a viable business in the foreseeable future (actually he also said that he's a very happy Ubuntu-user himself :)  ).

Echo (makers of Audiofire) send me this response, which I'm not shure I understand.
Does it say that Audiofire is supported? Or just that it could easily be supported.
Can I safely buy an Audiofire?

> Periodically we get asked about Linux drivers for AudioFire.

Echo's AudioFire hardware is compatible with FireWire standards.   As
such, no proprietary information is necessary to develop a driver.  We
encourage the development of a universal FireWire audio driver for
Linux, similar to Apple's OS X FireWire audio driver.

Our hardware supports the same AV/C commands as other devices, such as
those based on the Bridgeco or Oxford chipsets.   You may be familiar
with the FreeBob project, which aims to develop a Linux driver for
FireWire hardware based on the Bridgeco chipset.  Since our devices
support the same commands, the FreeBob project could be expanded to
support Echo's hardware.

[http://freebob.sourceforge.net/index.php/Main_Page](http://freebob.sourceforge.net/index.php/Main_Page)



---

### Post by paulg on 2007-06-27
...soon.

Maybe not the answer you wanted to hear.

Echo has been co-operating with the FreeBoB developers (now called [FFADO]("http:/[URL="http://www.ffado.org")) providing specs and test hardware! Good news for sure! The FFADO developers are planning to build support for the AudioFire 4, 6, 8 and 12 and have been given test equipment by Echo. See the news post [here]("http://www.ffado.org/?q=node/184").

For those unfamiliar with it, the Free Firewire Audio Driver [O?] (FFADO) provide user space drivers for firewire devices and is the direct successor to FreeBoB. Currently devices based on BridgeCo.'s "BeBoB" semiconductor are the best supported as a result of work completed under the FreeBoB project. Developers are expanding support to additional devices giving preference to devices they are receiving assistance for from companies. FFADO is still in the alpha stage and can only be compiled from CVS. As a result you are probably better off using the FreeBob binaries unless your device is only listed as working under FFADO compatibility list.

[Supported Devices for FreeBoB]("http://freebob.sourceforge.net/index.php/List_of_Supported_Devices")
[Supported Devices for FFADO]("http://www.ffado.org/?q=devicesupport/list")

---

### Post by fsando on 2007-06-27
Thanks for explaining it to me :) 
I had planned on getting a sound card this week but will now spend the next month or so asserting the options more carefully.
I'm quite excited about how things are moving in the Linux field these days. It seems that Linux will soon be a mainstream market to most manufacturers.

---

### Post by linkx on 2007-07-02
I use the amazing Focusrite Sapphire LE with UbuntuStudio and JACK uses it just fine with the freebob driver.

---

### Post by ethanay on 2008-05-13
> Echo has been co-operating with the FreeBoB developers (now called FFADO) providing specs and test hardware! Good news for sure! The FFADO developers are planning to build support for the AudioFire 4, 6, 8 and 12 and have been given test equipment by Echo. See the news post here.

This thread was the major factor in my decision to purchase an Echo Audiofire2.  I also e-mailed Echo and told them that their decision to support Linux driver development for their hardware (as well as a high quality product) was a major factor in my decision to purchase one of their cards.  Plus, the price was right :)

---

### Post by Kevin C on 2008-06-11
Well, I made the switch just recently.  I purchased this Acer Aspire 5520--5912 and wipe Vista off the hard drive with Kill Disk.  Ubuntu Hardy Heron installed with no problems, which is great since I know very little about Linux.  Everything seemed to be working fine.  

Since my ultimate goal is to develop multi-media music therapy type of applications using programs like Pure Data and/or Processing, I figured I would start with good audio interface that provides audio and midi in/out.  The Audiofire 2 seemed just right for my needs and it appears to be supported for Linux use.  

I received it yesterday and don't really know where to start to get up and running. I have searched the web for a few hours but still don't get it.  All I have done is, I downloaded the ffado beta 6 firewire driver to my desktop and have the folder setting there.  

I am an absolute beginner using Linux.  I have been running a Pro Tools recording studio on OSX for a few years and managed to get through the various snags and bumps along the way with that.  

I wish I could find a step by step beginners tutorial to get this audio interface up and going.  I believe that it would be tremendously valuable to getting Linux off and running as a standard Dedicated Audio Workstation for the masses. 

Thank you in advance for any helpful information that you may provide.

Best Regards,
Kevin C.

---

### Post by ethanay on 2008-06-11
Hi Kevin,

Ubuntu Hardy is my main OS, and I did the same a few months ago (wiped Vista clean off and made the move!).  My 2nd O/S is 64studio 3.0beta, which I use specifically for audio work.  I just installed it, so can't say I am very experienced.

I JUST got my AudioFire2 running in 64Studio 3.0beta...Like you I was completely lost when I first started, but now have a much deeper understanding of Linux :) (it was painful at times, tho) I am willing to help you but unfortunately I am leaving the country (and internet connection...) in a couple of days for over a month.  However, I have left quite a snail trail for others to follow...here are some starts for you :)

[http://64studio.com/node/599](http://64studio.com/node/599)
[http://64studio.com/node/586](http://64studio.com/node/586)
[http://www.ffado.org/?q=node/580](http://www.ffado.org/?q=node/580)

Some tips:
1) Look out for missing dependencies when compiling from source...analyzing error messages while compiling will often give hints about a package that is missing.  Google can be very helpful for this, too :)
2) take detailed notes of changes you make to your system (files you've changed, overwritten, packages you've installed, etc) and the setup process you go through (tweak this, modify that...according to this website here, I should...etc etc).  For two reasons:  1) If you need to undo a bad choice, it is straightforward 2) if you can't undo and need to blast it all and start over, it is very helpful to get back up and running without having to remember what you did or "where the hell you found that fix/workaround you need..."
3) Make and keep current backups of your /home folder on an external hdd, so it is not a heart-pounding experience to wipe the hard drive clean as needed.  This is a good security measure for EVERYONE, not just the adventurous (because things go wrong...especially when you don't have the backup!)

Good luck, and please post back w/your experiences (successes/questions/failures, etc)!  Hopefully there will be others who can help.  Hopefully the information I have left behind can make it a little more straightforward for you :)  sign up to mailing lists (ffado...), post on forums, etc.
---------------------------
UPDATE:  [http://ubuntuforums.org/showthread.php?t=824177](http://ubuntuforums.org/showthread.php?t=824177)

The significance of this is, I have full low-latency functionality with (some) Windows standalone applications (using WineASIO) and also Windows-based VSTi's (using dssi-vst), now using my firewire interface.

Also, according to Quentin Harley from 64studio, the 3.0 release coming out later this year should have [full FFADO support out of the box]("http://64studio.com/node/586#comment-2466") :) :) very good news indeed.  I highly recommend the distro for minimal setup to working with audio in Linux.

---

