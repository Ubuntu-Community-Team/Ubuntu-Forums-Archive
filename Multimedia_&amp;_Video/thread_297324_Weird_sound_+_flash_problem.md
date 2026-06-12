---
title: "Weird sound + flash problem"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by 14bmail on 2006-11-10
Hello there,
  I am running kde on ubuntu edgy. With the kubuntu 6.10 CD, the sound is detected and I can play music from it but after a few hours/day or so and upgrades the sound card either cannot be detected or when it is (I did "sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils" and then "sudo apt-get install linux-sound-base alsa-base alsa-utils" to get the sound card detected again on boot)

I then try to play music and things like xmms just don't play mp3s but if I have a streaming radio station, it seems to play 1-2 seconds of doubled speed music then stops. Backspace in console doesn't do a beep when it did 'at the start of the install'. It just seems something upgraded interferes with the sound card. Also I installed flash 9 and in browsers, things like youtube will load but only play 1-2 seconds then stop. I can fast forward and see the video and if I skip to a section somewhere, it will play but for 1-2 seconds again.

Some background. I have a toshiba m45-s265 laptop. dmesg log is:
[17179588.484000] intel8x0_measure_ac97_clock: measured 55470 usecs
[17179588.484000] intel8x0: clocking to 48000


also.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


0:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at e100 [size=256]
        I/O ports at e200 [size=64]
        Memory at d0180000 (32-bit, non-prefetchable) [size=512]
        Memory at d0180200 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>



*edit* This is dmesg.log from when I use kubuntu CD initially

[17179658.552000] intel8x0_measure_ac97_clock: measured 55499 usecs
[17179658.552000] intel8x0: clocking to 48000
[17179658.552000] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

*not sure if third line is to do with sound card?*

Any help is appreciated.. I really don't want to use windows to get sound out of my lappy.  If any one needs me to do things/show output, I'm happy to do so.

---

### Post by schlodowec on 2006-11-20
The same happens to me with flash in youtube, except that my soundcard is alright. I'm used to run Amarok, Kaffeine and Skype together, and everything works fine.

**Flash 9 plays 1/2 seconds then stops, too**. This weird behavior is present in Firefox, Opera and Konqueror, as they are all set up to use Flash 9. It didn't happen in previous versions of flashplayer.

[I]
"I can fast forward and see the video and if I skip to a section somewhere, it will play but for 1-2 seconds again"[/I]

The same happens here.

I use Kubuntu 6.10 Edgy.

---

### Post by 14bmail on 2006-11-26
Hi there, just to let you know, I fixed my error by doing [http://ubuntuforums.org/showthread.php?t=197082&page=2](http://ubuntuforums.org/showthread.php?t=197082&page=2)

Basically I turned off APCI in grub and the problems I stated initially stopped. Hope this may be of help.. :-k

---

