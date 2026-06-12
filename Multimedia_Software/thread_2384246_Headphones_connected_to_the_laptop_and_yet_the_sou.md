---
title: "Headphones connected to the laptop and yet the sound come from devices's speakers"
date: 2018-02-04
forum: Multimedia Software
---

### Post by edenah on 2018-02-04
Hello i'm pretty new to all the linux world and i made a dual boot system of both ubuntu 17 and windows.

After few days of using ubuntu i noticed that my headphones don't work only on my ubuntu. when i am connecting my earbuds my computer does recognize them and in the sound setting do show that headphones are connected. it does change the volume to fit the headset volume.
And yet when i play sound THE LAPTOPS SPEAKER WORKS INSTEAD OF THE HEADSET. everything acts as i have a headset connected to the laptop yet the machine plays the sound on the laptops speakers.
so i checked the web for a solution. so i checked the web.
i have tried playing with pavucontrol and tried sudo alsa force-reload, the alsamixer shows i have volume, and i'm definitely not on "mute".
i got clueless. 
Please help :)

---

### Post by Yellow Pasque on 2018-02-04
Is there an "Auto Mute" option in your alsamixer?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by edenah on 2018-02-05
> **Temüjin said:**
> Is there an "Auto Mute" option in your alsamixer?
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[http://www.alsa-project.org/db/?f=dd71863b10a8cada9403a790c58e84900af48286](http://www.alsa-project.org/db/?f=dd71863b10a8cada9403a790c58e84900af48286)

No i have no auto mute
Just to make sure you understood me. Yes I don't want my laptop's speaker to work.
BUT a bigger problem is that my headphones don't seem to work. I have tried many kinds of headphones plus all of them seem to work on my windows partition.

btw thanks for the response :)

---

### Post by Yellow Pasque on 2018-02-05
Try enabling these settings:
```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

Headphones should work on this model. There has already been a patch applied for it: [https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133#diff-dac40fa16ffab363ae9a07ae827850a3](https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133#diff-dac40fa16ffab363ae9a07ae827850a3)

---

### Post by edenah on 2018-02-05
> **Temüjin said:**
> Try enabling these settings:
```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

