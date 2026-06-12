---
title: "Backend hardware help"
date: 2008-10-28
forum: Mythbuntu
---

### Post by shiftybugger on 2008-10-28
Hi all,

I've done quite a bit of searching on this. I think I know the answer, I just want to confirm.

I am building a file server running Ubuntu (although will prly go with Mythbuntu now, it looks like it would suit me exactlY)

Mobo: Asus M3A78-EMH HDMI
CPU: something like an X2 5000 - 6000 (lower or higher depending on if I understand correctly)
Ram: 4g DDR2 800 (existing)
and a bunch of hard drives in software raid 5 or 6

I also want to use the server as a MythTV backend for both SD and HD OTA television. I need it to be able to play and record both. The server might also double as an SD frontend until I get a HDTV (won't bother building a HD frontend until then - and it will be standalone, probably running XBMC Live)

Now, if I understand correctly, I don't need an uber CPU in the backend (I assume because encoding will be done on the TV tuner card?) but I do need 3ghz CPU in the frontend to decode HD stuff.

So:
1. Am I correct? (low grunt backend, high grunt frontend)
2. Mythbuntu contains all requirements for Linux software raid, right? Will running software raid impact the MythTV backend in any way?
3. Anyone know of a good TV tuner (available in Australia) that can do OTA digital and analogue? (or should I just get multiple cards?)
4. I chose the Asus M3A78-EMH HDMI because it has 6 SATA ports. I've read that AMD/ATI drivers can be sketchy in Linux. Anyone have any info on this particular board?

Thanks in advance for any advice.

---

### Post by ian dobson on 2008-10-29
Hi,

I can't answer all your questions but herewe go:-

1) The backend doesn't need to be that powerful. The only time you need "grunt" is when your transcoding recordings (MPEG2 -> MEG4)
2) MDADM is the raid configuration tool to use, and yes it's included in Mythbuntu/ubuntu. I'm running a 3Tb RAID5 array on my backend without any problems.
3) Sorry not sure, but [www.linuxtv.org](www.linuxtv.org) is a good place to look for supported cards.
4) I know that the ATI graphic drivers are abit dodgy on linux, but SATA shouldn't be a problem. I think linux has standard/builtin drivers for most SATA controllers.

Regards
Ian Dobson

---

### Post by larsolav on 2008-10-29
Just a short note on issue 3:
Are there any OTA channels in your area that are not digitally transmitted? If not, then you would not need an analogue tuner card (unless you want to capture cable or any other analogue signal). For digital tuners, whether the signal be SD or HD, the tuner cards do not encode the signal as it is already encoded. The digital tuners just saves the signal to a file.
Cheers and have fun!

---

### Post by newlinux on 2008-10-29
I'd just add that for decoding HD on your frontend if you don't need a 3ghz necessarily. Just about any dual core will do for decoding HD mpeg-2. I've gotten my old P4 2.6 to decode HD mpeg 2 recordings without XvMC. Now, if you want to decode 1080i or 1080p h.264 you will likely need a slightly more powerful CPU. But still not super powerful by today's high end dual cores and quad cores...

As mentioned, the extra power in your backend is useful for transcoding (which can take a while) and also commercial flagging.

---

### Post by Valen00 on 2008-10-30
If you can avoid RAID for your media drives and use storage groups you will greatly reduce the seek load on your disks. Keep RAID for the important stuff ;->.

---

