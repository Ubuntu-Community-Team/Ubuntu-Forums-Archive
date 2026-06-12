---
title: "Error: RingBuffer::safe_read(RemoteFile* ...): read failed"
date: 2008-12-11
forum: Mythbuntu
---

### Post by elj4176 on 2008-12-11
Had mythfrontend installed on my laptop with 64 bit 8.10 (upgraded from several versions prior) and it was working fine. I had to send the laptop to hp and they wiped my drive. Yes I had an image of it but I thought it would be a good idea to install 64 bit 8.10 fresh. 
At the same time I added a pvr-150 to my BE to go with my pvr-350. Everything is working fine on a different FE but my freshly installed 8.10 (with/without compiz and with/without ndivia hardware drivers) is having a lot of trouble. The FE freezes regularly with livetv and recorded shows and here is what is in the frontend.log:

2008-12-11 21:00:15.202 Mixer unable to find control PCM
2008-12-11 21:00:15.805 AFD: Opened codec 0x23bf8b0, id(MPEG2VIDEO) type(Video)
2008-12-11 21:00:15.805 AFD: codec MP2 has 2 channels
2008-12-11 21:00:15.805 AFD: Opened codec 0x227f2a0, id(MP2) type(Audio)
2008-12-11 21:00:16.872 NVP: prebuffering pause
2008-12-11 21:00:18.203 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:19.533 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:20.864 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:21.961 RingBuf(myth://ipofmyBE:6543/1057_20081209173000.mpg) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2008-12-11 21:00:22.194 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:23.526 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:24.857 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:26.187 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:27.518 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:28.848 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:30.179 NVP: Prebuffer wait timed out 10 times.
2008-12-11 21:00:31.509 NVP: Prebuffer wait timed out 10 times.

Anyone have any ideas? I'm just about ready to wipe the drive and try again - maybe with mepis or 32 bit something or other.

---

