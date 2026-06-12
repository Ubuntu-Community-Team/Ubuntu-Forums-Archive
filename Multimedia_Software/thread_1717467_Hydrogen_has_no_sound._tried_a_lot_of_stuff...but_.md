---
title: "Hydrogen has no sound. tried a lot of stuff...but i am a noob."
date: 2011-03-29
forum: Multimedia Software
---

### Post by humanisfood on 2011-03-29
i have the OSS drivers installed for my M-audio Delta 66 card. took a lot of tweaking to get it my sound to work well.

installed hydrogen and no sound. read that i need jackd. messed around with that and couldnt get it to work either. no matter what i do i cant get sound.

i am a super duper newbie at linux. usually i can find some writeup about how to make something work but not luck with this issue. thanks so much if you can help out.

a little background on myself and why i am such a newb:
I use to download pirated copies of windows and pretty much any software i wanted. kinda thought it was time to stop stealing software when there was so much out there available for free. i am trying really hard to stick with linux. but i have a lot to learn. my friend who is big into linux told me "the linux community needs people like you" i am pretty much the average person, not a big computer nerd, but i am really into the unbuntu philosophy.

well TIA,
Damien

---

### Post by humanisfood on 2011-03-30
ok ill try to be more specific. this the error i get when i just try to start Hydrogen with OSS drivers.

damien@damien-GA-770TA-UD3:~$ hydrogen -d oss

Hydrogen 0.9.4 [Sep 30 2010]  [[http://www.hydrogen-music.org]](http://www.hydrogen-music.org])
Copyright 2002-2008 Alessandro Cominu

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
(E) OssDriver	connect ERROR_IOCTL: unable to set BlockSize 
(E) 	void H2Core::audioEngine_startAudioDrivers() Error starting audio driver [audioDriver::connect()] 
(E) 	void H2Core::audioEngine_startAudioDrivers() Using the NULL output audio driver 
(E) 	void H2Core::audioEngine_startAudioDrivers() m_pMainBuffer_L == NULL 
(E) 	void H2Core::audioEngine_startAudioDrivers() m_pMainBuffer_R == NULL 
(E) 	void* H2Core::alsaMidiDriver_thread(void*) Error opening ALSA sequencer: No such file or directory 
(E) 	void H2Core::audioEngine_setupLadspaFX(unsigned int) nBufferSize=0 
(E) NullDriver	setBpm not implemented yet 

Bye...
damien@damien-GA-770TA-UD3:~$


there seems to be some kinda fix here, but i dont understand it. arg.
[http://72.32.12.210/archives/openbsd/2007-04/2109.html](http://72.32.12.210/archives/openbsd/2007-04/2109.html)

thanks to anyone who can help.

---

### Post by lidex on 2011-04-01
You may want to try the hydrogen bug-tracker/forums.
[http://www.assembla.com/spaces/hydrogen/tickets/119-oss-driver-won-t-start-due-to-wrong-block-size](http://www.assembla.com/spaces/hydrogen/tickets/119-oss-driver-won-t-start-due-to-wrong-block-size)

---

### Post by humanisfood on 2011-04-01
> **lidex said:**
> You may want to try the hydrogen bug-tracker/forums.
[http://www.assembla.com/spaces/hydrogen/tickets/119-oss-driver-won-t-start-due-to-wrong-block-size](http://www.assembla.com/spaces/hydrogen/tickets/119-oss-driver-won-t-start-due-to-wrong-block-size)
thank you for your reply. the link you have shared is the same link i posted as well. there is some kinda workaround but the guy was using FreeBSD and i dont understand how to do what he did in Ubuntu. any further help would be great appreciated.

---

