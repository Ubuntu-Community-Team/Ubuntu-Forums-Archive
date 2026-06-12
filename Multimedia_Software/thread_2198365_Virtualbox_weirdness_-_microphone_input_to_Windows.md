---
title: "Virtualbox weirdness - microphone input to Windows guest"
date: 2014-01-08
forum: Multimedia Software
---

### Post by Cloudy Brain on 2014-01-08
I'm posting this here in the hope that it might help someone. I've marked the post as solved as it is kind of a workaround.

Background: I use Windows XP in a virtual machine for my work VPN client (I don't want to even try wine for this). Very occasionally I have to attend gotomeetings with VOIP, which also is not supported under Linux. Until fairly recently the audio in/out to the Windows guest has worked fine. 

Problem: After some updates (of VirtualBox or something else I've no idea) the microphone stopped working, audio out was fine. The guest was not altered. The mic is picked up fine in Ubuntu. I've been pulling my hair out for a while over this!

Solution: By accident I found that starting the guest headless, connecting to it by RDP the microphone is picked up again. :)

This is ok as a workaround but I would like to better understand what is going on, if anyone reads this and has any ideas?!

Some details:

The virtual machine still needs the ALSA driver to function properly, and either of the Intel HD or ICH guest emulation seemed to work ok.
Enable "Remote Desktop" for the VirtualBox client
I use Remmina as the RDP client, connecting to localhost:3389 (the default remote port)
VirtualBox version is 4.3.6 r91406
Start the virtual machine from a command line with "vboxheadless -s <MachineName> &"

---

### Post by istaveren2 on 2014-03-05
I found this solution [http://www.youtube.com/watch?v=tULmqpe5Yos](http://www.youtube.com/watch?v=tULmqpe5Yos)

---

