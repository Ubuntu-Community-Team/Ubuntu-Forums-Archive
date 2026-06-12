---
title: "ubuntu 11.04 noise on mic input channels"
date: 2011-05-20
forum: Multimedia Software
---

### Post by ondra_spa on 2011-05-20
Hello  *just have updated to 11.04. Before I already had problems with mi sound device*, I had always to remove pulse and use alsa, if not would to deal with lots of noises and not working volume controls. Now when I updated to natty I was surprised that sound controls work.. that everything works. But I did not check the mic. When I tried to use skype I realized that mic is not working, mic is present in pulse and alsamixer, also working but I just get a loud noise, I tryed different mics, I tryed removing alsa and pulse and installing again, but have not tried removing pulse and using alsa because I'm fed-up of having to improvise and having to use alsamixer. Here is my soundcard.
I wold like to give thanks in advance for anyone who will help solving this issue.

lspci output -  00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

            
   aplay -l output  - karta 0: SB [HDA ATI SB], za&#345;ízení 0: AD198x Analog [AD198x Analog]
                            Podza&#345;ízení: 0/1
                            Podza&#345;ízení #0: subdevice #0
                            karta 0: SB [HDA ATI SB], za&#345;ízení 1: AD198x Digital [AD198x Digital]
                            Podza&#345;ízení: 1/1
                            Podza&#345;ízení #0: subdevice #0
If you need any more info just tell me.

---

### Post by kottenator on 2011-07-12
I have the same problem. And still have not found any other solution than to uninstall Pulse and use ALSA (but I don't want to do this)

---

### Post by lidex on 2011-07-14
If everything works except skype, then it's skype that's the issue. Disable the setting to allow skype to control audio levels.

---

