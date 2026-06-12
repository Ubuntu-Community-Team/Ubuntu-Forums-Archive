---
title: "myth music problrm"
date: 2009-05-05
forum: Mythbuntu
---

### Post by liorkr on 2009-05-05
yesterday i was trying to install some plugin for mythmusic

and now i have no sound in **mythmusic** 

how can i restore the previous sound device ?

sound is working fine in video/recording/livetv

the frontend log show this error:

2009-05-05 20:02:58.443 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.443 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.443 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.444 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.444 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.444 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.444 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.444 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.444 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.444 Error opening audio device (????? ????), the error was: No such file or directory
????? ????: No such file or directory
2009-05-05 20:02:58.445 AudioOutput Error: Error opening audio device (????? ????), the error was: No such file or directory

thanks for help

---

### Post by wyliecoyoteuk on 2009-05-05
What plugin were you installing?
What audio output is set in the music setup pages?

---

### Post by liorkr on 2009-05-05
sudo apt-get install libsdl1.2debian-all libsdl1.2-dev
i have some problems with visualization and this was suppose to fix it
audio output is set for default

---

### Post by liorkr on 2009-05-06
problem solved i set the audio output to ALSA:default

and everything working

---

