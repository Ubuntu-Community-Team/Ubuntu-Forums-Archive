---
title: "No sound Ubuntu 10.10 Asus laptop N82J"
date: 2011-03-01
forum: Multimedia Software
---

### Post by etiennenoel on 2011-03-01
Hi,

I have an Asus N82J and I don't have sound. ?  Can someone give me clue please on where I can start ?

Thank you very much

Etienne

---

### Post by etiennenoel on 2011-03-01
Strangest thing, the sound works by using the headphone jack. Can someone guide me in order to resolve this problem ?

Thank you very much !

---

### Post by etiennenoel on 2011-03-01
I also want to mention that nothing is muted under alsamixer and I can control the sound of the headphones as well as the master, but nothing comes out.

---

### Post by etiennenoel on 2011-03-01
Hi Everyone,

I follow the comprehensive guide step by step but it seems that my sound card isn't supported.

Can someone suggest me something?

Thanks in advance !

---

### Post by lidex on 2011-03-01
Hard to know without some system info. 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by etiennenoel on 2011-03-01
Thank you very much for your time.

[http://www.alsa-project.org/db/?f=f19324ba1698e62530bf18604db63e568d42b11c](http://www.alsa-project.org/db/?f=f19324ba1698e62530bf18604db63e568d42b11c)

I think this is what you meant by upload.

Thanks again

---

### Post by lidex on 2011-03-01
OK. Remove the edit you made to alsa-base.conf then try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by etiennenoel on 2011-03-01
Unfortunately, it still doesn't work. I tried to put it on every profile without success. Do you have any other clues ? When I tried what you told me, I got more choices in the output tab. I try to do what they mention in another forum but without success... [http://ubuntuforums.org/showthread.php?t=1658502](http://ubuntuforums.org/showthread.php?t=1658502)

Thank you very much for you help and I hope this will get resolved !

---

### Post by lidex on 2011-03-01
Have you tried raising the level on the 'Speaker Playback Volume' in alsa mixer. It's currently set at zero.

```
control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 87'
		comment.dbmin -6525
		comment.dbmax 0
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 0
		value.1 0
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
```

---

### Post by etiennenoel on 2011-03-01
In alsamixer, there is nothing named speaker playback volume. but htere is something named speaker that is at 100.

---

### Post by lidex on 2011-03-02
> **etiennenoel said:**
> In alsamixer, there is nothing named speaker playback volume. but htere is something named speaker that is at 100.
Then try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by etiennenoel on 2011-03-02
I have it installed but it is not shown there either...

---

### Post by lidex on 2011-03-02
Do you have all the elements enabled in the 'Edit -> Sound Card Properties' menu?

---

### Post by etiennenoel on 2011-03-02
Yes, everything is enabled. Thanks again for your time.

---

### Post by lidex on 2011-03-02
Did you remove that line from alsa-base.conf? Can you post an updated alsa-info script please?
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```

---

### Post by etiennenoel on 2011-03-02
[http://www.alsa-project.org/db/?f=e0ff6fa20c816e9ec0d9800ab94e3f73bcd98df7](http://www.alsa-project.org/db/?f=e0ff6fa20c816e9ec0d9800ab94e3f73bcd98df7)

---

### Post by lidex on 2011-03-02
> Did you remove that line from alsa-base.conf?
So you're saying you're not going to remove it?

---

### Post by etiennenoel on 2011-03-02
Sorry I don't understand what you mean. You want me to remove which line?

---

### Post by lidex on 2011-03-02
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```

Find near the bottom, a line starting with:
```
options snd-hda-intel
```

Remove it, save, close, reboot.

---

### Post by etiennenoel on 2011-03-02
I removed the line you told me, and reboot but the sound still doesn't work. However, the sound still works with the headphone jack.

---

### Post by lidex on 2011-03-02
I'm drawing a blank here. The 2.6.34 kernel was supposedly patched for your codec - it should work. File a bug report for the audio devs to look at. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by etiennenoel on 2011-03-02
Thanks for your time, I did what you told me. HEre is the link of the bug [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/727868](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/727868) .

---

### Post by lidex on 2011-03-02
Thank you for following up so quickly. I'll keep an eye on it.

---

### Post by lokiguy on 2011-03-23
I had no sound in headphones - adding the ppa:ubuntu-audio-dev/ppa worked fine for me - just a reboot was all that was needed after that.

Thanks lidex!

---

