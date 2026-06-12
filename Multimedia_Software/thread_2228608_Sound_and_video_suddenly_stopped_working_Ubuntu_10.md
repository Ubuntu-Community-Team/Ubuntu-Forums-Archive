---
title: "Sound and video suddenly stopped working Ubuntu 10.04?"
date: 2014-06-08
forum: Multimedia Software
---

### Post by Tapasweni_Pathak on 2014-06-08
[COLOR=#333333][FONT=UbuntuRegular]I am using Ubuntu 10.04* 32bit from many years, in Dell inspiron 1525.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Today, the sound and video suddenly stopped working. When I tried to play videos on youtube on chromium, it gives me something like this :[http://i.gyazo.com/4015b5fe655611a4307550ee15954c30.png](http://i.gyazo.com/4015b5fe655611a4307550ee15954c30.png)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]It's buffering fine, but it does not get played, it remains stopped at a specific point.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I tried viewing videos in Mozilla, but it stops responding after some time, and I have to killall mozilla to stop it.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I searched about this problem and I tried :[/FONT][/COLOR]

[LIST=1]
[*]Re-installing flash player
[*]I also tried deleting my cookies, in chromium.
[*]I also tried this : [http://askubuntu.com/a/140054/290664](http://askubuntu.com/a/140054/290664)
[*]I tried installing sudo apt-get install ubuntu-restricted-extras
[*]I tried cat /proc/cpuinfo | grep sse2, and it's not blank, suggested on a link.
[*]Administration->Hardware drivers are not suggesting anything.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]nothing helped. Even the videos and music files in my computer also stopped working. When I played the the media player, it stopped responding and VLC is showing similar behavior like youtube. I am not getting any sounds too.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My chromium plugins looks like this : [http://i.gyazo.com/4015b5fe655611a4307550ee15954c30.png](http://i.gyazo.com/4015b5fe655611a4307550ee15954c30.png) Any help would be greatly appreciated. Thanks.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]*I still use Ubuntu 10.04 as with 10.04+ versions my wireless, webcam does't work, and I cannot buy a new system.[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2014-06-08
Try booting into the previous kernel. Others are having issues with new kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1327014](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1327014)

---

### Post by Tapasweni_Pathak on 2014-06-08
How can I do that?

---

### Post by Yellow Pasque on 2014-06-08
Hold down shift key when you boot: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Tapasweni_Pathak on 2014-06-08
Can you please explain what will this do? 
It would be really helpful of you.
Thanks.

---

### Post by Tapasweni_Pathak on 2014-06-08
I booted with previous version, this solved the hang problem and the youtube play problem too, but there is no sound.?

---

### Post by Yellow Pasque on 2014-06-08
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Tapasweni_Pathak on 2014-06-09
This is what I got after doing the stuff written on the link provided by you : [http://www.alsa-project.org/db/?f=757316b99ce399507cb237d2f63308b00327b4a1](http://www.alsa-project.org/db/?f=757316b99ce399507cb237d2f63308b00327b4a1)

---

### Post by mörgæs on 2014-06-09
> **Tapasweni_Pathak said:**
> [COLOR=#333333][FONT=UbuntuRegular]I still use Ubuntu 10.04 as with 10.04+ versions my wireless, webcam does't work, and I cannot buy a new system.[/FONT][/COLOR]

Then it would be better to focus your energy on getting these things to work in (L/X/K/Ubuntu) 14.04. This might help:
[http://ubuntuforums.org/showthread.php?t=2218729](http://ubuntuforums.org/showthread.php?t=2218729)

 10.04 is a security risk, and you might see more breakage in the future. Many problems have been reported lately:
[http://ubuntuforums.org/showthread.php?t=2228206](http://ubuntuforums.org/showthread.php?t=2228206)

---

### Post by Yellow Pasque on 2014-06-09
Nothing looks out of place with the alsa info. You didn't add this line recently, did you?
```
snd-hda-intel: model=generic
```

---

### Post by Tapasweni_Pathak on 2014-06-09
Yes I have.

---

### Post by Tapasweni_Pathak on 2014-06-09
Yes, I have. How can I revert back if I need to?

---

### Post by Yellow Pasque on 2014-06-09
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

1. Remove line 'options snd-hda-intel model=generic'
2. Save
3. Reboot (or run 'sudo  alsa force-reload')

---

### Post by Tapasweni_Pathak on 2014-06-09
Done. Thank you so much. It's all perfect. Thanks.

---

### Post by tom107 on 2014-06-11
Hi. I have the same problem but the fix provided does not work for me because the file (when I open it) does not have this line. 
The most similar line I have are these:
```

options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

```

---

### Post by tom107 on 2014-06-11
I have the same problem. Fix was offered here:
[HTML]
http://askubuntu.com/questions/479529/sound-and-video-suddenly-stopped-working-ubuntu-10-04
[/HTML]

However I don't have this line in my file. Are there any other recommendations?

---

### Post by Yellow Pasque on 2014-06-11
> **tom107 said:**
> Hi. I have the same problem

You have the same symptom, but unless you have the same laptop model (or anything with Realtek ALC260 codec), you probably have a different cause. Please start a new thread. Include ALSA info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by bapoumba on 2014-06-15
Thread closed as per : [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

