---
title: "problem with skype"
date: 2008-07-21
forum: Multimedia Software
---

### Post by Deadweight on 2008-07-21
I'm running xubuntu 8.04 and I just installed Skype for Linux, which seems to work for text, but when I try to make a call or someone calls me I get the error message "problem with audio capture" and the call fails. The other party gets a message saying I have a problem with my audio recording device (I don't actually have a mic plugged in atm, but I've been told that I can still make calls without one). Has anyone experienced this problem or have any suggestions?

thanks

---

### Post by liswitalis on 2008-07-22
Hi,
I am having exactly the same problem as you.
I have played with all skype audio settings - no joy.
Any ideas ?
Regards,

---

### Post by fantan on 2008-07-22
Hi for all You,

There is a big problem between Skype and pulseaudio in Hardy.
The solution is to use skype-static-oss package insteed of ordinary Skype.
If you add the mediubuntu repositories to sources.list, make an apt-get update, after that you could remove the ordinary Skype and install insteed the Skype-static-oss and it's dependencies.
In the Skype options on the Sound devices tab you have to setup the sound input to the /dev/dsp1 and the sound output and ring to the 
/dev/dsp. That's all!

Best regards,
fantan

---

