---
title: "Itunes, decrypting music in Rhythm box"
date: 2010-03-31
forum: Multimedia Software
---

### Post by ubuchignome on 2010-03-31
Any one know how to decrypt music purchased from Itunes to run in RhythmBox? Some of my music loaded, but some will not?:guitar:

---

### Post by Chronon on 2010-03-31
I don't think there's a way to do that.  You might be able to find a workaround to circumvent the DRM, but I won't advise you about that (since it can be illegal).  You should be able to find advice about that if you are interested.

This whole bother is one of the biggest reasons not to purchase media encumbered by DRM (digital restrictions management!).  If you decide to change platforms then you can lose the ability to playback music you have legally purchased.

---

### Post by ubuchignome on 2010-03-31
Thanks, that is why I hate apple. But I should not have purchased the music.

---

### Post by Chronon on 2010-04-01
If you have access to iTunes (dual boot or VirtualBox maybe?), this might be an option:
> **Can I upgrade previously purchased music to iTunes Plus?**

Yes. Any available upgrades will be shown on the Upgrade to iTunes Plus page. You can upgrade all of your items at once by using the Buy All button. This replaces all eligible previous purchases with iTunes Plus versions of the same items. You can also choose to make individual upgrades by clicking the Buy button to the right of each item. Song upgrades are available for 0.30 USD, video upgrades for 0.60 USD, and albums for 30 percent of the album price. The counter to the right of the "Upgrade to iTunes Plus" link in the Quick Links box will indicate when additional eligible content become available.
From [http://support.apple.com/kb/ht1711](http://support.apple.com/kb/ht1711)

Not saying this is what you should do.  That's up to you, of course.

---

### Post by ubuchignome on 2010-04-01
Thanks, for now I am using the Virtual Box and running XP for I tunes. I am going to look for a device to replace my ipod. Any suggestions? I want to find a phone that supports Linux and plays music. I was looking at the Droid, but have not really checked out anything else.
Thanks much.

---

### Post by Chronon on 2010-04-01
I'll let someone else chime in about that.  I don't have a fancy phone.  I have a few mp3 players, though.  I am a Rockbox enthusiast, so I tend to choose devices based on ability to run Rockbox.

---

### Post by snares on 2010-04-01
There should be a codec to decrypt iTunes files. I haven't had any problem. I pulled stuff right of my friends ipod. I also have gotten a HDD from another friend that had a bunch of music he bought. Ubuntu recognized the file format and installed the codec. I don't know why its not happening on your computer but I'v'nt had it not recognize the file format since say 8.04 so its been a while. 

As for a phone that you should go with to replace the iPod. The Droid is an excellent choice. I have a Nexus One myself. You'd have to wait for that if you got Verizon. If your able to switch carrier Hero is great. Or you could wait for the EVO looks really nice. Basically any Android phone would be a great choice. Look at what you want in a phone (touch screen size, cpu power, storage space, physical or virtual keyboard, etc)and then select an android phone that fits you. Dont be afraid to go into the store and try it out before you buy. If your going to sign a contract you better like the phone.

---

### Post by Chronon on 2010-04-01
> **snares said:**
> There should be a codec to decrypt iTunes files. I haven't had any problem. I pulled stuff right of my friends ipod. I also have gotten a HDD from another friend that had a bunch of music he bought. Ubuntu recognized the file format and installed the codec. I don't know why its not happening on your computer but I'v'nt had it not recognize the file format since say 8.04 so its been a while. 


Playing MP4 containers containing AAC-LC audio streams (typically these have a .m4a extension when created by iTunes [or purchased from their store]) is not the problem.  The problem is that many tracks purchased from the online store are encumbered by DRM (Digital Rights [Restrictions!] Management).  These tracks are encrypted and can only be played on a computer that has the right decryption key.  I am quite sure that there isn't a codec that is able to generate keys on all possible encrypted files.

You can buy music from iTunes that doesn't have DRM (I have done this in the past).  So, merely playing music that has been purchased from the iTunes store doesn't really tell you much.  Do the files you are talking about have a .m4p extension (used by iTunes to signify an MP4 container containing encrypted streams)?

---

### Post by ubuchignome on 2010-04-02
All the music I have from the Itunes store has an M4a extension. I can play some of them on rhythm box but some are reporting an import error stream is encryped...decryption not supported

---

### Post by Chronon on 2010-04-02
Huh.  All of the encrypted files I have encountered have had a .m4p extension.  I guess this means that convention isn't universally followed.  They are all just MP4 containers containing various media streams.

---

### Post by ubuchignome on 2010-04-02
I stand corrected, here is the full file extension (01 Swing, Swing.m4a) and under properties it is listed as (MPEG-4 audio (audio/mp4)

---

### Post by andrea000 on 2010-04-02
Try sound [converter]("http://soundconverter.berlios.de/") it is in synaptic and it will
convert to mp3 or what ever your looking for but it
will not do videos only songs.

---

### Post by Chronon on 2010-04-02
It appears that that would only work if you are able to decode the streams in the first place, which appears to be the trouble here.

---

### Post by ubuchignome on 2010-04-02
Anyone know what would be a decoder for this issue?

---

### Post by Chronon on 2010-04-02
If we trust that the streams are encrypted then I think that no available codec is going to help you.  You either need to circumvent the DRM or purchase versions that don't have DRM. 

If the encryption messages are incorrect then you should be able to play the streams in linux.  You could try andrea000's suggestion or see if VLC will play them (since I think VLC uses its own codecs rather than gstreamer codecs).

---

### Post by jfa2214 on 2010-04-14
Use itunes software to burn cd. The cd will be a .cdda format. It will be playable on commercial cd players. You can also load the cd contents into Rytmbox and it will convert them to mp3, if you select mp3 under preference. Some issues may occur. Sometimes only the track numbers are displayed, but the music is still playable.

---

### Post by Chronon on 2010-04-14
I don't think discussion on DRM circumvention methods is wanted here.

---

### Post by fallenice on 2010-05-04
I just want to be clear that don't condone circumventing DRM for files you haven't purchased yourself.  That being said, I'm pretty sure you should be able to, copy and paste files from an authorized iSomething into Rythymbox DRM or not.

If you have an ipod/phone/pad around, I believe using it as an intermediary transfer device is all you need.  As long as it is authorized for the itunes account the music is registered to.

I would try highlighting and copying all of the music files in the device music list, and paste to the local library.

I'm thinking that the transfer method employed is similar to the method used when listening to music off of an iSomething through itunes.  You can do this on non-authorized machines, so perhaps the device stores the key as well (since you have to authorize the device before transfering purchase TO it as well).

Hope that helps.

---

