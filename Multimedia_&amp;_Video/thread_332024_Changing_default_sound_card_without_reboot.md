---
title: "Changing default sound card without reboot"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by tiroxino on 2007-01-05
Hello, 
I have two sound cards and one of them is set as the default.
My file **/etc/modprobe.d/alsa-base** shows:

```
#My Mod - Set Default sound card
options snd_via82xx index=0
options snd_ens1371 index=1

```

where the default sound card is set with index=0.

Sometimes I'd like to change the default sound card in order to listen to music (or videos) through the secondary sound card. Can I do this?

Thanks.

---

### Post by moeFinley on 2007-01-05
You can change your default card in

```
sudo gedit /etc/asound.conf
```

and restart ALSA with

```
sudo /etc/init.d/alsa-utils restart
```

You can check that your cards details with

```
aplay -l
```

Hope this helps

---

### Post by tiroxino on 2007-01-05
Could you tell me how to modify the file **asound.conf**, please?
I have two sound cars. XMMS shows them as "hw:0,0" (VIA) and "hw:1,0" (AudioPCI).

I get this information with **aplay -l**:
```
 aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: rev50 [VIA 82C686A/B rev50], dispositivo 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 1: AudioPCI [Ensoniq AudioPCI], dispositivo 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: AudioPCI [Ensoniq AudioPCI], dispositivo 1: ES1371/2 [ES1371 DAC1]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```

And my **/etc/asound.conf** shows the following code:

```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}
```


I think I had to modify the *pcm.dmixer* section, setting **pcm "hw:0,0"** with the new value **pcm "hw:1,0"**, but I'm not sure.

Thanks.

---

### Post by moeFinley on 2007-01-05
I don't really have enough knowledge to help you with confidence.  

This defines your default card
```
pcm.!default {
type plug
slave.pcm "dmixer"
}
```

dmixer is a virtual software sound card.  You need this to be able to play more than one thing at one time.

I think your right about changing```
pcm "hw:0,0"
```

Have a look [here]("http://alsa.opensrc.org/Main_Page") for loads of infomation and examples

---

### Post by tiroxino on 2007-01-05
I changed it (setting **pcm "hw:1,0"**) and restarted alsa-utils, but the default sound card still is the same. I get the same information with **aplay -l** too. :-k

---

### Post by moeFinley on 2007-01-05
[This has lots of info about setting up multiple cards.]("http://alsa.opensrc.org/MultipleCards")

And this looks like this my be useful for testing which card is 0,0 and which is 1,0```
alsaplayer -o alsa -d hw:0,0  some_k00!.ogg
```

sorry I can't be more helpful

---

### Post by tiroxino on 2007-01-06
Thank you for your help ;)

---

### Post by PurplePenguin on 2007-02-16
Hey, I know I'm a bit late, but thanks for the help!  I had everything set up the way I wanted it, but after some updating, my two soundcards got mixed up... now everything works great!  One card for music (coming out of the speakers) and one card for Ekiga! :D

---

