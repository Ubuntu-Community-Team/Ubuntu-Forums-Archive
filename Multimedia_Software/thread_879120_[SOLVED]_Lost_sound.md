---
title: "[SOLVED] Lost sound"
date: 2008-08-03
forum: Multimedia Software
---

### Post by Dyffo on 2008-08-03
My sound has gone after installing upgrades.  My sound applett is crossed in red. I get an error message " NO VOLUME CONTROL G STREAMER PLUGINS AND OR DEVICES FOUND "I have tried everything but am getting no result. Any ideas out there.:confused:

---

### Post by montgoss on 2008-08-03
I have the same error after installing updates.  No clue how to fix it.  But you're not the only one.

See [http://ubuntuforums.org/showthread.php?t=879235]("http://ubuntuforums.org/showthread.php?t=879235") and [http://ubuntuforums.org/showthread.php?t=877441]("http://ubuntuforums.org/showthread.php?t=877441")

---

### Post by Dyffo on 2008-08-05
THIS SOLVED MY PROBLEM !!!!!!!!!!!!!!!!!1

Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-ubuntu-modules-$(uname -r)

---

