---
title: "How i got yamaha sound card in Ubuntu breezy"
date: 2006-02-15
forum: Multimedia &amp; Video
---

### Post by Pnut on 2006-02-15
I have been running ubuntu breezy for about 2 months now.  I have been experiencing a major sound issue on my laptop since i have installed breezy on it.  I have been working with people kind enough to have the patience to deal with nooby issues and I really like the community atmosphere.  FarEast, has provided me with most of the resources I needed to resolve this issue. FarEast also asked that I share my resolution with the forums.

My laptop is a Gateway Solo 9100.  it has a yamaha sound card as its onboard multimedia controller for audio.  It is the YM715 model.  

This is what made it work:

1) I had to create a config file for the sound device.  I named the file "sound".  The line that worked is posted here---options snd-opl3sa2 index=0 id=CARD_0 port=0x370 sb_port=0x220 wss_port=0x530 midi_port=-1 fm_port=-1 irq=5 dma1=0 dma2=1 isapnp=0---(this line was written as one line) I used Gedit to create this file.

2) I then saved the file to my desktop and opened terminal.  As root user i copied the file from my desktop to its proper destination, which is /etc/modprobe.d  -  using the commands as following.

root@pnut~$cd /etc/modprobe.d (enter)
cp -Rf /home/pnut/Desktop/sound ./ (enter)
sudo update-modules (enter)
sudo modprobe snd-opl3sa2 (enter)
alsamixer (enter)

Once alsa mixer was open i could control my sound hardware listen to music ect. 

Thanks to all the people that helped me, and i hope that this helps someone else :)

---

### Post by oldfogie on 2006-05-28
[QUOTE=Pnut]I have been running ubuntu breezy for about 2 months now.  I have been experiencing a major sound issue on my laptop since i have installed breezy on it.  I have been working with people kind enough to have the patience to deal with nooby issues and I really like the community atmosphere.  FarEast, has provided me with most of the resources I needed to resolve this issue. FarEast also asked that I share my resolution with the forums.

My laptop is a Gateway Solo 9100.  it has a yamaha sound card as its onboard multimedia controller for audio.  It is the YM715 model.  

This is what made it work:

1) I had to create a config file for the sound device.  I named the file "sound".  The line that worked is posted here---options snd-opl3sa2 index=0 id=CARD_0 port=0x370 sb_port=0x220 wss_port=0x530 midi_port=-1 fm_port=-1 irq=5 dma1=0 dma2=1 isapnp=0---(this line was written as one line) I used Gedit to create this file.

2) I then saved the file to my desktop and opened terminal.  As root user i copied the file from my desktop to its proper destination, which is /etc/modprobe.d  -  using the commands as following.

root@pnut~$cd /etc/modprobe.d (enter)
cp -Rf /home/pnut/Desktop/sound ./ (enter)
sudo update-modules (enter)
sudo modprobe snd-opl3sa2 (enter)
alsamixer (enter)

Once alsa mixer was open i could control my sound hardware listen to music ect. 

Thanks to all the people that helped me, and i hope that this helps someone else :)[/QUOTE]

Hey just wanted to say thanks for this.  Worked on my laptop for ubuntu, and also for puppy linux.

---

### Post by Pnut on 2006-06-21
[QUOTE=oldfogie]Hey just wanted to say thanks for this.  Worked on my laptop for ubuntu, and also for puppy linux.[/QUOTE]
no problem Im glad that this information was able to help someone else just as i was  helped by someone else :)


Pnut
Not so Newbie anyomore ^^

---

