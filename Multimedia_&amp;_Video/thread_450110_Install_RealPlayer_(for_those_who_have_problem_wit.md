---
title: "Install RealPlayer (for those who have problem with starting realplayer)"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by gjxdotcom on 2007-05-21
First of all, go to [https://player.helixcommunity.org/2005/downloads/]("https://player.helixcommunity.org/2005/downloads/")
download the installer.
in the terminal, type:
chmod +x [REALPLAYER FILENAME]
then type:
./[REALPLAYER FILENAME]
then ENTER

it will ask where do you want the software to be installed, or you can just hit ENTER to install it on the Desktop.
later,it will ask you to confirm, just hit F
Now you have installed the RealPlayer, go to the folder where you chose eariler. double click "realplay"
if RealPlayer starts without any problem,then you are luck,LOL
if you can't get it started like me T_T then don't worry,just follow the next step.
the reason is because realplayer doesn't like SCIM!!
use gedit or other editor to open "realplay" file, on the next line of #!/bin/sh, type
export GTK_IM_MODULE=xim
save it and close it.
now try to start it again. It should start now.

My first post here, Thank you....

---

### Post by el_rawyy on 2007-09-21
Thank you very much it was so helpful.
Thanks again.

---

