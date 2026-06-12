---
title: "Freenx server Help"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by bikerpego on 2010-02-27
Hello world!
I have installed Freenx-server on my ubuntu 9.10 and i am  unable to create custom keys.
The guide is at "https://help.ubuntu.com/community/FreeNX"

I enter:

sudo dpkg-reconfigure freenx-server

into the terminal, follow the prompts choosing "Create New Custom Keys"
and then "SSH"

afterward i get an error in terminal that says:

update-rc.d: warning: freenx-server stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)
Not starting freenx-server, it's already started.

keys remain the default and the file " /var/lib/nxserver/home/custom_keys/client.id_dsa.key " does not exist.

Any help would be greatly appreciated.

---

### Post by bikerpego on 2010-03-01
Someone can help me?

---

### Post by missfroguk on 2010-03-09
Have a look at this thread which deals with the same problem, you may find you answer
[http://swiss.ubuntuforums.org/showthread.php?p=8707157]("http://swiss.ubuntuforums.org/showthread.php?p=8707157")
Cheers

---

