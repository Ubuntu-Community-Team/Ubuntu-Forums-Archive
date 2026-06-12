---
title: "HD DVD or Blu Ray on a computer"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by DanielJackins on 2008-02-03
I was just wondering how to go about viewing these on a computer (running Linux, of course). I have no idea how this works with  computers; do I need to purchase a player, or are there simply Linux programs that allow you to watch them?

---

### Post by TeaSwigger on 2008-02-03
Goes to show how out of date I am, I guess. I didn't think there was any Blu-Ray or HD-DVD support on any PCs...

---

### Post by DanielJackins on 2008-02-03
Maybe there isn't :) I just kind of assumed there was.

If there isn't, has anyone tried setting up the xbox 360's HD player with their computer? There is plenty of tutorials of how to do it for windows, but has anyone had success trying it with Ubuntu?

---

### Post by Aquaman420 on 2008-02-03
You would need to buy an optical drive that can support HD DVD or Blu-ray.  Looks like Blu-ray has the lead on the format war.  AS for software I am not sure what works with the HD formats.

---

### Post by /home on 2008-02-03
I Think that Blu Ray isn't linux or mac compatible
Dam* M$ copyright

---

### Post by Aquaman420 on 2008-02-03
I bet it does work.  if you think about it linux and Mac would be Blu-rays best allies.  because Sony owns Blu-ray and PS3.  So there biggest competition is xbox360 and toshiba's hd dvd who are obviously in cahoots.  So only having blu-ray available on your biggest competitors OS doesn't make much sense to me.

---

### Post by rsidle on 2008-02-03
I played around with this for quite some time before giving up. The stumbling block that I ran up against was getting my kernel patched to read the UDF 2.5 file system that is used on HDDVDs. The xbox 360 drive was recognized just fine and played DVDs and CDs with no issues. Another consideration is that you'll need quite a good computer. I almost had it working in Winxp but it wouldn't play for me on a Pentium D 2.66 2gb ram and geforce 7600. My system specs were just too low. If you can get the UDF 2.5 FS to install, I bet the decryption and playback would be pretty easy.

---

### Post by mc4man on 2008-02-03
Basic info
[http://forum.doom9.org/showthread.php?t=133901](http://forum.doom9.org/showthread.php?t=133901)

---

### Post by AlanR8 on 2008-02-03
My Sony VGN-FZ21S has a CD/DVD/BlueRay disk installed. It all works on cd and dv but haven't tried a BlueRay yet

---

### Post by DanielJackins on 2008-02-03
Would it work if I just set up my xbox 360 with the hd player, and then plugged the 360 in to the dvi or hdmi on my monitor?

---

### Post by disturbedite on 2008-02-03
@ DanielJackins
i think that *might* be possible.  but the software setup would be a bit more complex than the situation you described.

---

### Post by mc4man on 2008-02-03
> Would it work if I just set up my xbox 360 with the hd player, and then plugged the 360 in to the dvi or hdmi on my monitor?
What your describing is using the xbox to play hd disks on a monitor or display - would certainly work.
As far as playback in linux from the commercial disks it's not going to happen - no software player that can decrypt the keys = no playback

---

### Post by TeaSwigger on 2008-02-03
> **rsidle said:**
> I played around with this for quite some time before giving up. The stumbling block that I ran up against was getting my kernel patched to read the UDF 2.5 file system that is used on HDDVDs. The xbox 360 drive was recognized just fine and played DVDs and CDs with no issues. Another consideration is that you'll need quite a good computer. I almost had it working in Winxp but it wouldn't play for me on a Pentium D 2.66 2gb ram and geforce 7600. My system specs were just too low. If you can get the UDF 2.5 FS to install, I bet the decryption and playback would be pretty easy.

Thank you for sharing your experiences.

Oh well I'll just forget both Blu-Ray and HD-DVD until what time I actually buy a monster spec computer.

---

### Post by caramelsoul on 2008-02-04
Interesting stuff this. So Linux would not be able to play a "back up" blu ray film that i have stored on my PC straight to my TV?

---

### Post by disturbedite on 2008-02-04
if it isn't encrypted.  or if it is & you decrypt it you could play it.

---

### Post by mc4man on 2008-02-04
> So Linux would not be able to play a "back up" blu ray film that i have stored on my PC straight to my TV?
unencrypted back ups yes, the original discs - no

---

### Post by caramelsoul on 2008-02-06
So what program would i use for this...VLC?

---

### Post by AlanR8 on 2008-02-06
To bump this thread.....

As I stated in an earlier post in this thread, I have a Sony VGN-FZ21S laptop that has a combo CD/DVD/Blueray disk. Long story, but the drive failed and the machine's just come back from having a new drive installed by Sony. I also registered the machine with Sony and as a reward they sent me a free copy of Spider-Man 3 that arrived today.

Running Kubuntu, insert the disk and a window opens asking what do I want to do. I select Open in a new window.

It also recognises the Blueray disk as 02146765_SPIDER_MAN_3_KDEDaemon.

Click OK to open a new window and the disk tries to mount but gives the following error:

> mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Click OK to the message and nothing appears in the opened window.

Tried opening the disk in VLC and MPlayermto no avail.

So, there's a bit of additional info for all you real techs, maybe a solution can be found.

---

### Post by rsidle on 2008-02-11
Sure, the xbox 360 works just fine with LCD monitors. Just be sure your monitor had HDCP or DRM will be sure to screw you.

---

