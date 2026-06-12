---
title: "Mic not working on VAIO VPCSB with 11.04"
date: 2011-04-02
forum: Multimedia Software
---

### Post by puller on 2011-04-02
Hi, I have a new sony VAIO VPCSB with Kubuntu 11.04 installed (2.6.38). This notebook doesn't have an external mic jack (only phones jack), so it is vital for me to have the internal mic working.

Could someone please help me to activate it?

```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 04)
```

```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
```

```
uname -r
2.6.38-7-generic
```

```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC275
Codec: Intel CougarPoint HDMI

```

---

### Post by lidex on 2011-04-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by puller on 2011-04-03
Thanks for your reply!

This is the link of my updated data: [http://www.alsa-project.org/db/?f=f3ba0f7f5e17b8e3bba75d071bfd9dd461778923](http://www.alsa-project.org/db/?f=f3ba0f7f5e17b8e3bba75d071bfd9dd461778923)

Just for information, yesterday I updated ALSA using the script provided here: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by lidex on 2011-04-03
Time to file a bug report. I have not seen anything on the alc275.
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by puller on 2011-04-03
I run
```
ubuntu-bug audio
```
It just asked me to indicate the hardware I am having problems with, then it asks me a question about external firewire cards, then it tells me that the script /usr/share/apport/symptoms/audio.py didn't found any altered packet, then everything disappears.

Is this the correct procedure? Has the bug already been filed?

---

### Post by lidex on 2011-04-05
No idea. 
Alsa 1.0.24 is supposed to address some of these issues. The mixers are not being set up correctly. No input. What is your selected profile?

---

### Post by puller on 2011-04-05
How can I know which is my selected profile?

P.S.: Many thanks for your help!

---

### Post by lidex on 2011-04-05
Sound preferences, the hardware tab.
The devs really need to see this. Try:
```
ubuntu-bug alsa-base
```
or go upstream:
[https://bugtrack.alsa-project.org/alsa-bug/](https://bugtrack.alsa-project.org/alsa-bug/)

---

### Post by puller on 2011-04-05
> **lidex said:**
> Sound preferences, the hardware tab.
The devs really need to see this. Try:
```
ubuntu-bug alsa-base
```
or go upstream:
[https://bugtrack.alsa-project.org/alsa-bug/](https://bugtrack.alsa-project.org/alsa-bug/)

My system just got down...
After today updates I am not able to boot not even in rescue mode (system hangs or shows a black screen).
I think the issue is ATI related.

I'm looking forward to make it work again and continue this topic...

---

### Post by lidex on 2011-04-05
We need to close this thread down. Just realized (duh) this is natty - only supposed to post to the development forum:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)
See you over there.

---

### Post by puller on 2011-04-08
I filed the bug report [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/752792](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/752792) and very quickly David Henningsson provided a patch which has totally fixed the problem!

To apply the patch I used the alsa upgrade script found on this forum ([http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)), then after the download step (-d) I went to /opt/Alsa-1.0.24/alsa-driver-1.0.24/sound/pci/hda/ (which is where the script downloads the files)
```
cd /opt/Alsa-1.0.24/alsa-driver-1.0.24/sound/pci/hda/
```
and applied the patch to patch_realtek.c file:
```
sudo patch patch_realtek.c < patch_file
```

Then I proceeded with the upgrade script compile (-c) and install (-i) steps.

---

