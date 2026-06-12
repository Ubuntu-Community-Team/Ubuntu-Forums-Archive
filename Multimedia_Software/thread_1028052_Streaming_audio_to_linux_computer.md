---
title: "Streaming audio to linux computer"
date: 2009-01-02
forum: Multimedia Software
---

### Post by fragman44 on 2009-01-02
I have a Desktop computer running Intred Ibex, and a mini laptop running windows XP.  I have set of speakers plugged into my desktop computer, while my laptop doesn't have any speakers.  I was wondering how I could stream or use a proxy like PulseAudio to stream audio from my laptop running XP to my desktop running Intrepid Ibex.  Is this sort of thing possible?

Regards,
Steven

---

### Post by cariboo on 2009-01-02
The easiest way would be to share you musiv directory on the laptop then connect to the share in Ubuntu. There is no etxra setup needed, as Ubuntu automagically connects to Windows share out of the box. Just make sure that both computers are in the same work group. Depending on which version of XP you are running, XP Pro uses WORKGROUP and XP Home uses MSHOME. Ubuntu uses WORKGROUP by default, it is easier for someone that is more familiar with XP to change the workgroup in Windows, so if you are using XP Home change the workgroup.

Once you have the sharing and workgroups setup go to Places-->Network-->Windows Networking-->WORKGROUP--><ComputerName>--><SharedDirectory> and start playing tunes. <ComputerName> = your laptops name and SharedDirectory is the music directory you set up to share.

Jim

---

### Post by fragman44 on 2009-01-02
I've got that all set up, but I am going to be using my laptop to connect to my projector which cannot be plugged into my desktop computer. with the layout of my room, any of my computers can't be plugged into the speakers and the projector at the same time.  I could solve this with some extended cables, but I would much rather solve this with software. it would also nice to be able to play to my speakers from my laptop anywhere in my room.

regards,
steven

---

### Post by fragman44 on 2009-01-02
bump?

---

