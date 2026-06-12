---
title: "MythTV pinnacle 800i setup"
date: 2008-02-16
forum: Mythbuntu
---

### Post by michaeld003 on 2008-02-16
I have installed a pinnacle pctv hd pci card 800i in my mythbuntu box and I have been able to watch both analog and digital tv in tvtime and in mplayer.  My problem is that whenever I go to set it up in mythtv it says it cannot open the card to scan for channels.  I was just wondering if anyone had any advice or could show me their working set up of it.  Thanks in advance.

---

### Post by icevapor on 2008-03-24
Hello,

I just setup this card this weekend.  Let me give you a quick rundown on how I got this to work and some of my troubles:

-I used mythbuntu 7.10, clean install used the entire drive.
-I noticed that there were a bunch of updates ready to be installed but thought I would try to get the card to work first.
-I installed the firmware as described here 
-Then installed the linuxtv drivers

Going into mythtv-setup I could immediately add analog channels using the generic analog tuner selection.  I left it at /dev/video0.  I just worked.

As for digital, I could not for the life of me get myth tv to see any channels. I had a DVB device that said it was a samsung, so I thought this couldnt be it.  I also had a PCTV device listed saying it was the 800i but listed the device under /dev/video0 instead of /dev/dvb/adapter0 like I knew it should be.  I tried both and could not pick up any channels.

I used scan ([http://www.linuxtv.org/wiki/index.php/Scan](http://www.linuxtv.org/wiki/index.php/Scan)) to find and create a channels.conf file and could tune into these digital channels (had to used azap also) with mplayer so I knew the tuner was working, very much like your setup.

After messing with it for like 3 hours, I decided to install whatever updates mythbuntu wanted me to install.  After which I needed to re-install my 800i drivers.

Going back into mythtv-setup, I found that my PCTV card was no longer listed with the other cards.  But noticed that I still had the samsung choice.  ( do a dmesg and you'll see "DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)" ) I selected that as my choice and tried to use my channels.conf file that I had made using scan... it didnt work, just sat at 0% forever.  So i tried doing a full scan (broadcast, 8vsb) and it worked, It picked up all my digital (over the air) channels.

So my best advice for you is to update your system, then reinstall your driver, then use the DVB card that shows the samsung as the hardware.

Hope this helps.

Also, If you figure out the remote with this thing, let me know.  It seems as though mine is not useing LIRC.  I can shutdown lirc and can still type numbers in a text editor using the remote.  It seems to be used as an input device.  I dont understand it.

---

### Post by Johnius on 2009-08-03
Did you ever get your remote to work?  I can't get it to do anything.

---

### Post by Johnius on 2009-08-05
Bump

---

### Post by sgeoxd on 2009-12-09
I fought over the remote aspect for awhile and was pretty upset when I realized how easy it really is.  The "hard way" :

Obviously you want LIRC installed (choose "none" when prompted for type):
```
sudo apt-get install -y lirc
```

After installation find out which input the IR is registered to (look for "cx88"):
```
cat /proc/bus/input/devices
```

Then edit your hardware.conf file...
```
sudo nano /etc/lirc/hardware.conf
```

...and add the event for the IR from the previous step under "REMOTE_DEVICE".  e.g.
```
REMOTE_DEVICE="/dev/input/event7"
```

...also add "devinput" for the REMOTE_DRIVER:
```
REMOTE_DRIVER="devinput"
```
 
Once you have the hardware.conf file updated restart LIRC:
```
sudo /etc/init.d/lirc restart
```

---

