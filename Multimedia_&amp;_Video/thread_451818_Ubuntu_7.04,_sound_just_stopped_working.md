---
title: "Ubuntu 7.04, sound just stopped working"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by xmrkite on 2007-05-22
hello, i have ubuntu 7.04 (feisty) and i was using the optical output on my sony vaio. It's been working nicely for about a week....

I was having this problem with audio being out of sync in video files, so i thought i'd try VLC...I installed VLC and opened an mpeg file...sound was still out of sync...i closed the mpeg file, opened a dvd file (.vob), and no sound. I go back to the mpeg, and no sound there either. I am able to plug in some analog speakers and they work fine, but now my optical doesn't work. No 5.1 for dvd's now. Any help or ideas will be greatly appreciated. I checked the physical optical connections, they were ok..i rebooted...i checked alsamixer and the other ubuntu sound mixers...everything seems to check out, just no sound on optical port.

I'm setting up a mythtv box (now becoming a 6 month project). Other current issues include audio out of sync on all video files except for dvd's, any video player crashes when fast forwarding or seeking, nvidia FX5200 drivers installed, but video playback is still not smooth, and the desktop screen scrolls to the right for some reason (my lcd is 1280x1024, but it seems like the screen space is set to 1800x1024, so the screen moves to the right when you mouse to the far right...I think it has to do with the TV out port being set to 640x480)

--Anyhow, i really appreciate the help on this one. It just seems like i am running into problem after problem with linux...i've been on it for about a year now and can do a lot of stuff in it, but some of the multimedia stuff is beyond my control (like audio out of sync, or optical just quitting on me).

---

### Post by newlinux on 2007-05-23
Maybe thiese will be helpful (they helped me):

[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound)
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
Good luck.

---

### Post by xmrkite on 2007-06-04
Thank you but nothing worked. It was easier to do a complete reinstall. I then made an image file of my partition in case this ever happens again. It's a lot of work/time to get everything setup how I like it.

---

### Post by se2131 on 2007-06-07
I realize that this is too late, but something similar happened to me as well, sound just stopped working.

For future reference, what I ended up doing is going into a terminal and running the program:

```
alsamixer
```

You'll see columns for Master, Headphones, PCM, etc etc.

What you want to do is make sure that they're not at 0.  Additionally (this is what I had to do), make sure that everything is **unmuted**.  This means that you don't see "MM" anywhere above the individual headings.  If you do see this, then press the "m" button to unmute it.

This solution is given in newlinux's links, but it's a bit buried, so I just wanted to highlight it.

---

### Post by xmrkite on 2007-06-07
Hello. I did try running that, but to no avail. Everything checked out ok. I also downloaded a few different sound mixer programs via synaptics, but none could help. But after the reinstall, there have been no issues.

-Thanks

---

### Post by tck on 2007-06-23
Well this has just happened to me, I don't run Myth TV and no soundcard - just simple onboard chipset. Was working lovely. Then I installed VirtualBox and set new group permissions for vboxusers  - logged out and then when i logged back in  - zilch

---

### Post by xmrkite on 2007-06-23
Unfortunately, there seems to be quite a few bugs still left in Ubuntu (ie. you can't just change a video card either, the system freaks out on you and you have to reconfigure x).

I've learned that i have to make system backups before making changes, cause some of these problems just take so long to figure out, that sometimes it's easier to just do a complete reinstall....it shouldn't be that much drama, but it usually is in my experience.

---

### Post by dracomordag on 2007-06-23
i've changed nothing, but my sound stopped working. well, not entirely. when i reboot, there's about a 10% chance the sound will work. The other 9 times, nothing.

cat /proc/asound/cards puts out:
 0 [ICH5           ]: ICH4 - Intel ICH5
                      Intel ICH5 with AD1980 at 0xfeb7fa00, irq 21
 1 [Live           ]: EMU10K1X - Dell Sound Blaster Live!
                      Dell Sound Blaster Live! at 0xdda0 irq 21

it used to be that the SB Live! works and the ICH5 doesn't, but now I can't get either to work.

---

### Post by dtro on 2007-06-23
ive had this happen to me so many times. it usely happends after i install something. i just reboot and it starts working agin.

---

### Post by dracomordag on 2007-06-24
i've figured out part of my problem

when i double click the volume control on the panel to bring up the GUI mixer, if Dell Sound Blaster Live! is listed under 0: in File->Change Device, then the sound will work on that boot up. if it's listed under 1:, and Intel ICH5 is listed under 0:, then the sound will not work (no matter what i do in System->Preferences->Sound)

so basically, does anyone know how to force Dell Sound Blaster Live! to be listed under 0:?

---

### Post by tom957 on 2007-06-24
first do
```
asoundconf list
```
to see your available cards, then set your default card with
```
sudo asoundconf set-default-card yourcard
```
hopefully that should get you started

---

### Post by dracomordag on 2007-06-24
didn't change anything. should i restart?

---

### Post by dracomordag on 2007-06-24
the restart worked, but contrary to my original statement, Dell Sound Blaster Live! is still listed at 1:

---

### Post by Xavier Oddmon on 2007-08-23
I am having a similar problem, but I have to do a purge and re-install every time I loose sound (sound is lost often when changing seemingly unrelated options, such as resolution, or when the computer is not shut down properly). After the re-install, I continue on the tutorial (found here), and invariably, the configure fails, but often the sound comes back. I tried changing my default sound card to "Live" as the list said, but there is still no sound. Is there any way to remove the intel ICH5 from the list? I'm not sure if I need it, so it may be a bad idea, but I do not actually have any other audio ports on my computer other than the Dell Sound Blaster Live! 24-bit card.

---

### Post by Arcturus691 on 2007-08-23
Just out of curiosity did any of you install the latest updates for 7.04?  I had my audio working before I installed the latest updates and then after a reboot I have no audio.  I know it is ubuntu and not my hardware because sound works on M$.    

Does anyone know how to find out which updates where most recently installed and then roll them back? :-k  

I tried to filter for it through synaptic package manager but was unsuccessful.  If I can rollback todays updates I can test for sure if they are the issue.   I am running AMD64 dist on a  nforce4 board with onboard sound using alsa.

thanks

---

### Post by Xavier Oddmon on 2007-08-24
Actually, the sound problems existed before the update, but they got worse afterwards. Also, I found that decreasing my resoltion to 1024*768 when I log off and restarting X makes the sound come back (I edited xorg.conf to allow higher resolutions, which worked fine, but at the expense of my sound...)
Funny that these two things would mess each other up, they're seemingly unrelated...

---

### Post by Arcturus691 on 2007-08-24
I think my problem was with the Alsa Mixer.  Somehow the settings got changed after the update.  I think I am going to start backing up before I install updates though.

---

### Post by Xavier Oddmon on 2007-09-22
Hey, it turns out that the problem was just that it kept changing to my integrated sound card, namely Intel ICH5. I disabled it in BIOS, and everything's just peachy.

---

### Post by Tierial on 2007-09-22
might i inquire how you did that in the bios?

---

### Post by Xavier Oddmon on 2007-09-23
Certainly. I rebooted my computer, and pressed F2 to enter setup. In the second section in the list is the option "integrated cards" I selected it, highlighted sound, and pressed right to turn it off. sound works fine. keep in mind this varies greatly with different computers.

---

