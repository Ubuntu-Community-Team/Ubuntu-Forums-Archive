---
title: "I broke Lirc, pls help"
date: 2009-12-25
forum: Mythbuntu
---

### Post by mfaust731 on 2009-12-25
Hey Everyone,
K heres the deal.
Everthing was going ok, but I was trying to add some buttons for a new remote to my config - somewhere in the process I have screwwed lirc up altogether.
I have disable/reenabled through  Mythbuntu control center but it doesnt fix it. I have verified that the config files are there in /etc/lirc/
and in /home/.lirc/

irw used to work fine but now it just sits there like no button was pressed.
yes I have new batteries:)

I have restarted lirc via
sudo /etc/init.d/lirc restart
which says OK  but I have noticed it doesnt say anything about lirc modules, which I have seen in some displays.

any idea how to proceed form here?

---

### Post by nickrout on 2009-12-27
try a reboot

---

### Post by mfaust731 on 2009-12-27
ha, thanks for the suggestion - but it was more than a reboot.
Tried for a while to fix it, but in the end I gave up and reloaded ubuntu.
It works fine now, not sure what the issue was but it had something to do with the module not loading.

I am back to my original issue now.
I have a working lirc config with the hauppauge grey remote.
I have another remote with way more buttons ( besides the ones It learned from the grey hauppaue) but am unable to find a way to add them to my config
I cant get irrecord to work.

---

