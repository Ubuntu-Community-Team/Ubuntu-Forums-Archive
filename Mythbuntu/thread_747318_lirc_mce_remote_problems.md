---
title: "lirc mce remote problems"
date: 2008-04-06
forum: Mythbuntu
---

### Post by JAKEOTR on 2008-04-06
Hi, I'm having some weird problems with the MCE remote/blaster and lirc. I have a Dish box that I use the blaster to change channels with and when it works, no problem. It dies intermittently (maybe every few days) and I get the wrong recordings. I cant find any anomalies in the logs (unless im missing it)....it just seems to break without a sound. Using the remote to control Myth seems to continue to work flawlessly....unless I do /etc/init.d/lirc restart and that kills the remote all together, I have to reboot to get it back...and its not just me...I set up a friends system (with an MCE remote) a couple of days ago and his does the same thing when restarting lirc. Hes using 0.8.2...I'm using 0.8.3pre1......please help this is making me nutz!

---

### Post by KillerKiwi on 2008-04-06
If you restart lircd you will also need to restart the mythfrontend.

---

### Post by JAKEOTR on 2008-04-07
Thanks...I'll give it a try when I can get to my system....any ideas about the blaster? I was hoping upgrading to the latest lirc version would solve it.

---