Headphones should work on this model. There has already been a patch applied for it: [https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133#diff-dac40fa16ffab363ae9a07ae827850a3](https://github.com/torvalds/linux/commit/b5337cfe067e96b8a98699da90c7dcd2bec21133#diff-dac40fa16ffab363ae9a07ae827850a3)



It didn't work :(
maybe a thing that would be a game changer. but my device cant make a sound test in the sound settings. i only test it with videos.

---

### Post by tinylagarto on 2018-02-05
When you open alsamixer from terminal:

```
alsamixer
```

does it show speakers as muted when your headphones are plugged in? Of course headphones should not be muted in this case.

---

### Post by edenah on 2018-02-06
No... It's not on mute. Just to make sure I have raised allllllllll the available stats on. And also if it was a mute problem then the device's speaker wouldn't be working instead.


I see two stats that both are raised to top.

---

### Post by Yellow Pasque on 2018-02-06
I don't what else to suggest. I made the same suggestion to someone else and it worked, but I guess Alienware 15 R2 is different somehow:
[https://www.linuxquestions.org/questions/linux-hardware-18/sound-does-not-switch-to-headphones-after-plugging-jack-on-alienware-15-a-4175587808/](https://www.linuxquestions.org/questions/linux-hardware-18/sound-does-not-switch-to-headphones-after-plugging-jack-on-alienware-15-a-4175587808/)

---

### Post by edenah on 2018-02-06
I have noticed a thing. my [COLOR=#000000][FONT=&quot]alsamixer doesn't even show my headphones! i only see them in my sound settings of the ubuntu!
Also i tried connecting a bluetooth speaker to my laptop and it seemed to be impossible! it could pair but when i choose that the device would work as an audio device the pairing would go off!
I tried pressing the pair mode more times and then my laptop went into sleep![/FONT][/COLOR]

---

### Post by edenah on 2018-02-06
also i am trying the link you sent:
[https://patchwork.kernel.org/patch/9447987/](https://patchwork.kernel.org/patch/9447987/)
how do i install this patch file?

---

### Post by Yellow Pasque on 2018-02-06
The patch was already applied in kernel 4.10

---

### Post by edenah on 2018-02-06
uname -a
Linux eden-Alienware-15-R2 4.13.0-32-generic #35-Ubuntu SMP Thu Jan 25 09:13:46 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/versiAdvanced Linux Sound Architecture Driver Version k4.13.0-32-generic

 head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Creative CA0132


==> /proc/asound/card0/codec#2 <==
Codec: Intel Skylake HDMI

---

### Post by edenah on 2018-02-12
Bump

---

### Post by Yellow Pasque on 2018-02-12
Look at amixer output again to make sure you turned on the proper settings:
```
amixer
```

---

### Post by edenah on 2018-02-13
> **Temüjin said:**
> Look at amixer output again to make sure you turned on the proper settings:
```
amixer
```

that is my output while connected to headphones:

```

amixerSimple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 99
  Mono:
  Front Left: Playback 86 [87%] [-4.00dB] [on]
  Front Right: Playback 86 [87%] [-4.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Surround',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Mic SVM',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Mic1-Boost (30dB)',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',2
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',3
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',4
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 99
  Front Left: Capture 99 [100%] [9.00dB] [on]
  Front Right: Capture 99 [100%] [9.00dB] [on]
Simple mixer control 'AMic1/DMic',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'AMic1/DMic Auto Detect',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Analog-Mic2',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 99
  Front Left: Capture 90 [91%] [0.00dB] [on]
  Front Right: Capture 90 [91%] [0.00dB] [on]
Simple mixer control 'CrystalVoice',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Crystalizer',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Dialog Plus',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Echo Cancellation',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Equalizer',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Noise Reduction',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'PlayEnhancement',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Smart Volume',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Voice Focus',0
  Capabilities: cswitch cswitch-joined
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'VoiceFX',0
  Capabilities: cenum
  Items: 'Neutral' 'Female2Male' 'Male2Female' 'ScrappyKid' 'Elderly' 'Orc' 'Elf' 'Dwarf' 'AlienBrute' 'Robot' 'Marine' 'Emo' 'DeepVoice' 'Munchkin'
  Item0: 'Neutral'
Simple mixer control 'What U Hear',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 99
  Front Left: Capture 90 [91%] [0.00dB] [on]
  Front Right: Capture 90 [91%] [0.00dB] [on]
Simple mixer control 'X-Bass',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]

```
is it ok? idk how these settings are supposed to work.

---

### Post by Yellow Pasque on 2018-02-13
```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

You don't have the HeadPhone sensing enabled. Disconnect the headphones and enable ^those settings in alsamixer.

---

### Post by edenah on 2018-02-13
> **Temüjin said:**
> ```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

You don't have the HeadPhone sensing enabled. Disconnect the headphones and enable ^those settings in alsamixer.


Sorry for the stupid question but... How do i do that? :>

---

### Post by tinylagarto on 2018-02-13
Open alsamixer from terminal:

```
alsamixer
```

Switch with the keyboard to headphones, to the right it would be, and then hit the key 'm'. That should activate the headphones. Then you can also increase or decrease the volume. With the esc key you will exit alsamixer

---

### Post by edenah on 2018-02-13
it works!! 
Thank you all!!!
im sorry i said it wasn't mute. i thought all i needed to unmute, all i needed to do was press enter.
seems the key was m. 
thanks :D

---

### Post by edenah on 2018-02-19
Hi i am a week after this issue got solved and it happened again!
i tried again to unmute the setting in the alsamixer and it doesn't work anymore! please help

---

### Post by mikervr on 2018-03-13
Hi, I am facing the same problem. I am new in Linux OS. I have Hyperx Cloud Headset which I bought a few days back. My friend also suggests me to buy this headset. I read few [posts]("https://www.bestdigiworld.com/best-gaming-headset-100.html") about it then buy. See Anandtech gaming headset [discussion]("https://forums.anandtech.com/threads/gaming-headset.2522057/"), they talking about a headset.
I asked on a group can I use this on Ubuntu OS, and someone replied yes. then I buy. I tried a lot of things but nothing happens. Even I tried to remove the speaker jack. I have tried [this instruction]("https://askubuntu.com/questions/132440/headphone-jack-not-working") as well.

---

### Post by Yellow Pasque on 2018-03-13
The solution to this sort of problem depends on your specific laptop/mobo/soundcard. Do you have the same Alienware 15 R2 laptop as the OP? If not, please start your own thread, and give the alsa information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

