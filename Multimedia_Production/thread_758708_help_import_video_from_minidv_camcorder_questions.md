---
title: "help import video from minidv camcorder questions"
date: 2008-04-18
forum: Multimedia Production
---

### Post by jaime77 on 2008-04-18
hi,
im very new to import videos from a camcorder to a pc.
i used pynnacle usb pctv in windows xp for analog signal, a few years ago, and used firewire in windows just once.
i buy a laptop and was thinking buy studio 11, but just cant take any more vista, i just hate it, even copying and searching files was a nightmare.

so i will try ubuntu, but have some questions.

1. should i try downloading and try ubuntu studio, has everything i need, or i just download some packages in ubuntu?

2. whats the best program, how many real working options i have to edit videos?

3. i will import videos from a sony camcorder, firewire, is there any special setting, resolution, i mean, when you import videos all are the same quality, or can be customized

4. after importing the video, what recommend to encode or store the video, file type, resolution, quality, size, bitrate, etc

5. i know the proccesor is important to the encode be fast or slow, but it affect the quality?, i mean, a celeron will take longer to solve a complicated math calculation, a core 2 duo will take less time, but both will have the same result. is true in video encoding? the processor only affect the time or it affect the quality too?

im sorry if some questions are stupid, but i really a newbie in this, any help, tip, experience, etc will be very apreciated

---

### Post by kayosiii on 2008-04-18
1) the second option will mostly cover you - install the ubuntu studio packages you want through apt-get.

2) There is no really good solution yet... Cinelerra is usuable but can be quite buggy (more so in Hardy than Gutsy)  - though kdenlive  & openmovie editor are all worth trying. Cinelerra is being retooled into a new application but that is still some ways off.

3)kino I have found by far the best way of importing from a dv camera.

4) for firewire video is best to leave in DV codec either quicktime avi type 2 or raw dv should be fine.... it is reasonably well read and understood.

Cinelerra in particular behaves itself a lot better with uncompressed footage... I have been using ffmpeg to encode a lot of my other sources as png encoded quicktime movies. This gives you lossless compression but chews a lot of hard disk space - The style of video editing I do involves mixing video in passes so lossy compression really gets noticed. To go out from Cinelerra to DVD I have been using the yuv4mpeg export option.... however this process is very slow and I am looking for alternatives.

5) Processor will not effect the quality... not directly anyways - its just that you are more likely to compromise if you are on a slower processor in order to save time.

---

### Post by jaime77 on 2008-04-20
thx

one last question...

what processor you think is better for what i will do?

Turion 64 MK-38 2.2ghz 512kb L2
Turion 64 X2 Dual-Core TK-57 1.9ghz 256kbX2 L2  
Intel Pentium T2330 1.6ghz 1mb L2

each one with

Nvidia 7000M
ATI X1200
INTEL X3100

thx

---

