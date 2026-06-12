---
title: "OSS and ALSA conflick"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by gaillard on 2007-01-27
Hi I posted this over at the OSS help page but I kind of need a bit of some speedy help...

I was installing OSS and I didn't do anything with disabling alsa before hand, perhaps I should have.  Please give me a hand, thanks

"Hi,

I just tried to install OSS because I want to test it out with my chaintech av 710 but It said at the end of the install

Failed to disable conflicting sound drivers
Reboot and try running soundon again

because all the modules were in use I assume by ALSA.

Do I need to remove alsa or something else?

Also, I am planning on buying a cmi8788 based sound card (sondigo inferno) and want to use the OSS drivers for it. I will need to play sound files through any player and then (I assume with JACK?) route the audio to BruteFIR and then out to the sound card with the OSS drivers. Is this going to be ok??

Thank you so much for the help, sorry for my ineptitude.
Back to top 	
View user's profile Send private message 	 	
gaillard



Joined: 27 Jan 2007
Posts: 2

	
PostPosted: Sat Jan 27, 2007 3:32 pm    Post subject: bigger issue 	Reply with quote Edit/Delete this post Delete this post
Ok after I rebooted I get a screen that says, my session only lasted less than 10 seconds and it gives me this error, this is the last of the 4 lines it gives.

x-session-manager: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory


Now ALL I did before this was install OSS by the way of the sticky and I got the error I posted in my last post before I rebooted. I rebooted and this.

All I can log into now is a fail safe console.

Please help me get the system back up, and with OSS working and ALSA off or gone, because I have a lot of work to do and this laptop can't do it.

Thanks and sorry for the trouble."

I realise I probably made a mistake installing OSS but I wanted to try the OSS drivers for the chaintech because the alsa ones won't allow audio through the 7 & 8 ports.  I need to use that DAC and I am sure there is a way but the info I found was old and didn't work.  There was probably a better way to try the oss drivers in emulation or something, I know... sorry.

Should I just reinstall?  I still can't get alsa configured if I do though.

---

### Post by gaillard on 2007-01-27
nevermind this I have reinstalled and there is a new asound.state on the third page of this that I didn't see

[http://166.90.205.111/forums/showthread.php?t=142981&page=3](http://166.90.205.111/forums/showthread.php?t=142981&page=3)

I will test later on.

---

