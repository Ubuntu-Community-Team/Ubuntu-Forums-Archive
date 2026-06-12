---
title: "Can't hear sound form a site."
date: 2009-05-27
forum: Multimedia Software
---

### Post by FernandoLB on 2009-05-27
I installed ubuntu-restricted-extras and still can't hear sounds form this site:
[http://http://say.expressivo.com/]("http://http//say.expressivo.com/")
It is not the video that I cannot see/hear. It is the text it should read for me. I can see/hear videos just fine. I even tried to remove my $HOME/.mozilla and $HOME/.opera but it did not work either. 

I used to had it working on a previous install (9.04) of Ubuntu. I just  reinstalled everything. So it is the same Ubuntu version as before. Any help would be appreciated.

---

### Post by timcredible on 2009-05-27
what app reads the text?  check to see what sound driver it's trying to use.  although linux can have many apps using audio at once, only 1 audio driver can run at a time, so all apps trying to use sound must be configured to use the same audio driver.  i think 9.04 default is pulse.

---

### Post by FernandoLB on 2009-05-27
I'm not sure what app reads the text. I downloaded that sound (downloadHelper) and it is an .wav file, which I can play with any of the player I have installed. Also, I'm trying to reproduce just that one sound. I'm not playing anything else together with that.

---

