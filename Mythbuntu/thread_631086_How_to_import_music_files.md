---
title: "How to import music files"
date: 2007-12-04
forum: Mythbuntu
---

### Post by Steven McMegabyte on 2007-12-04
Hello,

it is my first installation of mythubuntu (7.10) and it looks very good.

I use a Jetway 7F2 1G5 mini ITX Board with VIA UniChrome graphic
and an Terratec DMX 6 Fire soundcard.

My main intention is to create a jukebox.
Video or TV comes later.

After starting the frontend I tried to import my music files from a 
usb harddisk. But I didn't find no function to do this.
I have found only music cd import. 

Can you explain me how I can import music files (wav, mp3, ogg)?

Thank you in advance.

Steven McMegabyte

---

### Post by Ek0nomik on 2007-12-04
> **Steven McMegabyte said:**
> Hello,

it is my first installation of mythubuntu (7.10) and it looks very good.

I use a Jetway 7F2 1G5 mini ITX Board with VIA UniChrome graphic
and an Terratec DMX 6 Fire soundcard.

My main intention is to create a jukebox.
Video or TV comes later.

After starting the frontend I tried to import my music files from a 
usb harddisk. But I didn't find no function to do this.
I have found only music cd import. 

Can you explain me how I can import music files (wav, mp3, ogg)?

Thank you in advance.

Steven McMegabyte

I have never used Mythbuntu, but I can't imagine it to be too different.

Once you put your USB device in, does it pop up saying to import files, browse files, or anything like that?

Can you post the output of these with the USB device in:

```
sudo fdisk -l
```

```
mount
```

---

### Post by Steven McMegabyte on 2007-12-04
Thank you very mutch for your answer.

After connnecting my harddisk mythubuntu makes an automount of this device. At the desktop I can see it in "thunar filemanager" with all my
music.
But when I start the mythubuntu frontend I want add these files to a playlist. But how?

---

### Post by daengbo on 2007-12-04
You'll need to create a folder and copy them into the folder. Then you'll just assign the folder as the music location in the Mythbuntu settings.

---

### Post by Steven McMegabyte on 2007-12-04
Thank you daengbo!

Can you explain me the path to the location where I can do this?

I know it gives a folderpath in preferences (var/lib/mythubuntu/music).

One of my first steps with the frontend was the import of a music cd.
After this import I could see index files in this folder but no wav, mp3 or ogg files. I suppose that the musicdata is stored in the mysql database.

In this reason, I thought there is a tool for import musicfiles.

If I copy my music in this folder, what is the next step?

---

### Post by Steven McMegabyte on 2007-12-04
Oh no!
It is so easy!
Sorry for my questions.
The only thing what to do is copying my files in /var/lib/mythtv/music
and then take a rescan for new music within the frontend.

Thank you for your endurance

---

### Post by mcouture on 2007-12-05
As a followup to this question....

Does Myth modify anything in its music directory?   I'm wondering if I can use the same music files/directory I am using to update my iPods and sharing with other applications...?

I don't want to have to have multiple copies of my ~135GB of mp3's.....

---

### Post by uopjohnson on 2007-12-05
myth doesn't modify the music directory.  I mount an NFS share all over the place and it seems to play nice.  I tunes will do all kinds of crap though so don't let it in there.

---

### Post by daengbo on 2007-12-06
I do this on my server. I have Myth with music, and I use [mt-daapd]("apt:mt-daapd") to share the music iTunes-style over the network. I don't actually have iTunes anywhere, but Rhythmbox sees and plays the share well.

No need to duplicate your music directory, sir!

---

### Post by mcouture on 2007-12-06
Great!  Good to know that I only need to have that big directory in one place.

---

