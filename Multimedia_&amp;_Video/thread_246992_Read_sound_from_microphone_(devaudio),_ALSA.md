---
title: "Read sound from microphone (/dev/audio), ALSA"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by radone on 2006-08-30
I have program that worked fine before year and now I am unable to read from /dev/audio :( 
Hardware is the same, distro has changed to Kernel: 2.6.12-9-386, Dapper drake.

Please, could anyone help me?

```
#include <sys/stat.h>
#include <fcntl.h>
// open
#include <unistd.h>
// perror
#include <stdio.h>
// some consts
int PACKET_SIZE=1000;

int main(){
    int audioinput;
    char *filename="/dev/audio";
    audioinput=open(filename,O_RDONLY|O_NDELAY);


    if( audioinput < 0 ){
        perror("open ");
    }

    unsigned char buffer[PACKET_SIZE];
    int count = read(audioinput,buffer,PACKET_SIZE);
    printf("len (should be 160):%d\n", count);

    close(audioinput);
    return 0;
}

OUTPUT: len (should be 160):-1

``` 


```
$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0:  [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``````

$ lspci -v
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
        Subsystem: Asustek Computer, Inc.: Unknown device 1733
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at a800 [size=256]
        I/O ports at a400 [size=128]
        Capabilities: [48] Power Management version 2

``````

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).

``````

$ cat /proc/asound/devices
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
 56: [1- 0]: digital audio capture
 32: [1- 0]: ctl

``````

$ cat /proc/asound/modules
0 snd_intel8x0
1 snd_usb_audio

``````

$ cat /proc/asound/cards
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with ALC650F at 0xa800, irq 18
1 [U0x46d0x8b0    ]: USB-Audio - USB Device 0x46d:0x8b0
                     USB Device 0x46d:0x8b0 at usb-0000:00:03.1-1, full speed

``````

$ cat /proc/asound/pcm
00-00: Intel ICH : SiS SI7012 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : SiS SI7012 - MIC ADC : capture 1
01-00: USB Audio : USB Audio : capture 1

```

---

### Post by amo-ej1 on 2006-08-30
read() returning -1 means an error has occured and that errno has been set (it could be something stupid like something else already having a lock, or a permission denied). So perhaps it makes sens to run your application within an strace or print out errno. 
Or even simpler, can you cat /dev/audio ?

---

