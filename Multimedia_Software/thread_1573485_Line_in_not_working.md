---
title: "Line in not working"
date: 2010-09-12
forum: Multimedia Software
---

### Post by mikeglaz on 2010-09-12
I have a Giga-byte GA-890GPA-UD3H motherboard and Ubuntu 10.04.  I just upgraded from an old ASUS board.  I'm trying to record stuff through the line in jack but it's not picking up anything.  I installed GNOME-ALSAmixer and it only gives me 3 options (Master, PCM, Capture).  When I had it installed with the old motherboard I had like 20 options including Line In.  Any ideas??

thanks,
mike

---

### Post by mikeglaz on 2010-09-13
bump

---

### Post by mikeglaz on 2010-09-16
bump

---

### Post by lidex on 2010-09-17
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by mikeglaz on 2010-09-23
That didn't work...

---

### Post by lidex on 2010-09-24
> **mikeglaz said:**
> That didn't work...

Copy and paste this command into a terminal and press enter. When you are prompted to upload your info enter Y and press enter key. You will be given a link to the uploaded data. Provide the url please.

```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh

```

---

### Post by mikeglaz on 2010-09-26
Is this what you're looking for?

Your ALSA information is located at [http://www.alsa-project.org/db/?f=b9f6986a59e966b6b5849a0f7bf6d26a491bdda1](http://www.alsa-project.org/db/?f=b9f6986a59e966b6b5849a0f7bf6d26a491bdda1)

mike

---

### Post by lidex on 2010-09-26
> **mikeglaz said:**
> I have a Giga-byte GA-890GPA-UD3H motherboard and Ubuntu 10.04.  I just upgraded from an old ASUS board.  I'm trying to record stuff through the line in jack but it's not picking up anything.  I installed GNOME-ALSAmixer and it only gives me 3 options (Master, PCM, Capture).  When I had it installed with the old motherboard I had like 20 options including Line In.  Any ideas??

thanks,
mike

Yeah. Alsa is using the generic parser for the sound chip. Probably because a newer codec. Your best bet is an alsa upgrade. Follow the corresponding link in my sig.

---

### Post by mikeglaz on 2010-09-28
OK, that did something.  I now have a full Alsamixer.  I can hear my microphone through my speakers but still when I try to record LINE IN I get nothing.

mike

---

### Post by lidex on 2010-09-29
> **mikeglaz said:**
> OK, that did something.  I now have a full Alsamixer.  I can hear my microphone through my speakers but still when I try to record LINE IN I get nothing.

mike

OK. Can you provide updated info?

---

### Post by mikeglaz on 2010-09-29
Sorry, updated info of what?

---

### Post by lidex on 2010-09-29
The alsa-info script.

---

### Post by mikeglaz on 2010-10-02
uh, sorry, what do you mean by "updated info"?

---

### Post by mikeglaz on 2010-10-02
sorry, disregard second post.  I haven't realized a reply has been posted.

---

### Post by mikeglaz on 2010-10-02
Your ALSA information is located at [http://www.alsa-project.org/db/?f=f05177c96c635782eb1238fbbd41f7c35355ab18](http://www.alsa-project.org/db/?f=f05177c96c635782eb1238fbbd41f7c35355ab18)

---

### Post by lidex on 2010-10-02
Something strange in your install and alsa did not upgrade correctly. I want you to re-install alsa, first removing these config files:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf /etc/modprobe.d/alsa-base.conf
```

```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Next use the link in my sig to upgrade alsa.

---

### Post by mikeglaz on 2010-10-05
Did all that and ran the AlSA script. Your ALSA information is located at [http://www.alsa-project.org/db/?f=79555f67c0dcfc2e0851f777474325039b4a9598](http://www.alsa-project.org/db/?f=79555f67c0dcfc2e0851f777474325039b4a9598)

but still, can't record from line in.

---

### Post by lidex on 2010-10-05
> **mikeglaz said:**
> Did all that and ran the AlSA script. Your ALSA information is located at [http://www.alsa-project.org/db/?f=79555f67c0dcfc2e0851f777474325039b4a9598](http://www.alsa-project.org/db/?f=79555f67c0dcfc2e0851f777474325039b4a9598)

but still, can't record from line in.

Seems your capture elements are both set to 'mic'. Try alsamixer and change the input to 'line'.
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

So you want <F4> for capture. Scroll left-right using L/R arrow keys to 'Input Source'. Toggle to 'Line' using Up/Dn keys. May need to increase 'Capture' levels. Make sure you have selected a profile with 'Analog Input' or 'Stereo Duplex' in Sound Preferences.

---

### Post by mikeglaz on 2010-10-06
wow, that worked...thank you so much.

---

### Post by mikeglaz on 2010-10-06
One more question.  In my GNOME ALSA mixer how come I have two Capture sliders and one Line slider?

---

### Post by lidex on 2010-10-06
> **mikeglaz said:**
> One more question.  In my GNOME ALSA mixer how come I have two Capture sliders and one Line slider?

You're welcome, enjoy.
My guess is the other is for mic.
Please mark the thread solved using 'Thread Tools' up top.

---

### Post by mikeglaz on 2010-10-07
I just rebooted my computer and alsamixer went back to having both inputs as mics.  How can I automatically have it set one to Line In on boot?

---

### Post by lidex on 2010-10-07
> **mikeglaz said:**
> I just rebooted my computer and alsamixer went back to having both inputs as mics.  How can I automatically have it set one to Line In on boot?

Set your mixer the way you want it and and use this command to save: ```
sudo alsactl store 0
```

---

