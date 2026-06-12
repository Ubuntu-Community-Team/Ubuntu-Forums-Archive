---
title: "help with atsc tuning"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by cac67 on 2007-02-18
I've recently purchased an atsc-110 tuner card for my computer and I'm having a little trouble with it.  I've run scan in the dvbapps pkg, but I'm getting a lot more output than the instructions I've been able to find indicate I should see.  At the end of the scan it showed me 239 services found, but in the list only 1 had a station identified, and it came off the cable.  I combined all the non-irc and hrc lists that came with the package and ran that, and it found 539 services.  Many of course were duplicated since I didn't edit out the duplicates in the freq list, but again only one station identified, this time a different one off the antenna.

Here's a small sample of my channels.conf file:

[0001]:627000000:QAM_256:181:184:1
[000b]:633000000:QAM_256:98:99:11
[000c]:633000000:QAM_256:101:104:12
[000e]:633000000:QAM_256:117:120:14
[000f]:633000000:QAM_256:106:107:15
[0010]:633000000:QAM_256:114:115:16
[0071]:633000000:QAM_256:0:132:113
[0070]:633000000:QAM_256:0:126:112
WUFTH:567000000:QAM_256:66:67:102

I've spent a couple of days going through the list and changing the bracketed parts to letters (A,B,C..etc.) and tried tuning them.  I've found a feed from a local station, 3 feeds from music choice (all the same heavy metal station,) and what I thought was 5 more pbs channels (wuft is pbs.)  Then I noticed that any time I renamed a freq H it tuned pbs, but if it was named anything else it wouldn't tune anything.  My sanity is rapidly failing at this point, but the voices in my head tell me sanity is over rated anyways.  :)  

[These]("http://linuxtv.org/~mkrufky/atscscan/") are the instructions I've been using. 

 I'm new to Linux and even newer to HD, so I'm kind of running a little blind here.  I've tried running a script I found that's supposed to run through the channels.conf file but it just keeps saying command not found.  Is this not working because I'm using bash but it's an sh script?  Does that even matter?

Also, if anyone has any suggestions for places to look (other than mythtv, I'm already there) I'd appreciate the pointer.

---

### Post by barney_1 on 2007-02-19
Hi there,

Sorry, can't offer any help but had a couple of questions for you.  I thought that the ATSC-110 was not supported with linux drivers.  Can you let me know of any support sites (other than the one listed) that you are using for it?  

Also, are you using this card to tune digital cable television channels in the US?  If so, did you have to go through your cable company to get your card to decode the channels?

Thanks!

---

### Post by cac67 on 2007-02-19
Atsc-110 is supported, but a little difficult.  The [[COLOR="Blue"]Mythtv wiki[/COLOR]]("http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110") has instructions for how to get it running.  I don't actually have it running in myth yet, still playing around with tuning first.  That's probably going to change by this weekend, though, thanks to the fine folks at [[COLOR="Blue"]avs forums[/COLOR]]("http://www.avsforum.com/avs-vb/forumdisplay.php?s=&daysprune=&f=45"), one of whom was kind enough to post the channels.conf file he generated for my cable provider.

My goal with this was to tune the cable provided hd channels, but in going through the scan results I've found a few music choice channels, which I thought were only digital cable.  Actually, it's the same channel on two frequencies, one of which has it on two channels.  The digital channels are mostly encrypted, so while my scan picked up 239 entries most dont play anything.  Cable cards aren't supported on pc's yet, although I think I saw something the other day about ati coming out with one.  To get those channels now would require using a set top box.

---

