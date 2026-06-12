---
title: "Need software to capture video"
date: 2008-05-20
forum: Multimedia Software
---

### Post by 47_MasoN_47 on 2008-05-20
I need some software to capture video from my video capture card.  I've tried using Cinelerra but I have no idea how to work it and it crashes pretty much every time I change a setting.  I installed tvtuner just to see if the card was working properly.  It works just fine and shows the video in nice quality, but I can't record it with that software.  Is there any software that I can use to capture from my VCC?  I really don't want to have to rely on Wind0ze for this.

---

### Post by 47_MasoN_47 on 2008-05-21
Bump, surely somebody knows of some.

---

### Post by 47_MasoN_47 on 2008-05-23
IS THERE NONE!?  This is pretty urgent!  I need the videos off this DVR by next Tuesday or my boss is not going to be happy.

---

### Post by xc3RnbFO8P on 2008-05-23
I use Kaffeine and Me-Tv, but I got DVB TV card

---

### Post by xc3RnbFO8P on 2008-05-23
Try [Lives]("http://www.getdeb.net/app/LiVES"), I dont know if it works

---

### Post by 47_MasoN_47 on 2008-05-23
Me-TV doesn't work with my capture card.  I'm downloading LiVES now.  Thanks for giving me some replies I was starting to think I was never going to get any!

---

### Post by xc3RnbFO8P on 2008-05-23
> **47_MasoN_47 said:**
> Me-TV doesn't work with my capture card.  I'm downloading LiVES now.  Thanks for giving me some replies I was starting to think I was never going to get any!


Change your avatar :)

---

### Post by 47_MasoN_47 on 2008-05-23
I like my avatar though :P

Does LiVES record anything other than through firewire?  I don't seem to see anything other than recording through that or DVDs.

---

### Post by Dai777 on 2008-05-23
when you say video capture card do you mean from a video camera into your computer. If so kino will do it but you need to set it up for fire wire.

If you mean sd card of the like then ubuntu should pick it up automatically (should do, doesn't always).

just in case here are the instructions for setting up kino:
> To set up kino to use raw1394 on Ubuntu Hardy Heron do the following:
type in the following in to the terminal:

sudo gedit /etc/udev/rules.d/40-permissions.rules
type in your password

copy the line 
KERNEL=="raw1394",			GROUP="disk"
and paste it so the are are two of them.

now change the second line so it reads.
KERNEL=="raw1394",			GROUP="video"

and comment out the first line

reboot your system and Kino should be set up to capturte video.

here is an example:
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
#KERNEL=="raw1394",			GROUP="disk"
KERNEL=="raw1394",			GROUP="video"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

---

### Post by 47_MasoN_47 on 2008-05-23
I don't want firewire, I don't have any firewire ports on this computer even if I did have a firewire device.  It's an old DVR that has standard RCA ports on it.  I'm using a Leadtek TV2000 XP RM video capture card.

---

### Post by xc3RnbFO8P on 2008-05-23
Try this in terminal:
> cat /dev/video0 > myvideo.mpg  <return>

Use CTRL + C to stop, and play
> mplayer myvideo.mpg

---

### Post by 47_MasoN_47 on 2008-05-23
Rats I just had to leave work a little while ago.  I'll try it on Monday when I go in.  If that doesn't work I guess I'll just take the card out and put it in a Windows machine.

Thanks for the help, hopefully that suggestion will work.

---

