---
title: "Can play iso but not when burned to disk"
date: 2015-08-29
forum: Multimedia Software
---

### Post by Pete White on 2015-08-29
I'm trying to understand something about why a DVD copy does not work, which is probably exposing a basic misunderstanding about how DVDs work. Can I ask for some help?

- I have a video DVD, which I would like to copy because my daughter scratched it, so it no longer plays in our home player, but does in the computer. Note that this is legal "fair use" in this country.
- I run ddrescue on it, and I get an iso file.
- VLC can play the iso file, and all is well.
- I write the iso file to a blank DVD.

So far so good. This is the bit that I am baffled by.
- VLC cannot play the physical DVD media that I copied to. The video is just a total mess, and horribly corrupted.
- It's not actually corrupted, because if I read the bad disk copy to iso file, it's the same as the iso file that VLC can play (same => same md5sum, so byte for byte identical).

My guess is that VLC is doing something different when playing a disk to when it is playing the iso from file - and that's some part of the whole "how video DVDs work" logic that I'm missing. Can somebody please enlighten me or point me at some information?

One piece of context that is almost certainly relevant. This disk has Disney copy protection; running dvdbackup plus mkisofs doesn't work because they've done fishy things with the file system (as I understand it their model creates dummy VOB files that share blocks with other files; since the player never needs to access these, it doesn't matter, but naively copying will fail because there are GB of fake data there - I am now sufficiently irritated that I am thinking of trying to crack that, but first want to get my head round the madness above). 

Thanks for your help

---

### Post by TheFu on 2015-08-29
DRM. Commercial video DVDs have DRM that ties into the hardware of players.

---

### Post by mc4man on 2015-08-29
Your ddrescue iso is css encrypted (& structure protected). Vlc can play back the iso locally by using libdvdcss2 in brute force mode. 
However you cannot use that css encrypted iso to recreate a DVD_VIDEO dvd disk.

---

### Post by Pete White on 2015-08-30
I get that CSS encryption is there in the ISO file, and I can remove that with dvdbackup (at the cost of some tedious dealing with the DRM shenanigans - I get 47GB of data on this disk because of the DRM), or I can just play the encrypted ISO with VLC (that has the encryption keys).

I think the (very basic) issue that I had not appreciated is that even though I can create a data DVD with the right contents (i.e. the ISO file that VLC can read), it's a data DVD, not a DVD_VIDEO DVD. Hence when VLC (or any other player) expects to read a DVD_VIDEO disk, it all goes wrong. I need to create a DVD_VIDEO from the contents of the iso, and thanks to the nasty DRM and the deliberately corrupted files in the file system that's rather fiddly (though I can certainly do it - if I can play it, I can record and so make my backup, though ironically losing all the Disney adverts etc. because of their copy protection!).

Thanks for the help.

---

### Post by TheFu on 2015-08-30
I understand that ABC/Disney has some of the ugliest DRM out there. When I was backing up our collection here - trying to keep little fingers off it completely - vobcopy handled it about 80% of the time. If the disc was already corrupted, who knows if it will every be readable with or without DRM? For any discs that can't be backed up, little fingers cannot touch. They are not allowed. Perhaps when they reach 25 yrs of age - some of those discs cannot be replaced after all.

---

### Post by Rob Sayer on 2015-08-30
Disney does indeed use pretty nasty advanced DRM which is beyond CSS.  I don't know of any linux tools that can handle it.  Many if not most WIndows DVD rippers won't.

My suggestion would be to get the installer for DVDFab HD Decrypter and run it in Wine.  It's free.  And according to this ...

[https://appdb.winehq.org/objectManager.php?sClass=application&iId=2377](https://appdb.winehq.org/objectManager.php?sClass=application&iId=2377)

... it should work fine.

---

### Post by TheFu on 2015-08-30
> **Rob Sayer said:**
> Disney does indeed use pretty nasty advanced DRM which is beyond CSS.  I don't know of any linux tools that can handle it..

makemkv - but it just slurps the mpeg2 streams and subs into an MKV per title. No package - source + binary blob to build it and it expires every 30-60 days ... I hear.  They have a commercial product for the other OS.  Do not mount the disc before using it.

Then use something like handbrake to transcode to a smaller size - usually about 75% smaller. So I hear. vobcopy is much nicer when it works, I hear.

---

### Post by mc4man on 2015-08-30
> **Pete White said:**
> I get that CSS encryption is there in the ISO file, and I can remove that with dvdbackup (at the cost of some tedious dealing with the DRM shenanigans - I get 47GB of data on this disk because of the DRM), or I can just play the encrypted ISO with VLC (that has the encryption keys).

I think the (very basic) issue that I had not appreciated is that even though I can create a data DVD with the right contents (i.e. the ISO file that VLC can read), it's a data DVD, not a DVD_VIDEO DVD. Hence when VLC (or any other player) expects to read a DVD_VIDEO disk, it all goes wrong. I need to create a DVD_VIDEO from the contents of the iso, and thanks to the nasty DRM and the deliberately corrupted files in the file system that's rather fiddly (though I can certainly do it - if I can play it, I can record and so make my backup, though ironically losing all the Disney adverts etc. because of their copy protection!).

Thanks for the help.
That's generally correct to a point. Vlc (or any other player that supports DVD_VIDEO) don't 'have' the keys, they just use libdvdcss in one way or the other. Correct or incorrect keys are stored in ~./dvdcss in a per volume label basis, players first look there & use if found. 
Your .iso would not usually have the same label as the orig. disc so the player would use & need to use a different means to decrypt.


   >  DVDCSS_METHOD: sets the authentication and decryption method that libdvdcss will use to read scrambled discs. Can be one of title, key or disc.
        key is the default method. libdvdcss will use a set of calculated player keys to try and get the disc key. This can fail if the drive does not recognize any of the player keys.

        disc is a fallback method when key has failed. Instead of using player keys, libdvdcss will crack the disc key using a brute force algorithm. This process is CPU intensive and requires 64 MB of memory to store temporary data.

        title is the fallback when all other methods have failed. It does not rely on a key exchange with the DVD drive, but rather uses a crypto attack to guess the title key. On rare cases this may fail because there is not enough encrypted data on the disc to perform a statistical attack, but in the other hand it is the only way to decrypt a DVD stored on a hard disc, or a DVD with the wrong region on an RPC2 drive.


Disc keys are on the orig. disc but aren't & cannot be copied to an. iso file as the area they are stored on is not accessible to ddrescue or similar like dvddisaster.
(- 'title' method  is what's used on the iso file you have)

While it's is possible to do an 'in place' decryption of css on an iso file thru some obscure code/compiled binary,  in this case wouldn't be much value  as you'd have to manually fix the structure protection which can be a chore in linux or just plain not possible.
To get a true back up to dvd disc you'd be better off in windows/windows programs or maybe thru the mentioned windows app in wine.

---

### Post by Pete White on 2015-08-31
I have found that :
- ddrescue gets me an ISO file that VLC can play, but that directly burning to DVD doesn't help with (pity!).
- dvdbackup on that ISO gets me the whole VIDEO.TS structure, but with some dummy files. That's playable too.
- mkisofs blows up horribly because of the multi GB dummy files that disney likes to leave lying around. Sigh.

So I seem to be able to rip the contents, but haven't got writing back to be reliable yet. That's tedious, but I'm sure I can get past it; worst case I can turn the main track to MP4 and just burn it to disk. I hate this nonsense; it doesn't stop piracy, just annoys real customers.

---

