---
title: "No Sound (Conexant High Definition Audio)"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by chicobo329 on 2008-01-23
Conexant High Definition Audio provides the sound on my HP Pavilion dv2000 laptop on Ubuntu 7.04. I finally installed everything on my external successfully but there's still no sound. The speaker icon on the taskbar still registers volume settings and the like, but no sound plays at all.

When I go to the Sound settings it detects Conexant (because it's selectable in the various options) but testing every one shows there's just no sound. What can I do to get sound playing?

---

### Post by balaknair on 2008-01-23
This thread should have the answer
[http://ubuntuforums.org/showthread.php?t=455147](http://ubuntuforums.org/showthread.php?t=455147)

If it solves your problem, please reply and mark this thread as solved

All the Best

---

### Post by chicobo329 on 2008-01-23
No dice, I still have no sound. In particular, every step of the thread you linked me to worked except for one, where I had to input: "/usr/sbin/alsaconf" as root. It would tell me no such directory exists. I would assume 'usr' to be 'user' which means replace it with my name but that still got me the same error message.

---

### Post by balaknair on 2008-01-23
OK try this
sudo modprobe snd-hda-intel

---

### Post by chicobo329 on 2008-01-23
Doesn't work. I assumed so since 'intel' involved the processor. My HP runs on an AMD.

---

### Post by balaknair on 2008-01-23
Actually the intel referes to the audio driver module(snd-hda-intel) your card uses

Could you type in these commands and post the output
aplay -l
cat /proc/asound/card0/codec#* | grep Codec

---

### Post by chicobo329 on 2008-01-23
frankie@frankie-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

frankie@frankie-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Conexant CX20549 (Venice)

---

### Post by balaknair on 2008-01-23
In a terminal type
sudo nano /etc/modprobe.d/alsa-base

This will open the alsa-base file using nano in the terminal. Scroll down down to the bottom of the page with the down arrow key and paste this as the last line
options snd-hda-intel model=laptop

save and exit and reboot

---

### Post by chicobo329 on 2008-01-23
Still no sound. It might be worth noting that the alsa-base file had nothing inside it. Therefore I could not scroll all the way down, so I just pasted what you told me to onto there.

---

### Post by rzrgenesys187 on 2008-01-23
(Note: Info i'm putting here is just from this thread: [http://ubuntuforums.org/showthread.php?t=349491&highlight=p105-s6177](http://ubuntuforums.org/showthread.php?t=349491&highlight=p105-s6177))

I downloaded the custom dsdt file from here: [http://acpi.sourceforge.net/dsdt/view.php?id=802](http://acpi.sourceforge.net/dsdt/view.php?id=802) and ran these commands in the terminal (replace the Toshiba-P105-S6177-3.30-custom.asl with whatever your file is named obviously)

```

sudo apt-get install iasl (if you don't have iasl already installed)
iasl Toshiba-P105-S6177-3.30-custom.asl
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo dpkg-reconfigure linux-image-$(uname -r)

```

I hope this helps in some way, it works great for my toshiba and on the site where i got my custom dsdt file there are many different ones for different laptops so you should check it out.  I know for my laptop, I have sound out of the box (so to say) for the latest Hardy Alpha so it looks like they are addressing this issue.

---

### Post by balaknair on 2008-01-23
OK I think maybe a small error crept in somewhere along the way(it's possible with the Command line)

The Alsa base file shouldn't be blank as far as I know if everything has been installed properly.
Add this line to the alsa base file like you did earlier
options snd-hda-intel probe_mask=1
save and exit and reboot

If it doesn't work, maybe you could try this howto
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
It should work if you're using Feisty(Ubuntu 7.04)
Just use the alsa 1.0.15 packages instead of 1.0.14
According to the Alsa documentation I've just been going through the issues with Conexant HDA cards should be fixed in 1.0.14 and later, but 1.0.15 is the latest stable version. 
Before that you might want to remove the previous install 
sudo apt-get remove --purge alsa-base alsa-tools

I have to go now(gotta work), but I'll check this thread as soon as I get back

All the best

EDIT: You could try out the steps mentioned by rzrgenesys first(I have no idea about what it really does, but it seems to work for Conexant cards in Feisty, so you should give it a shot)
Wishing you luck

---

### Post by ahervey85 on 2008-01-23
quick question, how do you save the alsa base file for some reason i cant figure it out

---

### Post by balaknair on 2008-01-23
After editing the file, press Ctrl+o and then press Enter/Return to save the file to disk, then Ctrl+x to exit
This is if you're using nano to edit
You can also use gedit(replace nano with gedit in the command) which gives you a graphical option.

---

### Post by chicobo329 on 2008-01-26
I added to the alsa-base file first, but I got no change: still no sound. So now I'm attempting the how-to you linked me to. I'm not going with RZR's suggestion yet because I'm not sure what to do here (keep in mind that all I've been doing right now is just copy-pasting code, I have no idea how to work Linux Terminal or other advanced functions).

---

### Post by farsight on 2008-02-21
Hi all. I'm effectively totally new to Ubuntu. I've managed to get everything but the sound working on my HP dv2500. Having searched around last night and after trying several of the other options to no avail i'm writing to see if anyone has overcome this problem. I'm running Ubuntu 7.10 at the moment, which for me runs absolutely fine other than this bizarre problem. 

Hardware: Conexant High Definition Audio
Problem: Not working
Question: Has anyone managed to get this sorted yet and if so how?

Thanks everyone in advance for any help you can offer me. 

Regards Farsight

---

