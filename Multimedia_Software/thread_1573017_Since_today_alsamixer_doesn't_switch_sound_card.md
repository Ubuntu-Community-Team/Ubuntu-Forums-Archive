---
title: "Since today alsamixer doesn't switch sound card"
date: 2010-09-12
forum: Multimedia Software
---

### Post by antismap on 2010-09-12
Hello, I installed lubuntu yesterday and it worked great. lubuntu uses only alsa without pulseaudio. Since today Sound works only on my internal sound card. Yesterday it worked well on my USB sound card, i just did alsamixer and chose the USB sound card with f6 and that was it.

Now, I can choose this sound card with f6 but then if I quit alsamixer and open it again, i'm on the first sound card again.. It's like alsamixer really doesn't want to use another sound card.

The other wierd thing is that when I do cat /proc/asound/cards, this usb card is listed at default.. but it's not because only the first one (listed as 0) works.

> michael@michael-desktop:~$ cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 22
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
 2 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xa000, irq 16
 3 [U0x46d0x804    ]: USB-Audio - USB Device 0x46d:0x804
                      USB Device 0x46d:0x804 at usb-0000:00:02.1-2, high speed
 4 [default        ]: USB-Audio - USB Audio CODEC 
                      Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:02.0-10, full

What can i do to use my usb sound card ? Yesterday it worked well so it's really no problem with my sound card.. (that works without any drivers btw)

thanks in advance for help.

---

