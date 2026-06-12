---
title: "Sound Issues ATIIXP"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by ColdFusionEESG on 2008-02-26
Hey All,

I know there are a tonne of sound threads out there, but mine is a tad different.

Things you should know:

1) I had sound working fine before flattening my laptop and re-installing Ubuntu (Gutsy).  It was a bit troublesome to get working in the first place and unfortunately suddenly "worked".  So I never found out what the real issue was before.

2) I have read all the threads about no sound and all the "comprehensive sound guides etc.  I have checked and double checked mixer settings, sound not muted, blown out and re-installed the alsa base, made sure the card is detected, is card 0, and atiixp module is loaded....it's all good.  I've also run with the ALSA drivers that come with Ubuntu (1.0.14).....had the old system running with 1.0.15...tried that version on this system build.....now running the latest 1.0.16.

3) The oddness....
When I login the Ubuntu post login screen chanting is heard and cuts out before finishing.  Once booted I check the processes and APLAY is  listed as sleeping and when mousing over it in the list it shows /usr/share/sounds/startup3.wav (link file to startup.wav).  If APLAY is listed in the process list, sound will NOT PLAY.  if I kill that process, I HAVE SOUND!!  Now the truly fun bit.....I fire up VlC to play an MP3...I hear sound....if I let it play it eventually (5-30 seconds) cuts out.  If I perform any other action (like say opening the properties of any file on the desktop), it cuts out.

So unlike most folks with major no sound issues, I have sound....it just doesn't "stick"....I also used to have sound that worked just fine.  Somewhere I'm missing something and I'm stumped at this point.

I've attached the output from the alsa-info.sh script....hopefully someone can find something there or perhaps my description of my situation will spark an "ah ha!" in someone ;-)

TIA

Cheers

---

### Post by ColdFusionEESG on 2008-02-27
Well it turns out that VLC must be configured wrong (and I'll be damned if I can find the same options to change as I can in XMMS and MPlayer).  I used it as it came on my last install (which worked fine), but this time it's just flaky.

I'm now using XMMS for audio files and MPlayer for video....both required some re-configuring to get them to use ALSA nicely.

I must say I HATE the way sound is handled in Linux....way too many things have to be tweaked when it should be much more central (i.e. card detected...driver installed...all apps that use sound just work like in *gasp* Windows)....I sure hope the "new way" I've heard about for the next major Ubuntu release is better ;-)

That all said, my sound is working better than it did on my last install...less interference noise and Unreal 2004 has proper sound effects again (previously all sound on the map at full volume all at once)...tough to know when someone is sneaking up on you...hehe).

Anyways...thanks for all the replies....hehe

Cheers

---

