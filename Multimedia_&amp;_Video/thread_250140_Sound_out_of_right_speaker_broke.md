---
title: "Sound out of right speaker broke????"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by dannyboy79 on 2006-09-03
Please please whoever can help I would greatly appreciate it. I did a fresh install of Dapper and my sound worked fine out of both speakers and the subwoofer!! It's a 2.1 channel system. It's onboard sound, here is the output of  aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
Well, I had buddies over for poker night and did a remotre desktop from my laptop into my ubuntu box because that's where 1200 songs are. I used xmms and basically have one of those cables where it basically turns a audio plug (like the one that's on the end of headphones) and on the other side is rca plugs, white and red. I have used this kind of thing before but this time insterad of having to run up into my room and add songs to the playlist, I did it remotely using my laptop. Basically the audio cable I was using went from my ubuntu box out into my receiver tape selection and it plays what would be coming out of my ubuntu box. Well all of a sudden the it started playing out of the left side only. I didn't think anything of it at the time and just figured it was a badly recorded .mp3. Well, sure enough, now my sound only comes out of the left speaker and that's it. I have 2 computer hooked up aan audio, keyboard, mouse kvm switch and when I select the other computer by hitting scroll lock twice on the keyboard the other computers (winxp) sound is fine and comes out of both speakers so obviously it's ubuntu or alsa or something like that. What do I do? What could have made it break by just playing songs thru xmms. That was the first time i used remote desktop to do that and the first time I played with xmms but that can't be it can it? This is my lspci output:
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX H ost (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media I O] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound  Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fa st Ethernet (rev 90)
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller  180 SATA/PATA  [SiS] (rev 01)
0000:00:08.0 FireWire (IEEE 1394): Texas Instruments FireWire Controller (rev 01 )
0000:00:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG- 2 Encoder (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)
the only important line in dmesg was this:
input: PC Speaker as /class/input/input1
Can anyone please help me troubleshoot this.

---

### Post by Omnios on 2006-09-03
I had a similar problem before and after trying for hours found out it was the wire connection. Anyways worth checking out. Fiddle the wire a bit and see what happens

---

### Post by dannyboy79 on 2006-09-05
As I have explained it is not a wire issue due to BOTH speakers working on the windows xp box. My kvm controls my keyboard, mouse, and AUDIO. When I switch over to WINXP by hitting scroll lock twice the sound comes out of both sides, when I go back to Ubuntu, it only comes out of the left side so I know that it boils down to the Ubuntu install? I also know it's the ubuntu box because I can plug in a set of headphones right into the ubuntu box bypassing the kvm and still sound only comes out of the left side but when I test the same headphones in winxp, sound comes out of both sides! I don't have any clue why this would be??? As I said, all of a sudden it just started playing out of the left side only after playing some mp3's thru xmms over remote desktop. I would hate to have to reinstall over this issue!!!! If I did and then tried to restore my home directory who know if I am going to just restore some config that screws up the sound again and makes it only work out of the left side again. Please please, some expert has to know what's going on.

---

### Post by dannyboy79 on 2006-09-07
Ubuntu Forum moderators, can anyone please help with this??????? There are about 3 or 4 similar threads and this problem is not just a little thing, I believe it is serious. Can someone with years of linux knowledge please help us out????

---

### Post by dannyboy79 on 2006-09-15
bump, please please help. I have posted a few questions asking for help and so far neither of them have been answered???? This may be one reason why newbies end up going back to WINBLOZ! ANyway, I would really appreciate some help here. Also on my other threads about my Microsolutions Backpack CD-writer and most recently my resolution issue. Thank you.

---

### Post by TheMatt on 2006-09-16
Wow, I fixed it!!! For those of you using a kde desktop, go into Kmix and raise the IEC playback (or whatever volume control is below or to the right of the PCM) to full. Then it should work. If not, play around with the settings in there and see if you get it.

---

### Post by dannyboy79 on 2006-09-22
Why can't anyone help me here. I can't believe that NO ONE is familar with how alsa or oss works. Can't anyone help me troubleshoot this?????? It doesn't make sense because the sound was working before I played the music through xmms thru a remote desktop setup and also the speakers work in winbloz!! Help me please please please

---

### Post by dannyboy79 on 2006-09-25
Hello, please help me diagnos this????????

---

### Post by dannyboy79 on 2006-09-27
bump again!!!!!

---

### Post by dannyboy79 on 2006-10-05
Help please.

---

### Post by dannyboy79 on 2006-10-12
Please help. I go around helping people but can't seem to get any help myself. Anyone?

---

### Post by play150 on 2008-02-10
I just use windows, but sometimes my speakers do that too and I unplug and plug the speakers and it works again.

Temporary fix I hope it helps :D

Yes I know its a necro post, so what?

---

