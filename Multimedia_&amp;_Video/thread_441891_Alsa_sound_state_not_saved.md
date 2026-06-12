---
title: "Alsa sound state not saved"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by feffer on 2007-05-13
After upgrading to Feisty, sound was muted. My card, a Dell Sound Blaster Live! is working, and the Alsa module is loaded. Alsamixer shows the sound channels open to the correct levels. However, the control for the Analog line is also open. I know from long experience that this will block my speaker output. So I muted this channel and then saved the state with "sudo alsactl store." After muting Analog, sound worked normally through the speakers. After logging out and back in, or rebooting, the sound state is lost and my speakers are muted again. 

In the past, using alsactl store has always saved my settings. What's wrong? I noticed that settings are saved to a file called, "/var/lib/alsa/asound.state" This /var file doesn't survive rebooting. 

I also saw a post about Feisty and sound discussing the .asoundrc file, [http://ubuntuforums.org/showthread.php?t=418360&highlight=asoundrc+feisty](http://ubuntuforums.org/showthread.php?t=418360&highlight=asoundrc+feisty) and tried those suggestions, but no joy. My sound system seems to work fine, it is just that settings are not saved? Any ideas?

Thanks,
feffer

---

