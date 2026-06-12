---
title: "linking issues lircrc"
date: 2008-10-24
forum: Mythbuntu
---

### Post by set321go on 2008-10-24
hello

right im having issues!

irw recognises the remote and displays name of button pressed

wen i go t myth remote does nothing

i have tried:
sudo ln -s /home/mythtv/.lirc /home/mythtv/.mythtv/lircrc

some wiki told me this was what i needed to do!! obviously not!!

what was i trying to do? i was trying to make a symbolic link from what folder to what folder? 

y do some things have a . before them?

i know the /home/mythtv/lircrc has the mapping from the remote to myth

help :)

---

### Post by anonymousdog on 2008-10-24
When logged into the deskop as the who runs the frontend, I think the correct command is 'ln -s ./.lirc/mythtv ./.mythtv/lircrc'.  That creates a link at ./.mythtv/lircrc to ./.lirc/mythtv which is the actual file containing the mappings.  My mythtv user's home directory has no lirc configuration files in it, but, in my system mythtv is the backend service account.  The interactive user of the frontend is an account of your choosing (at install).

Files prepended with a dot are hidden (i.e., don't show in a standard 'ls' command, Thunar or other file browsers by default).

---

