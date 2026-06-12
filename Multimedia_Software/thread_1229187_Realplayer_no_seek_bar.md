---
title: "Realplayer: no seek bar?"
date: 2009-08-01
forum: Multimedia Software
---

### Post by m_ad on 2009-08-01
[This]("http://ubuntuforums.org/showthread.php?t=1077239") guy had the same problem with no response :(

Running 8.04, after enabling medibuntu repositories, I installed the package 'realplayer.' For some reason, this realplayer doesn't have a seek bar to ffw/rew.

No matter what kind of media I play, there is no seek bar. Online streams, local files, etc..

Is there a way to fix this?

RealPlayer 11.0.0.4028 (GOLD)

---

### Post by vinutux on 2009-08-02
> **m_ad said:**
> [This]("http://ubuntuforums.org/showthread.php?t=1077239") guy had the same problem with no response :(

Running 8.04, after enabling medibuntu repositories, I installed the package 'realplayer.' For some reason, this realplayer doesn't have a seek bar to ffw/rew.

No matter what kind of media I play, there is no seek bar. Online streams, local files, etc..

Is there a way to fix this?

RealPlayer 11.0.0.4028 (GOLD)

1. uninstall realplayer from mediubuntu

2. download deb from official site **[http://www.real.com/linux]("http://www.real.com/linux")** 

3. install deb if you are running 32 bit...if you are running 64 bit

right click extract here....

4. open extracted folder ...again right click extract [COLOR="Red"]data folder[/COLOR]

5. open extracted data folder /opt/real/RealPlayer ...and run realplay ...it run smoothly

6. copy Realplay folder to somewere...like /opt (with gksu)...or home folder and make a launcher in menus.

---

