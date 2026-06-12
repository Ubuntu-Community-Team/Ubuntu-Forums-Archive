---
title: "how to link my ubuntu pc to my windows xp pc? need plz"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by tbones on 2009-02-02
how do i connect ubuntu to my windows xp pc? im not running a server, im just a normal home user

---

### Post by kbutcher5 on 2009-02-02
Create a share on either and connect to it, I recollect that you don't know how to do this.
Well to make a share on linux, right click a directory, go to properties, and share. The setup should be pretty self explanitory, if not then just ask :)
On windows it's pretty much the same!

To log onto a windows pc from a linux machine, select my places in the top bar, and select the connect to server, in the dropdown box you select windows/samba server.
Then you put in the ip of your windows machine, and the name of the share you made on the windows machine, aswell as the username of your user, then press ok and it should prompt for password.

On windows, you jsut press start -> run and type "\\$yourlinuxiphere"
Where $yourlinuxiphere is the ip of your linux machine, and press okay, then it prompts for a password and username, which is the one you use to log into the linux machine.

To get the ip of the windows machine, press start -> run and type cmd, press ok, then a black box comes up. Here you type ipconfig, then there is a place on each of your netcards that says ip address :)
On linux you open a terminal and type ifconfig, and it should give you approx the same!

Happy hunting!

---

