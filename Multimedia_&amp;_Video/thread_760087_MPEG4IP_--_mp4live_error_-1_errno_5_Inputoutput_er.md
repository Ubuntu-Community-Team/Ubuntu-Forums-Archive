---
title: "MPEG4IP -- mp4live: error -1 errno 5 Input/output error"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by garbage2 on 2008-04-19
Hi all!

I'm trying to stream to a darwin server using mp4live 1.6.1 compiled from CVS in ubuntu 7.10 . Compiling went fine without errors. After starting mp4live everything is fine and for some minute (variable between 0 and 10-15) the audio/video quality (Xvid/AAC) is fantastic, but after some time the video freeze while the audio still being ok. This is the console output:

01:40:19.399-rtp-6: Created database entry for ssrc 0x4733b886 (1 valid sources)
01:40:19.400-mp4live-7: Using small frags
01:40:19.401-mp4live-7: oss init done
01:40:19.401-mp4live-7: Audio input size is 4096
01:40:19.433-mp4live-7: default:frametime 32000
01:40:19.465-mp4live-7: default:frametime 32000
01:40:19.497-mp4live-7: default:frametime 32000
01:40:19.530-mp4live-7: default:frametime 32000
01:40:20.827-mp4live-7: format is YUV 4:2:0 352x288
01:40:20.831-mp4live-7: control brightness min 0 max 255 val 56 convert 142
01:40:20.831-mp4live-7: control hue min -128 max 127 val 50 convert -1
01:40:20.831-mp4live-7: control saturation min 0 max 127 val 66 convert 83
01:40:20.831-mp4live-7: control contrast min 0 max 127 val 70 convert 88
01:40:20.831-mp4live-7: v4l2 thread start capture
01:40:20.902-mp4live-7: Frame 1208648420902895 request key frame
01:40:21.627-mp4live-3: error -1 errno 5 Input/output error


The last line is the moment when video freezes.
The capture card is a pinnacle with the famous saa7131 chip, but I've tried also with a Terratec HT Pci using the same chip and the result is the same: after the "error -1 errno 5 Input/output error" error mp4live still continues to stream audio only. At that moment if I tick the "preview" control the video starts again for some minute, after that it freezes again.
I've tried with other two differents TV cards that are using BT8xx chip and they works fine and without video freezes, but the video/audio quality is very poor against the saa7131-4 based cards.
I've tried the 1.5 version from tarball and is the same. I've tried another motherboard with AMD dualcore cpu (now I'm using a P4 2.2 Ghz) but is the same. I've tried using different parameters modprobing saa7134 and saa7134-alsa modules but nothing changed. I've tried linux-rt kernel... Nothing. I've changed pci latency in bios settings... Nothing. If I use some other audio codec (ulaw) everything works, but the audio is really ugly. I've tried installing some other version of faac... Nothing. I'm really stuck!!
I've tried installing mpeg4ip on the 8.04 beta release of ubuntu using apt-get but I haven't managed how to get AAC in mp4live in that deb version.

Is there someone with a good idea? Googling around I've found only another guy with the same problem but no solutions.


---Edit: Googling around I've found that the errno 5 Input/output error seems to be system-related (not coming from mp4live), this is why I'm asking here :)


Thank you in advance!

Nik

---

### Post by xc3RnbFO8P on 2008-04-20
Did you check your network card?

---

### Post by garbage2 on 2008-04-20
> **Ringi said:**
> Did you check your network card?




Thank you Ringi for your interest!  Even if I have not done special tests, I think that the network card is not the problem: it works fine, even when -sometimes- I control the machine via vnc from a windows machine. Lately I disabled vnc too, believing that was conflicting in some way with mp4live, but no way....  Another thing that make me think that it cannot be a network issue is that before starting streaming in mp4live, just activating for some minute the preview window the freeze happens the same in the preview even if there's no streaming in that moment. Last thing is that the problem happens in the AMD machine too, and that machine is using a completely different network card. In my opinion there is some kind of read/write error from physical interfaces (audio? video?) at low level (kernel?), but I'm not so skilled in Linux and I really can't figure out how to find what's happening and WHY ME!! :)

Some other idea?

---

### Post by xc3RnbFO8P on 2008-04-20
No I haven't. 
Only thing I find is related to hardware:
reading cd, dvd,
writing ide hard disk
and wireless.

---

### Post by garbage2 on 2008-04-20
Yeah, I found same things in google... That's why I'm thinking about a low-level (kernel to hardware) problem. I think that the TV card is seen by the system as like any other peripherical (being hdd, or wireless etc.) where system can read or write data, and something goes wrong at a certain point reading or writing into it. Or maybe the error is not correctly showed and is related to something else... Dunno.
The thing that drives me crazy is that it seems that I'm almost the only one in the world having this problem, I hope that if there is someone else he will post his experience here even if he has no solution. At least I'll feel not so lonely! :) :)

Thank you again for your support Ringi.


So:  nobody found this problem when streaming with mp4live?

---

### Post by SNG on 2008-05-30
> **garbage2 said:**
> 
So:  nobody found this problem when streaming with mp4live?

Yes, I found this problem too. I get mp4live source from hardy repository and rebuild for gutsy. I have 3 mashines: P4 3.2 HT, P4 3.0 HT and dual cpu AMD Opteron. All comps with 32 bit OS. Comps with P4 - Ok. Dual CPU comp - the same problem. I patch source and make loop for ioctl function with error counter (Up to 1000 errors). And now I don't have this problem on all comps.
This is not good solution, but i can't found true solution.

PS: Sorry for my english.

---

### Post by Kimran on 2008-06-02
hi there,
sorry to butt in,i don't really have a solution to your problem because i'm actually only trying out the streaming solution like u too,but u apparently have gotten further than i have,and i would really appreciate the help  from u guys just to get to the point where u're at presently and maybe we could brain storm from there ,i've got my channel encoders inplace,my capture cards (sabrent PCIRC),mpeg4ip version 1.6 and DSS 1.5 installed on an ubuntu gutsy 7 machine .So far between the DSS AND the mpeg4ip i could only tell that the DSS runs properly,i guess all  that's missing is the proper configurations .But i have no idea how to use the mp4live from mpeg4ip and that's where i need help with getting the video source and the configuration of the mp4live program,also i'd like to know whether mp4live has the ability to work with raw files (ie.able to take an avi or DVD OR mpeg 4 file and encode them ,hint them and stream them).please i know u got ur own problems but you have gotten that far,sometimes when i have problems helping some-one else with what i have gotten to work usally sheds some light on my present problem at hand so i'll be your student.need the help.one last thing if u do answer me please include the direction to the mp4live output file.where it saves it's stuff by default.

---

