---
title: "Sound missing"
date: 2010-03-04
forum: Multimedia Software
---

### Post by P.Virie on 2010-03-04
At first my ubuntu did well in everything; that was before I found out that the sound quality was rather poor. So I decided to update alsa driver.

I executed this command
cat /proc/asound/card0/codec#* | grep Codec
and there was something return, I guess it is my alsa's spec (Kiwiwi something at the ending)

But then I found this script on the Internet and executed it.

# This script will recompile the ALSA drivers for Ubuntu
# This procedure was gotten from
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
#
# Authored by Bob Nelson  [EMAIL="admin@stchman.com"]admin@stchman.com[/EMAIL]
#
# This script updated 9/6/2007

script_name="alsa_setup.sh"
.... (It's quite long and unpleasant to show here; basically, it loads, compiles, and installs  driver files.)


After restart, everything has gone.
The output of this command cat /proc/asound/card0/codec#* | grep Codec show nothing but:
cat: /proc/asound/card0/codec#*: No such file or directory

Does someone has any suggestion?

---

### Post by Yellow Pasque on 2010-03-05
You used a really old script? Try something current: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by P.Virie on 2010-03-05
> **Temüjin said:**
> You used a really old script? Try something current: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)


Nice! Thank a lots. It's working now, and the sound quality is great.

---

