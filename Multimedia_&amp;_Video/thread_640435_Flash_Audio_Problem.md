---
title: "Flash Audio Problem"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by rheywood on 2007-12-14
Hello.

I'm having what seems to be a simple problem getting audio to work in Flash videos (Youtube, BBC iPlayer, etc). Sound works fine in Rhythmbox, etc so that's fine.

I've searched these forums for the last hour or so, and also searched Google but to no avail.

When searching I found the article from the Ubuntu help site [https://help.ubuntu.com/community/RestrictedFormats/Flash#head-f036b17c3150dd72f58d952a0e13094568c9f92e]("https://help.ubuntu.com/community/RestrictedFormats/Flash#head-f036b17c3150dd72f58d952a0e13094568c9f92e"), and followed the guide as instructed. When running the command of cat /proc/asound/cards I get the following output:
> 
 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with ALC655 at irq 22
 1 [Speaker        ]: USB-Audio - Z-10 USB Speaker
                      Logitech Z-10 USB Speaker at usb-0000:00:03.0-2, full speed
 2 [Phone          ]: USB-Audio - VoIPVoice USB Phone
                      PDT VoIPVoice USB Phone at usb-0000:00:03.1-3, full speed



Whenever I try to set the above commands with setdefault and restart Firefox, I can still never hear the audio on the websites. An example of the command I've tried was asoundconf set-default-card "Speaker"

 Also, when I run the "asoundconf list" command I am given a simpler output, with just the following:

> 
Names of available sound cards:
SI7012
Speaker
Phone


Any ideas what I am doing wrong here? The card I want to use is the one related to " Logitech Z-10 USB Speaker". It's probably something simple but I can't for the life in me figure it out. I'm running Ubuntu 7.10 and the latest version of Firefox/Flash - if you need any more information I'll add it to the post. If anybody can help it would be greatly appreciated.

-Richard

---

