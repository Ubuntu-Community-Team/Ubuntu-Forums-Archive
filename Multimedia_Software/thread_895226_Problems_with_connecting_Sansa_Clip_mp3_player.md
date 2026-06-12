---
title: "Problems with connecting Sansa Clip mp3 player"
date: 2008-08-20
forum: Multimedia Software
---

### Post by pfeifferock on 2008-08-20
i am trying to connect my San Disk Sansa Clip to my Fujitsu Lifebook s seres (hardy) and it worked when i was running windows but now it wont even notice it most of the time. My computer wont notice it if it is in MTP or MSC mode but if it is in auto detect. a logo will appear on the desktop and it will tell me to open it with rhythmbox but it will not apear in rythmbox. But when i try opening it with Banshee it will give me this error message 
"mtp device error 
Mtp.libmtpexeption: libmtp_error_connecting
at mtp.error.checkerror (errorcode error code) [0x00000]
at mpt.libmtp.getconnecteddevices (system.intptr& list)
[0x00000]
at mtp.mtpdevice.detect () [0x00000]
at banshe.dap.mtp.mtpdap.initialize (hal.device haldevice) [0x00000]" 
any help would be greatly appreciated i would really like to be able to move music from my laptop to my mp3 player. I am a relitive begenner so try to explain things as simply as you can. thanks :)

---

### Post by IanW on 2008-08-20
You should be able to mount it in Nautilus when set to MSC mode, which says "Hi I'm a USB drive" when connected.
(MTP mode says "Hi, I'm an mp3 player", but I've found it easier to use MSC in Linux.)

Once you've mounted the player, create an empty text file in the root of your Sansa called ".is_audio_player" (note the . at the start).
This will help Rhythmbox recognise it.

---

### Post by jtuchscherer on 2008-08-20
I used this method, too, but I had some content in the .is_audio_player file:

audio_folders=MUSIC/
folder_depth=99
output_formats=audio/x-ms-wma,audio/mpeg,audio/aac,audio/mp4 

I use a Sansa Clip as well.

---

### Post by IanW on 2008-08-20
jtuchscherer - You're right.

If the file is empty, all your music gets placed in the root of the player's drive.

---

### Post by pfeifferock on 2008-08-25
in msc format my computer sees that there is a flash connected but when i look inside it can't seem to find anything on it. it shows the files music, audible and recorded but they are all empty. Rythombox reads it when the drive is in auto detect. as does the desktop but it wont let me go inside the drive it just sees that it is there but if i click on it is just won't pay attention. With the added file should my computer read it in msc mode?
-Matthew Pfeiffer

---

