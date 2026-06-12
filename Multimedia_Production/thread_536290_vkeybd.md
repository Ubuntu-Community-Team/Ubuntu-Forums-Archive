---
title: "vkeybd"
date: 2007-08-27
forum: Multimedia Production
---

### Post by anv on 2007-08-27
I don't have sound from my vkeybd, hydrogen is working and normal sounds too, I remember I had this installed earlier and it worked without any extra tuning..

---

### Post by Stochastic on 2007-09-17
do you have Jack running? check the midi tab inside Jack if you do - quite often it makes you connect things manually, if you don't your problem probably lies in the alsa midi area.

---

### Post by darsu on 2007-09-17
Are you connecting vkeybd correctly?

"pmidi -l" shows you what ALSA ports are active. Eg:

```

 Port     Client name                       Port name
 14:0     Midi Through                      Midi Through Port-0
 16:0     SBLive! Value [CT4832]            EMU10K1 MPU-401 (UART)
 17:0     Emu10k1 WaveTable                 Emu10k1 Port 0
 17:1     Emu10k1 WaveTable                 Emu10k1 Port 1
 17:2     Emu10k1 WaveTable                 Emu10k1 Port 2
 17:3     Emu10k1 WaveTable                 Emu10k1 Port 3
128:0     ZynAddSubFX                       ZynAddSubFX

```

In this situation starting vkeybd with "vkeybd --addr 128:0" will make the vkeybd instance explicitly use ZynAddSubFX. If there are several programs running, you possibly need to specify the port like this.

---

