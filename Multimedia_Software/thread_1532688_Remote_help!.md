---
title: "Remote help!"
date: 2010-07-16
forum: Multimedia Software
---

### Post by lostincable on 2010-07-16
Okay newb alert so be gentle....

Been at this for a few hours so hoping some one can put my mind at ease :)

I am running Ubuntu 10 and running XBMC. I am using a Harmony 525 remote to control XMBC and that is working fine with a media center IR receiver and the remote acting as media center remote.

So now I want to be able to launch XBMC by pressing a specified button on the remote so far I have done the following,

1) Followed some guides on the net so I have a kill and start script for XBMC located in /home/user/scripts/
2) Created an .lircrc file in /home/user/
3) Added into the .lircrc file

begin
remote = mceusb
button = Red
prog = irexec
repeat = 0
config = /home/user/scripts/startXBMC.sh
end

4) I then rebooted and pressed the Red button at the ubuntu desktop but no joy. 


I have verified running the script from the terminal launches XBMC fine but can not get the remote to co operate.

Any help appreciated!

---

