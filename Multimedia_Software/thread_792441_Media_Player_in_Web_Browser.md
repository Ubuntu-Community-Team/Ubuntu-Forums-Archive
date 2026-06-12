---
title: "Media Player in Web Browser"
date: 2008-05-12
forum: Multimedia Software
---

### Post by Silpheed2K on 2008-05-12
I downloaded and install VLC media player on my Linux. I was wondering,  for web pages with the movies embedded in them, how do i get VLC media player to play them in my browser cause I want to view WMV and MOV files embedded in webpages without a problem.

Also is it normal in linux to have only one application use audio at a time?
I noticed if I have my browser playing audio (through flash) and I pen a separate media player on my desktop.. that there will be no audio.. is this normal for linux (just got into linux 2 days ago and loving it)

Thanks to whoever helps.

---

### Post by llama320 on 2008-05-12
I'm not sure about the embedded apps thing, but I can comment on the flash stuff..I had that problem on hardy at first

Go to System > Preferences > Sound and change all the "sound playback" options to pulseaudio

If that doesn't work, you may want to reinstall flashplugin-nonfree after doing the pulseaudio stuff. I think that's everything I did to get it working...

Hopefully that'll fix it

---

### Post by Silpheed2K on 2008-05-13
> **llama320 said:**
> I'm not sure about the embedded apps thing, but I can comment on the flash stuff..I had that problem on hardy at first

Go to System > Preferences > Sound and change all the "sound playback" options to pulseaudio

If that doesn't work, you may want to reinstall flashplugin-nonfree after doing the pulseaudio stuff. I think that's everything I did to get it working...

Hopefully that'll fix it
I tried that and i still have the same problem with the audio.
Also, what does redirecting it to this Pulse Audio do?
and also does this reduce sound quality or anything? (such as not hardware accelerated or anything)

edit: also do i need to restart my computer for it to take effect?
edit 2: Also I changed it back to autodetect because my Linux or my windows wouldn't boot after I changed it to that and restarted.. I dunno what's up with it but i'm not going to touch that option again.

---

### Post by Silpheed2K on 2008-05-13
nevermind i found a VLC plugin
edit: removed VLC plugin cause it basically breaks firefox due to the fact it has no menu and just plays videos with no options

---

