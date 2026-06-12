---
title: "cant capture video using kino"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by sirab on 2007-05-27
I have to start it using gksu kino and I can activate and control my tape using av/c and when i go in preferences it does know that my camera is connected.

When I press capture the tape starts playing in my tape but the screen on kino stays black and when the "waiting for dv" counter stop the video stops playing.

What should I do?

---

### Post by fenian on 2007-05-27
Have you added permission to /dev/raw1394?

If not do that with these commands...
> 
chown root:video /dev/raw1394
chmod 666 /dev/raw1394

---

### Post by fenian on 2007-05-27
I just found this might help...

In order to use Firewire DV cameras on Ubuntu with this
build, you must have read and write permission to
/dev/raw1394, which is not enabled by default. You can run
Kino with sudo to workaround this. Alternatively, change the
system configuration which governs the device file
permission, even if you reboot:

> sudo gedit /etc/udev/rules.d/40-permissions.rules


Press Ctrl+F and search for "raw1394"
Read the security warning. Realize the security risk only applies when you have a Firewire storage device connected and the raw1394 module loaded. If you decide to accept this risk, change 'GROUP="disk"' to 'GROUP="video"'.
Click Save and close gedit.

---

### Post by sirab on 2007-05-27
I get 

> sirab@sirab-laptop:~$ chmod 666 /dev/raw1394
chmod: changing permissions of `/dev/raw1394': Operation not permitted

when i try that. thanks for all your help today

---

### Post by fenian on 2007-05-27
sorry should be sudo for both commands.

---

### Post by sirab on 2007-05-27
When I run in sudo i get the old error message.

and when i went to change to group=video all it said group=users not group=disc.

i did change group=users to group=video but i havent tried it out yet because i know if i plug my card in now im going to have to reboot and im downloading something

lol its at 53 percent im not waiting another hour for it to finish =]

---

### Post by sirab on 2007-05-27
i did the sudo chmod 666 /dev/raw1394 but i cant test it out yet... 56% lol

---

### Post by sirab on 2007-05-28
still doesnt work =/

---

### Post by sirab on 2007-05-28
one last bump

---

